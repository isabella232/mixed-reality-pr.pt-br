---
title: Visão geral da programação
description: Saiba como acessar objetos e interfaces do maquette com scripts.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935318"
---
# <a name="programming-overview"></a>Visão geral da programação

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logotipo](../images/MaquetteIcon.png) Visão geral da programação

O Microsoft maquette usa JavaScript (ECMAScript 5,1 com extensões) com base no interpretador do [Jint](https://github.com/sebastienros/jint) . A extensão `.mqjs` é usada para distinguir arquivos JavaScript maquette do JavaScript normal.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Os objetos e as interfaces do maquette são acessíveis e programáveis por meio do `Maquette` objeto. A documentação sobre objetos e interfaces maquette é fornecida na referência de API do maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript é uma nova adição e, no fluxo, para que as alterações sejam esperadas. Documentação e atualizações mais detalhadas disponíveis em breve.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Destaques sobre scripts

* TBD-destaques de scripts focados como exemplos/tutoriais
  * 2x imagens/legendas – link para página de destaque

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Introdução ao MaquetteScript

* Mqjs vs. JS
* Modelo de Programação
  * Editando vs. em execução
* Link para fluxo de trabalho de programação
* Link para compartilhar resultados

## <a name="programming-workflow"></a>Fluxo de trabalho de programação

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Operação de script
* Operação do depurador
* Loop de depuração
* Copiar/colar código?

## <a name="running-mqjs-scripts"></a>Executando scripts. mqjs

<!-- TODO(Stefan): Need screenshot -->
Para executar um arquivo MaquetteScript. mqjs, vá para as janelas complementares do maquette e abra a guia script para localizar scripts.

> [!NOTE] 
> Algumas opções ainda não funcionarão, pois não enviamos os scripts.

## <a name="vscode-editor-workflow"></a>Fluxo de trabalho do editor de VSCode

Para avaliar o script em maquette de dentro de VSCode, o usuário precisa saber dois comandos:

   `CTRL-5` avalia o texto selecionado ou a linha inteira onde o cursor está localizado. 

   `CTRL-SHIFT-5` avalia o arquivo inteiro.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
O texto é enviado para maquette, avaliado no ambiente JavaScript e o resultado é enviado de volta para o console de saída do VSCode. Isso pode ser usado como um REPL (Read-eval-Print-loop).

## <a name="example-first-step"></a>Primeira etapa de exemplo

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copie o código a seguir em um arquivo em VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Selecione o código ou apenas as seções e clique `CTRL-5` para executar. Isso deve criar um cubo, colocá-lo na frente e alterar sua cor.

Há mais exemplos para localizar por meio da extensão.

## <a name="sharing-results"></a>Compartilhando resultados

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Como compartilhar entre usuários/equipes
* Projeto zip no diretório documentos
* Copiar projeto para compartilhamento de arquivos
* Adicionando o local do arquivo de envios de compartilhamento de equipe à equipe do maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Inclui, referência a código em outro lugar com caminhos relativos/absolutos, módulos
* DLLs?
* Suporte de runtime
* Externas não resolvidas-comportamento quando as entradas estão ausentes/falhando
* Podemos adicionar/editar/observar o script associado a objetos específicos?
  * Podemos copiar/colar este script em outro lugar?
  * E quanto às propriedades do objeto?
  * Nomeando objetos em minha cena? (renomeando script com ele)
  * Esta palavra-chave ou SELF para o script associado a um objeto
  * Se eu clicar com o botão direito do mouse em um objeto, posso ver o código associado a ele (e a sua hierarquia)
  * Posso selecionar na interface do usuário e ser colocado no código em VSCode?
  * Mantendo o código associado a um objeto "juntos" no arquivo de origem do script?
  * Trazer a janela de propriedades para cima de um objeto quando eu clicar nele? Em VR e na guia principal?
* Problemas de segurança
* Teste – pode ser TBD, mas poderíamos sugerir a captura de vídeo ou quadro por script
* Se tivermos um mecanismo de relatório de bugs, poderemos torná-lo acessível por meio de script para outros (?)... outro
* Implantação – como "compartilhar" o resultado, pacote como EXE
* Executando/controlando uma demonstração ou spectating/monitoramento
* Modo de jogador
* Podemos ter um segmento sobre como fazer "componentes" para compartilhamento? (pode ser TBD)
  * Há #include? Isso lida com o JS puro que eu suponhai, mas pode ter conflitos de namespace.
  * Há algo que poderíamos fazer para um maquette incorporar algum outro maquette com objetos nomeados para coincidir com o código JS?
