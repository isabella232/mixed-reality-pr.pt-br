---
title: Visão geral do software e histórico de lançamento
description: Uma visão geral dos principais componentes de software para Windows Mixed Reality, headsets imersivos e seu histórico de lançamento.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, componentes de software, histórico de lançamento, notas de versão, histórico de versão
appliesto:
- Windows 10
ms.openlocfilehash: 2d11a43e96843073bf86919f1c4a10425fa12c00
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741908"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Visão geral do software de Realidade Misturada e histórico de versões

## <a name="introduction-to-mixed-reality-software"></a>Introdução ao software de Realidade Misturada

Windows Mixed Reality consiste nos seguintes principais componentes de software:

1. **Portal de Realidade Misturada**, que fornece a experiência Windows Mixed Reality principal
    * Nas Windows 10 1709 e 1803, o Portal de Realidade Misturada é um componente fundamental do sistema operacional Windows 10 atualizado por meio do Windows Update.
    * No Windows 10 versão 1809 e mais recente, o Portal de Realidade Misturada é atualizado por meio do Microsoft Store aplicativo.
2. O **FOD (pacote** de recursos sob demanda) da Realidade Misturada, baixado e instalado automaticamente durante Portal de Realidade Misturada primeira vez. Mais informações sobre o pacote FOD podem ser encontradas [aqui](/windows/application-management/manage-windows-mixed-reality)
3. O driver do controlador de movimento e **headset** de Realidade Misturada, também conhecido como driver dos Sensores do HoloLens, é o pacote de driver principal que permite que Windows Mixed Reality headsets funcionem com Windows Mixed Reality. Isso é baixado e instalado automaticamente por meio Windows Update primeira vez que o headset de Realidade Misturada é conectado e é atualizado regularmente por meio de Windows Update
4. Os drivers de modelo do controlador de movimento **Realidade Misturada contêm os modelos 3D dos controladores de movimento de Realidade Misturada e necessários para experiências de Realidade Misturada de terceiros. Isso é baixado e instalado automaticamente por meio do Windows Update na primeira vez que os controladores de movimento de Realidade Misturada são emparelhados com seu computador e são atualizados por meio de Windows Update
5. **Windows 10, a versão 1709 (a** Atualização do Fall Creator) ou mais recente contém os principais componentes e tecnologias do sistema operacional que permitem Windows Mixed Reality

O Windows Mixed Reality no SteamVR requer o seguinte software:

