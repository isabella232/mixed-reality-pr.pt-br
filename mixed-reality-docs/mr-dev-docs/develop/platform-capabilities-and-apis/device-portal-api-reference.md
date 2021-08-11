---
title: Referência de API do portal de dispositivos
description: Mantenha-se atualizado sobre a API Windows Portal de Dispositivos para HoloLens desenvolvimento.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, Windows Portal de Dispositivos, API, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 6b41c569917150c303da933a75d354f574fb579ba676dac281e9cde2bfc59818
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207834"
---
# <a name="device-portal-api-reference"></a>Referência de API do portal de dispositivos

Tudo no [Windows Portal de Dispositivos](using-the-windows-device-portal.md) é criado com base nas APIs REST que você pode usar para acessar os dados e controlar seu dispositivo programaticamente.

## <a name="app-deloyment"></a>Desalocar o aplicativo

**/api/app/packagemanager/package (DELETE)**

Desinstala um aplicativo

Parâmetros
* package : nome do arquivo do pacote a ser desinstalado.

**/api/app/packagemanager/package (POST)**

Instala um aplicativo

Parâmetros
* package : nome do arquivo do pacote a ser instalado.

Carga útil
* corpo http em conformidade com várias partes

**/api/app/packagemanager/packages (GET)**

Recupera a lista de aplicativos instalados no sistema, com detalhes

Retornar dados
* Lista de pacotes instalados com detalhes

**/api/app/packagemanager/state (GET)**

Obtém o status da instalação do aplicativo em andamento

## <a name="dump-collection"></a>Coleta de despejo

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Desabilita a coleta de despejo de falha para um aplicativo com sideload

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashcontrol (GET)**

Obtém configurações para coleta de despejo de falha de aplicativos com sideload

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashcontrol (POST)**

Habilita e define as configurações de controle de despejo para um aplicativo com sideload

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashdump (DELETE)**

Exclui um despejo de falha para um aplicativo com sideload

Parâmetros
* packageFullname: nome do pacote
* fileName: nome do arquivo de despejo

**/api/debug/dump/usermode/crashdump (GET)**

Recupera um despejo de falha para um aplicativo com sideload

Parâmetros
* packageFullname: nome do pacote
* fileName: nome do arquivo de despejo

Retornar dados
* Arquivo de despejo. Inspecionar com WinDbg ou Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Retorna a lista de todos os despejos de falha para aplicativos com sideload

Retornar dados
* Lista de despejos de falha por aplicativo carregado lado a lado

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

Enumera provedores registrados

Retornar dados
* Lista de provedores, nome amigável e GUID

**/api/etw/session/realtime (GET/WebSocket)**

Cria uma sessão ETW em tempo real; gerenciado em um websocket.

Retornar dados
* Eventos ETW dos provedores habilitados

## <a name="holographic-os"></a>Sistema operacional holográfico

**/api/holographic/os/etw/customproviders (GET)**

Retorna uma lista de HoloLens ETW específicos que não estão registrados com o sistema

**/api/holographic/os/services (GET)**

Retorna os estados de todos os serviços em execução.

**/api/holographic/os/settings/ipd (GET)**

Obtém o IPD armazenado (distância interpupária) em milímetros

**/api/holographic/os/settings/ipd (POST)**

Define o IPD

Parâmetros
* ipd: novo valor ipD a ser definido em milímetros

**/api/holographic/os/webmanagement/settings/https (GET)**

Obter requisitos de HTTPS para o Device Portal

**/api/holographic/os/webmanagement/settings/https (POST)**

Define os requisitos de HTTPS para o Portal de Dispositivos

Parâmetros
* obrigatório: sim, não ou padrão

## <a name="holographic-perception"></a>Percepção holográfica

**/api/holographic/perception/client (GET/WebSocket)**

Aceita atualizações do websocket e executa um cliente de percepção que envia atualizações a 30 fps.

Parâmetros
* clientmode: "active" força o modo de acompanhamento visual quando ele não pode ser estabelecido passivamente

## <a name="holographic-thermal"></a>Holographic Thermal

**/api/holographic/thermal/stage (GET)**

Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)

## <a name="map-manager"></a>Gerenciador de Mapas

**/api/holographic/mapmanager/mapFiles (GET)**

Obtém a lista dos arquivos de mapa disponíveis (.mapx).

**/api/holographic/mapmanager/anchorFiles (GET)**

Obtém a lista de arquivos de âncora disponíveis (.ancx).

**/api/holographic/mapmanager/srdbFiles (GET)**

