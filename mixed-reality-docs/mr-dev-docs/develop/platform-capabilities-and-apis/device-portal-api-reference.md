---
title: Referência de API do portal de dispositivos
description: Referência de API para o portal de dispositivo do Windows no HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677965"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="f8184-104">Referência de API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f8184-104">Device portal API reference</span></span>

<span data-ttu-id="f8184-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="f8184-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="f8184-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f8184-106">App deloyment</span></span>

<span data-ttu-id="f8184-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="f8184-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f8184-108">Uninstalls an app</span></span>

<span data-ttu-id="f8184-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-109">Parameters</span></span>
* <span data-ttu-id="f8184-110">Package: nome de arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="f8184-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="f8184-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="f8184-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f8184-112">Installs an App</span></span>

<span data-ttu-id="f8184-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-113">Parameters</span></span>
* <span data-ttu-id="f8184-114">Package: nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="f8184-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="f8184-115">Carga útil</span><span class="sxs-lookup"><span data-stu-id="f8184-115">Payload</span></span>
* <span data-ttu-id="f8184-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="f8184-116">multi-part conforming http body</span></span>

<span data-ttu-id="f8184-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="f8184-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="f8184-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="f8184-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-119">Return data</span></span>
* <span data-ttu-id="f8184-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="f8184-120">List of installed packages with details</span></span>

<span data-ttu-id="f8184-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="f8184-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="f8184-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="f8184-123">Despejar coleção</span><span class="sxs-lookup"><span data-stu-id="f8184-123">Dump collection</span></span>

<span data-ttu-id="f8184-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="f8184-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="f8184-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-126">Parameters</span></span>
* <span data-ttu-id="f8184-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="f8184-127">packageFullname : package name</span></span>

<span data-ttu-id="f8184-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="f8184-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="f8184-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-130">Parameters</span></span>
* <span data-ttu-id="f8184-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="f8184-131">packageFullname : package name</span></span>

<span data-ttu-id="f8184-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="f8184-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="f8184-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-134">Parameters</span></span>
* <span data-ttu-id="f8184-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="f8184-135">packageFullname : package name</span></span>

<span data-ttu-id="f8184-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="f8184-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="f8184-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-138">Parameters</span></span>
* <span data-ttu-id="f8184-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="f8184-139">packageFullname : package name</span></span>
* <span data-ttu-id="f8184-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="f8184-140">fileName : dump file name</span></span>

<span data-ttu-id="f8184-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="f8184-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="f8184-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-143">Parameters</span></span>
* <span data-ttu-id="f8184-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="f8184-144">packageFullname : package name</span></span>
* <span data-ttu-id="f8184-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="f8184-145">fileName : dump file name</span></span>

<span data-ttu-id="f8184-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-146">Return data</span></span>
* <span data-ttu-id="f8184-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="f8184-147">Dump file.</span></span> <span data-ttu-id="f8184-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f8184-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="f8184-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="f8184-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="f8184-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="f8184-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-151">Return data</span></span>
* <span data-ttu-id="f8184-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="f8184-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="f8184-153">ETW</span><span class="sxs-lookup"><span data-stu-id="f8184-153">ETW</span></span>

<span data-ttu-id="f8184-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="f8184-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="f8184-155">Enumerates registered providers</span></span>

<span data-ttu-id="f8184-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-156">Return data</span></span>
* <span data-ttu-id="f8184-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="f8184-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="f8184-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="f8184-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="f8184-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="f8184-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="f8184-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-160">Return data</span></span>
* <span data-ttu-id="f8184-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="f8184-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="f8184-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="f8184-162">Holographic OS</span></span>

<span data-ttu-id="f8184-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="f8184-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="f8184-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="f8184-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="f8184-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="f8184-166">Returns the states of all services running.</span></span>

<span data-ttu-id="f8184-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="f8184-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="f8184-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="f8184-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="f8184-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="f8184-170">Sets the IPD</span></span>

