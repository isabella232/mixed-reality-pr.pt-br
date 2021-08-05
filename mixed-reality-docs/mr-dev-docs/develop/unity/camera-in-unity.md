---
title: Configuração da câmera no Unity
description: Saiba como configurar e usar a Câmera Principal do Unity para Windows Mixed Reality desenvolvimento para fazer renderização holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, renderização holográfica, holográfico, imersivo, ponto de foco, buffer de profundidade, somente orientação, posicional, opaco, transparente, clipe, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212193"
---
# <a name="camera-setup-in-unity"></a>Configuração da câmera no Unity

Quando você usa um headset de realidade misturada, ele se torna o centro do seu mundo holográfico. O componente Câmera [do](https://docs.unity3d.com/Manual/class-Camera.html) Unity manipulará automaticamente a renderização estereografária e seguirá o movimento e a rotação da cabeça. No entanto, para otimizar totalmente a qualidade visual e a estabilidade [do holograma,](../platform-capabilities-and-apis/hologram-stability.md)você deve definir as configurações de câmera descritas abaixo.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens headsets imersivos versus VR

As configurações padrão no componente Câmera do Unity são para aplicativos 3D tradicionais, que precisam de um plano de fundo parecido com o skybox, pois eles não têm um mundo real.

* Ao executar em um **[headset](../../discover/immersive-headset-hardware-details.md)** imersivo, você está renderizar tudo o que o usuário vê e, portanto, provavelmente deseja manter o skybox.
* No entanto, ao executar em um **headset holográfico** [como HoloLens](/hololens/hololens2-hardware), o mundo real deve aparecer por trás de tudo o que a câmera renderiza. De definir a plano de fundo da câmera como transparente (HoloLens, o preto é renderiza como transparente) em vez de uma textura do Skybox:
    1. Selecione a Câmera Principal no painel Hierarquia
    2. No painel Inspetor, encontre o componente Câmera e altere o menu suspenso Limpar Sinalizadores de Skybox para Cor Sólida
    3. Selecione o seletor Cor da tela de fundo e altere os valores de RGBA para (0, 0, 0, 0)
        1. Se definir isso do código, você poderá usar o do Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Instalação da câmera

Seja qual for o tipo de experiência que você está desenvolvendo, a Câmera Principal é sempre o componente de renderização estéreo primário anexado à exibição montada com a cabeça do dispositivo. Será mais fácil de colocar seu aplicativo se você imaginar a posição inicial do usuário como (X: 0, Y: 0, Z: 0). Como a Câmera Principal está acompanhando o movimento da cabeça do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da Câmera Principal.

A opção central que você precisa fazer é se você está desenvolvendo para headsets imersivos HoloLens ou VR. Depois de fazer isso, pule para a seção de instalação que se aplicar.

### <a name="hololens-camera-setup"></a>HoloLens da câmera

Para HoloLens aplicativos, você precisa usar âncoras para todos os objetos que deseja bloquear no ambiente de cena. É recomendável usar espaço nãobounded para maximizar a estabilidade e criar âncoras em várias salas.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configuração da câmera de VR

Windows Mixed Reality dá suporte a aplicativos em uma ampla variedade de escalas de experiência, desde aplicativos somente de orientação e escala de sedados até [aplicativos](../../design/coordinate-systems.md#mixed-reality-experience-scales)de escala de sala. No HoloLens, você pode ir além e criar aplicativos de escala mundial que permitem que os usuários andem além de 5 metros, explorando um andar inteiro de um prédio e além.

Sua primeira etapa na criação de uma experiência de realidade misturada no Unity é determinar qual escala de [experiência](../../design/coordinate-systems.md) seu aplicativo terá como destino:

* [Orientação ou escala de seada](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Escala de espaço ou em pé](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Escala mundial](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Experiências em escala de sala ou em espera

> [!NOTE]
> Se você estiver criando para HL2, recomendamos criar uma [](../platform-capabilities-and-apis/scene-understanding-sdk.md) experiência no nível do olho ou considerar o uso do Entendimento de Cena para analisar o andar da cena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Experiências de setada

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configurando a plano de fundo da câmera

Se você estiver usando o MRTK, a plano de fundo da câmera será configurada e gerenciada automaticamente. Para projetos do SDK XR ou WSA herdados, é recomendável definir a plano de fundo da câmera como preto HoloLens e manter a área de fundo para VR.

## <a name="using-multiple-cameras"></a>Usando várias câmeras

Quando há vários componentes de Câmera na cena, o Unity sabe qual câmera usar para renderização estereografada com base em qual GameObject tem a marca MainCamera. No XR herddo, ele também usa essa marca para sincronizar o acompanhamento de cabeça. No SDK do XR, o acompanhamento de cabeça é orientado por um script TrackedPoseDriver anexado à câmera.

## <a name="sharing-depth-buffers"></a>Compartilhando buffers de profundidade

Compartilhar o buffer de profundidade do aplicativo para Windows cada quadro dará ao aplicativo um dos dois aumentos na estabilidade do holograma, com base no tipo de headset para o qual você está renderizar:

* **Os headsets imersivos** de VR podem cuidar da reprojeção posicional quando um buffer de profundidade é fornecido, ajustando seus hologramas para preterição indevida na posição e na orientação.
* **HoloLens headsets** têm alguns métodos diferentes. HoloLens 1 selecionará automaticamente um ponto de foco quando um buffer de profundidade for fornecido, otimizando [a](focus-point-in-unity.md) estabilidade do holograma ao longo do plano que intersecciona a maior parte do conteúdo. HoloLens 2 estabilizará o conteúdo usando [a LSR de profundidade (consulte Comentários).](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Usando planos de recorte

Renderizar conteúdo muito próximo do usuário pode ser confuso na realidade misturada. Você pode ajustar os [planos de clipe](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) próximo e distante no componente Câmera.

1. Selecione a **Câmera Principal** no painel **Hierarquia**
2. No painel **Inspetor,** localie  os **Planos** de Recorte do componente Câmera e altere a **caixa** de texto Próximo de **0,3** para **0,85**. O conteúdo renderizado ainda mais próximo pode levar ao mal-estar do usuário e deve ser evitado de acordo com as diretrizes [de distância de renderização.](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="recentering-the-camera"></a>Como reativar a câmera

Se você estiver criando uma experiência de escala de banco de [dados,](../../design/coordinate-systems.md)poderá criar a origem do mundo do Unity na posição atual da cabeça do usuário chamando o **[XR. Método InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** no XR herdado ou no método **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** no SDK do XR.

## <a name="teleportation"></a>Portabilidade

Esse recurso normalmente é reservado para experiências de VR:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modos de reprodução

Os HoloLens e os headsets imersivos reprojetarão cada quadro que seu aplicativo renderizar para ajustar qualquer preterido da posição de cabeça real do usuário quando os fótons são emitidos.

Por padrão:

* **Os headsets imersivos** de VR cuidarão da reprojeção posicional se o aplicativo fornece um buffer de profundidade para um determinado quadro. Os headsets imersivos também ajustarão seus hologramas quanto à previsão indevida na posição e na orientação. Se um buffer de profundidade não for fornecido, o sistema corrigirá apenas as previsões incorretamente na orientação.
* **Headsets holográficos** como HoloLens 2 cuidarão da reprojeção posicional, independentemente se o aplicativo fornece seu buffer de profundidade ou não. A reprojeção posicional é possível sem buffers de profundidade no HoloLens pois a renderização geralmente é esparsa com um plano de fundo estável fornecido pelo mundo real.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Foco](gaze-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md)
* [Escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Como controlar a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Persistência no Unity](persistence-in-unity.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* [Âncoras Espaciais do Azure](/azure/spatial-anchors)
* [SDK de Âncoras Espaciais do Azure para Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)