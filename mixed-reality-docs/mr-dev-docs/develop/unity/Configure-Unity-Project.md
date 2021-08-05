---
title: Configurar seu projeto sem o MRTK
description: Saiba como configurar um novo projeto do Unity para Windows Mixed Reality sem o Toolkit.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidade misturada, desenvolvimento, começar, novo projeto, Windows Mixed Reality, UWP, XR, desempenho
ms.openlocfilehash: 85f8dee3208ce2c2a3bd328641544cbba0525cabdd1bf99404065572aeb354cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210969"
---
# <a name="configuring-your-project-without-mrtk"></a>Como configurar seu projeto sem o MRTK

Windows Mixed Reality (WMR) é uma plataforma da Microsoft introduzida como parte do Windows 10 operacional. A plataforma WMR permite que você crie aplicativos que renderizam conteúdo digital em dispositivos holográficos e de exibição de VR.

Embora a Microsoft e a comunidade tenham criado ferramentas de software livre, como [o MRTK (Mixed Reality Toolkit),](/windows/mixed-reality/mrtk-unity/configuration/usingupm) que configurará automaticamente o ambiente wmr, muitos desenvolvedores desejam criar suas experiências desde o zero.  A documentação a seguir demonstrará como configurar corretamente um projeto para desenvolvimento de Realidade Misturada, independentemente de você estar usando o MRTK ou não.  As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.

> [!NOTE]
> Você sempre pode importar o MRTK posteriormente, portanto, não há nenhuma penalidade para ir para a rota manual primeiro.

Se você escolher a configuração manual do WMR, as configurações que você precisa alterar serão divididas em duas categorias: por projeto e por cena.

## <a name="per-project-settings"></a>Configurações por projeto

Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela Configurações build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando HoloLens 2, será necessário alternar para a Plataforma de Windows Universal:

1.  Selecione **Arquivo > Build Configurações...**
2.  Selecione **Plataforma Windows Universal** na lista Plataforma e selecione **Alternar Plataforma**
3.  Defina a **Arquitetura** como **ARM 64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina o **Tipo de Build** como **D3D**
6.  Defina o **SDK do UWP** como **Último instalado**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela Configurações build aberta no editor do Unity com a Plataforma universal Windows realçada](images/wmr-config-img-4.png)

Depois de configurar sua plataforma, você precisa permitir que o Unity saiba para criar uma [exibição](../../design/app-views.md) imersiva em vez de uma exibição 2D quando exportada.

### <a name="for-xrsdk"></a>Para XRSDK 

1. No Editor do Unity, navegue até **Editar > Project configurações e** selecione Gerenciamento de **Plug-in XR**

2. Selecione **Instalar o Gerenciamento de Plug-in do XR**

![Captura de tela Project Configurações janela aberta no editor do Unity com o gerenciamento de plug-in XR realçada](images/wmr-config-img-5.png)

3. Selecione **Inicializar XR na Inicialização** **e Windows Mixed Reality**

![Captura de tela Project janela configurações aberta no editor do Unity com o gerenciamento de plug-in XR realçada](images/wmr-config-img-7.png)

4. Expanda a **seção Gerenciamento de Plug-inS XR** e selecione **a guia Windows Plataforma Configurações Univeral**
5. Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar **OpenXR** **ou Windows Mixed Reality**. 
    * Você pode escolher qualquer runtime.  Se você estiver desenvolvendo especificamente para o HoloLens 2 ou o HP Reverb G2 e decidir experimentar o **OpenXR,** selecione a caixa OpenXR e revise nosso guia para Usar o plug-in [OpenXR](./xr-project-setup.md) de Realidade Misturada para Unity para se configurar corretamente para esses dispositivos antes de retornar a este tutorial

> [!NOTE]
> A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.  Conforme migramos para esse caminho, no Unity 2021.1, o plug-in XR do Windows será preterido e removido em 2021.2, tornando o OpenXR o único caminho com suporte. Você pode encontrar mais informações em [Usando o plug-in OpenXR](./xr-project-setup.md)de Realidade Misturada .

6. Se você decidir escolher o **plug-in Windows Mixed Reality,** marque todas as caixas e de definir Modo de **Envio** de Profundidade **como Profundidade 16 Bits**

