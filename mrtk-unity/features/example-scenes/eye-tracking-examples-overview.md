---
title: Visão geral dos exemplos de acompanhamento ocular
description: Exemplo para criar eyetracking em MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223198"
---
# <a name="eye-tracking-examples-overview"></a>Visão geral dos exemplos de acompanhamento ocular

Este tópico descreve como começar rapidamente a usar o controle de olho no MRTK criando exemplos de acompanhamento de olho do MRTK (ativos/MRTK/exemplos/demos/EyeTracking).
Esses exemplos permitem que você experimente um de nossos novos recursos de entrada do mágico: **acompanhamento ocular**!
A demonstração inclui vários casos de uso, variando de ativações implícitas com base em olhos para como combinar diretamente as informações sobre o que você está vendo com a entrada de **voz** e **mão** .
Isso permite que os usuários selecionem e movam com rapidez e facilidade o conteúdo do Holographic em sua exibição simplesmente examinando um destino e dizendo _' Select '_ ou executando um gesto de mão.
As demonstrações também incluem um exemplo de rolagem direcionada olhar, panorâmica e zoom de texto e imagens em um Slate.
Por fim, um exemplo é fornecido para gravar e visualizar a atenção visual do usuário em um Tablet 2D.
Na seção a seguir, você encontrará mais detalhes sobre o que cada um dos diferentes exemplos no pacote de exemplo de acompanhamento de olho MRTK (assets/MRTK/examples/demos/EyeTracking) inclui:

