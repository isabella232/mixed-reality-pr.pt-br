---
title: Criação de perfil com informações inreais
description: Saiba como usar percepções inreais no HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Inreal, Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, contornar, insights, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486303"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="40911-104">Criação de perfil com informações inreais</span><span class="sxs-lookup"><span data-stu-id="40911-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="40911-105">[Insights inreais](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) é um sistema de criação de perfil que coleta, analisa e visualiza dados de um mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="40911-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="40911-106">O sistema de criação de perfil pode ajudá-lo a encontrar gargalos de otimização e áreas em que o desempenho de aplicativos poderia usar um aumento.</span><span class="sxs-lookup"><span data-stu-id="40911-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="40911-107">Normalmente, você habilita informações inreais diretamente do editor, mas para o HoloLens 2, você precisará usar a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="40911-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="40911-108">Instalação</span><span class="sxs-lookup"><span data-stu-id="40911-108">Setup</span></span>

<span data-ttu-id="40911-109">Inreal permite que você crie e configure um "perfil personalizado" no iniciador do HoloLens com os parâmetros de linha de comando que habilitam insights inreais.</span><span class="sxs-lookup"><span data-stu-id="40911-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="40911-110">Localize o endereço IP do seu computador usando o comando **ipconfig** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="40911-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="40911-111">O endereço IP é o endereço IPv4 listado por ipconfig.</span><span class="sxs-lookup"><span data-stu-id="40911-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="40911-112">Tenha isso em mente para mais tarde quando você definir parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="40911-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40911-113">Se você estiver atrás de uma VPN, talvez seja necessário fornecer o endereço IP fornecido por meio da VPN.</span><span class="sxs-lookup"><span data-stu-id="40911-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Captura de tela dos resultados da linha de comando para o comando ipconfig](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="40911-115">Vá para a parte superior do painel de mecanismo inreal e abra **Device Manager** no botão **Iniciar** :</span><span class="sxs-lookup"><span data-stu-id="40911-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Captura de tela das opções de inicialização com o Gerenciador de dispositivos realçado](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="40911-117">Na Device Manager, selecione **Adicionar um dispositivo não listado**:</span><span class="sxs-lookup"><span data-stu-id="40911-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Captura de tela do Gerenciador de dispositivos aberta no mecanismo inreal](images/unreal-insights-img-03.png)

4. <span data-ttu-id="40911-119">Clique em **selecionar uma plataforma** e escolha **HoloLens**:</span><span class="sxs-lookup"><span data-stu-id="40911-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Captura de tela de adicionar lista suspensa de dispositivos não listados com o HoloLens realçado](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="40911-121">Se você estiver usando IPoverUSB, digite 127.0.0.1:10080 como o identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40911-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="40911-122">Insira seu usuário e senha do HoloLens em seus respectivos campos e preencha o **nome de exibição** como desejar.</span><span class="sxs-lookup"><span data-stu-id="40911-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40911-123">O identificador de dispositivo é o endereço IP do HoloLens, não o computador que executa informações invisíveis encontradas na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="40911-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Captura de tela dos detalhes do dispositivo do HoloLens no Gerenciador de dispositivos](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="40911-125">Selecione **Adicionar** e seu HoloLens deve aparecer na lista de dispositivos do Gerenciador de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="40911-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Captura de tela do HoloLens adicionado à lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="40911-127">Inicializar</span><span class="sxs-lookup"><span data-stu-id="40911-127">Launch</span></span>

1. <span data-ttu-id="40911-128">Abra o **inicializador de projeto** no painel UE4 no botão **Iniciar** :</span><span class="sxs-lookup"><span data-stu-id="40911-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Captura de tela das opções de inicialização com o iniciador do projeto](images/unreal-insights-img-07.png)

2. <span data-ttu-id="40911-130">Selecione o **+** botão para criar um perfil personalizado em **perfis de inicialização personalizados**.</span><span class="sxs-lookup"><span data-stu-id="40911-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="40911-131">Depois de criado, você sempre poderá editar este perfil mais tarde:</span><span class="sxs-lookup"><span data-stu-id="40911-131">Once created, you can always edit this profile later:</span></span>

![Captura de tela do iniciador de projeto com perfis de inicialização personalizados realçados](images/unreal-insights-img-08.png)

3. <span data-ttu-id="40911-133">Selecione o botão **Editar perfil** no perfil de inicialização personalizada do HoloLens e configure:</span><span class="sxs-lookup"><span data-stu-id="40911-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="40911-134">Selecione o **Cookie** para **o livro** para habilitar a cópia para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="40911-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="40911-135">Convém verificar se deseja **arquivar?** na seção **arquivo morto** para manter o. appxbundle gerado em vez de excluir para economizar espaço em disco.</span><span class="sxs-lookup"><span data-stu-id="40911-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="40911-136">Especifique um local para o. appxbundle e alterne para uma compilação de desenvolvimento, se desejar</span><span class="sxs-lookup"><span data-stu-id="40911-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Captura de tela de opções de Cook na configuração de perfil com o Cook pelo livro e o HoloLens realçado](images/unreal-insights-img-09.png)

