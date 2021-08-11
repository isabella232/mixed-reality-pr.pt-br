---
title: Streaming no Unreal
description: Saiba como transmitir seus aplicativos Unreal para o HoloLens 2, incluindo opções de linha de comando e limitações de streaming.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, streaming, PC, comunicação remota do aplicativo holográfico, player de comunicação remota holográfica, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 4b3be99f699c7c1d40d3ea98aacecde6f60e4d2db759448f84c820a43d89bb0a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218848"
---
# <a name="streaming-in-unreal"></a>Streaming no Unreal

O streaming de um computador para o HoloLens fornece duas vantagens principais: 
* Ele permite que o aplicativo de realidade misturada aproveite a capacidade computacional dos seus computadores. 
* Ele ajuda a acelerar o tempo de iteração do desenvolvimento. 

Para começar, baixe o [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) no seu dispositivo HoloLens. O Holographic Remoting Player permite o streaming direto do seu aplicativo para o player de comunicação remota no HoloLens por meio das seguintes fontes:

* O editor do Unreal Engine
* Um executável empacotado do Windows 

Durante o streaming, você tem acesso a quase todas as mesmas funcionalidades do HoloLens que teria ao executar um aplicativo em um dispositivo. Isso inclui o [acompanhamento da articulação da mão](unreal-hand-tracking.md), se você está usando um HoloLens 2, o [mapeamento espacial](unreal-spatial-mapping.md) e as [âncoras espaciais](unreal-spatial-anchors.md), mas exclui os recursos desta [lista](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * A qualidade de streaming é altamente dependente da força da rede Wi-Fi.
> * Todos os recursos são habilitados automaticamente para o player de comunicação remota holográfica. Se você encontrar uma funcionalidade que exija permissão de usuário (por exemplo, acompanhamento de olho) para funcionar por streaming, mas não durante a execução no dispositivo, verifique se você habilitou os recursos adequados nas configurações do seu projeto.

### <a name="streaming-limitations"></a>Limitações de streaming

As malhas de mão, a câmera do HoloLens e o teclado do sistema não estão disponíveis por streaming. Observe que a entrada de fala para aplicativos transmitidos por streaming pode ser adquirida por meio do microfone do computador em que você está fazendo streaming.

#### <a name="openxr"></a>OpenXR

O Unreal 4.26 em execução no OpenXR é compatível com streaming para as versões 2.4.0 e posteriores do Player de Comunicação Remota Holográfica. O streaming do OpenXR na versão 2.4.0 não é compatível com o mapeamento espacial e âncoras espaciais. 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origem</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Headsets imersivos</strong></td>
    </tr>
     <tr>
        <td>Editor do Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Pacote do Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming do editor do Unreal

Como desenvolvedor, você descobrirá que o streaming por meio do editor do Unreal para o dispositivo HoloLens oferece benefícios significativos durante o teste. Ou seja, você não precisa mais esperar que o aplicativo seja compilado e implantado para experimentar as atualizações.

Encontre instruções detalhadas do [streaming por meio do editor do Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) em nossa série de tutoriais.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming de um executável empacotado do Windows

No Unreal 4.25.1 em diante, você pode transmitir seu aplicativo para um dispositivo HoloLens 2 por meio de um executável empacotado do Windows: 

1. Acesse **Arquivo > Projeto de Pacote > Windows** no menu do editor. 
    * Escolha uma localização para salvar o pacote e **Selecionar Pasta**.

2. Depois que o pacote terminar de ser compilado, abra o **Holographic Remoting Player** no HoloLens 2 e anote o endereço IP. 
3. Deixe o **Holographic Remoting Player** aberto e use o prompt de linha de comando para: 
    * Executar cd no diretório local em que você salvou o pacote.
    * Digite o seguinte comando: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`

> [!NOTE]
> O nome do aplicativo nas configurações do projeto deverá ser usado automaticamente para criar o pacote do Windows. Se ele for diferente por algum motivo, use o nome do executável do Windows no prompt de comando.

Pressione ENTER e veja seu aplicativo começar a ser transmitido.

### <a name="command-line-options"></a>Opções de linha de comando

Outras opções de linha de comando para streaming em cada plataforma no Unreal Engine 4.26+ podem ser encontradas na tabela abaixo. 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>Veja também

* [Histórico de versões do Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)