6. **O SteamVR**, desenvolvido e mantido pela Valve Corporation que permite aplicativos e jogos de realidade virtual no Steam. Encontre mais informações [aqui](https://go.microsoft.com/fwlink/?linkid=862788)
7. O **Windows Mixed Reality para o componente SteamVR,** que faz a ponte do SteamVR com Windows Mixed Reality. Mais informações sobre esse componente podem ser [encontradas na página Windows Mixed Reality para SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gerenciando seu Windows Mixed Reality headset:

8. O **Aplicativo De Dispositivos** Desempanhado, desenvolvido e mantido por cada um dos fabricantes de headset, fornece uma introdução rápida ao headset Windows Mixed Reality dispositivo. Em headsets com funcionalidade De Bluetooth interno, o aplicativo De dispositivo Companion permite restaurar controladores de movimento para seu emparelhamento Bluetooth de fábrica. Alguns headsets (como SamsungSeyy e Samsung Samsung Bty+) também usam o Aplicativo De Dispositivo Companion para fornecer atualizações de firmware de headset do fabricante do headset. Esse aplicativo é baixado automaticamente na primeira vez que o headset é conectado e pode ser encontrado no Menu Iniciar do Windows.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 de versão – maio de 2020

A Windows 10 de maio de **2020 (v2004)** inclui novos recursos para headsets de VR (Windows Mixed Reality), como a capacidade de iniciar aplicativos Win32 na casa de realidade misturada. O HoloLens (1ª geração) está em LTS (Manutenção de Longo Prazo), com atualizações de manutenção a serem lançadas mensalmente.

Atualizando para a versão mais recente do pc Windows Mixed Reality para headsets imersivos (VR), abra Configurações **> Atualizar & Segurança** e selecione Verificar se há **atualizações**. Em um Windows 10, você também pode instalar manualmente o Windows 10 atualização de maio de **2020** usando a ferramenta de [criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente para Desktop:** Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Atualizações para Windows Mixed Reality headsets imersivos

#### <a name="introducing-the-new-microsoft-edge"></a>Introdução à nova Microsoft Edge

Conforme [anunciado anteriormente,](/windows/mixed-reality/new-microsoft-edge)fizemos atualizações para dar melhor suporte usando o novo navegador Microsoft Edge no Windows Mixed Reality. A nova Microsoft Edge o projeto de software livre Chromium para criar melhor compatibilidade com a Web para clientes e menos fragmentação da Web para todos os desenvolvedores da Web. Ele também dá suporte ao WebXR, o novo padrão para criar experiências da Web imersivas para headsets de VR, no lugar de WebVR.

#### <a name="improved-settings-for-wmr"></a>Configurações aprimoradas para WMR

Graças aos seus comentários, adicionamos e esclarecemos as configurações na página de exibição Headset:

* **Qualidade visual da minha casa** – alterar essas configurações afeta apenas o ambiente doméstico de realidade misturada (Casa no Penhasco e Skyloft):

* **Ajuste o nível de detalhes e a qualidade** dos efeitos na casa da realidade misturada – isso altera algumas das alterações de renderização que usamos na casa. Em particular, a qualidade visual de materiais diferentes (floresta, concreto e assim por diante) será dimensionado conforme você alterar essa configuração de baixa para alta.

* **Alterar a resolução da** janela do aplicativo – por padrão, a maioria das janelas 2D lançadas na página principal é lançada com uma resolução de 720 p. Embora seja possível reeslizá-los manualmente horizontalmente & verticalmente, você também pode optar por fazer com que todos eles tenham sido lançados em 1080p. Anteriormente, essa opção estava disponível como a opção Muito alta (beta) em Qualidade do visual. Nós o dividimos adequadamente como uma configuração separada agora.

* **Opções de** experiência – essas opções ajustam a experiência de realidade misturada para reduzir a carga em sistemas em que o hardware pode ter dificuldades para acompanhar 90 fps irrestritos. Você pode habilitar ou desabilitar explicitamente essas configurações adicionais ou escolher Permitir que o Windows decida e permita que nossa heurística continue decidindo quando ativar e desativar essas configurações.

* **Resolução** – se você tiver um headset de alta resolução como o HP Reverb, damos suporte à execução dele em sua resolução nativa ou a uma resolução reduzida por motivos de desempenho. Os headsets anteriores, como Samsung Bty eSeyy+, só são compatíveis com uma única resolução para que você não possa alterar essa configuração nesses headsets.

* **Taxa de** quadros – agora você pode definir manualmente a taxa de quadros da exibição do headset ou continuar a permitir que o Windows use sua heurística para determinar se 60 Hz ou 90 Hz é mais apropriado.

* **Calibragem** – como antes, você pode ajustar o IPD (distância interpupila) se tiver suporte do headset.

* **Alternância de entrada** – alterne o comportamento de alternância de foco de entrada (Win+Y) para ser automático (com base nos comentários do sensor de presença) ou manual.

#### <a name="new-cortana-app"></a>Novo aplicativo Cortana

Essa atualização para o Windows inclui a versão mais recente do aplicativo Cortana, que atualmente é somente em inglês dos EUA e não dá mais suporte a determinados comandos específicos de realidade misturada, como "Take a picture" e "Take a video". Você pode usar a nova Cortana para iniciar aplicativos e ela também dá suporte a novos comandos voltados para produtividade, como "Quando é minha próxima reunião?" ou "Enviar um email <name> para que estou atrasado".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Atualizações adicionais disponíveis em 19041.546 (lançadas em outubro de 2020)

Essa atualização de manutenção mensal da área de trabalho inclui as seguintes alterações para Windows Mixed Reality dispositivos: 
* Reduz distorções e distorções em Windows Mixed Reality hmd (exibições montadas com a cabeça). 
* Adiciona suporte para futuros controladores de Windows Mixed Reality HP. 
* Altera o comportamento da configuração de taxa de atualização de 90 Hz no Windows Mixed Reality para não voltar automaticamente para 60 Hz em determinados casos em que 90 Hz não podem ser obtidos. 

#### <a name="help-us-improve"></a>Ajude-nos a melhorar!

Buscamos continuamente melhorar a compatibilidade.  Se você achar que seu aplicativo win32 clássico favorito não está se comportando corretamente enquanto estiver Windows Mixed Reality, envie comentários por meio de nosso [Hub de Comentários.](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

### <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – maio de 2019](release-notes-may-2019.md)
* [Notas sobre a versão – outubro de 2018](release-notes-october-2018.md)
* [Notas sobre a versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Histórico de lançamento do driver do controlador de movimento e headset de Realidade Misturada ###

Esse driver é baixado e instalado automaticamente por meio Windows Update, mas os links de download são fornecidos em linha:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versão 2004 (atualização de maio de 2020) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 de março de 2021  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Atualize a ordem de venda da malha de área oculta para que o HP Reverb G2 seja consistente com outros headsets.</li><li>Melhorias de qualidade de visuais para os headsets HP Reverb G2.</li><li>Windows Mixed Reality plataforma de headset e melhorias de confiabilidade.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 de dezembro de 2020  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Novo firmware do controlador para o controlador HP resolver um problema em que alguns controladores têm gatilhos que não estão funcionando.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 de outubro de 2020  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Suporte oficial para o HP Reverb G2, HP Omnicept e o novo controlador hp.</li><li>Correções secundárias de exibição para headsets HP Reverb e SamsungSeyy+. (Requer o build do sistema operacional [19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) ou superior ou builds do sistema operacional [18362.1110 e 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) ou superior).</li><li>Melhorias na transição de estado de energia do computador do sleep para reduzir erros de SWW 1 a 4.</li><li>Windows Mixed Reality pequenas correções de plataforma de headset e melhorias de confiabilidade.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 de maio de 2020      | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Melhorias de confiabilidade e correções do Windows Mixed Reality headset.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versão 1903 (atualização de maio de 2019) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 de outubro de 2019      | Compatível com o Windows 10, versão 1809 e mais recente.<br/><ul><li>Pequenas correções da plataforma Headset do Windows Mixed realm.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 de junho de 2019      | Compatível com o Windows 10, versão 1809 e mais recente.<br/><ul><li>Plataforma de headset do Windows Mixed Realm fone de ouvido e melhorias de confiabilidade em computadores de suspensão e transições de estado de energia.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1º de maio de 2019      | Compatível com o Windows 10, versão 1809 e mais recente.<br/><ul><li>Contém atualização de firmware para os headsets 2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo e Medion Windows Mixed Reality. Essa atualização de firmware melhora a compatibilidade e a confiabilidade da exibição de fone de ouvido com determinados adaptadores gráficos ou drivers gráficos.</li><li>Melhorias de confiabilidade e plataforma do Windows Mixed Reality Headset</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versão 1803 (atualização de abril de 2018) e versão 1809 (atualização de outubro de 2018) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 de janeiro de 2019      | Compatível com o Windows 10, versão 1803 e mais recente.<br/><ul><li>Tremulação de acompanhamento de headset e correções de stutter</li><li>Correções de confiabilidade do modo de lanterna</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 de outubro de 2018      | Lançamento público inicial do driver para Windows 10, versão 1809.<br/>Compatível com o Windows 10, versão 1803 e mais recente.<br/><ul><li>Habilita novos recursos do Windows Mixed Reality, como o modo de lanterna, no Windows 10, versão 1809</li><li>Melhorias de confiabilidade e acompanhamento de fone de ouvido</li><li>Aprimoramentos de desempenho e rastreamento do controlador de movimento</li><li>Desempenho e melhorias de USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 de abril de 2018      | Versão pública inicial do driver para Windows 10, versão 1803<br/> <ul><li>Melhorias de confiabilidade e acompanhamento de fone de ouvido</li><li>Aprimoramentos de desempenho e rastreamento do controlador de movimento</li></ul>  |

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

Esse driver também é baixado e instalado automaticamente por meio de Windows Update, mas links de download são fornecidos embutidos:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versão 2004 (atualização de maio de 2020)

| Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 de setembro de 2020      | Versão pública inicial do driver para os novos controladores HP Motion. Compatível com o Windows 10, versão 1903 e mais recente. Este driver é compatível apenas com os novos controladores HP Motion.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versão 1803 (atualização de abril de 2018) e versão 1809 (atualização de outubro de 2018) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 de outubro de 2018      | Lançamento público inicial do driver para Windows 10, versão 1809. Compatível com o Windows 10, versão 1803 e mais recente.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 de abril de 2018      | Lançamento público inicial do driver para Windows 10, versão 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versão 1709 (atualização para criadores de outono) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 de outubro de 2017    | Versão pública inicial do driver                          |

### <a name="mixed-reality-portal-release-history"></a>Portal de Realidade Misturada de lançamento ###

No Windows 10, versão 1809 e mais novos, [o Portal de Realidade Misturada](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) é atualizado por meio do Microsoft Store aplicativo.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versão 1809 e mais novos ####

   | Versão            | Data de lançamento          | Principais alterações                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 de junho de 2021          | <ul><li>Adiciona links de solução de problemas ao aplicativo Obter Ajuda para erros comuns de headset.</li><li>Resolve um problema em que o aplicativo de dispositivo de headset pode ser ignorado durante a configuração inicial.</li><li>Atualiza a página de requisitos do sistema com informações adicionais para headsets de alta resolução.</li><li>Atualiza a tela inicial e a página de aterrissagem com novos visuais.</li></ul>  |
   | 2000.21041.1051.0  | 26 de abril de 2021        | <ul><li>Atualiza o ícone do aplicativo para Portal de Realidade Misturada.</li></ul>  |
   | 2000.20111.1381.0  | 10 de dezembro de 2020     | <ul><li>Atualiza a página de aterrissagem do Portal de Realidade Misturada.</li><li>Reduz erros de conectividade do headset durante atualizações de firmware. </li></ul>  |
   | 2000.20071.1133.0  | 5 de agosto de 2020        | <ul><li>Suporte para [OpenXR](/windows/mixed-reality/openxr) pausar a janela de visualização.</li></ul>  | 
   | 2000.20041.1212.0  | 11 de maio de 2020          | <ul><li>Resolve um problema de tempo que estava resultando em um erro inconsistente de 15 a 5.</li><li>Suporte aprimorado para executar Windows Mixed Reality sem conexão com a Internet.</li><li>Suporte aprimorado para emparelhar controladores de movimento por meio **de controladores de instalação**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 de abril de 2020        | <ul><li>Suporte para inscrição para obter informações, dicas e ofertas sobre Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 de fevereiro de 2020     | <ul><li>Suporte aprimorado para aplicativos [que usam OpenXR](/windows/mixed-reality/openxr) em dispositivos com a Atualização de maio de 2019.</li><li>Aborda problemas de acessibilidade e foco do teclado</li></ul>  | 
   | 2000.19101.1211.0  | 11 de novembro de 2019     | <ul><li>Resolve um problema que impede a agregação de visuais de limite da sala.</li><li>Resolve um problema que impede que você centralmente um headset durante a configuração de limite da sala.</li></ul>  | 
   | 2000.19081.1301.0  | 23 de setembro de 2019    | <ul><li>Aborda um problema em que os headsets com problemas de hardware eram mostrados com uma mensagem de erro incorreta. Os usuários que receberam um código de erro de 1 a 4 em versões anteriores agora podem receber um código de erro mais específico para o estado do dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 de agosto de 2019     | <ul><li>Suporte para aplicativos [que usam OpenXR](/windows/mixed-reality/openxr) em dispositivos com a Atualização de maio de 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 de julho de 2019         | <ul><li>Suporte para opções de configuração JSON para personalizar o comportamento do aplicativo. Leia mais em https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Histórico de lançamento do SteamVR ###

As notas de versão da válvula para o SteamVR podem ser encontradas aqui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality para o histórico de lançamento do SteamVR ###

Nossas notas de versão para o Windows Mixed Reality para o componente SteamVR podem ser encontradas aqui: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
