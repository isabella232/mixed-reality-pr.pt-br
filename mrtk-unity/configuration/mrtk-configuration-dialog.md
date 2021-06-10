---
title: Caixa de diálogo de configuração do MRTK
description: Configurar o MRTK no projeto do Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345089"
---
# <a name="mrtk-project-configuration-dialog"></a>Caixa de diálogo configuração do projeto MRTK

A caixa de diálogo configuração do MRTK é exibida quando o Unity carrega um projeto e é determinado que uma ou mais opções de configuração precisam da atenção do desenvolvedor.

![Aplicar ignorar mais tarde](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Para aplicar as alterações, clique no botão **aplicar** . O botão **posterior** adiará as alterações até que o projeto seja recarregado em um momento futuro.

> [!NOTE]
> A caixa de diálogo de configuração reaparecerá se uma ou mais das configurações recomendadas forem deixadas desmarcadas. Para evitar que isso ocorra, aplique as opções desejadas e reinicie a caixa de diálogo por meio de utilitários do **Kit de ferramentas da realidade misturados**  >    >  **Configurar o projeto do Unity** e clique em **ignorar**. Isso impedirá que a caixa de diálogo de configuração reapareça automaticamente.

## <a name="common-settings"></a>Configurações padrão

Todos os destinos de compilação compartilham uma coleção de opções comuns.

![Configurações Comuns](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forçar a serialização de ativos de texto e habilitar os metadados visíveis

Essas configurações ajudam a simplificar o trabalho com projetos do Unity e sistemas de controle do código-fonte (por exemplo: git).

### <a name="enable-vr-supported"></a>Habilitar VR com suporte

**Unity 2018**

Configura a realidade virtual com suporte e as opções do SDK da realidade virtual nas **configurações do Player**  >  **XR Settings**.

### <a name="set-single-pass-instanced-rendering-path"></a>Definir caminho de renderização da instância única Pass

Define as configurações do **Player**  >  **XR Settings**  >  **modo de renderização estéreo** para **passagem única instância**.

### <a name="set-default-spatial-awareness-layer"></a>Definir camada de reconhecimento espacial padrão

Registra o reconhecimento espacial como a camada 31 para habilitar a configuração fácil e consistente das opções Raycast e física.

### <a name="audio-spatializer"></a>Spatializer de áudio

Os spatializers de áudio são os componentes que desbloqueiam o poder do som espacial e do áudio posicional para tornar as experiências de realidade misturadas verdadeiramente imersivas.

> [!NOTE]
> Definir o áudio spatializer como nenhum desabilitará os recursos de áudio posicional.

#### <a name="common-spatializers"></a>Spatializers comuns

- Spatializer Microsoft

A Microsoft forneceu spatializer que dá suporte à utilização de aceleração de hardware no HoloLens 2.

Esse spatializer está disponível por meio do [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e do [GitHub](https://github.com/microsoft/spatialaudio-unity).

Mais detalhes sobre o Microsoft Spatializer podem ser encontrados na [documentação de som espacial](/windows/mixed-reality/spatial-sound-in-unity).

- Spatializer MS HRTF

Microsoft Windows spatializer que é fornecido pelo Unity como parte dos pacotes da plataforma Windows Mixed e da realidade do Windows XR.

- Áudio Resonance

Um spatializer de plataforma cruzada do Google fornecido pelo Unity.

Mais informações podem ser encontradas no site de [documentação de áudio do resonance](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .

## <a name="universal-windows-platform-settings"></a>Configurações de Plataforma Universal do Windows

![Configurações de UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Recursos de UWP

Habilita recursos de aplicativo específicos para Plataforma Universal do Windows aplicativo. Esses recursos permitem que a plataforma informe e solicite permissão para habilitar a funcionalidade específica.

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

Na versão mais recente do Unity 2019, quando "trabalhos gráficos" estiver habilitado, o aplicativo falhará quando for implantado em um HoloLens 2.
Essa configuração é habilitada por padrão no Unity-enquanto esse bug existe (consulte o [bug do Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), o configurador usará como padrão a definição de trabalhos gráficos como ' false ' (permitindo que os aplicativos implantados no HoloLens 2 não falhem).

## <a name="android-settings"></a>Configurações do Android

Definições de configuração para dar suporte a aplicativos AR em dispositivos com Android.

![Configurações do Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Desabilitar renderização multi-threaded

Desabilita **as configurações do Player**  >  **outras configurações**  >  **renderização multi-threaded** conforme exigido pelo suporte a ar do Android.

### <a name="set-minimum-api-level"></a>Definir nível mínimo de API

Define o valor das **configurações do Player**  >  **outras configurações**  >  **nível mínimo de API** para impor os requisitos do sistema operacional para aplicativos ar.

## <a name="ios-settings"></a>Configurações do iOS

Definições de configuração para dar suporte a aplicativos AR em dispositivos com iOS.

![Configurações do iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Definir versão do sistema operacional necessária

Define o valor das **configurações do Player**  >  **outras configurações** de  >  **destino versão mínima do IOS** para impor os requisitos do sistema operacional para aplicativos ar.

### <a name="set-required-architecture"></a>Definir a arquitetura necessária

Define o valor das **configurações do Player**  >  **outra**  >  **arquitetura** de configurações para impor os requisitos de plataforma para aplicativos ar.

### <a name="set-camera-usage-descriptions"></a>Definir descrições de uso da câmera

Define o valor das **configurações do Player**  >  **outras configurações**  >  **Descrição uso da câmera** usada para solicitar permissão para usar a câmera do dispositivo.