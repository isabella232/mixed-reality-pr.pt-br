---
title: Referência de API do portal de dispositivos
description: Mantenha-se atualizado sobre a API do portal do dispositivo Windows para o desenvolvimento de HoloLens.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: cdbe9635fc51a0d19c978b72fdc8d5db6b8e8e01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581249"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="7fdee-104">Referência de API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="7fdee-104">Device portal API reference</span></span>

<span data-ttu-id="7fdee-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="7fdee-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="7fdee-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7fdee-106">App deloyment</span></span>

<span data-ttu-id="7fdee-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="7fdee-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="7fdee-108">Uninstalls an app</span></span>

<span data-ttu-id="7fdee-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-109">Parameters</span></span>
* <span data-ttu-id="7fdee-110">Package: nome de arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="7fdee-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="7fdee-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="7fdee-112">Installs an App</span></span>

<span data-ttu-id="7fdee-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-113">Parameters</span></span>
* <span data-ttu-id="7fdee-114">Package: nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="7fdee-115">Carga útil</span><span class="sxs-lookup"><span data-stu-id="7fdee-115">Payload</span></span>
* <span data-ttu-id="7fdee-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="7fdee-116">multi-part conforming http body</span></span>

<span data-ttu-id="7fdee-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="7fdee-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="7fdee-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="7fdee-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-119">Return data</span></span>
* <span data-ttu-id="7fdee-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="7fdee-120">List of installed packages with details</span></span>

<span data-ttu-id="7fdee-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="7fdee-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="7fdee-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="7fdee-123">Coleta de despejo</span><span class="sxs-lookup"><span data-stu-id="7fdee-123">Dump collection</span></span>

<span data-ttu-id="7fdee-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="7fdee-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="7fdee-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-126">Parameters</span></span>
* <span data-ttu-id="7fdee-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="7fdee-127">packageFullname : package name</span></span>

<span data-ttu-id="7fdee-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="7fdee-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="7fdee-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-130">Parameters</span></span>
* <span data-ttu-id="7fdee-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="7fdee-131">packageFullname : package name</span></span>

<span data-ttu-id="7fdee-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="7fdee-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="7fdee-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-134">Parameters</span></span>
* <span data-ttu-id="7fdee-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="7fdee-135">packageFullname : package name</span></span>

<span data-ttu-id="7fdee-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="7fdee-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="7fdee-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-138">Parameters</span></span>
* <span data-ttu-id="7fdee-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="7fdee-139">packageFullname : package name</span></span>
* <span data-ttu-id="7fdee-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="7fdee-140">fileName : dump file name</span></span>

<span data-ttu-id="7fdee-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="7fdee-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="7fdee-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-143">Parameters</span></span>
* <span data-ttu-id="7fdee-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="7fdee-144">packageFullname : package name</span></span>
* <span data-ttu-id="7fdee-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="7fdee-145">fileName : dump file name</span></span>

<span data-ttu-id="7fdee-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-146">Return data</span></span>
* <span data-ttu-id="7fdee-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="7fdee-147">Dump file.</span></span> <span data-ttu-id="7fdee-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7fdee-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="7fdee-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="7fdee-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="7fdee-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="7fdee-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-151">Return data</span></span>
* <span data-ttu-id="7fdee-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="7fdee-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="7fdee-153">ETW</span><span class="sxs-lookup"><span data-stu-id="7fdee-153">ETW</span></span>

<span data-ttu-id="7fdee-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="7fdee-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="7fdee-155">Enumerates registered providers</span></span>

<span data-ttu-id="7fdee-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-156">Return data</span></span>
* <span data-ttu-id="7fdee-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="7fdee-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="7fdee-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="7fdee-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7fdee-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="7fdee-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-160">Return data</span></span>
* <span data-ttu-id="7fdee-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="7fdee-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="7fdee-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="7fdee-162">Holographic OS</span></span>

<span data-ttu-id="7fdee-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="7fdee-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="7fdee-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="7fdee-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="7fdee-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="7fdee-166">Returns the states of all services running.</span></span>

