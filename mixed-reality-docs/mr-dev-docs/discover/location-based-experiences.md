---
title: Entretenimento baseado em localização com Windows Mixed Reality
description: Saiba mais sobre Windows Mixed Reality para o Entretenimento Baseado na Localização — hardware, PCs, acompanhamento, configuração e suporte.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: realidade misturada, vr, lbe, local, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, hardware, HoloLens, multi player, serviços de nuvem, azure
ms.openlocfilehash: e9cff1184ca60f4b64be5346a187666e7b401aab06fee87c179917e300aa07f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196780"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Entretenimento baseado em localização com Windows Mixed Reality

Nos últimos anos, vimos uma quantidade incrível de crescimento e inovação na categoria entretenimento baseado em localização. Locais tradicionais, como parques de tema e cenários, começaram a oferecer experiências imersivas e multi player como experiências complementares a instalações e corridas existentes. Novos operadores e locais estão levando experiências exclusivas multi player e multi player a um preço atraente para o público. Todas essas experiências estão pressionando o envelope para o que é possível com a realidade misturada.

Este documento é um guia para começar a Windows Mixed Reality na categoria Entretenimento Baseado na Localização. As diretrizes abaixo também podem ser aplicáveis a experiências baseadas em localização além de entretenimento, como treinamento, design de produto e outros casos de uso.

## <a name="engineering-faq"></a>Perguntas frequentes sobre engenharia

### <a name="hardware"></a>Hardware

**P: Qual hardware está disponível da Microsoft e de seus parceiros que posso usar em minha configuração?**

R: A Microsoft e seus parceiros OEM oferecem um portfólio atraente de dispositivos para escolher dependendo de suas necessidades.  

Se as experiências que você está fornecendo aos seus clientes exigirem um headset de realidade virtual, headsets no mercado da HP, Samsung e Acer são uma ótima ideia. Cada headset tem seus próprios atributos diferenciados. Mais detalhes sobre cada um abaixo.

