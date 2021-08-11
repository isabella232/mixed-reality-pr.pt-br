---
title: Modo de pesquisa do HoloLens
description: Usando o Modo de Pesquisa no HoloLens, um aplicativo pode acessar os principais fluxos de sensor do dispositivo (profundidade, acompanhamento de ambiente e refletividade de IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de Pesquisa, cv, rs4, pesquisa visual computacional, pesquisa HoloLens, HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193672"
---
# <a name="hololens-research-mode"></a>Modo de pesquisa do HoloLens

O Modo de Pesquisa foi introduzido em HoloLens (1ª geração) para dar acesso aos principais sensores, especificamente para aplicativos de pesquisa que não se destinam à implantação.  O Modo de Pesquisa HoloLens 2 mantém as funcionalidades do HoloLens 1, mas adiciona acesso aos seguintes fluxos:

* **Câmeras de acompanhamento de ambiente claro visíveis** – câmeras em escala de cinza usadas pelo sistema para o acompanhamento de cabeça e a criação de mapas.
* **Câmera de profundidade** – opera em dois modos:  
    + AHAT, detecção de profundidade próxima de 45 FPS (alta frequência) usada para acompanhamento de mão. Diferentemente do modo de lançamento curto da primeira versão, o AHAT fornece pseudo profundidade com quebra de fase além de 1 medidor. 
    + Detecção de profundidade profunda de lançamento longo e baixa frequência (1 a 5 FPS) usada pelo [Mapeamento Espacial](../../design/spatial-mapping.md)

* **Duas versões do fluxo de reflexão de IR** – usadas pelo HoloLens para calcular a profundidade. Essas imagens são ilustradas por lâmpadas e não afetadas pela luz visível do ambiente.

Se você estiver usando um HoloLens 2, também terá acesso às entradas adicionais abaixo:

* **Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.
* **Girote** – usado pelo sistema para determinar as rotações.
* **Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.

> [!IMPORTANT]
> O Modo de Pesquisa está atualmente em Visualização Pública. 

![Captura de tela do aplicativo modo de pesquisa](images/sensor-stream-viewer.jpg)<br>
*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no Modo de Pesquisa*

## <a name="usage"></a>Uso

O Modo de Pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e Robótica.  Ele não se destina a aplicativos implantados em ambientes empresariais ou disponíveis por meio do Microsoft Store ou outros canais de distribuição.

Além disso, a Microsoft não fornece garantias de que o Modo de Pesquisa ou a funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional. No entanto, não deixe que isso o pare de usá-lo para desenvolver e testar novas ideias!

## <a name="security-and-performance"></a>Segurança e desempenho

A habilitação do Modo de Pesquisa usa mais energia da bateria do que o HoloLens 2 em condições normais, mesmo se o aplicativo que usa os recursos do Modo de Pesquisa não estiver em execução.  A habilitação desse modo também pode reduzir a segurança geral do seu dispositivo porque os aplicativos podem usar indevidamente os dados do sensor.  Você pode encontrar mais informações sobre a segurança do dispositivo [nas Perguntas frequentes HoloLens segurança.](/hololens/hololens-faq-security)  

## <a name="device-support"></a>Suporte a dispositivos
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Câmeras de acompanhamento de cabeça</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profundidade & ir câmera</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Acelerômetro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Giroscópio</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnetômetro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Habilitando o modo de pesquisa (HoloLens primeira geração e HoloLens 2)

O Modo de Pesquisa é uma extensão do Modo de Desenvolvedor. Antes de começar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do Modo de Pesquisa: 

* Abra **o Menu Iniciar > Configurações** e selecione **Atualizações**.
* Selecione **Para Desenvolvedores e** habilita o Modo de **Desenvolvedor.**
* Role para baixo e habilite o **Portal de Dispositivos**.

Depois que os recursos do desenvolvedor estão habilitados, [conecte-se ao portal do dispositivo](/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do Modo de Pesquisa:

* Vá para **o Modo > Pesquisa do Sistema** no **Portal de Dispositivos**.
* Selecione **Permitir acesso ao fluxo do sensor.**
* Reinicie o dispositivo do item **de** menu Energia na parte superior da página.

Depois de reiniciar o dispositivo, os aplicativos carregados por meio do **Portal de Dispositivos** podem acessar fluxos do Modo de Pesquisa.

![Guia Modo de Pesquisa HoloLens Portal de Dispositivos](images/ResearchModeDevPortal.png)<br>
*Janela Modo de Pesquisa no HoloLens Portal de Dispositivos*

> [!IMPORTANT]
> O Modo de Pesquisa HoloLens 2 está disponível a partir do build 19041.1364 . Se você precisar de acesso em um build anterior, inscreva-se em nosso [programa Insider Preview.](/hololens/hololens-insider) Você pode encontrar mais detalhes no repositório [GitHub Pesquisa](https://github.com/microsoft/HoloLens2ForCV).

### <a name="using-sensor-data-in-your-apps"></a>Usando dados de sensor em seus aplicativos

Os aplicativos podem acessar os dados de fluxo do sensor da mesma [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) acessa os fluxos de câmera de fotos e vídeos. 

Todas as APIs que funcionam para HoloLens desenvolvimento também estão disponíveis no Modo de Pesquisa. Em particular, o aplicativo sabe exatamente onde HoloLens está no espaço 6DoF em cada tempo de captura de quadro do sensor.

Temos aplicativos de exemplo mostrando o acesso ao fluxo do Modo de Pesquisa, usando [intrínsecos](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e extrínsecos e fluxos de gravação:
* [HoloLens (primeira geração)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Suporte

Por HoloLens (primeira geração), use [](https://github.com/Microsoft/HololensForCV/issues) o rastreador de problemas no repositório HoloLensForCV para postar comentários e acompanhar problemas conhecidos.

Por HoloLens 2, use [](https://github.com/microsoft/HoloLens2ForCV/issues) o rastreador de problemas no repositório HoloLens2ForCV para postar comentários e acompanhar problemas conhecidos.

## <a name="see-also"></a>Confira também

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [GitHub de GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub repo](https://github.com/microsoft/HoloLens2ForCV)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)