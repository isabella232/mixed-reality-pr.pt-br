---
title: Visão geral do exemplo de acompanhamento de olho
description: Exemplo para criar eyetracking em MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144684"
---
# <a name="eye-tracking-examples"></a>Exemplos de acompanhamento de olho

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

### <a name="eye-supported-navigation"></a>[**Navegação com suporte ocular**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine que você esteja lendo algumas informações em uma exibição distante ou em seu leitor de email e, quando chegar ao final do texto exibido, o texto rolará automaticamente para cima para revelar mais conteúdo.
Ou que tal ampliar magicamente diretamente para onde você estava olhando?
Estes são alguns dos exemplos apresentados neste tutorial sobre navegação com suporte ocular.
Além disso, há um exemplo de rotação de mãos livres de hologramas 3D, fazendo com que eles girem automaticamente com base no foco atual.

**Resumo:** role, pan, zoom, rotação 3D usando uma combinação de olhos, voz e entrada à mão.

### <a name="eye-supported-positioning"></a>[**Posicionamento com suporte ocular**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

Este tutorial mostra um cenário de entrada chamado [Put-That-There](https://youtu.be/CbIn8p4_4CQ) voltando à pesquisa do MIT Media Lab no início dos anos 1980 com entrada de olho, mão e voz.
A ideia é simples: beneficie-se de seus olhos para seleção e posicionamento rápidos de destino.
Basta olhar para um holograma e dizer _"coloque_ isso", veja onde você deseja colocá-lo e diga _"lá!"._
Para posicionar seu holograma com mais precisão, você pode usar entradas adicionais de suas mãos, voz ou controladores.

**Resumo:** Posicionando hologramas usando os olhos, a voz e a entrada de mão *(arrastar e soltar*). Controles deslizantes com suporte ocular usando olhos + mãos.

### <a name="visualization-of-visual-attention"></a>**Visualização da atenção visual**

Os dados com base na aparência dos usuários fazem uma ferramenta extremamente poderosa para avaliar a usabilidade de um design e identificar problemas em fluxos de trabalho eficientes.
Este tutorial aborda diferentes visualizações de acompanhamento ocular e como elas se ajustam a diferentes necessidades.
Fornecemos exemplos básicos para registro em log e carregamento de dados de acompanhamento ocular e exemplos de como visualizá-los.

**Resumo:** mapa de atenção bidimensional (mapas de calor) em slates. Registrando & a reprodução de dados de acompanhamento ocular.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configurando os exemplos de acompanhamento ocular do MRTK

### <a name="prerequisites"></a>Pré-requisitos

Observe que usar os exemplos de acompanhamento de olho no dispositivo requer um HoloLens 2 e um pacote de aplicativo de exemplo criado com o recurso de "entrada olhar" no AppXManifest do pacote.

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

Para carregar cenas aditivas durante o tempo de execução, você deve adicionar essas cenas às suas _configurações de Build-> cenas no menu de Build_ primeiro.
É importante que a cena raiz seja mostrada como a primeira cena na lista:

![Menu de cena de configurações de compilação para exemplos de acompanhamento de olho](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. reproduzir os exemplos de acompanhamento de olho no editor do Unity

Depois de adicionar os bastidores de acompanhamento de olho às configurações de compilação e carregar o _EyeTrackingDemo-00-RootScene_, há uma última coisa que você pode querer verificar: é o script _' OnLoadStartScene '_ que está anexado ao _MixedRealityBasicSceneSetup_ gameobject habilitado? Isso é para permitir que a cena raiz saiba qual cena de demonstração carregar primeiro.

![Exemplo para o script de OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Vamos rolar! Toque _em "Reproduzir"_!
Você deverá ver várias gemas aparecerem e o menu de cena na parte superior.

![Captura de tela de exemplo da cena de seleção de destino ET](../images/eye-tracking/mrtk_et_targetselect.png)

Você também deve observar um pequeno círculo semitransparente no centro da exibição de jogo.
Isso funciona como um indicador (cursor) do seu olhar _simulado:_ basta pressionar o botão direito do _mouse_ e mover o mouse para alterar sua posição.
Quando o cursor estiver sobre as gemas, você observará que ele se ajustará ao centro da gema exibida no momento.
Essa é uma ótima maneira de testar se os eventos são disparados conforme o esperado ao _"olhar&quot;_ para um destino.
Esteja ciente de _que_ o olhar simulado por meio do controle do mouse é um suplemento bastante ruim para nossos movimentos de olho rápidos e não intencional.
No entanto, é ótimo testar a funcionalidade básica antes de iterar no design implantando-a no dispositivo HoloLens 2.
Retornando à nossa cena de exemplo de acompanhamento ocular: a gem gira desde que seja analisada e possa ser destruída por &quot;olhar&quot; para ela e ...

- Pressionar _Enter_ (que simula dizer &quot;selecionar")
- Dizendo _"selecionar"_ no microfone
- Ao pressionar _Espaço para_ mostrar a entrada da mão simulada, clique no botão esquerdo do mouse para executar uma pinçagem simulada

Descrevemos mais detalhadamente como você pode obter essas interações em nosso tutorial seleção de destino com [**suporte ocular.**](../input/eye-tracking/eye-tracking-target-selection.md)

Ao mover o cursor para a barra de menus superior na cena, você observará que o item com foco no momento realça subtly.
Você pode selecionar o item realçado no momento usando um dos métodos de confirmação descritos acima (por exemplo, pressionar _Enter_).
Dessa forma, você pode alternar entre as diferentes cenas de exemplo de acompanhamento ocular.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Como testar sub-cenas específicas

Ao trabalhar em um cenário específico, talvez você não queira passar pelo menu de cena toda vez.
Em vez disso, talvez você queira começar diretamente da cena em que está trabalhando no momento ao pressionar o _botão_ Reproduzir.
Sem problemas. Veja o que você pode fazer:

1. Carregar a cena _raiz_
2. Na cena _raiz_ , desabilite o script _' OnLoadStartScene '_
3. _Arraste e solte_ um dos cenas de teste de controle ocular descritos abaixo (ou qualquer outra cena) em sua exibição de _hierarquia_ , conforme mostrado na captura de tela abaixo.

    ![Exemplo de cena aditiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Pressione _reproduzir_

Observe que o carregamento da sub-rotina como esta não é persistente: isso significa que, se você implantar seu aplicativo no dispositivo do HoloLens 2, ele carregará apenas a cena raiz (supondo que ela apareça na parte superior das configurações de Build).
Além disso, quando você compartilha seu projeto com outras pessoas, os sub-cenas não são carregados automaticamente.

---

Agora que você sabe como fazer as cenas de exemplo de acompanhamento de olho do MRTK para funcionar, vamos continuar com mais detalhes sobre como selecionar hologramas com seus olhos: [seleção de destino com suporte de olho](../input/eye-tracking/eye-tracking-target-selection.md).

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
