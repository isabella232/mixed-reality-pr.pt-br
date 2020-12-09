---
title: Portabilidade dos aplicativos de VR para o Windows Mixed Reality
description: Uma explicação passo a passo explicando como portar um aplicativo de imersão existente para a realidade mista do Windows.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: porta, Unity, não real, middleware, mecanismo, UWP, Win32, portabilidade, 1º de HoloLens, headset de realidade misturada, headset de realidade mista do Windows, migração, Windows 10, mapeamento de entrada,
ms.openlocfilehash: 9f3e064c4462fc3d12a23bd94885476bcd2f9466
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925946"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portabilidade dos aplicativos de VR para o Windows Mixed Reality

O Windows 10 inclui suporte direto para headsets de imersão e Holographic. Se você tiver criado conteúdo para outros dispositivos, como o Oculus Rift ou o HTC Naopak, eles têm dependências em bibliotecas que existem acima da API de plataforma do sistema operacional. A disponibilização de aplicativos existentes do Win32 Unity VR para a realidade mista do Windows envolve o redirecionamento do uso de SDKs de VR específicos do fornecedor para as APIs VR entre fornecedores do Unity.

## <a name="porting-requirements"></a>Requisitos de portabilidade

Em um alto nível, as etapas a seguir estão envolvidas na portabilidade de conteúdo existente:
1. **Verifique se o PC está executando a atualização dos criadores de outono do Windows 10 (16299).** Não é mais recomendável receber compilações prévias do anel do insider skip ahead, pois essas compilações não serão as mais estáveis para o desenvolvimento de realidade misturada.
2. **Atualize para a versão mais recente do seu mecanismo de gráficos ou jogos.** Os mecanismos de jogo precisarão dar suporte à versão 10.0.15063.0 do SDK do Windows 10 (lançado em abril de 2017) ou superior.
3. **Atualize qualquer middleware, plug-ins ou componentes.** Se seu aplicativo contiver qualquer componente, é uma boa ideia atualizar para a versão mais recente.
4. **Remova dependências em SDKs duplicados**. Dependendo de qual dispositivo o seu conteúdo foi direcionado, você precisará remover ou compilar condicionalmente esse SDK (por exemplo, SteamVR) para que você possa direcionar as APIs do Windows em vez disso.
5. **Trabalhe com problemas de compilação.** Neste ponto, o exercício de portabilidade é específico para seu aplicativo, seu mecanismo e as dependências de componente que você tem.

## <a name="common-porting-steps"></a>Etapas de portabilidade comuns

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Verifique se você tem o hardware de desenvolvimento correto

A página [instalar as ferramentas](../install-the-tools.md#immersive-vr-headset-requirements) lista o hardware de desenvolvimento recomendado.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. atualizar para o vôo mais recente do Windows 10

A plataforma Windows Mixed Reality ainda está em desenvolvimento ativo. Recomendamos que você [ingresse no programa Windows Insider](https://insider.windows.com/) para acessar o vôo "Windows Insider Fast".
1. Instalar a [atualização do Windows 10 para criadores](https://www.microsoft.com/software-download/windows10)
2. [Junte](https://insider.windows.com/) -se ao programa Windows Insider.
3. Habilitar [modo de desenvolvedor](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Alterne para o [Fast do Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) por meio **das configurações > seção atualização & segurança**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. atualizar para a compilação mais recente do Visual Studio
* Se você estiver usando o Visual Studio, atualize para a compilação mais recente
* Consulte [instalar a página de ferramentas](../install-the-tools.md#installation-checklist) no Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. escolha o adaptador correto
* Em sistemas como notebooks com duas GPUs, [direcione o adaptador correto](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Isso se aplica aos aplicativos do Unity e do DirectX nativo, em que um ID3D11Device é criado, explícita ou implicitamente (Media Foundation), para sua funcionalidade.

## <a name="unity-porting-guidance"></a>Diretrizes de portabilidade do Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Diretrizes de portabilidade inreal

> [!IMPORTANT]
> Se você estiver usando os controladores de reverberação do HP, consulte [Este artigo](../unreal/unreal-reverb-g2-controllers.md) para obter instruções adicionais de mapeamento de entrada.

## <a name="see-also"></a>Confira também
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Entendendo o desempenho da realidade misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para o Unity](../unity/performance-recommendations-for-unity.md)
* [Controladores de movimentos](../../design/motion-controllers.md)
* [Gestos e controladores de movimento no Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guias de portabilidade](porting-guides.md)