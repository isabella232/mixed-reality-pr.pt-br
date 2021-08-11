---
title: Configuração básica de acompanhamento ocular
description: Como configurar o Acompanhamento Ocular no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Acompanhamento Ocular,
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197436"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Como começar a acompanhar o acompanhamento ocular no MRTK

Esta página aborda como configurar sua cena do MRTK do Unity para usar o acompanhamento ocular em seu aplicativo.
O exemplo a seguir pressu que você está começando com uma nova cena.
Como alternativa, você pode conferir nossos exemplos de acompanhamento ocular do [MRTK](../../example-scenes/eye-tracking-examples-overview.md) já configurados com vários exemplos excelentes nos quais você pode se basear diretamente.

## <a name="eye-tracking-requirements-checklist"></a>Lista de verificação de requisitos de acompanhamento ocular

Para que o acompanhamento ocular funcione corretamente, os requisitos a seguir devem ser atendidos.
Se você for novo no acompanhamento ocular no HoloLens 2 e como o acompanhamento ocular está definido no MRTK, não se preocupe!
Entraremos em detalhes sobre como abordar cada um deles mais adiante.

1. Um _'Eye Gaze Provedor de Dados'_ deve ser adicionado ao sistema de entrada. Isso fornece dados de acompanhamento ocular da plataforma.
2. A _funcionalidade 'GazeInput'_ deve ser habilitada no manifesto do aplicativo.
   **Essa funcionalidade pode ser definida no Unity 2019, mas no Unity 2018 e anterior, essa funcionalidade só está disponível no Visual Studio e por meio da ferramenta de build do MRTK**
