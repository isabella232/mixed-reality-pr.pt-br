---
title: Instância de material
description: Documentação sobre a instância material e seus usos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, MaterialInstance,
ms.openlocfilehash: 6d9a2a35a009bfce1fcfae15000ea02c47be637a8c5a483254ea30d9948922e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210046"
---
# <a name="material-instance"></a>Instância de material

O [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento ajuda a controlar o tempo de vida do material da instância e destrói automaticamente os materiais em instância para o usuário. Este componente do utilitário pode ser usado como uma substituição para [renderizador. material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ou [renderizador. materiais](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) são preferenciais sobre a criação de instâncias de material, mas nem sempre estão disponíveis em todos os cenários.

Por que usar o [Renderer. material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) é um problema? Se você adicionar o código abaixo a uma cena do Unity e pressionar a opção usar uso de memória continuará a subir e subir:

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
> O comportamento de vazamento acima **falhará no Unity** se for executado por muito tempo!

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

Ao invocar [renderizador. material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) do Unity, o Unity instancia automaticamente os novos materiais. É responsabilidade do chamador destruir os materiais quando um material não é mais necessário ou quando o objeto do jogo é destruído. O [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento ajuda a evitar vazamentos de material e mantém os caminhos de alocação de material consistentes durante a edição e o tempo de execução.

Quando um [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) não pode ser usado e um material deve ser em instância, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) pode ser usado da seguinte maneira:

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

Se vários objetos precisarem de propriedade da instância material, é melhor ter uma propriedade explícita para o acompanhamento de referência. (Uma interface opcional chamada [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) existe para auxílio com a propriedade.) Veja a seguir um exemplo de uso:

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

Para obter mais informações, consulte o exemplo de uso demonstrado dentro do [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.

## <a name="see-also"></a>Confira também

* [Sombreador padrão MRTK](mrtk-standard-shader.md)
