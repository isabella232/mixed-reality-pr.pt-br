---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638606"
---
# <a name="all-platforms"></a>[Todas as plataformas](#tab/all)

Os mesmos mapeamentos de ação e de eixo nas configurações do projeto de entrada do jogo podem ser usados em C++.

1. Criar uma nova classe C++ com a classe File/New C++...

![Criando uma nova classe C++](../images/reverb-g2-img-11.png)

2. Criar um peão

![Criando um peão](../images/reverb-g2-img-12.png)

3. Na solução do Visual Studio do projeto, localize a nova classe peão e configure-a para entrada.
* Primeiro, no construtor, defina AutoPossessPlayer para o primeiro jogador para rotear a entrada para o peão.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* Em seguida, em SetupPlayerInputComponent, associe ações e eventos de eixo aos nomes de ação das configurações de entrada do projeto.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Adicione as funções de retorno de chamada à classe:

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

* Atualize o cabeçalho do peão com as definições da função de retorno de chamada:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Compile do Visual Studio para iniciar o editor com o novo peão. Arraste e solte o peão do navegador de conteúdo para o jogo e o peão agora executará os retornos de chamada quando a entrada for pressionada.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Ao usar eventos de eixo de Thumbstick, o nome do evento de eixo deve terminar em "_X" ou "_Y" correspondente à chave usada.

![Usando eventos Thumbstick](../images/reverb-g2-img-09.png)

Por fim, registre as ações no jogo com SteamVR usando os botões **regenerar ação manifest** e **regenerar associações de controlador** nas configurações do projeto > entrada VR.

![Registrando ações nas configurações do projeto](../images/reverb-g2-img-10.png)

