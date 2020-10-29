---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de pesquisa, CV, RS4, pesquisa Visual computacional, Research, HoloLens, HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675311"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="db512-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="db512-104">HoloLens Research Mode</span></span>

<span data-ttu-id="db512-105">O modo de pesquisa foi introduzido no HoloLens de primeira geração para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa que não se destinam à implantação.</span><span class="sxs-lookup"><span data-stu-id="db512-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="db512-106">O modo de pesquisa para o HoloLens 2 retém os recursos do HoloLens 1, adicionando acesso a fluxos adicionais:</span><span class="sxs-lookup"><span data-stu-id="db512-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="db512-107">**Câmeras de acompanhamento de ambiente leve visíveis** – câmeras em escala cinza usadas pelo sistema para rastreamento de cabeçalho e criação de mapa.</span><span class="sxs-lookup"><span data-stu-id="db512-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="db512-108">**Câmera de profundidade** – opera em dois modos:</span><span class="sxs-lookup"><span data-stu-id="db512-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="db512-109">Detecção de AHAT, alta frequência (45 FPS) usada para acompanhamento à mão.</span><span class="sxs-lookup"><span data-stu-id="db512-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="db512-110">Diferentemente do modo de curto-throw da primeira versão, AHAT dá uma pseudo profundidade com o encapsulamento de fase além de 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="db512-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="db512-111">Detecção de longo alcance, de baixa frequência (1-5 FPS) de longa profundidade usada pelo [mapeamento espacial](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="db512-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="db512-112">**Duas versões do fluxo ir-reflectivity** -usadas pelo HoloLens para calcular a profundidade.</span><span class="sxs-lookup"><span data-stu-id="db512-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="db512-113">Essas imagens são iluminadas por infravermelho e não são afetadas pela luz visível de ambiente.</span><span class="sxs-lookup"><span data-stu-id="db512-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="db512-114">Se você estiver usando um HoloLens 2, também terá acesso às entradas adicionais abaixo:</span><span class="sxs-lookup"><span data-stu-id="db512-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="db512-115">**Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.</span><span class="sxs-lookup"><span data-stu-id="db512-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="db512-116">**Giro** – usado pelo sistema para determinar rotações.</span><span class="sxs-lookup"><span data-stu-id="db512-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="db512-117">**Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.</span><span class="sxs-lookup"><span data-stu-id="db512-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db512-118">O modo de pesquisa está atualmente em visualização pública.</span><span class="sxs-lookup"><span data-stu-id="db512-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="db512-119">![Captura de tela do aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="db512-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="db512-120">*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="db512-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="db512-121">Uso</span><span class="sxs-lookup"><span data-stu-id="db512-121">Usage</span></span>

<span data-ttu-id="db512-122">O modo de pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="db512-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="db512-123">Ele não se destina a aplicativos implantados em ambientes corporativos ou disponíveis por meio do Microsoft Store ou de outros canais de distribuição.</span><span class="sxs-lookup"><span data-stu-id="db512-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="db512-124">Além disso, a Microsoft não fornece garantias de que o modo de pesquisa ou funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="db512-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="db512-125">No entanto, isso não deve impedir que você o use para desenvolver e testar novas ideias!</span><span class="sxs-lookup"><span data-stu-id="db512-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="db512-126">Segurança e desempenho</span><span class="sxs-lookup"><span data-stu-id="db512-126">Security and performance</span></span>

<span data-ttu-id="db512-127">Lembre-se de que habilitar o modo de pesquisa usa mais energia da bateria do que usar o HoloLens 2 em condições normais.</span><span class="sxs-lookup"><span data-stu-id="db512-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="db512-128">Isso é verdadeiro mesmo que o aplicativo que usa os recursos do modo de pesquisa não esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="db512-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="db512-129">Habilitar esse modo também pode reduzir a segurança geral do seu dispositivo, pois os aplicativos podem indevidamente os dados do sensor.</span><span class="sxs-lookup"><span data-stu-id="db512-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="db512-130">Você pode encontrar mais informações sobre a segurança do dispositivo nas [perguntas frequentes sobre segurança do HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="db512-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="db512-131">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="db512-131">Device support</span></span>
<table><span data-ttu-id="db512-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="db512-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="db512-133"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="db512-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="db512-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></span><span class="sxs-lookup"><span data-stu-id="db512-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="db512-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="db512-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="db512-136">Câmeras de acompanhamento de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="db512-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="db512-137">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-137">✔️</span></span></td>
        <td><span data-ttu-id="db512-138">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="db512-139">Profundidade & câmera IR</span><span class="sxs-lookup"><span data-stu-id="db512-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="db512-140">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-140">✔️</span></span></td>
        <td><span data-ttu-id="db512-141">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="db512-142">Acelerômetro</span><span class="sxs-lookup"><span data-stu-id="db512-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="db512-143">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="db512-144">Giroscópio</span><span class="sxs-lookup"><span data-stu-id="db512-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="db512-145">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="db512-146">Magnetômetro</span><span class="sxs-lookup"><span data-stu-id="db512-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="db512-147">✔️</span><span class="sxs-lookup"><span data-stu-id="db512-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="db512-148">Habilitando o modo de pesquisa (primeiro a partir do HoloLens e do HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="db512-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="db512-149">O modo de pesquisa é uma extensão do modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="db512-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="db512-150">Antes de iniciar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do modo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="db512-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="db512-151">Abra o **menu iniciar > configurações** e selecione **atualizações** .</span><span class="sxs-lookup"><span data-stu-id="db512-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="db512-152">Selecione **para desenvolvedores** e habilite o **modo de desenvolvedor** .</span><span class="sxs-lookup"><span data-stu-id="db512-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="db512-153">Role para baixo e habilite o **Portal de Dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="db512-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="db512-154">Depois que os recursos do desenvolvedor estiverem habilitados, [Conecte-se ao portal do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do modo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="db512-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="db512-155">Vá para o **sistema > modo de pesquisa** no **portal do dispositivo** .</span><span class="sxs-lookup"><span data-stu-id="db512-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="db512-156">Selecione **permitir acesso ao fluxo do sensor** .</span><span class="sxs-lookup"><span data-stu-id="db512-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="db512-157">Reinicie o dispositivo a partir do item de menu de **energia** na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="db512-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="db512-158">Depois de reiniciar o dispositivo, os aplicativos carregados por meio do portal do **dispositivo** poderão acessar os fluxos do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="db512-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="db512-159">![Guia modo de pesquisa do portal do dispositivo do HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="db512-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="db512-160">*Janela do modo de pesquisa no portal do dispositivo do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="db512-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db512-161">O modo de pesquisa para o HoloLens 2 está disponível a partir do Build 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="db512-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="db512-162">Se você precisar de acesso em uma compilação anterior, Inscreva-se em nosso programa [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="db512-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="db512-163">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="db512-163">Using sensor data in your apps</span></span>

<span data-ttu-id="db512-164">Os aplicativos podem acessar os dados de fluxo do sensor da mesma maneira que os fluxos de foto e câmera de vídeo são acessados por meio de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="db512-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="db512-165">Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="db512-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="db512-166">Em particular, o aplicativo sabe precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.</span><span class="sxs-lookup"><span data-stu-id="db512-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="db512-167">Você pode encontrar aplicativos de exemplo para acessar os vários fluxos do modo de pesquisa, usando os [intrínsecos e as extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), e gravando fluxos no respectivo modo de pesquisa repositórios:</span><span class="sxs-lookup"><span data-stu-id="db512-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="db512-168">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="db512-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="db512-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="db512-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="db512-170">Suporte</span><span class="sxs-lookup"><span data-stu-id="db512-170">Support</span></span>

<span data-ttu-id="db512-171">Para o HoloLens (1º gen), use o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV para postar comentários e acompanhar problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="db512-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="db512-172">Para o HoloLens 2, use o Issue [Tracker](https://github.com/microsoft/HoloLens2ForCV/issues) no repositório HoloLens2ForCV para postar comentários e acompanhar problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="db512-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="db512-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db512-173">See also</span></span>

* [<span data-ttu-id="db512-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="db512-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="db512-175">Repositório GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="db512-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="db512-176">Repositório GitHub HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="db512-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="db512-177">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="db512-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
