---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103895"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

O plug-in Mixed Reality OpenXR é a **recomendação da Microsoft para o** Unity 2020 LTS ou posterior. À medida que novos recursos forem desenvolvidos no futuro, eles só serão incluídos no plug-in Mixed Reality OpenXR.

O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva o código raycasting uma vez que se estenda por telefones 2 e ARCore/ARKit celulares e tablets.

### <a name="prerequisites"></a>Pré-requisitos 

* Ferramentas mais recentes [para o desenvolvimento do HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)
* LTS do Unity 2020,3 mais recente, (recomendamos o 2020.3.8 F1 ou superior)

### <a name="minimum-versions"></a>Versões mínimas

As instruções nesta página o configurarão com os melhores e mais recentes requisitos de Unity e OpenXR listados abaixo:

* Plug-in mais recente do Unity OpenXR (Recomendamos 1,2 ou posterior)
* Plugin OpenXR de realidade mista mais recente, (recomendamos a versão 1.0.0 ou posterior)
* Se seu projeto usar MRTK, recomendamos a versão 2.7.2 ou posterior
* Se o seu projeto usa o pacote do pipeline de renderização universal (URP), recomendamos a versão 10.5.1 ou posterior

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

A Microsoft não recomenda usar o plug-in do Windows XR para novos projetos no Unity 2020.

No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2,0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in permitirá esse suporte.

> [!IMPORTANT]
> O uso desse plug-in no Unity 2019 não oferece suporte a âncoras espaciais do Azure. 

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Se você ainda estiver no Unity 2019 ou anterior, a Microsoft recomenda usar o suporte interno a XR herdado. Embora o plug-in do Windows XR seja funcional no Unity 2019, não é recomendável porque as âncoras espaciais do Azure não têm suporte.