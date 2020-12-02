---
title: Perguntas frequentes sobre HP reverbs G2
description: Perguntas frequentes sobre como usar o HP reverberar G2 Headset
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, desempenho
appliesto:
- Windows 10
ms.openlocfilehash: 7712641bad36b8759b9237abf14593f8c121e81b
ms.sourcegitcommit: 3eb4c1a79e9173a5c9b6d2284f34c0bceced402c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96501704"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Perguntas frequentes sobre o HP reverbs G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>Há uma ordem específica que devo seguir para conectar meus cabos de headset a um PC

A HP recomenda:

- Conecte primeiro o cabo de 6 medidores ao headset antes de se conectar ao PC ou à fonte de energia.
- Deixe o cabo de 6 metros conectado ao headset após a instalação inicial.
- Quando o headset não estiver em uso, desconecte o adaptador de energia do cabo de 6 metros.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>O que devo fazer para obter uma imagem mais nítida

Há algumas coisas que você pode tentar se sentir que a exibição parece um pouco desfoque:

- Verifique se o headset está em sua cabeça corretamente para que seus olhos estejam centralizados com relação às lentes.
- Tente ajustar o IPD (distância interpupillary). Observe que o reverberador de reverbo usa um IPD de hardware. Para alterá-lo, procure ajuste de IPD no headset.
- Se precisar de óculos ou contatos, eles ainda serão necessários.
- Verifique suas lentes se elas precisam ser limpas (somente tecido microfiber – sem fluids).
- Devido ao design avançado do headset, pode haver algumas fantasmas de imagem secundária nos primeiros minutos ao iniciar o dispositivo enquanto estiver frio até que os LCDs tenham a oportunidade de fazer o aquecimento.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>Estou recebendo um erro de 7-14 "algo errado" ao conectar meu Headset

O 7-14 algo deu errado significa que alguns dos componentes USB2 necessários não foram encontrados.  Devido ao cabo extra para o HP, o caractere de reverberação de caracteres USB são mais apertados.  Isso significa que uma porta em seu computador pode funcionar de forma mais confiável do que outra.

Se você estiver vendo um erro 7-14 "algo deu errado", tente as seguintes etapas:

- Verifique se você tem os drivers mais recentes instalados para o headset e o controlador USB.
- Verifique se você está usando um driver USB da Microsoft. Deve haver uma "Microsoft" no nome do dispositivo "controlador de host extensível".
- Tente conectar o cabo a uma porta USB-3,0 diferente em seu computador. (Experimente o tipo USB-C e as portas Type-A)
- Use o USB C incluído em um adaptador para testar portas diferentes.
- Tente conectar o headset por meio de um hub USB ao seu computador.

> [!NOTE]
> A HP recomenda o uso de controladores USB integrados à placa-mãe com dispositivos reverbo G2.
> Se não for possível conectar seu dispositivo, entre em contato com o [suporte da HP](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Estou recebendo um erro de 13-14 "algo errado" quando meu PC reinicia da hibernação (S4)

Às vezes, durante o processo de retomada, a placa de vídeo não pode estabelecer uma conexão, portanto, desconectar o tipo USB C do seu PC e conectá-lo novamente pode ajudar a estabelecer uma conexão.

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>O meu joystick do controlador HP Motion às vezes vai para um lado

Esse problema é corrigido com a remoção completa do joystick até que ele clique e seja movido livremente.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>O portal de realidade misturada diz "não é possível executar a realidade misturada neste headset", mas isso funcionou bem com meu Headset WMR anterior

Isso pode acontecer porque seu HP reverbo G2 requer um PC mais potente para garantir a melhor experiência. Para obter mais informações, consulte os requisitos mínimos do [PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Parece que minha exibição à esquerda é ampliada e a exibição à direita está descentralizada e meia preta

Isso pode acontecer quando o headset não está em execução na resolução nativa. Devido à natureza das exibições de alta resolução no HP reverbs G2 HMD, nem todos os sistemas poderão renderizar a resolução nativa. Há uma correção em um futuro Windows Update que resolverá o problema de renderização quando o headset não estiver na resolução nativa.

Há alguns motivos pelos quais o sistema não pode renderizar na resolução nativa:

- O DisplayPort no sistema pode não ser compatível com 1,3 ou pode não dar suporte a todas as quatro pistas.
- Se você estiver usando um adaptador, talvez ele não seja compatível com HBR3, ou talvez não dê suporte a todas as 4 pistas.
- Se o seu sistema tiver uma GPU híbrida, isso pode estar limitando a largura de banda disponível para o DisplayPort.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Por que meus modelos do meu HP Motion Controller não aparecem corretamente em um jogo

Embora a maioria dos jogos não exiba os controladores ou use os modelos instalados pelo driver, alguns jogos usam suas próprias versões dos modelos de controlador, para personalizá-los ou para exibir a ajuda contextual para as entradas disponíveis. Normalmente, isso não bloqueia nenhum recurso dos jogos, mas pode levar à confusão ou até mesmo a artefatos visuais. Isso só pode ser corrigido com uma atualização do próprio jogo.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>Meus jogos do SteamVR parecem funcionar corretamente com meus controladores HP Motion

Embora os desenvolvedores estejam trabalhando para atualizar seus jogos para compatibilidade com o HP Motion Controller, fornecemos associações de controlador personalizadas para muitos dos jogos mais populares no fluxo. Com o "Windows Mixed realment for SteamVR" totalmente atualizado para a versão 1.2.444, essas associações devem ser selecionadas automaticamente quando o jogo estiver em execução. No entanto, se o jogo não parece registrar suas ações no momento, você pode procurar manualmente por perfis de associação personalizados usando o menu de configurações do SteamVR.
Para fazer isso

- Abra o menu SteamVR pressionando o botão de menu do controlador de movimento à direita
- Selecione o ícone "configurações" no canto inferior direito do menu SteamVR
- Selecione a guia "controladores"
- Selecione a opção "gerenciar associações de controlador"

A partir daqui, você pode alterar a associação do controlador ativo para "personalizado", que abrirá a opção para experimentar associações de jogos compartilhadas pela Comunidade.
Se nenhuma associação de jogo personalizada já tiver sido compartilhada para este jogo (ou se você não estiver totalmente satisfeito com as que você tentou), também poderá criar suas próprias associações de jogos personalizadas e até mesmo ajudar o restante da Comunidade, compartilhando-as após algumas sessões de jogo.