---
title: Como funciona o acompanhamento interno
description: informações sobre o sistema de controle interno baseado em câmera usado em Windows Mixed Reality headsets.
ms.topic: article
keywords: Windows Mixed Reality, realidade misturada, realidade Virtual, VR, MR, inside-out, controle de saída, câmera
ms.openlocfilehash: 579ef23c1eca2c184d07878c4e71ce298c5ad9922255b5e43643458a256b61bf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197857"
---
# <a name="inside-out-tracking"></a>Acompanhamento interno

## <a name="how-does-inside-out-tracking-work"></a>Como funciona o acompanhamento interno?

**Resposta rápida:** o sistema de controle usa duas câmeras visíveis de baixa resolução para observar os recursos em seu ambiente. Em seguida, as câmeras atestam as informações com os dados do IMU para determinar uma posição precisa do dispositivo em seu ambiente.

**Mais detalhes:** O sistema de controle usa duas câmeras pretas e brancas de baixa resolução para identificar recursos em seu ambiente de uma luz visível. O sistema irá triangular sua posição com base nos recursos observados, que complementam as informações, combinando dados de IMU de alta taxa para produzir uma estimativa de pose contínua para o HMD em seu ambiente. As informações de pose são usadas por ambos os aplicativos para renderizar uma cena e pelo sistema para corrigir esse processamento para qualquer previsão incorreta no tempo e na posição. Seu PC armazena informações de ambiente para que o sistema de controle possa recuperar dados específicos do ambiente, como o local físico dos limites da sala. Se você usar seu dispositivo em várias salas, poderá configurar limites diferentes em cada sala e o sistema de rastreamento poderá lembrar o limite específico do espaço específico.

como o rastreamento em headsets de imersão Windows Mixed Reality funciona como o rastreamento em [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), esse vídeo pode ser útil:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>O que é necessário para que o rastreamento funcione bem?

Há duas preocupações a serem abordadas para garantir que o controle funcione bem para você:
1. Verifique se seu PC atende aos requisitos para executar o Windows Mixed Reality. se o seu pc atender aos requisitos mínimos para Windows Mixed Reality, o rastreamento terá recursos suficientes para ser executado em seu PC.
2. Verifique se seu ambiente é adequado para o tipo de controle visual que o dispositivo emprega. Você deve usar o dispositivo em um ambiente com luz suficiente. Como o dispositivo funciona observando seu ambiente na luz visível, deve haver uma luz suficiente para que o ambiente possa ser observado. Também deve haver recursos visuais que diferenciam o suficiente (em outras palavras, decorações, pontos de contraste e assim por diante) para que o sistema de rastreamento funcione.

## <a name="how-much-light-is-enough-light"></a>Qual é a quantidade de luz suficiente?

Se você puder se movimentar confortavelmente no ambiente sem ficar muito escuro, e se você puder observar os recursos de outras pessoas se sentirem de toda a sala, o sistema de controle provavelmente terá uma luz suficiente. Tenha em mente que isso é muito claro, se você estiver olhando diretamente para a sol, as câmeras poderão ficar saturadas e não serão rastreadas de forma confiável. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>Qual é o número recomendado de recursos ambientais?

O produto foi projetado para funcionar em ambientes normais. Considere o seguinte experimento de pensamento – se você estava em um espaço em branco com paredes brancas, um teto branco e um piso branco, o sistema de controle não encontraria nenhum recurso para acompanhar e falharia. Se você estivesse em uma sala que foi abordada em trabalho e decoração de arte, o sistema de controle encontraria muitos recursos para acompanhar e funcionaria bem. Normalmente, as residências e os escritórios em geral foram demonstrados para ter detalhes de recursos suficientes para serem bem acompanhados.

## <a name="how-fast-can-i-move-with-the-device"></a>Quão rápido posso mover com o dispositivo?

O dispositivo foi projetado para dar suporte ao movimento que excede o que normalmente é experiente pelo movimento de cabeça humana. Fique à vontade para se mover para o. Tenha em mente que você reduziu a conscientização de seus arredores físicos enquanto estiver em um headset de imersão, portanto, certifique-se de que você está se movendo com segurança em seu ambiente.

## <a name="where-will-tracking-not-work"></a>Onde o rastreamento não funcionará?

