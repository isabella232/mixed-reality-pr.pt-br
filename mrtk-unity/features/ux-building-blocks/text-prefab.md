---
title: Pré-fabricado de texto
description: Visão geral do TextPrefab no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, TMP,
ms.openlocfilehash: 1969bc9e3054fec509e9f7d536cbfe4b97e43563e26ba5476601e78e65ad24f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209036"
---
# <a name="text-prefab"></a>Pré-fabricado de texto

Esses pré-fabricados são otimizados para a qualidade de renderização no Windows Mixed Reality. para obter mais informações, leia o texto de diretrizes [no Unity](/windows/mixed-reality/text-in-unity) no Microsoft Windows Centro de Desenvolvimento.

## <a name="prefabs"></a>Pré-fabricados

### <a name="3dtextprefab"></a>3DTextPrefab

Malha de texto 3D pré-fabricado (assets/MRTK/SDK/StandardAssets/pré-fabricados/Text) com fator de dimensionamento otimizado em distância de 2 metros. (Leia as instruções abaixo)

### <a name="uitextprefab"></a>UITextPrefab

Malha de texto de interface do usuário pré-fabricado (assets/MRTK/SDK/StandardAssets/pré-fabricados/Text) com fator de dimensionamento otimizado em distância de 2 metros. (Leia as instruções abaixo)

## <a name="fonts"></a>Fontes

Fontes de software livre (ativos/MRTK/núcleo/StandardAssets/fontes) incluídas na realidade misturada Toolkit.

> [!IMPORTANT]
> O texto pré-fabricado usa a fonte de código aberto ' Selawik '. Para usar pré-fabricado de texto com uma fonte diferente, importe o arquivo de fonte e siga as instruções abaixo. O exemplo abaixo mostra como usar a fonte ' Segoe UI ' com o texto pré-fabricado.

![Importando Segoe UI arquivo de fonte](../images/text-prefab/TextPrefabInstructions01.png)

1. Atribua a textura de fonte ao material 3DTextSegoeUI. passe-partout.

    ![Atribuindo textura de fonte](../images/text-prefab/TextPrefabInstructions02.png)

1. No material 3DTextSegoeUI. passe-partout, selecione o sombreador personalizado/3DTextShader. sombreador.

    ![Atribuindo sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. Atribua Segoe UI fonte e material 3DTextSegoeUI aos componentes de texto no pré-fabricados.

    ![Atribuindo material e arquivo de fonte](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Trabalhando com fontes no Unity

Ao adicionar uma nova textmesh 3D a uma cena no Unity, há dois problemas que são visualmente aparentes. Uma delas, a fonte aparece muito grande e duas, a fonte aparece muito borrada. Também é interessante observar que o valor do tamanho da fonte padrão é definido como zero no Inspetor. Substituir esse valor zero por 13 não mostrará nenhuma diferença no tamanho, porque 13 é, na verdade, o valor padrão.

O Unity pressupõe que todos os novos elementos adicionados a uma cena tenham uma unidade Unity de tamanho ou uma escala de transformação de 100%, o que traduz em cerca de 1 metro na HoloLens. No caso de fontes, a caixa delimitadora de uma telemalha 3D entra, por padrão, em cerca de 1 metro de altura.

### <a name="font-scale-and-font-sizes"></a>Escala de fonte e tamanhos de fonte

A maioria dos designers visuais usa pontos para definir tamanhos de fonte no mundo real, bem como seus programas de design. Há cerca de 2835 pontos (2, 834.645666399962) em 1 metro. Com base na conversão do sistema de ponto para 1 medidor e tamanho de fonte de textmesh padrão de Unity de 13, a matemática simples de 13 dividido por 2835 é igual a 0, 46 (0.004586111116 a ser exato) fornece uma boa escala padrão para começar, embora alguns possam desejar arredondar para 0, 5.

De qualquer forma, dimensionar o objeto de texto ou o contêiner para esses valores não só permitirá a conversão 1:1 de tamanhos de fonte de um programa de design, mas também fornecerá um padrão para manter a consistência em todo o aplicativo ou jogo.

### <a name="ui-text"></a>Texto da interface do usuário

Ao adicionar um elemento de texto baseado na interface do usuário ou tela a uma cena, o tamanho da disparidade ainda é maior. As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de texto baseados na interface do usuário a 0, 46 (0.0004586111116 para ser exato) ou 0, 5 para o valor arredondado.

**Isenção de responsabilidade**: o valor padrão de qualquer fonte pode ser afetado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base na fonte Arial padrão no Unity, bem como uma outra fonte importada.

![Tamanho da fonte com fatores de dimensionamento](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik. passe-partout](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material para 3DTextPrefab com suporte a oclusão. Requer 3DTextShader. Shader

![Material de fonte padrão versus material de 3DTextSegoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader. Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Sombreador para 3DTextPrefab com suporte a oclusão.
