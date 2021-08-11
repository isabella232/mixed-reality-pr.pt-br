---
title: Interação com base no foco com o olhar
description: saiba mais sobre interações baseadas em olhar e olho no HoloLens 2 e nos novos níveis de contexto e compreensão humana se isso for acessível em experiências de holographic.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: acompanhamento de olho, realidade misturada, entrada, olho-olhar, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, design, interações
ms.openlocfilehash: aec41c6654ce10254648e90e08a09ff9adade75a3dc63af81a0953b67b95729f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220952"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>interação baseada em olhar no HoloLens 2

![Demonstração de controle de olho no MRTK](images/mrtk_et_scenemenu.jpg)

um dos nossos novos recursos empolgantes no HoloLens 2 é o acompanhamento dos olhos. em nosso [controle de olho na página HoloLens 2](eye-tracking.md) , mencionamos a necessidade de cada usuário passar por uma [calibração](/hololens/hololens-calibration), fornecemos algumas diretrizes para desenvolvedores e casos de uso destacados para acompanhamento de olho. Olho – a entrada olhar ainda é um novo tipo de entrada do usuário e há muito a aprender. 

embora a entrada olhar seja usada apenas sutilmente em nossa experiência de Shell Holographic (a interface do usuário que você vê quando você inicia o HoloLens 2), vários aplicativos, como o ["HoloLens Playground"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), demonstram ótimos exemplos de como as informações de olhar podem ser adicionadas à mágica da sua experiência com o Holographic.
Nesta página, discutiremos as considerações de design para integrar a entrada olhar para interagir com seus aplicativos Holographic.

Você aprenderá sobre as principais vantagens e também desafios exclusivos que acompanham a entrada olhar. Com base nesses, fornecemos várias recomendações de design para ajudá-lo a criar interfaces de usuário com suporte olhar. 

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
     <td>Olho-olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de rastreamento da cabeça e dos olhos

Se quiser ver os conceitos de design de rastreamento da cabeça e dos olhos em ação, confira abaixo nosso vídeo de demonstração do **Projetando hologramas - Rastreamento da cabeça e rastreamento dos olhos**. Depois de assistir ao vídeo, prossiga para saber mais sobre os tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="eye-gaze-input-design-guidelines"></a>Diretrizes de design de entrada olhar

A criação de uma interação que aproveita o direcionamento de olho rápido pode ser desafiadora. Nesta seção, resumimos as principais vantagens e desafios a serem considerados ao projetar seu aplicativo. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios da entrada olhar

- **Apontar com alta velocidade.** O olho capacidade é o capacidade mais rápido de reagir no corpo humano. 

- **Pouco esforço.** Quase nenhum movimento físico é necessário. 

- **Capacidade de ser implícito.** Geralmente descritas pelos usuários como "leitura mental", as informações sobre os movimentos de um usuário permitem que o sistema saiba qual alvo o usuário planeja participar. 

- **Canal de entrada alternativo.** O olho-olhar pode fornecer uma poderosa entrada de suporte para a mão e entrada de voz em anos de experiência de usuários com base em sua coordenação de olhos.

- **Atenção visual.** Outro benefício importante é a possibilidade de inferir o que um usuário está prestando a atenção. Isso pode ajudar em várias áreas de aplicativos que vão desde a avaliação de diferentes designs para auxiliar em interfaces de usuário mais inteligentes e indicações sociais aprimoradas para comunicação remota.

Resumindo, usar olhar como uma entrada oferece um sinal de entrada contextual rápido e sem esforço. Isso é poderoso quando combinado com outras entradas, como *voz* e entrada *manual* , para confirmar a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios de olhar de olho como uma entrada

Embora os olhos olhar possam ser usados para criar experiências de usuário satisfatórias, que fazem você sentir como um Superhero, também é importante saber o que não é bom para se considerar apropriadamente. A lista a seguir aborda alguns *desafios* a serem considerados e como solucioná-los ao trabalhar com a entrada de olhar de olho: 

