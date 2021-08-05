---
title: Documentação do Empacotador de Dados Espaciais de Realidade Misturada
description: A ferramenta Empacotador de Dados Espaciais de Realidade Misturada agora foi preterida e não funciona mais em nenhuma plataforma. Em vez disso, a ferramenta Gerenciador de Mapas é recomendada.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 914e22c4e80385c93696ebd978000978e1e03f57706d466bdbb3cfcd5843f69e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213160"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentação do Empacotador de Dados Espaciais de Realidade Misturada

>[!NOTE]
> PRETERIDO 
> 
> A partir de 1/8/2020, essa ferramenta foi preterida e não funciona mais em nenhuma plataforma. É recomendável usar a [ferramenta Gerenciador](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) de Mapas no Portal de Dispositivos em vez disso. 
> 
> Essa ferramenta e sua operação são oferecidas no momento. Ele está sujeito a alterações sem aviso prévio e pode não ser compatível com versões futuras Windows ou Windows Mixed Reality HMD. 


## <a name="download"></a>Baixar
 Baixe [MixedRealitySpatialDataPackager aqui](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Empacotador de Dados Espaciais de Realidade Misturada</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>Início Rápido

A ferramenta Empacotador de Dados Espaciais de Realidade Misturada copia os dados espaciais de um aplicativo de destino de um computador para outro por meio de um processo de exportação e importação de duas etapas. A ferramenta deve ser executado com privilégios de administrador e exclui os dados espaciais existentes na importação. A exportação deixa os dados espaciais existentes intactos.

Principais requisitos e limitações:

1. A ferramenta deve ser executado com privilégios de administrador 
2. Talvez seja preciso reiniciar o computador se Portal de Realidade Misturada instável depois de executar a ferramenta
3. A ferramenta não será executado ao encontrar incompatibilidades ou incompatibilidades de versão de dados espaciais
4. A ferramenta apagará os dados espaciais existentes na importação
5. Se o processo de importação falhar, os dados anteriores não poderão ser restaurados, a menos que tenha sido feito backup exportando anteriormente
6. A qualidade da funcionalidade de importação depende do modo "Somente Leitura" para dados de mapa espacial
***

## <a name="mapping-best-practices"></a>Práticas recomendadas de mapeamento

1. Limpar mapas existentes do Painel de Controle (Configurações -> Mixed Reality -> Environment -> Limpar dados de ambiente)
2. Garantir iluminação suficiente para um bom acompanhamento e, se estiver executando o modo de mapa bloqueado, tente manter a mesma iluminação
3. Quando possível, mantenha o intervalo dinâmico de iluminação baixo, evitando áreas de alta iluminação ao lado de áreas escuras e sombreadas
4. Minimizar superfícies em branco e sem textura, por exemplo, colocar uma variedade de cartazes diferentes em paredes brancas
5. Mapear o espaço sem objetos dinâmicos na cena, como mover pessoas
6. Bloquear o mapa na importação (disponível por meio do Insider Preview)
7. Desbloquear o mapa e digitaliza novamente o ambiente quando o controle de qualidade degrada e/ou há alterações no ambiente (iluminação ou alterações no layout do objeto)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Executando o Empacotador de Dados Espaciais de Realidade Misturada com Script Descontinuado

Fornecemos MRSpatialPackagerHelperScript.ps1 que executa as ferramentas do empacotador de mapa. 


Os parâmetros de script são definidos abaixo:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Uso e saída de exemplo de script do Powershell

.\MRSpatialPackagerHelperScript.ps1 holoshell -AppName -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>Como exportar usando MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

A exportação de mapas do dispositivo gera dois arquivos mapx, het.mapx e sa.mapx. Durante o processo de exportação, todas as âncoras espaciais são removidas, exceto o aplicativo especificado e o limite criado pelo usuário (se existir). O nome da família do pacote de origem deve corresponder a um aplicativo instalado existente ou o exe falhará.

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>Como importar usando MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
A importação exclui os dados espaciais existentes e os substitui com os dados do diretório especificado. A entrada do nome do aplicativo especifica o nome do pacote do aplicativo de destino que, como as âncoras espaciais, deve ser importado para e o SID do usuário de destino especifica o usuário que deve ter acesso às âncoras espaciais importadas. O nome da família de pacotes de destino e os SIDs de usuário devem corresponder aos valores existentes no PC ou o exe falhará.


***
## <a name="error-messages"></a>Mensagens de erro
Além disso, as mensagens de erro abaixo das falhas também serão acompanhadas com um HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Se houver um erro de argumentos inválidos
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Se o executável não foi executado no modo de administrador
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Se houve um erro ao habilenciar ou desabilitar o driver
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Se houve um erro ao validar a versão do banco de dados espacial
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Se houve um erro ao validar o nome da família de pacotes fornecido para o aplicativo de importação/exportação de destino
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Se houve um erro ao validar o SID do usuário
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Se houve um erro relacionado aos arquivos de dados espaciais de origem ou de destino
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Se houve um erro relacionado ao início e interrupção de Spectrum/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```