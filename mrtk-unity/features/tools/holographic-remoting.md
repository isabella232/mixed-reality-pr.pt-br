---
title: Comunicação remota holográfica
description: Documentação do Holographic de comunicação remota MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176643"
---
# <a name="holographic-remoting"></a><span data-ttu-id="7351c-104">Comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7351c-104">Holographic remoting</span></span>

<span data-ttu-id="7351c-105">o Holographicing remoting transmite o conteúdo do Holographic de um PC para seu Microsoft HoloLens em tempo real, usando uma conexão de cabo Wi-Fi ou USB.</span><span class="sxs-lookup"><span data-stu-id="7351c-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="7351c-106">Esse recurso pode aumentar significativamente a produtividade do desenvolvedor ao desenvolver aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7351c-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="7351c-107">O XR SDK, conforme mencionado abaixo, refere-se ao [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="7351c-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="7351c-108">Consulte [aqui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) para obter mais informações sobre como usar o SDK do XR com MRTK.</span><span class="sxs-lookup"><span data-stu-id="7351c-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="7351c-109">O XR herdado refere-se ao pipeline XR existente que está incluído no Unity 2018, preterido no Unity 2019,3 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="7351c-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="7351c-110">Instalação inicial</span><span class="sxs-lookup"><span data-stu-id="7351c-110">Initial setup</span></span>

