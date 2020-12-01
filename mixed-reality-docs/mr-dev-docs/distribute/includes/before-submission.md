---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443501"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Se você tiver um aplicativo HoloLens, escolha sua [opção de distribuição](../distribute-overview.md#distribution-options) preferida na tabela a seguir. Se estiver publicando no Microsoft Store, você terá a opção de adicionar [compras no aplicativo](../in-app-purchases.md) para monetizar seu conteúdo.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Se você estiver trabalhando com um aplicativo de imersão que tem como alvo um headset de realidade mista do Windows, crie um iniciador de aplicativo 3D e escolha sua [opção de distribuição](../distribute-overview.md#distribution-options) preferida na tabela a seguir. Se estiver publicando no Microsoft Store, você terá a opção de adicionar [compras no aplicativo](../in-app-purchases.md) para monetizar seu conteúdo.

### <a name="designing-3d-app-launchers-for-vr"></a>Projetando iniciadores de aplicativos 3D para VR 

os iniciadores de aplicativos 3D aparecem como objetos no ambiente inicial do Windows Mixed Reality que aparece sempre que um usuário coloca um headset de imersão. Esses objetos são seus para criar e personalizar, como você gosta, mas é recomendável que você comece com nosso artigo de [diretrizes de design](../3d-app-launcher-design-guidance.md) para obter as boas práticas de design, incluindo dimensionamento, tipo, escolha de cor, texturing e acima tudo o que o torna em um ambiente virtual.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modelando e exportando inicializadores de aplicativo 3D

Depois de definir a ideia para seu iniciador de aplicativo 3D, você precisa verificar se ele atende aos requisitos de Microsoft Store, incluindo formato de arquivo de ativo, contagem de triângulo, tamanhos de textura, tamanho da animação e otimização de ativos. Esse processo pode ser altamente técnico e, portanto, é recomendável usar nosso artigo de [criação de modelo 3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para marcar todas as caixas. Os ativos que não atenderem a essa especificação de criação não serão renderizados na página inicial do Windows Mixed Reality.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Adicionando inicializadores de aplicativo 3D em seus aplicativos

Depois de garantir que seu iniciador de aplicativo 3D atenda às diretrizes de criação do Windows Mixed Reality, ele pode ser usado para substituir o inicializador 2D padrão para seu aplicativo no ambiente doméstico do Windows Mixed Reality. O processo de integração de um iniciador de aplicativo 3D em seu aplicativo depende do tipo de aplicativo que você está desenvolvendo:

* [Aplicativos UWP](../implementing-3d-app-launchers.md)
* [Aplicativos Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Adicional Colocando modelos 3D na página inicial do Windows Mixed Reality

Como um bônus adicional, alguns aplicativos 2D permitem que você coloque modelos 3D diretamente na casa da realidade mista do Windows como decorações ou para uma inspeção mais detalhada no 3D completo. O protocolo adicionar modelo permite que você envie um modelo 3D do seu site ou aplicativo para a página inicial do Windows Mixed Realm, onde ele persistirá, como inicializadores de aplicativos 3D, aplicativos 2D e hologramas. Confira [como posicionar modelos 3D na página inicial do Windows Mixed Reality](../enable-placement-of-3d-models-in-the-home.md) para encontrar mais detalhes e instruções sobre como dar vida a seus próprios aplicativos.