<span data-ttu-id="f8184-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-171">Parameters</span></span>
* <span data-ttu-id="f8184-172">IPD: novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="f8184-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="f8184-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="f8184-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="f8184-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="f8184-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="f8184-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="f8184-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="f8184-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-177">Parameters</span></span>
* <span data-ttu-id="f8184-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="f8184-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="f8184-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="f8184-179">Holographic Perception</span></span>

<span data-ttu-id="f8184-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="f8184-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="f8184-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="f8184-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="f8184-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-182">Parameters</span></span>
* <span data-ttu-id="f8184-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="f8184-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="f8184-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="f8184-184">Holographic Thermal</span></span>

<span data-ttu-id="f8184-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="f8184-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="f8184-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="f8184-187">Gerenciador de Mapas</span><span class="sxs-lookup"><span data-stu-id="f8184-187">Map Manager</span></span>

<span data-ttu-id="f8184-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="f8184-189">Obtém a lista dos arquivos de mapa disponíveis (. MapX).</span><span class="sxs-lookup"><span data-stu-id="f8184-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="f8184-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="f8184-191">Obtém a lista de arquivos de âncora disponíveis (. ancx).</span><span class="sxs-lookup"><span data-stu-id="f8184-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="f8184-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="f8184-193">Obtém a lista de arquivos de banco de dados de reconstrução espacial disponíveis (. SRDB).</span><span class="sxs-lookup"><span data-stu-id="f8184-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="f8184-194">**/API/Holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="f8184-195">Obtém a lista de âncoras persistentes para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="f8184-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="f8184-196">Baixar/carregar/excluir arquivos</span><span class="sxs-lookup"><span data-stu-id="f8184-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="f8184-197">**/API/Holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="f8184-198">Baixa um mapa, âncora ou arquivo de banco de dados de reconstrução espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="f8184-199">O arquivo deve ter sido carregado ou exportado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f8184-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="f8184-200">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-200">Parameters</span></span>
* <span data-ttu-id="f8184-201">FileName: nome do arquivo a ser baixado.</span><span class="sxs-lookup"><span data-stu-id="f8184-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="f8184-202">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="f8184-203">**/API/Holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="f8184-204">Carrega um arquivo de banco de dados de reconstituição de mapa, âncora ou espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="f8184-205">Depois que um arquivo é carregado, ele pode ser importado posteriormente para ser usado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="f8184-206">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-206">Parameters</span></span>
* <span data-ttu-id="f8184-207">File: o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="f8184-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="f8184-208">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-208">Example:</span></span>
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

<span data-ttu-id="f8184-209">**/API/Holographic/mapmanager/Delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="f8184-210">Exclui um arquivo de banco de dados de mapa, âncora ou reconstituição espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="f8184-211">O arquivo deve ter sido carregado ou exportado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f8184-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="f8184-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-212">Parameters</span></span>
* <span data-ttu-id="f8184-213">FileName: nome do arquivo a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="f8184-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="f8184-214">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="f8184-215">Exportação</span><span class="sxs-lookup"><span data-stu-id="f8184-215">Export</span></span>

