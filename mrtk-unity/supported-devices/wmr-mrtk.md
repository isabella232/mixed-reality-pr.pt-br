---
title: Implantação em headsets Hololens e WMR
description: Documentação sobre build e implantação de aplicativos em vários dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441155"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Implantação em headsets Hololens e WMR

Há duas maneiras de implantar aplicativos construídos com o MRTK em seu dispositivo Windows, a UWP (Plataforma Univeral do Windows) e a Plataforma Autônoma. Os aplicativos criado para o HoloLens 1 ou o HoloLens 2 devem ser destinados à UWP, enquanto os aplicativos criado para headsets WMR podem ser destinados a UWP ou Autônomo.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Criando e implantando o MRTK no HoloLens 1, hololens 2 e headsets WMR (UWP)

Instruções sobre como criar e implantar para **o HoloLens 1** e **o HoloLens 2** (UWP) podem ser encontradas na criação do aplicativo [para o dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Essas etapas também permitem implantar em **headsets WMR.**

> [!NOTE]
> Ao implantar seu aplicativo em seu dispositivo no Visual Studio, você precisa configurar Visual Studio de forma ligeiramente diferente, dependendo do dispositivo. As configurações são as a seguir
>
>| Plataforma | Configuração | Arquitetura | Destino |
|---|---|---|---|
| HoloLens 2 | Versão ou Mestre | ARM64 | Dispositivo |
| HoloLens 1 | Versão ou Mestre | x86 | Dispositivo |
| WMR Headsets | Versão ou Mestre | x64 | Computador Local |

**Dica:** Ao criar para o HoloLens 1, o HoloLens 2 ou o WMR, é recomendável que as configurações de build "Versão do SDK de Destino" e "Versão Mínima da Plataforma" se pareçam com a imagem abaixo:

![Janela de build](../features/images/getting-started/BuildWindow.png)

As outras configurações podem ser diferentes (por exemplo, Configuração de Build/Arquitetura/Tipo de Build e outras sempre podem ser alteradas na solução do Visual Studio).

Verifique se a lista suspensa "Versão do SDK de Destino" inclui a opção "10.0.18362.0". Se isso estiver ausente, [o último SDK do Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) precisará ser instalado.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 e HoloLens

Se um aplicativo do HoloLens aparecer como um painel 2D no dispositivo, verifique se as seguintes configurações foram definidas no Unity 2019.3.x antes de implantar seu aplicativo UWP:

Se você estiver usando o XR herdado:

1. Acesse Editar > Configurações do Projeto, Player
1. Em **Configurações de XR** na guia UWP, verifique se a opção **Realidade Virtual Compatível** está habilitada e se o SDK do **Windows Mixed Reality** foi adicionado aos SDKs.
1. Build e implantação no Visual Studio

Se você estiver usando o Plug-in de XR:

1. Siga as etapas encontradas em [Introdução ao XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Verifique se o perfil de configuração é o **DefaultXRSDKConfigurationProfile**
1. Acesse **Editar > Configurações de Projeto, Gerenciamento do Plug-in de XR** e verifique se o **Windows Mixed Reality** está habilitado.
1. Build e implantação no Visual Studio

>[!IMPORTANT]
> Se você estiver usando o Unity 2019.3.x, selecione **ARM64** e não **ARM** como a arquitetura de build no Visual Studio. Com as configurações padrão do Unity no Unity 2019.3.x, um aplicativo do Unity não será implantado em um HoloLens se o ARM for selecionado devido a um bug do Unity. Acompanhe isso no [rastreador de problemas do Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).
>
> Se a arquitetura do ARM for necessária, acesse **Editar > Configurações de Projeto, Player** e, no menu **Outras Configurações**, desabilite **Trabalhos Gráficos**. A desabilitação de **Trabalhos Gráficos** permitirá que o aplicativo seja implantado com a arquitetura de build do ARM para o Unity 2019.3.x, mas o ARM64 é recomendado.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Criando e implantando o MRTK em headsets WMR (autônomo)

Builds autônomos do MRTK podem ser usados em headsets WMR. Um build autônomo para um headset do WMR exige as seguintes etapas extras:

> [!NOTE]
> O SDK de XR do Unity também dá suporte ao WMR nativo em builds autônomos, mas não exige o plug-in do SteamVR ou do WMR. Essas etapas são necessárias para o XR herdado do Unity.

1. Instale o [Steam](https://store.steampowered.com/about/)
1. Instale o [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Instale o [Plug-in do WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Como usar o plug-in do WMR

1. Abra o Steam e procure o Plug-in do Windows Mixed Reality
    - Verifique se o SteamVR está fechado antes de iniciar o Plug-in do WMR. A inicialização do plug-in do WMR também inicia o SteamVR.
    - Verifique se o headset do WMR está conectado.

    ![Pesquisa de plug-in do WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Selecione **Iniciar** no Plug-in do Windows Mixed Reality para SteamVR.

    ![Plug-in do WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - O SteamVR e o plug-in do WMR serão iniciados e uma nova janela de status de acompanhamento do headset do WMR será exibida.
    - Para obter mais informações, acesse a [documentação do Windows Mixed Reality para Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aparência da inicialização do WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. No Unity, com a cena do MRTK aberta, acesse **Arquivo > Configurações de Build**

1. Compilar a cena
    - Selecione **Adicionar Cena Aberta**
    - Verifique se a Plataforma é **Autônomo**
    - Selecione **Compilar**
    - Escolha a localização do novo build no Explorador de Arquivos

    ![Configurações de Build para Autônomo](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Um executável do Unity será criado. Para iniciar seu aplicativo, selecione o executável do Unity no Explorador de Arquivos.

    ![Unity no Explorador de Arquivos](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Confira também

- [Suporte para Android e iOS](using-ar-foundation.md)
- [Suporte para Leap Motion](leap-motion-mrtk.md)
- [Como detectar funcionalidades de plataforma](detecting-platform-capabilities.md)