---
title: Configurar seu projeto sem MRTK
description: Saiba como configurar um novo projeto do Unity para o Windows Mixed Reality sem o Mixed Reality Toolkit.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117620"
---
# <a name="configuring-your-project-without-mrtk"></a>Como configurar seu projeto sem o MRTK

O Windows Mixed Reality (WMR) é uma plataforma da Microsoft introduzida como parte do sistema operacional Windows 10. A plataforma WMR permite que você crie aplicativos que processam conteúdo digital em dispositivos de vídeo Holographic e VR.

Embora a Microsoft e a Comunidade tenham criado ferramentas abertas como o [MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.  A documentação a seguir demonstrará como configurar corretamente um projeto para o desenvolvimento de realidade misturada se você estiver usando MRTK ou não.  As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.

> [!NOTE]
> Você sempre pode importar MRTK posteriormente, portanto, não há penalidade para passar a rota manual primeiro.

Se você escolher a configuração manual do WMR, as configurações que você precisa alterar serão divididas em duas categorias: por projeto e por cena.

## <a name="per-project-settings"></a>Configurações por projeto

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  Selecione **arquivo > configurações de Build...**
2.  Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Definir a **arquitetura** para o **ARM 64**
4.  Definir o **dispositivo de destino** para o **HoloLens**
5.  Definir **tipo de compilação** como **D3D**
6.  Definir o **SDK do UWP** para o **mais recente instalado**
7.  Definir a **configuração de Build** como **Release** porque há problemas de desempenho conhecidos com a depuração

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.

### <a name="for-xrsdk"></a>Para XRSDK 

1. No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**

2. Selecione **instalar o gerenciamento de plugin XR**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-5.png)

3. Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-7.png)

4. Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**
5. Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar **OpenXR (visualização)** ou a **realidade mista do Windows**
6. Você pode escolher qualquer tempo de execução.  Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir tentar a **OpenXR (versão prévia)**, selecione a caixa OpenXR (versão prévia) e examine nosso guia para [usar o plug-in informativo da realidade misturada para o Unity](openxr-getting-started.md) para se configurar corretamente para esses dispositivos antes de retornar a este tutorial
7. Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Para o XR herdado 

> [!CAUTION]
> O XR herdado é preterido no Unity 2019 e removido no Unity 2020.

1. Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**
2. Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual
3. Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**
4. Definir **modo de renderização estéreo** para **instância de passagem única**
5. Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Atualizando o manifesto

Seu aplicativo agora pode manipular a renderização Holographic e a entrada espacial. No entanto, seu aplicativo precisa declarar os recursos apropriados em seu manifesto para aproveitar determinadas funcionalidades. Você pode encontrar os recursos de seus projetos acessando **configurações do Player > configurações para Plataforma Universal do Windows > configurações de publicação > recursos**. 

É recomendável que você faça as declarações de manifesto no Unity para incluí-las em todos os projetos futuros que você exportar. Os recursos aplicáveis para habilitar as APIs do Unity comumente usadas para realidade misturada são:

|  Funcionalidade  |  APIs que exigem capacidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a malhas de [mapeamento espacial](../../design/spatial-mapping.md) no HoloLens) &mdash; *nenhum recurso necessário para acompanhamento espacial geral do headset* | 
|  Integrada  |  VideoCapture e fotocaptura | 
|  PicturesLibrary / VideosLibrary  |  VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e para usar o criador de perfil do Unity) | 

### <a name="quality-settings"></a>Configurações de qualidade

O HoloLens tem uma GPU de classe móvel. Se seu aplicativo estiver direcionando para o HoloLens, você desejará começar com as configurações de qualidade em seu aplicativo ajustadas para um desempenho mais rápido, a fim de garantir que ela mantenha a taxa completa de quadros.  Depois que você tiver as suas próximas em seu desenvolvimento, poderá considerar upping as configurações de qualidade para encontrar o equilíbrio certo de qualidade e desempenho: 

1. Selecione **Editar configurações do projeto > > qualidade** 
2. Selecione o **menu suspenso** sob o logotipo da  **Windows Store**   e selecione  **muito baixo**. Você saberá que a configuração foi aplicada corretamente quando a caixa na coluna da Windows Store e a linha muito baixa estiverem verdes 
3. Na seção **sombras**   , selecione **desabilitar sombras** 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações de qualidade realçada](images/wmr-config-img-10.png)<br>
*Configurações de qualidade do Unity*

## <a name="per-scene-settings"></a>Configurações por cena

### <a name="unity-camera-settings"></a>Configurações da câmera do Unity

Com a **realidade virtual suportada** marcada, o componente da [câmera do Unity](camera-in-unity.md) lida com o [controle de cabeçalho e a renderização de estereoscópico](../platform-capabilities-and-apis/rendering.md). Isso significa que não há necessidade de substituir o objeto da câmera principal por uma câmera personalizada.

Se seu aplicativo estiver direcionando para o HoloLens especificamente, você precisará alterar algumas configurações para otimizar para as exibições transparentes do dispositivo. Essas configurações permitem que o conteúdo do Holographic seja mostrado ao mundo físico:

1. Na **hierarquia**, selecione a **câmera principal**
2. No painel de **inspetores** , defina a **posição** de transformação como **0, 0,** portanto, o local da cabeça do usuário começa na origem do Unity World.
3. Alterar **sinalizadores claros** para **cor sólida**.
4. Altere a cor do **plano de fundo** para **RGBA 0, 0, 0, 0**. O preto é renderizado como transparente no HoloLens.
5. Alterar os **planos de recorte-próximo** ao [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

![Captura de tela da guia Inspetor aberta no editor do Unity](images/wmr-config-img-11.png)<br>
*Configurações da câmera do Unity*

> [!IMPORTANT]
> Se você excluir e criar uma nova câmera, verifique se a nova câmera está marcada como **MainCamera**.

## <a name="next-steps"></a>Próximas etapas

Agora que seu projeto está pronto, você pode começar a desenvolver sua experiência de realidade mista:

* Adicionar [blocos de construção principais](unity-development-overview.md#2-core-building-blocks)
* Confira as [APIs e os recursos de plataforma](unity-development-overview.md#3-advanced-features) disponíveis
* Saiba como [implantar seu aplicativo](../platform-capabilities-and-apis/using-visual-studio.md#)
* Usar o [simulador de realidade misturada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)