<span data-ttu-id="7fdee-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="7fdee-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="7fdee-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="7fdee-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="7fdee-170">Sets the IPD</span></span>

<span data-ttu-id="7fdee-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-171">Parameters</span></span>
* <span data-ttu-id="7fdee-172">IPD: novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="7fdee-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="7fdee-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="7fdee-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="7fdee-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="7fdee-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="7fdee-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="7fdee-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-177">Parameters</span></span>
* <span data-ttu-id="7fdee-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="7fdee-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="7fdee-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="7fdee-179">Holographic Perception</span></span>

<span data-ttu-id="7fdee-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="7fdee-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="7fdee-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="7fdee-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-182">Parameters</span></span>
* <span data-ttu-id="7fdee-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="7fdee-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="7fdee-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="7fdee-184">Holographic Thermal</span></span>

<span data-ttu-id="7fdee-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="7fdee-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="7fdee-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="7fdee-187">Gerenciador de Mapas</span><span class="sxs-lookup"><span data-stu-id="7fdee-187">Map Manager</span></span>

<span data-ttu-id="7fdee-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="7fdee-189">Obtém a lista dos arquivos de mapa disponíveis (. MapX).</span><span class="sxs-lookup"><span data-stu-id="7fdee-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="7fdee-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="7fdee-191">Obtém a lista de arquivos de âncora disponíveis (. ancx).</span><span class="sxs-lookup"><span data-stu-id="7fdee-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="7fdee-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="7fdee-193">Obtém a lista de arquivos de banco de dados de reconstrução espacial disponíveis (. SRDB).</span><span class="sxs-lookup"><span data-stu-id="7fdee-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="7fdee-194">**/API/Holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="7fdee-195">Obtém a lista de âncoras persistentes para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="7fdee-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="7fdee-196">Baixar/carregar/excluir arquivos</span><span class="sxs-lookup"><span data-stu-id="7fdee-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="7fdee-197">**/API/Holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="7fdee-198">Baixa um mapa, âncora ou arquivo de banco de dados de reconstrução espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="7fdee-199">O arquivo deve ter sido carregado ou exportado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7fdee-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="7fdee-200">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-200">Parameters</span></span>
* <span data-ttu-id="7fdee-201">FileName: nome do arquivo a ser baixado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="7fdee-202">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="7fdee-203">**/API/Holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="7fdee-204">Carrega um arquivo de banco de dados de reconstituição de mapa, âncora ou espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="7fdee-205">Depois que um arquivo é carregado, ele pode ser importado posteriormente para ser usado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="7fdee-206">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-206">Parameters</span></span>
* <span data-ttu-id="7fdee-207">File: o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="7fdee-208">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="7fdee-209">**/API/Holographic/mapmanager/Delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="7fdee-210">Exclui um arquivo de banco de dados de mapa, âncora ou reconstituição espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="7fdee-211">O arquivo deve ter sido carregado ou exportado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7fdee-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="7fdee-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-212">Parameters</span></span>
* <span data-ttu-id="7fdee-213">FileName: nome do arquivo a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="7fdee-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="7fdee-214">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="7fdee-215">Exportação</span><span class="sxs-lookup"><span data-stu-id="7fdee-215">Export</span></span>

