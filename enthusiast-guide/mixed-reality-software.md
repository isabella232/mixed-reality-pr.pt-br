---
title: Visão geral do software e histórico de versões
description: uma visão geral dos principais componentes de software para Windows Mixed Reality, headsets de imersão e seu histórico de versões.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, componentes de software, histórico de lançamento, notas de versão, histórico de versão
appliesto:
- Windows 10
ms.openlocfilehash: 51c13326d2ad8aebe164e64d0bfc380923a91d1be02cea840cec4addd062533f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219722"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Visão geral do software de Realidade Misturada e histórico de versões

## <a name="introduction-to-mixed-reality-software"></a>Introdução ao software de realidade misturada

Windows Mixed Reality consiste nos principais componentes de software a seguir:

1. **Portal de realidade misturada**, que fornece a principal experiência de Windows Mixed Reality
    * no Windows 10 versões 1709 e 1803, o Portal de realidade misturada é um componente fundamental do sistema operacional Windows 10 atualizado por meio de Windows Update.
    * no Windows 10 versão 1809 e mais recente, o Portal de realidade misturada é atualizado por meio do aplicativo Microsoft Store.
2. O **pacote de recursos sob demanda da realidade misturada** (fod), baixado automaticamente e instalado durante a primeira execução do portal de realidade misturada. Mais informações sobre o pacote FOD podem ser encontradas [aqui](/windows/application-management/manage-windows-mixed-reality)
3. o **driver do controlador de headset e de movimento da realidade mista**, também conhecido como driver de sensores de HoloLens, é o principal pacote de driver que permite que Windows Mixed Reality headsets trabalhem com Windows Mixed Reality. isso é baixado e instalado automaticamente por meio de Windows Update na primeira vez que o headset da realidade misturada está conectado e é atualizado regularmente por meio de Windows Update
4. Os drivers de modelo do controlador de movimento da realidade misturada * contêm os modelos 3D dos controladores de movimento da realidade misturada e necessários para experiências de realidade misturada de terceiros. isso é baixado e instalado automaticamente por meio do Windows Update na primeira vez que os controladores de movimento da realidade misturada são emparelhados em seu PC e são atualizados por meio de Windows Update
5. **Windows 10, a versão 1709 (a atualização do criador de outono) ou mais recente** contém OS principais componentes e tecnologias do sistema operacional que habilitam Windows Mixed Reality

o uso de Windows Mixed Reality no SteamVR requer o seguinte software:

