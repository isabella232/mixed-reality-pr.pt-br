---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212190"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

A [caixa de diálogo de configuração do MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tentará definir as configurações de buffer de profundidade para o XR SDK e o WSA herdado, mas é bom verificar essas guias e verificar as configurações no Unity.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para definir se seu aplicativo de Unity fornecerá um buffer de profundidade para Windows:

1. vá para **editar**  >  **Project**  >  o **gerenciamento de Plug-ins Configurações XR** e verifique se o item de menu está expandido.
2. clique no item de menu correspondente ao tempo de execução de XR escolhido, seja Windows Mixed Reality ou OpenXR. além disso, verifique se a plataforma de compilação correta está selecionada, pois as guias para Windows autônomos e Plataforma Universal do Windows estão disponíveis.
3. Para habilitar e configurar o:
    1. Para OpenXR, selecione um formato de profundidade ou "nenhum" no menu suspenso do **modo de envio de profundidade** .
    2. para Windows Mixed Reality, marque ou desmarque a caixa de seleção **Buffer de profundidade compartilhada** . Em seguida, selecione um formato na lista suspensa **formato do buffer de profundidade** .

![Windows Configurações de profundidade do plugin XR ](../../images/xrsdk-winxr-depth.png)
 ![ configurações de profundidade de OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Geralmente, é recomendável usar buffers de profundidade de 16 bits para melhorar o desempenho. No entanto, se você estiver usando o formato de profundidade de 16 bits, os efeitos necessários do buffer de estêncil (como alguns painéis de rolagem da interface do usuário do Unity) não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, em* geral, criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , se aplicável na plataforma de gráficos do ponto de extremidade.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para definir se seu aplicativo de Unity fornecerá um buffer de profundidade para Windows:

1. vá para **editar**  >  **Project Configurações**  >  **Player**  >  **Plataforma Universal do Windows guia**  >  **XR Configurações**.
2. expanda o item **Windows Mixed Reality SDK** .
3. Marque ou desmarque a caixa de seleção **Habilitar compartilhamento de buffer de profundidade** . Habilitar o compartilhamento de buffer de profundidade é verificado por padrão em novos projetos, mas pode ter sido desmarcado por padrão em projetos mais antigos.

![Configurações de profundidade de XR herdadas](../../images/wmr-depth.png)

um buffer de profundidade pode melhorar a qualidade visual desde que Windows possa mapear com precisão os valores de profundidade por pixel normalizados em seu buffer de profundidade de volta para distâncias em metros, usando os planos próximos e distantes que você definiu no Unity na câmera principal. Se a renderização passar a lidar com valores de profundidade de maneiras típicas, geralmente você deve estar bom aqui, embora o processamento translúcida passe na gravação para o buffer de profundidade durante a exibição para pixels de cor existentes pode confundir a Reprojeção.  Se você souber que os seus passos de renderização deixarão muitos dos seus pixels de profundidade final com valores de profundidade imprecisos, você provavelmente obterá uma melhor qualidade visual desmarcando "Habilitar compartilhamento de buffer de profundidade".

> [!NOTE]
> Geralmente, é recomendável usar buffers de profundidade de 16 bits para melhorar o desempenho. No entanto, se você estiver usando o formato de profundidade de 16 bits, os efeitos necessários do buffer de estêncil (como alguns painéis de rolagem da interface do usuário do Unity) não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, em* geral, criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , se aplicável na plataforma de gráficos do ponto de extremidade.