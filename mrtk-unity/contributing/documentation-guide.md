---
title: Diretrizes da documentação
description: Diretrizes e padrões de documentação para o MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 95af19b71a9fe06dabad058e75f78d951262ba4a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175354"
---
# <a name="documentation-guidelines"></a>Diretrizes da documentação

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

este documento descreve as diretrizes e os padrões de documentação para a realidade misturada Toolkit (MRTK). Isso fornece uma introdução aos aspectos técnicos de escrita e geração de documentação, para destacar armadilhas comuns e para descrever o estilo de escrita recomendado.

A página em si deve servir como exemplo, portanto, ela usa o estilo pretendido e os recursos de marcação mais comuns da documentação.

- [Origem](#source-documentation)
- [Instruções](#how-to-documentation)
- [Projetar](#design-documentation)
- [Notas de desempenho](#performance-notes)
- [Alterações da falha](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funcionalidade e marcação

Esta seção descreve os recursos frequentemente necessários. Para ver como eles funcionam, examine o código-fonte da página.

1. Listas numeradas
   1. Listas numeradas aninhadas com pelo menos 3 espaços em branco à esquerda
   1. O número real no código é irrelevante; a análise cuidará da definição do número de item correto.

- Listas de pontos de marcador
  - Listas de pontos de marcador aninhados
- Texto em **negrito** com \* \* asterisco duplo\*\*
-  *texto* em itálico com \_ sublinhado \_ ou \* asterisco único\*
- Texto `highlighted as code` dentro de uma frase \` usando aspas revertidas\`
- Links para páginas de docs [MRTK diretrizes de documentação](documentation-guide.md)
- Links para [âncoras em uma página](#style); as âncoras são formadas com a substituição de espaços por traços e a conversão em minúsculas

Para exemplos de código, usamos os blocos com três marcas de escala \` \` \` e especificamos *Csharp* como o idioma para realce de sintaxe:

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Ao mencionar o código dentro de uma frase `use a single backtick` .

### <a name="todos"></a>TODOs

Evite usar todos no docs, assim como esses TODO (como TODO o código) tendem a se acumular e informações sobre como eles devem ser atualizados e por que são perdidos.

Se for absolutamente necessário adicionar um TODO, siga estas etapas:

1. Execute um novo problema no GitHub que descreve o contexto por trás do TODO e forneça um plano de fundo suficiente que outro colaborador possa entender e, em seguida, abordar o TODO.
2. Referencie a URL do problema no todo no docs.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Seções realçadas

Para realçar pontos específicos para o leitor, use *> [!NOTE]* , *> [!WARNING]* e *> [!IMPORTANT]* para produzir os seguintes estilos. É recomendável usar observações para pontos gerais e pontos de aviso/importantes somente para casos especiais relevantes.

> [!NOTE]
> Exemplo de uma observação

> [!WARNING]
> Exemplo de um aviso

> [!IMPORTANT]
> Exemplo de um comentário importante

## <a name="page-layout"></a>Layout de página

### <a name="introduction"></a>Introdução

A parte logo após o título do capítulo principal deve servir como uma breve introdução sobre o que é o capítulo. Não torne isso muito longo, em vez disso, adicione subtítulos. Elas permitem vincular a seções e podem ser salvas como indicadores.

### <a name="main-body"></a>Corpo principal

Use manchetes de dois níveis e de três níveis para estruturar o restante.

**Mini seções**

Use uma linha em negrito de texto para blocos que devem ser destacados. Podemos substituir isso por manchetes de quatro níveis em algum momento.

### <a name="see-also-section"></a>Seção ' Veja também '

A maioria das páginas deve terminar com um capítulo chamado *Ver também*. Este capítulo é simplesmente uma lista com marcadores de links para páginas relacionadas a este tópico. Esses links também podem aparecer dentro do texto da página quando apropriado, mas isso não é necessário. Da mesma forma, o texto da página pode conter links para páginas que não estão relacionadas ao tópico principal, eles não devem ser incluídos na lista *Consulte também* . Consulte o [capítulo ' ' Veja também ' ' da página](#see-also) como um exemplo para a escolha de links.

## <a name="table-of-contents-toc"></a>Sumário (TOC)

Os arquivos de Sumário são usados para gerar as barras de navegação na documentação do MRTK github.io.
Sempre que um novo arquivo de documentação for adicionado, verifique se há uma entrada para esse arquivo em um dos arquivos TOC. yml da pasta de documentação. Somente os artigos listados nos arquivos de Sumário serão exibidos na navegação dos documentos do desenvolvedor. Pode haver um arquivo de Sumário para cada subpasta na pasta de documentação que pode ser vinculada a qualquer arquivo de Sumário existente para adicioná-lo como uma subseção à parte correspondente da navegação.

## <a name="style"></a>Estilo

### <a name="writing-style"></a>Estilo de escrita

Regra geral: Tente **soar profissional**. Isso geralmente significa evitar um ' Tom de conversação '. Além disso, tente evitar o hiperbólico e o sensationalism.

1. Não tente ser (excessivamente) engraçado.
2. Nunca gravar ' I '
3. Evite ' nós '. Normalmente, isso pode ser reformulado facilmente, usando ' MRTK ' em vez disso. Exemplo: "damos suporte a esse recurso"-> "o MRTK" dá suporte a esse recurso "ou" há suporte para os recursos a seguir... ".
4. Da mesma forma, tente evitar ' você '. Exemplo: "com essa alteração simples seu sombreador se torna configurável!" -> "os sombreadores podem se tornar configuráveis com pouco esforço".
5. Não use ' impreciso frases '.
6. Evite parecer muito empolgado, não precisamos vender nada.
7. Da mesma forma, evite ser muito expressivos. Os pontos de exclamação raramente são necessários.

### <a name="capitalization"></a>Uso de maiúsculas

- Use o **caso de sentença para manchetes**. Ie. colocar a primeira letra e os nomes em maiúsculas, mas nada mais.
- Use o inglês regular para todo o resto. Isso significa que não **coloque palavras arbitrárias em maiúsculas**, mesmo que elas contenham um significado especial nesse contexto. Prefira *texto em itálico* para realçar determinadas palavras, [Veja abaixo](#emphasis-and-highlighting).
- Quando um link é inserido em uma sentença (que é o método preferencial), o nome do capítulo padrão sempre usa letras maiúsculas, dividindo, assim, a regra sem maiúsculas e minúsculas arbitrárias dentro do texto. Portanto, use um nome de link personalizado para corrigir a capitalização. Por exemplo, aqui está um link para a documentação de [controle de limites](../features/ux-building-blocks/bounds-control.md) .
- Fazer maiúsculas nomes, como o *Unity*.
- Não colocar "Editor" em maiúscula ao escrever o *Editor Unity*.

### <a name="emphasis-and-highlighting"></a>Ênfase e realce

Há duas maneiras de enfatizar ou realçar palavras, torná-las em negrito ou torná-las em itálico. O efeito do texto em negrito é que o **texto em negrito** fica inativo e, portanto, pode ser facilmente notado enquanto espiada uma parte do texto ou até mesmo apenas rolando uma página. O negrito é ótimo para realçar frases que as pessoas devem lembrar. No entanto, **use o texto em negrito raramente**, pois ele geralmente é confuso.

Muitas vezes, você deseja "agrupar" algo que pertença logicamente ao mesmo tempo ou realce um termo específico, pois ele tem um significado especial. Essas coisas não precisam destacar o texto geral. Use texto em itálico como um *método leve* para realçar algo.

Da mesma forma, quando um nome de arquivo, um caminho ou uma entrada de menu é mencionado em texto, prefira deixá-lo em itálico para agrupá-lo logicamente, sem atrapalhar.

Em geral, tente **evitar o realce de texto desnecessário**. Os termos especiais podem ser realçados uma vez para facilitar o reconhecimento do leitor, não repita o realce em todo o texto, quando ele não tem mais nenhuma finalidade e apenas uma distração.

### <a name="mentioning-menu-entries"></a>Mencionando entradas de menu

ao mencionar uma entrada de menu que um usuário deve clicar, a convenção atual é: *Project > arquivos > criar > folha*

### <a name="links"></a>Links

Insira o máximo possível de links úteis para outras páginas, mas cada link apenas uma vez. Suponha que um leitor clique em cada link na página e pense no quão entediante seria se a mesma página fosse aberta 20 vezes.

Prefira links inseridos em uma frase:

- BAD: as diretrizes são úteis. Confira [este capítulo para](../contributing/documentation-guide.md) obter detalhes.
- BOM: [as diretrizes](documentation-guide.md) são úteis.

Evite links externos, eles podem ficar desatualizados ou conter conteúdo protegido por direitos autorais.

Ao adicionar um link, considere se ele também deve ser listado na [seção](#see-also) Ver também. Da mesma forma, verifique se um link para a nova página deve ser adicionado à página vinculada.

### <a name="images--screenshots"></a>Imagens/capturas de tela

**Use capturas de tela com moderação.** Manter imagens na documentação é muito trabalho, pequenas alterações na interface do usuário podem tornar muitas capturas de tela desatualizadas. As regras a seguir reduzirão o esforço de manutenção:

1. Não use capturas de tela para coisas que podem ser descritas no texto. Especialmente, **nunca captura de tela de uma grade de** propriedades com a única finalidade de mostrar valores e nomes de propriedade.
2. Não inclua coisas em uma captura de tela irrelevantes para o que é mostrado. Por exemplo, quando um efeito de renderização é mostrado, faça uma captura de tela do viewport, mas exclua qualquer interface do usuário ao redor dele. Mostrando alguma interface do usuário, tente mover janelas de forma que apenas essa parte importante está na imagem.
3. Ao incluir a interface do usuário de captura de tela, mostre apenas as partes importantes. Por exemplo, ao falar sobre botões em uma barra de ferramentas, faça uma imagem pequena que mostre os botões importantes da barra de ferramentas, mas exclua tudo ao redor dela.
4. Use apenas imagens fáceis de reproduzir. Isso significa que não pintar marcadores ou realça em capturas de tela. Primeiro, não há regras consistentes sobre como elas devem ser, de qualquer forma. Em segundo lugar, reproduzir essa captura de tela é um esforço adicional. Em vez disso, descreva as partes importantes no texto. Há exceções a essa regra, mas elas são raras.
5. Obviamente, é muito mais esforço recriar um GIF animado. Espere ser responsável por recriá-lo até o fim do tempo ou esperar que as pessoas o lancem, se não quiserem gastar esse tempo.
6. Mantenha o número de imagens em um artigo baixo. Geralmente, um bom método é fazer uma captura de tela geral de alguma ferramenta, que mostra tudo e, em seguida, descrever o restante em texto. Isso facilita a substituição da captura de tela quando necessário.

Alguns outros aspectos:

- A interface do usuário do editor para capturas de tela deve usar o editor de tema cinza claro, pois nem todos os usuários têm acesso ao tema escuro e queremos manter as coisas o mais consistente possível.
- A largura padrão da imagem é de 500 pixels, pois isso é exibido bem na maioria dos monitores. Tente não desviar muito dele. A largura de 800 pixels deve ser a máxima.
- Use PNGs para capturas de tela da interface do usuário.
- Use PNGs ou JPGs para capturas de tela do viewport 3D. Prefira a qualidade em vez da taxa de compactação.

### <a name="list-of-component-properties"></a>Lista de propriedades do componente

Ao documentar uma lista de propriedades, use texto em negrito para realça o nome da propriedade e, em seguida, quebras de linha e texto regular para descrevê-las. Não use sub capítulos ou listas de pontos de marcador.

Além disso, não se esqueça de concluir todas as frases com um ponto final.

## <a name="page-completion-checklist"></a>Lista de verificação de conclusão da página

1. Verifique se as diretrizes deste documento foram seguidas.
1. Procure a estrutura do documento e veja se o novo documento pode ser mencionado na [seção Ver também](#see-also) de outras páginas.
1. Se disponível, tenha alguém com conhecimento do tópico que leia a página para ver se há correção técnica.
1. Fazer com que alguém leia a página com prova para estilo e formatação. Isso pode ser alguém que não está familiarizado com o tópico, o que também é uma boa ideia para obter comentários sobre como a documentação é compreensível.

## <a name="source-documentation"></a>Documentação de origem

A documentação da API será gerada automaticamente dos arquivos de origem do MRTK. Para facilitar isso, os arquivos de origem são necessários para conter o seguinte:

- [Blocos de resumo de classe, struct, enum](#class-struct-enum-summary-blocks)
- [Blocos de propriedade, método, resumo de eventos](#property-method-event-summary-blocks)
- [Versão e dependências de introdução de recursos](#feature-introduction-version-and-dependencies)
- [Campos serializados](#serialized-fields)
- [Valores de enumeração](#enumeration-values)

Além do acima, o código deve ser bem comentado para permitir manutenção, correções de bugs e facilidade de personalização.

### <a name="class-struct-enum-summary-blocks"></a>Blocos de resumo de classe, struct, enum

Se uma classe, struct ou enum estiver sendo adicionado ao MRTK, sua finalidade deverá ser descrita. Isso é para assumir a forma de um bloco de resumo acima da classe .

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Se houver dependências de nível de classe, elas deverão ser documentadas em um bloco de comentários, imediatamente abaixo do resumo.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Solicitações de pull enviadas sem resumos para classes, estruturas ou enums não serão aprovadas.

### <a name="property-method-event-summary-blocks"></a>Blocos de propriedade, método, resumo de eventos

Propriedades, métodos e eventos (PMEs), bem como campos, devem ser documentados com blocos de resumo, independentemente da visibilidade do código (pública, privada, protegida e interna). A ferramenta de geração de documentação é responsável por filtrar e publicar apenas os recursos públicos e protegidos.

OBSERVAÇÃO: um bloco de resumo **não é** necessário para métodos do Unity (por exemplo: Ativas, Iniciar, Atualizar).

A documentação do PME **é necessária** para que uma solicitação de pull seja aprovada.

Como parte de um bloco de resumo do PME, o significado e a finalidade dos parâmetros e dos dados retornados são necessários.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Versão e dependências de introdução de recursos

Como parte da documentação de resumo da API, as informações sobre a versão do MRTK na qual o recurso foi introduzido e quaisquer dependências devem ser documentadas em um bloco de comentários.

As dependências devem incluir dependências de extensão e/ou plataforma.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Campos serializados

É uma boa prática usar o atributo de dica de ferramenta do Unity para fornecer documentação de runtime para os campos de um script no inspetor.

Para que as opções de configuração sejam incluídas  na documentação da API, os scripts são necessários para incluir pelo menos o conteúdo da dica de ferramenta em um bloco de resumo.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valores de enumeração

Ao definir e enumerar, o código também deve documentar o significado dos valores de enumeração usando um bloco de resumo. Opcionalmente, os blocos de comentários podem ser usados para fornecer detalhes adicionais para aprimorar a compreensão.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentação de como fazer

Muitos usuários do Toolkit realidade misturada podem não precisar usar a documentação da API. Esses usuários aproveitarão nossos pré-requisitos e scripts pré-feitos e reutilizáveis para criar suas experiências.

Cada área de recurso conterá um ou mais arquivos markdown (.md) que descrevem em um nível bastante alto, o que é fornecido. Dependendo do tamanho e/ou da complexidade de uma determinada área de recurso, pode haver necessidade de arquivos adicionais, até um por recurso fornecido.

Quando um recurso é adicionado (ou o uso é alterado), a documentação de visão geral deve ser fornecida.

Como parte desta documentação, as seções de ida e volta, incluindo ilustrações, devem ser fornecidas para ajudar os clientes novos a um recurso ou conceito de começar.

## <a name="design-documentation"></a>Documentação de design

A Realidade Misturada oferece uma oportunidade de criar mundos totalmente novos. Parte disso provavelmente envolverá a criação de ativos personalizados para uso com o MRTK. Para tornar isso o mais claro possível para os clientes, os componentes devem fornecer documentação de design que descreve qualquer formatação ou outros requisitos para ativos de arte.

Alguns exemplos em que a documentação de design pode ser útil:

- Modelos de cursor
- Visualizações de mapeamento espacial
- Arquivos de efeito de som

Esse tipo de documentação **é altamente** recomendável e **pode** ser solicitado como parte de uma revisão de solicitação de pull.

Isso pode ou não ser diferente da recomendação de design no [site do Desenvolvedor do MS](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Notas de desempenho

Alguns recursos importantes vêm com um custo de desempenho. Geralmente, esse código dependerá muito de como eles são configurados.

Por exemplo:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

As notas de desempenho são recomendadas para  componentes de CPU e/ou GPU pesada e podem ser solicitadas como parte de uma revisão de solicitação de pull. Todas as notas de desempenho aplicáveis devem ser incluídas na API e **na documentação de visão** geral.

## <a name="breaking-changes"></a>Alterações de quebra

A documentação de alterações significativas é composta por um arquivo de nível [superior](../contributing/breaking-changes.md) que se vincula ao arquivo individual de cada área de breaking-changes.md.

A área de breaking-changes.md arquivos deve conter a lista de todas  as alterações de quebra conhecidas para uma determinada versão, bem como o histórico de alterações significativas de versões anteriores.

Por exemplo:

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

As informações contidas no nível do recurso breaking-changes.md arquivos serão agregadas às notas de versão de cada nova versão do MRTK.

Todas as alterações significativas que fazem parte de uma alteração **devem** ser documentadas como parte de uma solicitação de pull.

## <a name="tools-for-editing-markdown"></a>Ferramentas para editar MarkDown

[Visual Studio Code](https://code.visualstudio.com/) é uma ótima ferramenta para editar arquivos markdown que fazem parte da documentação do MRTK.

Ao escrever a documentação, instalar as duas extensões a seguir também é altamente recomendável:

- Extensão Markdown do Docs para Visual Studio Code – use Alt+M para abrir um menu de opções de autor de documentos.

- Verificador Ortônico de Código – palavras com ortagem inoclinada serão sublinhadas; Clique com o botão direito do mouse em uma palavra com o botão direito do mouse para alterá-la ou salvá-la no dicionário.

Ambos são empacotados no Pacote de Autorização do Docs publicado pela Microsoft.

## <a name="see-also"></a>Confira também

- [Exemplo de link "consulte também" para documentação](https://www.microsoft.com)
