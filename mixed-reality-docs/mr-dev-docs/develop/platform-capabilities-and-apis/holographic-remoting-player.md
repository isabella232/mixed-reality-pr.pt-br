---
title: Player de Comunicação Remota Holográfica
description: saiba mais sobre o reprodutor de comunicação remota do Holographic e o conteúdo de Holographic de um PC para seu HoloLens em tempo real por Wi-Fi.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens, comunicação remota, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual, diagnóstico, desempenho
ms.openlocfilehash: f467b32ddab231286fc916916b0a40f210a66eb1
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757014"
---
# <a name="holographic-remoting-player"></a>Player de Comunicação Remota Holográfica

[Conheça os fundamentos da comunicação remota do Holographic.](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>a comunicação remota Holographic para HoloLens 2 é uma alteração de versão principal. [os aplicativos remotos para **HoloLens (1ª gen)**](add-holographic-remoting.md) devem usar NuGet pacote versão **1. x** e [aplicativos remotos para **HoloLens 2**](holographic-remoting-create-remote-wmr.md) devem usar **2. x**. x. isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com HoloLens (1ª gen) e vice-versa.

O [Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota do Holographic. o Player está disponível para HoloLens (primeira gen) e HoloLens 2.  os aplicativos de PC com suporte para comunicação remota Holographic com HoloLens precisam ser atualizados para dar suporte à comunicação remota Holographic com HoloLens 2. Entre em contato com seu provedor de aplicativos se tiver dúvidas sobre quais versões têm suporte.

>[!TIP]
>a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) , o Holographic Remoting player também está disponível para computadores Windows que executam o [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>A partir da versão [2.4.0](holographic-remoting-version-history.md#v2.4.0) , os aplicativos remotos usando a [API OpenXR](../native/openxr.md) podem ser criados. Para começar a fazer check-out, [escreva um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectando-se ao Player de comunicação remota do Holographic

Siga as instruções do aplicativo para se conectar ao Player de comunicação remota do Holographic. você precisará inserir o endereço IP do seu dispositivo HoloLens, que pode ser visto na tela principal do reprodutor de comunicação remota, da seguinte maneira:

![Player de Comunicação Remota Holográfica](images/holographicremotingplayer.png)

Sempre que vir a tela principal, você saberá que não tem um aplicativo conectado.

A conexão remota Holographic **não está criptografada**. Você sempre deve usar a comunicação remota do Holographic por meio de uma conexão segura Wi-Fi confiável.

## <a name="quality-and-performance"></a>Qualidade e desempenho

A qualidade e o desempenho da sua experiência variam com base em três fatores:
* **A experiência do Holographic que você está executando** -aplicativos que processam alta resolução ou conteúdo altamente detalhado pode exigir um PC mais rápido ou uma conexão sem fio mais rápida.
* **Hardware do seu PC** -seu PC precisa ser capaz de executar e codificar sua experiência com o holographic em 60 quadros por segundo. Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou o AMD Radeon R9 290 ou superior. Novamente, sua experiência específica pode exigir um cartão maior ou menor.
* **Sua conexão de Wi-Fi** -sua experiência com o Holographic é transmitida por Wi-Fi. Use uma rede rápida com baixo congestionamento para maximizar a qualidade. Usar um computador conectado por um cabo Ethernet, em vez de Wi-Fi, também pode melhorar a qualidade.

## <a name="diagnostics"></a>Diagnósticos

Para medir a qualidade de sua conexão, diga **"habilitar o diagnóstico"** enquanto estiver na tela principal do Holographic Remoting Player. quando os diagnósticos estiverem habilitados, em **HoloLens (primeira gen)** , o aplicativo mostrará:

* **FPS** -o número médio de quadros renderizados que o player de comunicação remota está recebendo e renderizando por segundo. O ideal é de 60 FPS.
* **Latência** -a quantidade média de tempo que leva para um quadro passar do seu PC para a HoloLens. Quanto menor for o melhor. Isso é amplamente dependente de sua rede Wi-Fi.

no **HoloLens 2** , o aplicativo mostrará:

![Diagnóstico do player de comunicação remota do Holographic](images/holographicremotingplayer-diag.png)

* **Render** -o número de quadros processados pelo Player de comunicação remota durante o último segundo. Observe que isso é independente do número de quadros que chegaram pela rede (consulte **quadros de vídeo**). O tempo Delta médio/máximo de renderização em milissegundos no último segundo entre os quadros renderizados é exibido.

* **Quadros de vídeo** -o primeiro número exibido são os quadros de vídeo ignorados, o segundo são quadros de vídeo reutilizados e o terceiro recebe quadros de vídeo. Todos os números representam a contagem no último segundo.
    * ```Received frames``` é o número de quadros de vídeo, que chegaram no último segundo. Em condições normais, isso deve ser 60, mas se não for, um indicador de que os quadros serão descartados devido a problemas de rede ou o lado remoto/remoto não produzirá quadros com a taxa esperada.
    * ```Reused frames``` é a contagem de quadros de vídeo usados mais de uma vez no último segundo. Por exemplo, se os quadros de vídeo chegarem atrasados, o loop de renderização do Player ainda renderizará um quadro, mas precisará *reutilizar* o quadro de vídeo que já foi usado para o quadro anterior.
    * ```Skipped frames``` é a contagem de quadros de vídeo, que não foram usados pelo loop de renderização do Player. Por exemplo, a tremulação de rede pode ter o efeito de que os quadros de vídeo chegando não são mais distribuídos uniformemente. Por exemplo, se alguns estiverem atrasados e outros chegarem no tempo, com o resultado, eles não terão mais um Delta de 16,66 milissegundos quando executados em 60 Hz. Pode ocorrer que mais de um quadro chega entre dois tiques do loop de renderização do Player. Nesse caso, o Player *ignora* um ou mais quadros, pois ele deve sempre exibir o quadro de vídeo mais recente recebido.

    >[!NOTE]
    >Quando voltada para a variação da rede, os quadros ignorados e reutilizados geralmente são aproximadamente os mesmos. Por outro lado, se você ver apenas os quadros ignorados, esse é um indicador de que o Player não atingiu sua taxa de quadros de destino. Nesse caso, você deve ficar atento ao tempo máximo de processamento Delta ao diagnosticar problemas.

* **Quadros de vídeo Delta** -o Delta mínimo/máximo entre quadros de vídeo recebidos no último segundo. Esse número geralmente se correlaciona com os quadros ignorados/reutilizados em caso de problemas causados pela tremulação da rede.
* **Latência** -o tempo de conclusão médio em milissegundos no último segundo. o retorno nesse contexto significa que o tempo de envio de dados de pose/sensor do HoloLens para o lado remoto/remoto até exibir o quadro de vídeo para os dados de pose/telemetria na exibição de HoloLens.
* **Quadros de vídeo descartados** -o número de quadros de vídeo descartados no último segundo e desde que uma conexão foi estabelecida. A principal causa de quadros de vídeo descartados é quando um quadro de vídeo não chega na ordem e, por esse motivo, precisa ser descartado, pois já existe um mais recente. Isso é semelhante a *quadros descartados* , mas a causa está em um nível inferior na pilha de comunicação remota. Os quadros de vídeo descartados só são esperados em condições de rede inadequadas.

Na tela principal, você pode dizer **"desabilitar o diagnóstico"** para desativar o diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos do sistema do PC
* seu computador **deve** estar executando a atualização Windows 10 aniversário ou mais recente.
* Recomendamos uma placa gráfica GeForce GTX 970 ou AMD Radeon R9 290 ou superior.
* Recomendamos que você conecte seu PC à sua rede por meio de Ethernet para reduzir o número de saltos sem fio.

## <a name="see-also"></a>Consulte Também
* [HoloLens (primeira gen): adicionar comunicação remota do Holographic](add-holographic-remoting.md)
* [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)