---
title: Estrutura e runtime
description: Informações relacionadas à estrutura e ao runtime no MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121603"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="1919e-104">Estrutura e runtime</span><span class="sxs-lookup"><span data-stu-id="1919e-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="1919e-105">Alterações na cena</span><span class="sxs-lookup"><span data-stu-id="1919e-105">Changes to the scene</span></span>

<span data-ttu-id="1919e-106">Para usar o kit de ferramentas, uma instância do script MixedRealityToolkit deve estar em sua cena.</span><span class="sxs-lookup"><span data-stu-id="1919e-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="1919e-107">Para adicionar um, use a opção de menu: Kit de Ferramentas de Realidade Misturada -> Adicionar à Cena e Configurar.</span><span class="sxs-lookup"><span data-stu-id="1919e-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="1919e-108">Essa instância é responsável por registrar, atualizar e destruir serviços.</span><span class="sxs-lookup"><span data-stu-id="1919e-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="1919e-109">Também é onde seu perfil de configuração é escolhido.</span><span class="sxs-lookup"><span data-stu-id="1919e-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="1919e-110">Além de adicionar o GameObject do MRTK à cena, a opção de menu também:</span><span class="sxs-lookup"><span data-stu-id="1919e-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="1919e-111">Adicione o MixedRealityPlayspace, que é usado por muitos outros componentes do MRTK para levar em conta as transformações de espaço local e do mundo.</span><span class="sxs-lookup"><span data-stu-id="1919e-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="1919e-112">Mova a câmera principal como um filho do MixedRealityPlayspace (e também adicione alguns scripts relacionados à entrada e foco à câmera principal, o que ajuda a apricar o UnityUI e a funcionalidade de entrada relacionada ao foco).</span><span class="sxs-lookup"><span data-stu-id="1919e-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="1919e-113">Runtime e objeto MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1919e-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="1919e-114">O MRTK tem vários serviços principais.</span><span class="sxs-lookup"><span data-stu-id="1919e-114">The MRTK has several core services.</span></span> <span data-ttu-id="1919e-115">Algumas coordenadas entre si; outros são independentes.</span><span class="sxs-lookup"><span data-stu-id="1919e-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="1919e-116">Todos compartilham o mesmo ciclo de vida – inicialização, registro, atualização e rebaixamento – e esse ciclo de vida se diferencia do ciclo de vida monoBehaviour do Unity.</span><span class="sxs-lookup"><span data-stu-id="1919e-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="1919e-117">Esta [postagem média](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explica algumas das informações e da motivação por trás dessa abordagem.</span><span class="sxs-lookup"><span data-stu-id="1919e-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="1919e-118">O MRTK tem um único objeto que gerencia a vida e o runtime de seus serviços.</span><span class="sxs-lookup"><span data-stu-id="1919e-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="1919e-119">Essa entidade garante que:</span><span class="sxs-lookup"><span data-stu-id="1919e-119">This entity ensures that:</span></span>

- <span data-ttu-id="1919e-120">quando o jogo é iniciado, a descoberta e a inicialização de serviços ocorrem em uma ordem pré-definida.</span><span class="sxs-lookup"><span data-stu-id="1919e-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="1919e-121">ele fornece um mecanismo para que os serviços se registrem (ou seja, "Eu dá suporte a esse serviço!") e para outros chamadores obterem uma conta desses serviços.</span><span class="sxs-lookup"><span data-stu-id="1919e-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="1919e-122">ele fornece as chamadas Update()/LateUpdate() e as encaminha para os vários serviços (ou seja, por meio de UpdateAllServices/LateUpdateAllServices).</span><span class="sxs-lookup"><span data-stu-id="1919e-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
