---
title: Player de Comunicação Remota Holográfica
description: Saiba mais sobre o Holographic Remoting Player e streaming de conteúdo holográfico de um computador para seu HoloLens em tempo real via Wi-Fi.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, diagnóstico, desempenho
ms.openlocfilehash: 1e286612035a34c1bac174a620c350a91eb2b0fd59c3e808fe3a99368e03f43c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217132"
---
# <a name="holographic-remoting-player"></a>Player de Comunicação Remota Holográfica

[Conheça os conceitos básicos da comunicação remota do Holographic.](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>A remoção holográfica para HoloLens 2 é uma alteração de versão principal. Os aplicativos remotos [ **para HoloLens (1ª geração)**](add-holographic-remoting.md) devem usar NuGet versão **1.x.x** e os aplicativos remotos para [HoloLens **2**](holographic-remoting-create-remote-wmr.md) devem usar **2.x.x.** Isso implica que aplicativos remotos escritos para HoloLens 2 não são compatíveis com HoloLens (1ª geração) e vice-versa.

O [Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) é um aplicativo que se conecta a aplicativos de PC e jogos que suportam a Holographic Remoting. O Player está disponível para o HoloLens (primeira geração) e HoloLens 2.  Os aplicativos de pc que suportam a HoloLens holográfico com o HoloLens precisam ser atualizados para dar suporte à remoção holográfica com HoloLens 2. Entre em contato com seu provedor de aplicativos se tiver dúvidas sobre quais versões têm suporte.

>[!TIP]
>A partir da [versão 2.2.0,](holographic-remoting-version-history.md#v2.2.0) o player de Remoção Holográfica também está disponível para PCs Windows executando [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>A partir da [versão 2.4.0,](holographic-remoting-version-history.md#v2.4.0) aplicativos remotos usando a [API openXR](../native/openxr.md) podem ser criados. Para começar, confira [Escrevendo um aplicativo remoto de remoção holográfica usando APIs openXR](holographic-remoting-create-remote-openxr.md).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectando-se ao Holographic Remoting Player

Siga as instruções do aplicativo para se conectar ao Holographic Remoting Player. Você precisará inserir o endereço IP do dispositivo HoloLens, que pode ser exibido na tela principal do Player de Remo, da seguinte forma:

![Player de Comunicação Remota Holográfica](images/holographicremotingplayer.png)

Sempre que vir a tela principal, você verá que não tem um aplicativo conectado.

A conexão de remoção holográfica **não é criptografada.** Você sempre deve usar a Holographic Remoting em uma conexão Wi-Fi segura em que confia.

## <a name="quality-and-performance"></a>Qualidade e desempenho

A qualidade e o desempenho de sua experiência variam com base em três fatores:
* **A experiência holográfica que você está executando** – Aplicativos que renderizam conteúdo altamente detalhado ou de alta resolução podem exigir um computador mais rápido ou uma conexão sem fio mais rápida.
* **Hardware do computador –** seu computador precisa ser capaz de executar e codificar sua experiência holográfica a 60 quadros por segundo. Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou AMD Radeon R9 290 ou melhor. Novamente, sua experiência específica pode exigir um cartão superior ou inferior.
* **Sua Wi-Fi de dados** – sua experiência holográfica é transmitida por Wi-Fi. Use uma rede rápida com baixo congestionamento para maximizar a qualidade. O uso de um computador conectado por um cabo Ethernet, em vez de Wi-Fi, também pode melhorar a qualidade.

## <a name="diagnostics"></a>Diagnóstico

Para medir a qualidade da conexão, diga "habilitar **diagnóstico"** na tela principal do Holographic Remoting Player. Quando o diagnóstico estiver habilitado, no **HoloLens (primeira geração),** o aplicativo mostrará:

* **FPS** – o número médio de quadros renderizados que o player de remo está recebendo e renderizar por segundo. O ideal é 60 FPS.
* **Latência** – a quantidade média de tempo que leva para que um quadro vá do computador para o HoloLens. Quanto menor, melhor. Isso depende muito da sua rede Wi-Fi rede.

No **HoloLens 2,** o aplicativo mostrará:

![Diagnóstico holográfico do player de remoção](images/holographicremotingplayer-diag.png)

* **Renderização** – o número de quadros que o player de remo renderização durante o último segundo. Observe que isso é independente do número de quadros, que chegou por meio da rede (consulte **Quadros de vídeo**). O tempo delta médio/máximo de renderização em milissegundos durante o último segundo entre quadros renderizados é exibido.

* **Quadros de vídeo** – o primeiro número exibido são quadros de vídeo ignorados, o segundo é reutilizado quadros de vídeo e o terceiro recebe quadros de vídeo. Todos os números representam a contagem no último segundo.
    * ```Received frames``` é o número de quadros de vídeo, que chegou ao último segundo. Em condições normais, isso deve ser 60, mas se não for, esse é um indicador de que os quadros são descartados devido a problemas de rede ou o lado remoto/remoto não produz quadros com a taxa esperada.
    * ```Reused frames``` é a contagem de quadros de vídeo usados mais de uma vez no último segundo. Por exemplo, se os quadros de vídeo chegam com atraso, o loop de renderização do player ainda renderiza um quadro, mas precisa *reutilizar* o quadro de vídeo que ele já usou para o quadro anterior.
    * ```Skipped frames``` é a contagem de quadros de vídeo, que não foram usados pelo loop de renderização do player. Por exemplo, a tremeia de rede pode ter o efeito de que os quadros de vídeo que chegam não são mais distribuídos uniformemente. Por exemplo, se alguns estão atrasados e outros chegam no tempo com o resultado de que eles não têm um delta de 16,66 milissegundos mais ao executar em 60 Hz. Pode ocorrer que mais de um quadro chegue entre dois tiques do loop de renderização do player. Nesse caso, o player *ignora um* ou mais quadros, pois ele deve sempre exibir o quadro de vídeo recebido mais recente.

    >[!NOTE]
    >Ao enfrentar a tremlusão de rede, quadros ignorados e reutilizados geralmente são quase os mesmos. Por outro lado, se você vir apenas quadros ignorados, esse é um indicador de que o jogador não atinge sua taxa de quadros de destino. Nesse caso, você deve ficar atento ao tempo delta de renderização máximo ao diagnosticar problemas.

* **Delta de quadros de vídeo** – o delta mínimo/máximo entre quadros de vídeo recebidos no último segundo. Esse número geralmente se correlaciona com quadros ignorados/reutilizados em caso de problemas causados pela treme de rede.
* **Latência** – a média de retorno em milissegundos ao longo do último segundo. A solução alternativa nesse contexto significa o tempo de envio de dados de pose/sensor do HoloLens para o lado remoto/remoto até exibir o quadro de vídeo para esses dados de pose/telemetria na tela HoloLens vídeo.
* **Quadros de vídeo descartados** – o número de quadros de vídeo descartados no último segundo e desde que uma conexão foi estabelecida. A principal causa para quadros de vídeo descartados é quando um quadro de vídeo não chega em ordem e, por esse motivo, precisa ser descartado, pois já há um mais novo. Isso é semelhante a *quadros descartados,* mas a causa está em um nível inferior na pilha de Remoting. Quadros de vídeo descartados só são esperados em condições de rede ruins.

Na tela principal, você pode dizer **"desabilitar diagnóstico"** para desativar o diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos do sistema pc
* Seu computador **deve estar** executando a Atualização Windows 10 Aniversário ou mais recente.
* Recomendamos uma placa gráfica GeForce GTX 970 ou AMD Radeon R9 290 ou melhor.
* Recomendamos que você conecte seu computador à sua rede via ethernet para reduzir o número de saltos sem fio.

## <a name="see-also"></a>Consulte Também
* [HoloLens (primeira geração): adicionar a remoção holográfica](add-holographic-remoting.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs Windows Mixed Reality holográficas](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)