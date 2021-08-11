---
title: Teclado, mouse e entrada do controlador no DirectX
description: explica como criar um aplicativo para Windows Mixed Reality que usa controladores de teclado, mouse e jogo.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, teclado, mouse, controlador de jogo, xbox controller, HoloLens, desktop, passo a passos, código de exemplo
ms.openlocfilehash: 2e83fa0a14a24eb98001c7dc88af062202a2ef9a5eee7cd53e9702dbe4eedc8e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192020"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Teclado, mouse e entrada do controlador no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](../native/openxr-getting-started.md)**.

teclados, mouses e controladores de jogos podem ser formas úteis de entrada para dispositivos Windows Mixed Reality. Bluetooth teclados e mouses têm suporte no HoloLens, para uso com a depuração do aplicativo ou como uma forma alternativa de entrada. o Windows Mixed Reality também dá suporte a headsets de imersão conectados a PCs – onde os mouses, teclados e controladores de jogos têm sido historicamente a norma.

para usar a entrada de teclado no HoloLens, emparelhe um Bluetooth teclado para seu dispositivo ou use a entrada virtual por meio do Portal do dispositivo Windows. para usar a entrada de teclado ao utilizar um Windows Mixed Reality headset de imersão, atribua o foco de entrada à realidade mista, colocando no dispositivo ou usando a combinação de teclado Windows chave + Y. tenha em mente que os aplicativos destinados a HoloLens devem fornecer funcionalidade sem esses dispositivos conectados.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o uso de C++/CX em vez de c++/WinRT compatível com C + +17, conforme usado no [modelo de projeto do C++ Holographic](../native/creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a um projeto/WinRT do C++, embora você precise converter o código.

## <a name="subscribe-for-corewindow-input-events"></a>Assinar eventos de entrada do CoreWindow

### <a name="keyboard-input"></a>Entrada por teclado

no modelo de aplicativo Windows Holographic, incluímos um manipulador de eventos para entrada de teclado, assim como qualquer outro aplicativo UWP. Seu aplicativo consome dados de entrada do teclado da mesma maneira no Windows Mixed Reality.

De AppView. cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Entrada de teclado virtual
para headsets de área de trabalho de imersão, você pode dar suporte a teclados virtuais renderizados por Windows sobre sua exibição de imersão implementando **CoreTextEditContext**. isso permite que Windows entenda o estado de suas próprias caixas de texto renderizadas pelo aplicativo, para que o teclado virtual possa contribuir corretamente para o texto lá.

Para obter mais informações sobre como implementar o suporte a CoreTextEditContext, consulte o [exemplo CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Entrada do mouse

Você também pode usar a entrada do mouse, novamente por meio dos manipuladores de eventos de entrada UWP CoreWindow. veja como modificar o modelo de aplicativo Windows Holographic para dar suporte a cliques do mouse da mesma maneira que os gestos pressionados. Depois de fazer essa modificação, um clique do mouse ao usar um dispositivo de headset de imersão reposicionará o cubo.

> [!NOTE]
> Os aplicativos UWP também podem obter dados XY brutos para o mouse usando a API [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) .

Comece declarando um novo manipulador OnPointerPressed em AppView. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Em AppView. cpp, adicione este código a SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Em seguida, coloque essa definição para OnPointerPressed na parte inferior do arquivo:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

O manipulador de eventos que acabamos de adicionar é uma passagem para a classe principal do modelo. Vamos modificar a classe principal para dar suporte a essa passagem. Adicione essa declaração de método público ao arquivo de cabeçalho:

```
// Handle mouse input.
       void OnPointerPressed();
```

Você também precisará dessa variável de membro privado:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Por fim, atualizaremos a classe principal com nova lógica para dar suporte a cliques do mouse. Comece adicionando este manipulador de eventos. Certifique-se de atualizar o nome da classe:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Agora, no método Update, substitua a lógica existente para obter uma pose de ponteiro com esta:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Recompile e reimplante. observe que o clique do mouse agora reposicionará o cubo em seu headset de imersão ou HoloLens com o mouse bluetooth anexado.

### <a name="game-controller-support"></a>Suporte ao controlador de jogos

os controladores de jogo podem ser uma maneira divertida e conveniente de permitir que o usuário controle uma experiência de Windows Mixed Reality imersiva.

 Adicione as seguintes declarações de membro privado à classe de cabeçalho para o arquivo principal:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Inicializar eventos do gamepad e todos os gamepads que estão anexados no momento, no construtor para sua classe principal:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Adicione esses manipuladores de eventos à classe principal. Certifique-se de atualizar o nome da classe:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Por fim, atualize a lógica de entrada para reconhecer as alterações no estado do controlador. Aqui, usamos a mesma variável m_pointerPressed discutida na seção acima para adicionar eventos de mouse. Adicione isso ao método Update, pouco antes de onde ele verifica o SpatialPointerPose:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Não se esqueça de cancelar o registro dos eventos ao limpar a classe principal:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Recompile e reimplante. Agora você pode anexar ou emparelhar um controlador de jogo e usá-lo para reposicionar o cubo de rotação.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Diretrizes importantes para entrada de teclado e mouse

há algumas diferenças importantes em como esse código pode ser usado no Microsoft HoloLens – que é um dispositivo que depende principalmente da entrada natural do usuário, em comparação com o que está disponível em um PC com Windows Mixed Reality habilitado.
* Você não pode contar com o teclado ou a entrada do mouse para estar presente. Toda a funcionalidade do seu aplicativo deve funcionar com olhar, gesto e entrada de fala.
* quando um teclado Bluetooth é anexado, pode ser útil habilitar a entrada de teclado para qualquer texto que seu aplicativo possa solicitar. Isso pode ser um excelente suplemento para ditado, por exemplo.
* Quando se trata de criar seu aplicativo, não confie (por exemplo) WASD e controles de aparência do mouse para seu jogo. HoloLens foi projetado para que o usuário percorra a sala. Nesse caso, o usuário controla a câmera diretamente. Uma interface para orientar a câmera em todo o espaço com os controles mover/procurar não fornecerá a mesma experiência.
* A entrada de teclado é uma maneira excelente de controlar seu aplicativo ou a depuração do mecanismo de jogos, especialmente porque o usuário não precisará usar o teclado. Conectar-se a ele é o mesmo que você está acostumado a, com APIs de evento CoreWindow. Nesse cenário, você pode optar por implementar uma maneira de configurar seu aplicativo para rotear eventos de teclado para um modo de "somente entrada de depuração" durante as sessões de depuração.
* Bluetooth controladores também funcionam.

## <a name="see-also"></a>Confira também
* [Acessórios de hardware](../../discover/hardware-accessories.md)