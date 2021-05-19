---
title: Instância de material
description: Documentação sobre a Instância de Material e seus usos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, MaterialInstance,
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145216"
---
# <a name="material-instance"></a>Instância de material

O comportamento auxiliará no tempo de vida do material da instância de acompanhamento e destruirá automaticamente os materiais da instância [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) para o usuário. Esse componente do utilitário pode ser usado como uma substituição para [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ou [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) são preferenciais em vez de instanciamento de material, mas nem sempre estão disponíveis em todos os cenários.

Por que usar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) pode ser um problema? Se você adicionar o código abaixo a uma cena do Unity e tocar em reproduzir o uso de memória, o continuará a se ressuar e prosseguir:

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
> O comportamento de Vazamento acima **falhará no Unity** se for muito longo!

Como alternativa, tente usar o [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento:

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

## <a name="usage"></a>Uso

Ao invocar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) do Unity, o Unity cria automaticamente novos materiais. É responsabilidade do chamador destruir os materiais quando um material não é mais necessário ou o objeto do jogo é destruído. O [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento ajuda a evitar vazamentos de material e mantém os caminhos de alocação de material consistentes durante a edição e o tempo de operação.

Quando um [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) não puder ser usado e um material deve ser instânciado, poderá ser [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) usado da seguinte forma:

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

Se vários objetos precisam de propriedade da instância de material, é melhor assumir a propriedade explícita para o acompanhamento de referência. (Existe uma interface opcional [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) chamada para auxiliar com propriedade.) Veja abaixo um exemplo de uso:

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

Para obter mais informações, consulte o uso de exemplo demonstrado dentro do [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.

## <a name="see-also"></a>Confira também

* [Sombreador padrão MRTK](mrtk-standard-shader.md)
