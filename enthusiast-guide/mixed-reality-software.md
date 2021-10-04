---
title: Visão geral do software e histórico de lançamento
description: Uma visão geral dos principais componentes de software para Windows Mixed Reality, headsets imersivos e seu histórico de lançamento.
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, componentes de software, histórico de lançamento, notas de versão, histórico de versão
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: e20b2075e45620a7533dbb2d369d00e73b98f9c7
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436623"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Visão geral do software de Realidade Misturada e histórico de versões

## <a name="introduction-to-mixed-reality-software"></a>Introdução ao software de Realidade Misturada

Windows Mixed Reality consiste nos seguintes principais componentes de software:

1. **Portal de Realidade Misturada**, que fornece a experiência Windows Mixed Reality principal
    * Nas Windows 10 1709 e 1803, o Portal de Realidade Misturada é um componente fundamental do sistema operacional Windows 10 atualizado por meio da Windows Update.
    * No Windows 10 versão 1809 e mais recente, o Portal de Realidade Misturada é atualizado por meio do Microsoft Store aplicativo.
    * Na Windows 11 versão 21H2.
2. O **FOD (pacote** de recursos sob demanda) da Realidade Misturada, baixado e instalado automaticamente durante a primeira Portal de Realidade Misturada da primeira vez. Mais informações sobre o pacote FOD podem ser encontradas [aqui](/windows/application-management/manage-windows-mixed-reality)
3. O driver do **controlador** de movimento e headset de Realidade Misturada, também conhecido como driver HoloLens Sensors, é o pacote de driver principal que permite que Windows Mixed Reality headsets funcionem com Windows Mixed Reality. Isso é baixado e instalado automaticamente por meio do Windows Atualizar na primeira vez que o headset de Realidade Misturada é conectado e é atualizado regularmente por meio do Windows Update
4. Os drivers de modelo do controlador de movimento **Realidade Misturada contêm os modelos 3D dos controladores de movimento de Realidade Misturada e necessários para experiências de Realidade Misturada de terceiros. Isso é baixado e instalado automaticamente por meio do Windows Atualizar na primeira vez que os controladores de movimento de Realidade Misturada são emparelhados com o computador e são atualizados por meio de Windows Update
5. **Windows 10, a versão 1709 (a** Atualização do Fall Creator) ou mais recente contém os principais componentes e tecnologias do sistema operacional que permitem Windows Mixed Reality

Usar Windows Mixed Reality no SteamVR requer o seguinte software:

