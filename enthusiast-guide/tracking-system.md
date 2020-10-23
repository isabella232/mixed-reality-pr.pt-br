---
title: Como funciona o acompanhamento interno
description: Informações sobre o sistema de controle interno baseado em câmera usado em headsets de realidade mista do Windows.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, Inside-Out, dentro do rastreamento, câmera
ms.openlocfilehash: eda1b323915788f72ae6f4a2efcf51850734eac9
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434600"
---
# <a name="inside-out-tracking"></a>Rastreamento interno

## <a name="how-does-inside-out-tracking-work"></a>Como funciona o acompanhamento interno?

**Resposta rápida:** o sistema de controle usa duas câmeras visíveis de baixa resolução para observar recursos em seu ambiente e fusível essas informações com dados de IMU para determinar uma posição precisa do dispositivo em seu ambiente.

**Mais detalhes:** O sistema de controle usa duas câmeras pretas e brancas de baixa resolução para identificar recursos em seu ambiente de uma luz visível. O sistema irá triangular sua posição com base nos recursos observados e complementar essas informações, combinando dados de IMU de alta taxa para produzir uma estimativa de pose contínua para o HMD em seu ambiente. As informações de pose são usadas por ambos os aplicativos para renderizar uma cena e pelo sistema para corrigir esse processamento para qualquer previsão incorreta no tempo e na posição. As informações em seu ambiente são armazenadas em seu computador para que o sistema de rastreamento possa recuperar dados específicos do ambiente, como o local físico do limite em sua sala. Se você usar seu dispositivo em várias salas, poderá configurar limites diferentes em cada sala e o sistema de controle poderá se lembrar do limite específico do espaço específico.

Como o rastreamento em headsets de imersão de realidade mista do Windows funciona como o rastreamento no [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), você pode achar esse vídeo útil:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>O que é necessário para que o rastreamento funcione bem?

Há duas preocupações a serem abordadas para garantir que o controle funcione bem para você:
1. Verifique se seu PC atende aos requisitos para executar a realidade mista do Windows. Se o seu PC atender aos requisitos mínimos para a realidade mista do Windows, o rastreamento terá recursos suficientes para ser executado em seu PC.
2. Verifique se seu ambiente é adequado para o tipo de controle visual que o dispositivo emprega. Você deve usar o dispositivo em um ambiente com luz suficiente. Como o dispositivo funciona observando seu ambiente na luz visível, deve haver uma luz suficiente para que o ambiente possa ser observado. Também deve haver recursos visuais que diferenciam o suficiente (em outras palavras, decorações, pontos de contraste, etc.) para que o sistema de rastreamento funcione.

## <a name="how-much-light-is-enough-light"></a>Qual é a quantidade de luz suficiente?

Uma boa regra geral é que se você puder se movimentar confortavelmente no ambiente sem ficar muito escuro e se puder observar os recursos de outras pessoas se sentirem de toda a sala, o sistema de controle provavelmente terá uma luz suficiente.

## <a name="what-is-the-recommended-amount-of-environmental-features"></a>Qual é a quantidade recomendada de recursos ambientais?

O produto foi projetado para funcionar em ambientes normais. Considere o seguinte experimento de pensamento – se você estava em um espaço completamente em branco (paredes brancas, teto branco, piso branco), o sistema de controle não encontrará nenhum recurso para acompanhar e falharia. Se você estivesse em uma sala que foi abordada em trabalho e decoração de arte, o sistema de controle encontraria muitos recursos para acompanhar e funcionaria bem. Na maior parte, normalmente, as residências e os escritórios decorados foram demonstrados para ter detalhes de recursos suficientes para serem bem acompanhados.

## <a name="how-fast-can-i-move-with-the-device"></a>Quão rápido posso mover com o dispositivo?

O dispositivo foi projetado para dar suporte ao movimento que excede o que normalmente é experiente pelo movimento de cabeça humana. Fique à vontade para se mover para o. Tenha em mente que você reduziu a conscientização de seus arredores físicos enquanto estiver em um headset de imersão, portanto, certifique-se de que você está se movendo com segurança em seu ambiente.

## <a name="where-will-tracking-not-work"></a>Onde o rastreamento não funcionará?

O acompanhamento não funcionará em uma sala escura, em que as câmeras não poderão ver recursos suficientes devido à baixa luz. O controle geralmente não funcionará bem (ou, às vezes, funcionará) ao mover veículos como aviões, barramentos, trens, carros ou elevadors.

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Qual é a diferença entre 3DOF e 6DOF?

