---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 5db08dee6b26de6fa3f44d92709e4903bb90a44c
ms.sourcegitcommit: 7595db7438398b5c78cec41a6f8ab625711bf8ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97664414"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Recursos com suporte da realidade misturada OpenXR no Unity

O pacote de **plug-in OpenXR da realidade mista** é uma extensão do **plug-in OpenXR** do Unity e dá suporte a um conjunto de recursos para headsets do HoloLens 2 e do Windows Mixed Reality. Antes de continuar, certifique-se de ter instalado o **Unity 2020,2** ou posterior, **OpenXR plugin versão 0.1.1** ou posterior e seu projeto de Unity está [configurado para OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>O que tem suporte

Atualmente, há suporte para os seguintes recursos:

* Dá suporte a aplicativos UWP para o HoloLens 2 e aplicativos Win32 VR para headsets de realidade mista do Windows.
* Otimiza o pacote UWP e a interação CoreWindow para aplicativos do HoloLens 2.
* Controle de escala mundial usando âncoras e espaço não associado.
* API de armazenamento de ancoragem para persistir âncoras no armazenamento local do HoloLens 2.
* [Controlador de movimento e interações de mão](#motion-controller-and-hand-interactions), incluindo o novo controlador do HP reverberate G2.
* Controle de mão articulado usando 26 junções e entradas de raio conjuntas.
* Observe a interação olhar no HoloLens 2.
* Localizando a câmera de foto/vídeo (PV) no HoloLens 2.
* A realidade misturada é a captura usando o processamento de 3ª vista por meio da câmera VP.
* Dá suporte à ["reprodução" para o HoloLens 2 com o aplicativo de comunicação remota do Holographic](#holographic-remoting-in-unity-editor-play-mode), permitindo que os desenvolvedores depurem scripts sem compilar e implantar no dispositivo.
* Compatível com MRTK Unity 2.5.2 por meio do pacote do adaptador MRTK OpenXR. <missing link>
* Compatível com o Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou posterior

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic comunicação remota no modo de reprodução do editor do Unity

Criar um projeto de Unity do UWP no projeto do Visual Studio e, em seguida, compactá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo. Uma solução é habilitar a comunicação remota do editor do Holographic, que permite que você depure seu script C# usando o modo "Play" diretamente em um dispositivo de HoloLens 2 em sua rede. Esse cenário evita a sobrecarga de criar e implantar um pacote UWP para um dispositivo remoto.

1. Primeiro, você precisa [instalar o aplicativo de player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do repositório no seu HoloLens 2  
2. Execute o aplicativo de player de comunicação remota do Holographic no HoloLens 2 e você verá o número de versão e o endereço IP para se conectar
    * Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR

![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

3. Abra **configurações do projeto de > de edição**, navegue até **Gerenciamento de plug-in de XR** e marque a caixa conjunto de recursos do **Windows Mixed Realm** :

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-features-img-02.png)

4. Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**
5. Marque a caixa de seleção **comunicação remota do editor de Holographic** e insira o endereço IP obtido do aplicativo de comunicação remota do Holographic:

![Captura de tela do painel de configurações do projeto aberto no editor do Unity com recursos realçados](images/openxr-features-img-03.png)

Agora você pode clicar no botão "reproduzir" para reproduzir seu aplicativo do Unity no aplicativo de comunicação remota do Holographic em seu HoloLens. Você também pode [anexar o Visual Studio ao Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts C# no modo de reprodução.

> [!NOTE]
> A partir da versão 0.1.0 a comunicação remota Holographic, o tempo de execução não dá suporte ao recurso de ancoragem e as funcionalidades de ARAnchorManager não funcionarão por meio de comunicação remota.  Esse recurso estará disponível em versões futuras.

## <a name="motion-controller-and-hand-interactions"></a>Controlador de movimento e interações de mão
Para aprender as noções básicas sobre interações de realidade misturada no Unity, visite o [manual do Unity para entrada do Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para s mais generalizadas `InputFeatureUsage` , como as entradas de XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais. 
 
O plug-in Mixed Reality OpenXR fornece perfis de interação de entrada adicionais, mapeados para `InputFeatureUsage` os s padrão, conforme detalhado abaixo: 
 
| `InputFeatureUsage` | Controlador do HP reverbo G2 (OpenXR) | Mão do HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Botões | |
| primary2DAxisClick | Joystick – clique em | |
| gatilho | Gatilho  | |
| Dimensiona | Dimensiona | Toque ou aperte o ar |
| primaryButton | [X/A]-Pressione | Fechar e abrir dedos indicador e polegar |
| secondaryButton | [S/B]-Pressione | |
| gripButton | Segure a tecla | |
| triggerButton | Gatilho-Pressione | |
| menuButton | Menu | |

#### <a name="haptics"></a>Haptics
Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics). 


## <a name="whats-coming-soon"></a>O que virá em breve

Os seguintes problemas e recursos ausentes são conhecidos com o plug-in OpenXR da realidade misturada **versão 0.1.0**. Estamos trabalhando nessas soluções e lançaremos correções e novos recursos em versões futuras.

* **ARPlaneSubsystem** ainda não é compatível. **ARPlaneManager**, **ARRaycastManager** e API relacionada, como **ARAnchorManager. AttachAnchor** , também não têm suporte no HoloLens 2.
* A **âncora** não é suportada pela comunicação remota do Holographic ainda, mas está chegando em breve.
* O rastreamento de **malha à mão** , **códigos QR** e **XRMeshSubsystem** ainda não têm suporte.
* O suporte a **âncoras espaciais do Azure** estará disponível em uma versão futura.
* **ARM64** é a única plataforma com suporte para aplicativos do HoloLens 2. A plataforma **ARM** estará disponível em uma versão futura.

## <a name="troubleshooting"></a>Solução de problemas 

Quando você suspende e retoma um aplicativo do Unity no HoloLens 2, o aplicativo não pode retomar corretamente, o que leva a 4 pontos girando na exibição do HoloLens. 
* Defina o **modo de envio de profundidade** como **nenhum** nas configurações do projeto OpenXR como uma solução alternativa