Obtém a lista de arquivos de banco de dados de reconstrução espacial disponíveis (.srdb).

**/api/holographic/mapmanager/getanchors (GET)**

Obtém a lista de âncoras persistentes para o usuário atual. 

### <a name="downloaduploaddelete-files"></a>Baixar/Upload/excluir arquivos
**/api/holographic/mapmanager/download (GET)**

Baixa um mapa, âncora ou arquivo de banco de dados de reconstrução espacial. O arquivo deve ter sido carregado ou exportado anteriormente.

Parâmetros
* FileName: nome do arquivo a ser baixado.

Exemplo: 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/API/Holographic/mapmanager/upload (POST)**

Carrega um arquivo de banco de dados de reconstituição de mapa, âncora ou espacial. Depois que um arquivo é carregado, ele pode ser importado posteriormente para ser usado pelo sistema.

Parâmetros
* File: o nome do arquivo a ser carregado.

Exemplo:
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

**/API/Holographic/mapmanager/Delete (POST)**

Exclui um arquivo de banco de dados de mapa, âncora ou reconstituição espacial. O arquivo deve ter sido carregado ou exportado anteriormente.

Parâmetros
* FileName: nome do arquivo a ser excluído.

Exemplo: 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>Exportação

**/API/Holographic/mapmanager/Export (POST)**

Exporta o mapa atualmente em uso pelo sistema. Depois de exportado, ele pode ser baixado. 

Exemplo: 
```
$.post("/api/holographic/mapmanager/export")
```

**/API/Holographic/mapmanager/exportanchors (POST)**

Exporta o mapa atualmente em uso pelo sistema. Depois de exportado, ele pode ser baixado. Exemplo: 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/API/Holographic/mapmanager/exportmapandanchors (POST)**

Exporta o mapa e as âncoras atualmente em uso pelo sistema. Depois de exportadas, elas podem ser baixadas. Exemplo: 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/API/Holographic/mapmanager/exportmapandspatialmappingdb (POST)**

Exporta o mapa e o banco de dados de reconstrução espacial atualmente em uso pelo sistema. Depois que eles são exportados, eles podem ser baixados. 

Exemplo: 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>Importar

**/API/Holographic/mapmanager/Import (POST)**

Indica ao sistema qual mapa deve ser usado no momento. Pode ser chamado em arquivos que foram exportados ou carregados.

Parâmetros
* Nome do arquivo: o nome do mapa a ser usado. 

Exemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/API/Holographic/mapmanager/importanchors (POST)**

Indica ao sistema quais âncoras devem ser usadas no momento. Pode ser chamado em arquivos que foram exportados ou carregados.

Parâmetros
* Nome do arquivo: nome das âncoras a serem usadas. 

Exemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/API/Holographic/mapmanager/importspatialmappingdb (POST)**

Indica ao sistema qual banco de dados de reconstrução espacial deve ser usado no momento. Pode ser chamado em arquivos que foram exportados ou carregados.

Parâmetros
* Nome do arquivo: nome do BD de mapeamento espacial a ser usado. 

Exemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>Outro

**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

Redefina o sistema o banco de dados mapa, âncoras e reconstrução espacial.

Exemplo: 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/API/Holographic/mapmanager/status (GET)**

Obtém o status do sistema, incluindo quais mapas, âncoras e arquivos de banco de dados de reconstrução espacial foram importados pela última vez. 


## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/API/Holographic/MRC/File (GET)**

Baixa um arquivo de realidade misturada do dispositivo. Use op = Stream Query parâmetro para streaming.

Parâmetros
* filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido
* op: fluxo

**/API/Holographic/MRC/File (excluir)**

Exclui uma gravação de realidade misturada do dispositivo.

Parâmetros
* filename: nome, hex64 codificado, do arquivo a ser excluído

**/API/Holographic/MRC/Files (GET)**

Retorna a lista de arquivos de realidade misturada armazenados no dispositivo

**/API/Holographic/MRC/Photo (POST)**

Usa uma foto de realidade misturada e cria um arquivo no dispositivo

Parâmetros
* holo: capturar hologramas: true ou false (o padrão é false)
* PV: capturar câmera PV: true ou false (o padrão é false)
* RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)

**/API/Holographic/MRC/Settings (GET)**

Obtém as configurações padrão da captura de realidade misturada

**/API/Holographic/MRC/Settings (POST)**

Define as configurações padrão de captura de realidade misturada.  Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.

**/API/Holographic/MRC/status (GET)**

