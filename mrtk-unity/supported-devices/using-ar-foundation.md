---
title: Implantando no Android e iOS (AR Foundation) [experimental]
description: Documentação para configurar o MRTK para Android e iOS (ARFoundation) no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, ar Core, ar Kit, ios, ios, Android, ar Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281943"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a>Implantando no Android e iOS (AR Foundation) [experimental]

## <a name="install-required-packages"></a>Instalar os pacotes necessários

1. Baixe e importe o **Microsoft. MixedReality. Toolkit. pacote do unity. Foundation** , do [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou do [Gerenciador de Pacotes do unity](../configuration/usingupm.md)

1. no Gerenciador de Pacotes do Unity (UPM), instale os seguintes pacotes:

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

1. atualize o MRTK UnityAR scripting define invocando o item de menu: **realidade misturada > Toolkit > Utilities > UnityAR > atualizar script define**

    ![Atualizar definições de script](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Habilitando o provedor de configurações da câmera do Unity AR

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![MRTK hierarquia de cena configurada](../features/images/MRTK_ConfiguredHierarchy.png)

1. Selecione **copiar e personalizar** para clonar o perfil MRTK para habilitar a configuração personalizada.

    ![Clonar perfil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Selecione **clonar** ao lado do perfil da câmera.

    ![Clonar perfil da câmera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. navegue pelo painel inspetor até a seção sistema de câmera e expanda a seção **câmera Configurações provedores** .

    ![Expandir provedores de configurações](../features/images/camera-system/ExpandProviders.png)

1. clique em **adicionar câmera Configurações provedor** e expanda a **nova** entrada de configurações de câmera recém-adicionada.

    ![Expandir novo provedor de configurações](../features/images/camera-system/ExpandNewProvider.png)

1. selecione o provedor de Configurações da câmera do Unity AR

    ![Selecionar provedor de configurações do Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    Para obter mais informações sobre como configurar o provedor de configurações da câmera do Unity AR: [provedor de configurações da câmera do Unity ar](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Essa instalação verifica (quando o aplicativo é iniciado) se os componentes do AR Foundation estão na cena. Caso contrário, eles serão adicionados automaticamente para que funcionem com ARCore e ARKit.
> Se você precisar definir um comportamento específico, deverá adicionar os componentes necessários por conta própria.
> Para obter mais informações sobre os componentes e a instalação do AR Foundation, consulte esta [documentação](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Criando uma cena para dispositivos Android e iOS

1. verifique se você adicionou o provedor de Configurações de câmera UnityAR à sua cena.

1. alterne a plataforma para Android ou iOS no Build do Unity Configurações

1. Verifique se o provedor de gerenciamento de plug-in do XR associado está habilitado

    Gerenciamento de plug-ins do iOS XR:  ![ Ios de gerenciamento de plug-in de XR](../features/images/XRManagementiOS.png)

1. Compilar e executar a cena

## <a name="see-also"></a>Confira também

- [Configurações de câmera do Unity AR](../features/camera-system/unity-ar-camera-settings.md)
