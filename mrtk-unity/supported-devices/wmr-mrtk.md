---
title: implantando em fones de ouvido HoloLens e WMR
description: Documentação sobre build e implantação de aplicativos em vários dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176368"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>implantando em fones de ouvido HoloLens e WMR

há duas maneiras de implantar aplicativos criados com o MRTK em seu dispositivo windows, a UWP (universal Windows platform) e a plataforma autônoma. os aplicativos criados para HoloLens 1 ou HoloLens 2 devem ter como alvo o uwp, enquanto os aplicativos criados para fones de ouvido WMR podem se concentrar em uwp ou autônomos.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>criando e implantando MRTK para HoloLens 1, HoloLens 2 e WMR headsets (UWP)

as instruções sobre como criar e implantar para o **HoloLens 1** e o **HoloLens 2** (UWP) podem ser encontradas em [criando seu aplicativo para o dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Essas etapas também permitem que você implante em **headsets WMR**.

> [!NOTE]
> ao implantar seu aplicativo em seu dispositivo no Visual Studio, você precisa configurar Visual Studio um pouco diferente dependendo do dispositivo. As configurações são as seguintes
>
>| Plataforma | Configuração | Arquitetura | Destino |
|---|---|---|---|
| HoloLens 2 | Lançamento ou mestre | ARM64 | Dispositivo |
| HoloLens 1 | Lançamento ou mestre | x86 | Dispositivo |
| Headsets WMR | Lançamento ou mestre | x64 | Computador Local |

**Dica:** ao compilar para HoloLens 1, HoloLens 2 ou WMR, é recomendável que as configurações de compilação "versão do SDK de destino" e "versão mínima da plataforma" tenham a seguinte aparência na imagem abaixo:

![Janela de build](../features/images/getting-started/BuildWindow.png)

As outras configurações podem ser diferentes (por exemplo, Configuração de Build/Arquitetura/Tipo de Build e outras sempre podem ser alteradas na solução do Visual Studio).

Verifique se a lista suspensa "Versão do SDK de Destino" inclui a opção "10.0.18362.0". Se isso estiver ausente, [o último SDK do Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) precisará ser instalado.

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 e HoloLens

se um aplicativo HoloLens aparecer como um painel 2d no dispositivo, verifique se as configurações a seguir foram configuradas no Unity antes de implantar seu aplicativo UWP:

Se estiver usando o suporte interno do XR herdado (somente Unity 2019):

1. Acesse Editar > Configurações do Projeto, Player
1. Em **Configurações de XR** na guia UWP, verifique se a opção **Realidade Virtual Compatível** está habilitada e se o SDK do **Windows Mixed Reality** foi adicionado aos SDKs.
1. Build e implantação no Visual Studio

se estiver usando os plug-ins OpenXR ou Windows XR:

1. Siga as etapas encontradas em [Introdução ao XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Verifique se o perfil de configuração é o **DefaultXRSDKConfigurationProfile**
1. Acesse **Editar > Configurações de Projeto, Gerenciamento do Plug-in de XR** e verifique se o **Windows Mixed Reality** está habilitado.
1. Build e implantação no Visual Studio

>[!IMPORTANT]
> Se você estiver usando o Unity 2019.3.x, selecione **ARM64** e não **ARM** como a arquitetura de build no Visual Studio. Com as configurações padrão do Unity no Unity 2019.3.x, um aplicativo do Unity não será implantado em um HoloLens se o ARM for selecionado devido a um bug do Unity.
>
> Se a arquitetura do ARM for necessária, acesse **Editar > Configurações de Projeto, Player** e, no menu **Outras Configurações**, desabilite **Trabalhos Gráficos**. A desabilitação de **Trabalhos Gráficos** permitirá que o aplicativo seja implantado com a arquitetura de build do ARM para o Unity 2019.3.x, mas o ARM64 é recomendado.
>
> Esse problema foi corrigido no Unity 2019,4 e no Unity 2020,3.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Criando e implantando MRTK em headsets WMR (autônomos)

Compilações autônomas de MRTK podem ser usadas em headsets WMR. Um build autônomo para um headset do WMR exige as seguintes etapas extras:

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
