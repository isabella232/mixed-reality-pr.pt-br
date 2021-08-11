---
ms.openlocfilehash: 923f7eda8b40e88aa69006896bd478f7aedcbcafccd449b75f144231d02b0d56
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202696"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

O plug-in OpenXR de Realidade Misturada é a recomendação da **Microsoft** para **Unity 2020 LTS** ou posterior. À medida que novos recursos são desenvolvidos no futuro, eles só serão incluídos no plug-in OpenXR de Realidade Misturada no futuro.

O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de raycasting uma vez que, em seguida, abrange HoloLens e telefones e tablets ARCore/ARKit.

### <a name="prerequisites"></a>Pré-requisitos 

* Ferramentas [mais recentes para HoloLens desenvolvimento 2](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Unity 2020.3 LTS mais recente: versão 2020.3.8f1 ou posterior

### <a name="recommended-package-versions"></a>Versões de pacote recomendadas

As instruções nesta página configurarão você com os principais pacotes OpenXR do Unity necessários para implantar HoloLens 2 ou Windows Mixed Reality aplicativos:

* Plug-in do Unity OpenXR: versão 1.2 ou posterior
* Plug-in openXR de Realidade Misturada: versão 1.0.0 ou posterior

Se você usar os seguintes pacotes em seu projeto, precisará garantir que use pelo menos as versões mínimas listadas abaixo:

* MRTK: versão 2.7.2 ou posterior
* AR Foundation: versão 4.1.1 ou posterior
* URP (Pipeline de Renderização Universal): versão 10.5.1 ou posterior
* Âncoras Espaciais do Azure: versão 2.10 ou posterior
* Azure Remote Rendering: versão 1.0.15 ou posterior

> [!NOTE]
> Se você estiver criando aplicativos de VR no Windows PC, o plug-in OpenXR de Realidade Misturada não será estritamente necessário. No entanto, você deseja instalar o plug-in se estiver configurando vinculações de entrada para controladores HP Reverb G2 ou criando aplicativos que funcionam em headsets HoloLens 2 e VR.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

A Microsoft não recomenda usar o plug-in Windows XR para novos projetos no Unity 2020.  Em vez disso, você deve usar o plug-in OpenXR de Realidade Misturada.

No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2.0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in habilita esse suporte.

> [!IMPORTANT]
> O uso desse plug-in no Unity 2019 não é compatível com as Âncoras Espaciais do Azure.

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Se você ainda estiver no **Unity 2019** ou anterior, a Microsoft recomenda o uso do suporte a **XR integrado herdado.**

Embora o plug-in Windows XR seja funcional no Unity 2019, não é recomendável porque esse plug-in não é compatível com âncoras espaciais do Azure no Unity 2019.

Se você estiver iniciando um novo projeto, recomendamos instalar o [Unity 2020](../../choosing-unity-version.md) e usar o plug-in OpenXR de Realidade Misturada.