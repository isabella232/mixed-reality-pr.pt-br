---
title: Recursos experimentais
description: Documento relacionado a recursos experimentais no MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 705b7ab96d22c5c94c04476de30e5524095c1ce2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144781"
---
# <a name="experimental-features"></a><span data-ttu-id="10800-104">Recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="10800-104">Experimental features</span></span>

<span data-ttu-id="10800-105">Alguns recursos em que a equipe do MRTK trabalha parecem ter muito valor inicial, mesmo que ainda não tenhamos completado os detalhes.</span><span class="sxs-lookup"><span data-stu-id="10800-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="10800-106">Para esses tipos de recursos, queremos que a comunidade receba a oportunidade de vê-los mais cedo.</span><span class="sxs-lookup"><span data-stu-id="10800-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="10800-107">Como eles estão no início do ciclo, os rotularemos como experimentais para indicar que ainda estão evoluindo e sujeitos a alterações ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="10800-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="10800-108">O que esperar de um recurso experimental</span><span class="sxs-lookup"><span data-stu-id="10800-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="10800-109">Se um componente for marcado como experimental, você poderá esperar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="10800-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="10800-110">Uma cena de exemplo que demonstra o uso, localizada `MRTK/Examples/Experimental` na sub pasta</span><span class="sxs-lookup"><span data-stu-id="10800-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="10800-111">Os recursos experimentais podem não ter documentos.</span><span class="sxs-lookup"><span data-stu-id="10800-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="10800-112">Provavelmente, eles não têm testes.</span><span class="sxs-lookup"><span data-stu-id="10800-112">They probably don't have tests.</span></span>
- <span data-ttu-id="10800-113">Os recursos experimentais estão sujeitos a alterações.</span><span class="sxs-lookup"><span data-stu-id="10800-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="10800-114">Diretrizes de recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="10800-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="10800-115">O código experimental deve residir em uma pasta separada</span><span class="sxs-lookup"><span data-stu-id="10800-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="10800-116">O código experimental deve entrar em uma pasta experimental de nível superior seguida pelo nome do recurso experimental.</span><span class="sxs-lookup"><span data-stu-id="10800-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="10800-117">Por exemplo, se estiver tentando contribuir com um novo recurso FooBar, coloque o código no seguinte:</span><span class="sxs-lookup"><span data-stu-id="10800-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="10800-118">Cenas de exemplo, os scripts vão para `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="10800-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="10800-119">Scripts de componente, pré-requisitos para `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="10800-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="10800-120">Os inspetores de componentes vão para `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="10800-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="10800-121">Ao usar sub pastas sob o nome do recurso experimental, tente espelhar a mesma estrutura de pastas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="10800-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="10800-122">Por exemplo, os solucionadores entrariam em `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="10800-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="10800-123">Mantenha cenas em uma pasta de cena perto da parte superior: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="10800-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="10800-124">Consideramos não ter uma única pasta raiz experimental e, em vez disso, colocar o experimental sob digamos `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="10800-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="10800-125">Decidimos usar as pastas na base para facilitar a descoberta dos recursos experimentais.</span><span class="sxs-lookup"><span data-stu-id="10800-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="10800-126">O código experimental deve estar em um namespace especial</span><span class="sxs-lookup"><span data-stu-id="10800-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="10800-127">Verifique se o código experimental reside em um namespace experimental que corresponde ao local não experimental.</span><span class="sxs-lookup"><span data-stu-id="10800-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="10800-128">Por exemplo, se o componente fizer parte de solveres em `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , seu namespace deverá ser `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="10800-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="10800-129">Consulte [esta PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="10800-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="10800-130">Os recursos experimentais devem ter um atributo [experimental]</span><span class="sxs-lookup"><span data-stu-id="10800-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="10800-131">Adicione um `[Experimental]` atributo acima de um dos campos para que uma pequena caixa de diálogo apareça no editor de componentes que mencione que o recurso é experimental e esteja sujeito a alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="10800-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="10800-132">Os menus para recursos experimentais devem estar no submenu "experimental"</span><span class="sxs-lookup"><span data-stu-id="10800-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="10800-133">Verifique se os recursos experimentais estão em submenus "experimentais" ao adicionar comandos aos menus no editor.</span><span class="sxs-lookup"><span data-stu-id="10800-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="10800-134">Veja alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="10800-134">Here are a few examples:</span></span>

<span data-ttu-id="10800-135">Adicionando um comando de menu de nível superior:</span><span class="sxs-lookup"><span data-stu-id="10800-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="10800-136">Adicionando um menu de componentes:</span><span class="sxs-lookup"><span data-stu-id="10800-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="10800-137">Documentação</span><span class="sxs-lookup"><span data-stu-id="10800-137">Documentation</span></span>

