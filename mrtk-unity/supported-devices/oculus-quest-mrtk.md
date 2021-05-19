---
title: MRTK de solicitação Oculus
description: Documentação para configurar o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Oculus Quest,
ms.openlocfilehash: c0eccd0b366d39529eafc51d23031fc30144b1ae
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143968"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a>Como configurar o Oculus Quest no MRTK usando o pipeline do SDK do XR

Uma [Quest Oculus](https://www.oculus.com/quest/) é necessária.

O suporte do MRTK para o Oculus Quest é fornecido por meio de duas fontes diferentes, o pipeline XR do Unity e o pacote do Oculus Integration Unity. O **OCULUS XRSDK provedor de dados** permite o uso de ambas as fontes e deve ser usado para usar o MRTK no Oculus Quest.

O [pipeline XR do Unity](https://docs.unity3d.com/Manual/XR.html) permite o uso de controladores de toque Oculus e acompanhamento de cabeçalho com o Oculus Quest.
Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019,3 e posterior. Para usar esse pipeline, certifique-se de usar o **Unity 2019,3 ou mais recente**.

O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do **acompanhamento manual** com o Oculus Quest.
Este provedor de dados **não usa o** pipeline **XR** do Unity ou o **tubulator XR herdado**, mas como os controladores e Headtracking são tratados pelo pipeline XR do Unity, as etapas na **configuração do projeto para o Oculus Quest** devem ser seguidas para garantir que você esteja usando o **pipeline XR** e não o pipeline de @ **Legacy herdado** a ser preterido.

## <a name="setting-up-project-for-the-oculus-quest"></a>Configurando o projeto para o Oculus Quest

1. Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.

1. Verifique se o [modo de desenvolvedor](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) está habilitado em seu dispositivo. A instalação dos drivers Oculus ADB é opcional.

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>Configurando o pipeline XR para Oculus Quest

1. Verifique se o **plug-in OCULUS XR** está instalado na **janela--> Package Manager**

    ![Pacote de plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Verifique se o provedor de plug-in do Oculus está incluído no seu projeto acessando **Editar--> configurações do projeto--> o gerenciamento de plug-ins do XR--provedores de plug-in do >**

    ![Provedor de plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configurando o pacote do Unity de Integração do Oculus para habilitar o retrocesso

1. Baixe e importe a [Integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do Unity Asset Store. A versão mais recente testada para funcionar é a 20.0.0. Versões mais antigas podem ser encontradas neste [arquivo](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Navegue até Kit de Ferramentas de Realidade Misturada > utilitários > Oculus > integrar módulos do Unity de integração do Oculus. Isso atualizará as asmdefs com definições e referências necessárias para que o código relevante do Oculus Quest funcione. Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de Integração do Oculus. O repo do MRTK contém um arquivo csc que converte avisos em erros; essa conversão interrompe o processo MRTK-Quest configuração.

    ![Asmdef de integração do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Na pasta Oculus importada (deve ser encontrada em Ativos/Oculus), há um objeto que pode ser script chamado OculusProjectConfig. Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "Controladores e Mãos".

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configurando a cena

1. Criar uma nova cena do Unity ou abrir uma cena pré-existente, como HandInteractionExamples
1. Adicione o MRTK à cena navegando até Kit de Ferramentas de **Realidade** Misturada  >  **Adicionar à Cena e Configurar**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Usando o SDK do Oculus XR Provedor de Dados

1. Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**
    - Se não pretende modificar os perfis de configuração
        - Altere seu perfil para DefaultXRSDKConfigurationProfile e vá para Criar e implantar seu [projeto no OculusNix](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - Caso contrário, siga o seguinte:
        - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - Selecionar o perfil de configuração de **entrada**

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.  Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. O SDK do Oculus XR Provedor de Dados inclui um Rig da câmera OVR pré-fabricado que configura automaticamente o projeto com um dispositivo de câmera OVR e as mãos de OVR para rotear corretamente a entrada. Adicionar manualmente um Rig da câmera OVR à cena exigirá a configuração manual de configurações e de entrada.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Criar e implantar seu projeto no Oculus Quest

1. Conecte seu Oculus Quest por meio de um cabo USB 3,0-> USB C
1. Navegue até o **arquivo > configurações de Build**
1. Alterar a implantação para **Android**
1. Verifique se a Quest Oculus está selecionada como o dispositivo de execução aplicável

    ![Oculus executar dispositivo](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Selecione compilar e executar
    - Você provavelmente encontrará o seguinte conjunto de erros de compilação ao selecionar *Compilar e executar* a primeira vez. Você deve ser capaz de implantar com êxito ao selecionar *Compilar e executar* novamente.

    ![Oculus erros de compilação esperados](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Aceite o prompt _permitir depuração de USB_ de dentro do Quest
1. Veja sua cena dentro do Oculus Quest

## <a name="removing-oculus-integration-from-the-project"></a>Removendo a integração do Oculus do projeto

1. Navegue até o kit de ferramentas de realidade misturada > Oculus > módulos de integração do Oculus separados  ![ Oculus separação Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Permitir que o Unity atualize como referências no Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e outros arquivos sejam modificados nesta etapa
1. Fechar o Unity
1. Feche o Visual Studio, se ele estiver aberto
1. Abra o explorador de arquivos e navegue até a raiz do projeto do MRTK Unity
1. Excluir o diretório de UnityProjectName/biblioteca
1. Excluir o diretório UnityProjectName/assets/Oculus
1. Excluir o arquivo UnityProjectName/assets/Oculus. meta
1. Reabrir o Unity

## <a name="common-errors"></a>Erros comuns

### <a name="quest-not-recognized-by-unity"></a>Quest não reconhecida pelo Unity

Verifique se os caminhos do Android estão configurados corretamente. Se você continuar a encontrar problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Editar preferências de > > ferramentas externas > Android**

![Configuração de ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
