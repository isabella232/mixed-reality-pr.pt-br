---
title: Implementar inicializadores de aplicativos 3D (aplicativos UWP)
description: Como criar iniciadores de aplicativos 3D e logotipos para aplicativos e jogos do Windows Mixed Reality UWP (distribuídos por meio do Microsoft Store), tanto no HoloLens quanto em headsets de imersão (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, bloco, cubo ao vivo, link profundo, secondarytile, bloco secundário, UWP, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, XML, caixa delimitadora, Unity
ms.openlocfilehash: 38f0932f20e3660c91b87de7bcb9d66799d9a51a
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757487"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="ecc94-104">Implementar inicializadores de aplicativos 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="ecc94-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="ecc94-105">Esse recurso foi adicionado como parte da RS3 (atualização para criadores de outono do 2017) para headsets de imersão e tem suporte do HoloLens com a atualização do Windows 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="ecc94-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="ecc94-106">Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.16299 em headsets de imersão e 10.0.17125 no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ecc94-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="ecc94-107">Você pode encontrar as SDK do Windows mais recentes [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="ecc94-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="ecc94-108">O [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ecc94-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="ecc94-109">Ao criar um aplicativo UWP para a realidade mista do Windows, por padrão, os aplicativos são iniciados como slates 2D com o logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="ecc94-110">Ao desenvolver experiências para a realidade mista do Windows, um iniciador 3D pode, opcionalmente, ser definido para substituir o inicializador 2D padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="ecc94-111">Em geral, os iniciadores 3D são recomendados para iniciar aplicativos de imersão que levam os usuários da casa do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ecc94-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="ecc94-112">O inicializador 2D padrão é preferencial quando o aplicativo é ativado no local.</span><span class="sxs-lookup"><span data-stu-id="ecc94-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="ecc94-113">Você também pode criar um [link de 3D Deep (secondaryTile)](#3d-deep-links-secondarytiles) como um iniciador 3D para o conteúdo em um aplicativo UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="ecc94-114">processo de criação do inicializador de aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="ecc94-114">3D app launcher creation process</span></span>

<span data-ttu-id="ecc94-115">Há três etapas para criar um iniciador de aplicativo 3D:</span><span class="sxs-lookup"><span data-stu-id="ecc94-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="ecc94-116">Design e conceito</span><span class="sxs-lookup"><span data-stu-id="ecc94-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="ecc94-117">Modelagem e exportação</span><span class="sxs-lookup"><span data-stu-id="ecc94-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="ecc94-118">Integrando-o ao seu aplicativo (este artigo)</span><span class="sxs-lookup"><span data-stu-id="ecc94-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="ecc94-119">os ativos 3D a serem usados como iniciadores para seu aplicativo devem ser criados usando as [diretrizes de criação do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="ecc94-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="ecc94-120">Os ativos que não atenderem a essa especificação de criação não serão renderizados na página inicial do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ecc94-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="ecc94-121">Configurando o iniciador 3D</span><span class="sxs-lookup"><span data-stu-id="ecc94-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="ecc94-122">Quando você cria um novo projeto no Visual Studio, ele cria um bloco padrão simples que exibe o nome e o logotipo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="ecc94-123">Para substituir essa representação 2D por um modelo 3D personalizado, edite o manifesto de aplicativo do seu aplicativo para incluir o elemento "MixedRealityModel" como parte de sua definição de bloco padrão.</span><span class="sxs-lookup"><span data-stu-id="ecc94-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="ecc94-124">Para reverter para o inicializador 2D, basta remover a definição de MixedRealityModel do manifesto.</span><span class="sxs-lookup"><span data-stu-id="ecc94-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="ecc94-125">XML</span><span class="sxs-lookup"><span data-stu-id="ecc94-125">XML</span></span>

<span data-ttu-id="ecc94-126">Primeiro, localize o manifesto do pacote do aplicativo em seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ecc94-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="ecc94-127">Por padrão, o manifesto será nomeado Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="ecc94-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="ecc94-128">Se você estiver usando o Visual Studio, clique com o botão direito do mouse no manifesto no seu visualizador de solução e selecione **Exibir origem** para abrir o XML para edição.</span><span class="sxs-lookup"><span data-stu-id="ecc94-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="ecc94-129">Na parte superior do manifesto, adicione o esquema uap5 e inclua-o como um namespace ignorável:</span><span class="sxs-lookup"><span data-stu-id="ecc94-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="ecc94-130">Em seguida, especifique o "MixedRealityModel" no bloco padrão para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ecc94-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="ecc94-131">O elemento MixedRealityModel aceita um caminho de arquivo que aponta para um ativo 3D armazenado em seu pacote de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="ecc94-132">Atualmente, apenas modelos 3D entregues usando o formato de arquivo. glb e criados em relação às [instruções de criação de ativos 3D da realidade do Windows Mixed](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ecc94-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="ecc94-133">Os ativos devem ser armazenados no pacote do aplicativo e a animação não tem suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="ecc94-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="ecc94-134">Se o parâmetro "Path" for deixado em branco, o Windows mostrará o Tablet 2D em vez do iniciador 3D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="ecc94-135">**Observação:** o ativo. glb deve ser marcado como "conteúdo" em suas configurações de compilação antes de compilar e executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="ecc94-136">![Selecione o. glb no Gerenciador de soluções e use a seção Propriedades para marcá-lo como "conteúdo" nas configurações de compilação](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="ecc94-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="ecc94-137">*Selecione o. glb no Gerenciador de soluções e use a seção Propriedades para marcá-lo como "conteúdo" nas configurações de compilação*</span><span class="sxs-lookup"><span data-stu-id="ecc94-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="ecc94-138">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="ecc94-138">Bounding box</span></span>

<span data-ttu-id="ecc94-139">Uma caixa delimitadora pode ser usada para adicionar opcionalmente uma região extra do buffer ao objeto.</span><span class="sxs-lookup"><span data-stu-id="ecc94-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="ecc94-140">A caixa delimitadora é especificada usando um ponto central e extensões, que indicam a distância do centro da caixa delimitadora às suas bordas ao longo de cada eixo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="ecc94-141">As unidades da caixa delimitadora podem ser mapeadas para 1 unidade = 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="ecc94-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="ecc94-142">Se uma caixa delimitadora não for fornecida, uma será ajustada automaticamente à malha do objeto.</span><span class="sxs-lookup"><span data-stu-id="ecc94-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="ecc94-143">Se a caixa delimitadora fornecida for menor que o modelo, ela será redimensionada para se ajustar à malha.</span><span class="sxs-lookup"><span data-stu-id="ecc94-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="ecc94-144">O suporte para o atributo da caixa delimitadora será fornecido com a atualização RS4 do Windows como uma propriedade no elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="ecc94-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="ecc94-145">Para definir uma caixa delimitadora primeiro na parte superior do manifesto do aplicativo, adicione o esquema uap6 e inclua-o como namespaces ignoráveis:</span><span class="sxs-lookup"><span data-stu-id="ecc94-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="ecc94-146">Em seguida, no MixedRealityModel, defina a propriedade SpatialBoundingBox para definir a caixa delimitadora:</span><span class="sxs-lookup"><span data-stu-id="ecc94-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="ecc94-147">Usando o Unity</span><span class="sxs-lookup"><span data-stu-id="ecc94-147">Using Unity</span></span>

<span data-ttu-id="ecc94-148">Ao trabalhar com o Unity, o projeto deve ser compilado e aberto no Visual Studio antes que o manifesto do aplicativo possa ser editado.</span><span class="sxs-lookup"><span data-stu-id="ecc94-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="ecc94-149">O iniciador 3D deve ser redefinido no manifesto ao compilar e implantar uma nova solução do Visual Studio do Unity.</span><span class="sxs-lookup"><span data-stu-id="ecc94-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="ecc94-150">links de 3D Deep (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="ecc94-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="ecc94-151">Esse recurso foi adicionado como parte da RS3 (atualização para criadores de outono) de 2017 para fones de ouvido (VR) e como parte da atualização de abril de 2018 (RS4) para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ecc94-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="ecc94-152">Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.16299 em headsets de imersão (VR) e 10.0.17125 no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ecc94-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="ecc94-153">Você pode encontrar as SDK do Windows mais recentes [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="ecc94-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="ecc94-154">os secondaryTiles (3D Deep links) funcionam apenas com aplicativos UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="ecc94-155">No entanto, você pode criar um [iniciador de aplicativo 3D](implementing-3d-app-launchers.md) para iniciar um aplicativo exclusivo na página inicial do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ecc94-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="ecc94-156">Seus aplicativos 2D podem ser aprimorados para a realidade mista do Windows, adicionando a capacidade de posicionar modelos 3D de seu aplicativo na [casa do Windows Mixed Realm](../discover/navigating-the-windows-mixed-reality-home.md) como links profundos para conteúdo em seu aplicativo 2D, assim como [blocos 2D secundários](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) no menu Iniciar do Windows.</span><span class="sxs-lookup"><span data-stu-id="ecc94-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="ecc94-157">Por exemplo, você pode criar fotografias de 360 ° que se vinculam diretamente a um aplicativo de visualizador de fotos 360 ° ou permitem que os usuários coloquem o conteúdo 3D de uma coleção de ativos que abre uma página de detalhes sobre o autor.</span><span class="sxs-lookup"><span data-stu-id="ecc94-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="ecc94-158">Essas são apenas duas maneiras de expandir a funcionalidade do seu aplicativo 2D com conteúdo 3D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="ecc94-159">Criando um "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="ecc94-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="ecc94-160">Você pode posicionar o conteúdo 3D do seu aplicativo usando "secondaryTiles" definindo um modelo de realidade misturada no momento da criação.</span><span class="sxs-lookup"><span data-stu-id="ecc94-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="ecc94-161">Os modelos de realidade misturada são criados referenciando um ativo 3D em seu pacote de aplicativo e, opcionalmente, definindo uma caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="ecc94-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="ecc94-162">No momento, não há suporte para a criação de "secondaryTiles" de dentro de uma exibição exclusiva.</span><span class="sxs-lookup"><span data-stu-id="ecc94-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="ecc94-163">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="ecc94-163">Bounding box</span></span>

<span data-ttu-id="ecc94-164">Uma caixa delimitadora pode ser usada para adicionar uma região extra do buffer ao objeto.</span><span class="sxs-lookup"><span data-stu-id="ecc94-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="ecc94-165">A caixa delimitadora é especificada usando um ponto central e extensões, que indicam a distância do centro da caixa delimitadora às suas bordas ao longo de cada eixo.</span><span class="sxs-lookup"><span data-stu-id="ecc94-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="ecc94-166">As unidades da caixa delimitadora podem ser mapeadas para 1 unidade = 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="ecc94-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="ecc94-167">Se uma caixa delimitadora não for fornecida, uma será ajustada automaticamente à malha do objeto.</span><span class="sxs-lookup"><span data-stu-id="ecc94-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="ecc94-168">Se a caixa delimitadora fornecida for menor que o modelo, ela será redimensionada para se ajustar à malha.</span><span class="sxs-lookup"><span data-stu-id="ecc94-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="ecc94-169">Comportamento de ativação</span><span class="sxs-lookup"><span data-stu-id="ecc94-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="ecc94-170">Esse recurso terá suporte a partir da atualização RS4 do Windows.</span><span class="sxs-lookup"><span data-stu-id="ecc94-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="ecc94-171">Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.17125 se você planeja usar esse recurso</span><span class="sxs-lookup"><span data-stu-id="ecc94-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="ecc94-172">Você pode definir o comportamento de ativação para um secondaryTile 3D para controlar como ele reage quando um usuário o seleciona.</span><span class="sxs-lookup"><span data-stu-id="ecc94-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="ecc94-173">Isso pode ser usado para posicionar objetos 3D na casa misturada da realidade, que são puramente informativas ou decorativas.</span><span class="sxs-lookup"><span data-stu-id="ecc94-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="ecc94-174">Há suporte para os seguintes tipos de comportamento de ativação:</span><span class="sxs-lookup"><span data-stu-id="ecc94-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="ecc94-175">Padrão: quando um usuário seleciona o secondaryTile 3D, o aplicativo é ativado</span><span class="sxs-lookup"><span data-stu-id="ecc94-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="ecc94-176">Nenhum: quando o usuário seleciona o 3D secondaryTile, nada acontece e o aplicativo não é ativado.</span><span class="sxs-lookup"><span data-stu-id="ecc94-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="ecc94-177">Obtendo e atualizando um "secondaryTile" existente</span><span class="sxs-lookup"><span data-stu-id="ecc94-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="ecc94-178">Os desenvolvedores podem obter uma lista de seus blocos secundários existentes, que incluem as propriedades especificadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ecc94-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="ecc94-179">Eles também podem atualizar as propriedades alterando o valor e, em seguida, chamando UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="ecc94-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="ecc94-180">Verificando se o usuário está no Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ecc94-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="ecc94-181">os links de 3D Deep (secondaryTiles) só podem ser criados enquanto a exibição está sendo exibida em um headset de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="ecc94-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="ecc94-182">Quando o modo de exibição não está sendo apresentado em um headset de realidade misturada do Windows, é recomendável lidar normalmente com isso ocultando o ponto de entrada ou mostrando uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="ecc94-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="ecc94-183">Você pode verificar isso consultando [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="ecc94-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="ecc94-184">Notificações de bloco</span><span class="sxs-lookup"><span data-stu-id="ecc94-184">Tile notifications</span></span>

<span data-ttu-id="ecc94-185">Notificações de bloco atualmente não dão suporte ao envio de uma atualização com um ativo 3D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="ecc94-186">Isso significa que os desenvolvedores não podem fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ecc94-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="ecc94-187">Notificações por Push</span><span class="sxs-lookup"><span data-stu-id="ecc94-187">Push Notifications</span></span>
* <span data-ttu-id="ecc94-188">Sondagem periódica</span><span class="sxs-lookup"><span data-stu-id="ecc94-188">Periodic Polling</span></span>
* <span data-ttu-id="ecc94-189">Notificações agendadas</span><span class="sxs-lookup"><span data-stu-id="ecc94-189">Scheduled Notifications</span></span>

<span data-ttu-id="ecc94-190">Para obter mais informações sobre os outros recursos e atributos de blocos e como eles são usados para blocos 2D, consulte a [documentação blocos para aplicativos UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="ecc94-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="ecc94-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecc94-191">See also</span></span>

* <span data-ttu-id="ecc94-192">[Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contém um iniciador de aplicativo 3D.</span><span class="sxs-lookup"><span data-stu-id="ecc94-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="ecc94-193">Diretrizes de projeto do inicializador de aplicativos 3D</span><span class="sxs-lookup"><span data-stu-id="ecc94-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="ecc94-194">Criando modelos 3D para uso na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ecc94-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="ecc94-195">Implementando inicializadores de aplicativo 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="ecc94-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="ecc94-196">Como navegar na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ecc94-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