![Lista de cenas de acompanhamento de olho](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

A seção a seguir é uma rápida visão geral do que são os bastidores da demonstração de controle de olho individual.
Os bastidores de demonstração de acompanhamento de olho MRTK são carregados de forma [aditiva](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), o que explicaremos abaixo de como configurar.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Visão geral dos exemplos de demonstração de acompanhamento de olho

### <a name="eye-supported-target-selection"></a>[**Seleção de destino com suporte de olho**](../input/eye-tracking/eye-tracking-target-selection.md)

Este tutorial demonstra a facilidade de acessar dados de olhar de olho para selecionar destinos.
Ele inclui um exemplo para um feedback sutil, mas poderoso, para fornecer ao usuário a confiança de que um alvo está concentrado sem ser impressionante.
Além disso, há um exemplo simples de notificações inteligentes que desaparecem automaticamente após serem lidas.

**Resumo**: seleções de destino rápidas e sem esforço usando uma combinação de olhos, entrada de voz e mão.

### <a name="eye-supported-navigation"></a>[**Navegação com suporte de olho**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine que você está lendo algumas informações em uma exibição distante ou em seu e-reader e quando chega ao final do texto exibido, o texto rola automaticamente para revelar mais conteúdo.
Ou como aplicar um zoom mágico diretamente para onde você estava olhando?
Estes são alguns dos exemplos demonstrados neste tutorial sobre navegação com suporte de olho.
Além disso, há um exemplo de rotação sem intervenções de hologramas 3D, fazendo com que eles giram automaticamente com base no seu foco atual.

**Resumo**: rolar, deslocar, aplicar zoom, rotação 3D usando uma combinação de olhos, entrada de voz e mão.

### <a name="eye-supported-positioning"></a>[**Posicionamento com suporte de olho**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

Este tutorial mostra um cenário de entrada chamado [Put-que-lá](https://youtu.be/CbIn8p4_4CQ) foi feito para Pesquisar do laboratório de mídia do MIT no início de 1980 com entrada de voz e olho.
A ideia é simples: beneficie-se de seus olhos para seleção e posicionamento de destino rápido.
Basta examinar um holograma e dizer _"colocar este"_, examinar onde você deseja colocá-lo e dizer _"lá!"_.
Para posicionar com mais precisão seu holograma, você pode usar entradas adicionais de suas mãos, voz ou controladores.

**Resumo**: posicionamento de hologramas usando olhos, entrada de voz e mão (*arrastar e soltar*). Controles deslizantes com suporte de olho usando olhos + mãos.

### <a name="visualization-of-visual-attention"></a>**Visualização da atenção Visual**

Os dados com base em onde os usuários procuram tornam uma ferramenta extremamente poderosa para avaliar a usabilidade de um design e identificar problemas em fluxos de trabalho eficientes.
Este tutorial discute diferentes visualizações de controle de olho e como elas se ajustam a diferentes necessidades.
Fornecemos exemplos básicos para registrar e carregar dados de acompanhamento de olho e exemplos de como visualizá-los.

**Resumo**: mapa de atenção bidimensional (calor) em slates. Gravação & reprodução de dados de controle de olho.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configurando os exemplos de acompanhamento de olho do MRTK

### <a name="prerequisites"></a>Pré-requisitos

observe que usar os exemplos de acompanhamento de olho no dispositivo requer um HoloLens 2 e um pacote de aplicativo de exemplo criado com o recurso "entrada olhar" no AppXManifest do pacote.

Para usar esses exemplos de acompanhamento de olho no dispositivo, certifique-se de seguir [estas etapas](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) antes de criar o aplicativo no Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. carregar EyeTrackingDemo-00-RootScene. Unity

O *EyeTrackingDemo-00-RootScene* é a cena base (_raiz_) que tem todos os componentes principais do MRTK incluídos.
Essa é a cena que você precisa carregar primeiro e a partir da qual você executará as demonstrações de controle de olho.
Ele apresenta um menu de cena gráfica que permite alternar facilmente entre os diferentes exemplos de controle de olho que serão [carregados](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)de forma aditiva.

![Menu cena no exemplo de acompanhamento de olho](../images/eye-tracking/mrtk_et_scenemenu.jpg)

A cena raiz inclui alguns componentes principais que persistirão em bastidores com carregamento aditivo, como os perfis configurados por MRTK e a câmera de cena.
O _MixedRealityBasicSceneSetup_ (veja a captura de tela abaixo) inclui um script que irá carregar automaticamente a cena referenciada na inicialização.
Por padrão, isso é _EyeTrackingDemo-02-TargetSelection_.  

![Exemplo para o script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. adicionando cenas ao menu de compilação

para carregar cenas aditivas durante o tempo de execução, você deve adicionar essas cenas ao _Build Configurações > cenas no menu de build_ primeiro.
É importante que a cena raiz seja mostrada como a primeira cena na lista:

![menu criar Configurações cena para exemplos de acompanhamento de olho](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. reproduzir os exemplos de acompanhamento de olho no editor do Unity

depois de adicionar os bastidores de acompanhamento de olho à Configurações de compilação e carregar o _EyeTrackingDemo-00-RootScene_, há uma última coisa que você pode querer verificar: é o script _' OnLoadStartScene '_ que está anexado ao _MixedRealityBasicSceneSetup_ gameobject habilitado? Isso é para permitir que a cena raiz saiba qual cena de demonstração carregar primeiro.

![Exemplo para o script de OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Vamos rolar! Clique em _"reproduzir"_!
Você deve ver várias Gems exibidas e o menu de cena na parte superior.

![Captura de tela de exemplo do destino ET selecionar cena](../images/eye-tracking/mrtk_et_targetselect.png)

Você também deve observar um pequeno círculo semitransparente no centro do modo de exibição do jogo.
Isso age como um indicador (cursor) de seu _olho simulado olhar_: simplesmente pressione o _botão direito do mouse_ e mova o mouse para alterar sua posição.
Quando o cursor estiver focalizando as Gems, você observará que ele se ajustará ao centro do GEM exibido no momento.
Essa é uma ótima maneira de testar se os eventos são disparados conforme o esperado ao _"olhar&quot;_ em um destino.
Lembre-se de que o _olho simulado olhar_ por meio do controle do mouse é um complemento bem baixo para nossos movimentos de olho rápidos e inadvertidos.
no entanto, é ótimo para testar a funcionalidade básica antes de iterar no design implantando-a no dispositivo HoloLens 2.
Voltando à nossa cena de exemplo de acompanhamento de olho: a gem gira enquanto estiver sendo examinada e pode ser destruída por &quot;olhando&quot; e...

- Pressionar _Enter_ (que simula dizer &quot;Select")
- Dizendo _"Select"_ no microfone
- Ao pressionar _espaço_ para mostrar a entrada do lado simulado, clique no botão esquerdo do mouse para executar uma pinçagem simulada

Descrevemos em mais detalhes como você pode obter essas interações em nosso tutorial [**de seleção de destino com suporte de olho**](../input/eye-tracking/eye-tracking-target-selection.md) .

Ao mover o cursor para cima até a barra de menus superior na cena, você observará que o item atualmente focalizado será destacado sutilmente.
Você pode selecionar o item realçado no momento usando um dos métodos de confirmação descritos acima (por exemplo, pressionando _Enter_).
Dessa forma, você pode alternar entre os bastidores de amostra de controle de olho diferentes.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. como testar sub-cenas específicas

Ao trabalhar em um cenário específico, talvez você não queira passar pelo menu cena todas as vezes.
Em vez disso, talvez você queira iniciar diretamente a partir da cena em que você está trabalhando no momento ao pressionar o botão _reproduzir_ .
Sem problemas. Veja o que você pode fazer:

1. Carregar a cena _raiz_
2. Na cena _raiz_ , desabilite o script _' OnLoadStartScene '_
3. _Arraste e solte_ um dos cenas de teste de controle ocular descritos abaixo (ou qualquer outra cena) em sua exibição de _hierarquia_ , conforme mostrado na captura de tela abaixo.

    ![Exemplo de cena aditiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Pressione _reproduzir_

observe que o carregamento da sub-rotina como esta não é persistente: isso significa que, se você implantar seu aplicativo no dispositivo HoloLens 2, ele carregará apenas a cena raiz (supondo que apareça na parte superior do Configurações de compilação).
Além disso, quando você compartilha seu projeto com outras pessoas, os sub-cenas não são carregados automaticamente.

---

Agora que você sabe como fazer as cenas de exemplo de acompanhamento de olho do MRTK para funcionar, vamos continuar com mais detalhes sobre como selecionar hologramas com seus olhos: [seleção de destino com suporte de olho](../input/eye-tracking/eye-tracking-target-selection.md).

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