6. **SteamVR**, desenvolvido e mantido pela válvula Corporation que habilita aplicativos de realidade virtual e jogos em fluxo. Encontre mais informações [aqui](https://go.microsoft.com/fwlink/?linkid=862788)
7. o **Windows Mixed Reality para** o componente SteamVR, que une SteamVR com Windows Mixed Reality. mais informações sobre esse componente podem ser encontradas [na página Windows Mixed Reality para SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

gerenciando seu Windows Mixed Reality headset:

8. o **aplicativo do Device Companion**, desenvolvido e mantido por cada um dos fabricantes de headset, fornece uma rápida introdução ao seu Windows Mixed Reality headset. em fones de ouvido com recurso interno de Bluetooth, o aplicativo do Device Companion permite restaurar controladores de movimento para seus Bluetooth de fábrica. Alguns headsets (como o Samsung Odyssey e o Samsung Odyssey +) também usam o aplicativo do Device Companion para fornecer atualizações de firmware de headset do fabricante do headset. esse aplicativo é baixado automaticamente na primeira vez que o headset é conectado e pode ser encontrado no Menu iniciar Windows.

## <a name="windows-10-release-notes---may-2020"></a>notas de versão do Windows 10 – maio de 2020

o **Windows 10 v2004 (atualização 2020 de maio)** inclui novos recursos para fones de ouvido Windows Mixed Reality (VR), como a capacidade de iniciar aplicativos Win32 na página inicial misturada de realidade. HoloLens (1º gen) está em manutenção a longo prazo (LTS), com atualizações de serviço a serem liberadas mensalmente.

atualizando para a versão mais recente do PC para fones de ouvido de Windows Mixed Reality imersiva (VR), abra **Configurações > atualizar & segurança** e selecione **verificar se há atualizações**. em um computador Windows 10, você também pode instalar manualmente o **Windows 10 pode 2020 atualização** usando a [ferramenta de criação de mídia Windows](https://www.microsoft.com/software-download/windows10).

**versão mais recente do Desktop**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>atualizações para Windows Mixed Reality headsets de imersão

#### <a name="introducing-the-new-microsoft-edge"></a>Apresentando o novo Microsoft Edge

como [anunciado anteriormente](/windows/mixed-reality/new-microsoft-edge), fizemos atualizações para dar melhor suporte ao uso do novo navegador Microsoft Edge em Windows Mixed Reality. o novo Microsoft Edge adota o Chromium projeto de software livre para criar melhor compatibilidade com a web para clientes e menos fragmentação da web para todos os desenvolvedores da web. Ele também dá suporte a WebXR, o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

#### <a name="improved-settings-for-wmr"></a>Configurações aprimoradas para WMR

Graças aos seus comentários, adicionamos e esclarecemos as configurações na página de exibição do headset:

* A **qualidade visual da minha página inicial** altera essas configurações afeta apenas o ambiente doméstico da realidade misturada (Cliff House e Skyloft):

* **Ajuste o nível de detalhes e a qualidade dos efeitos na página inicial da realidade misturada** . isso altera parte da renderização que o utiliza em casa. Em particular, a qualidade visual de materiais diferentes (madeira, concreta e assim por diante) será dimensionada à medida que você alterar essa configuração de baixo para alto.

* **Alterar a resolução da janela do aplicativo** -por padrão, a maioria das janelas 2D iniciadas na página inicial é iniciada com uma resolução de 720-p. Embora seja possível redimensioná-las manualmente & verticalmente, você também pode optar por fazer com que todas elas sejam iniciadas em 1080p em vez disso. Anteriormente, essa opção estava disponível como a opção muito alta (beta) em qualidade visual. Nós o dividimos adequadamente como uma configuração separada agora.

* **Opções de experiência** – essas opções ajustam a experiência de realidade misturada para reduzir a carga em sistemas em que o hardware pode se esforçar para acompanhar uma leitura irrestrita de 90 fps. você pode habilitar ou desabilitar explicitamente essas configurações adicionais ou escolher deixar Windows decidir e permitir que nossa heurística continue decidindo quando ativar e desativar.

* **Resolução** – se você tiver um headset de alta resolução como o HP, oferecemos suporte para executá-lo em sua resolução nativa ou em uma resolução reduzida por motivos de desempenho. Headsets anteriores, como o Samsung Odyssey e o Odyssey +, dão suporte apenas a uma única resolução, de modo que não é possível alterar essa configuração nesses headsets.

* **taxa de quadros** -agora você pode definir manualmente a taxa de quadros da exibição do headset ou continuar a permitir que Windows use sua heurística para determinar se 60 hz ou 90 hz é mais apropriado.

* **Calibragem** -como antes, você pode ajustar seu IPD (distância interpupillary) se houver suporte para o headset.

* **Alternância de entrada** -Alterne o comportamento de alternância de foco de entrada (Win + Y) para ser automático (com base nos comentários do sensor de presença) ou manual.

#### <a name="new-cortana-app"></a>novo aplicativo Cortana

esta atualização para Windows inclui a versão mais recente do aplicativo Cortana, que atualmente é somente em inglês dos eua e não dá mais suporte a determinados comandos específicos de realidade misturada, como "tirar uma foto" e "fazer um vídeo". você pode usar o novo Cortana para iniciar aplicativos e ele também dá suporte a novos comandos com foco em produtividade, como "a minha próxima reunião?". ou "enviar um email para o <name> que estou executando atrasado".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Atualizações adicionais disponíveis em 19041,546 (lançadas em outubro de 2020)

esta atualização de serviço mensal da área de trabalho inclui as seguintes alterações para dispositivos Windows Mixed Reality: 
* reduz distorções e aberrations em HMD (exibições montadas Windows Mixed Reality). 
* adiciona suporte para futuros controladores HP Windows Mixed Reality motion. 
* altera o comportamento da configuração de taxa de atualização de 90 Hz no Windows Mixed Reality para não voltar mais automaticamente para 60 Hz em determinados casos, quando 90 Hz não puder ser alcançado. 

#### <a name="help-us-improve"></a>Ajude-nos a melhorar!

Estamos continuamente procurando melhorar a compatibilidade.  se você achar que seu aplicativo Win32 clássico favorito não está se comportando corretamente enquanto estiver em Windows Mixed Reality, envie comentários por meio de nosso [Hub de comentários](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas de versão – maio de 2019](release-notes-may-2019.md)
* [Notas sobre a versão – outubro de 2018](release-notes-october-2018.md)
* [Notas de versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Histórico de lançamento do driver do controlador de movimento e do headset da realidade misturada ###

esse driver é baixado e instalado automaticamente por meio de Windows Update, mas links de download são fornecidos embutidos:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versão 2004 (atualização de maio de 2020) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 de março de 2021  | compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Atualize a ordem de enrolamento da malha da área oculta para que o HP reverbo G2 seja consistente com outros headsets.</li><li>Aprimoramentos de qualidade de visuais para os fones de ouvido do HP reverbs G2.</li><li>Windows Mixed Reality aperfeiçoamentos de confiabilidade e plataforma de headset.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 de dezembro de 2020  | compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Novo firmware do controlador para o controlador HP para resolver um problema em que alguns controladores têm gatilhos que não funcionam.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 de outubro de 2020  | compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Suporte oficial para o HP reverberate G2, HP Omnicept e o novo controlador HP.</li><li>Correções de exibição secundárias para HP reverbera e Samsung Odyssey + headsets. (Requer a [compilação do sistema operacional 19041,546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) ou superior ou o Builds do [sistema operacional 18362,1110 e 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) ou superior).</li><li>Melhorias na transição de estado de energia do computador da suspensão para reduzir os erros do SWW 1-4.</li><li>Windows Mixed Reality as correções secundárias e melhorias de confiabilidade da plataforma headset.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 de maio de 2020      | compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Windows Mixed Reality as correções secundárias e melhorias de confiabilidade da plataforma headset.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versão 1903 (atualização de maio de 2019) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 de outubro de 2019      | compatível com Windows 10, versão 1809 e mais recente.<br/><ul><li>Windows Mixed Reality as correções secundárias da plataforma headset.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 de junho de 2019      | compatível com Windows 10, versão 1809 e mais recente.<br/><ul><li>Windows Mixed Reality a plataforma headset e aprimoramentos de confiabilidade em computadores de suspensão e transições de estado de energia.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1º de maio de 2019      | compatível com Windows 10, versão 1809 e mais recente.<br/><ul><li>contém atualização de firmware para 2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo e Medion Windows Mixed Reality headsets. Essa atualização de firmware melhora a compatibilidade e a confiabilidade da exibição de fone de ouvido com determinados adaptadores gráficos ou drivers gráficos.</li><li>melhorias de confiabilidade e plataforma do Windows Mixed Reality headset</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versão 1803 (atualização de abril de 2018) e versão 1809 (atualização de outubro de 2018) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 de janeiro de 2019      | compatível com Windows 10, versão 1803 e mais recente.<br/><ul><li>Tremulação de acompanhamento de headset e correções de stutter</li><li>Correções de confiabilidade do modo de lanterna</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 de outubro de 2018      | versão pública inicial do driver para Windows 10, versão 1809.<br/>compatível com Windows 10, versão 1803 e mais recente.<br/><ul><li>habilita novos recursos de Windows Mixed Reality, como o modo de lanterna, em Windows 10, versão 1809</li><li>Melhorias de confiabilidade e acompanhamento de fone de ouvido</li><li>Aprimoramentos de desempenho e rastreamento do controlador de movimento</li><li>Desempenho e melhorias de USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 de abril de 2018      | lançamento público inicial do driver para Windows 10, versão 1803<br/> <ul><li>Melhorias de confiabilidade e acompanhamento de fone de ouvido</li><li>Aprimoramentos de desempenho e rastreamento do controlador de movimento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versão 1709 (atualização para criadores de outono) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 de fevereiro de 2018    | <ul><li>Suporte oficial para 3Glasses Blubur S2 Mixed Reality Headset</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 de dezembro de 2017   | <ul><li>Resolve o problema de HID que leva a *algo que deu errado* no código de erro 2181038087-7 em alguns PCs</li><li>Várias correções de estabilidade e confiabilidade</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 de dezembro de 2017    | <ul><li>Acompanhamento de fone de ouvido aprimorado</li><li>Melhorias de capacidade de resposta do Touchpad do controlador de movimento</li><li>Resolve problemas em que a instalação do driver às vezes poderia falhar</li><li>Várias correções de estabilidade e confiabilidade</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 de novembro de 2017   | <ul><li>Resolve um problema que levou às telas de fone de ouvido às vezes em preto durante o uso</li><li>Resolve um problema que às vezes levou à desapareceção dos controladores de movimento</li><li>Melhorias de desempenho do sensor de presença para o headset do Dell visor</li><li>Várias correções de estabilidade e confiabilidade</li></ul> |
   | 10.0.16299.1036  | 7 de novembro de 2017    | <ul><li>O controlador de movimento gera melhorias mecânicas:<ul><li>A velocidade agora será relatada corretamente quando a precisão da posição for aproximada; portanto, agora você pode jogar por trás da cabeça!</li><li>O código de exemplo para lançamento pode ser encontrado no pacote de Unity "ThrowingStarter" [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Abra a cena de lançamento para começar</li></ul></li><li>Relatório de bateria do controlador de movimento aprimorado</li><li>Várias correções de estabilidade e confiabilidade</li></ul> |
   | 10.0.16299.1012  | 17 de outubro de 2017    | Versão pública inicial do driver                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Histórico de lançamento do driver do modelo de movimento da realidade misturada ###

esse driver também é baixado e instalado automaticamente por meio de Windows Update, mas links de download são fornecidos embutidos:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versão 2004 (atualização de maio de 2020)

| Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 de setembro de 2020      | Versão pública inicial do driver para os novos controladores HP Motion. compatível com Windows 10, versão 1903 e mais recente. Este driver é compatível apenas com os novos controladores HP Motion.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versão 1803 (atualização de abril de 2018) e versão 1809 (atualização de outubro de 2018) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 de outubro de 2018      | versão pública inicial do driver para Windows 10, versão 1809. compatível com Windows 10, versão 1803 e mais recente.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 de abril de 2018      | lançamento público inicial do driver para Windows 10, versão 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versão 1709 (atualização para criadores de outono) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 de outubro de 2017    | Versão pública inicial do driver                          |

### <a name="mixed-reality-portal-release-history"></a>Histórico de lançamento do portal de realidade misturada ###

no Windows 10, versão 1809 e mais recente, o [Portal de realidade misturada](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) é atualizado por meio do aplicativo Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versão 1809 e mais recente ####

   | Versão            | Data de lançamento          | Principais alterações                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 de junho de 2021          | <ul><li>adiciona links de solução de problemas ao aplicativo Obter Ajuda para erros comuns de headset.</li><li>Resolve um problema em que o aplicativo do dispositivo de fone de ouvido pode ser ignorado durante a instalação inicial.</li><li>Atualiza a página requisitos do sistema com informações adicionais para headsets de alta resolução.</li><li>Atualiza a tela inicial e a página de aterrissagem com novos visuais.</li></ul>  |
   | 2000.21041.1051.0  | 26 de abril de 2021        | <ul><li>Atualiza o ícone do aplicativo para o portal de realidade misturada.</li></ul>  |
   | 2000.20111.1381.0  | 10 de dezembro de 2020     | <ul><li>Atualiza a página de aterrissagem do portal de realidade misturada.</li><li>Reduz erros de conectividade de headset durante atualizações de firmware. </li></ul>  |
   | 2000.20071.1133.0  | 5 de agosto de 2020        | <ul><li>Suporte para [OpenXR](/windows/mixed-reality/openxr) para pausar a janela de visualização.</li></ul>  | 
   | 2000.20041.1212.0  | 11 de maio de 2020          | <ul><li>Resolve um problema de tempo que estava resultando em um erro de 15-5 inconsistente.</li><li>suporte aprimorado para execução de Windows Mixed Reality sem conexão com a internet.</li><li>Suporte aprimorado para controladores de movimento de emparelhamento por meio de **controladores de instalação**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 de abril de 2020        | <ul><li>Suporte para inscrever-se para obter informações, dicas e ofertas sobre Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 de fevereiro de 2020     | <ul><li>Suporte aprimorado para aplicativos que usam o [OpenXR](/windows/mixed-reality/openxr) em dispositivos com a atualização de maio de 2019.</li><li>Resolve problemas de acessibilidade e foco de teclado</li></ul>  | 
   | 2000.19101.1211.0  | 11 de novembro de 2019     | <ul><li>Resolve um problema que impede a alternância de visuais de limite de sala.</li><li>Resolve um problema que impede que você centralize um headset durante a configuração de limite de sala.</li></ul>  | 
   | 2000.19081.1301.0  | 23 de setembro de 2019    | <ul><li>Aborda um problema em que os headsets com problemas de hardware foram mostrados como uma mensagem de erro incorreta. Os usuários que receberam um código de erro 1-4 em versões anteriores podem agora receber um código de erro mais específico para o estado do dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 de agosto de 2019     | <ul><li>Suporte para aplicativos que usam o [OpenXR](/windows/mixed-reality/openxr) em dispositivos com a atualização de maio de 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 de julho de 2019         | <ul><li>Suporte para opções de configuração JSON para personalizar o comportamento do aplicativo. Leia mais em https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Histórico de versões do SteamVR ###

As notas de versão da válvula para SteamVR podem ser encontradas aqui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality para o histórico de versões do SteamVR ###

nossas notas de versão para o componente Windows Mixed Reality para SteamVR podem ser encontradas aqui:[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
