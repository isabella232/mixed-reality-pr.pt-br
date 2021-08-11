---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: c50be323bac18984e735517f85724fb087e76cbf0ae8a6ccde6b44c460ef0b8e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203348"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Como empacotar e implantar no dispositivo ou emulador

No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela. Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador. Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo. Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador. Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.

## <a name="objectives"></a>Objetivos

* [Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo
* Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2

## <a name="device-only-streaming"></a>[Somente para dispositivo] Streaming

[Comunicação remota holográfica](/windows/mixed-reality/add-holographic-remoting) significa transmitir dados de um PC ou um dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal. Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo novamente para o HoloLens por Wi-Fi. O streaming permite que você adicione exibições imersivas remotas a um programa de software de PC desktop existente e tenha acesso a mais recursos do sistema.

Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:

1.  Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo. Anote o endereço IP exibido no aplicativo.
    * Acesse **Editar > Configurações de Projeto** e verifique se o **RHI Padrão** do Windows está definido como **Padrão** ou **D3D11**:

![RHI Padrão](../images/unreal/performance-recommendations-img-09.png)

2.  De volta no editor do Unreal, acesse **Editar > Configurações do Projeto** e marque **Habilitar a Comunicação Remota** na seção **Abrir Comunicação Remota do XR Holographic**.

3.  Reinicie o editor e insira o endereço IP do dispositivo (conforme exibido no aplicativo Player de Comunicação Remota do Holographic) e clique em **Conectar**.

Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**. O aplicativo será executado na janela de Visualização de VR, que é transmitida para o headset do HoloLens.

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>Empacotar e implantar o aplicativo por meio do portal do dispositivo

>[!NOTE]
>Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.
>- Vá para **Preferências do Editor > Geral > Código-Fonte > Editor de Código-Fonte** e verifique se o Visual Studio 2019 está selecionado.
>- Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**.
>- Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.
>![Alterar a plataforma de destino nas configurações do projeto](images/unreal-uxt/6-installationoptions.PNG)

1.  Acesse **Editar > Configurações do Projeto**.
    * Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto.
    * Adicione **CN=NomeDaSuaEmpresa** em **Projeto > Descrição > Editor > Nome Diferenciado da Empresa**.
    * Selecione **Iniciar em VR** em **Projeto > Descrição > Configurações**.

> [!IMPORTANT]
> Se você deixar um desses campos em branco, isso resultará em um erro quando você tentar e gerar um novo certificado na etapa 3.

> [!IMPORTANT]
> O nome do editor precisa estar no [Formato de Nomes Diferenciados LADPv3](https://www.ietf.org/rfc/rfc2253.txt). Um nome malformado do editor gera o erro "Chave de assinatura não encontrada. Não foi possível assinar o aplicativo digitalmente." durante o empacotamento.

> [!IMPORTANT]
> Se você não selecionar "Iniciar em VR", o aplicativo tentará iniciar em um slate

![Configurações do projeto – descrição](images/unreal-uxt/6-cn-new.PNG)

2.  Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.

3.  Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Autenticação**).

> [!IMPORTANT]
> Se você está usando um certificado que já foi gerado, o nome do editor do certificado precisa ser igual ao nome do editor do aplicativo. Caso contrário, isso gera o erro "Chave de assinatura não encontrada. Não foi possível assinar o aplicativo digitalmente." erro.

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Clique em **Nenhum** para fins de teste quando precisar criar uma senha da chave privada.

![Como gerar um novo certificado](images/unreal-uxt/6-private-key-testing.png)

5. Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.
    * Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.

6.  Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.

7.  Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**.

    * Marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura** se você está instalando o aplicativo no seu dispositivo pela primeira vez.
    * Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados: **arm64** para dispositivo e **x64** para emulador. Encontre os arquivos no **HoloLens**, dentro da pasta em que você salvou o pacote.

8.  Clique em **Instalar**
    * Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**. 

Parabéns! Seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso. No entanto, esse não é o final da estrada. O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR. Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](/windows/mixed-reality/unreal-development-overview).

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Entrada por foco](../unreal-gaze-input.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](../unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](../unreal-development-overview.md#2-core-building-blocks) a qualquer momento.