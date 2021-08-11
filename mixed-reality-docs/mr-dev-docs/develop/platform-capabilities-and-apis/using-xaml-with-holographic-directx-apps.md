---
title: Como usar o XAML com aplicativos DirectX holográficos
description: Explica o impacto de alternar entre exibições do XAML 2D e exibições de imersão em seu aplicativo DirectX e como fazer uso eficiente de uma exibição XAML e de imersão.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: realidade mista do Windows, UWP, gerenciamento de exibição de aplicativo, XAML, teclado, passo a passos, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220942"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Como usar o XAML com aplicativos DirectX holográficos

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](../native/openxr-getting-started.md)**.

Este tópico explica o impacto de alternar entre [exibições do XAML 2D e exibições de imersão](../../design/app-views.md) em seu aplicativo DirectX e como fazer uso eficiente de uma exibição XAML e exibição imersiva.

## <a name="xaml-view-switching-overview"></a>Visão geral de alternância de exibição XAML

no HoloLens, um aplicativo de imersão que, posteriormente, pode exibir uma exibição xaml 2d precisa inicializar o modo de exibição xaml primeiro e imediatamente alternar para uma exibição de imersão a partir daí. O XAML será carregado antes que seu aplicativo possa fazer qualquer coisa, o que adiciona um pequeno aumento ao tempo de inicialização. O XAML continuará ocupando espaço de memória no processo do aplicativo enquanto ele permanecer em segundo plano. A quantidade de atraso de inicialização e uso de memória depende do que seu aplicativo faz com XAML antes de alternar para a exibição nativa. Se você não fizer nada no código de inicialização do XAML a princípio, exceto iniciar o modo de exibição de imersão, o impacto deverá ser menor. Além disso, como a renderização Holographic é feita diretamente na exibição imersiva, você evitará restrições relacionadas a XAML nessa renderização.

O uso de memória conta para CPU e GPU. O Direct3D 11 pode trocar a memória gráfica virtual, mas pode não ser capaz de trocar alguns ou todos os recursos de GPU XAML, e pode haver um impacto perceptível no desempenho. De qualquer forma, não carregar nenhum recurso XAML de que você não precisa deixará mais espaço para seu aplicativo e fornecerá uma experiência melhor.

## <a name="xaml-view-switching-workflow"></a>Fluxo de trabalho de alternância de exibição XAML

O fluxo de trabalho para um aplicativo que vai diretamente do XAML para o modo de imersão é assim:
* O aplicativo é iniciado na exibição 2D XAML.
* A sequência de inicialização XAML do aplicativo detecta se o sistema atual dá suporte à renderização Holographic:
* Em caso afirmativo, o aplicativo cria a exibição imersiva e a coloca em primeiro plano imediatamente. o carregamento de XAML é ignorado para qualquer coisa não necessária em dispositivos Windows Mixed Reality, incluindo quaisquer classes de renderização e carregamento de ativos na exibição XAML. Se o aplicativo estiver usando XAML para entrada de teclado, essa página de entrada ainda deverá ser criada.
* Caso contrário, o modo de exibição XAML pode continuar com os negócios normalmente.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Dica para renderizar elementos gráficos em ambas as exibições

se seu aplicativo precisar implementar alguma quantidade de renderização no DirectX para o modo de exibição XAML no Windows Mixed Reality, sua melhor aposta é criar um renderizador que possa funcionar com ambos os modos. O renderizador deve ser uma instância que possa ser acessada de ambos os modos de exibição e deve alternar entre a renderização 2D e Holographic. Dessa forma, os ativos de GPU são carregados apenas uma vez, o que reduz os tempos de carregamento, o impacto de memória e a quantidade de recursos trocados ao alternar entre exibições.
