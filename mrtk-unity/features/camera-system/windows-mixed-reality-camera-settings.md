---
title: Configurações da câmera do Windows Mixed Reality
description: Documentação para usar Windows Mixed Reality configurações de câmera no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212678"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality de configurações da câmera

O Windows Mixed Reality de configurações da câmera de segurança determina o tipo de dispositivo no qual o aplicativo está em execução e aplica as definições de configuração apropriadas com base na exibição (transparente ou opaca).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Habilitando o provedor Windows Mixed Reality configurações da câmera

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Navegue pelo painel Inspetor até a seção sistema de câmeras e expanda a seção **Provedores Configurações câmera.**

    ![Expandir provedores de configurações](../images/camera-system/ExpandProviders.png)

3. Clique **em Adicionar Provedor Configurações Câmera e** expanda a entrada Novas **configurações de câmera recém-adicionada.**

    ![Expandir novo provedor de configurações](../images/camera-system/ExpandNewProvider.png)

4. Selecione o provedor Windows Mixed Reality câmera Configurações câmera

    ![Selecione Windows Mixed Reality de configurações](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Ao usar os perfis padrão do Microsoft Mixed Reality Toolkit, o provedor Windows Mixed Reality configurações de câmera já estará habilitado e configurado.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Configurando o provedor Windows Mixed Reality configurações da câmera

O Windows Mixed Reality câmera Configurações também dá suporte a um perfil. Esse perfil fornece as seguintes opções:

![Windows Mixed Reality configuração da câmera](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Renderizar a captura de realidade misturada da câmera de foto/vídeo

Com essa configuração no HoloLens 2, você pode habilitar o alinhamento do holograma em suas capturas de realidade misturada. Se habilitada, a plataforma fornecerá um HolographicCamera adicional ao aplicativo quando uma foto ou vídeo de captura de realidade misturada for tirado. Esse HolographicCamera fornece matrizes de exibição correspondentes ao local da câmera de foto/vídeo e fornece matrizes de projeção usando o campo de exibição da câmera de foto/vídeo. Isso garantirá que os hologramas, como malhas de mão, permaneçam visivelmente alinhados na saída do vídeo.

### <a name="hololens-2-reprojection-method"></a>HoloLens método de reprojeção 2

Define o método inicial para HoloLens reprodução 2. A recomendação padrão é usar a reprojetação de profundidade, pois todas as partes da cena serão estabilizadas de forma independente com base na distância do usuário. Se os hologramas ainda aparecerem instável, tente garantir que todos os objetos tenham enviado corretamente sua profundidade para o buffer de profundidade. Às vezes, essa é uma configuração de sombreador. Se a profundidade parecer ser enviada corretamente e a instabilidade ainda estiver presente, tente a estabilização autoplanar, que usa o buffer de profundidade para calcular um plano de estabilização. Se um aplicativo não puder enviar dados de profundidade suficientes para que qualquer uma dessas opções seja acessível, a reprojeção planar será fornecida como um fallback. Esse método será baseado nos dados de ponto de foco fornecidos por um aplicativo por meio [de SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)

Para atualizar o método de reprojeção em runtime, acesse `WindowsMixedRealityReprojectionUpdater` da mesma forma:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Isso só precisa ser atualizado uma vez e o valor é reutilizado para todos os quadros subsequentes. Se o método for atualizado com frequência, é recomendável armazenar em cache o resultado de em vez `EnsureComponent` de chamá-lo com frequência.

## <a name="see-also"></a>Confira também

- [Visão geral do sistema de câmeras](camera-system-overview.md)
- [Criando um provedor de Configurações câmera](create-settings-provider.md)
- [Renderização Captura de Realidade Misturada da câmera PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Reprodução holográfica](/windows/mixed-reality/hologram-stability#reprojection)