<span data-ttu-id="7fdee-216">**/API/Holographic/mapmanager/Export (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="7fdee-217">Exporta o mapa atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="7fdee-218">Depois de exportado, ele pode ser baixado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="7fdee-219">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="7fdee-220">**/API/Holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="7fdee-221">Exporta o mapa atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="7fdee-222">Depois de exportado, ele pode ser baixado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="7fdee-223">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="7fdee-224">**/API/Holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="7fdee-225">Exporta o mapa e as âncoras atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="7fdee-226">Depois de exportadas, elas podem ser baixadas.</span><span class="sxs-lookup"><span data-stu-id="7fdee-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="7fdee-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="7fdee-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="7fdee-229">Exporta o mapa e o banco de dados de reconstrução espacial atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="7fdee-230">Depois que eles são exportados, eles podem ser baixados.</span><span class="sxs-lookup"><span data-stu-id="7fdee-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="7fdee-231">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="7fdee-232">Importar</span><span class="sxs-lookup"><span data-stu-id="7fdee-232">Import</span></span>

<span data-ttu-id="7fdee-233">**/API/Holographic/mapmanager/Import (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="7fdee-234">Indica ao sistema qual mapa deve ser usado no momento.</span><span class="sxs-lookup"><span data-stu-id="7fdee-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="7fdee-235">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="7fdee-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="7fdee-236">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-236">Parameters</span></span>
* <span data-ttu-id="7fdee-237">Nome do arquivo: o nome do mapa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="7fdee-238">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="7fdee-239">**/API/Holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="7fdee-240">Indica ao sistema quais âncoras devem ser usadas no momento.</span><span class="sxs-lookup"><span data-stu-id="7fdee-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="7fdee-241">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="7fdee-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="7fdee-242">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-242">Parameters</span></span>
* <span data-ttu-id="7fdee-243">Nome do arquivo: nome das âncoras a serem usadas.</span><span class="sxs-lookup"><span data-stu-id="7fdee-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="7fdee-244">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="7fdee-245">**/API/Holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="7fdee-246">Indica ao sistema qual banco de dados de reconstrução espacial deve ser usado no momento.</span><span class="sxs-lookup"><span data-stu-id="7fdee-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="7fdee-247">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="7fdee-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="7fdee-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-248">Parameters</span></span>
* <span data-ttu-id="7fdee-249">Nome do arquivo: nome do BD de mapeamento espacial a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="7fdee-250">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="7fdee-251">Outro</span><span class="sxs-lookup"><span data-stu-id="7fdee-251">Other</span></span>

<span data-ttu-id="7fdee-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="7fdee-253">Redefina o sistema o banco de dados mapa, âncoras e reconstrução espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="7fdee-254">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7fdee-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="7fdee-255">**/API/Holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="7fdee-256">Obtém o status do sistema, incluindo quais mapas, âncoras e arquivos de banco de dados de reconstrução espacial foram importados pela última vez.</span><span class="sxs-lookup"><span data-stu-id="7fdee-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="7fdee-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="7fdee-257">Mixed Reality Capture</span></span>

<span data-ttu-id="7fdee-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="7fdee-259">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fdee-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="7fdee-260">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="7fdee-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="7fdee-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-261">Parameters</span></span>
* <span data-ttu-id="7fdee-262">filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="7fdee-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="7fdee-263">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="7fdee-263">op : stream</span></span>

<span data-ttu-id="7fdee-264">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="7fdee-265">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fdee-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="7fdee-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-266">Parameters</span></span>
* <span data-ttu-id="7fdee-267">filename: nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="7fdee-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="7fdee-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="7fdee-269">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="7fdee-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="7fdee-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="7fdee-271">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="7fdee-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="7fdee-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-272">Parameters</span></span>
* <span data-ttu-id="7fdee-273">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-274">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-275">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="7fdee-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="7fdee-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="7fdee-277">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7fdee-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="7fdee-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="7fdee-279">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7fdee-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="7fdee-280">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="7fdee-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="7fdee-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="7fdee-282">Obtém o estado da captura de realidade misturada no portal do dispositivo Windows.</span><span class="sxs-lookup"><span data-stu-id="7fdee-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="7fdee-283">\**_Resposta_* _</span><span class="sxs-lookup"><span data-stu-id="7fdee-283">\**_Response_* _</span></span>

<span data-ttu-id="7fdee-284">A resposta contém uma propriedade JSON que indica se o portal do dispositivo Windows está gravando vídeo ou não.</span><span class="sxs-lookup"><span data-stu-id="7fdee-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="7fdee-285">_ */API/Holographic/MRC/Thumbnail (Get)*\*</span><span class="sxs-lookup"><span data-stu-id="7fdee-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="7fdee-286">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="7fdee-287">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-287">Parameters</span></span>
* <span data-ttu-id="7fdee-288">filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="7fdee-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="7fdee-289">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="7fdee-290">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7fdee-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="7fdee-291">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-291">Parameters</span></span>
* <span data-ttu-id="7fdee-292">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-293">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-294">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-295">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-296">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="7fdee-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="7fdee-297">Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="7fdee-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="7fdee-298">vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="7fdee-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="7fdee-299">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="7fdee-300">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7fdee-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="7fdee-301">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7fdee-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="7fdee-302">Devido ao isolamento de auto-retorno, você não pode se conectar ao streaming de realidade misturada de dentro de um aplicativo em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fdee-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="7fdee-303">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="7fdee-304">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="7fdee-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="7fdee-305">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="7fdee-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="7fdee-306">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="7fdee-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="7fdee-307">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="7fdee-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="7fdee-308">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="7fdee-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="7fdee-309">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="7fdee-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="7fdee-310">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="7fdee-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="7fdee-311">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="7fdee-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="7fdee-312">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="7fdee-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="7fdee-313">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="7fdee-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="7fdee-314">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="7fdee-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="7fdee-315">**/API/Holographic/Stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="7fdee-316">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="7fdee-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="7fdee-317">**/API/Holographic/Stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="7fdee-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="7fdee-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="7fdee-319">**/API/Holographic/Stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="7fdee-320">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="7fdee-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="7fdee-321">**/API/Holographic/Stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="7fdee-322">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="7fdee-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="7fdee-323">Rede</span><span class="sxs-lookup"><span data-stu-id="7fdee-323">Networking</span></span>

<span data-ttu-id="7fdee-324">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="7fdee-325">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="7fdee-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="7fdee-326">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="7fdee-326">OS Information</span></span>

<span data-ttu-id="7fdee-327">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="7fdee-328">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="7fdee-328">Gets operating system information</span></span>

<span data-ttu-id="7fdee-329">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="7fdee-330">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="7fdee-330">Gets the machine name</span></span>

<span data-ttu-id="7fdee-331">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="7fdee-332">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="7fdee-332">Sets the machine name</span></span>

<span data-ttu-id="7fdee-333">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-333">Parameters</span></span>
* <span data-ttu-id="7fdee-334">Nome: novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="7fdee-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="7fdee-335">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="7fdee-335">Perception Simulation Control</span></span>

<span data-ttu-id="7fdee-336">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="7fdee-337">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="7fdee-337">Get the simulation mode</span></span>

<span data-ttu-id="7fdee-338">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="7fdee-339">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="7fdee-339">Set the simulation mode</span></span>

<span data-ttu-id="7fdee-340">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-340">Parameters</span></span>
* <span data-ttu-id="7fdee-341">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="7fdee-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="7fdee-342">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="7fdee-343">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="7fdee-343">Delete a control stream.</span></span>

<span data-ttu-id="7fdee-344">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="7fdee-345">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="7fdee-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="7fdee-346">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="7fdee-347">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="7fdee-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="7fdee-348">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="7fdee-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="7fdee-349">**/API/Holographic/Simulation/display/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="7fdee-350">Solicite um fluxo de vídeo de simulação contendo o conteúdo renderizado para a exibição do sistema quando estiver no modo ' Simulation '.</span><span class="sxs-lookup"><span data-stu-id="7fdee-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="7fdee-351">Um cabeçalho de descritor de formato simples será enviado inicialmente, seguido de texturas codificadas H. 264, cada um precedido por um cabeçalho que indica o índice de olho e o tamanho da textura.</span><span class="sxs-lookup"><span data-stu-id="7fdee-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="7fdee-352">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="7fdee-352">Perception Simulation Playback</span></span>

<span data-ttu-id="7fdee-353">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="7fdee-354">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-354">Delete a recording.</span></span>

<span data-ttu-id="7fdee-355">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-355">Parameters</span></span>
* <span data-ttu-id="7fdee-356">gravação: o nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="7fdee-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="7fdee-357">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="7fdee-358">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-358">Upload a recording.</span></span>

<span data-ttu-id="7fdee-359">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="7fdee-360">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="7fdee-360">Get all recordings.</span></span>

<span data-ttu-id="7fdee-361">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="7fdee-362">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="7fdee-363">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-363">Parameters</span></span>
* <span data-ttu-id="7fdee-364">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-364">recording : Name of recording.</span></span>

<span data-ttu-id="7fdee-365">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="7fdee-366">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-366">Unload a recording.</span></span>

<span data-ttu-id="7fdee-367">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-367">Parameters</span></span>
* <span data-ttu-id="7fdee-368">gravação: nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="7fdee-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="7fdee-369">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="7fdee-370">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-370">Load a recording.</span></span>

<span data-ttu-id="7fdee-371">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-371">Parameters</span></span>
* <span data-ttu-id="7fdee-372">gravação: o nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="7fdee-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="7fdee-373">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="7fdee-374">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="7fdee-374">Get all loaded recordings.</span></span>

<span data-ttu-id="7fdee-375">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="7fdee-376">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-376">Pause a recording.</span></span>

<span data-ttu-id="7fdee-377">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-377">Parameters</span></span>
* <span data-ttu-id="7fdee-378">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-378">recording : Name of recording.</span></span>

<span data-ttu-id="7fdee-379">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="7fdee-380">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-380">Play a recording.</span></span>

<span data-ttu-id="7fdee-381">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-381">Parameters</span></span>
* <span data-ttu-id="7fdee-382">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-382">recording : Name of recording.</span></span>

<span data-ttu-id="7fdee-383">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="7fdee-384">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-384">Stop a recording.</span></span>

<span data-ttu-id="7fdee-385">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-385">Parameters</span></span>
* <span data-ttu-id="7fdee-386">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-386">recording : Name of recording.</span></span>

<span data-ttu-id="7fdee-387">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="7fdee-388">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="7fdee-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="7fdee-389">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-389">Parameters</span></span>
* <span data-ttu-id="7fdee-390">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="7fdee-391">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="7fdee-391">Perception Simulation Recording</span></span>

<span data-ttu-id="7fdee-392">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="7fdee-393">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-393">Start a recording.</span></span> <span data-ttu-id="7fdee-394">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="7fdee-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="7fdee-395">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="7fdee-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="7fdee-396">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-396">Parameters</span></span>
* <span data-ttu-id="7fdee-397">Cabeçalho: Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7fdee-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="7fdee-398">Hands: Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="7fdee-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="7fdee-399">spatialMapping: Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="7fdee-400">ambiente: Defina como 1 para gravar dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="7fdee-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="7fdee-401">Nome: o nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-401">name : Name of the recording.</span></span>
* <span data-ttu-id="7fdee-402">singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="7fdee-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="7fdee-403">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="7fdee-404">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="7fdee-404">Get recording state.</span></span>

<span data-ttu-id="7fdee-405">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="7fdee-406">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="7fdee-406">Stop the current recording.</span></span> <span data-ttu-id="7fdee-407">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7fdee-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="7fdee-408">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="7fdee-408">Performance data</span></span>

<span data-ttu-id="7fdee-409">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="7fdee-410">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="7fdee-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="7fdee-411">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-411">Return data</span></span>
* <span data-ttu-id="7fdee-412">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="7fdee-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="7fdee-413">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="7fdee-414">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="7fdee-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="7fdee-415">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-415">Return data</span></span>
* <span data-ttu-id="7fdee-416">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="7fdee-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="7fdee-417">Energia</span><span class="sxs-lookup"><span data-stu-id="7fdee-417">Power</span></span>

<span data-ttu-id="7fdee-418">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="7fdee-419">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="7fdee-419">Gets the current battery state</span></span>

<span data-ttu-id="7fdee-420">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="7fdee-421">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="7fdee-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="7fdee-422">Controle remoto</span><span class="sxs-lookup"><span data-stu-id="7fdee-422">Remote Control</span></span>

<span data-ttu-id="7fdee-423">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="7fdee-424">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="7fdee-424">Restarts the target device</span></span>

<span data-ttu-id="7fdee-425">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="7fdee-426">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="7fdee-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="7fdee-427">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="7fdee-427">Task Manager</span></span>

<span data-ttu-id="7fdee-428">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="7fdee-429">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="7fdee-429">Stops a modern app</span></span>

<span data-ttu-id="7fdee-430">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-430">Parameters</span></span>
* <span data-ttu-id="7fdee-431">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="7fdee-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="7fdee-432">forcestop: forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="7fdee-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="7fdee-433">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="7fdee-434">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="7fdee-434">Starts a modern app</span></span>

<span data-ttu-id="7fdee-435">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-435">Parameters</span></span>
* <span data-ttu-id="7fdee-436">AppID: PRAID do aplicativo a ser iniciado, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="7fdee-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="7fdee-437">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="7fdee-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="7fdee-438">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="7fdee-438">WiFi Management</span></span>

<span data-ttu-id="7fdee-439">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="7fdee-440">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="7fdee-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="7fdee-441">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-441">Return data</span></span>
* <span data-ttu-id="7fdee-442">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="7fdee-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="7fdee-443">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="7fdee-444">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="7fdee-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="7fdee-445">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-445">Parameters</span></span>
* <span data-ttu-id="7fdee-446">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="7fdee-446">interface : network interface guid</span></span>
* <span data-ttu-id="7fdee-447">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="7fdee-447">profile : profile name</span></span>

<span data-ttu-id="7fdee-448">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="7fdee-449">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="7fdee-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="7fdee-450">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-450">Parameters</span></span>
* <span data-ttu-id="7fdee-451">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="7fdee-451">interface : network interface guid</span></span>

<span data-ttu-id="7fdee-452">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-452">Return data</span></span>
* <span data-ttu-id="7fdee-453">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="7fdee-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="7fdee-454">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="7fdee-455">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="7fdee-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="7fdee-456">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-456">Parameters</span></span>
* <span data-ttu-id="7fdee-457">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="7fdee-457">interface : network interface guid</span></span>
* <span data-ttu-id="7fdee-458">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="7fdee-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="7fdee-459">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="7fdee-459">op : connect or disconnect</span></span>
* <span data-ttu-id="7fdee-460">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="7fdee-460">createprofile : yes or no</span></span>
* <span data-ttu-id="7fdee-461">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="7fdee-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="7fdee-462">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="7fdee-462">Windows Performance Recorder</span></span>

<span data-ttu-id="7fdee-463">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="7fdee-464">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="7fdee-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="7fdee-465">Carga útil</span><span class="sxs-lookup"><span data-stu-id="7fdee-465">Payload</span></span>
* <span data-ttu-id="7fdee-466">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="7fdee-466">multi-part conforming http body</span></span>

<span data-ttu-id="7fdee-467">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-467">Return data</span></span>
* <span data-ttu-id="7fdee-468">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="7fdee-468">Returns the WPR session status.</span></span>

<span data-ttu-id="7fdee-469">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="7fdee-470">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="7fdee-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="7fdee-471">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-471">Return data</span></span>
* <span data-ttu-id="7fdee-472">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="7fdee-472">WPR session status.</span></span>

<span data-ttu-id="7fdee-473">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="7fdee-474">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="7fdee-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="7fdee-475">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-475">Return data</span></span>
* <span data-ttu-id="7fdee-476">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="7fdee-476">Returns the trace ETL file</span></span>

<span data-ttu-id="7fdee-477">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="7fdee-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="7fdee-478">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="7fdee-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="7fdee-479">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdee-479">Parameters</span></span>
* <span data-ttu-id="7fdee-480">Perfil: nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="7fdee-480">profile : Profile name.</span></span> <span data-ttu-id="7fdee-481">Os perfis disponíveis são armazenados em perfprofiles/profiles.jsem</span><span class="sxs-lookup"><span data-stu-id="7fdee-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="7fdee-482">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="7fdee-482">Return data</span></span>
* <span data-ttu-id="7fdee-483">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="7fdee-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fdee-484">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fdee-484">See also</span></span>
* [<span data-ttu-id="7fdee-485">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="7fdee-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="7fdee-486">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="7fdee-486">Device Portal core API reference (UWP)</span></span>](/windows/uwp/debug-test-perf/device-portal-api-core)