---
title: Distribuindo seus aplicativos
description: Uma visão geral das diferentes opções de distribuição para várias plataformas com suporte e armazenamentos de publicação.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: HoloLens, realidade misturada, headsets de imersão, aplicativo, UWP, envio, envio, filtros, metadados, requisitos de sistema, palavras-chave, wack, certificação, pacote, Appx, merchandising
ms.openlocfilehash: f52109792e174a0b0fbdd9738539b5fc88f190a1
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443521"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="cba50-104">Distribuindo seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="cba50-104">Distributing your apps</span></span>

![Lancher de aplicativo 3D de pássaro flutuante na página inicial do WMR](images/distribute-hero-image.png)

<span data-ttu-id="cba50-106">Colocar seus aplicativos em mãos de seus usuários ou de fora do mundo é o mais importante, e às vezes criteriosa, faz parte de qualquer esforço de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="cba50-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="cba50-107">Simplificamos o processo em um conjunto de recursos listados abaixo, todos eles dependem do cenário de distribuição e implantação mais adequado para você ou sua equipe.</span><span class="sxs-lookup"><span data-stu-id="cba50-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="cba50-108">Opções de distribuição</span><span class="sxs-lookup"><span data-stu-id="cba50-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="cba50-109">Se você estiver compartilhando seu aplicativo com outra parte, será necessário compilar e fornecer o arquivo Appx.</span><span class="sxs-lookup"><span data-stu-id="cba50-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="cba50-110">Se estiver usando o instalador do aplicativo, você também precisará compartilhar o certificado com o usuário.</span><span class="sxs-lookup"><span data-stu-id="cba50-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="cba50-111">Se você estiver compartilhando com uma organização, precisará de uma conta corporativa ou de estudante e acessar a infraestrutura [MDM (gerenciamento de dispositivo móvel)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) das organizações.</span><span class="sxs-lookup"><span data-stu-id="cba50-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="cba50-112">Se você for a parte compartilhada, precisará ser um administrador em seu locatário e usar o [centro de administração do Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) para disponibilizar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cba50-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="cba50-113">Outra opção é compartilhar o arquivo Appx e as dependências do aplicativo com o usuário final.</span><span class="sxs-lookup"><span data-stu-id="cba50-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="cba50-114">Se você for o usuário final, o aplicativo será baixado automaticamente ou estará disponível para download depois que você se registrar no locatário da organização de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="cba50-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="cba50-115"><strong>Cenário</strong></span><span class="sxs-lookup"><span data-stu-id="cba50-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="cba50-116"><strong>Instalação do dispositivo local</strong></span><span class="sxs-lookup"><span data-stu-id="cba50-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="cba50-117"><strong>Compartilhar com qualquer pessoa</strong></span><span class="sxs-lookup"><span data-stu-id="cba50-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="cba50-118"><strong>Compartilhar com uma organização</strong></span><span class="sxs-lookup"><span data-stu-id="cba50-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador do aplicativo</strong></a> (por meio de <a href="https://docs.microsoft.com/hololens/hololens-insider">compilações do Windows Insider</a>)</span><span class="sxs-lookup"><span data-stu-id="cba50-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></a> (through <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider builds</a>)</span></span></td>
    <td><span data-ttu-id="cba50-120">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-120">✔️</span></span></td>
    <td><span data-ttu-id="cba50-121">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portal da Empresa</strong></a></span><span class="sxs-lookup"><span data-stu-id="cba50-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cba50-123">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM – instalação necessária do aplicativo</strong></a></span><span class="sxs-lookup"><span data-stu-id="cba50-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cba50-125">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="cba50-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="cba50-127">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-127">✔️</span></span></td>
    <td><span data-ttu-id="cba50-128">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></span><span class="sxs-lookup"><span data-stu-id="cba50-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cba50-130">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Pacote de provisionamento</strong></a></span><span class="sxs-lookup"><span data-stu-id="cba50-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="cba50-132">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-132">✔️</span></span></td>
    <td><span data-ttu-id="cba50-133">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-133">✔️</span></span></td>
    <td><span data-ttu-id="cba50-134">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cba50-135"><a href="#additional-scenarios"><strong>Implantação personalizada do Win32</strong></a> (somente realidade mista do Windows-Veja abaixo)</span><span class="sxs-lookup"><span data-stu-id="cba50-135"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Windows Mixed Reality only - see below)</span></span></td>
    <td><span data-ttu-id="cba50-136">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-136">✔️</span></span></td>
    <td><span data-ttu-id="cba50-137">✔️</span><span class="sxs-lookup"><span data-stu-id="cba50-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="cba50-138">O instalador do aplicativo não está disponível no momento para dispositivos gerenciados ou dispositivos HoloLens (1º gen).</span><span class="sxs-lookup"><span data-stu-id="cba50-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="cba50-139">Cenários adicionais</span><span class="sxs-lookup"><span data-stu-id="cba50-139">Additional scenarios</span></span>

* <span data-ttu-id="cba50-140">Para a implantação de aplicativos Win32, incluindo o fluxo e o jogo pass, você pode produzir um Win32. Arquivo EXE usando o destino de Build do PC autônomo do Unity e envie seus aplicativos normalmente para a plataforma escolhida.</span><span class="sxs-lookup"><span data-stu-id="cba50-140">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="cba50-141">Se você precisar instalar um aplicativo do HoloLens 2 enquanto estiver offline, consulte as instruções [offline seguras do hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) ou instale o aplicativo por meio de um pacote de provisionamento sem habilitar o modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="cba50-141">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="cba50-142">Você também pode implantar compilações em seu dispositivo e compartilhá-las com outros desenvolvedores que têm o modo de desenvolvedor habilitado [Implantando e Depurando com o Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou [instalando um pacote de aplicativos com o portal do dispositivo](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="cba50-142">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="cba50-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="cba50-143">See also</span></span>
* [<span data-ttu-id="cba50-144">Localizando, instalando e desinstalando aplicativos do Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="cba50-144">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->