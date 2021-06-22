---
title: Criando e implantando no Android e iOS por meio do AR Foundation
description: Documentação para configurar o MRTK para Android e iOS (ARFoundation) no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449735"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a>Criando e implantando no Android e iOS por meio do AR Foundation [experimental]

## <a name="install-required-packages"></a>Instalar os pacotes necessários

1. Baixe e importe o pacote **Microsoft. MixedReality. Toolkit. Unity. Foundation** , do [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou do [Gerenciador de pacotes do Unity](../configuration/usingupm.md)

1. No Gerenciador de pacotes do Unity (UPM), instale os seguintes pacotes:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Comentários |
    | --- | --- | --- |
    | AR Foundation  <br/> Versão: 1.5.0-Preview 6 | AR Foundation  <br/> Versão: 1.5.0-Preview 6 | Para o Unity 2018,4, esse pacote é incluído como uma visualização. Para exibir o pacote: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Plug-in ARCore XR <br/> Versão: 2.1.2 | Plug-in ARKit XR <br/> Versão: 2.1.2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versão: 2.1.8 |  AR Foundation  <br/> Versão: 2.1.8 |
    | Plug-in ARCore XR <br/> Versão: 2.1.11 | Plug-in ARKit XR <br/> Versão: 2.1.9 |

    **Unity 2020.3. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versão: 3.1.3 |  AR Foundation  <br/> Versão: 4.0.12 |
    | Plug-in ARCore XR <br/> Versão: 3.1.4 | Plug-in ARKit XR <br/> Versão: 4.1.7 |

1. Atualize o MRTK UnityAR scripting define invocando o item de menu: **mixed reality > Toolkit > Utilities > UnityAR > atualizar script define**

    ![Atualizar definições de script](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Habilitando o provedor de configurações da câmera do Unity AR

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![MRTK hierarquia de cena configurada](../features/images/MRTK_ConfiguredHierarchy.png)

1. Selecione **copiar e personalizar** para clonar o perfil MRTK para habilitar a configuração personalizada.

    ![Clonar perfil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Selecione **clonar** ao lado do perfil da câmera.

    ![Clonar perfil da câmera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Navegue pelo painel Inspetor até a seção sistema de câmera e expanda a seção **provedores de configurações da câmera** .

    ![Expandir provedores de configurações](../features/images/camera-system/ExpandProviders.png)

1. Clique em **Adicionar provedor de configurações de câmera** e expanda a nova entrada de configurações de **câmera** recém-adicionada.

    ![Expandir novo provedor de configurações](../features/images/camera-system/ExpandNewProvider.png)

1. Selecione o provedor de configurações da câmera do Unity AR

    ![Selecionar provedor de configurações do Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    Para obter mais informações sobre como configurar o provedor de configurações da câmera do Unity AR: [provedor de configurações da câmera do Unity ar](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Essa instalação verifica (quando o aplicativo é iniciado) se os componentes do AR Foundation estão na cena. Caso contrário, eles serão adicionados automaticamente para que funcionem com ARCore e ARKit.
> Se você precisar definir um comportamento específico, deverá adicionar os componentes necessários por conta própria.
> Para obter mais informações sobre os componentes e a instalação do AR Foundation, consulte esta [documentação](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Criando uma cena para dispositivos Android e iOS

1. Verifique se você adicionou o provedor de configurações da câmera UnityAR à sua cena.

1. Mudar a plataforma para Android ou iOS nas configurações de Build do Unity

1. Verifique se o provedor de gerenciamento de plug-in do XR associado está habilitado

    Gerenciamento de plug-ins do iOS XR:  ![ Ios de gerenciamento de plug-in de XR](../features/images/XRManagementiOS.png)

1. Compilar e executar a cena

## <a name="see-also"></a>Confira também

- [Configurações da câmera do Unity AR](../features/camera-system/unity-ar-camera-settings.md)
