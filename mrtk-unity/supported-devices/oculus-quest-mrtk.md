---
title: Criando e implantando no Oculus Quest
description: Documentação para configurar o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Oculus Quest
ms.openlocfilehash: 96b4b5b8a68c3b61d54b6796ba01c9e2516ba959
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449755"
---
# <a name="building-and-deploying-to-oculus-quest-using-the-xr-sdk-pipeline"></a>Criando e implantando no Oculus Quest usando o pipeline do SDK do XR

Uma [Quest Oculus](https://www.oculus.com/quest/) é necessária.

O suporte do MRTK para o Oculus Quest é fornecido por meio de duas fontes diferentes, o pipeline do SDK XR do Unity e o pacote do Oculus Integration Unity. O **OCULUS XRSDK provedor de dados** permite o uso de ambas as fontes e deve ser usado para implantar MRTK no Oculus Quest.

O [pipeline do SDK do Unity XR](https://docs.unity3d.com/Manual/XR.html) permite o uso de controladores de toque Oculus e acompanhamento de cabeçalho com o Oculus Quest.
Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019,3 e posterior. Para usar esse pipeline, certifique-se de usar o **Unity 2019,3 ou mais recente**. Isso é **necessário** para implantar aplicativos MRTK no Oculus Quest.

O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do **acompanhamento manual** com o Oculus Quest. Este provedor de dados **não usa o** **pipeline do SDK XR** do Unity ou o **pipeline XR herdado**.

## <a name="setting-up-project-for-the-oculus-quest"></a>Configurando o projeto para o Oculus Quest

1. Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.

1. Verifique se o [modo de desenvolvedor](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) está habilitado em seu dispositivo. A instalação dos drivers Oculus ADB é opcional.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Configurando o pipeline do SDK do XR para Oculus Quest

1. Verifique se o **plug-in OCULUS XR** está instalado na **janela--> Package Manager**

    ![Pacote de plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Verifique se o provedor de plug-in do Oculus está incluído no seu projeto acessando **Editar--> configurações do projeto--> o gerenciamento de plug-ins do XR--provedores de plug-in do >**

    ![Provedor de plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configurando o pacote do Oculus Integration Unity para habilitar o handtracking

1. Baixe e importe a [integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do repositório de ativos do Unity. A versão mais recente testada para o trabalho é 20.0.0. Versões mais antigas podem ser encontradas neste [arquivo morto](https://developer.oculus.com/downloads/package/unity-integration-archive/).

1. Navegue até Mixed Reality Toolkit > Utilities > Oculus > integrar módulos do Oculus Integration Unity. Isso atualizará o asmdefs com definições e referências necessárias para que o código relevante da Quest Oculus funcione. Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de integração do Oculus. O repositório MRTK contém um arquivo csc que converte avisos em erros, essa conversão interrompe o processo de configuração MRTK-Quest.

    ![Integração do Oculus Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Na pasta importada oculus (ela deve ser encontrada em assets/Oculus), há um objeto programável chamado OculusProjectConfig. Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "controladores e mãos".

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configurando a cena

1. Crie uma nova cena do Unity ou abra uma cena já existente como HandInteractionExamples.
1. Adicione MRTK à cena navegando até **Mixed Reality Toolkit**  >  **Adicionar à cena e configurar**.

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Usando o SDK do Oculus XR Provedor de Dados

::: moniker range=">= mrtkunity-2021-05"

1. Configurar seu perfil para usar o **SDK do OCULUS XR provedor de dados**
    - Se não pretende modificar os perfis de configuração
        - Use qualquer um dos perfis de MRTK padrão, que são todos configurados nos pipelines XR do Unity. O DefaultXRSDKConfigurationProfile anterior agora está rotulado como obsoleto.
        - Vá para [Compilar e implantar seu projeto no Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).
    - Caso contrário, siga o seguinte:
        - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - Selecione o perfil de configuração de **entrada** .

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.  Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. Configurar seu perfil para usar o **SDK do OCULUS XR provedor de dados**
    - Se não pretende modificar os perfis de configuração
        - Altere seu perfil para DefaultXRSDKConfigurationProfile.
        - Vá para [Compilar e implantar seu projeto no Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).
    - Caso contrário, siga o seguinte:
        - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - Selecione o perfil de configuração de **entrada** .

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.  Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

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
