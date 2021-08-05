---
title: Implantação no Oculus Quest
description: Documentação a ser configurada para o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Oculus Quest
ms.openlocfilehash: c5633af09cca5e8b20eb81e897ca8129fed86174e30a97f7242efde231fb7aa1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186627"
---
# <a name="deploying-to-oculus-quest"></a>Implantação no Oculus Quest

Uma [Oculus Quest](https://www.oculus.com/quest/) é necessária.

O suporte do MRTK para o Oculus Quest é feito por meio de duas fontes diferentes, o pipeline do SDK XR do Unity e o pacote do Unity de Integração do Oculus. O **Oculus XRSDK Provedor de Dados** permite o uso de ambas as fontes e deve ser usado para implantar o MRTK na Oculus Quest.

O [Pipeline do SDK](https://docs.unity3d.com/Manual/XR.html) do Unity XR permite o uso de controladores Oculus Touch e acompanhamento de cabeça com o Oculus Quest.
Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019.3 e além. Para usar esse pipeline, certifique-se de usar **o Unity 2019.3 ou mais novo.** Isso é **necessário para** implantar aplicativos MRTK no Oculus Quest.

O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do acompanhamento de **mão** com o Oculus Quest. Esse provedor de dados **NÃO usa** o Pipeline **do SDK XR do** Unity ou o Pipeline **XR herdado.**

## <a name="setting-up-project-for-the-oculus-quest"></a>Configurando o projeto para o Oculus Quest

1. Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.

1. Verifique se [o modo de](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) desenvolvedor está habilitado em seu dispositivo. Instalar os Drivers do Oculus ADB é opcional.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Configurando o pipeline do SDK do XR para o Oculus Quest

1. Verifique se o **Plug-in do Oculus XR** está instalado em **Janela --> Gerenciador de Pacotes**

    ![Pacote de plug-in do Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Certifique-se de que o Provedor de Plug-in do Oculus está incluído em seu projeto indo para **Editar --> Project Configurações --> Gerenciamento de Plug-in XR --> Provedores de Plug-in**

    ![Provedor de plug-in do Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configurando o pacote do Unity de Integração do Oculus para habilitar o retrocesso

1. Baixe e importe a [Integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do Unity Asset Store. A versão mais recente testada para funcionar é a 20.0.0. Versões mais antigas podem ser encontradas neste [arquivo](https://developer.oculus.com/downloads/package/unity-integration-archive/).

1. Navegue até Realidade Misturada Toolkit > utilitários > Oculus > integrar módulos do Unity de integração do Oculus. Isso atualizará as asmdefs com definições e referências necessárias para que o código relevante do Oculus Quest funcione. Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de Integração do Oculus. O repo do MRTK contém um arquivo csc que converte avisos em erros; essa conversão interrompe o processo MRTK-Quest configuração.

    ![Asmdef de integração do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Na pasta Oculus importada (deve ser encontrada em Ativos/Oculus), há um objeto que pode ser script chamado OculusProjectConfig. Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "Controladores e Mãos".

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configurando a cena

1. Crie uma nova cena do Unity ou abra uma cena pré-existente, como HandInteractionExamples.
1. Adicione o MRTK à cena navegando até Realidade **Misturada Toolkit**  >  **Adicionar à Cena e Configurar**.

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Usando o SDK do Oculus XR Provedor de Dados

::: moniker range=">= mrtkunity-2021-05"

1. Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**
    - Se não pretende modificar os perfis de configuração
        - Use qualquer um dos perfis padrão do MRTK, que são todos configurados nos pipelines XR do Unity. O DefaultXRSDKConfigurationProfile anterior agora é rotulado como obsoleto.
        - Vá para [Criar e implantar seu projeto no Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Caso contrário, siga o seguinte:
        - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione Copiar e **Personalizar** para clonar o perfil de realidade misturada padrão.

        ![Clonar Perfil](../images/cross-platform/CloneProfile.png)

        - Selecione o **Perfil de Configuração** de Entrada.

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Selecione **Clonar** no perfil do sistema de entrada para habilitar a modificação.

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra a **seção Provedores de** Dados de **Entrada, selecione Adicionar Provedor de Dados** na parte superior e o novo provedor de dados será adicionado ao final da lista.  Abra o novo provedor de dados e de definir **o Tipo** **como Microsoft.MixedReality.Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus Add XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**
    - Se não pretende modificar os perfis de configuração
        - Altere seu perfil para DefaultXRSDKConfigurationProfile.
        - Vá para [Criar e implantar seu projeto no Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Caso contrário, siga o seguinte:
        - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione Copiar e **Personalizar** para clonar o perfil de realidade misturada padrão.

        ![Clonar Perfil](../images/cross-platform/CloneProfile.png)

        - Selecione o **Perfil de Configuração** de Entrada.

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Selecione **Clonar** no perfil do sistema de entrada para habilitar a modificação.

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra a **seção Provedores de** Dados de **Entrada, selecione Adicionar Provedor de Dados** na parte superior e o novo provedor de dados será adicionado ao final da lista.  Abra o novo provedor de dados e de definir **o Tipo** **como Microsoft.MixedReality.Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus Add XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. O SDK do Oculus XR Provedor de Dados inclui um Pré-fab de Equipamento de Câmera OVR que configura automaticamente o projeto com um Equipamento de Câmera OVR e Mãos OVR para rotear corretamente a entrada. Adicionar manualmente um Equipamento de Câmera OVR à cena exigirá a configuração manual de configurações e de entrada.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Criar e implantar seu projeto no Oculus Quest

1. Conecte seu Oculus Quest por meio de um cabo USB 3.0 -> USB C
1. Navegue **até Arquivo > Build Configurações**
1. Alterar a implantação para **Android**
1. Verifique se o Oculus Quest está selecionado como o dispositivo de executar aplicável

    ![Executar dispositivo Oculus](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Selecione Build e Executar
    - Você provavelmente encontrará o seguinte conjunto de erros de build ao selecionar *Criar e Executar* na primeira vez. Você deve ser capaz de implantar com êxito ao selecionar *Build e Executar* novamente.

    ![Erros de build esperados do Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Aceite o _prompt Permitir Depuração USB_ de dentro da busca
1. Veja sua cena dentro do Oculus Quest

## <a name="removing-oculus-integration-from-the-project"></a>Removendo a integração do Oculus do Project

1. Navegue até a Separação do Oculus Toolkit > Oculus > Módulos separados do Oculus Integration Unity ![ asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Deixe o Unity atualizar como referências no Microsoft.MixedReality. Toolkit. Providers.Oculus.asmdef e outros arquivos são modificados nesta etapa
1. Fechar Unity
1. Feche Visual Studio, se estiver aberto
1. Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK
1. Excluir o diretório UnityProjectName/Library
1. Excluir o diretório UnityProjectName/Assets/Oculus
1. Excluir o arquivo UnityProjectName/Assets/Oculus.meta
1. Reabrir o Unity

## <a name="common-errors"></a>Erros comuns

### <a name="quest-not-recognized-by-unity"></a>Busca não reconhecida pelo Unity

Certifique-se de que os caminhos do Android estão configurados corretamente. Se você continuar encontrando problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Editar > preferências > ferramentas externas > Android**

![Configuração das Ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
