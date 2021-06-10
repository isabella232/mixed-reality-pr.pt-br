---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110630821"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

A [caixa de diálogo de configuração do MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tentará definir as configurações de buffer de profundidade para o XR SDK e o WSA herdado, mas é bom verificar essas guias e verificar as configurações no Unity.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para definir se seu aplicativo de Unity fornecerá um buffer de profundidade para o Windows:

1. Vá para **Editar**  >  **configurações do projeto**  >  **Gerenciamento de plug-ins do XR** e verifique se o item de menu está expandido.
2. Clique no item de menu correspondente ao tempo de execução do XR escolhido, seja o Windows Mixed Reality ou OpenXR. Além disso, verifique se a plataforma de compilação correta está selecionada, pois as guias para Windows standalone e Plataforma Universal do Windows estão disponíveis.
3. Para habilitar e configurar o:
    1. Para OpenXR, selecione um formato de profundidade ou "nenhum" no menu suspenso do **modo de envio de profundidade** .
    2. Para a realidade mista do Windows, marque ou desmarque a caixa de seleção **buffer de profundidade compartilhada** . Em seguida, selecione um formato na lista suspensa **formato do buffer de profundidade** .

![Configurações de profundidade do plugin do Windows XR ](../../images/xrsdk-winxr-depth.png)
 ![ configurações de profundidade do OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Geralmente, é recomendável usar buffers de profundidade de 16 bits para melhorar o desempenho. No entanto, se você estiver usando o formato de profundidade de 16 bits, os efeitos necessários do buffer de estêncil (como alguns painéis de rolagem da interface do usuário do Unity) não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, em* geral, criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , se aplicável na plataforma de gráficos do ponto de extremidade.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para definir se seu aplicativo de Unity fornecerá um buffer de profundidade para o Windows:

1. Vá para **Editar**  >  **configurações do projeto**  >  **Player**  >  **plataforma universal do Windows guia**  >  **configurações do XR**.
2. Expanda o item **Windows Mixed Reality SDK** .
3. Marque ou desmarque a caixa de seleção **Habilitar compartilhamento de buffer de profundidade** . Habilitar o compartilhamento de buffer de profundidade é verificado por padrão em novos projetos, mas pode ter sido desmarcado por padrão em projetos mais antigos.

![Configurações de profundidade de XR herdadas](../../images/wmr-depth.png)

Um buffer de profundidade pode melhorar a qualidade visual desde que o Windows possa mapear com precisão os valores de profundidade por pixel normalizados no buffer de profundidade de volta para distâncias em metros, usando os planos próximos e distantes que você definiu no Unity na câmera principal. Se a renderização passar a lidar com valores de profundidade de maneiras típicas, geralmente você deve estar bom aqui, embora o processamento translúcida passe na gravação para o buffer de profundidade durante a exibição para pixels de cor existentes pode confundir a Reprojeção.  Se você souber que os seus passos de renderização deixarão muitos dos seus pixels de profundidade final com valores de profundidade imprecisos, você provavelmente obterá uma melhor qualidade visual desmarcando "Habilitar compartilhamento de buffer de profundidade".

> [!NOTE]
> Geralmente, é recomendável usar buffers de profundidade de 16 bits para melhorar o desempenho. No entanto, se você estiver usando o formato de profundidade de 16 bits, os efeitos necessários do buffer de estêncil (como alguns painéis de rolagem da interface do usuário do Unity) não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, em* geral, criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , se aplicável na plataforma de gráficos do ponto de extremidade.