![Captura de tela Project janela configurações aberta no editor do Unity com a Windows Mixed Reality realçada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Para XR herddo 

> [!CAUTION]
> O XR herdado foi preterido no Unity 2019 e removido no Unity 2020.

1. Abra **o player Configurações...** no **build Configurações... janela** e expanda o **grupo de Configurações** XR
2. Na seção **XR Configurações,** selecione **Realidade Virtual Com** Suporte para adicionar a lista Dispositivos de Realidade Virtual
3. Definir **Formato de Profundidade** como Profundidade de **16 bits e** habilitar o **Compartilhamento de Buffer de Profundidade**
4. Definir **o modo de renderização estéreo** como instância de passagem **única**
5. Selecione **WSA Holographic Remoting Supported** se você quiser usar a remoting holográfica 

![Captura de tela Project janela configurações aberta no editor do Unity com a seção Configurações do player realçada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Atualizando o manifesto

Seu aplicativo agora pode lidar com a renderização holográfica e a entrada espacial. No entanto, seu aplicativo precisa declarar os recursos apropriados em seu manifesto para aproveitar determinada funcionalidade. Você pode encontrar os recursos de seus projetos indo para **Player Configurações > Configurações plataforma universal Windows plataforma**> de Configurações > recursos . 

É recomendável que você faça as declarações de manifesto no Unity para incluí-las em todos os projetos futuros exportados. As funcionalidades aplicáveis para habilenciar APIs do Unity comumente usadas para Realidade Misturada são:

|  Funcionalidade  |  APIs que exigem funcionalidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a [malhas](../../design/spatial-mapping.md) de mapeamento espacial HoloLens) Nenhuma funcionalidade necessária para o acompanhamento &mdash; *espacial geral do headset* | 
|  Webcam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture ou VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e para usar o Unity Profiler) | 

### <a name="quality-settings"></a>Configurações de qualidade

HoloLens tem uma GPU de classe móvel. Se seu aplicativo estiver direcionando HoloLens, comece com as configurações de qualidade em seu aplicativo ajustadas para desempenho mais rápido para garantir que ele mantenha a taxa de quadros completa.  Depois que você tiver seu desenvolvimento, considere aumentar as configurações de qualidade para encontrar o equilíbrio certo de qualidade e desempenho: 

1. Selecione **Editar > Project Configurações > Qualidade** 
2. Selecione o **menu suspenso no** logotipo Windows  **Store** e selecione   Muito  **Baixo.** Você sabe que a configuração é aplicada corretamente quando a caixa na coluna Windows Store e a linha Muito Baixa está verde 
3. Na **** seção   Sombras, selecione **Desabilitar Sombras** 

![Captura de tela Project janela configurações aberta no editor do Unity com a seção configurações de qualidade realçada](images/wmr-config-img-10.png)<br>
*Configurações de qualidade do Unity*

## <a name="per-scene-settings"></a>Configurações por cena

### <a name="unity-camera-settings"></a>Configurações de câmera do Unity

Com **a realidade virtual com suporte marcada,** o componente Câmera do [Unity](camera-in-unity.md) lida com o acompanhamento de cabeça e [a renderização estereografada.](../platform-capabilities-and-apis/rendering.md) Isso significa que não há necessidade de substituir o objeto Câmera Principal por uma câmera personalizada.

Se seu aplicativo estiver direcionando HoloLens especificamente, você precisará alterar algumas configurações para otimizar as exibições transparentes do dispositivo. Essas configurações permitem que seu conteúdo holográfico seja passado para o mundo físico:

1. Na Hierarquia **,** selecione a **Câmera Principal**
2. No painel **Inspetor,** de  definir a posição de transformação como **0, 0, 0** para que o local da cabeça do usuário comece na origem do mundo do Unity.
3. Altere **Limpar Sinalizadores** para **Cor Sólida**.
4. Altere **a cor da** tela de fundo para **RGBA 0,0,0,0**. O preto é renderiza como transparente HoloLens.
5. Alterar **planos de recorte – próximo** ao HoloLens [recomendado](camera-in-unity.md#using-clipping-planes) 0,85 (metros).

![Captura de tela da guia inspetor aberta no editor do Unity](images/wmr-config-img-11.png)<br>
*Configurações de câmera do Unity*

> [!IMPORTANT]
> Se você excluir e criar uma nova câmera, certifique-se de que sua nova câmera seja marcada como **MainCamera.**

## <a name="next-steps"></a>Próximas etapas

Agora que seu projeto está pronto, você pode começar a desenvolver sua experiência de Realidade Misturada:

* Adicionar [blocos de construção principais](unity-development-overview.md#2-core-building-blocks)
* Confira as [APIs](unity-development-overview.md#3-advanced-features) e as funcionalidades da plataforma disponíveis
* Saiba como implantar [seu aplicativo](../platform-capabilities-and-apis/using-visual-studio.md#)
* Usar o [simulador de Realidade Misturada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)