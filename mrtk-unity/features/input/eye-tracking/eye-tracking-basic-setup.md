---
title: Configuração básica de acompanhamento ocular
description: Como configurar o Acompanhamento Ocular no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Acompanhamento Ocular,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144090"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Como começar a acompanhar o acompanhamento ocular no MRTK

Esta página aborda como configurar sua cena do MRTK do Unity para usar o acompanhamento ocular em seu aplicativo.
O exemplo a seguir pressu que você está começando com uma nova cena.
Como alternativa, você pode conferir nossos exemplos de acompanhamento ocular do [MRTK](../../example-scenes/eye-tracking-examples-overview.md) já configurados com vários exemplos excelentes nos quais você pode se basear diretamente.

## <a name="eye-tracking-requirements-checklist"></a>Lista de verificação de requisitos de acompanhamento ocular

Para que o acompanhamento ocular funcione corretamente, os requisitos a seguir devem ser atendidos.
Se você for novo no acompanhamento ocular no HoloLens 2 e em como o acompanhamento ocular está definido no MRTK, não se preocupe!
Entraremos em detalhes sobre como abordar cada um deles mais adiante.

1. Um _'Eye Gaze Provedor de Dados'_ deve ser adicionado ao sistema de entrada. Isso fornece dados de acompanhamento ocular da plataforma.
2. A _funcionalidade 'GazeInput'_ deve ser habilitada no manifesto do aplicativo.
   **Essa funcionalidade pode ser definida no Unity 2019, mas no Unity 2018 e anterior, essa funcionalidade só está disponível no Visual Studio e por meio da ferramenta de build do MRTK**