obtém o estado da captura da realidade misturada dentro do Windows Portal do dispositivo.

***Resposta***

a resposta contém uma propriedade JSON que indica se Windows Portal do dispositivo está gravando vídeo ou não.

``` javascript
{"IsRecording" : boolean}
```

**/API/Holographic/MRC/Thumbnail (GET)**

Obtém a imagem em miniatura do arquivo especificado.

Parâmetros
* filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada

**/API/Holographic/MRC/Video/Control/Start (POST)**

Inicia uma gravação de realidade misturada

Parâmetros
* holo: capturar hologramas: true ou false (o padrão é false)
* PV: capturar câmera PV: true ou false (o padrão é false)
* MIC: capturar microfone: true ou false (o padrão é false)
* loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)
* RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)
* vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)
* vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)

**/API/Holographic/MRC/Video/Control/Stop (POST)**

Interrompe a gravação atual da realidade misturada

## <a name="mixed-reality-streaming"></a>Streaming de realidade misturada

> [!CAUTION]
> Devido ao isolamento de auto-retorno, você não pode se conectar ao streaming de realidade misturada de dentro de um aplicativo em um dispositivo.

o HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um mp4 fragmentado.

Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:
* holo: capturar hologramas: verdadeiro ou falso
* PV: capturar câmera PV: verdadeiro ou falso
* MIC: capturar microfone: verdadeiro ou falso
* loopback: capturar áudio do aplicativo: verdadeiro ou falso

Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados<br>
Se houver algum especificado: os parâmetros não especificados serão padronizados como false

parâmetros opcionais (somente HoloLens 2)
* RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)
* Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)
* vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)

**/API/Holographic/Stream/live.mp4 (GET)**

1280x720p 30fps 5Mbit Stream.

**/API/Holographic/Stream/live_high.mp4 (GET)**

1280x720p 30fps 5Mbit Stream.

**/API/Holographic/Stream/live_med.mp4 (GET)**

Um fluxo 854x480p 30fps 2.5 Mbit.

**/API/Holographic/Stream/live_low.mp4 (GET)**

Um fluxo 428x240p 15fps 0,6 Mbit.

## <a name="networking"></a>Rede

**/API/Networking/ipconfig (GET)**

Obter a configuração de IP atual

## <a name="os-information"></a>Informações do sistema operacional

**/API/os/info (GET)**

Obtém informações do sistema operacional

**/API/os/MachineName (GET)**

Obtém o nome do computador

**/API/os/MachineName (POST)**

Define o nome do computador

Parâmetros
* Nome: novo nome do computador, hex64 codificado, para definir como

## <a name="perception-simulation-control"></a>Controle de simulação de percepção

**/API/Holographic/Simulation/Control/Mode (GET)**

Obter o modo de simulação

**/API/Holographic/Simulation/Control/Mode (POST)**

Definir o modo de simulação

Parâmetros
* modo: modo de simulação: padrão, simulação, remoto, herdado

**/API/Holographic/Simulation/Control/Stream (excluir)**

Excluir um fluxo de controle.

**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**

Abra uma conexão de soquete da Web para um fluxo de controle.

**/API/Holographic/Simulation/Control/Stream (POST)**

Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário). Espera-se que os dados postados sejam do tipo ' application/octet-stream '.

**/API/Holographic/Simulation/display/Stream (obter/WebSocket)**

Solicite um fluxo de vídeo de simulação contendo o conteúdo renderizado para a exibição do sistema quando estiver no modo ' Simulation '.  Um cabeçalho de descritor de formato simples será enviado inicialmente, seguido de texturas codificadas H. 264, cada um precedido por um cabeçalho que indica o índice de olho e o tamanho da textura.

## <a name="perception-simulation-playback"></a>Reprodução da simulação de percepção

**/API/Holographic/Simulation/playback/File (excluir)**

Excluir uma gravação.

Parâmetros
* gravação: o nome da gravação a ser excluída.

**/API/Holographic/Simulation/playback/File (POST)**

Upload uma gravação.

**/API/Holographic/Simulation/playback/Files (GET)**

Obter todas as gravações.

**/API/Holographic/Simulation/playback/Session (GET)**

Obter o estado de reprodução atual de uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/File (excluir)**

Descarregar uma gravação.

Parâmetros
* gravação: nome da gravação a ser descarregada.

**/API/Holographic/Simulation/playback/Session/File (POST)**

Carregar uma gravação.

Parâmetros
* gravação: o nome da gravação a ser carregada.

**/API/Holographic/Simulation/playback/Session/Files (GET)**