4. <span data-ttu-id="40911-138">Defina **como você deseja implantar a compilação?** para **copiar para o dispositivo** para ativar a seção de **inicialização** da interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="40911-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Captura de tela do iniciador de projeto com opções de implantação com cópia para dispositivo realçado](images/unreal-insights-img-10.png)

5. <span data-ttu-id="40911-140">Defina **parâmetros de linha de comando adicionais** na seção **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="40911-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="40911-141">Os parâmetros serão gravados em um arquivo ue4commandline.txt, empacotados no pacote e usados na inicialização.</span><span class="sxs-lookup"><span data-stu-id="40911-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="40911-142">Tente isso para os iniciantes: **-tracehost = IP_OF_YOUR_PC-Trace = log, indicador, quadro, CPU, GPU, loadtime, File, net**</span><span class="sxs-lookup"><span data-stu-id="40911-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="40911-143">Você pode encontrar uma lista completa dos parâmetros de inicialização disponíveis na [documentação de referência do insights não reais](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="40911-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="40911-144">"IP_OF_YOUR_PC" é o endereço IP que encontramos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="40911-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="40911-145">Esse é o endereço IP do computador que está executando insights inreais, não o endereço IP do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="40911-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40911-146">Os rastreamentos podem ficar grandes muito rapidamente.</span><span class="sxs-lookup"><span data-stu-id="40911-146">Traces can get large very quickly.</span></span> <span data-ttu-id="40911-147">Habilite somente os canais necessários para manter o tamanho do rastreamento baixo.</span><span class="sxs-lookup"><span data-stu-id="40911-147">Enable only those channels you need to keep trace size low.</span></span>

![Captura de tela das opções de configuração de inicialização](images/unreal-insights-img-11.png)

6. <span data-ttu-id="40911-149">Inicie informações incorretas antes da inicialização do aplicativo; caso contrário, os insights não poderão ser inicializados adequadamente antes do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="40911-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="40911-150">O executável insights não reais é armazenado na pasta do mecanismo de binários, geralmente da seguinte maneira: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="40911-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Captura de tela de executáveis insights em execução](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="40911-152">Selecione **voltar** para retornar à raiz da caixa de diálogo **iniciador do projeto**</span><span class="sxs-lookup"><span data-stu-id="40911-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="40911-153">De volta ao editor, clique em **Iniciar** em seu perfil de inicialização personalizado</span><span class="sxs-lookup"><span data-stu-id="40911-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Captura de tela de perfis de inicialização personalizados](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="40911-155">Assista à medida que seu projeto é empacotado, instalado em seu dispositivo e iniciado</span><span class="sxs-lookup"><span data-stu-id="40911-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="40911-156">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="40911-156">Profiling</span></span>

<span data-ttu-id="40911-157">De volta às informações inreais, selecione a conexão **dinâmica** com o dispositivo para iniciar a criação de perfil</span><span class="sxs-lookup"><span data-stu-id="40911-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="40911-158">O perfil personalizado é compartilhado entre projetos.</span><span class="sxs-lookup"><span data-stu-id="40911-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="40911-159">Daqui em diante, você pode usar o perfil personalizado criado em vez de ter que fazer isso todas as vezes.</span><span class="sxs-lookup"><span data-stu-id="40911-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="40911-160">Você só precisa recriar a conexão com o dispositivo toda vez que iniciar inreal com as etapas 3 a 6 na [seção de instalação](#setup).</span><span class="sxs-lookup"><span data-stu-id="40911-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="40911-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40911-161">See also</span></span>
* [<span data-ttu-id="40911-162">Documentação de informações inreais</span><span class="sxs-lookup"><span data-stu-id="40911-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