O controle não funcionará em uma sala escura em que as câmeras não possam ver recursos suficientes devido à baixa luz. O acompanhamento não funcionará bem (ou algumas vezes trabalhará) ao mover veículos como aviões, barramentos, trens, carros ou elevadors. O rastreamento também pode falhar em situações em que há muita luz ou uma grande diferença clara. Por exemplo, se houver um fluxo direto de luz solar em uma sala, as câmeras poderão reduzir a exposição para reduzir a saturação e não verão recursos naturais normais. É recomendável que você se depara com uma iluminação relativamente uniforme e, se você tiver que semicerrarr ou encontrar coisas inseguramente brilhantes, o sistema de controle pode não fazer muito bem. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Qual é a diferença entre 3DOF e 6DOF?

Primeiro, o DOF é curto para "graus de liberdade". Ao discutir os sistemas de controle, isso significa os graus ou tipos de movimento que podem ser detectados. Esses movimentos são divididos em duas categorias principais: ' rotação ' e ' rotação com translação '. 3DOF refere-se a 3 graus de liberdade e representa rotações sobre cada eixo. Em suma, o controle de 3DOF permite que você olhe para a esquerda/direita, para cima/para baixo e incline sua cabeça (roll) lado a lado. Não é possível traduzir ou avançar para frente/para trás no 3DOF. 6DOF é curto para 6 graus de liberdade. Ele se baseia nas rotações do 3DOF e adiciona a ele traduções de ti. Isso significa que você pode percorrer para frente/para trás, strafe para a esquerda/direita e Crouch e se destacar. Três acompanhamento de DOF é o tipo de controle que você normalmente encontraria em um telefone ou produto VR baseado em celular, enquanto o 6DOF será encontrado em plataformas VR mais poderosas. Algumas experiências são adaptadas para o 3DOF e só permitirão o movimento do 3DOF (rotações), mesmo que o dispositivo dê suporte ao rastreamento de 6DOF. Um exemplo disso seria assistir a um vídeo 360 em Windows Mixed Reality. O vídeo permitirá que você examine, mas não permitirá que você percorra seu ambiente.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>As coisas estão se tremulando ou ocorrendo no meu headset. Meu controle não está funcionando?

Há algumas fontes desse tipo de erro. É importante atribuir o que você está observando à causa certa para que possa ser resolvido. Consulte a seção [solução de problemas](tracking.md) para ajudar a entender por que isso pode estar ocorrendo.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Posso trazer minha própria tecnologia de controle para Windows Mixed Reality?

Atualmente, não há suporte para essa funcionalidade.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Por que vejo a interface do usuário que diz "não foi possível encontrar seu limite?"

Como o limite de segurança é específico para um local físico, se você estiver usando o dispositivo em um local diferente, o sistema não conseguirá localizar os limites. Além disso, depois de configurar seu limite, o sistema sempre o procurará, mesmo que você use o dispositivo em um local físico diferente. Você verá essa interface do usuário sempre que usar o dispositivo em um local diferente e ainda não tiver configurado um limite nesse local. Você pode configurar limites em cada local em que usa o dispositivo e o dispositivo irá lembrar os limites específicos do local.

Se você estiver usando o dispositivo em um local em que você configurou um limite anteriormente e o dispositivo ainda não conseguir encontrá-lo, você poderá configurar um novo limite ou limpar todos os dados do ambiente para remover todos os limites do dispositivo. Consulte a seção de [solução de problemas](tracking.md) para entender por que o sistema não consegue localizar seus limites e etapas para corrigi-lo.

## <a name="how-do-i-set-up-tracking"></a>Como fazer configurar o acompanhamento?

o rastreamento no Windows Mixed Reality é simples de usar, não há infraestrutura ou configuração necessária. Se você optar por, poderá configurar um limite virtual para uso. Consulte a seção sobre como [configurar seu limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para obter mais informações.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Como fazer limpar os dados de controle e de ambiente?

O sistema de controle armazena alguns dados de ambiente para que ele possa se lembrar do local físico do mundo real de coisas como seus limites de segurança. Essas informações, incluindo os limites de segurança, podem ser removidas a qualquer momento. Se essas informações forem removidas, o sistema não reconhecerá mais seu espaço nem rechamará os limites de segurança. Se você quiser usar limites de segurança depois de limpar os dados do ambiente, precisará configurá-lo novamente. Consulte a seção sobre como configurar [seu limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para configurar um novo limite. para remover todos esses dados, abra Configurações, navegue até "realidade misturada" e selecione a seção ambiente no menu do lado esquerdo. Selecione o botão rotulado "limpar dados do ambiente" para remover todos os dados de ambiente e de controle.

## <a name="see-also"></a>Confira também
* [Solucionando problemas do sistema de controle](tracking.md)
* [Controladores de movimentos](controllers-in-wmr.md)
* [Sua página inicial do Windows Mixed Reality](your-mixed-reality-home.md)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
