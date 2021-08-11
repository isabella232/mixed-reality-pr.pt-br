---
title: Como atualizar aplicativos UWP 2D para o Windows Mixed Reality
description: Este artigo descreve como atualizar seu aplicativo 2D Universal Windows Platform para ser executado em HoloLens e Windows Mixed Reality headsets imersivos.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Aplicativo 2D, UWP, aplicativo simples, HoloLens, headset imersivo, modelo de aplicativo, botão voltar, barra de aplicativos, dpi, resolução, escala, portação, HoloLens 1ª geração, HoloLens 2, headset de realidade misturada, headset de realidade misturada do Windows, migração, Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195968"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>Como atualizar aplicativos UWP 2D para o Windows Mixed Reality

Windows Mixed Reality permite que os usuários vejam hologramas como se eles estivesse ao redor deles no mundo físico e digital. No núcleo, os HoloLens e os computadores desktop aos que você anexa acessórios de headset imersivos são Windows 10 dispositivos. Você pode executar quase todos os aplicativos UWP (Plataforma universal Windows) na Store como aplicativos 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Criando um aplicativo UWP 2D para realidade misturada

A primeira etapa para trazer um aplicativo 2D para headsets de realidade misturada é fazer com que seu aplicativo seja executado como um aplicativo 2D padrão no monitor da área de trabalho.

### <a name="building-a-new-2d-uwp-app"></a>Criando um novo aplicativo UWP 2D

Para criar um novo aplicativo 2D para realidade misturada, você cria um aplicativo UWP (Plataforma de Windows Universal) 2D padrão. Nenhuma outra alteração de aplicativo é necessária para que o aplicativo seja executado como um slate na realidade misturada.

Para começar a criar um aplicativo UWP 2D, confira o artigo Criar [seu primeiro](/windows/uwp/get-started/your-first-app) aplicativo.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Trazer um aplicativo 2D Store existente para a UWP

Se você já tiver um aplicativo de Windows 2D na Store, certifique-se de que ele está direcionando o Windows 10 UWP (Plataforma universal Windows). Aqui estão todos os possíveis pontos de partida que você pode ter com seu aplicativo da Store hoje:
<br>

