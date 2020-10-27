---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638606"
---
# <a name="all-platforms"></a>[<span data-ttu-id="ba7eb-101">Todas as plataformas</span><span class="sxs-lookup"><span data-stu-id="ba7eb-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="ba7eb-102">Os mesmos mapeamentos de ação e de eixo nas configurações do projeto de entrada do jogo podem ser usados em C++.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="ba7eb-103">Criar uma nova classe C++ com a classe File/New C++...</span><span class="sxs-lookup"><span data-stu-id="ba7eb-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Criando uma nova classe C++](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="ba7eb-105">Criar um peão</span><span class="sxs-lookup"><span data-stu-id="ba7eb-105">Create a pawn</span></span>

![Criando um peão](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="ba7eb-107">Na solução do Visual Studio do projeto, localize a nova classe peão e configure-a para entrada.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="ba7eb-108">Primeiro, no construtor, defina AutoPossessPlayer para o primeiro jogador para rotear a entrada para o peão.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="ba7eb-109">Em seguida, em SetupPlayerInputComponent, associe ações e eventos de eixo aos nomes de ação das configurações de entrada do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="ba7eb-110">Adicione as funções de retorno de chamada à classe:</span><span class="sxs-lookup"><span data-stu-id="ba7eb-110">Add the callback functions to the class:</span></span>

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* <span data-ttu-id="ba7eb-111">Atualize o cabeçalho do peão com as definições da função de retorno de chamada:</span><span class="sxs-lookup"><span data-stu-id="ba7eb-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="ba7eb-112">Compile do Visual Studio para iniciar o editor com o novo peão.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="ba7eb-113">Arraste e solte o peão do navegador de conteúdo para o jogo e o peão agora executará os retornos de chamada quando a entrada for pressionada.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="ba7eb-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="ba7eb-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="ba7eb-115">Ao usar eventos de eixo de Thumbstick, o nome do evento de eixo deve terminar em "_X" ou "_Y" correspondente à chave usada.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Usando eventos Thumbstick](../images/reverb-g2-img-09.png)

<span data-ttu-id="ba7eb-117">Por fim, registre as ações no jogo com SteamVR usando os botões **regenerar ação manifest** e **regenerar associações de controlador** nas configurações do projeto > entrada VR.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Registrando ações nas configurações do projeto](../images/reverb-g2-img-10.png)

