---
title: Streaming no Unreal
description: Saiba como transmitir seus aplicativos Unreal para o HoloLens 2, incluindo opções de linha de comando e limitações de streaming.
author: sw5813
ms.author: v-vtieto
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, streaming, PC, comunicação remota do aplicativo holográfico, player de comunicação remota holográfica, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 091f0876c37756fad47d2d78520adbd526aab24d
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184612"
---
# <a name="streaming-in-unreal"></a>Streaming no Unreal

Às vezes, "streaming" é chamado de "comunicação remota holográfica". Para saber mais, confira [Visão geral de comunicação remota holográfica](../platform-capabilities-and-apis/holographic-remoting-overview.md)

O streaming de um computador para o HoloLens fornece duas vantagens principais: 
* Ele permite que o aplicativo de realidade misturada aproveite a capacidade computacional dos computadores. 
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

> [!NOTE]
> Se o acompanhamento ocular não estiver funcionando ao transmitir de um executável empacotado, desabilite os outros plug-ins com rastreadores oculares com suporte para PC (exemplo: Magic Leap) ou execute o aplicativo na linha de comando com o argumento de acompanhamento ocular relevante (confira [opções de linha de comando](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unreal/unreal-streaming?tabs=wmr#command-line-options)).

Pressione ENTER e veja seu aplicativo começar a ser transmitido.

### <a name="command-line-options"></a>Opções de linha de comando

Outras opções de linha de comando para streaming em cada plataforma no Unreal Engine 4.26+ podem ser encontradas na tabela abaixo. 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>Veja também

* [Histórico de versões do Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
