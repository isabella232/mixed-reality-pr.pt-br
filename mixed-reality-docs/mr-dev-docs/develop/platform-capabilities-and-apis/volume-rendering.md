---
title: Renderização de volume
description: Saiba como renderizar com eficiência imagens volumosas com opacidade e cor em Windows Mixed Reality.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagem volumetric, renderização de volume, desempenho, realidade misturada
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220922"
---
# <a name="volume-rendering"></a>Renderização de volume

Para volumes médicos de MRI ou engenharia, consulte [Renderização de volume na Wikipédia.](https://en.wikipedia.org/wiki/Volume_rendering) Essas "imagens volumosas" contêm informações rich com opacidade e cor em todo o volume que não podem ser expressas facilmente como superfícies como [malhas poligonais](https://en.wikipedia.org/wiki/Polygon_mesh).

Principais soluções para melhorar o desempenho
1. BAD: Abordagem naïve: mostrar volume inteiro, geralmente é executado muito lentamente
2. BOM: Plano de Corte: mostrar apenas uma única fatia do volume
3. BOM: Reduzindo o sub volume: mostrar apenas algumas camadas do volume
4. BOM: reduza a resolução da renderização de volume (consulte 'Renderização de cena de resolução misturada')

Há apenas uma determinada quantidade de informações que podem ser transferidas do aplicativo para a tela em qualquer quadro específico, que é a largura de banda total de memória. Além disso, qualquer processamento (ou 'sombreamento') necessário para transformar esses dados para apresentação requer tempo. As principais considerações ao fazer a renderização de volume são:
* Screen-Width * Screen-Height * Screen-Count * Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (volume de res completo: muitos exemplos)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% de total) (fatia fina: 1 amostra por pixel, é executado sem problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% de total) (fatia de subvolume: 10 amostras por pixel, é executado sem problemas, parece 3d)
* 200 * 200 * 2 * 256 = 20480000 (5% de volume res inferior: menos pixels, volume completo, parece 3d, mas um pouco desfocado)

## <a name="representing-3d-textures"></a>Representando texturas 3D

Na CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Na GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Sombreamento e gradientes

Como sombrear um volume, como a MRI, para visualização útil. O método principal é ter uma "janela de intensidade" (um mínimo e um máximo) em que você deseja ver as intenções e simplesmente dimensionar para esse espaço para ver a intensidade preta e branca. Uma 'rampa de cores' pode então ser aplicada aos valores dentro desse intervalo e armazenada como uma textura, para que diferentes partes do espectro de intensidade possam ser sombreadas em cores diferentes:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

Em muitos de nossos aplicativos, armazenamos em nosso volume um valor de intensidade bruto e um 'índice de segmentação' (para segmentar partes diferentes, como capa e cúlsia; esses segmentos são criados por especialistas em ferramentas dedicadas). Isso pode ser combinado com a abordagem acima para colocar uma cor diferente ou até mesmo uma rampa de cores diferente para cada índice de segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Fatia de volume em um sombreador

Uma primeira etapa excelente é criar um "plano de fatiamento" que pode passar pelo volume, 'fatiando-o' e como os valores de verificação em cada ponto. Isso pressupo que há um cubo 'VolumeSpace', que representa onde o volume está no espaço do mundo, que pode ser usado como uma referência para colocar os pontos:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Rastreamento de volume em sombreadores

Como usar a GPU para fazer o rastreamento de subvolume (percorre alguns voxels de profundidade e, em seguida, camadas nos dados de volta para frente):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Renderização de volume inteiro

Modificando o código de subvolume acima, podemos obter:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Renderização de cena de resolução misturada

Como renderizar uma parte da cena com uma resolução baixa e colocá-la novamente no lugar:
1. Configurar duas câmeras fora da tela, uma para seguir cada olho que atualiza cada quadro
2. Configurar dois destinos de renderização de baixa resolução (ou seja, 200 x 200 cada) em que as câmeras são renderizações
3. Configurar um quádruplo que se move na frente do usuário

Cada quadro:
1. Desenhar os destinos de renderização para cada olho em baixa resolução (dados de volume, sombreadores caros e assim por diante)
2. Desenhar a cena normalmente como resolução completa (malhas, interface do usuário e assim por diante)
3. Desenhar um quádruplo na frente do usuário, sobre a cena e projetar que o low-res renderiza nesse
4. Resultado: combinação visual de elementos de resolução completa com dados de volume de baixa resolução, mas de alta densidade
