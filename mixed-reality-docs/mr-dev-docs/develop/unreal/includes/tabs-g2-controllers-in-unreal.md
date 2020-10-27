---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638607"
---
# <a name="all-platforms"></a>[Todas as plataformas](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Habilitando plug-in do controlador HP Motion 

O perfil de interação e os mapeamentos do controlador estão no plug-in do controlador HP Motion, que deve ser habilitado para expor os mapeamentos do controlador para o sistema de entrada do inreal.

![Habilitando o plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configurando inicialização e HMDPluginPriority

A entrada em inreal usando SteamVR tem algumas diferenças.  Ao configurar o projeto, primeiro verifique se ele está usando o novo sistema de entrada do SteamVR adicionando **VR. SteamVR. EnableVRInput = 1** para a seção de **inicialização** em **Engine/config/ConsoleVariables.ini** .  Esse ini é encontrado no diretório de instalação do mecanismo, não no diretório do projeto.

![Atualizando a configuração de inicialização](../images/reverb-g2-img-07.png)

O plug-in do controlador HP Motion habilitará o OpenXR.  Se você não estiver usando o OpenXR, será necessário editar o HMDPluginPriority de SteamVR no BaseEngine.ini no mesmo diretório que ConsoleVariables.ini.  Altere o valor de SteamVR para que seja maior que o valor de OpenXRHMD.

![Atualizando a configuração do HMDPluginPriority](../images/reverb-g2-img-08.png)


