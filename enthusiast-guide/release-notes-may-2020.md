---
title: Notas sobre a versão – maio de 2020
description: Mantenha-se atualizado sobre as Windows Mixed Reality de versão do Windows 10 de maio de 2020.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: notas de versão, versão, windows 10, build, 19h1, sistema operacional, maio de 2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439156"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 de versão – maio de 2020

A atualização Windows 10 de maio de **2020 (v2004)** inclui novos recursos para headsets Windows Mixed Reality (VR), como a capacidade de iniciar aplicativos Win32 na casa de realidade misturada. HoloLens (1ª geração) está em LTS (Manutenção de Longo Prazo), com atualizações de manutenção a serem lançadas mensalmente.

Atualizando para Windows Mixed Reality versão mais recente do pc para headsets imersivos (VR), abra Configurações > **Atualizar & Segurança** e selecione Verificar se há **atualizações**. Em um Windows 10, você também pode instalar manualmente o Windows 10 atualização de maio de **2020** usando a Windows de criação [de mídia.](https://www.microsoft.com/software-download/windows10)

**Versão mais recente para Desktop:** Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Atualizações para Windows Mixed Reality headsets imersivos

### <a name="introducing-the-new-microsoft-edge"></a>Apresentando o novo Microsoft Edge

Conforme [anunciado anteriormente,](/windows/mixed-reality/new-microsoft-edge)fizemos atualizações para dar melhor suporte usando o novo navegador Microsoft Edge no Windows Mixed Reality. O novo Microsoft Edge adota o Chromium de software livre para criar melhor compatibilidade com a Web para clientes e menos fragmentação da Web para todos os desenvolvedores da Web. Ele também dá suporte ao WebXR, o novo padrão para criar experiências da Web imersivas para headsets de VR, no lugar de WebVR.

### <a name="improved-settings-for-wmr"></a>Melhoria Configurações para WMR

Graças aos seus comentários, adicionamos e esclarecemos as configurações na página de exibição headset:

* **Qualidade visual da minha casa** – alterar essas configurações afeta apenas o ambiente de casa de realidade misturada (Casa no Penhasco e Skyloft):

* **Ajuste o nível de detalhes e a qualidade** dos efeitos na casa da realidade misturada – isso altera algumas das alterações de renderização que usamos na casa. Em particular, a qualidade visual de materiais diferentes (floresta, concreto e assim por diante) será dimensionado conforme você alterar essa configuração de baixa para alta.

* **Alterar a resolução da** janela do aplicativo – por padrão, a maioria das janelas 2D lançadas na página principal é lançada com uma resolução de 720 p. Embora seja possível reeslizá-los manualmente horizontalmente & verticalmente, você também pode optar por fazer com que todos eles seja lançado em 1080p. Anteriormente, essa opção estava disponível como a opção Muito alta (beta) em Qualidade do visual. Nós o dividimos adequadamente como uma configuração separada agora.

* **Opções de** experiência – essas opções ajustam a experiência de realidade misturada para reduzir a carga em sistemas em que o hardware pode ter dificuldades para acompanhar 90 fps irrestritos. Você pode habilitar ou desabilitar explicitamente essas configurações adicionais ou escolher Windows decidir e permitir que nossa heurística continue decidindo quando ativar e desativar essas configurações.

* **Resolução** – se você tiver um headset de alta resolução como o HP Reverb, damos suporte à execução dele em sua resolução nativa ou a uma resolução reduzida por motivos de desempenho. Os headsets anteriores, como o SamsungSeyy e o Headsety+, só são compatíveis com uma única resolução para que você não possa alterar essa configuração nesses headsets.

* **Taxa de** quadros – agora você pode definir manualmente a taxa de quadros da exibição do headset ou continuar a permitir que Windows use sua heurística para determinar se 60 Hz ou 90 Hz é mais apropriado.

* **Calibragem** – como antes, você pode ajustar o IPD (distância interpupila) se tiver suporte do headset.

* **Alternância de entrada** – alterne o comportamento de alternância de foco de entrada (Win+Y) para ser automático (com base nos comentários do sensor de presença) ou manual.

### <a name="new-cortana-app"></a>Novo Cortana aplicativo

Essa atualização para Windows inclui a versão mais recente do aplicativo Cortana, que atualmente é somente em inglês dos EUA e não dá mais suporte a determinados comandos específicos de realidade misturada, como "Take a picture" e "Take a video". Você pode usar o novo Cortana para iniciar aplicativos e ele também dá suporte a novos comandos voltados para produtividade, como "Quando é minha próxima reunião?" ou "Enviar um email \< name \> para que estou atrasado".
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Atualizações adicionais disponíveis em 19041.546 (lançadas em outubro de 2020)

Essa atualização de manutenção mensal da área de trabalho inclui as seguintes alterações para Windows Mixed Reality dispositivos: 
* Reduz distorções e distorções Windows Mixed Reality exibições montadas com a cabeça (HMD). 
* Adiciona suporte para futuros controladores de Windows Mixed Reality hp. 
* Altera o comportamento da configuração de taxa de atualização de 90 Hz no Windows Mixed Reality para não voltar automaticamente para 60 Hz em determinados casos em que 90 Hz não podem ser obtidos. 

### <a name="help-us-improve"></a>Ajude-nos a melhorar!

Buscamos continuamente melhorar a compatibilidade.  Se você achar que seu aplicativo win32 clássico favorito não está se comportando corretamente enquanto estiver Windows Mixed Reality, envie comentários por meio de nosso [Hub de Comentários.](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – maio de 2019](release-notes-may-2019.md)
* [Notas sobre a versão – outubro de 2018](release-notes-october-2018.md)
* [Notas sobre a versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Suporte ao headset imersivo (link externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Fornecer comentários](/windows/mixed-reality/give-us-feedback)