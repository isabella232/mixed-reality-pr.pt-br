---
title: Focar com a cabeça e esperar
description: Comece com uma visão geral do olhar e do modelo de entrada de duração, incluindo cenários comuns e princípios de design.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade mista, UX, diretrizes, exibição de lista
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007076"
---
# <a name="head-gaze-and-dwell"></a>Focar com a cabeça e esperar

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis. Os comandos de voz, assim como os gestos, podem não ser confiáveis em determinados contextos (por exemplo, em ambientes excessivamente barulhentos). Além disso, usar a voz para controlar computadores não é universalmente comum, mas certamente está ganhando força! O modelo de focar com a cabeça e esperar oferece o mecanismo mais familiar e fácil de dominar para trabalhar sem utilizar as mãos no HoloLens. Além disso, esse modelo é 100% confiável, independentemente da interferência de ruído e das restrições de silêncio do ambiente operacional.

## <a name="scenarios"></a>Cenários

O Head-olhar e a pesquisa são ótimos em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas. O recurso também é útil quando a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais. Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro. Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor. O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz. O Head-olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho. 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Focar com a cabeça e esperar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>


## <a name="design-principles"></a>Princípios de design

**Evitar "Mirar como uma arma"**

A ação de focar com a cabeça e esperar exige que o retorno visual seja intuitivo, mas seu excesso pode induzir a ansiedade. Os comentários devem ajudar um usuário a saber o que eles estão direcionando, mas não selecioná-lo em sua intenção. Ao ler texto, ícones e rótulos, você precisa fornecer ao usuário tempo para absorver as informações antes de selecionar.
    
**Buscar a velocidade ideal**
    
As interações de espera podem ter tempos diferentes com base no impacto na navegação: as funções usadas com mais frequência geralmente se beneficiam de tempos de preenchimento mais rápidos, enquanto que as funções mais consequentes podem se beneficiar de tempos de preenchimento mais longos. Ao usar um efeito de preenchimento para mostrar esses tempos, curvas de animação da cor de preenchimento podem influenciar positivamente uma sensação de tempo mais rápido. Consideração deve ser tomada para permitir a decisão do usuário a partir de substituições das velocidades de preenchimento rápidas/médias/lentas.
    
**Acabar com o efeito ioiô**

O efeito de Yo-Yo é um padrão de movimento de cabeça desconfortável que ocorre quando os controles de colocação de conteúdo e de cabeçalho/olhar de pesquisa forçam as pessoas a Pesquisar e reduzir repetidamente. Por exemplo, uma barra de navegação de lista com o botão de olhar e de duração na parte inferior induzi um loop de-Olhe para a pesquisa, pesquisa em resultados, olha para a pesquisa e assim por diante. O padrão resultante é desconfortável, portanto, é recomendável colocar controles de navegação em um local centralizado que exija menos suporte. O posicionamento de botões de pesquisa com base em seus efeitos se torna importante para o conforto.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Diretrizes e práticas recomendadas para a experiência do usuário

### <a name="target-sizes"></a>Tamanhos do alvo

Para ser facilmente acessível, os destinos de olhar e de pesquisa precisam ser grandes o suficiente para examinar confortavelmente e manter uma cabeça estável no destino pelo tempo prescrito. Recomendamos um tamanho mínimo de destino de 2 graus para alcançar a experiência mais confortável. 

### <a name="visual-feedback"></a>Feedback visual

Ao usar um preenchimento radial para representar o tempo de espera, comece do centro do botão. Uma resposta consistente é menos confusa que diferentes direções em botões diferentes. 

  * Essa regra pode ser quebrada no entanto para interações direcionais (por exemplo, NAV up/down/esquerda/direita e assim por diante). Por exemplo, os Guias do Microsoft Dynamics 365 fazem uma exceção a essa regra nos botões AVANÇAR/VOLTAR, que são preenchidos da esquerda para a direita.
  * Considere inverter o preenchimento radial de fora, para cenários como alternar para fora de um botão. A sensação inversa de apertar um botão é um padrão visual adequado para manter. 