<span data-ttu-id="7351c-111">para habilitar a comunicação remota com um HoloLens, é importante garantir que o projeto esteja usando os componentes de comunicação remota mais recentes.</span><span class="sxs-lookup"><span data-stu-id="7351c-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="7351c-112">abrir **> de janela Gerenciador de Pacotes**</span><span class="sxs-lookup"><span data-stu-id="7351c-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="7351c-113">se estiver usando a XR legacy: verifique se a versão mais recente do pacote de **Windows Mixed Reality** está instalada.</span><span class="sxs-lookup"><span data-stu-id="7351c-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="7351c-114">se estiver usando o SDK do xr: verifique se a versão mais recente do pacote de **plug-in Windows XR** está instalada.</span><span class="sxs-lookup"><span data-stu-id="7351c-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="7351c-115">verifique se o aplicativo de comunicação remota Holographic mais recente está instalado na HoloLens, por meio do Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="7351c-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="7351c-116">Continue nas [instruções de instalação do XR Legacy](#legacy-xr-setup-instructions) ou nas [instruções de instalação do XR SDK](#xr-sdk-setup-instructions) , dependendo de qual pipeline é usado no projeto.</span><span class="sxs-lookup"><span data-stu-id="7351c-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="7351c-117">Instruções de instalação do XR Legacy</span><span class="sxs-lookup"><span data-stu-id="7351c-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="7351c-118">as instruções a seguir se aplicam somente ao remoting com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7351c-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="7351c-119">se você executar apenas a comunicação remota com HoloLens (1ª Gen), pule para [se conectar ao HoloLens com Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="7351c-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="7351c-120">ao usar um HoloLens 2, o suporte para dados de rastreamento articulado e de controle de dicas de comunicação remota foi adicionado ao MRTK.</span><span class="sxs-lookup"><span data-stu-id="7351c-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="7351c-121">Para habilitar esses recursos, siga as etapas documentadas em [importar DotNetWinRT para o projeto](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="7351c-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="7351c-122">depois de importado, a próxima etapa é selecionar a **realidade misturada**  >  **Toolkit**  >  **utilitários**  >  **Windows Mixed Reality**  >  **verificar a configuração**.</span><span class="sxs-lookup"><span data-stu-id="7351c-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="7351c-123">Esta etapa adiciona uma definição de script que habilita a dependência DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="7351c-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="7351c-124">Ao usar o Unity 2019,4 e mais recente, não é necessário executar o utilitário verificar configuração.</span><span class="sxs-lookup"><span data-stu-id="7351c-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="7351c-125">para habilitar o acompanhamento de junções de mão e acompanhamento de olho, siga as etapas na seção **depuração HoloLens 2 remotas por meio de importação de pacote do Unity** e relacionadas.</span><span class="sxs-lookup"><span data-stu-id="7351c-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="7351c-126">depuração de comunicação remota HoloLens 2 por meio da importação de pacote do Unity</span><span class="sxs-lookup"><span data-stu-id="7351c-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="7351c-127">se HoloLens junções de duas mãos e acompanhamento de olho não estiverem trabalhando em relação à comunicação remota, haverá alguns pontos comuns de possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="7351c-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="7351c-128">Eles estão listados abaixo na ordem em que devem ser verificados.</span><span class="sxs-lookup"><span data-stu-id="7351c-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="7351c-129">Esses problemas são especialmente relevantes quando executados no **Unity 2019,3** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7351c-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="7351c-130">Importar DotNetWinRT para o projeto</span><span class="sxs-lookup"><span data-stu-id="7351c-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="7351c-131">Baixe a [ferramenta de funcionalidade de realidade misturada](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="7351c-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="7351c-132">Na exibição **descobrir recursos** , selecione *projeções do WinRT de realidade misturada*</span><span class="sxs-lookup"><span data-stu-id="7351c-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Selecionar pacote DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="7351c-134">Clique em **obter recursos** e continue para [importar o pacote](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="7351c-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="7351c-135">DOTNETWINRT_PRESENT definir gravações nas configurações do Player</span><span class="sxs-lookup"><span data-stu-id="7351c-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="7351c-136">ao usar o Unity 2019,4 e mais recente, o DOTNETWINRT_PRESENT definir está contido nos arquivos. asmdef apropriados e não no Configurações do Unity Player.</span><span class="sxs-lookup"><span data-stu-id="7351c-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="7351c-137">A etapa verificar configuração não é necessária.</span><span class="sxs-lookup"><span data-stu-id="7351c-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="7351c-138">A partir do MRTK versão 2.5.0, por motivos de desempenho, essa #define não é mais definida automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7351c-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="7351c-139">para habilitar esse sinalizador, use o item de menu da **realidade misturada Toolkit**  >  **utilitários**  >  **Windows Mixed Reality**  >  **verificar configuração** .</span><span class="sxs-lookup"><span data-stu-id="7351c-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="7351c-140">O item de configuração de verificação não exibe uma confirmação.</span><span class="sxs-lookup"><span data-stu-id="7351c-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="7351c-141">para confirmar que a definição foi definida, navegue até o Configurações do Unity Player.</span><span class="sxs-lookup"><span data-stu-id="7351c-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="7351c-142">a partir daí, na guia UWP, verifique em outros Configurações para que o script defina os símbolos.</span><span class="sxs-lookup"><span data-stu-id="7351c-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="7351c-143">Verifique se DOTNETWINRT_PRESENT está escrito corretamente na lista.</span><span class="sxs-lookup"><span data-stu-id="7351c-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="7351c-144">Se isso estiver lá, essa etapa foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7351c-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="7351c-146">removendo HoloLens suporte a comunicação remota específico</span><span class="sxs-lookup"><span data-stu-id="7351c-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="7351c-147">Se você estiver executando conflitos ou outros problemas devido à presença do adaptador DotNetWinRT, entre [em contato com um dos nossos recursos de ajuda](../../index.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="7351c-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="7351c-148">Instruções de instalação do XR SDK</span><span class="sxs-lookup"><span data-stu-id="7351c-148">XR SDK setup instructions</span></span>

<span data-ttu-id="7351c-149">siga as [instruções de instalação do Windows Mixed Reality na página introdução ao SDK do MRTK e do XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e certifique-se de executar a etapa necessária para comunicação remota HoloLens no editor.</span><span class="sxs-lookup"><span data-stu-id="7351c-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="7351c-150">conectando-se ao HoloLens com Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="7351c-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="7351c-151">Depois que o projeto tiver sido configurado, uma conexão poderá ser estabelecida com a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7351c-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="7351c-152">em **arquivo > build Configurações**, verifique se o tipo de compilação do projeto está definido como **Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="7351c-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="7351c-153">na HoloLens, inicie o aplicativo de **comunicação remota Holographic** .</span><span class="sxs-lookup"><span data-stu-id="7351c-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="7351c-154">no Unity, selecione **Window > XR > emulação de Holographic (se estiver usando o SDK xr)/Windows xr Plugin de comunicação remota (se estiver usando o do xr)**.</span><span class="sxs-lookup"><span data-stu-id="7351c-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Iniciar emulação de Holographic](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="7351c-156">Defina o **modo de emulação** como **remoto para dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="7351c-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Definir modo de emulação](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="7351c-158">(**_Aplica-se somente a XR herdado_**) Selecione a **versão do dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="7351c-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Selecionar versão do dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="7351c-160">Usando o endereço IP exibido pelo aplicativo de player de comunicação remota do Holographic, defina o campo **máquina remota** .</span><span class="sxs-lookup"><span data-stu-id="7351c-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Inserir endereço IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="7351c-162">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="7351c-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="7351c-163">se você não puder se conectar, verifique se o HoloLens 2 não está conectado ao seu PC e reinicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="7351c-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="7351c-164">conectando-se ao HoloLens com cabo USB</span><span class="sxs-lookup"><span data-stu-id="7351c-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="7351c-165">A conexão de cabo USB fornece melhor qualidade de renderização e estabilidade.</span><span class="sxs-lookup"><span data-stu-id="7351c-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="7351c-166">para usar a conexão de cabo USB, desconecte-se da HoloLens da Wi-Fi na Configurações do HoloLens e inicie o aplicativo do Player de comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="7351c-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="7351c-167">Ele exibirá um endereço IP que começa com 169.</span><span class="sxs-lookup"><span data-stu-id="7351c-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="7351c-168">Use esse endereço IP na configuração de emulação de Holographic do Unity para se conectar.</span><span class="sxs-lookup"><span data-stu-id="7351c-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="7351c-169">depois que o endereço IP para o cabo USB tiver sido identificado, será seguro conectar o HoloLens para Wi-Fi novamente.</span><span class="sxs-lookup"><span data-stu-id="7351c-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="7351c-170">Iniciando uma sessão de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="7351c-170">Starting a remoting session</span></span>

<span data-ttu-id="7351c-171">com o Unity conectado à HoloLens, insira o modo de reprodução no editor.</span><span class="sxs-lookup"><span data-stu-id="7351c-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="7351c-172">Quando a sessão estiver concluída, saia do modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="7351c-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="7351c-173">Há um problema conhecido com algumas versões do Unity, em que o editor pode travar ao entrar no modo de reprodução durante uma sessão de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="7351c-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="7351c-174">Esse problema poderá ser manifestado se a janela Holographic estiver aberta quando o projeto for carregado.</span><span class="sxs-lookup"><span data-stu-id="7351c-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="7351c-175">Para garantir que esse problema não ocorra, sempre feche a caixa de diálogo Holographic antes de sair do Unity.</span><span class="sxs-lookup"><span data-stu-id="7351c-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="7351c-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="7351c-176">See also</span></span>

- [<span data-ttu-id="7351c-177">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="7351c-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="7351c-178">Termos de licença para software Microsoft Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7351c-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