Obter todas as gravações carregadas.

**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**

Pausar uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Play (POST)**

Reproduzir uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Stop (POST)**

Parar uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Types (GET)**

Obter os tipos de dados em uma gravação carregada.

Parâmetros
* gravação: nome da gravação.

## <a name="perception-simulation-recording"></a>Gravação da simulação de percepção

**/API/Holographic/Simulation/Recording/Start (POST)**

Inicie uma gravação. Apenas uma única gravação pode estar ativa de uma vez. É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.

Parâmetros
* Cabeçalho: Defina como 1 para registrar dados de cabeçalho.
* Hands: Defina como 1 para gravar dados de mão.
* spatialMapping: Defina como 1 para registrar o mapeamento espacial.
* ambiente: Defina como 1 para gravar dados do ambiente.
* name : nome da gravação.
* singleSpatialMappingFrame: definido como 1 para registrar apenas um único quadro de mapeamento espacial.

**/api/holographic/simulation/recording/status (GET)**

Obter o estado de gravação.

**/api/holographic/simulation/recording/stop (GET)**

Pare a gravação atual. A gravação será retornada como um arquivo.

## <a name="performance-data"></a>Dados de desempenho

**/api/resourcemanager/processes (GET)**

Retorna a lista de processos em execução com detalhes

Retornar dados
* JSON com lista de processos e detalhes para cada processo

**/api/resourcemanager/systemperf (GET)**

Retorna estatísticas de perf do sistema (E/S de leitura/gravação, estatísticas de memória etc.

Retornar dados
* JSON com informações do sistema: CPU, GPU, Memória, Rede, E/S

## <a name="power"></a>Energia

**/api/power/battery (GET)**

Obtém o estado atual da bateria

**/api/power/state (GET)**

Verifica se o sistema está em um estado de baixa energia

## <a name="remote-control"></a>Controle remoto

**/api/control/restart (POST)**

Reinicia o dispositivo de destino

**/api/control/shutdown (POST)**

Desliga o dispositivo de destino

## <a name="task-manager"></a>Gerenciador de Tarefas

**/api/taskmanager/app (DELETE)**

Interrompe um aplicativo moderno

Parâmetros
* package : nome completo do pacote do aplicativo, codificado em hex64
* forcestop: forçar a parada de todos os processos (=sim)

**/api/taskmanager/app (POST)**

Inicia um aplicativo moderno

Parâmetros
* appid: PRAID do aplicativo para iniciar, codificado em hex64
* package : nome completo do pacote do aplicativo, codificado em hex64

## <a name="wifi-management"></a>Gerenciamento de WiFi

**/api/wifi/interfaces (GET)**

Enumera interfaces de rede sem fio

Retornar dados
* Lista de interfaces sem fio com detalhes (GUID, descrição etc.)

**/api/wifi/network (DELETE)**

Exclui um perfil associado a uma rede em uma interface especificada

Parâmetros
* interface : guid de interface de rede
* profile : nome do perfil

**/api/wifi/networks (GET)**

Enumera redes sem fio no interface de rede especificado

Parâmetros
* interface : guid de interface de rede

Retornar dados
* Lista de redes sem fio encontradas no interface de rede com detalhes

**/api/wifi/network (POST)**

Conecta ou desconecta a uma rede na interface especificada

Parâmetros
* interface : guid de interface de rede
* ssid : ssid, hex64 codificado, para se conectar a
* op: conectar ou desconectar
* createprofile : sim ou não
* chave : chave compartilhada, codificada hex64

## <a name="windows-performance-recorder"></a>Windows Gravador de desempenho

**/api/wpr/customtrace (POST)**

Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.

Carga útil
* corpo http em conformidade com várias partes

Retornar dados
* Retorna o status da sessão WPR.

**/api/wpr/status (GET)**

Recupera o status da sessão WPR

Retornar dados
* Status da sessão WPR.

**/api/wpr/trace (GET)**

Interrompe uma sessão de rastreamento WPR (desempenho)

Retornar dados
* Retorna o arquivo ETL de rastreamento

**/api/wpr/trace (POST)**

Inicia sessões de rastreamento wpr (desempenho)

Parâmetros
* profile : nome do perfil. Os perfis disponíveis são armazenados em perfprofiles/profiles.json

Retornar dados
* Ao iniciar, retorna o status da sessão WPR.

## <a name="see-also"></a>Confira também
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
* [Portal de Dispositivos UWP (referência de API principal)](/windows/uwp/debug-test-perf/device-portal-api-core)