HP Reverb: [Detalhes](https://hp.com/go/Reverbpro)

Samsung Bty+: [Detalhes](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Detalhes](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Se sua localização for especializada em experiências de realidade misturada ou aumentada com headsets de consulta, confira a Microsoft HoloLens 2.  

HoloLens 2: [Pré-solicitar juros](https://www.microsoft.com//hololens/buy)

Se você estiver experimentando experiências que usam pesquisa visual computacional avançada, fala e acompanhamento de corpo, o DK do Azure Kinect é uma boa ideia.  

Azure Kinect: [Detalhes](https://azure.microsoft.com//services/kinect-dk/)

**P: Qual é o portfólio de computadores de treinamento que posso usar para executar minhas experiências de VR com suporte para PC?**

Para experiências de VR com dispositivos de PC, nossos OEMs oferecem uma seleção incrível de computadores incríveis, criadas exatamente para essa necessidade.

A HP acabou de iniciar seu HP VR G2, o PC acessível mais poderoso do mundo – otimizado para experiências de roaming livre, agora com 30% mais potência com uma GPU RTX 2080 dentro. [Detalhes](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Instalação

**P: Como posso configurar mais facilmente a instalação e personalizar o Portal de Realidade Misturada para LBE?**

>[!NOTE]
>Esse recurso requer a versão 2000.19061.1011.0 ou superior.  

Você pode achar que precisa de mais personalização de Portal de Realidade Misturada do que normalmente está disponível por meio do aplicativo para implantar aplicativos em quiosques ou experiências personalizadas. A atualização mais recente de julho do Portal de Realidade Misturada dá suporte a várias configurações avançadas, que podem ser definidas por meio de um arquivo de configuração:  

Permitir verificações do sistema com falha – normalmente, o processo de instalação verifica o computador quanto à compatibilidade com Windows Mixed Reality antes de concluir a instalação. Ignorar verificações de compatibilidade pode causar problemas ao tentar executar Windows Mixed Reality se houver problemas de compatibilidade.  

Ignorar o Aplicativo Desacatador de Dispositivo – o DCA fornece etapas de configuração específicas do headset fornecidas pelo fabricante e permite a atualização do firmware do headset.  

Ignorar a instalação da sala – em vez de ser solicitado a criar um limite de sala, você pode continuar diretamente no headset no modo Seated/Standing.  

Ignorar a instalação de aplicativos da Store – a instalação normal instala vários aplicativos da Store, incluindo Visualizador 3D e o complemento visualizador do Edge 360. Isso ignorará a instalação desses aplicativos, mas talvez você não tenha a funcionalidade do dispositivo.  

Mostrar visualização em tela inteira – Portal de Realidade Misturada padrão será mostrar a visualização do headset em tela inteira no computador desktop enquanto o headset estiver em uso.  

Ocultar Novo para o painel lateral – impede que o painel Novo para você seja expandido na Portal de Realidade Misturada.  

#### <a name="how-to-configure"></a>Como configurar:  

Para definir qualquer uma dessas configurações, você precisa criar um arquivo _chamadoUserConfig.jsneste_ diretório: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState \\_

Para a maioria dos usuários, isso terá a aparência: _C:\Users \<username> \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState \\_

O arquivo JSON deve ter o conteúdo abaixo com "true" definido para qualquer uma das configurações acima que você deseja habilitar:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**P: Há alguma orientação sobre como configurar o playspace?**

R: A configuração de um playspace deve ser feita como você faria com uma experiência de configuração do consumidor. O processo de Instalação da Sala também permitirá que você defina seus limites de sala. Mais detalhes sobre como configurar limites de sala podem ser lidos [aqui.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

Conforme discutido no documento acima, o playspace máximo razoável de coordenada única é de cerca de 5 mx5m. Se você quiser ter uma área maior, poderá usar a funcionalidade Âncoras Espaciais na pilha Windows API Holográfica. Usar essa API exigirá engenharia personalizada nas experiências que você está produzindo.  

Mais detalhes sobre como otimizar seu conteúdo para tamanhos de espaço diferentes podem ser [lidos aqui.](/windows/mixed-reality/coordinate-systems)
 

**P: Meu espaço é muito grande e estou com erros quando tento configurar uma experiência permanente com limites. O que devo fazer para configurar meu trabalho de grande experiência de roamão livre?**

R: Para configurar um espaço maior que ~18x18ft, você não pode usar a experiência de limite fornecida pelo sistema.  Os sistemas de limite dependem de uma única "âncora" de coordenada fixa, que pode se tornar instável quando um usuário está muito longe da âncora de estágio central. 

Você pode configurar o modo "setado", que não exibirá o limite nem configurará limites de estágio ou playspace.  Você precisará configurar várias âncoras espaciais dentro do aplicativo para fazer referência a áreas de limite físicas. 

O desenvolvedor do aplicativo é responsável por exibir as proteções necessárias para que os usuários não colidam com o ambiente físico.  Elas podem ser paredes digitais dentro da experiência ou um visual de limite de jogo personalizado. 

As diretrizes sobre como configurar o limite de sala com o WMR podem ser encontradas [aqui.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

**P: Onde está a origem do playspace?**

R: A origem do playspace é determinada pela experiência de Instalação da Sala, mais especificamente a posição DO HMD quando o botão Central é pressionado durante a instalação. 

### <a name="multi-player-setup"></a>CONFIGURAÇÃO DE VÁRIOS PLAYER

**P: Estou implantando uma experiência com vários jogadores no meu local. Há suporte para isso Windows Mixed Reality?**

R: Se você optar pelo build Windows 20H1 ou posterior por meio de nosso programa Insider, poderá acessar uma nova interface para compartilhamento de mapa. Essa nova funcionalidade está disponível por meio da interface [do Gerenciador de](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) Mapas do portal Windows Dispositivo. Para usar essa ferramenta, siga as etapas abaixo:
* Certifique-se de que você tenha optado pelo 20H1 ou posterior – após setembro de 2019, isso significa usar nosso programa Insider
* Habilita o Windows Portal de Dispositivos (WDP) usando estas [instruções](/windows/uwp/debug-test-perf/device-portal-desktop)
* Conecte um Windows Mixed Reality HMD de onde você deseja baixar um mapa existente ou importar um novo mapa
* Navegue até o WDP no navegador de sua escolha usando a URL fornecida na tela de configurações.
    * Depois, navegue até a seção "Realidade Misturada" e selecione "Gerenciador de Mapas".
    * Agora você pode usar o botão "Baixar" para exportar um mapa existente do computador.
    * Você pode usar o botão "Upload um arquivo de mapa" para importar um mapa de uma exportação anterior (talvez em um computador diferente).
    * Você pode usar "Importar" para permitir que o sistema use esse mapa para este HMD neste computador.

> [!NOTE] 
> Anteriormente, era possível usar a Ferramenta de Empacotador de Dados Espaciais, no entanto, essa ferramenta foi lançada originalmente como sem suporte e agora está oficialmente preterida e não funciona mais no 20H1. Em vez disso, use a ferramenta [Gerenciador de Mapas](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) de caixa de entrada, conforme descrito acima. 

### <a name="tracking"></a>Rastreamento

P: Como funciona a tecnologia de acompanhamento Windows Mixed Reality headsets?  

A Realidade Misturada compartilha a mesma tecnologia de acompanhamento que a HoloLens. Para saber mais sobre o sistema de acompanhamento interno, confira a documentação [aqui.](/windows/mixed-reality/enthusiast-guide/tracking-system)

Para uma descrição de como funciona o sistema de mapeamento espacial de nível superior, leia nossa descrição [aqui.](../design/spatial-mapping.md)

**P: Há alguma prática recomendada para obter um volume de acompanhamento confiável?**

Para configurar melhor o ambiente para acompanhar o sucesso, você pode ler as práticas recomendadas nesta [postagem.](/hololens/hololens-environment-considerations)

**P: Há nuances específicas com o acompanhamento em espaços de escala de warehouse ou otimizações a considerar?**

R: As seguintes práticas podem ajudar a obter um volume de acompanhamento mais confiável:  

Fornecer recursos diferentes na sala que se sobrepõem em várias posições ajudará o sistema de acompanhamento a obter um bloqueio sólido. Pense em splatters de pintura aleatórios e em uma hatching em vez de usar linhas de estilo de contorno sólidas. 

Minimize o intervalo dinâmico de iluminação em sua área sempre que possível. As câmeras de acompanhamento em nossos HMDs de Realidade Misturada não são HDR e têm o AGC (ganho automático) e o AEC (exposição automática) lidarão com iluminação diferente. Dependendo da distribuição da luz da superfície, dos padrões e do contraste, o AGC ou o AEC podem concluir que você está em uma sala muito branca ou preta, o que pode limpar seus recursos que podem estar na "cor" oposta. Se você estiver tentando tirar uma foto interior na frente de uma janela exterior com luz do dia brilhante e ajustar a exposição para que possa ver detalhes fora, tudo no interior será subexposto e preto. Ou, se definido para dentro, tudo o que está fora agora é sobreposto e todo branco.  

Destaques em uma sala (até mesmo sobrecarga) que estão em exibição se as câmeras de acompanhamento às vezes podem ser responsáveis, o que confunda o AEC/AGC das câmeras de acompanhamento. A iluminação simples/difusa ajuda.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVIÇOS DE NUVEM DE REALIDADE MISTURADA E AZURE 

**P: Como pode Microsoft Azure minha escala de negócios?**

R: O Azure baseado no local e no gerenciamento remoto pode ajudar sua empresa a ser controlada por dados, reduzir os custos operacionais e dimensionar a implantação em locais novos e existentes. Serviços de nuvem do Azure, como o Azure Armazenamento, Azure Functions, Serviço de Aplicativo, Rede do Azure e Hub IOT podem ajudar com os seguintes casos de uso:  

Gerenciamento de & de implantação de dispositivo remoto 

Análise no local Real-Time 

LBE cheia de adaptação inteligente 

Streaming e implantação de conteúdo do LBE 

Calor de preferência do LBE Player 

LBE reserva e sistema de reservas 

**P: estou desenvolvendo um MMOG espacial para implantar em grande quantidade de espaço. Todos os serviços que me ajudam a gerenciar meu conteúdo e minha persistência de objetos?**

r: as âncoras espaciais do Azure são um novo serviço de realidade misturada que permite experiências de realidade mista de vários usuários, com reconhecimento espacial em todos os dispositivos HoloLens, iOS e Android. Você pode aprender mais sobre as âncoras espaciais do Azure [aqui](https://azure.microsoft.com//services/spatial-anchors/).

**Perguntas. Nosso local é especialista em experiências de vários jogadores e gostaria de concentrar nosso tempo de desenvolvimento em conteúdo e desenvolvimento de front-end. Há ofertas que podem me ajudar a inicializar ou descarregar o desenvolvimento de back-end?**

R: o Azure PlayFab é uma plataforma de back-end completa para jogos ao vivo. Você pode aprender mais sobre isso [aqui](https://playfab.com/).

### <a name="misc"></a>Diversos

**P: Eu uso SteamVR para implantar minhas experiências. Windows Mixed Reality funciona com o SteamVR?**

r: Windows Mixed Reality para SteamVR permite que os usuários executem experiências de SteamVR em headsets de imersão Windows Mixed Reality. Saiba mais sobre SteamVR com WMR [aqui](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Suporte e comunidade  

Temos alguns recursos úteis para ajudá-lo a se envolver com especialistas do assunto em nossa equipe, obter suporte para solução de problemas e contribuir com a comunidade de desenvolvimento de realidade misturada mais ampla.  

Se você tiver problemas com recursos lançados publicamente, execute um bug usando o Hub de comentários. para obter diretrizes, consulte esta [página](/windows/mixed-reality/enthusiast-guide/filing-feedback).

Para obter outras ajuda de solução de problemas com o WMR, solucione uma [solicitação de suporte](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) com nossa equipe de suporte ao cliente.

Junte-se ao nosso canal de margem de atraso HoloDevelopers para envolver os desenvolvedores de realidade misturada e especialistas no assunto: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: Siga nossa equipe de relações de desenvolvedor de realidade misturada para notícias, eventos e atualizações @MxdRealityDev 

Se você estiver em ou em volta de San Francisco, sempre haverá algo acontecendo no reator da Microsoft. Você pode ver nosso calendário de eventos [aqui](https://developer.microsoft.com//reactor/Location/San%20Francisco).
