---
title: Idioma principal
description: Saiba mais sobre os principais detalhes da linguagem da Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, criação de protótipos, Realidade Misturada, Realidade Virtual, VR, MR, Comentários, Hub de Comentários, bugs
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197396"
---
# <a name="maquettescript-core-language-details"></a>Detalhes da linguagem principal do MaquetteScript

<!-- TODO(Harrison): Need consolidated logo with text -->
![Logotipo maquette ](../images/MaquetteIcon.png) MaquetteScript Core Language Details

## <a name="accessing-maquette-object-and-namespace"></a>Acessando `Maquette` o objeto e o namespace

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
A Maquette expõe objetos e interfaces internos em JavaScript por meio do `Maquette` objeto e seus filhos. Essa funcionalidade é descrita na documentação [de Objeto e Namespace do Maquette.](https://www.maquette.ms/doc_staging/objects/Maquette.html) 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
O objeto tem funções de nível superior para facilitar a interação com o próprio Maquette e facilitar a resolução de problemas `Maquette` repetitivos. Isso é descrito na documentação de [MaquetteScriptObject.](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)

## <a name="maquette-startup-and-loading"></a>Inicialização e carregamento do Maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
O Maquette carregará e avaliará arquivos JavaScript específicos para habilitar a configuração, a instalação e a inicialização nos seguintes momentos:

Durante a inicialização do Maquette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Sempre que qualquer projeto é carregado:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Os projetos carregam seus respectivos scripts de projeto:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implementação de JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
O interpretador de JavaScript usado no Maquette é baseado em [Jint.](https://github.com/sebastienros/jint) Jint é compatível com ECMAScript 5.1 e dá suporte a extensões [adicionais do ECMAScript 6.](https://github.com/sebastienros/jint/issues/343) 

A extensão `.mqjs` é usada para distinguir arquivos JavaScript maquette do JavaScript normal.

## <a name="see-also"></a>Confira também 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->