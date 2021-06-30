---
title: Alterações de quebra
description: Política relativa a alterações significativas no MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 713cb5a0965d713c7073004059218ab2ab37201d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121544"
---
# <a name="breaking-changes"></a>Alterações de quebra

Os consumidores do MRTK dependem de ter uma superfície de API de liberação para liberação estável, para que eles possam realizar atualizações no MRTK sem ter grandes alterações significativas a cada vez.

Esta página descreve nossa política atual sobre alterações significativas no MRTK, juntamente com algumas metas mais longas em torno de como podemos gerenciar melhor a compensação entre manter as alterações significativas baixas e ser capaz de fazer as alterações técnicas de longo prazo certas no código.

## <a name="what-is-a-breaking-change"></a>O que é uma alteração significativa?

Uma alteração é uma alteração significativa se atender a qualquer uma das condições da [lista](#list-a) a e atender a todas as condições na [lista B](#list-b)

### <a name="list-a"></a>Listar um

- A adição, remoção ou atualização de qualquer membro ou função de qualquer interface (ou remoção/renomeação da interface inteira).
- A remoção, a atualização (alterando o tipo/definição, tornando privado ou interno) de qualquer membro ou função de classe protegida ou pública. (ou remoção/renomeação da classe inteira).
- A alteração na ordem dos eventos acionados por uma classe.
- A renomeação de qualquer serializador particular (sem uma marca FormerlySerializedAs correspondente) ou propriedade pública em um ScriptableObject (especialmente alterações nos perfis).
- Alterar o tipo de um campo em um ScriptableObject (especialmente alterações nos perfis).
- Atualiza para o namespace ou asmdefs de qualquer classe ou interface.
- Remoção de qualquer pré-fabricado ou remoção de um script no objeto de nível superior de um pré-fabricado.

### <a name="list-b"></a>Lista B

- O ativo em questão está no pacote base (ou seja, está em uma das seguintes pastas):

  - MRTK/núcleo
  - MRTK/provedores/
  - MRTK/serviços/
  - MRTK/SDK/
  - MRTK/extensões

- O ativo em questão não pertence ao namespace experimental.

> [!IMPORTANT]
> Qualquer ativo que esteja no pacote de exemplos (ou seja, parte do MRTK/exemplos/pasta) está sujeito a alterações a qualquer momento, pois os ativos foram projetados para serem copiados e exibidos por consumidores como "implementações de referência", mas não fazem parte do conjunto principal de APIs e ativos. Os ativos no namespace experimental (ou mais geralmente, os recursos rotulados como experimentais) são aqueles que são publicados antes que toda a auditoria devida tenha sido feita (ou seja, testes, iteração de UX, documentação) e seja publicada antecipadamente para obter comentários mais cedo.  No entanto, como eles não têm testes e documentação, e como é provável que não tenhamos assumido todas as interações e designs, publicamos-os em um estado em que o público deve assumir que eles podem e mudar (ou seja, ser modificado, completamente removido, etc.).
>
> Consulte [recursos experimentais](../contributing/experimental-features.md) para obter mais informações.

Como a área da superfície para alterações significativas é muito grande, é importante observar que ter uma regra absoluta que diz "sem alterações significativas" seria impossível. pode haver problemas que só podem ser corrigidos de uma forma confortável por meio de uma alteração significativa. Para colocar de outra maneira, a única maneira de realmente ter "nenhuma alteração significativa" é não ter nenhuma alteração.

Nossa política mais importante é evitar fazer alterações significativas, se possível, e fazer isso apenas se a alteração acumular um valor significativo de longo prazo do cliente ou da estrutura.

## <a name="what-to-do-about-breaking-changes"></a>O que fazer sobre alterações significativas

Se for possível realizar algo sem uma alteração significativa e sem comprometer a estrutura de longo prazo e a viabilidade do recurso, não faça a alteração significativa. Se não houver outra maneira, a política atual será avaliar cada alteração significativa individual, para entender se o benefício de fazer a alteração supera o custo para o consumidor de absorver a alteração. Debate sobre o que vale a pena fazer e o que geralmente não ocorrerá na sua própria discussão ou problema.

O que pode acontecer aqui se enquadra em vários buckets:

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>A alteração significativa adiciona valor, mas pode ser escrito de uma forma que não está se dividindo

Por exemplo, [essa pr](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) adicionou um novo recurso que foi inicialmente escrito de uma maneira que estava dividindo uma interface existente, mas foi então reescrita onde o recurso foi dividido como sua própria interface. Geralmente, esse é o melhor resultado possível. Não tente forçar uma alteração em um formato não separável se isso for comprometer a viabilidade de longo prazo ou a estrutura do recurso.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>A alteração significativa agrega valor suficiente ao cliente que vale a pena fazer

Documente as alterações significativas e forneça a melhor mitigação possível (ou seja, etapas prescritivas sobre como migrar ou melhor ainda as ferramentas que serão migradas automaticamente para o cliente). Cada versão pode conter uma pequena quantidade de alterações que estão sendo interrompidas-elas devem ser sempre documentadas em documentos como foram feitas nesta [PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858). Se já houver um guia de migração 2. x. x → 2. x +1. x + 1, adicione instruções ou ferramentas a esse documento. Se ele não existir, crie-o.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>A alteração significativa agrega valor, mas o problema do cliente seria muito alto

Nem todos os tipos de alterações significativas são criados de forma igual-alguns são significativamente mais problemáticos que outros, com base em nossa experiência e com base nas experiências do cliente. Por exemplo, as alterações em interfaces podem ser problemáticas, mas se a alteração significativa for aquela em que um cliente provavelmente não terá ampliado/implementado no passado (o sistema de visualização de diagnóstico, por exemplo), o custo real provavelmente será baixo para nada. No entanto, se a alteração for o tipo de um campo em um ScriptableObject (por exemplo, em um dos perfis principais do MRTK), isso provavelmente causará um grande problema do cliente. Os clientes já clonaram o perfil padrão, a mesclagem/atualização de perfis pode ser extremamente difícil de fazer manualmente (ou seja, por meio de um editor de texto durante o tempo de mesclagem), e copiar novamente o perfil padrão e reconfigurar tudo manualmente é extremamente provável de levar a uma regressão difícil de depurar.

Essas alterações precisam ser colocadas na prateleira até que exista uma ramificação que permita alterações significativas (juntamente com um valor significativo que dará aos clientes um motivo para a atualização). Essa ramificação não existe no momento. Em nossas reuniões futuras de planejamento de iteração, examinaremos o conjunto de alterações/problemas que estavam "muito rompendo" para ver se atingimos uma massa crítica para fazer com que seja razoável buscar um conjunto de alterações de uma só vez. Observe que é perigoso criar uma ramificação "tudo é permitido" sem que a auditoria detalhada seja feita por causa dos recursos de engenharia limitados que temos e do fato de que teríamos de dividir os testes e a validação entre esses dois. Precisa haver uma clara finalidade e uma data de início e de término bem comunicada de tal ramificação quando ela existe.

## <a name="long-term-management-of-breaking-changes"></a>Gerenciamento de longo prazo de alterações significativas

A longo prazo, devemos procurar reduzir o escopo do que é uma alteração significativa, aumentando o conjunto de condições na [lista B](#list-b). O encaminhamento do conjunto de coisas na [lista a](#list-a) sempre estará tecnicamente procurando pelo conjunto de arquivos e ativos que consideramos na "superfície da API pública". A maneira como podemos obter um pouco mais de liberdade para iteração (ou seja, alterar os detalhes da implementação interna, permitindo refatoração e compartilhamento de código entre várias classes, etc.) é mais explícito sobre quais partes do código são uma superfície oficial, em vez de detalhes da implementação.

Uma coisa que já fizemos é introduzir o conceito de um recurso "experimental" (ele pertence ao namespace experimental, ele pode não ter testes/documentação e é propedido publicamente para existir, mas pode ser removido e atualizado sem aviso). Isso tem a liberdade de adicionar novos recursos mais cedo para obter comentários anteriores, mas não estar diretamente vinculados à sua superfície de API (porque pode não ter pensado totalmente na superfície da API).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Outros exemplos de coisas que podem ajudar no futuro

- Uso da [palavra-chave interna](/dotnet/csharp/language-reference/keywords/internal).
  Isso permitiria que possamos ter código compartilhado em nossos próprios assemblies (para reduzir a duplicação de código) sem tornar as coisas públicas para consumidores externos.
- Criação de um namespace "interno" (ou seja, Microsoft. MixedReality. Toolkit. Internal. Utilities), no qual documentamos publicamente que qualquer coisa contida nesse namespace interno está sujeita a alterações a qualquer momento e pode ser removida, etc. Isso é semelhante a como as bibliotecas de cabeçalho do C++ farão uso de:: namespaces internos para ocultar seus detalhes de implementação.