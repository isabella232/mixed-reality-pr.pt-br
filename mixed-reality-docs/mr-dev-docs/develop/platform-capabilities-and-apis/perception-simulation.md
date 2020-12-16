---
title: Simulação de percepção
description: Um guia para usar a biblioteca de simulação de percepção para automatizar a entrada simulada para aplicativos de imersão
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulação, teste
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530393"
---
# <a name="perception-simulation"></a><span data-ttu-id="c2e70-104">Simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c2e70-104">Perception simulation</span></span>

<span data-ttu-id="c2e70-105">Deseja criar um teste automatizado para seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="c2e70-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="c2e70-106">Você deseja que seus testes vão além dos testes de unidade de nível de componente e realmente exercitam seu aplicativo de ponta a ponta?</span><span class="sxs-lookup"><span data-stu-id="c2e70-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="c2e70-107">A simulação de percepção é o que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="c2e70-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="c2e70-108">A biblioteca de simulação de percepção envia dados de entrada humanos e mundiais para seu aplicativo para que você possa automatizar seus testes.</span><span class="sxs-lookup"><span data-stu-id="c2e70-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="c2e70-109">Por exemplo, você pode simular a entrada de uma aparência humana para uma posição específica e repetível e, em seguida, usar um controlador de gesto ou movimento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="c2e70-110">A simulação de percepção pode enviar uma entrada simulada como esta para um HoloLens físico, o emulador do HoloLens (primeira gen), o emulador do HoloLens 2 ou um PC com o portal de realidade misturada instalado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="c2e70-111">A simulação de percepção ignora os sensores ao vivo em um dispositivo de realidade misturada e envia a entrada simulada para aplicativos em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="c2e70-112">Os aplicativos recebem esses eventos de entrada por meio das mesmas APIs que sempre usam e não conseguem dizer a diferença entre a execução com sensores reais versus a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="c2e70-113">A simulação de percepção é a mesma tecnologia usada pelos emuladores do HoloLens para enviar a entrada simulada para a máquina virtual do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c2e70-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="c2e70-114">Para começar a usar a simulação em seu código, comece criando um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="c2e70-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="c2e70-115">A partir desse objeto, você pode emitir comandos para controlar as propriedades de um "humano" simulado, incluindo a posição da cabeça, a posição da mão e os gestos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="c2e70-116">Você também pode habilitar e manipular os controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="c2e70-117">Configurando um projeto do Visual Studio para simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c2e70-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="c2e70-118">[Instale o emulador do HoloLens](../install-the-tools.md) no seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="c2e70-119">O emulador inclui as bibliotecas que você usa para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="c2e70-120">Crie um novo projeto de desktop do Visual Studio C# (um projeto de console funciona muito bem para começar).</span><span class="sxs-lookup"><span data-stu-id="c2e70-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="c2e70-121">Adicione os seguintes binários ao seu projeto como referências (projeto->referência ao suplemento de >...). Você pode encontrá-los em% ProgramFiles (x86)% \ Microsoft XDE \\ (versão), como **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** para o emulador do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c2e70-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="c2e70-122">(Observação: embora os binários façam parte do emulador do HoloLens 2, eles também funcionam para a realidade mista do Windows na área de trabalho.) um.</span><span class="sxs-lookup"><span data-stu-id="c2e70-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="c2e70-123">Wrapper de C# gerenciado por PerceptionSimulationManager.Interop.dll para simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="c2e70-124">b.</span><span class="sxs-lookup"><span data-stu-id="c2e70-124">b.</span></span> <span data-ttu-id="c2e70-125">PerceptionSimulationRest.dll-Library para configurar um canal de comunicação de soquete da Web para o HoloLens ou o emulador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="c2e70-126">c.</span><span class="sxs-lookup"><span data-stu-id="c2e70-126">c.</span></span> <span data-ttu-id="c2e70-127">SimulationStream.Interop.dll-tipos compartilhados para simulação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="c2e70-128">Adicione o PerceptionSimulationManager.dll binário de implementação ao seu projeto a.</span><span class="sxs-lookup"><span data-stu-id="c2e70-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="c2e70-129">Primeiro, adicione-o como um binário ao projeto (projeto->adicionar >item existente...). Salve-o como um link para que ele não o copie para a pasta de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="c2e70-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="c2e70-130">![Adicione PerceptionSimulationManager.dll ao projeto como um link ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="c2e70-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="c2e70-131">Em seguida, verifique se ele é copiado para a pasta de saída na compilação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="c2e70-132">Isso está na folha de propriedades do binário.</span><span class="sxs-lookup"><span data-stu-id="c2e70-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="c2e70-133">![Marque PerceptionSimulationManager.dll para copiar para o diretório de saída](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="c2e70-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="c2e70-134">Defina sua plataforma de solução ativa como x64.</span><span class="sxs-lookup"><span data-stu-id="c2e70-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="c2e70-135">(Use o Configuration Manager para criar uma entrada de plataforma para x64 se ainda não existir uma.)</span><span class="sxs-lookup"><span data-stu-id="c2e70-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="c2e70-136">Criando um objeto do Gerenciador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="c2e70-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="c2e70-137">Para controlar a simulação, você emitirá atualizações para objetos recuperados de um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="c2e70-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="c2e70-138">A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou emulador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="c2e70-139">Você pode obter o endereço IP do emulador clicando no botão portal do dispositivo na barra de [ferramentas](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="c2e70-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="c2e70-140">![Abrir o ícone do portal do dispositivo ](images/emulator-deviceportal.png) **abra o portal do dispositivo**: Abra o portal do dispositivo do Windows para o sistema operacional do HoloLens no emulador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="c2e70-141">Para a realidade mista do Windows, isso pode ser recuperado no aplicativo configurações em "atualizar & segurança" e, em seguida, "para desenvolvedores" na seção "conectar usando:" em "habilitar o portal do dispositivo".</span><span class="sxs-lookup"><span data-stu-id="c2e70-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="c2e70-142">Lembre-se de anotar o endereço IP e a porta.</span><span class="sxs-lookup"><span data-stu-id="c2e70-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="c2e70-143">Primeiro, você chamará RestSimulationStreamSink. Create para obter um objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="c2e70-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="c2e70-144">Esse é o dispositivo ou emulador de destino que você controlará em uma conexão http.</span><span class="sxs-lookup"><span data-stu-id="c2e70-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="c2e70-145">Seus comandos serão passados e manipulados pelo portal do [dispositivo Windows](using-the-windows-device-portal.md) em execução no dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="c2e70-146">Os quatro parâmetros necessários para criar um objeto são:</span><span class="sxs-lookup"><span data-stu-id="c2e70-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="c2e70-147">URI Uri-endereço IP do dispositivo de destino (por exemplo, " https://123.123.123.123 " ou " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="c2e70-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="c2e70-148">System .net. NetworkCredential credenciais-nome de usuário/senha para se conectar ao [portal de dispositivo do Windows](using-the-windows-device-portal.md) no dispositivo ou emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="c2e70-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="c2e70-149">Se você estiver se conectando ao emulador por meio de seu endereço local (por exemplo,*168...* \*) no mesmo PC, todas as credenciais serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="c2e70-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="c2e70-150">bool normal-true para prioridade normal, false para baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="c2e70-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="c2e70-151">Em geral, você desejará definir isso como *verdadeiro* para cenários de teste, o que permite que seu teste assuma o controle.</span><span class="sxs-lookup"><span data-stu-id="c2e70-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="c2e70-152">O emulador e a simulação de realidade mista do Windows usam conexões de baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="c2e70-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="c2e70-153">Se o teste também usar uma conexão de baixa prioridade, a conexão estabelecida mais recentemente estará no controle.</span><span class="sxs-lookup"><span data-stu-id="c2e70-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="c2e70-154">System. Threading. CancellationToken token-token para cancelar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="c2e70-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="c2e70-155">Em segundo lugar, você criará o IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="c2e70-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="c2e70-156">Esse é o objeto que você usa para controlar a simulação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="c2e70-157">Isso também deve ser feito em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c2e70-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="c2e70-158">Controlar o humano simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-158">Control the simulated Human</span></span>

<span data-ttu-id="c2e70-159">Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="c2e70-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="c2e70-160">Para controlar o humano simulado, execute operações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="c2e70-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="c2e70-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c2e70-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="c2e70-162">Aplicativo de console C# de exemplo básico</span><span class="sxs-lookup"><span data-stu-id="c2e70-162">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="c2e70-163">Aplicativo de console C# de exemplo estendido</span><span class="sxs-lookup"><span data-stu-id="c2e70-163">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="c2e70-164">Observação em controladores 6-DOF</span><span class="sxs-lookup"><span data-stu-id="c2e70-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="c2e70-165">Antes de chamar qualquer propriedade em métodos em um controlador de 6 DOF simulado, você deve ativar o controlador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="c2e70-166">Não fazer isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="c2e70-167">A partir da atualização do Windows 10 de maio de 2019, os controladores 6 DOF simulados podem ser instalados e ativados definindo a propriedade status no objeto ISimulatedSixDofController como SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="c2e70-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="c2e70-168">Na atualização do Windows 10 de outubro de 2018 e anterior, você deve instalar separadamente um controlador de 6 DOF simulado primeiro chamando a ferramenta PerceptionSimulationDevice localizada na pasta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="c2e70-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="c2e70-169">O uso dessa ferramenta é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2e70-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="c2e70-170">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="c2e70-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="c2e70-171">As ações com suporte são:</span><span class="sxs-lookup"><span data-stu-id="c2e70-171">Supported actions are:</span></span>
* <span data-ttu-id="c2e70-172">i = instalar</span><span class="sxs-lookup"><span data-stu-id="c2e70-172">i = install</span></span>
* <span data-ttu-id="c2e70-173">q = consulta</span><span class="sxs-lookup"><span data-stu-id="c2e70-173">q = query</span></span>
* <span data-ttu-id="c2e70-174">r = remover</span><span class="sxs-lookup"><span data-stu-id="c2e70-174">r = remove</span></span>

<span data-ttu-id="c2e70-175">As instâncias com suporte são:</span><span class="sxs-lookup"><span data-stu-id="c2e70-175">Supported instances are:</span></span>
* <span data-ttu-id="c2e70-176">1 = o controlador de 6 DOF à esquerda</span><span class="sxs-lookup"><span data-stu-id="c2e70-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="c2e70-177">2 = o controlador de 6 DOF à direita</span><span class="sxs-lookup"><span data-stu-id="c2e70-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="c2e70-178">O código de saída do processo indicará êxito (um valor de retorno zero) ou falha (um valor de retorno diferente de zero).</span><span class="sxs-lookup"><span data-stu-id="c2e70-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="c2e70-179">Ao usar a ação ' q ' para consultar se um controlador está instalado, o valor de retorno será zero (0) se o controlador ainda não estiver instalado ou um (1) se o controlador estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="c2e70-180">Ao remover um controlador na atualização do Windows 10 de outubro de 2018 ou anterior, defina seu status como off por meio da API primeiro e, em seguida, chame a ferramenta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="c2e70-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="c2e70-181">Essa ferramenta deve ser executada como administrador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="c2e70-182">Referência de API</span><span class="sxs-lookup"><span data-stu-id="c2e70-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="c2e70-183">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="c2e70-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="c2e70-184">Descreve um tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="c2e70-185">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="c2e70-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="c2e70-186">Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="c2e70-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="c2e70-187">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="c2e70-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="c2e70-188">Descreve um modo de controlador de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="c2e70-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="c2e70-189">**Microsoft. PerceptionSimulation. HeadTrackerMode. Default**</span><span class="sxs-lookup"><span data-stu-id="c2e70-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="c2e70-190">Rastreamento de cabeçalho padrão.</span><span class="sxs-lookup"><span data-stu-id="c2e70-190">Default Head Tracking.</span></span> <span data-ttu-id="c2e70-191">Isso significa que o sistema pode selecionar o melhor modo de controle de cabeçalho com base nas condições de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="c2e70-192">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="c2e70-193">Controle de cabeçalho somente orientação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="c2e70-194">Isso significa que a posição controlada pode não ser confiável, e algumas funcionalidades dependentes da posição de cabeçalho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c2e70-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="c2e70-195">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="c2e70-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="c2e70-196">Acompanhamento da cabeça posicional.</span><span class="sxs-lookup"><span data-stu-id="c2e70-196">Positional Head Tracking.</span></span> <span data-ttu-id="c2e70-197">Isso significa que a posição e a orientação da cabeça controlada são confiáveis</span><span class="sxs-lookup"><span data-stu-id="c2e70-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="c2e70-198">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="c2e70-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="c2e70-199">Descreve um gesto simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-199">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="c2e70-200">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="c2e70-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="c2e70-201">Um valor de sentinela usado para indicar que não há gestos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="c2e70-202">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="c2e70-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="c2e70-203">Um gesto de dedo pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-203">A finger pressed gesture.</span></span>

<span data-ttu-id="c2e70-204">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="c2e70-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="c2e70-205">Um gesto de liberação de dedo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-205">A finger released gesture.</span></span>

<span data-ttu-id="c2e70-206">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="c2e70-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="c2e70-207">O gesto de residência/sistema.</span><span class="sxs-lookup"><span data-stu-id="c2e70-207">The home/system gesture.</span></span>

<span data-ttu-id="c2e70-208">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="c2e70-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="c2e70-209">O gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="c2e70-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="c2e70-210">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="c2e70-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="c2e70-211">Os Estados possíveis de um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="c2e70-212">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**</span><span class="sxs-lookup"><span data-stu-id="c2e70-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="c2e70-213">O controlador de 6 DOF está desligado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="c2e70-214">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. active**</span><span class="sxs-lookup"><span data-stu-id="c2e70-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="c2e70-215">O controlador de 6 DOF é ativado e acompanhado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="c2e70-216">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="c2e70-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="c2e70-217">O controlador de 6 DOF está ativado, mas não pode ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="c2e70-218">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="c2e70-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="c2e70-219">Os botões com suporte em um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-219">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="c2e70-220">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="c2e70-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="c2e70-221">Um valor de sentinela usado para indicar nenhum botão.</span><span class="sxs-lookup"><span data-stu-id="c2e70-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="c2e70-222">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="c2e70-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="c2e70-223">O botão página inicial é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-223">The Home button is pressed.</span></span>

<span data-ttu-id="c2e70-224">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="c2e70-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="c2e70-225">O botão de menu é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-225">The Menu button is pressed.</span></span>

<span data-ttu-id="c2e70-226">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Segure**</span><span class="sxs-lookup"><span data-stu-id="c2e70-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="c2e70-227">O botão de alça é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-227">The Grip button is pressed.</span></span>

<span data-ttu-id="c2e70-228">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="c2e70-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="c2e70-229">O TouchPad é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="c2e70-230">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="c2e70-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="c2e70-231">O botão Selecionar é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-231">The Select button is pressed.</span></span>

<span data-ttu-id="c2e70-232">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="c2e70-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="c2e70-233">O TouchPad é tocado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-233">The TouchPad is touched.</span></span>

<span data-ttu-id="c2e70-234">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="c2e70-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="c2e70-235">O Thumbstick é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="c2e70-236">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="c2e70-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="c2e70-237">O botão máximo válido.</span><span class="sxs-lookup"><span data-stu-id="c2e70-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="c2e70-238">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="c2e70-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="c2e70-239">O estado de calibragem dos olhos simulados</span><span class="sxs-lookup"><span data-stu-id="c2e70-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="c2e70-240">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. indisponível**</span><span class="sxs-lookup"><span data-stu-id="c2e70-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="c2e70-241">A calibragem de olhos não está disponível.</span><span class="sxs-lookup"><span data-stu-id="c2e70-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="c2e70-242">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="c2e70-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="c2e70-243">Os olhos foram calibrados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="c2e70-244">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c2e70-244">This is the default value.</span></span>

<span data-ttu-id="c2e70-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.ConfigUring**</span><span class="sxs-lookup"><span data-stu-id="c2e70-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="c2e70-246">Os olhos estão sendo calibrados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="c2e70-247">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="c2e70-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="c2e70-248">Os olhos precisam ser calibrados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="c2e70-249">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="c2e70-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="c2e70-250">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="c2e70-251">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. indisponível**</span><span class="sxs-lookup"><span data-stu-id="c2e70-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="c2e70-252">A junção não é acompanhada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-252">The joint isn't tracked.</span></span>

<span data-ttu-id="c2e70-253">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="c2e70-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="c2e70-254">A posição conjunta é inferida.</span><span class="sxs-lookup"><span data-stu-id="c2e70-254">The joint position is inferred.</span></span>

<span data-ttu-id="c2e70-255">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="c2e70-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="c2e70-256">A junção é totalmente controlada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="c2e70-257">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="c2e70-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="c2e70-258">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-258">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="c2e70-259">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="c2e70-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="c2e70-260">As junções de dedo da mão são configuradas para refletir uma pose fechada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="c2e70-261">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="c2e70-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="c2e70-262">As junções de dedo da mão são configuradas para refletir uma pose aberta.</span><span class="sxs-lookup"><span data-stu-id="c2e70-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="c2e70-263">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="c2e70-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="c2e70-264">As junções de dedo da mão são configuradas para refletir uma pose de apontador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="c2e70-265">**Microsoft. PerceptionSimulation. SimulatedHandPose. pinçar**</span><span class="sxs-lookup"><span data-stu-id="c2e70-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="c2e70-266">As junções de dedo da mão são configuradas para refletir uma pose de pinçagem.</span><span class="sxs-lookup"><span data-stu-id="c2e70-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="c2e70-267">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="c2e70-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="c2e70-268">O valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="c2e70-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="c2e70-269">Microsoft. PerceptionSimulation. Playbackstate</span><span class="sxs-lookup"><span data-stu-id="c2e70-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="c2e70-270">Descreve o estado de uma reprodução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="c2e70-271">**Microsoft. PerceptionSimulation. Playbackstate. parado**</span><span class="sxs-lookup"><span data-stu-id="c2e70-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="c2e70-272">A gravação está atualmente parada e pronta para reprodução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="c2e70-273">**Microsoft. PerceptionSimulation. Playbackstate. reproduzindo**</span><span class="sxs-lookup"><span data-stu-id="c2e70-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="c2e70-274">A gravação está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-274">The recording is currently playing.</span></span>

<span data-ttu-id="c2e70-275">**Microsoft. PerceptionSimulation. Playbackstate. Paused**</span><span class="sxs-lookup"><span data-stu-id="c2e70-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="c2e70-276">A gravação está em pausa no momento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-276">The recording is currently paused.</span></span>

<span data-ttu-id="c2e70-277">**Microsoft. PerceptionSimulation. Playbackstate. end**</span><span class="sxs-lookup"><span data-stu-id="c2e70-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="c2e70-278">A gravação atingiu o final.</span><span class="sxs-lookup"><span data-stu-id="c2e70-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="c2e70-279">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="c2e70-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="c2e70-280">Descreve um vetor de três componentes, que pode descrever um ponto ou um vetor no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="c2e70-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="c2e70-281">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="c2e70-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="c2e70-282">O componente X do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-282">The X component of the vector.</span></span>

<span data-ttu-id="c2e70-283">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="c2e70-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="c2e70-284">O componente Y do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-284">The Y component of the vector.</span></span>

<span data-ttu-id="c2e70-285">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="c2e70-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="c2e70-286">O componente Z do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-286">The Z component of the vector.</span></span>

<span data-ttu-id="c2e70-287">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="c2e70-288">Construa um novo Vector3.</span><span class="sxs-lookup"><span data-stu-id="c2e70-288">Construct a new Vector3.</span></span>

<span data-ttu-id="c2e70-289">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-289">Parameters</span></span>
* <span data-ttu-id="c2e70-290">x – o componente x do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="c2e70-291">y-o componente y do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="c2e70-292">z-o componente z do vetor.</span><span class="sxs-lookup"><span data-stu-id="c2e70-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="c2e70-293">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="c2e70-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="c2e70-294">Descreve uma rotação de três componentes.</span><span class="sxs-lookup"><span data-stu-id="c2e70-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="c2e70-295">**Microsoft. PerceptionSimulation. Rotation3. pitch**</span><span class="sxs-lookup"><span data-stu-id="c2e70-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="c2e70-296">O componente de pitch da rotação, em volta do eixo X.</span><span class="sxs-lookup"><span data-stu-id="c2e70-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="c2e70-297">**Microsoft. PerceptionSimulation. Rotation3. Guinad**</span><span class="sxs-lookup"><span data-stu-id="c2e70-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="c2e70-298">O componente de guinada da rotação, logo em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="c2e70-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="c2e70-299">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="c2e70-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="c2e70-300">O componente de roll da rotação, logo em volta do eixo Z.</span><span class="sxs-lookup"><span data-stu-id="c2e70-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="c2e70-301">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="c2e70-302">Construa um novo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="c2e70-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="c2e70-303">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-303">Parameters</span></span>
* <span data-ttu-id="c2e70-304">Pitch-o componente de pitch da rotação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="c2e70-305">guinada-o componente de guinada da rotação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="c2e70-306">roll-o componente de rolagem da rotação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="c2e70-307">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="c2e70-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="c2e70-308">Descreve a configuração de uma junção em uma mão simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="c2e70-309">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="c2e70-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="c2e70-310">A posição da junção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-310">The position of the joint.</span></span>

<span data-ttu-id="c2e70-311">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="c2e70-312">A rotação da junção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-312">The rotation of the joint.</span></span>

<span data-ttu-id="c2e70-313">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="c2e70-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="c2e70-314">A precisão de rastreamento da junção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="c2e70-315">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="c2e70-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="c2e70-316">Descreve um frustum de exibição, como normalmente usado por uma câmera.</span><span class="sxs-lookup"><span data-stu-id="c2e70-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="c2e70-317">**Microsoft. PerceptionSimulation. frustum. near**</span><span class="sxs-lookup"><span data-stu-id="c2e70-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="c2e70-318">A distância mínima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="c2e70-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="c2e70-319">**Microsoft. PerceptionSimulation. frustum. far**</span><span class="sxs-lookup"><span data-stu-id="c2e70-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="c2e70-320">A distância máxima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="c2e70-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="c2e70-321">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="c2e70-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="c2e70-322">O campo horizontal de exibição do frustum, em radianos (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="c2e70-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="c2e70-323">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="c2e70-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="c2e70-324">A proporção do campo horizontal de exibição para o campo vertical da exibição.</span><span class="sxs-lookup"><span data-stu-id="c2e70-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="c2e70-325">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="c2e70-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="c2e70-326">Descreve a configuração da exibição do headset simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-326">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="c2e70-327">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="c2e70-328">A transformação do centro da cabeça à esquerda para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="c2e70-329">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="c2e70-330">A rotação do olho à esquerda para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="c2e70-331">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="c2e70-332">A transformação do centro da cabeça para o olho certo para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="c2e70-333">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="c2e70-334">A rotação do olho certo para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="c2e70-335">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="c2e70-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="c2e70-336">O valor de IPD relatado pelo sistema para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="c2e70-337">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="c2e70-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="c2e70-338">Se os valores fornecidos para transformações de olho esquerdo e direito devem ser considerados válidos e aplicados ao sistema em execução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="c2e70-339">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="c2e70-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="c2e70-340">Se o valor fornecido para o IPD deve ser considerado válido e aplicado ao sistema em execução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="c2e70-341">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="c2e70-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="c2e70-342">Raiz para gerar os pacotes usados para controlar um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="c2e70-343">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="c2e70-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="c2e70-344">Recupere o objeto de dispositivo simulado que interpreta o humano simulado e o mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="c2e70-345">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="c2e70-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="c2e70-346">Recupere o objeto que controla o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="c2e70-347">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="c2e70-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="c2e70-348">Redefine a simulação para seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="c2e70-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="c2e70-349">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="c2e70-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="c2e70-350">Interface que descreve o dispositivo, que interpreta o mundo simulado e o humano simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="c2e70-351">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="c2e70-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="c2e70-352">Recupere o controlador de cabeçalho do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="c2e70-353">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="c2e70-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="c2e70-354">Recupere o rastreador de mão do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="c2e70-355">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="c2e70-356">Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="c2e70-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="c2e70-357">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-357">Parameters</span></span>
* <span data-ttu-id="c2e70-358">tipo – o novo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="c2e70-359">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="c2e70-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="c2e70-360">Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedDevice para ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="c2e70-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="c2e70-361">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="c2e70-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="c2e70-362">Recupere ou defina se o humano simulado está ou não ativamente desativando o headset.</span><span class="sxs-lookup"><span data-stu-id="c2e70-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="c2e70-363">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c2e70-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="c2e70-364">Recupere ou defina as propriedades da exibição simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="c2e70-365">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="c2e70-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="c2e70-366">Interface que descreve a parte do dispositivo simulado que controla o início do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="c2e70-367">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="c2e70-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="c2e70-368">Recupera e define o modo de controlador de cabeçalho atual.</span><span class="sxs-lookup"><span data-stu-id="c2e70-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="c2e70-369">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="c2e70-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="c2e70-370">Interface que descreve a parte do dispositivo simulado que controla as mãos do humano simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="c2e70-371">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="c2e70-372">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="c2e70-373">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="c2e70-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="c2e70-374">Recupere e defina a posição do controlador de mão simulado em relação ao centro do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c2e70-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="c2e70-375">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. pitch**</span><span class="sxs-lookup"><span data-stu-id="c2e70-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="c2e70-376">Recupere e defina o timbre inferior do controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="c2e70-377">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="c2e70-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="c2e70-378">Recupere e defina se a frustum do controlador de mão simulado é ignorada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="c2e70-379">Quando ignorado, ambas as mãos estão sempre visíveis.</span><span class="sxs-lookup"><span data-stu-id="c2e70-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="c2e70-380">Quando não ignoradas (as mãos padrão) ficam visíveis apenas quando estão dentro do frustum do rastreador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="c2e70-381">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="c2e70-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="c2e70-382">Recupere e defina as propriedades frustum usadas para determinar se as mãos estão visíveis para o controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="c2e70-383">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="c2e70-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="c2e70-384">Interface de nível superior para controlar o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-384">Top-level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="c2e70-385">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="c2e70-386">Recupere e defina a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="c2e70-387">A posição corresponde a um ponto no centro dos pés humanos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="c2e70-388">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="c2e70-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="c2e70-389">Recupere e defina a direção das faces humanas simuladas do mundo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="c2e70-390">0 radianos está voltado para baixo no eixo Z negativo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="c2e70-391">Radianos positivos giram no sentido horário sobre o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="c2e70-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="c2e70-392">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="c2e70-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="c2e70-393">Recupere e defina a altura do humano simulado, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="c2e70-394">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="c2e70-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="c2e70-395">Recupere o lado esquerdo do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="c2e70-396">**Microsoft. PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="c2e70-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="c2e70-397">Recupere o lado direito do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="c2e70-398">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="c2e70-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="c2e70-399">Recupere o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="c2e70-400">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="c2e70-401">Mova o humano simulado relativo à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="c2e70-402">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-402">Parameters</span></span>
* <span data-ttu-id="c2e70-403">translação-a tradução a ser movida, relativa à posição atual.</span><span class="sxs-lookup"><span data-stu-id="c2e70-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="c2e70-404">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="c2e70-405">Girar o humano simulado em relação à sua direção atual, no sentido horário, sobre o eixo Y</span><span class="sxs-lookup"><span data-stu-id="c2e70-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="c2e70-406">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-406">Parameters</span></span>
* <span data-ttu-id="c2e70-407">radianos-o valor a ser girado em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="c2e70-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="c2e70-408">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="c2e70-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="c2e70-409">Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedHuman para ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="c2e70-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="c2e70-410">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="c2e70-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="c2e70-411">Recupere o controlador esquerdo 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="c2e70-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="c2e70-412">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="c2e70-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="c2e70-413">Recupere o controlador de 6 DOF à direita.</span><span class="sxs-lookup"><span data-stu-id="c2e70-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="c2e70-414">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="c2e70-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="c2e70-415">Interface que descreve uma mão do humano simulado</span><span class="sxs-lookup"><span data-stu-id="c2e70-415">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="c2e70-416">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="c2e70-417">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="c2e70-418">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="c2e70-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="c2e70-419">Recupere e defina a posição da mão simulada em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="c2e70-420">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="c2e70-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="c2e70-421">Recuperar e definir se a mão está ativada no momento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="c2e70-422">**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="c2e70-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="c2e70-423">Recupere se a mão está visível no momento para o SimulatedDevice (ou seja, se está em uma posição a ser detectada pelo HandTracker).</span><span class="sxs-lookup"><span data-stu-id="c2e70-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="c2e70-424">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="c2e70-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="c2e70-425">Mova a mão de modo que fique visível para o SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="c2e70-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="c2e70-426">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="c2e70-427">Mova a posição da mão simulada em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="c2e70-428">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-428">Parameters</span></span>
* <span data-ttu-id="c2e70-429">translation-o valor para converter a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="c2e70-430">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="c2e70-431">Execute um gesto usando a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="c2e70-432">Ele só será detectado pelo sistema se a mão estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="c2e70-433">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-433">Parameters</span></span>
* <span data-ttu-id="c2e70-434">gesto-o gesto a ser executado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="c2e70-435">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="c2e70-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="c2e70-436">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand em ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="c2e70-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="c2e70-437">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="c2e70-438">Recupere ou defina a rotação da mão simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="c2e70-439">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="c2e70-440">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="c2e70-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="c2e70-441">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand para ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="c2e70-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="c2e70-442">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c2e70-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="c2e70-443">Obter a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="c2e70-444">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c2e70-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="c2e70-445">Defina a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="c2e70-446">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="c2e70-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="c2e70-447">Defina a mão como uma pose conhecida com um sinalizador opcional para animar.</span><span class="sxs-lookup"><span data-stu-id="c2e70-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="c2e70-448">Observação: a animação não resultará em junções imediatamente refletindo suas configurações de conjuntos finais.</span><span class="sxs-lookup"><span data-stu-id="c2e70-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="c2e70-449">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="c2e70-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="c2e70-450">Interface que descreve o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="c2e70-451">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="c2e70-452">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="c2e70-453">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="c2e70-454">Recupere a rotação da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="c2e70-455">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="c2e70-456">**Microsoft. PerceptionSimulation. ISimulatedHead. diâmetro**</span><span class="sxs-lookup"><span data-stu-id="c2e70-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="c2e70-457">Recupere o diâmetro da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="c2e70-458">Esse valor é usado para determinar o centro da cabeça (ponto de rotação).</span><span class="sxs-lookup"><span data-stu-id="c2e70-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="c2e70-459">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="c2e70-460">Girar a cabeça simulada em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="c2e70-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="c2e70-461">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="c2e70-462">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-462">Parameters</span></span>
* <span data-ttu-id="c2e70-463">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="c2e70-464">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="c2e70-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="c2e70-465">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHead para ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="c2e70-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="c2e70-466">**Microsoft. PerceptionSimulation. ISimulatedHead2. eyess**</span><span class="sxs-lookup"><span data-stu-id="c2e70-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="c2e70-467">Recupere os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="c2e70-468">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="c2e70-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="c2e70-469">Interface que descreve um controlador de 6 DOF associado ao humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="c2e70-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="c2e70-471">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="c2e70-472">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="c2e70-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="c2e70-473">Recupere ou defina o estado atual do controlador.</span><span class="sxs-lookup"><span data-stu-id="c2e70-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="c2e70-474">O status do controlador deve ser definido com um valor diferente de desativado antes que as chamadas para mover, girar ou pressionar botões tenham sucesso.</span><span class="sxs-lookup"><span data-stu-id="c2e70-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="c2e70-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="c2e70-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="c2e70-476">Recupere ou defina a posição do controlador simulado em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="c2e70-477">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="c2e70-478">Recupere ou defina a orientação do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="c2e70-479">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="c2e70-480">Mova a posição do controlador simulado em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="c2e70-481">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-481">Parameters</span></span>
* <span data-ttu-id="c2e70-482">translation-o valor para converter o controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="c2e70-483">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="c2e70-484">Pressione um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="c2e70-485">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="c2e70-486">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-486">Parameters</span></span>
* <span data-ttu-id="c2e70-487">botão-o botão para pressionar.</span><span class="sxs-lookup"><span data-stu-id="c2e70-487">button - The button to press.</span></span>

<span data-ttu-id="c2e70-488">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="c2e70-489">Libere um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="c2e70-490">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="c2e70-491">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-491">Parameters</span></span>
* <span data-ttu-id="c2e70-492">botão-o botão a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-492">button - The button to release.</span></span>

<span data-ttu-id="c2e70-493">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="c2e70-494">Obtenha a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="c2e70-495">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-495">Parameters</span></span>
* <span data-ttu-id="c2e70-496">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="c2e70-497">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="c2e70-498">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="c2e70-499">Defina a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="c2e70-500">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-500">Parameters</span></span>
* <span data-ttu-id="c2e70-501">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="c2e70-502">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="c2e70-503">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="c2e70-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="c2e70-504">Propriedades e métodos adicionais estão disponíveis por meio da conversão de um ISimulatedSixDofController para ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="c2e70-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="c2e70-505">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="c2e70-506">Obtém a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="c2e70-507">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-507">Parameters</span></span>
* <span data-ttu-id="c2e70-508">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="c2e70-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="c2e70-509">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="c2e70-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="c2e70-510">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="c2e70-511">Defina a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="c2e70-512">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-512">Parameters</span></span>
* <span data-ttu-id="c2e70-513">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="c2e70-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="c2e70-514">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="c2e70-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="c2e70-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="c2e70-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="c2e70-516">Recupere ou defina o nível de bateria do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="c2e70-517">O valor deve ser maior que 0,0 e menor ou igual a 100,0.</span><span class="sxs-lookup"><span data-stu-id="c2e70-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="c2e70-518">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="c2e70-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="c2e70-519">Interface que descreve os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="c2e70-520">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="c2e70-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="c2e70-521">Recupere a rotação dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="c2e70-522">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="c2e70-523">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="c2e70-524">Gire os olhos simulados em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="c2e70-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="c2e70-525">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="c2e70-526">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-526">Parameters</span></span>
* <span data-ttu-id="c2e70-527">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="c2e70-528">**Microsoft. PerceptionSimulation. ISimulatedEyes. calibrable**</span><span class="sxs-lookup"><span data-stu-id="c2e70-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="c2e70-529">Recupera ou define o estado de calibragem dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="c2e70-530">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="c2e70-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="c2e70-531">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="c2e70-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="c2e70-532">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="c2e70-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="c2e70-533">Interface para interagir com uma única gravação carregada para reprodução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-533">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="c2e70-534">**Microsoft. PerceptionSimulation. ISimulationRecording. datatipos**</span><span class="sxs-lookup"><span data-stu-id="c2e70-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="c2e70-535">Recupera a lista de tipos de dados na gravação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="c2e70-536">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="c2e70-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="c2e70-537">Recupera o estado atual da gravação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="c2e70-538">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="c2e70-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="c2e70-539">Inicie a reprodução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-539">Start the playback.</span></span> <span data-ttu-id="c2e70-540">Se a gravação for pausada, a reprodução será retomada do local em pausa; Se for interrompido, a reprodução será iniciada no início.</span><span class="sxs-lookup"><span data-stu-id="c2e70-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="c2e70-541">Se já estiver em execução, essa chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="c2e70-542">**Microsoft. PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="c2e70-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="c2e70-543">Pausa a reprodução em seu local atual.</span><span class="sxs-lookup"><span data-stu-id="c2e70-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="c2e70-544">Se a gravação for interrompida, a chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="c2e70-545">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="c2e70-546">Procura a gravação no tempo especificado (em intervalos de 100 a nanossegundos desde o início) e pausa nesse local.</span><span class="sxs-lookup"><span data-stu-id="c2e70-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="c2e70-547">Se o tempo estiver além do fim da gravação, ele será pausado no último quadro.</span><span class="sxs-lookup"><span data-stu-id="c2e70-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="c2e70-548">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-548">Parameters</span></span>
* <span data-ttu-id="c2e70-549">tiques-o tempo para o qual buscar.</span><span class="sxs-lookup"><span data-stu-id="c2e70-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="c2e70-550">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="c2e70-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="c2e70-551">Interrompe a reprodução e redefine a posição para o início.</span><span class="sxs-lookup"><span data-stu-id="c2e70-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="c2e70-552">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="c2e70-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="c2e70-553">Interface para receber alterações de estado durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="c2e70-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="c2e70-554">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. reproduzstate)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="c2e70-555">Chamado quando o estado de reprodução de um ISimulationRecording é alterado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="c2e70-556">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-556">Parameters</span></span>
* <span data-ttu-id="c2e70-557">newState – o novo estado da gravação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="c2e70-558">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="c2e70-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="c2e70-559">Objeto raiz para criar objetos de simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="c2e70-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="c2e70-560">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="c2e70-561">Crie um objeto para gerar pacotes simulados e fornecê-los ao coletor fornecido.</span><span class="sxs-lookup"><span data-stu-id="c2e70-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="c2e70-562">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-562">Parameters</span></span>
* <span data-ttu-id="c2e70-563">coletor-o coletor que receberá todos os pacotes gerados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="c2e70-564">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2e70-564">Return value</span></span>

<span data-ttu-id="c2e70-565">O gerente criado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-565">The created Manager.</span></span>

<span data-ttu-id="c2e70-566">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="c2e70-567">Crie um coletor, que armazena todos os pacotes recebidos em um arquivo no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="c2e70-568">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-568">Parameters</span></span>
* <span data-ttu-id="c2e70-569">caminho-o caminho do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-569">path - The path of the file to create.</span></span>

<span data-ttu-id="c2e70-570">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2e70-570">Return value</span></span>

<span data-ttu-id="c2e70-571">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-571">The created sink.</span></span>

<span data-ttu-id="c2e70-572">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="c2e70-573">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="c2e70-574">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-574">Parameters</span></span>
* <span data-ttu-id="c2e70-575">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="c2e70-576">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="c2e70-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="c2e70-577">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2e70-577">Return value</span></span>

<span data-ttu-id="c2e70-578">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-578">The loaded recording.</span></span>

<span data-ttu-id="c2e70-579">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="c2e70-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="c2e70-580">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="c2e70-581">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-581">Parameters</span></span>
* <span data-ttu-id="c2e70-582">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="c2e70-583">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="c2e70-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="c2e70-584">retorno de chamada-um retorno de chamada, que recebe atualizações que retratam o status da gravação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="c2e70-585">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2e70-585">Return value</span></span>

<span data-ttu-id="c2e70-586">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="c2e70-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="c2e70-587">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="c2e70-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="c2e70-588">Descreve os diferentes tipos de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-588">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="c2e70-589">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="c2e70-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="c2e70-590">Um valor de sentinela usado para indicar nenhum tipo de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="c2e70-591">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="c2e70-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="c2e70-592">Fluxo de dados para a posição e a orientação do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c2e70-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="c2e70-593">**Microsoft. PerceptionSimulation. StreamDataTypes. hands**</span><span class="sxs-lookup"><span data-stu-id="c2e70-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="c2e70-594">Fluxo de dados para a posição e gestos de mãos.</span><span class="sxs-lookup"><span data-stu-id="c2e70-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="c2e70-595">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="c2e70-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="c2e70-596">Fluxo de dados para o mapeamento espacial do ambiente.</span><span class="sxs-lookup"><span data-stu-id="c2e70-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="c2e70-597">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="c2e70-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="c2e70-598">Fluxo de dados para a calibragem do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="c2e70-599">Os pacotes de calibragem são aceitos apenas por um sistema no modo remoto.</span><span class="sxs-lookup"><span data-stu-id="c2e70-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="c2e70-600">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="c2e70-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="c2e70-601">Fluxo de dados para o ambiente do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="c2e70-602">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="c2e70-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="c2e70-603">Fluxo de dados para controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="c2e70-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="c2e70-604">**Microsoft. PerceptionSimulation. StreamDataTypes. eyess**</span><span class="sxs-lookup"><span data-stu-id="c2e70-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="c2e70-605">Fluxo de dados com os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="c2e70-606">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c2e70-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="c2e70-607">Fluxo de dados com a configuração de exibição do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2e70-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="c2e70-608">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="c2e70-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="c2e70-609">Um valor de sentinela usado para indicar todos os tipos de dados gravados.</span><span class="sxs-lookup"><span data-stu-id="c2e70-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="c2e70-610">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="c2e70-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="c2e70-611">Um objeto que recebe pacotes de dados de um fluxo de simulação.</span><span class="sxs-lookup"><span data-stu-id="c2e70-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="c2e70-612">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (pacote de comprimento uint, Byte [])**</span><span class="sxs-lookup"><span data-stu-id="c2e70-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="c2e70-613">Recebe um único pacote, que é digitado internamente e com controle de versão.</span><span class="sxs-lookup"><span data-stu-id="c2e70-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="c2e70-614">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2e70-614">Parameters</span></span>
* <span data-ttu-id="c2e70-615">comprimento-o comprimento do pacote.</span><span class="sxs-lookup"><span data-stu-id="c2e70-615">length - The length of the packet.</span></span>
* <span data-ttu-id="c2e70-616">pacote-os dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="c2e70-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="c2e70-617">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="c2e70-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="c2e70-618">Um objeto que cria ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="c2e70-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="c2e70-619">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="c2e70-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="c2e70-620">Cria uma única instância de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="c2e70-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="c2e70-621">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2e70-621">Return value</span></span>

<span data-ttu-id="c2e70-622">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="c2e70-622">The created sink.</span></span>