### <a name="progressive-disclosure"></a>Divulgação progressiva

A divulgação progressiva significa mostrar apenas a quantidade de detalhes relevante em cada estágio de uma interação. Para a pesquisa, isso significa que o destino de pesquisa é revelado no realce (por exemplo, em um controle de lista).

 ### <a name="oversized-targets"></a>Alvos muito grandes

A região de espera pode ser maior do que o ícone inativo para facilitar o uso, como o botão Voltar nos Guias do Microsoft Dynamics 365.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evite a cintilação usando retornos atrasados

Aplique um pequeno atraso antes de iniciar o retorno visual para evitar cintilação ao passar sobre um alvo de espera.
* Para botões interagir com frequência, mantenha o atraso curto para que o aplicativo se sinta reativo.
* Para botões que são interagindo com pouca frequência, um atraso mais longo pode ser apropriado para evitar que a interface se sinta twitchy.

<br>

---

## <a name="ui-patterns"></a>Padrões da interface do usuário

### <a name="high-frequency-buttons"></a>Botões de alta frequência

:::row:::
    :::column:::
        Botões de alta frequência são botões que são usados normalmente em um aplicativo. Um bom exemplo são os botões Voltar e Avançar nos Guias do Microsoft Dynamics 365.<br>
        <br>
        **Recomendações**<br>
  * Botões de alta frequência devem ser grandes, mais fáceis de atingir com Head-olhar
  * Fique à altura dos olhos para evitar sobrecarregar o ergonômicos.<br>
        <br>
*Imagem: botão Avançar dos guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Botão Avançar dos guias do Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Botões de baixa frequência

Os botões de baixa frequência são botões que não são interagindo com o mais regular em todo o aplicativo. Um bom exemplo é um botão para acessar o menu de configurações ou um botão para limpar toda a tarefa.

* Tente manter esses botões longe dos caminhos de ações frequentes de focar com a cabeça para evitar ativação acidental. 

<br>

---

### <a name="confirmations"></a>Confirmações

:::row:::
    :::column:::
        Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluir trabalho ou iniciar um longo processo, é útil confirmar que uma pessoa pretendia selecionar um botão.<br>
        <br>
        **Recomendações**<br>
  * Mostre o realce de seleção no botão principal.
  * Revele o alvo da espera ao mesmo tempo que o realce da seleção.
  * Para o botão secundário, revele o alvo da espera ao focar com a cabeça.<br>
        <br>
*Imagem: caixa de diálogo de confirmação de guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Caixa de diálogo de confirmação dos guias do Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Botões de alternância

Botões de alternância exigem uma lógica sutil para funcionarem corretamente. Quando uma pessoa faz uma pesquisa em um botão de alternância e a ativa, ela precisa sair do botão e retornar para reiniciar a lógica de duração. É importante que os botões de alternância tenham um estado claro ativo versus inativo. 

<br>

---

### <a name="list-views"></a>Modos de exibição de lista

:::row:::
    :::column:::
        As exibições de lista apresentam um desafio específico para a entrada de olhar e de duração da pesquisa. As pessoas podem digitalizar o conteúdo sem se sentir que precisam tiptoer os destinos de pesquisa.<br>
        <br>
**Recomendações**<br>
  * Tenha toda a linha realçada quando Head-gazed, mas não inicia a pesquisa, a menos que Head-olhar esteja no destino de duração específico.
  * Mostrar somente o destino de duração de pesquisa quando a linha for realçada para reduzir o ruído visual.
  * Fique claro e consistente com a posição dos destinos de pesquisa.
  * Não mostre todos os destinos de pesquisa de uma só vez para evitar a interface do usuário repetitiva.
  * Reutilize o mesmo padrão o mais comum possível para estabelecer a familiaridade de UX.<br>
        <br>
*Imagem: lista de guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Lista de guias do Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Veja também

* [Focar e confirmar](gaze-and-commit.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