6. **O SteamVR**, desenvolvido e mantido pela Valve Corporation que permite aplicativos e jogos de realidade virtual no Steam. Encontre mais informações [aqui](https://go.microsoft.com/fwlink/?linkid=862788)
7. O **Windows Mixed Reality para o componente SteamVR,** que faz a ponte do SteamVR com Windows Mixed Reality. Mais informações sobre esse componente podem ser [encontradas na página Windows Mixed Reality para SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gerenciando seu Windows Mixed Reality headset:

8. O **Aplicativo De Dispositivos** Desempanhado, desenvolvido e mantido por cada um dos fabricantes de headset, fornece uma rápida introdução ao headset Windows Mixed Reality dispositivo. Em headsets com capacidade de Bluetooth interno, o aplicativo Device Companion permite restaurar controladores de movimento para seu emparelhamento de Bluetooth fábrica. Alguns headsets (como SamsungSeyy e Samsung Headsety+) também usam o Dispositivo Companion App para fornecer atualizações de firmware de headset do fabricante do headset. Esse aplicativo é baixado automaticamente na primeira vez que o headset é conectado e pode ser encontrado no menu Windows Iniciar.

## <a name="windows-11-release-notes---october-2021"></a>Windows 11 notas de versão – outubro de 2021

### <a name="infinite-expanse"></a>Expansão infinita

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* Novo ambiente de home virtual para Windows Mixed Reality dispositivos que apresentam uma redução significativa no escopo e no tamanho, simplificados até o estágio singular, em vez daHouse mais rica em recursos. 
* Criada com o desempenho em mente, a Expansão Infinita foi projetada para atender às solicitações de clientes de longa duração para um ambiente de casa virtual com menos uso de recursos que permite aos clientes obter o melhor desempenho de seus jogos e experiências. 
* Esse novo ambiente de home virtual pode ser encontrado no Painel **de Pinos** **no** menu Locais. 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>Inicialização do SteamVR com Portal de Realidade Misturada inicialização

* Nova configuração disponível para iniciar automaticamente o SteamVR quando o WMR for lançado, permitindo que você ignore o espaço de residência do WMR e pule diretamente para o SteamVR.
   * Essa nova configuração pode ser encontrada no aplicativo **Configurações** em Realidade Misturada > Inicialização e Área de Trabalho > **Inicialização Automática.**
    
### <a name="new-startup-experience-settings"></a>Novas configurações de experiência de inicialização

* Novas configurações disponíveis para definir melhor sua experiência de inicialização ideal aumentando o nível de controle sobre quando Portal de Realidade Misturada inicializa.
* Agora você pode controlar se o Portal de Realidade Misturada inicia quando um dispositivo está conectado ou quando o sensor de presença é ativado, bem como controlar como o aplicativo da Área de Trabalho virtual é aberto.
* Essas novas configurações podem ser encontradas no aplicativo **Configurações** em Realidade **Misturada > Inicialização e Área de Trabalho**
    * Alterne para iniciar o MRP no plug-in HMD.
    * Alterne para iniciar o MRP quando a presença for detectada.
    * Alterne o aplicativo Abrir Área de Trabalho no foco do aplicativo da área de trabalho.

### <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – maio de 2020](release-notes-may-2020.md)
* [Notas sobre a versão – maio de 2019](release-notes-may-2019.md)
* [Notas sobre a versão – outubro de 2018](release-notes-october-2018.md)
* [Notas sobre a versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Histórico de lançamento do driver do controlador de movimento e headset de Realidade Misturada ###

Esse driver é baixado e instalado automaticamente por meio do Windows Update, mas os links de download são fornecidos em linha:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versão 2004 (atualização de maio de 2020) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 de março de 2021  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Atualize a ordem de venda da malha de área oculta para que o HP Reverb G2 seja consistente com outros headsets.</li><li>Melhorias de qualidade de visuais para os headsets HP Reverb G2.</li><li>Windows Mixed Reality plataforma de headset e melhorias de confiabilidade.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 de dezembro de 2020  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Novo firmware do controlador para o controlador HP resolver um problema em que alguns controladores têm gatilhos que não estão funcionando.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 de outubro de 2020  | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Suporte oficial para o HP Reverb G2, HP Omnicept e o novo controlador hp.</li><li>Correções secundárias de exibição para headsets HP Reverb e SamsungSeyy+. (Requer o build do sistema operacional [19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) ou superior ou builds do sistema operacional [18362.1110 e 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) ou superior).</li><li>Melhorias na transição do estado de energia do computador do sleep para reduzir erros de SWW 1 a 4.</li><li>Windows Mixed Reality pequenas correções e melhorias de confiabilidade da plataforma de headset.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 de maio de 2020      | Compatível com Windows 10, versão 1903 e mais recente.<br/><ul><li>Windows Mixed Reality pequenas correções e melhorias de confiabilidade da plataforma de headset.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versão 1903 (atualização de maio de 2019) ####

   | Versão          | Data de lançamento          | Principais alterações                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 de outubro de 2019      | Compatível com Windows 10, versão 1809 e mais novos.<br/><ul><li>Windows Mixed Reality pequenas correções da plataforma de headset.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 de junho de 2019      | Compatível com Windows 10, versão 1809 e mais novos.<br/><ul><li>Windows Mixed Reality plataforma de headset e melhorias de confiabilidade em relação a computadores em espera e transições de estado de energia.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1º de maio de 2019      | Compatível com Windows 10, versão 1809 e mais novos.<br/><ul><li>Contém a atualização de firmware para headsets Acer, Asus, Dell, Fu firmware, HP, Lenovo e Medion 2017 Windows Mixed Reality headsets. Essa atualização de firmware melhora a compatibilidade e a confiabilidade da exibição do headset com determinados adaptadores gráficos ou drivers gráficos.</li><li>Windows Mixed Reality plataforma de headset e melhorias de confiabilidade</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versão 1803 (Atualização de abril de 2018) e versão 1809 (atualização de outubro de 2018) ####

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
   | 2000.19061.1011.0  | 16 de julho de 2019         | <ul><li>Suporte para opções de configuração JSON para personalizar o comportamento do aplicativo. Leia mais na [instalação do entretenimento baseado no local com o Windows Mixed Reality](/windows/mixed-reality/location-based-experiences#setup).</li></ul>  | 

### <a name="steamvr-release-history"></a>Histórico de versões do SteamVR ###

As notas de versão da válvula para SteamVR podem ser encontradas aqui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality para o histórico de versões do SteamVR ###

nossas notas de versão para o componente Windows Mixed Reality para SteamVR podem ser encontradas aqui:[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