<span data-ttu-id="f8184-216">**/API/Holographic/mapmanager/Export (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="f8184-217">Exporta o mapa atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="f8184-218">Depois de exportado, ele pode ser baixado.</span><span class="sxs-lookup"><span data-stu-id="f8184-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="f8184-219">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="f8184-220">**/API/Holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="f8184-221">Exporta o mapa atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="f8184-222">Depois de exportado, ele pode ser baixado.</span><span class="sxs-lookup"><span data-stu-id="f8184-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="f8184-223">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="f8184-224">**/API/Holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="f8184-225">Exporta o mapa e as âncoras atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="f8184-226">Depois de exportadas, elas podem ser baixadas.</span><span class="sxs-lookup"><span data-stu-id="f8184-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="f8184-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="f8184-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="f8184-229">Exporta o mapa e o banco de dados de reconstrução espacial atualmente em uso pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="f8184-230">Depois que eles são exportados, eles podem ser baixados.</span><span class="sxs-lookup"><span data-stu-id="f8184-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="f8184-231">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="f8184-232">Importar</span><span class="sxs-lookup"><span data-stu-id="f8184-232">Import</span></span>

<span data-ttu-id="f8184-233">**/API/Holographic/mapmanager/Import (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="f8184-234">Indica ao sistema qual mapa deve ser usado no momento.</span><span class="sxs-lookup"><span data-stu-id="f8184-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="f8184-235">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="f8184-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="f8184-236">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-236">Parameters</span></span>
* <span data-ttu-id="f8184-237">Nome do arquivo: o nome do mapa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f8184-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="f8184-238">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="f8184-239">**/API/Holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="f8184-240">Indica ao sistema quais âncoras devem ser usadas no momento.</span><span class="sxs-lookup"><span data-stu-id="f8184-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="f8184-241">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="f8184-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="f8184-242">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-242">Parameters</span></span>
* <span data-ttu-id="f8184-243">Nome do arquivo: nome das âncoras a serem usadas.</span><span class="sxs-lookup"><span data-stu-id="f8184-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="f8184-244">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="f8184-245">**/API/Holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="f8184-246">Indica ao sistema qual banco de dados de reconstrução espacial deve ser usado no momento.</span><span class="sxs-lookup"><span data-stu-id="f8184-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="f8184-247">Pode ser chamado em arquivos que foram exportados ou carregados.</span><span class="sxs-lookup"><span data-stu-id="f8184-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="f8184-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-248">Parameters</span></span>
* <span data-ttu-id="f8184-249">Nome do arquivo: nome do BD de mapeamento espacial a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f8184-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="f8184-250">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="f8184-251">Outro</span><span class="sxs-lookup"><span data-stu-id="f8184-251">Other</span></span>

<span data-ttu-id="f8184-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="f8184-253">Redefina o sistema o banco de dados mapa, âncoras e reconstrução espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="f8184-254">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="f8184-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="f8184-255">**/API/Holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="f8184-256">Obtém o status do sistema, incluindo quais mapas, âncoras e arquivos de banco de dados de reconstrução espacial foram importados pela última vez.</span><span class="sxs-lookup"><span data-stu-id="f8184-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="f8184-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="f8184-257">Mixed Reality Capture</span></span>

<span data-ttu-id="f8184-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="f8184-259">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f8184-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="f8184-260">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="f8184-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="f8184-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-261">Parameters</span></span>
* <span data-ttu-id="f8184-262">filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="f8184-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="f8184-263">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="f8184-263">op : stream</span></span>

<span data-ttu-id="f8184-264">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="f8184-265">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f8184-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="f8184-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-266">Parameters</span></span>
* <span data-ttu-id="f8184-267">filename: nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="f8184-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="f8184-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="f8184-269">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="f8184-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="f8184-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="f8184-271">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="f8184-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="f8184-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-272">Parameters</span></span>
* <span data-ttu-id="f8184-273">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-274">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-275">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="f8184-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="f8184-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="f8184-277">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f8184-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="f8184-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="f8184-279">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f8184-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="f8184-280">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="f8184-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="f8184-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="f8184-282">Obtém o estado da captura de realidade misturada no portal do dispositivo Windows.</span><span class="sxs-lookup"><span data-stu-id="f8184-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="f8184-283">\**_Resposta_* _</span><span class="sxs-lookup"><span data-stu-id="f8184-283">\**_Response_* _</span></span>

<span data-ttu-id="f8184-284">A resposta contém uma propriedade JSON que indica se o portal do dispositivo Windows está gravando vídeo ou não.</span><span class="sxs-lookup"><span data-stu-id="f8184-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="f8184-285">_ */API/Holographic/MRC/Thumbnail (Get)*\*</span><span class="sxs-lookup"><span data-stu-id="f8184-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="f8184-286">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="f8184-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="f8184-287">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-287">Parameters</span></span>
* <span data-ttu-id="f8184-288">filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="f8184-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="f8184-289">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="f8184-290">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f8184-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="f8184-291">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-291">Parameters</span></span>
* <span data-ttu-id="f8184-292">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-293">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-294">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-295">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-296">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="f8184-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="f8184-297">Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="f8184-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="f8184-298">vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="f8184-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="f8184-299">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="f8184-300">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f8184-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="f8184-301">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f8184-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="f8184-302">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="f8184-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="f8184-303">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="f8184-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="f8184-304">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="f8184-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="f8184-305">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="f8184-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="f8184-306">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="f8184-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="f8184-307">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="f8184-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="f8184-308">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="f8184-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="f8184-309">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="f8184-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="f8184-310">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f8184-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="f8184-311">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="f8184-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="f8184-312">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="f8184-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="f8184-313">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="f8184-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="f8184-314">**/API/Holographic/Stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="f8184-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="f8184-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="f8184-316">**/API/Holographic/Stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="f8184-317">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="f8184-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="f8184-318">**/API/Holographic/Stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="f8184-319">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="f8184-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="f8184-320">**/API/Holographic/Stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="f8184-321">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="f8184-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="f8184-322">Rede</span><span class="sxs-lookup"><span data-stu-id="f8184-322">Networking</span></span>

<span data-ttu-id="f8184-323">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="f8184-324">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="f8184-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="f8184-325">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="f8184-325">OS Information</span></span>

<span data-ttu-id="f8184-326">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="f8184-327">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="f8184-327">Gets operating system information</span></span>

<span data-ttu-id="f8184-328">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="f8184-329">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="f8184-329">Gets the machine name</span></span>

<span data-ttu-id="f8184-330">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="f8184-331">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="f8184-331">Sets the machine name</span></span>

<span data-ttu-id="f8184-332">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-332">Parameters</span></span>
* <span data-ttu-id="f8184-333">Nome: novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="f8184-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="f8184-334">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="f8184-334">Perception Simulation Control</span></span>

<span data-ttu-id="f8184-335">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="f8184-336">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="f8184-336">Get the simulation mode</span></span>

<span data-ttu-id="f8184-337">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="f8184-338">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="f8184-338">Set the simulation mode</span></span>

<span data-ttu-id="f8184-339">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-339">Parameters</span></span>
* <span data-ttu-id="f8184-340">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="f8184-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="f8184-341">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="f8184-342">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="f8184-342">Delete a control stream.</span></span>

<span data-ttu-id="f8184-343">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="f8184-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="f8184-344">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="f8184-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="f8184-345">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="f8184-346">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="f8184-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="f8184-347">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="f8184-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="f8184-348">**/API/Holographic/Simulation/display/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="f8184-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="f8184-349">Solicite um fluxo de vídeo de simulação contendo o conteúdo renderizado para a exibição do sistema quando estiver no modo ' Simulation '.</span><span class="sxs-lookup"><span data-stu-id="f8184-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="f8184-350">Um cabeçalho de descritor de formato simples será enviado inicialmente, seguido de texturas codificadas H. 264, cada um precedido por um cabeçalho que indica o índice de olho e o tamanho da textura.</span><span class="sxs-lookup"><span data-stu-id="f8184-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="f8184-351">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="f8184-351">Perception Simulation Playback</span></span>

<span data-ttu-id="f8184-352">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="f8184-353">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-353">Delete a recording.</span></span>

<span data-ttu-id="f8184-354">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-354">Parameters</span></span>
* <span data-ttu-id="f8184-355">gravação: o nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="f8184-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="f8184-356">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="f8184-357">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-357">Upload a recording.</span></span>

<span data-ttu-id="f8184-358">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="f8184-359">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="f8184-359">Get all recordings.</span></span>

<span data-ttu-id="f8184-360">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="f8184-361">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="f8184-362">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-362">Parameters</span></span>
* <span data-ttu-id="f8184-363">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-363">recording : Name of recording.</span></span>

<span data-ttu-id="f8184-364">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="f8184-365">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-365">Unload a recording.</span></span>

<span data-ttu-id="f8184-366">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-366">Parameters</span></span>
* <span data-ttu-id="f8184-367">gravação: nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="f8184-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="f8184-368">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="f8184-369">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-369">Load a recording.</span></span>

<span data-ttu-id="f8184-370">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-370">Parameters</span></span>
* <span data-ttu-id="f8184-371">gravação: o nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="f8184-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="f8184-372">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="f8184-373">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="f8184-373">Get all loaded recordings.</span></span>

<span data-ttu-id="f8184-374">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="f8184-375">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-375">Pause a recording.</span></span>

<span data-ttu-id="f8184-376">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-376">Parameters</span></span>
* <span data-ttu-id="f8184-377">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-377">recording : Name of recording.</span></span>

<span data-ttu-id="f8184-378">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="f8184-379">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-379">Play a recording.</span></span>

<span data-ttu-id="f8184-380">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-380">Parameters</span></span>
* <span data-ttu-id="f8184-381">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-381">recording : Name of recording.</span></span>

<span data-ttu-id="f8184-382">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="f8184-383">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-383">Stop a recording.</span></span>

<span data-ttu-id="f8184-384">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-384">Parameters</span></span>
* <span data-ttu-id="f8184-385">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-385">recording : Name of recording.</span></span>

<span data-ttu-id="f8184-386">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="f8184-387">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="f8184-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="f8184-388">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-388">Parameters</span></span>
* <span data-ttu-id="f8184-389">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="f8184-390">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="f8184-390">Perception Simulation Recording</span></span>

<span data-ttu-id="f8184-391">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="f8184-392">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-392">Start a recording.</span></span> <span data-ttu-id="f8184-393">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="f8184-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="f8184-394">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="f8184-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="f8184-395">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-395">Parameters</span></span>
* <span data-ttu-id="f8184-396">Cabeçalho: Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f8184-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="f8184-397">Hands: Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="f8184-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="f8184-398">spatialMapping: Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="f8184-399">ambiente: Defina como 1 para gravar dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="f8184-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="f8184-400">Nome: o nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-400">name : Name of the recording.</span></span>
* <span data-ttu-id="f8184-401">singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="f8184-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="f8184-402">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="f8184-403">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="f8184-403">Get recording state.</span></span>

<span data-ttu-id="f8184-404">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="f8184-405">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="f8184-405">Stop the current recording.</span></span> <span data-ttu-id="f8184-406">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f8184-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="f8184-407">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="f8184-407">Performance data</span></span>

<span data-ttu-id="f8184-408">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="f8184-409">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="f8184-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="f8184-410">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-410">Return data</span></span>
* <span data-ttu-id="f8184-411">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="f8184-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="f8184-412">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="f8184-413">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="f8184-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="f8184-414">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-414">Return data</span></span>
* <span data-ttu-id="f8184-415">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="f8184-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="f8184-416">Energia</span><span class="sxs-lookup"><span data-stu-id="f8184-416">Power</span></span>

<span data-ttu-id="f8184-417">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="f8184-418">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="f8184-418">Gets the current battery state</span></span>

<span data-ttu-id="f8184-419">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="f8184-420">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="f8184-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="f8184-421">Controle remoto</span><span class="sxs-lookup"><span data-stu-id="f8184-421">Remote Control</span></span>

<span data-ttu-id="f8184-422">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="f8184-423">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="f8184-423">Restarts the target device</span></span>

<span data-ttu-id="f8184-424">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="f8184-425">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="f8184-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="f8184-426">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="f8184-426">Task Manager</span></span>

<span data-ttu-id="f8184-427">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="f8184-428">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="f8184-428">Stops a modern app</span></span>

<span data-ttu-id="f8184-429">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-429">Parameters</span></span>
* <span data-ttu-id="f8184-430">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="f8184-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="f8184-431">forcestop: forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="f8184-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="f8184-432">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="f8184-433">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="f8184-433">Starts a modern app</span></span>

<span data-ttu-id="f8184-434">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-434">Parameters</span></span>
* <span data-ttu-id="f8184-435">AppID: PRAID do aplicativo a ser iniciado, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="f8184-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="f8184-436">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="f8184-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="f8184-437">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="f8184-437">WiFi Management</span></span>

<span data-ttu-id="f8184-438">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="f8184-439">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="f8184-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="f8184-440">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-440">Return data</span></span>
* <span data-ttu-id="f8184-441">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="f8184-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="f8184-442">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="f8184-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="f8184-443">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="f8184-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="f8184-444">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-444">Parameters</span></span>
* <span data-ttu-id="f8184-445">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="f8184-445">interface : network interface guid</span></span>
* <span data-ttu-id="f8184-446">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="f8184-446">profile : profile name</span></span>

<span data-ttu-id="f8184-447">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="f8184-448">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="f8184-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="f8184-449">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-449">Parameters</span></span>
* <span data-ttu-id="f8184-450">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="f8184-450">interface : network interface guid</span></span>

<span data-ttu-id="f8184-451">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-451">Return data</span></span>
* <span data-ttu-id="f8184-452">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="f8184-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="f8184-453">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="f8184-454">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="f8184-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="f8184-455">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-455">Parameters</span></span>
* <span data-ttu-id="f8184-456">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="f8184-456">interface : network interface guid</span></span>
* <span data-ttu-id="f8184-457">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="f8184-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="f8184-458">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="f8184-458">op : connect or disconnect</span></span>
* <span data-ttu-id="f8184-459">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="f8184-459">createprofile : yes or no</span></span>
* <span data-ttu-id="f8184-460">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="f8184-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="f8184-461">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="f8184-461">Windows Performance Recorder</span></span>

<span data-ttu-id="f8184-462">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="f8184-463">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="f8184-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="f8184-464">Carga útil</span><span class="sxs-lookup"><span data-stu-id="f8184-464">Payload</span></span>
* <span data-ttu-id="f8184-465">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="f8184-465">multi-part conforming http body</span></span>

<span data-ttu-id="f8184-466">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-466">Return data</span></span>
* <span data-ttu-id="f8184-467">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="f8184-467">Returns the WPR session status.</span></span>

<span data-ttu-id="f8184-468">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="f8184-469">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="f8184-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="f8184-470">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-470">Return data</span></span>
* <span data-ttu-id="f8184-471">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="f8184-471">WPR session status.</span></span>

<span data-ttu-id="f8184-472">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="f8184-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="f8184-473">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="f8184-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="f8184-474">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-474">Return data</span></span>
* <span data-ttu-id="f8184-475">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="f8184-475">Returns the trace ETL file</span></span>

<span data-ttu-id="f8184-476">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="f8184-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="f8184-477">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="f8184-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="f8184-478">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8184-478">Parameters</span></span>
* <span data-ttu-id="f8184-479">Perfil: nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="f8184-479">profile : Profile name.</span></span> <span data-ttu-id="f8184-480">Os perfis disponíveis são armazenados em perfprofiles/profiles.jsem</span><span class="sxs-lookup"><span data-stu-id="f8184-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="f8184-481">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="f8184-481">Return data</span></span>
* <span data-ttu-id="f8184-482">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="f8184-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8184-483">Veja também</span><span class="sxs-lookup"><span data-stu-id="f8184-483">See also</span></span>
* [<span data-ttu-id="f8184-484">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="f8184-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="f8184-485">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="f8184-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
