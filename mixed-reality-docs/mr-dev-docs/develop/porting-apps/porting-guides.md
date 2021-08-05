---
title: Portabilidade dos aplicativos de VR para o Windows Mixed Reality
description: Uma explicação passo a passo explicando como portar um aplicativo de imersão existente para Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: porta, unity, não real, middleware, mecanismo, UWP, Win32, portabilidade, HoloLens 1ª gen, headset de realidade misturada, headset de realidade mista do windows, migração, Windows 10, mapeamento de entrada,
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213500"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portabilidade dos aplicativos de VR para o Windows Mixed Reality

Windows 10 inclui suporte para headsets de imersão e holographic. Se você tiver criado conteúdo para outros dispositivos como o Oculus Rift ou o HTC Naopak, eles têm dependências em bibliotecas que existem acima da API de plataforma do sistema operacional. colocar aplicativos existentes do Win32 Unity vr no Windows Mixed Reality envolve o redirecionamento do uso de SDKs de vr específicos do fornecedor para as APIs vr entre fornecedores do Unity.

## <a name="porting-requirements"></a>Requisitos de portabilidade

Em um alto nível, as etapas a seguir estão envolvidas na portabilidade de conteúdo existente:
1. **verifique se o computador está executando o Windows 10 Fall Creators Update (16299).** Não é mais recomendável receber compilações prévias do anel do insider skip ahead, pois essas compilações não serão as mais estáveis para o desenvolvimento de realidade misturada.
2. **Atualize para a versão mais recente do seu mecanismo de gráficos ou jogos.** os mecanismos de jogo precisarão dar suporte ao SDK Windows 10 versão 10.0.15063.0 (lançado em abril de 2017) ou superior.
3. **Atualize qualquer middleware, plug-ins ou componentes.** Se seu aplicativo contiver qualquer componente, é uma boa ideia atualizar para a versão mais recente.
4. **Remova dependências em SDKs duplicados**. dependendo de qual dispositivo o seu conteúdo foi direcionado, você precisará remover ou compilar condicionalmente esse SDK para que você possa direcionar as APIs de Windows em vez disso. Um exemplo desse cenário seria SteamVR.
5. **Trabalhe com problemas de compilação.** Neste ponto, o exercício de portabilidade é específico para seu aplicativo, seu mecanismo e as dependências de componente que você tem.

## <a name="common-porting-steps"></a>Etapas de portabilidade comuns

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Verifique se você tem o hardware de desenvolvimento correto

A página [Guia de entusiastas VR](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) lista o hardware de desenvolvimento recomendado.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. atualizar para o vôo mais recente de Windows 10

a plataforma Windows Mixed Reality ainda está em desenvolvimento ativo. é recomendável [ingressar no programa insider Windows](https://insider.windows.com/) para acessar o vôo "Windows insider Fast".
1. instalar o [Atualização do Windows 10 para Criadores](https://www.microsoft.com/software-download/windows10)
2. [junte](https://insider.windows.com/) -se ao programa insider Windows.
3. Habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development)
4. mude para o [Windows Fast insider rapidamente](/archive/blogs/uktechnet/joining-insider-preview) por meio do **Configurações > seção atualização & segurança**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. atualizar para a compilação mais recente de Visual Studio
* se você estiver usando Visual Studio, atualize para a compilação mais recente
* consulte [instalar a página ferramentas](../install-the-tools.md#installation-checklist) em Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. escolha o adaptador correto
* Em sistemas como notebooks com duas GPUs, [direcione o adaptador correto](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Isso se aplica aos aplicativos do Unity e do DirectX nativo, em que um ID3D11Device é criado, explícita ou implicitamente (Media Foundation), para sua funcionalidade.

## <a name="unity-porting-guidance"></a>Diretrizes de portabilidade do Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Diretrizes de portabilidade inreal

> [!IMPORTANT]
> Se você estiver usando os controladores de reverberação do HP, consulte [Este artigo](../unreal/unreal-reverb-g2-controllers.md) para obter instruções adicionais de mapeamento de entrada.

## <a name="see-also"></a>Confira também
* [diretrizes mínimas de compatibilidade de hardware do PC Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Entendendo o desempenho da realidade misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](../unity/performance-recommendations-for-unity.md)
* [Controladores de movimentos](../../design/motion-controllers.md)
* [Controladores de movimento no Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guias de portabilidade](porting-guides.md)