---
title: Sobre o Maquette
description: Introdução ao maquette e a seus recursos.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, protótipos, realidade misturada, realidade Virtual, VR, sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: 81c09bf22ea531a76156c9264e127593b6302ad5d0bcb248de9518bfb647717b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197880"
---
# <a name="about-maquette"></a>Sobre o Maquette

<!-- TODO(Harrison): Need consolidated logo with text -->
![Introdução do logotipo ](../images/MaquetteIcon.png) MaquetteScript

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
O maquette integra o JavaScript padrão ECMA 5,1 para habilitar o investimento de interatividade em cenas de maquette e objetos que podem ser editados e executados no VSCode. As propriedades de objetos são expostas para leitura e configuração de dentro do script, métodos de objeto chamados e eventos de objeto e sistema. O script também pode interagir com o maquette em si por meio de objetos do sistema acessíveis por meio de script. Vários controles de interface de usuário com os quais o usuário pode interagir fazem parte do sistema. Eles podem ser adicionados durante a criação no maquette ou criados e gerenciados de dentro do script. Eventos de interação do usuário com esses elementos (entrada de dados, cliques, etc) também são expostos a scripts como eventos. Com essas adições, podem ser criadas cenas simples de complexas, desde experimentos até visualização de dados até explorações de cenários de usuário de realidade misturada até experiências totalmente percebidas em AR ou VR.

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
vídeo de 60 second'ish
* Cartão de título de entrada
  * Criação de conteúdo interativo de realidade misturada no maquette
  * Script/sistema de interface do usuário/interatividade
* O VO Welcome por legendas de equipe ou de vídeo?  explicando
  * raciocínio por trás do script para habilitar a criação de conteúdo interativo de MR
  * toque em como ele pode ser usado em traços de pincel muito amplos
* Vingette de scripts em ação
  * Caixa de diálogo de composição
  * Criando aplicativo a partir da estrutura de tópicos (demonstração do aplicativo de culinária)
  * Composição no modelo Photogrammetry
  * Interagindo com o guia de solução de problemas
  * Exibição de tela da depuração de scripts no VSCode
  * Obtendo acesso ao script de um objeto em cena
  * Etc...
* Cartão de título de resumo no final
  * Link para maquette
  * Onde ir para introdução ao script
  * Comunicados/status/Comunidade
  * Aguardar para ver o que você pode fazer/envios (?)
  * Comentários e como podemos atendê-lo melhor

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [Introdução](installation.md)
* [Exemplos e aplicativos de exemplo](../samples/overview.md)
* [Suporte](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a>Enviar seus comentários

Estamos ansiosos por ouvir suas experiências e resultados. Comentários, sugestões e relatórios de bugs sempre são bem-vindos!
<Link? >