Primeiro, o DOF é curto para "graus de liberdade". Ao discutir os sistemas de controle, isso significa os graus ou tipos de movimento que podem ser detectados. Esses movimentos são divididos em duas categorias principais: ' rotação ' e ' rotação com translação '. 3DOF refere-se a 3 graus de liberdade e representa rotações sobre cada eixo. Em suma, o controle de 3DOF permite que você olhe para a esquerda/direita, para cima/para baixo e incline sua cabeça (roll) lado a lado. Não é possível traduzir ou avançar para frente/para trás no 3DOF. 6DOF é curto para 6 graus de liberdade. Ele se baseia nas rotações do 3DOF e adiciona a ele traduções de ti. Isso significa que você pode percorrer para frente/para trás, strafe esquerda/direita e Crouch para baixo e para cima. 3 o acompanhamento do DOF é o tipo de controle que você normalmente encontraria em um telefone ou em um produto VR baseado em celular, enquanto o 6DOF será encontrado em plataformas VR mais poderosas. Algumas experiências são adaptadas para o 3DOF e só permitirão o movimento do 3DOF (rotações), mesmo que o dispositivo dê suporte ao rastreamento de 6DOF. Um exemplo disso seria assistir a um vídeo 360 no Windows Mixed Reality. O vídeo permitirá que você examine, mas não permitirá que você percorra seu ambiente.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>As coisas estão se tremulando ou ocorrendo no meu headset. Meu controle não está funcionando?

Há algumas fontes desse tipo de erro. É importante poder atribuir o que você está observando à causa certa para que possa ser resolvido. Consulte a seção [solução de problemas](tracking.md) para ajudar a entender por que isso pode estar ocorrendo.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Posso trazer minha própria tecnologia de controle para a realidade mista do Windows?

Atualmente, não há suporte para esse recurso.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Por que vejo a interface do usuário que diz "não foi possível encontrar seu limite?"

Como o limite de segurança é específico para um local físico, se você estiver usando o dispositivo em um local diferente, o sistema não poderá localizar os limites. Além disso, depois de configurar seu limite, o sistema sempre o procurará, mesmo que você use o dispositivo em um local físico diferente. Você verá essa interface do usuário sempre que usar o dispositivo em um local diferente e ainda não tiver configurado um limite nesse local. Você pode configurar limites em cada local em que você usa o dispositivo e o dispositivo irá lembrar os limites específicos do local.

Se você estiver usando o dispositivo em um local em que você configurou um limite anteriormente e o dispositivo ainda não conseguir encontrá-lo, você poderá configurar um novo limite ou limpar todos os dados do ambiente para remover todos os limites do dispositivo. Consulte a seção de [solução de problemas](tracking.md) para entender por que o sistema não consegue encontrar seus limites e etapas para corrigi-lo.

## <a name="how-do-i-set-up-tracking"></a>Como fazer configurar o acompanhamento?

O controle no Windows Mixed Reality é simples de usar. Não há nenhuma infraestrutura ou configuração necessária e o dispositivo funcionará prontamente. Se você optar por, poderá configurar um limite virtual para uso. Consulte a seção sobre como [configurar seu limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para obter mais informações.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Como fazer limpar os dados de controle e de ambiente?

O sistema de controle armazena alguns dados de ambiente para que ele possa se lembrar do local físico do mundo real de coisas como seus limites de segurança. Essas informações, incluindo os limites de segurança, podem ser removidas a qualquer momento. Se essas informações forem removidas, o sistema não reconhecerá mais seu espaço nem poderá se lembrar dos limites de segurança. Se desejar usar limites de segurança depois de limpar os dados do ambiente, você precisará configurá-lo novamente. Consulte a seção sobre como configurar [seu limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para configurar um novo limite. Para remover todos esses dados, abra configurações, navegue até "realidade misturada" e selecione a seção ambiente do menu do lado esquerdo. Clique no botão "limpar dados do ambiente" para remover todos os dados de ambiente e de controle.

## <a name="see-also"></a>Confira também
* [Solucionando problemas do sistema de controle](tracking.md)
* [Controladores de movimentos](controller-in-wmr.md)
* [Sua página inicial do Windows Mixed Reality](your-mixed-reality-home.md)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
