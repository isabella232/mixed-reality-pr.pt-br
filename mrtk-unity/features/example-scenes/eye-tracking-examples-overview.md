---
title: Visão geral de exemplos de acompanhamento ocular
description: Exemplo para criar o retrocesso no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175538"
---
# <a name="eye-tracking-examples-overview"></a>Visão geral de exemplos de acompanhamento ocular

Este tópico descreve como começar rapidamente com o acompanhamento ocular no MRTK criando exemplos de acompanhamento ocular do MRTK (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking).
Esses exemplos permitem que você experimente uma de nossas novas funcionalidades de entrada mágica: **Acompanhamento ocular!**
A demonstração inclui vários casos de uso, desde ativações implícitas baseadas em olho  até como combinar perfeitamente informações sobre o que você está vendo com a entrada de voz **e** mão.
Isso permite que os usuários selecionem e movam conteúdo holográfico de forma rápida e fácil em sua exibição simplesmente observando um destino e dizendo _"Selecionar"_ ou executando um gesto de mão.
As demonstrações também incluem um exemplo de rolagem direcionada ao olhar, panor rolante e zoom de texto e imagens em um slate.
Por fim, um exemplo é fornecido para gravar e visualizar a atenção visual do usuário em um slate 2D.
Na seção a seguir, você encontrará mais detalhes sobre o que cada uma das diferentes amostras no pacote de exemplo de acompanhamento ocular do MRTK (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking) inclui:

![Lista de cenas de acompanhamento ocular](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

A seção a seguir é uma visão geral rápida do que são as cenas de demonstração de acompanhamento ocular individuais.
As cenas de demonstração de acompanhamento ocular do MRTK são carregadas [aditivamente,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)que explicaremos abaixo como configurar.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Visão geral dos exemplos de demonstração de acompanhamento ocular

### <a name="eye-supported-target-selection"></a>[**Seleção de destino com suporte ocular**](../input/eye-tracking/eye-tracking-target-selection.md)

Este tutorial demonstra a facilidade de acessar dados de olhar para selecionar destinos.
Ele inclui um exemplo de comentários sutis, porém poderosos, para fornecer ao usuário a confiança de que um destino está focado sem sobrecarregá-lo.
Além disso, há um exemplo simples de notificações inteligentes que desaparecem automaticamente após serem lidas.

**Resumo:** seleções de destino rápidas e sem esforço usando uma combinação de olhos, voz e entrada de mão.

### <a name="eye-supported-navigation"></a>[**Navegação com suporte ocular**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine que você está lendo algumas informações sobre uma exibição distante ou seu leitor de email e quando você chega ao final do texto exibido, o texto rola automaticamente para cima para revelar mais conteúdo.
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

Observe que o uso dos exemplos de acompanhamento ocular no dispositivo requer um HoloLens 2 e um pacote de aplicativo de exemplo criado com a funcionalidade "Entrada de Olhar" no AppXManifest do pacote.

Para usar esses exemplos de acompanhamento ocular no [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) dispositivo, siga estas etapas antes de criar o aplicativo Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Carregar EyeTrackingDemo-00-RootScene.unity

O *EyeTrackingDemo-00-RootScene* é a cena base _(_ raiz) que tem todos os componentes principais do MRTK incluídos.
Essa é a cena que você precisa carregar primeiro e da qual executará as demonstrações de acompanhamento ocular.
Ele apresenta um menu de cena gráfica que permite alternar facilmente entre os diferentes exemplos de acompanhamento ocular que serão [carregados aditivamente.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)

![Menu cena no exemplo de acompanhamento ocular](../images/eye-tracking/mrtk_et_scenemenu.jpg)

A cena raiz inclui alguns componentes principais que persistirão nas cenas carregadas aditivamente, como os perfis configurados pelo MRTK e a câmera da cena.
O _MixedRealityBasicSceneSetup_ (veja a captura de tela abaixo) inclui um script que carregará automaticamente a cena referenciada na inicialização.
Por padrão, é _EyeTrackingDemo-02-TargetSelection._  

![Exemplo para o script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Adicionar cenas ao menu de build

Para carregar cenas aditivas durante o runtime, você deve adicionar essas cenas ao menu Criar Configurações _-> Cenas_ no Build primeiro.
É importante que a cena raiz seja mostrada como a primeira cena na lista:

![Criar Configurações de cena para amostras de acompanhamento ocular](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Reproduzir os exemplos de acompanhamento ocular no editor do Unity

Depois de adicionar as cenas de acompanhamento ocular ao Build Configurações e carregar o _EyeTrackingDemo-00-RootScene,_ há uma última coisa que você pode querer verificar: O script _'OnLoadStartScene'_ anexado ao _MixedRealityBasicSceneSetup_ GameObject está habilitado? Isso é para permitir que a cena raiz saiba qual cena de demonstração carregar primeiro.

![Exemplo para o OnLoad_StartScene script](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

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

1. Carregar a _cena_ raiz
2. Na cena _raiz,_ desabilite o script _'OnLoadStartScene'_
3. _Arraste e solte uma_ das cenas de teste de acompanhamento ocular  descritas abaixo (ou qualquer outra cena) na exibição Hierarquia, conforme mostrado na captura de tela abaixo.

    ![Exemplo de cena aditiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Pressione _Reproduzir_

Observe que carregar a sub-cena como esta não é persistente: isso significa que, se você implantar seu aplicativo no dispositivo HoloLens 2, ele carregará apenas a cena raiz (supondo que ela apareça na parte superior do seu build Configurações).
Além disso, quando você compartilha seu projeto com outras pessoas, as sub-cenas não são carregadas automaticamente.

---

Agora que você sabe como fazer com que as cenas de exemplo de acompanhamento ocular do MRTK funcionem, vamos continuar nos aprofundando em como selecionar hologramas com seus [olhos:](../input/eye-tracking/eye-tracking-target-selection.md)seleção de destino com suporte ocular.

---
[De volta ao "Acompanhamento ocular no MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
