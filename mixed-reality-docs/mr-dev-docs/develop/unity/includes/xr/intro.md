---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906933"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

O plug-in OpenXR de Realidade Misturada é a recomendação da **Microsoft** para Unity 2020 LTS ou posterior. À medida que novos recursos são desenvolvidos no futuro, eles só serão incluídos no plug-in OpenXR de Realidade Misturada no futuro.

O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de raycasting uma vez que abrange os telefones e tablets holoLens 2 e ARCore/ARKit.

### <a name="prerequisites"></a>Pré-requisitos 

* Ferramentas [mais recentes para desenvolvimento do HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Unity 2020.3 LTS mais recente, (recomendamos 2020.3.8f1 ou superior)

### <a name="minimum-versions"></a>Versões mínimas

As instruções nesta página configurarão você com os requisitos mais recentes e mais recentes do Unity e do OpenXR listados abaixo:

* Plug-in do Unity OpenXR mais recente (recomendamos 1.2 ou posterior)
* Plug-in OpenXR de Realidade Misturada mais recente (recomendamos a versão 1.0.0 ou posterior)
* **(Opcional)** MRTK mais recente(recomendamos a versão 2.7 ou posterior)
* **(Opcional)** Pacote de Pipeline de Renderização Universal mais recente (recomendamos a versão 10.5.1 ou posterior)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Se você estiver criando aplicativos de VR no computador Windows, o plug-in OpenXR de Realidade Misturada não será necessariamente necessário. No entanto, você deseja instalar o plug-in se estiver personalização do mapeamento do controlador para controladores HP Reverb G2 ou criação de aplicativos que funcionam em headsets HoloLens 2 e VR.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

A Microsoft não recomenda usar o plug-in do Windows XR para novos projetos no Unity 2020.

No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2.0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in habilita esse suporte.

> [!IMPORTANT]
> O uso desse plug-in no Unity 2019 não dá suporte a Âncoras Espaciais do Azure. 

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Se você ainda estiver no Unity 2019 ou anterior, a Microsoft recomenda o uso do suporte a XR integrado herdado. Embora o plug-in do Windows XR seja funcional no Unity 2019, não é recomendável porque não há suporte para Âncoras Espaciais do Azure.