3. O HoloLens **deve** ser calibrado com o olhar para o usuário atual. Confira nosso exemplo [para detectar se um usuário está calibrado com o olhar ou não.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Uma observação sobre a funcionalidade GazeInput

As ferramentas de build fornecidas pelo MRTK (ou seja, Kit de Ferramentas de Realidade Misturada -> Utilities -> Build Window) podem habilitar automaticamente a funcionalidade GazeInput para você. Para fazer isso, você precisa verificar se a 'Funcionalidade de Entrada do Olhar' está marcada na guia 'Opções de Build do Appx':

![Ferramentas de build do MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

Essa ferramenta encontrará o manifesto do AppX após a conclusão da compilação do Unity e adicionará manualmente o recurso GazeInput.
**Antes do Unity 2019, essas ferramentas não estão ativas ao usar a janela de compilação interna do Unity** (ou seja, configurações de compilação de > de arquivo).

Antes do Unity 2019, ao usar a janela de compilação do Unity, a capacidade precisará ser adicionada manualmente após a compilação do Unity, da seguinte maneira:

1. Abra seu projeto do Visual Studio compilado e, em seguida, abra o _' Package. appxmanifest '_ em sua solução.
2. Certifique-se de marcar a caixa de seleção _' GazeInput '_ em _recursos_. Se você não vir uma funcionalidade _' GazeInput '_ , verifique se o seu sistema atende aos [pré-requisitos para usar o MRTK](/windows/mixed-reality/develop/install-the-tools) (em particular a versão de SDK do Windows).

_Observação:_ Você só precisa fazer isso se criar uma nova pasta de compilação.
Isso significa que, se você já tiver criado seu projeto do Unity e configurado o appxmanifest antes e agora direcionar a mesma pasta novamente, não será necessário reaplicar as alterações.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configurando passo a passo de acompanhamento de olho

### <a name="setting-up-the-scene"></a>Configurando a cena

Configure o _MixedRealityToolkit_ simplesmente clicando em _' Mixed Reality Toolkit-> configurar... '_ na barra de menus.

![Configurar MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configurando os perfis de MRTK necessários para acompanhamento de olho

Depois de configurar sua cena do MRTK, você será solicitado a escolher um perfil para MRTK.
Você pode simplesmente selecionar _DefaultMixedRealityToolkitConfigurationProfile_ e, em seguida, selecionar a opção _' Copy & Custom '_ .

![Perfil de MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Criar um "provedor de dados olhar de olho"

- Clique na guia _' entrada '_ em seu perfil do MRTK.
- Para editar um padrão ( _' DefaultMixedRealityInputSystemProfile '_ ), clique no botão _' clonar '_ ao lado dele. Um menu _'Clonar Perfil'_ é exibido. Basta clicar _em "Clonar"_ na parte inferior desse menu.
- Clique duas vezes em seu novo perfil de entrada, expanda _"Provedores_ de Dados de Entrada" e selecione _'+ Adicionar Provedor de Dados'._
- Crie um novo provedor de dados:
  - Em **Tipo,** _selecione 'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - Para **Plataformas,** selecione _'Windows Universal'._

![Provedor de dados do MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulando o acompanhamento ocular no Editor do Unity

Você pode simular a entrada de acompanhamento ocular no Editor do Unity para garantir que os eventos sejam disparados corretamente antes de implantar o aplicativo no HoloLens 2.
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
    - Navegue até o perfil de configuração do MRTK-> _'_  ->  _ponteiros_ ' de entrada '
    - Clone o _' DefaultMixedRealityInputPointerProfile '_ para fazer alterações nele.
    - Na parte superior das _' configurações do ponteiro '_, você deve atribuir um cursor invisível pré-fabricado ao _' GazeCursor '_. Você pode fazer isso selecionando o pré-fabricado _' EyeGazeCursor '_ do MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Habilitando olhar com base nos olhos no provedor olhar

No HoloLens v1, o Head olhar foi usado como uma técnica apontadora primária.
Embora o Head olhar ainda esteja disponível por meio do _GazeProvider_ no MRTK que está anexado à sua [câmera](https://docs.unity3d.com/ScriptReference/Camera.html), você pode marcar para usar o olho olhar em vez disso, marcando a caixa de seleção _' IsEyeTrackingEnabled '_ nas configurações de olhar do perfil de ponteiro de entrada.

>[!NOTE]
>Os desenvolvedores podem alternar entre olhar com base nos olhos e olhars baseados em cabeçalho no código, alterando a propriedade _' IsEyeTrackingEnabled '_ de _' GazeProvider '_.  

>[!IMPORTANT]
>Se qualquer um dos requisitos de acompanhamento de olho não for atendido, o aplicativo voltará automaticamente para o olhar baseado em cabeçalho.

### <a name="accessing-eye-gaze-data"></a>Acessando dados de olhar de olho

Agora que sua cena está configurada para usar o acompanhamento de olho, vamos dar uma olhada em como acessá-la em seus scripts: [acessar dados de controle de olho por meio de EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e [seleções de destino com suporte de olho](eye-tracking-target-selection.md).

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Testando seu aplicativo Unity em um HoloLens 2

Criar seu aplicativo com acompanhamento de olho deve ser semelhante a como você compilaria outros aplicativos do HoloLens 2 MRTK. Verifique se você habilitou a funcionalidade *' entrada olhar '* , conforme descrito acima na seção [*uma observação sobre o recurso GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Calibragem de olho

Por fim, não se esqueça de executar a calibragem de olho no seu HoloLens 2.
O sistema de controle de olho não retornará nenhuma entrada se o usuário não for calibrado.
A maneira mais fácil de chegar à calibragem é folhear o visor e fazer o backup.
Uma notificação do sistema deve aparecer de boas-vindas como um novo usuário e pedindo que você passe pela calibragem de olho.
Como alternativa, você pode encontrar a calibragem de olho nas configurações do sistema: configurações > sistema > calibragem > executar calibragem de olhos.

#### <a name="eye-tracking-permission"></a>Permissão de acompanhamento de olho

Ao iniciar o aplicativo no seu HoloLens 2 pela primeira vez, um prompt deve ser exibido solicitando ao usuário a permissão para usar o controle ocular.
Se não estiver aparecendo, isso geralmente é uma indicação de que a funcionalidade _' GazeInput '_ não foi definida.

Depois que o prompt de permissão for mostrado uma vez, ele não será exibido automaticamente de novo.
Se você _"negou a permissão de acompanhamento de olho"_, poderá redefinir isso em configurações-> privacidade-> aplicativos.

---

Isso deve ajudá-lo a começar a usar o acompanhamento de olho em seu aplicativo do MRTK Unity.
Não se esqueça de conferir [nossos tutoriais e exemplos de acompanhamento de olho do MRTK](../../example-scenes/eye-tracking-examples-overview.md) demonstrando como usar a entrada de controle de olho e fornecer convenientemente os scripts que podem ser reutilizados em seus projetos.

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](eye-tracking-main.md)