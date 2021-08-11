---
title: Caixa de diálogo de configuração do MRTK
description: Configurar o MRTK no Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Unity
ms.openlocfilehash: c2ee07ee061eb66aef58e28b2d893f6902775e77d4aa2f77039fd422fa01d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219000"
---
# <a name="mrtk-configuration-dialog"></a>Caixa de diálogo de configuração do MRTK

A caixa de diálogo configuração do MRTK é exibida quando o Unity carrega um projeto e é determinado que uma ou mais opções de configuração precisam da atenção do desenvolvedor.

![Aplicar ignorar mais tarde](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Para aplicar as alterações, clique no botão **aplicar** . O botão **posterior** adiará as alterações até que o projeto seja recarregado em um momento futuro.

> [!NOTE]
> A caixa de diálogo de configuração reaparecerá se uma ou mais das configurações recomendadas forem deixadas desmarcadas. para evitar que isso ocorra, aplique as opções desejadas e reinicie a caixa de diálogo por meio da **realidade misturada Toolkit**  >  **utilitários**  >  **Configure o Unity Project** e clique em **ignorar**. Isso impedirá que a caixa de diálogo de configuração reapareça automaticamente.

## <a name="common-settings"></a>Configurações padrão

Todos os destinos de compilação compartilham uma coleção de opções comuns.

![Configurações Comuns](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forçar a serialização de ativos de texto e habilitar os metadados visíveis

Essas configurações ajudam a simplificar o trabalho com projetos do Unity e sistemas de controle do código-fonte (por exemplo: git).

### <a name="enable-vr-supported"></a>Habilitar VR com suporte

**Unity 2018**

configura a realidade virtual com suporte e as opções do SDK da realidade virtual no **Player Configurações**  >  **XR Configurações**.

### <a name="set-single-pass-instanced-rendering-path"></a>Definir caminho de renderização da instância única Pass

configura o modo de renderização estéreo do **Player Configurações**  >  **XR Configurações**  >   para **passagem única em instância**.

### <a name="set-default-spatial-awareness-layer"></a>Definir camada de reconhecimento espacial padrão

Registra o reconhecimento espacial como a camada 31 para habilitar a configuração fácil e consistente das opções Raycast e física.

### <a name="audio-spatializer"></a>Spatializer de áudio

Os spatializers de áudio são os componentes que desbloqueiam o poder do som espacial e do áudio posicional para tornar as experiências de realidade misturadas verdadeiramente imersivas.

> [!NOTE]
> Definir o áudio spatializer como nenhum desabilitará os recursos de áudio posicional.

#### <a name="common-spatializers"></a>Spatializers comuns

- Spatializer Microsoft

a Microsoft forneceu spatializer que dá suporte à utilização de aceleração de hardware no HoloLens 2.

esse spatializer está disponível por meio de [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).

Mais detalhes sobre o Microsoft Spatializer podem ser encontrados na [documentação de som espacial](/windows/mixed-reality/spatial-sound-in-unity).

- Spatializer MS HRTF

o Microsoft Windows spatializer fornecido pelo Unity como parte dos pacotes de plataforma Windows Mixed Reality e Windows XR.

- Áudio Resonance

Um spatializer de plataforma cruzada do Google fornecido pelo Unity.

Mais informações podem ser encontradas no site de [documentação de áudio do resonance](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .

## <a name="universal-windows-platform-settings"></a>configurações de Plataforma Universal do Windows

![Configurações UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Recursos de UWP

habilita recursos de aplicativo específicos para Plataforma Universal do Windows aplicativo. Esses recursos permitem que a plataforma informe e solicite permissão para habilitar a funcionalidade específica.

- Microfone

  Habilita a captura de som por meio do microfone.

- Cliente de Internet

  Habilita o suporte para acessar recursos na Internet.

- Percepção Espacial

  Habilita o suporte para o uso do ambiente do mundo real.

- Olhar de olho

  **Unity 2019,3 e mais recente**

  Habilita o suporte para controlar o olhar de olhos do usuário.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Evitar falha do Unity ' PlayerSettings. graphicsJob '

**Unity 2019,3 e mais recente**

na versão mais recente do Unity 2019, quando "trabalhos gráficos" estiver habilitado, o aplicativo falhará quando for implantado em um HoloLens 2.
essa configuração é habilitada por padrão no Unity-enquanto esse bug existe (consulte o [bug do unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), o configurador usará como padrão a definição de trabalhos gráficos como ' false ' (permitindo assim que os aplicativos implantados no HoloLens 2 não falhem).

## <a name="android-settings"></a>Configurações do Android

Definições de configuração para dar suporte a aplicativos AR em dispositivos com Android.

![Configurações Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Desabilitar renderização multi-threaded

desabilita o **Player Configurações**  >  **outro Configurações**  >  **renderização multi-threaded** , conforme exigido pelo suporte a AR do Android.

### <a name="set-minimum-api-level"></a>Definir nível mínimo de API

define o valor do **Player Configurações**  >  **outro Configurações**  >  **nível de API mínimo** para impor os requisitos do sistema operacional para aplicativos AR.

## <a name="ios-settings"></a>Configurações do iOS

Definições de configuração para dar suporte a aplicativos AR em dispositivos com iOS.

![Configurações do iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Definir versão do sistema operacional necessária

define o valor do **Player Configurações**  >  **outro Configurações**  >  **versão mínima do iOS de destino** para impor os requisitos do sistema operacional para aplicativos AR.

### <a name="set-required-architecture"></a>Definir a arquitetura necessária

define o valor do **Player Configurações**  >  **outra**  >  **arquitetura** de Configurações para impor os requisitos de plataforma para aplicativos AR.

### <a name="set-camera-usage-descriptions"></a>Definir descrições de uso da câmera

define o valor do **Player Configurações**  >  **outro Configurações**  >  **descrição de uso da câmera** usada para solicitar permissão para usar a câmera do dispositivo.
