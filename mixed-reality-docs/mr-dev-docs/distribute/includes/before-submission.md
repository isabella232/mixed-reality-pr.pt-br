---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198773"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Se você tiver um HoloLens, escolha sua opção de [distribuição preferencial](../distribute-overview.md#distribution-options) na tabela abaixo. Se você estiver publicando no Microsoft Store, terá a opção [](../in-app-purchases.md) de adicionar compras no aplicativo para monetizar seu conteúdo.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Se você estiver trabalhando com um aplicativo imersivo destinado a um headset Windows Mixed Reality, crie um launcher [](../distribute-overview.md#distribution-options) de aplicativo 3D e escolha a opção de distribuição preferencial na tabela abaixo. Se você estiver publicando no Microsoft Store, terá a opção [](../in-app-purchases.md) de adicionar compras no aplicativo para monetizar seu conteúdo.

### <a name="designing-3d-app-launchers-for-vr"></a>Projetando iniciadores de aplicativo 3D para VR 

Os iniciadores de aplicativo 3D aparecem como objetos no ambiente Windows Mixed Reality home que aparece sempre que um usuário coloca um headset imersivo. Esses objetos são seus para criar e personalizar da forma que você quiser, mas é recomendável que você comece com nosso artigo de diretrizes de [design](../3d-app-launcher-design-guidance.md) para obter o travamento de boas práticas de design, incluindo dimensionamento, tipo, escolha de cor, texto e, acima de tudo, tornando-o destaque em um ambiente virtual.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modelagem e exportação de iniciadores de aplicativo 3D

Depois de definir a ideia do seu launcher de aplicativo 3D, você precisará garantir que ele atenda aos requisitos do Microsoft Store, incluindo formato de arquivo de ativo, contagem de triângulos, tamanhos de textura, comprimento da animação e otimização de ativos. Esse processo pode ser altamente técnico, portanto, é recomendável usar nosso artigo de criação de modelo [3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para verificar todas as caixas. Os ativos que não atenderem a essa especificação de autor não serão renderizados no Windows Mixed Reality home.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Adicionando iniciadores de aplicativo 3D em seus aplicativos

Depois de garantir que o launcher do aplicativo 3D atenda às diretrizes de Windows Mixed Reality de Windows Mixed Reality, ele poderá ser usado para substituir o launcher 2D padrão para seu aplicativo no ambiente Windows Mixed Reality home. O processo para integrar um launcher de aplicativo 3D ao seu aplicativo depende do tipo de aplicativo que você está desenvolvendo:

* [Aplicativos UWP](../implementing-3d-app-launchers.md)
* [Aplicativos Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>[Opcional] Colocar modelos 3D na página Windows Mixed Reality página

Como um bônus adicional, alguns aplicativos 2D permitem colocar modelos 3D diretamente na Windows Mixed Reality como decorações ou para inspeção adicional em 3D completo. O protocolo add model permite que você envie um modelo 3D do seu site ou aplicativo para a página inicial do Windows Mixed Reality, em que ele persistirá como launchers de aplicativos 3D, aplicativos 2D e hologramas. Confira como [colocar modelos 3D](../enable-placement-of-3d-models-in-the-home.md) na página Windows Mixed Reality para encontrar mais detalhes e instruções sobre como aumente seus próprios aplicativos.