<span data-ttu-id="10800-138">Siga estas etapas para adicionar a documentação para seu recurso experimental:</span><span class="sxs-lookup"><span data-stu-id="10800-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="10800-139">Qualquer documentação para um recurso experimental deve estar em um `readme.md` arquivo na pasta experimental.</span><span class="sxs-lookup"><span data-stu-id="10800-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="10800-140">Por exemplo, MRTK/SDK/experimental/PulseShader/README. MD.</span><span class="sxs-lookup"><span data-stu-id="10800-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="10800-141">Em *visões gerais de recurso* , adicione um link na seção *experimental* em [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="10800-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="10800-142">Minimizar o impacto no código MRTK</span><span class="sxs-lookup"><span data-stu-id="10800-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="10800-143">Embora sua alteração MRTK possa fazer com que seu experimento funcione, isso pode afetar outras pessoas de maneiras que você não espera.</span><span class="sxs-lookup"><span data-stu-id="10800-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="10800-144">Quaisquer regressões feitas ao código do MRTK Core resultarão na reversão da sua solicitação pull.</span><span class="sxs-lookup"><span data-stu-id="10800-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="10800-145">O objetivo de ter zero alterações em pastas diferentes das pastas experimentais.</span><span class="sxs-lookup"><span data-stu-id="10800-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="10800-146">Aqui está uma lista de pastas que podem ter alterações experimentais:</span><span class="sxs-lookup"><span data-stu-id="10800-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="10800-147">MRTK/SDK/Experimental</span><span class="sxs-lookup"><span data-stu-id="10800-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="10800-148">MRTK/SDK/Inspetores/Experimental</span><span class="sxs-lookup"><span data-stu-id="10800-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="10800-149">MRTK/Examples/Experimental</span><span class="sxs-lookup"><span data-stu-id="10800-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="10800-150">As alterações fora dessas pastas devem ser tratadas com muito cuidado.</span><span class="sxs-lookup"><span data-stu-id="10800-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="10800-151">Se o recurso experimental deve incluir alterações no código principal do MRTK, considere dividir as alterações do MRTK em uma solicitação pull separada que inclui testes e documentação.</span><span class="sxs-lookup"><span data-stu-id="10800-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="10800-152">Usar seu recurso experimental não deve afetar a capacidade das pessoas de usar controles principais</span><span class="sxs-lookup"><span data-stu-id="10800-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="10800-153">A maioria das pessoas usa componentes de experiência do usuário principais, como o botão ManipulationHandler e o Interactable com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="10800-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="10800-154">Provavelmente, eles não usarão seu recurso experimental se impedirem o uso de botões.</span><span class="sxs-lookup"><span data-stu-id="10800-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="10800-155">O uso do componente não deve quebrar botões, ManipulationHandler, BoundingBox ou interaja.</span><span class="sxs-lookup"><span data-stu-id="10800-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="10800-156">Por exemplo, nesta [PR ScrollableObjectCollection](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), a adição de um ScrollableObjectCollection fez com que as pessoas não fosse capazes de usar os pré-fabs de botão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10800-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="10800-157">Embora isso não tenha sido causado por um bug na PR (mas, em vez disso, expôs um bug existente), ele impediu que a PR fosse verificada.</span><span class="sxs-lookup"><span data-stu-id="10800-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="10800-158">Forneça uma cena de exemplo que demonstra como usar o recurso</span><span class="sxs-lookup"><span data-stu-id="10800-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="10800-159">As pessoas precisam ver como usar seu recurso e como testá-lo.</span><span class="sxs-lookup"><span data-stu-id="10800-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="10800-160">Forneça um exemplo em MRTK/Examples/Experimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="10800-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="10800-161">Minimizar falhas visíveis do usuário em recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="10800-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="10800-162">Outros não usarão o recurso experimental se ele não funcionar, ele não será formado para um recurso.</span><span class="sxs-lookup"><span data-stu-id="10800-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="10800-163">Teste sua cena de exemplo em sua plataforma de destino, certifique-se de que ela funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="10800-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="10800-164">Certifique-se de que seu recurso também funcione no editor, para que as pessoas possam iterar rapidamente e ver seu recurso, mesmo que não tenham a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="10800-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="10800-165">Como transformar código experimental em código MRTK</span><span class="sxs-lookup"><span data-stu-id="10800-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="10800-166">Se um recurso acabar vendo muito uso, devemos gradua-lo no código principal de MRTK.</span><span class="sxs-lookup"><span data-stu-id="10800-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="10800-167">Para fazer isso, o recurso deve ter testes, documentação e uma cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="10800-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="10800-168">Quando estiver pronto para graduar o recurso MRTK, crie um problema para fazer check-in do seu PR em relação ao.</span><span class="sxs-lookup"><span data-stu-id="10800-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="10800-169">A PR deve incluir todas as coisas necessárias para tornar esse recurso principal: testes, documentação e uma cena de exemplo mostrando o uso.</span><span class="sxs-lookup"><span data-stu-id="10800-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="10800-170">Além disso, não se esqueça de atualizar os namespaces para remover o subespaço "experimental".</span><span class="sxs-lookup"><span data-stu-id="10800-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