- **Seu olho-olhar é "Always on"** No momento em que você abre suas tampas de olho, seus olhos começam a fixatingr sobre as coisas no ambiente. Reagir a todas as aparências que você fizer e emitir ações acidentalmente, porque você examinou algo por muito tempo, resultaria em uma experiência que não satisfaça.
É recomendável combinar olhars de olho com um *comando de voz*, um *gesto de mão*, um clique de *botão* ou uma pesquisa estendida para disparar a seleção de um destino (para obter mais informações, consulte [olhar e commit](gaze-and-commit-eyes.md)).
Essa solução também permite um modo no qual o usuário pode procurar livremente sem ser sobrecarregado por disparar involuntariamente algo. Esse problema também deve ser considerado ao criar comentários sobre Visual e auditoria ao examinar um destino.
Tente não sobrecarregar o usuário com efeitos pop-out imediatos ou sons de foco. A sutileza é fundamental. Discutiremos algumas práticas recomendadas para isso mais adiante, ao falar sobre [recomendações de design](eye-gaze-interaction.md#design-recommendations).

- **observação vs. controle** Imagine que você deseja endireitar precisamente uma fotografia em sua parede. Você olha para as bordas da fotografia e em volta dela para ver se ela fica bem alinhada. Agora imagine como você faria isso quando quiser usar seu olho-olhar como uma entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla de olho-olhar quando é necessário para entrada e controle. 

- **Sair antes de clicar em:** Para seleções de destino rápido, a pesquisa mostrou que o olhar de olho do usuário pode passar antes de concluir um clique manual (por exemplo, um toque de ar). Preste atenção especial à sincronização do sinal de olho rápido olhar com uma entrada de controle mais lenta (por exemplo, voz, mãos, controlador).

- **Destinos pequenos:** Você sabe a sensação quando tenta ler um texto que é um pouco pequeno demais para ler confortavelmente? Essa sensação de sobrecarregar seus olhos pode fazer com que você fique cansado e desgastado, pois você tenta reajustar os olhos para se concentrar melhor.
Essa é uma sensação que você pode invocar em seus usuários ao forçá-los a selecionar destinos que são muito pequenos em seu aplicativo usando o direcionamento de olho.
Para o design, visando criar uma experiência agradável e confortável para seus usuários, recomendamos que os alvos tenham um ângulo visual de, pelo menos, 2°, preferencialmente maior.

- **Olhos irregulares – movimentos olhars** Nossos olhos realizam movimentos rápidos do fixação da para o fixação da. Se você examinar os caminhos de exame dos movimentos oculares registrados, poderá ver que eles parecem irregulares. Seus olhos se movem rapidamente e em saltos ESPONTANEOS em comparação com os *olhar* ou os *movimentos de mão*.  

- **Confiabilidade de rastreamento:** A precisão do controle de olho pode diminuir um pouco a luz de alteração à medida que seus olhos se ajustam às novas condições.
Embora isso não deva afetar necessariamente o design do aplicativo, pois a precisão deve estar dentro da limitação de 2 °, pode ser necessário que o usuário calibre novamente. 


## <a name="design-recommendations"></a>Recomendações sobre design
Veja a seguir uma lista de recomendações de design específicas com base nas vantagens e nos desafios descritos para a entrada de olhar de olho:

1. **Olho-olhar não é o mesmo que Head-olhar:**
    - **Considere se movimentos de olho rápidos e irregulares se ajustam à sua tarefa de entrada:** Embora nossos movimentos de olho rápidos e irregulares sejam ótimos na seleção rápida de destinos em nosso campo de exibição, ele é menos aplicável para tarefas que exigem trajetórias de entrada suaves (por exemplo, desenho ou enfocar anotações). Nesse caso, apontar com a mão ou a cabeça deve ser preferencial.
  
    - **Evite anexar algo diretamente ao olhar de olho do usuário (por exemplo, um controle deslizante ou cursor).**
Com cursores, isso pode resultar em um efeito de "cursor fleeing" devido a pequenos deslocamentos no sinal olhar de olho projetado. Com um controle deslizante, ele pode entrar em conflito com a função dupla de controle do controle deslizante com seus olhos, enquanto também deseja verificar se o objeto está no local correto. Para o exemplo do controle deslizante, faz mais sentido usar olhar de olho em combinação com gestos de mão. Isso significa que o usuário pode alternar de forma rápida e fácil entre vários controles deslizantes, levantando sua mão e Pinçando o polegar e o dedo de índice para pegar e movê-lo. Quando o pinçamento é liberado, o controle deslizante para de mover. Os usuários poderiam ficar sobrecarregados e distraídosdos, especialmente se o sinal for impreciso para esse usuário. 
  
2. **Combine olho-olhar com outras entradas:** A integração do controle de olho com outras entradas, como gestos à mão, comandos de voz ou prensas de botão, oferece várias vantagens:
    - **Permita a observação gratuita:** Considerando que a principal função de nossos olhos é observar nosso ambiente, é importante que os usuários tenham permissão para examinar sem disparar comentários ou ações (visuais, auditivas e assim por diante). 
    Combinar o controle de olho com outro controle de entrada permite a transição tranqüila entre a observação de acompanhamento de olho e os modos de controle de entrada.
  
    - **Provedor de contexto poderoso:** Usar informações sobre onde e o que o usuário está observando ao dizer um comando de voz ou usar um gesto de mão permite canalizar diretamente a entrada entre os campos de exibição. Por exemplo: digamos _"colocar isso"_ para selecionar e posicionar um holograma de forma rápida e fluente em toda a cena observando um destino e seu destino pretendido. 

    - **Precisa de sincronização de entradas de multimodal:** Combinar movimentos de olhos rápidos com entradas mais complexas, como comandos de voz longos ou gestos de mão, tem o risco que o usuário já continua a examinar antes que o comando de entrada extra seja concluído e reconhecido. Se você criar seus próprios controles de entrada (por exemplo, gestos de mão personalizada), certifique-se de registrar o início dessa entrada ou duração aproximada para correlacioná-lo com o que um usuário examinou no passado.
    
3. **Comentários sutis para entrada de acompanhamento de olho:** É útil fornecer comentários quando um destino é examinado para indicar que o sistema está funcionando como pretendido, mas deve ser mantido sutil. Isso pode incluir a mesclagem lenta de entrada e saída, Destaques visuais ou a realização de outros comportamentos de destino sutis, como movimentos lentos, como o aumento ligeiramente do tamanho do destino. Isso indica que o sistema detectou corretamente que o usuário está olhando para um destino sem interromper desnecessariamente o fluxo de trabalho atual do usuário. 

4. **Evite impor movimentos de olho não naturais como entrada:** Não force os usuários a usar movimentos de olho específicos (gestos de olhar) para disparar ações em seu aplicativo.

5. **Conta para imprecisãos:** Distinguemos dois tipos de impedições, que são perceptíveis para os usuários: deslocamento e Tremulação. A maneira mais fácil de resolver um deslocamento é fornecer destinos suficientemente grandes para interagir com o. É recomendável que você use um ângulo visual maior que 2 ° como referência. Por exemplo, sua miniatura é de cerca de 2 ° no ângulo visual quando você amplia seu braço. Isso resulta nas seguintes diretrizes:
    - Não force os usuários a selecionar pequenos destinos. A pesquisa mostrou que se os destinos são suficientemente grandes e o sistema é projetado bem, os usuários descrevem suas interações como sem esforço e mágico. Se os alvos ficarem muito pequenos, os usuários descreverão a experiência como cansativa e frustrante.
  
<br>

Esta página forneceu uma boa visão geral para ajudá-lo a começar a entender os olhos olhar como uma entrada na realidade misturada. Para começar a desenvolver, confira nossas informações sobre [olhar no Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) e [olhar de olho no DirectX](../develop/native/gaze-in-directx.md).


## <a name="see-also"></a>Veja também
* [Conforto](comfort.md)
* [Olhar com o olhar no DirectX](../develop/native/gaze-in-directx.md)
* [Olhar com o olhar no Unity (realidade misturada Toolkit)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Entrada de voz](../out-of-scope/voice-design.md)