3. O HoloLens **deve** ser calibrado com o olhar para o usuário atual. Confira nosso exemplo [para detectar se um usuário está calibrado com o olhar ou não.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Uma observação sobre a funcionalidade GazeInput

As ferramentas de build fornecidas pelo MRTK (ou seja, Toolkit -> Utilities -> Build Window) podem habilitar automaticamente a funcionalidade GazeInput para você. Para fazer isso, você precisa verificar se a 'Funcionalidade de Entrada do Olhar' está marcada na guia 'Opções de Build do Appx':

![Ferramentas de build do MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

Essas ferramentas encontrarão o manifesto AppX depois que o build do Unity for concluído e adicionar manualmente a funcionalidade GazeInput.
**Antes do Unity 2019,** essas ferramentas NÃO estão ativas ao usar a Janela de Build interna do Unity (ou seja, Arquivo -> Build Configurações).

Antes do Unity 2019, ao usar a janela de build do Unity, o recurso precisará ser adicionado manualmente após o build do Unity, da seguinte maneira:

1. Abra o projeto Visual Studio compilado e abra _o 'Package.appxmanifest'_ em sua solução.
2. Marque a caixa de seleção _'GazeInput'_ em _Funcionalidades_. Se você não vir uma funcionalidade _'GazeInput',_ verifique se o sistema atende aos pré-requisitos para usar o [MRTK](/windows/mixed-reality/develop/install-the-tools) (em particular a versão do SDK do Windows).

_Observe:_ Você só precisa fazer isso se criar uma nova pasta de build.
Isso significa que, se você já tiver criado seu projeto do Unity e tiver definido o appxmanifest antes e agora tiver como destino a mesma pasta novamente, não precisará reaplicar suas alterações.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configurando o acompanhamento ocular passo a passo

### <a name="setting-up-the-scene"></a>Configurando a cena

Configure o _MixedRealityToolkit_ simplesmente clicando em _'Mixed Reality Toolkit -> Configure...'_ na barra de menus.

![Configurar o MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configurando os perfis do MRTK necessários para acompanhamento ocular

Depois de configurar sua cena do MRTK, você será solicitado a escolher um perfil para o MRTK.
Você pode simplesmente selecionar _DefaultMixedRealityToolkitConfigurationProfile_ e, em seguida, selecionar a opção _'Copiar & Personalizar'._

![Perfil do MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Criar um "provedor de dados de olhar com o olhar"

- Clique na guia _"Entrada"_ em seu perfil do MRTK.
- Para editar o padrão ( _'DefaultMixedRealityInputSystemProfile'),_ clique no _botão 'Clonar'_ ao lado dele. Um menu _'Clonar Perfil'_ é exibido. Basta clicar _em "Clonar"_ na parte inferior desse menu.
- Clique duas vezes em seu novo perfil de entrada, expanda _"Provedores_ de Dados de Entrada" e selecione _'+ Adicionar Provedor de Dados'._
- Crie um novo provedor de dados:
  - Em **Tipo,** _selecione 'Microsoft.MixedReality.Toolkit. WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - Para **Plataformas,** selecione _'Windows Universal'._

![Provedor de dados do MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulando o acompanhamento ocular no Editor do Unity

Você pode simular a entrada de acompanhamento ocular no Editor do Unity para garantir que os eventos sejam disparados corretamente antes de implantar o aplicativo em seu HoloLens 2.
O sinal de olhar é simulado simplesmente usando a localização da câmera como origem do olhar e o vetor de avanço da câmera como direção do olhar.
Embora isso seja ótimo para testes iniciais, observe que ele não é uma boa ideia para movimentos de olho rápidos.
Para isso, é melhor garantir testes frequentes de suas interações com base no olhar no HoloLens 2.

1. **Habilitar o acompanhamento ocular simulado:**
    - Clique na guia _"Entrada"_ no perfil de configuração do MRTK.
    - A partir daí, navegue até _'Provedores de Dados de Entrada'_  ->  _'Serviço de Simulação de Entrada'._
    - Clone _o 'DefaultMixedRealityInputSimpulationProfile'_ para fazer alterações nele.
    - Marque a _caixa de seleção 'Simular posição ocular'._

    ![Simular os olhos do MRTK](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Desabilitar o cursor** de olhar para a cabeça padrão: em geral, é recomendável evitar mostrar um cursor de olhar ou, se absolutamente necessário, torná-lo _muito_ sutil.
É recomendável ocultar o cursor de olhar para a cabeça padrão anexado ao perfil do ponteiro de olhar do MRTK por padrão.
    - Navegue até seu perfil de configuração do MRTK -> _'Entrada'_  ->  _'Ponteiros'_
    - Clone _o 'DefaultMixedRealityInputPointerProfile'_ para fazer alterações nele.
    - Na parte superior do _'Ponteiro Configurações',_ você deve atribuir um pré-fab de cursor invisível ao _'GazeCursor'._ Você pode fazer isso selecionando o pré-fab _'EyeGazeCursor'_ da MrTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Habilitando o olhar com base no olhar no provedor de olhar

No HoloLens v1, o foco com a cabeça foi usado como técnica de apontar para a primária.
Enquanto o olhar para a cabeça ainda está disponível por meio do _GazeProvider_ no MRTK que está anexado à [câmera,](https://docs.unity3d.com/ScriptReference/Camera.html)você pode verificar para usar o olhar em vez disso marcando a caixa de seleção _'IsEyeTrackingEnabled'_ nas configurações de olhar do perfil de ponteiro de entrada.

>[!NOTE]
>Os desenvolvedores podem alternar entre o olhar e o olhar baseado em cabeça no código alterando a propriedade _'IsEyeTrackingEnabled'_ _de 'GazeProvider'._  

>[!IMPORTANT]
>Se qualquer um dos requisitos de acompanhamento ocular não for atendido, o aplicativo voltará automaticamente para o olhar baseado em cabeça.

### <a name="accessing-eye-gaze-data"></a>Acessando dados de olhar com o olhar

Agora que sua cena está configurada para usar o acompanhamento ocular, vamos dar uma olhada em como [acessá-la](eye-tracking-target-selection.md)em seus scripts: Acessando dados de acompanhamento ocular por meio de [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e seleções de destino com suporte ocular .

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Testando seu aplicativo Unity em um HoloLens 2

Criar seu aplicativo com acompanhamento ocular deve ser semelhante a como você compilaria outros HoloLens 2 aplicativos MRTK. Certifique-se de que você habilitar a funcionalidade 'Entrada de *Olhar',* conforme descrito acima na seção Uma observação sobre a funcionalidade [*GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Calibragem de olho

Por fim, não se esqueça de executar a calibragem ocular em seu HoloLens 2.
O sistema de acompanhamento ocular não retornará nenhuma entrada se o usuário não estiver calibrado.
A maneira mais fácil de chegar à calibragem é invertendo o visor e voltando para baixo.
Uma notificação do sistema deve aparecer dando boas-vindas a você como um novo usuário e solicitando que você acesse a calibragem ocular.
Como alternativa, você pode encontrar a calibragem ocular nas configurações do sistema: Configurações > calibragem > sistema > Calibragem de olho.

#### <a name="eye-tracking-permission"></a>Permissão de acompanhamento ocular

Ao iniciar o aplicativo em seu HoloLens 2 pela primeira vez, um prompt deverá aparecer solicitando ao usuário permissão para usar o acompanhamento ocular.
Se ele não estiver aparecendo, isso geralmente é uma indicação de que a funcionalidade _'GazeInput'_ não foi definida.

Depois que o prompt de permissão aparecer uma vez, ele não será mostrado automaticamente novamente.
Se você _tiver "permissão de acompanhamento ocular negada",_ poderá redefini-la Configurações -> Privacy -> Apps.

---

Isso deve começar a usar o acompanhamento ocular em seu aplicativo UNITY do MRTK.
Não se esqueça de conferir nossos tutoriais e exemplos de acompanhamento ocular do [MRTK](../../example-scenes/eye-tracking-examples-overview.md) que demonstram como usar a entrada de acompanhamento ocular e fornecer convenientemente scripts que você pode reutilizar em seus projetos.

---
[De volta ao "Acompanhamento ocular no MixedRealityToolkit"](eye-tracking-main.md)