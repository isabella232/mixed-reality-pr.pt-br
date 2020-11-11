---
title: Perguntas frequentes sobre HP reverbs G2
description: Perguntas frequentes sobre como usar o HP reverberar G2 Headset
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, desempenho
appliesto:
- Windows 10
ms.openlocfilehash: c24f6766cab242332e79a0c5cf5ed3cd92c4687d
ms.sourcegitcommit: f459c7deb254409fd5db3967bcc875bcbc367e77
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94482394"
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

Se você estiver vendo um erro 7-14 "algo deu errado", tente as seguintes etapas:

- Verifique se você tem os drivers mais recentes instalados.
- Tente conectar o cabo a uma porta USB-3,0 diferente.
- Use o C USB para um adaptador incluído para testar portas diferentes.

Tente conectar o cabo em um hub USB diferente.  

> [!NOTE]
> A HP recomenda o uso de controladores USB integrados à placa-mãe com dispositivos reverbo G2.
> Se não for possível conectar seu dispositivo, entre em contato com o [suporte da HP](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Estou recebendo um erro de 13-14 "algo errado" quando meu PC reinicia da hibernação (S4)

Às vezes, durante o processo de retomada, a placa de vídeo não pode estabelecer uma conexão, portanto, desconectar o tipo USB C do seu PC e conectá-lo novamente pode ajudar a estabelecer uma conexão.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>O portal de realidade misturada diz "não é possível executar a realidade misturada neste headset", mas isso funcionou bem com meu Headset WMR anterior

Isso pode acontecer porque seu HP reverbo G2 requer um PC mais potente para garantir a melhor experiência. Para obter mais informações, consulte os requisitos mínimos do [PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Parece que minha exibição à esquerda é ampliada e a exibição à direita está descentralizada e meia preta

Isso pode acontecer quando o headset não está em execução na resolução nativa. Devido à natureza das exibições de alta resolução no HP reverbs G2 HMD, nem todos os sistemas poderão renderizar a resolução nativa. Há uma correção em um futuro Windows Update que resolverá o problema de renderização quando o headset não estiver na resolução nativa.

Há alguns motivos pelos quais o sistema não pode renderizar na resolução nativa:

- O DisplayPort no sistema pode não ser compatível com 1,3 ou pode não dar suporte a todas as quatro pistas.
- Se você estiver usando um adaptador, talvez ele não seja compatível com HBR3, ou talvez não dê suporte a todas as 4 pistas.
- Se o seu sistema tiver uma GPU híbrida, isso pode estar limitando a largura de banda disponível para o DisplayPort.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Por que meus modelos do meu HP Motion Controller não aparecem corretamente em um jogo

Embora muitos jogos funcionem imediatamente com os controladores HP Motion, alguns jogos têm dependências de recursos de controladores existentes e, portanto, podem ter alguns problemas:

- Modelo incorreto exibido: corrigir isso requer uma atualização de jogo. Normalmente, isso não bloqueia nenhum recurso do jogo, mas pode levar à confusão ou até mesmo a artefatos visuais.
- Dependência do Touchpad ou mais geralmente no layout de entrada do controlador. O SteamVR permite criar associações personalizadas para ajudar a evitar esse tipo de problema:
    - O Windows Mixed Reality for SteamVR inclui associações personalizadas para alguns jogos. Essas associações são usadas automaticamente quando o jogo é iniciado e nenhuma ação do usuário é necessária.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>Meus jogos do SteamVR parecem funcionar corretamente com meus controladores HP Motion

Embora os desenvolvedores estejam trabalhando para atualizar seus jogos para compatibilidade com o HP Motion Controller, fornecemos associações de controlador personalizadas para muitos dos jogos mais populares no fluxo. Com o "Windows Mixed realment for SteamVR" totalmente atualizado para a versão 1.2.444, essas associações devem ser selecionadas automaticamente quando o jogo estiver em execução. No entanto, se o jogo não parece registrar suas ações no momento, você pode procurar manualmente por perfis de associação personalizados usando o menu de configurações do SteamVR.
Para fazer isso

- Abra o menu SteamVR pressionando o botão de menu do controlador de movimento à direita
- Selecione o ícone "configurações" no canto inferior direito do menu SteamVR
- Selecione a guia "controladores"
- Selecione a opção "gerenciar associações de controlador"

A partir daqui, você pode alterar a associação do controlador ativo para "personalizado", que abrirá a opção para experimentar associações de jogos compartilhadas pela Comunidade.
Se nenhuma associação de jogo personalizada já tiver sido compartilhada para este jogo (ou se você não estiver totalmente satisfeito com as que você tentou), também poderá criar suas próprias associações de jogos personalizadas e até mesmo ajudar o restante da Comunidade, compartilhando-as após algumas sessões de jogo.