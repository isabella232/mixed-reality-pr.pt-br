---
title: Interação com base no foco com o olhar
description: Saiba mais sobre interações com o olhar e o olhar no HoloLens 2 e os novos níveis de contexto e compreensão humana se o for o caso em experiências holográficas.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Acompanhamento ocular, Realidade Misturada, Entrada, olhar com o olhar, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, design, interações
ms.openlocfilehash: 3067f5533dbe70d4decb6b5cf94a3f1c5029115a
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906862"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interação com base no olhar no HoloLens 2

![Demonstração de acompanhamento ocular no MRTK](images/mrtk_et_scenemenu.jpg)

Um dos nossos novos recursos interessantes no HoloLens 2 é o acompanhamento ocular. Em nossa página Acompanhamento ocular no [HoloLens 2,](eye-tracking.md) mencionamos [a](/hololens/hololens-calibration)necessidade de cada usuário passar por uma Calibragem, forneceu algumas diretrizes para desenvolvedores e realçamos casos de uso para acompanhamento ocular. A entrada com o olhar ainda é um novo tipo de entrada do usuário e há muito a aprender. 

Embora a entrada com o olhar seja usada apenas de forma sublinhada em nossa experiência do Shell Holographic (a interface do usuário que você vê ao iniciar o HoloLens 2), vários aplicativos, como o ["HoloLens Playground",](https://www.microsoft.com/p/mr-playground/9nb31lh723s2)mostram ótimos exemplos de como a entrada com o olhar pode adicionar à mágica da sua experiência holográfica.
Nesta página, discutiremos as considerações de design para integrar a entrada com o olhar para interagir com seus aplicativos holográficos.

Você aprenderá sobre as principais vantagens e também os desafios exclusivos que vêm com a entrada com o olhar. Com base neles, fornecemos várias recomendações de design para ajudá-lo a criar interfaces de usuário com suporte para o olhar. 

## <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Recurso</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Olhar com o olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração de conceitos de design de acompanhamento ocular e de cabeça

Se você quiser ver os conceitos de design de acompanhamento de cabeça e de olho em ação, confira nossa demonstração de vídeo **Designing Holograms – Head Tracking and Eye Tracking** abaixo. Quando terminar, continue para obter uma análise mais detalhada de tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi tirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui.](https://aka.ms/dhapp)*

## <a name="eye-gaze-input-design-guidelines"></a>Diretrizes de design de entrada com o olhar

Criar uma interação que aproveita o direcionamento de olho em movimento rápido pode ser um desafio. Nesta seção, resumimos as principais vantagens e desafios a considerar ao projetar seu aplicativo. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios da entrada com o olhar

- **Apontar com alta velocidade.** O cérebro ocular é o cérebro que reage mais rapidamente no corpo humano. 

- **Pouco esforço.** Quase nenhum movimento físico é necessário. 

- **Capacidade de ser implícito.** Geralmente descritas pelos usuários como "leitura da mente", as informações sobre os movimentos de olho de um usuário permitem que o sistema saiba qual destino o usuário planeja envolver. 

- **Canal de entrada alternativo.** O olhar pode fornecer uma entrada de suporte eficiente para a criação de entrada de mão e voz com base em anos de experiência dos usuários com base na coordenação do olhar.

- **Atenção visual.** Outro benefício importante é a possibilidade de inferir o que um usuário está prestendo atenção. Isso pode ajudar em várias áreas de aplicativos, desde avaliar com mais eficiência designs diferentes até auxiliar em interfaces de usuário mais inteligentes e avaliação social aprimorada para comunicação remota.

Em resumo, o uso do olhar como uma entrada oferece um sinal de entrada contextual rápido e sem esforço. Isso é poderoso quando combinado com  outras entradas, como voz e *entrada manual,* para confirmar a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios do olhar como entrada

Embora o olhar possa ser usado para criar experiências de usuário satisfatórias, o que faz com que você se sinta um homem mal-parecido, também é importante saber no que ele não é bom para levar em conta adequadamente isso. A lista a seguir aborda alguns *desafios a* considerar e como resolver esses problemas ao trabalhar com a entrada com o olhar: 

- **O olhar com o olhar está "sempre em cima"** No momento em que você abre as tampas dos olhos, seus olhos começam a se fixar em coisas no ambiente. Reagir a cada olhar que você faz e em emissão acidental de ações, porque você analisou algo por muito tempo, resultaria em uma experiência insatisfing.
É recomendável combinar o olhar com um  comando de voz *,* gesto de mão *,* clique no botão ou extensão estendida para disparar a seleção de um destino (para obter mais informações, consulte com o olhar e confirmação [).](gaze-and-commit-eyes.md)
Essa solução também permite um modo no qual o usuário pode dar uma olhada gratuitamente sem ser sobrecarregado disparando algo de forma insuntente. Esse problema também deve ser considerado ao criar comentários visuais e auditivos ao olhar para um destino.
Tente não sobrecarregar o usuário com efeitos pop-out imediatos ou sons de foco. A sutileza é a chave. Discutiremos algumas práticas recomendadas para isso mais adiante ao falar sobre [recomendações de design.](eye-gaze-interaction.md#design-recommendations)

- **Observação versus controle** Imagine que você deseja organizar precisamente uma fotografia em sua parede. Você olha para as bordas da fotografia e em volta dela para ver se ela fica bem alinhada. Agora imagine como você faria isso quando quisesse usar o olhar como uma entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla do olhar quando ele é necessário para entrada e controle. 

- **Deixe antes de clicar:** Para seleções rápidas de destino, a pesquisa mostrou que o olhar do usuário pode se mover antes de concluir um clique manual (por exemplo, um toque de ar). Preste atenção especial para sincronizar o sinal de olhar rápido com entrada de controle mais lenta (por exemplo, voz, mãos, controlador).

- **Destinos pequenos:** Você sabe qual é a sensação de tentar ler textos que são um pouco pequenos demais para ler de maneira confortável? Essa sensação de pressão nos olhos pode fazer com que você se sinta esgotado e esgotado, pois você tenta reajustar os olhos para se concentrar melhor.
Esse é um sentimento que você pode invocar em seus usuários ao forçá-los a selecionar destinos muito pequenos em seu aplicativo usando o direcionamento ocular.
Para o design, visando criar uma experiência agradável e confortável para seus usuários, recomendamos que os alvos tenham um ângulo visual de, pelo menos, 2°, preferencialmente maior.

- **Movimentos irregulares de olhar para o olhar** Nossos olhos executam movimentos rápidos da fixação à fixação. Se você examinar os caminhos de exame dos movimentos oculares registrados, poderá ver que eles parecem irregulares. Seus olhos se movem rapidamente e em saltos de remoção em comparação com o foco *com a cabeça* ou os movimentos da *mão.*  

- **Acompanhar a confiabilidade:** A precisão do acompanhamento ocular pode prejudicar um pouco a alteração da luz à medida que seus olhos se ajustam às novas condições.
Embora isso não deva afetar necessariamente o design do aplicativo, pois a precisão deve estar dentro da limitação de 2°, pode ser necessário que o usuário calibrar novamente. 


## <a name="design-recommendations"></a>Recomendações sobre design
Veja a seguir uma lista de recomendações de design específicas com base nas vantagens e desafios descritos para a entrada com o olhar:

1. **O olhar não é o mesmo que o olhar para a cabeça:**
    - **Considere se os movimentos rápidos, porém irregulares, se ajustam à sua tarefa de entrada:** Embora nossos movimentos de olho rápidos e irregulares sejam ótimos na seleção rápida de destinos em nosso campo de exibição, ele é menos aplicável para tarefas que exigem anotações suaves de entrada (por exemplo, desenhar ou cercar anotações). Nesse caso, apontar com a mão ou a cabeça deve ser preferencial.
  
    - **Evite anexar algo diretamente ao olhar do usuário (por exemplo, um controle deslizante ou cursor).**
Com cursores, isso pode resultar em um efeito de "cursor de desacordo" devido a pequenos deslocamentos no sinal de olhar projetado. Com um controle deslizante, ele pode entrar em conflito com a função dupla de controlar o controle deslizante com os olhos enquanto também deseja verificar se o objeto está no local correto. Para o exemplo do controle deslizante, faz mais sentido usar o olhar em combinação com gestos de mão. Isso significa que o usuário pode alternar rapidamente e sem esforço entre muitos controles deslizantes, aumentando a mão e pinçando o polegar e o dedo indicador para agarrá-lo e movê-lo. Quando a pinçar é liberada, o controle deslizante para de se mover. Os usuários podem ficar sobrecarregados e confusos, especialmente se o sinal for impreciso para esse usuário. 
  
2. **Combine o olhar com outras entradas:** A integração do acompanhamento ocular com outras entradas, como gestos de mão, comandos de voz ou pressionadores de botão, oferece várias vantagens:
    - **Permitir observação gratuita:** Considerando que a principal função dos nossos olhos é observar nosso ambiente, é importante que os usuários têm permissão para olhar ao redor sem disparar comentários ou ações (visuais, auditivas e assim por diante). 
    Combinar o acompanhamento ocular com outro controle de entrada permite a transição suave entre a observação de acompanhamento ocular e os modos de controle de entrada.
  
    - **Provedor de contexto poderoso:** Usar informações sobre onde e o que o usuário está vendo ao dizer um comando de voz ou usar um gesto de mão permite canalizar perfeitamente a entrada pelo campo de exibição. Por exemplo: diga _"coloque isso lá"_ para selecionar e posicionar de forma rápida e fluente um holograma em toda a cena observando um destino e seu destino pretendido. 

    - **Necessidade de sincronizar entradas multimodal:** Combinar movimentos de olho rápidos com entradas mais complexas, como comandos de voz longos ou gestos de mão, corre o risco de que o usuário já continue a olhar ao redor antes que o comando de entrada extra seja concluído e reconhecido. Se você criar seus próprios controles de entrada (por exemplo, gestos de mão personalizados), certifique-se de registrar o início dessa entrada ou duração aproximada para correlacioná-lo com o que um usuário viu no passado.
    
3. **Comentários sutis para entrada de acompanhamento ocular:** É útil fornecer comentários quando um destino é procurado para indicar que o sistema está funcionando conforme o esperado, mas deve ser mantido sutil. Isso pode incluir mesclagem lenta, realçamentos visuais ou outros comportamentos de destino sutis, como movimentos lentos, como aumentar um pouco o tamanho de destino. Isso indica que o sistema detectou corretamente que o usuário está observando um destino sem interromper desnecessariamente o fluxo de trabalho atual do usuário. 

4. **Evite impor movimentos de olho anormal como entrada:** Não force os usuários a usar movimentos otivos específicos (gestos de olhar) para disparar ações em seu aplicativo.

5. **Conta para imprecisões:** Distinguemos dois tipos de imprecisas, que são perceptíveis para os usuários: deslocamento e tremida. A maneira mais fácil de resolver um deslocamento é fornecer destinos suficientemente grandes para interagir. É sugerido que você use um ângulo visual maior que 2° como referência. Por exemplo, sua miniatura tem cerca de 2° no ângulo visual quando você estende o braço. Isso resulta nas seguintes diretrizes:
    - Não force os usuários a selecionar destinos pequenos. A pesquisa mostrou que, se os destinos são suficientemente grandes e o sistema é bem projetado, os usuários descrevem suas interações como sem esforço e mágica. Se os alvos ficarem muito pequenos, os usuários descreverão a experiência como cansativa e frustrante.
  
<br>

Esta página forneceu uma boa visão geral para começar a entender o olhar como uma entrada na realidade misturada. Para começar a desenvolver, confira nossas informações sobre o olhar no [Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) e o olhar [no DirectX.](../develop/native/gaze-in-directx.md)


## <a name="see-also"></a>Veja também
* [Conforto](comfort.md)
* [Olho-olhar no DirectX](../develop/native/gaze-in-directx.md)
* [Olho-olhar no Unity (Kit de ferramentas de realidade misturada)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Entrada de voz](../out-of-scope/voice-design.md)