|  Ponto inicial  |  Destino da plataforma de manifesto AppX  |  Como tornar isso universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto do aplicativo Silverlight |  [Migrar para o WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone Universal 8.1  |  8.1 Manifesto do AppX que não inclui o destino da plataforma  |  [Migrar seu aplicativo para a Plataforma de Windows Universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8  |  8 Manifesto do AppX que não inclui o destino da plataforma  |  [Migrar seu aplicativo para a Plataforma de Windows Universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8.1 Universal  |  8.1 Manifesto do AppX que não inclui o destino da plataforma  |  [Migrar seu aplicativo para a Plataforma de Windows Universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

Se você tiver um aplicativo 2D Unity criado hoje como um aplicativo Win32 no PC, mac & destino de build autônomo do **Linux,** alternar para o destino de build da Plataforma **Universal Windows** para realidade misturada.

Vamos falar sobre maneiras pelas quais você pode restringir seu aplicativo especificamente para HoloLens usando o Windows. Família de dispositivos [holográficos abaixo de](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Executar seu aplicativo 2D em um headset Windows Mixed Reality imersivo

Se você implantou seu aplicativo 2D em um computador desktop e experimentou-o em seu monitor, você está pronto para experimentá-lo em um headset de área de trabalho imersivo!

Basta ir para o menu Iniciar dentro do headset de realidade misturada e iniciar o aplicativo de lá. O shell da área de trabalho e o shell holográfico compartilham o mesmo conjunto de aplicativos UWP e, portanto, o aplicativo já deve estar presente depois que você implantou do Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Direcionando headsets imersivos e HoloLens

Parabéns! Seu aplicativo agora está usando a Windows 10 UWP (Plataforma Windows Universal).

Seu aplicativo agora é capaz de ser executado em dispositivos Windows atuais, como Desktop, Mobile, Xbox, Windows Mixed Reality headsets imersivos, HoloLens e dispositivos Windows futuros. No entanto, para realmente direcionar todos esses dispositivos, você precisará garantir que seu aplicativo está direcionando o Windows. Família de dispositivos universal.

### <a name="change-your-device-family-to-windowsuniversal"></a>Altere sua família de dispositivos para Windows. Universal

Agora, vamos entrar no manifesto do AppX para garantir que seu Windows 10 UWP possa ser executado HoloLens:
* Abra o arquivo de solução do aplicativo com **Visual Studio** e navegue até o manifesto do pacote do aplicativo
* Clique com o botão direito do mouse no arquivo **Package.appxmanifest** em sua Solução e vá para **Exibir Código**<br>
  ![package.appxmanifest em Gerenciador de Soluções](images/openappxmanifest-500px.png)<br>
* Verifique se a plataforma de destino está Windows. Universal na seção dependências
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Salvar!

Se você não usar o Visual Studio para seu ambiente de desenvolvimento, poderá abrir o **AppXManifest.xml** no editor de texto de sua escolha para garantir que você esteja direcionando o **Windows.** *TargetDeviceFamily* Universal.

### <a name="run-in-the-hololens-emulator"></a>Executar no HoloLens Emulator

Agora que seu aplicativo UWP tem como destino "Windows. Universal", vamos criar seu aplicativo e execute-o no [HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).
* Certifique-se de que [você instalou o HoloLens Emulator](../install-the-tools.md).
* Em Visual Studio, selecione a configuração de build **x86** para seu aplicativo

  ![Configuração de build x86 no Visual Studio](../platform-capabilities-and-apis/images/x86setting.png)<br>
* Selecione **Emulador do HoloLens** no menu suspenso do destino de implantação

  ![HoloLens Emulator na lista de destino de implantação](images/deployemulator-500px.png)<br>
* Selecione **Depurar > Iniciar Depuração** para implantar seu aplicativo e iniciar a depuração.
* O emulador iniciará e executará seu aplicativo.
* Com um teclado, mouse e um controlador Xbox, coloque seu aplicativo no mundo para inocioná-lo.

  ![HoloLens Emulator carregado com um exemplo UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Próximas etapas

Neste ponto, uma das duas coisas pode acontecer:
1. Seu aplicativo mostrará sua tela inicial e começará a ser executado depois que ele é colocado no Emulator! Maravilha!
2. Ou depois de ver uma animação de carregamento para um holograma 2D, o carregamento será parar e você verá apenas seu aplicativo na tela inicial. Isso significa que algo deu errado e será preciso mais investigação para entender como dar vida ao aplicativo na Realidade Misturada.

Você precisará depurar para chegar à raiz de possíveis problemas que estão interrompendo o início do aplicativo UWP HoloLens.

### <a name="running-your-uwp-app-in-the-debugger"></a>Executando seu aplicativo UWP no depurador

Essas etapas explicam como depurar seu aplicativo UWP usando o Visual Studio depurador.
* Se você ainda não fez isso, abra sua solução no Visual Studio. Altere o destino para o HoloLens Emulator e **a** configuração de build para **x86**.
* Selecione **Depurar > Iniciar Depuração** para implantar seu aplicativo e iniciar a depuração.
* Coloque o aplicativo no mundo com o mouse, o teclado ou o controlador Xbox.
* Visual Studio agora deve quebrar em algum lugar no código do aplicativo.
  - Se seu aplicativo não falhar imediatamente ou entrar no depurador devido a um erro sem correção, passe por uma passagem de teste dos principais recursos do aplicativo para garantir que tudo está em execução e funcional. Você pode ver erros como a figura abaixo (exceções internas que estão sendo tratadas). Para garantir que você não perca erros internos que impactam a experiência do seu aplicativo, execute seus testes automatizados e testes de unidade para garantir que tudo se comporte conforme o esperado.

![HoloLens Emulator carregado com um exemplo UWP mostrando uma exceção do sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Atualizar sua interface do usuário

Agora que seu aplicativo UWP está em execução em headsets imersivos e HoloLens como um holograma 2D, em seguida, garantiremos que ele ficará muito bem. Estas são algumas coisas que você deve considerar:
* Windows Mixed Reality executará todos os aplicativos 2D em uma resolução fixa e DPI que equivale a 853 x 480 pixels efetivos. Considere se seu design precisa de refinamento nessa escala e revise as diretrizes de design abaixo para melhorar sua experiência em HoloLens headsets imersivos.
* Windows Mixed Reality [dá suporte a](../../design/app-model.md) blocos 2D ao vivo. Se sua funcionalidade principal estiver mostrando informações sobre um peças ao vivo, considere mover essas informações de volta para seu aplicativo ou explorar os [iniciadores de aplicativo 3D.](../../distribute/3d-app-launcher-design-guidance.md)

### <a name="2d-app-view-resolution-and-scale-factor"></a>Resolução de exibição de aplicativo 2D e fator de escala

![Do design responsivo](images/scale-500px.png)

Windows 10 todo o design visual de pixels de tela real para **pixels efetivos.** Isso significa que os desenvolvedores projetam sua interface do usuário seguindo as Diretrizes de Interface Humana do Windows 10 para pixels efetivos e o dimensionamento Windows garante que esses pixels efetivos sejam o tamanho certo para usabilidade entre dispositivos, resoluções, DPI e assim por diante. Confira esta [excelente leitura sobre o MSDN](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) e esta apresentação [build](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx) para obter mais informações.

Mesmo com a capacidade exclusiva de colocar aplicativos em seu mundo a uma variedade de distâncias, as distâncias de exibição da TV são recomendadas para produzir a melhor leitura e interação com o olhar/gesto. Por isso, um slate virtual na Página Base de Realidade Misturada exibirá sua exibição UWP simples em:

**1280x720, 150%DPI** (853 x 480 pixels efetivos)

Essa resolução tem várias vantagens:
* Esse layout de pixel efetivo terá aproximadamente a mesma densidade de informações que um tablet ou uma pequena área de trabalho.
* Ele corresponde ao DPI fixo e aos pixels efetivos para aplicativos UWP em execução Xbox One, permitindo experiências perfeitas entre dispositivos.
* Esse tamanho parece bom quando dimensionado em nossa variedade de distâncias operacionais para aplicativos no mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>Práticas recomendadas de design da interface de exibição de aplicativo 2D

**Faça:**
* Siga as [diretrizes Windows 10 HIG (Diretrizes](https://dev.windows.com/design) de Interface Humana) para estilos, tamanhos de fonte e tamanhos de botão. HoloLens fará o trabalho para garantir que seu aplicativo tenha padrões de aplicativo compatíveis, tamanhos de texto leitura e o tamanho de destino de acerto apropriado.
* Verifique se a interface do usuário segue as práticas recomendadas para [o design](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) responsivo para ter uma melhor HoloLens de resolução exclusiva e DPI.
* Use as recomendações de tema de cores "claras" Windows.

**Não:**
* Altere sua interface do usuário drasticamente quando estiver na realidade misturada, para garantir que os usuários tenham uma experiência familiar dentro e fora do headset.

### <a name="understand-the-app-model"></a>Entender o modelo de aplicativo

O [modelo de aplicativo](../../design/app-model.md) para realidade misturada foi projetado para usar a Casa da Realidade Misturada, em que muitos aplicativos estão juntos. Pense nisso como o equivalente de realidade misturada da área de trabalho, na qual você executará muitos aplicativos 2D ao mesmo tempo. Isso tem implicações no ciclo de vida do aplicativo, blocos e outros recursos principais do seu aplicativo.

### <a name="app-bar-and-back-button"></a>Barra de aplicativos e botão Voltar

As exibições 2D são decoradas com uma barra de aplicativos acima do conteúdo. A barra de aplicativos tem dois pontos de personalização específica do aplicativo:

**Título:** exibe o *nome de exibição* do Tile associado à instância do aplicativo

**Botão Voltar:** gera o *[evento BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* quando pressionado. A visibilidade do botão Voltar é controlada *[por SystemNavigationManager.AppViewBackButtonVisibility.](/uwp/api/Windows.UI.Core.SystemNavigationManager)*

![Interface do usuário da barra de aplicativos na exibição de aplicativo 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interface do usuário da barra de aplicativos na exibição de aplicativo 2D*

### <a name="test-your-2d-apps-design"></a>Testar o design do aplicativo 2D

É importante testar seu aplicativo para garantir que o texto seja acessível, se os botões podem ser destinados e se o aplicativo geral parece correto. Você pode [testar em](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) um headset da área de trabalho, um HoloLens, um emulador ou um dispositivo de toque com resolução definida como 1280 x 720 @150 %.

## <a name="new-input-possibilities"></a>Novas possibilidades de entrada

HoloLens usa sensores avançados de profundidade para ver o mundo e ver os usuários. Isso permite gestos avançados de mão, como [abrir e](../../design/system-gesture.md#bloom) abrir [o ar.](../../design/gaze-and-commit.md#composite-gestures) Microfones poderosos também permitem [experiências de voz.](../../design/voice-input.md)

Com os headsets da Área de Trabalho, os usuários podem usar controladores de movimento para apontar para aplicativos e tomar medidas. Eles também podem usar um gamepad, direcionando objetos com seu olhar.

Windows cuida de toda essa complexidade para aplicativos UWP, traduzindo seu [olhar,](../../design/gaze-and-commit.md)gestos, [](/windows/uwp/design/input/handle-pointer-input#pointer_events) voz e entrada do controlador de movimento para eventos de ponteiro que abstraem o mecanismo de entrada. Por exemplo, um usuário pode ter feito um toque de ar com a mão ou tirado o gatilho Selecionar em um controlador de movimento, mas os aplicativos 2D não precisam saber de onde a entrada veio – eles veem apenas um pressionaamento de toque 2D, como se estivesse em uma tela sensível ao toque.

Aqui estão os conceitos/cenários de alto nível que você deve entender para entrada ao levar seu aplicativo UWP para HoloLens:
* [O](../../design/gaze-and-commit.md) foco se transforma em eventos de foco, que podem disparar inesperadamente menus, flyouts ou outros elementos de interface do usuário para pop-up apenas ao redor de seu aplicativo.
* O olhar não é tão preciso quanto a entrada do mouse. Use destinos de acerto de tamanho apropriado para HoloLens, semelhantes a aplicativos móveis amigáveis ao toque. Elementos pequenos próximos às bordas do aplicativo são especialmente difíceis de interagir.
* Os usuários devem alternar os modos de entrada para passar da rolagem para arrastar para o panorâmico de dois dedos. Se o aplicativo foi projetado para entrada por toque, considere garantir que nenhuma funcionalidade principal seja bloqueada atrás do panorâmico de dois dedos. Nesse caso, considere ter mecanismos de entrada alternativos, como botões que podem iniciar o panorâmico de dois dedos. Por exemplo, o Mapas aplicativo pode ampliar com dois dedos panorâmicos, mas tem um botão de a mais, menos e girar para simular as mesmas interações de zoom com cliques simples.

[A entrada de](../../design/voice-input.md) voz é uma parte crítica da experiência de realidade misturada. Habilitamos todas as APIs de fala que estão em Windows 10 de Cortana ao usar um headset.

## <a name="publish-and-maintain-your-universal-app"></a>Publicar e manter seu aplicativo Universal

Depois que o aplicativo está em execução, empacote seu aplicativo para [enviar para o Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Confira também
* [Modelo de aplicativo](../../design/app-model.md)
* [Focar com a cabeça e confirmar](../../design/gaze-and-commit.md)
* [Controladores de movimentos](../../design/motion-controllers.md)
* [Entrada de voz](../../design/voice-input.md)
* [Como enviar um aplicativo para a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Usando o emulador do HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)