---
title: Instância de material
description: Documentação sobre a Instância de Material e seus usos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, MaterialInstance,
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176723"
---
# <a name="material-instance"></a><span data-ttu-id="485be-104">Instância de material</span><span class="sxs-lookup"><span data-stu-id="485be-104">Material instance</span></span>

<span data-ttu-id="485be-105">O comportamento auxiliará no tempo de vida do material da instância de acompanhamento e destruirá automaticamente os materiais da instância [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) para o usuário.</span><span class="sxs-lookup"><span data-stu-id="485be-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="485be-106">Esse componente do utilitário pode ser usado como uma substituição para [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ou [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)</span><span class="sxs-lookup"><span data-stu-id="485be-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="485be-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) são preferenciais em vez de instanciamento de material, mas nem sempre estão disponíveis em todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="485be-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="485be-108">Por que usar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) pode ser um problema?</span><span class="sxs-lookup"><span data-stu-id="485be-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="485be-109">Se você adicionar o código abaixo a uma cena do Unity e tocar em reproduzir o uso de memória, o continuará a se ressuar e prosseguir:</span><span class="sxs-lookup"><span data-stu-id="485be-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="485be-110">O comportamento de Vazamento acima **falhará no Unity** se for muito longo!</span><span class="sxs-lookup"><span data-stu-id="485be-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="485be-111">Como alternativa, tente usar o [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento:</span><span class="sxs-lookup"><span data-stu-id="485be-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="485be-112">Uso</span><span class="sxs-lookup"><span data-stu-id="485be-112">Usage</span></span>

<span data-ttu-id="485be-113">Ao invocar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) do Unity, o Unity cria automaticamente novos materiais.</span><span class="sxs-lookup"><span data-stu-id="485be-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="485be-114">É responsabilidade do chamador destruir os materiais quando um material não é mais necessário ou o objeto do jogo é destruído.</span><span class="sxs-lookup"><span data-stu-id="485be-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="485be-115">O [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento ajuda a evitar vazamentos de material e mantém os caminhos de alocação de material consistentes durante a edição e o tempo de operação.</span><span class="sxs-lookup"><span data-stu-id="485be-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="485be-116">Quando um [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) não puder ser usado e um material deve ser instânciado, poderá ser [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) usado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="485be-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="485be-117">Se vários objetos precisam de propriedade da instância de material, é melhor assumir a propriedade explícita para o acompanhamento de referência.</span><span class="sxs-lookup"><span data-stu-id="485be-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="485be-118">(Existe uma interface opcional [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) chamada para auxiliar com propriedade.) Veja abaixo um exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="485be-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="485be-119">Para obter mais informações, consulte o uso de exemplo demonstrado dentro do [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.</span><span class="sxs-lookup"><span data-stu-id="485be-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="485be-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="485be-120">See also</span></span>

* [<span data-ttu-id="485be-121">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="485be-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
