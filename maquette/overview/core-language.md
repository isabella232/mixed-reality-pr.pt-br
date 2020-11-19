---
title: Idioma principal
description: Saiba mais sobre os detalhes da linguagem principal do maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935357"
---
# <a name="maquettescript-core-language-details"></a>Detalhes da linguagem MaquetteScript Core

<!-- TODO(Harrison): Need consolidated logo with text -->
![Detalhes do ](../images/MaquetteIcon.png) idioma principal do maquette logo MaquetteScript

## <a name="accessing-maquette-object-and-namespace"></a>Acessando `Maquette` objeto e namespace

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
O maquette expõe objetos internos e interfaces em JavaScript por meio do `Maquette` objeto e de seus filhos. Essa funcionalidade é descrita no [objeto maquette e](https://www.maquette.ms/doc_staging/objects/Maquette.html) na documentação do namespace. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
O `Maquette` objeto tem funções de nível superior para facilitar a interação com o próprio maquette e facilitar a solução de problemas repetitivos. Isso é descrito na documentação do [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Inicialização e carregamento do maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
O maquette carregará e avaliará arquivos JavaScript específicos para habilitar a configuração, a instalação e a inicialização nos seguintes horários:

Durante a inicialização do maquette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Sempre que qualquer projeto for carregado:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Os projetos carregam seus respectivos scripts de projeto:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implementação de JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
O interpretador JavaScript usado em maquette é baseado em [Jint](https://github.com/sebastienros/jint). O Jint é compatível com ECMAScript 5,1 e dá suporte a [extensões adicionais do ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

A extensão `.mqjs` é usada para distinguir arquivos JavaScript maquette do JavaScript normal.

## <a name="see-also"></a>Confira também 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->