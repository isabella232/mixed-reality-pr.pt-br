---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de pesquisa, CV, RS4, pesquisa Visual computacional, Research, HoloLens, HoloLens 2
ms.openlocfilehash: c8e626969f87eda8b686ba759a167a2bf48e3277
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583137"
---
# <a name="hololens-research-mode"></a>Modo de pesquisa do HoloLens

O modo de pesquisa foi introduzido nos dispositivos HoloLens (1º gen) para dar acesso aos principais sensores, especificamente para aplicativos de pesquisa que não se destinam à implantação.  O modo de pesquisa para o HoloLens 2 mantém os recursos do HoloLens 1, mas adiciona acesso aos seguintes fluxos:

* **Câmeras de acompanhamento de ambiente leve visíveis** – câmeras em escala cinza usadas pelo sistema para rastreamento de cabeçalho e criação de mapa.
* **Câmera de profundidade** – opera em dois modos:  
    + Detecção de AHAT, alta frequência (45 FPS) usada para acompanhamento à mão. Diferentemente do modo de curto-throw da primeira versão, AHAT dá uma pseudo profundidade com o encapsulamento de fase além de 1 medidor. 
    + Detecção de longo alcance, de baixa frequência (1-5 FPS) de longa profundidade usada pelo [mapeamento espacial](../../design/spatial-mapping.md)

* **Duas versões do fluxo ir-reflectivity** -usadas pelo HoloLens para calcular a profundidade. Essas imagens são iluminadas por infravermelho e não são afetadas pela luz visível de ambiente.

Se você estiver usando um HoloLens 2, também terá acesso às entradas adicionais abaixo:

* **Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.
* **Giro** – usado pelo sistema para determinar rotações.
* **Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.

> [!IMPORTANT]
> O modo de pesquisa está atualmente em visualização pública. 

![Captura de tela do aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)<br>
*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*

## <a name="usage"></a>Uso

O modo de pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e robótica.  Ele não se destina a aplicativos implantados em ambientes corporativos ou disponíveis por meio do Microsoft Store ou de outros canais de distribuição.

Além disso, a Microsoft não fornece garantias de que o modo de pesquisa ou funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional. No entanto, não deixe que o impeça de usá-lo para desenvolver e testar novas ideias!

## <a name="security-and-performance"></a>Segurança e desempenho

Habilitar o modo de pesquisa usa mais energia da bateria do que usar o HoloLens 2 em condições normais, mesmo que o aplicativo que usa os recursos do modo de pesquisa não esteja em execução.  Habilitar esse modo também pode reduzir a segurança geral do seu dispositivo, pois os aplicativos podem indevidamente os dados do sensor.  Você pode encontrar mais informações sobre a segurança do dispositivo nas [perguntas frequentes sobre segurança do HoloLens](/hololens/hololens-faq-security).  

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
        <td>Câmeras de acompanhamento de cabeçalho</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profundidade & câmera IR</td>
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

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Habilitando o modo de pesquisa (primeiro HoloLens Gen e HoloLens 2)

O modo de pesquisa é uma extensão do modo de desenvolvedor. Antes de iniciar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do modo de pesquisa: 

* Abra o **menu iniciar > configurações** e selecione **atualizações**.
* Selecione **para desenvolvedores** e habilite o **modo de desenvolvedor**.
* Role para baixo e habilite o **Portal de Dispositivos**.

Depois que os recursos do desenvolvedor estiverem habilitados, [Conecte-se ao portal do dispositivo](/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do modo de pesquisa:

* Vá para o **sistema > modo de pesquisa** no **portal do dispositivo**.
* Selecione **permitir acesso ao fluxo do sensor**.
* Reinicie o dispositivo a partir do item de menu de **energia** na parte superior da página.

Depois de reiniciar o dispositivo, os aplicativos carregados por meio do portal do **dispositivo** poderão acessar os fluxos do modo de pesquisa.

![Guia modo de pesquisa do portal do dispositivo do HoloLens](images/ResearchModeDevPortal.png)<br>
*Janela do modo de pesquisa no portal do dispositivo do HoloLens*

> [!IMPORTANT]
> O modo de pesquisa para o HoloLens 2 está disponível a partir do Build 19041,1356. Se você precisar de acesso em uma compilação anterior, Inscreva-se em nosso programa [Insider Preview](/hololens/hololens-insider) .

### <a name="using-sensor-data-in-your-apps"></a>Usando dados de sensor em seus aplicativos

Os aplicativos podem acessar os dados de fluxo do sensor da mesma maneira que [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) acessa fluxos de foto e de câmera de vídeo. 

Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa. Em particular, o aplicativo sabe precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.

Temos aplicativos de exemplo mostrando acesso de fluxo do modo de pesquisa, usando [intrínsecos e extrínsecos](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), e gravando fluxos:
* [HoloLens (primeira gen)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Suporte

Para o HoloLens (primeira gen), use o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV para postar comentários e acompanhar problemas conhecidos.

Para o HoloLens 2, use o Issue [Tracker](https://github.com/microsoft/HoloLens2ForCV/issues) no repositório HoloLens2ForCV para postar comentários e acompanhar problemas conhecidos.

## <a name="see-also"></a>Confira também

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [Repositório GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Repositório GitHub HoloLens2ForCV](https://github.com/microsoft/HoloLens2ForCV)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)