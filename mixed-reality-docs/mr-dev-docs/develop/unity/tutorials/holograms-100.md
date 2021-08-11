---
title: Noções básicas do HoloLens (1ª geração) 100 – Introdução ao Unity
description: saiba como criar seu primeiro aplicativo "hello world" básico de realidade mista para dispositivos HoloLens e Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, Windows Mixed Reality, HoloLens, imersão, vr, mr, introdução, holograma, academia, tutorial, academia de realidade misturada, unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196492"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>noções básicas de HoloLens (1ª gen) 100: introdução ao Unity

>[!IMPORTANT]
>os tutoriais misturados do academia de realidade foram projetados com a HoloLens (1ª gen), o Unity 2017 e o headset de imersão de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes ou as interações usadas para o HoloLens 2 e podem não ser compatíveis com as versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

Este tutorial orientará você na criação de um aplicativo básico de realidade misturada criado com o Unity.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Noções básicas do MR 100: introdução ao Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

* um computador Windows 10 configurado com as ferramentas corretas [instaladas](../../install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1-criar um novo Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para criar um aplicativo com o Unity, primeiro você precisa criar um projeto. Esse projeto é organizado em algumas pastas, o mais importante deles é sua pasta de ativos. essa é a pasta que contém todos os ativos que você importa das ferramentas de criação de conteúdo digital, como Maya, Max Cinema 4d ou Photoshop, todo o código criado com Visual Studio ou seu editor de código favorito, e qualquer quantidade de arquivos de conteúdo que o Unity cria à medida que você compõe cenas, animações e outros tipos de ativos de Unity no editor.

para compilar e implantar aplicativos UWP, o Unity pode exportar o projeto como uma solução Visual Studio que conterá todos os arquivos de ativos e de código necessários.

1. Iniciar o Unity
2. Selecione **Novo**
3. Insira um nome de projeto (por exemplo, "MixedRealityIntroduction")
4. Insira um local para salvar seu projeto
5. Verifique se a alternância **3D** está selecionada
6. Selecione **criar projeto**

Parabéns, você está pronto para começar a usar suas personalizações de realidade misturada agora.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2 – configurar a câmera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

A câmera principal do Unity lida com o controle de cabeçalho e a renderização de estereoscópico. Há algumas alterações a serem feitas na câmera principal para usá-la com realidade misturada.

1. Selecionar arquivo > nova cena

Primeiro, será mais fácil definir o layout de seu aplicativo se você imaginar a posição inicial do usuário como (**X**: 0, **Y**: 0, **Z**: 0). Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.

1. Selecione a **câmera principal** no painel **hierarquia**
2. No painel **Inspetor** , localize o componente **transformação** e altere a **posição** de (**x**: 0, **y**: 1, **z**:-10) para (**x**: 0, **y**: 0, **z**: 0)

Em segundo lugar, o plano de fundo da câmera padrão precisa de algum pensamento.

**para os aplicativos HoloLens**, o mundo real deve aparecer atrás de tudo que a câmera renderiza, não uma textura Skybox.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere a lista suspensa **limpar sinalizadores** de **Skybox** para **cor sólida**.
2. Selecione o seletor de cor do **plano de fundo** e altere os valores de **RGBA** para (0, 0, 0, 0)

**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a textura padrão do Skybox que o Unity fornece.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o menu suspenso **limpar sinalizadores** em **Skybox**.

Em terceiro lugar, vamos considerar o próximo clipe no Unity e impedir que os objetos sejam renderizados muito próximos dos olhos dos usuários, uma vez que um usuário se aproxima de um objeto ou um objeto se aproxima de um usuário.

**para os aplicativos HoloLens**, o próximo clipe pode ser definido como o [HoloLens](../camera-in-unity.md#using-clipping-planes) 0,85 medidores recomendados.

1. com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **inspetor** e altere o campo **próximo do plano do clipe** do padrão **0,3** para o HoloLens recomendado **0,85**.

**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a configuração padrão que o Unity fornece.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o campo **próximo do plano do clipe** para o padrão **0,3**.

Por fim, vamos salvar nosso progresso até o momento. Para salvar as alterações de cena, selecione **arquivo > salvar cena como**, nomeie a cena **principal** e selecione **salvar**.

## <a name="chapter-3---setup-the-project-settings"></a>capítulo 3 – configurar o Project Configurações

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

neste capítulo, definiremos algumas configurações de projeto do Unity que nos ajudam a direcionar o SDK Windows Holographic para desenvolvimento. Também definiremos algumas configurações de qualidade para nosso aplicativo. por fim, garantiremos que nossos destinos de compilação sejam definidos como Plataforma Universal do Windows.

### <a name="unity-performance-and-quality-settings"></a>Configurações de desempenho e qualidade do Unity

**Configurações de qualidade do Unity para HoloLens**

![Configurações de qualidade do Unity para HoloLens](images/qualitysettings.png)

como manter a alta taxa de quadros em HoloLens é tão importante, queremos que as configurações de qualidade sejam ajustadas para um desempenho mais rápido. Para obter informações de desempenho mais detalhadas, [recomendações de desempenho para o Unity](../performance-recommendations-for-unity.md).

1. selecione **editar > Project Configurações qualidade de >**
2. selecione o **menu suspenso** sob o logotipo **Plataforma Universal do Windows** e selecione **muito baixo**. Você saberá que a configuração foi aplicada corretamente quando a caixa na coluna Plataforma Universal do Windows e a linha **Muito Baixa** estiver verde.

**Para aplicativos de realidade misturados direcionados a exibições do obstruído**, você pode deixar as configurações de qualidade com seus valores padrão.

### <a name="target-windows-10-sdk"></a>SDK de Windows 10 de destino

**Windows SDK do Holographic de destino**

![Windows SDK do Holographic de destino](../images/xrsettings.png)

Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](../../../design/app-views.md) em vez de uma exibição 2D. fazemos isso habilitando o suporte de realidade Virtual no Unity direcionando o SDK do Windows 10.

1. vá para **editar > Project Configurações > Player**.
2. no **painel inspetor** para Configurações do Player, selecione o ícone de **Plataforma Universal do Windows** .
3. Expanda o grupo **Configurações de XR**.
4. Na seção **Renderização**, marque a caixa de seleção **Realidade Virtual Compatível** para adicionar uma nova lista de **SDKs de Realidade Virtual**.
5. Verifique se **Windows Mixed Reality** aparece na lista. Se não aparecer, selecione o botão **+** na parte inferior da lista e escolha **Windows Mixed Reality**.

>[!NOTE]
>se você não vir o ícone de **Plataforma Universal do Windows** , verifique se selecionou o suporte de Plataforma Universal do Windows Build durante a instalação. Caso contrário, talvez seja necessário reinstalar o Unity com a instalação correta do Windows.

Trabalho incrível ao obter todas as configurações de projeto aplicadas. Em seguida, vamos adicionar um holograma!

## <a name="chapter-4---create-a-cube"></a>Capítulo 4-criar um cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Criar um cubo em seu projeto de Unity é como criar qualquer outro objeto no Unity. Colocar um cubo na frente do usuário é fácil porque o sistema de coordenadas do Unity é mapeado para o mundo real, em que um medidor no Unity é aproximadamente um medidor no mundo real.

1. No canto superior esquerdo do painel **hierarquia** , selecione a lista suspensa **criar** e escolha o **objeto 3D > cubo**.
2. Selecione o **cubo** recém-criado no painel **hierarquia**
3. No **Inspetor** , localize o componente de **transformação** e altere a **posição** para (**X**: 0, **Y**: 0, **Z**: 2). *Isso posiciona o cubo 2 metros na frente da posição inicial do usuário.*
4. No componente **transformar** , altere a **rotação** para (**x**: 45, **y**: 45, **z**: 45) e altere a **escala** para (**x**: 0,25, **y**: 0,25, **z**: 0,25). *Isso dimensiona o cubo para 0,25 metros.*
5. Para salvar as alterações de cena, selecione **arquivo > salvar cena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5 – verificar no dispositivo do editor do Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Agora que criamos nosso cubo, é hora de fazer um check-in rápido no dispositivo. Você pode fazer isso diretamente de dentro do editor do Unity.

### <a name="initial-setup"></a>Instalação inicial

1. no seu PC de desenvolvimento, no Unity, abra o **arquivo > Build Configurações** janela.
2. altere a **plataforma** para **Plataforma Universal do Windows** e clique em **alternar plataforma**

### <a name="for-hololens-use-unity-remoting"></a>para HoloLens usar a comunicação remota do Unity

1. no HoloLens, instale e execute o [Holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md), disponível na Windows Store. Inicie o aplicativo no dispositivo e ele entrará em um estado de espera e mostrará o endereço IP do dispositivo. Anote o IP.
2. Abra **a janela > XR > emulação holográfica.**
3. Altere **o Modo de Emulação** **de Nenhum** para Remoto **para Dispositivo**.
4. Em **Computador Remoto**, insira o endereço IP do seu HoloLens indicado anteriormente.
5. Clique em **Conectar**.
6. Verifique se o **Status da Conexão** muda para verde **Conectado.**
7. Agora você pode clicar em **Reproduzir** no editor do Unity.

Agora você poderá ver o cubo no dispositivo e no editor. Você pode pausar, inspecionar objetos e depurar da mesma forma que está executando um aplicativo no editor, porque isso é essencialmente o que está acontecendo, mas com a entrada de vídeo, áudio e dispositivo transmitida entre a rede entre o computador host e o dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para outros headsets com suporte de realidade misturada

1. Conexão headset para o computador de desenvolvimento usando o cabo USB e o cabo de porta de exibição ou HDMI.
2. Iniciar o **Portal de Realidade Misturada** e verifique se você concluiu a primeira experiência de executar.
3. No Unity, agora você pode pressionar o botão Reproduzir.

Agora você poderá ver a renderização do cubo no headset de realidade misturada e no editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6 – Criar e implantar no dispositivo do Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Agora estamos prontos para compilar nosso projeto para Visual Studio e implantar em nosso dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportar para a solução Visual Studio dados

1. Abra **a janela > Build Configurações** Arquivo.
1. Clique **em Adicionar Cenas Abertas** para adicionar a cena.
1. Altere **Plataforma** **para Plataforma Universal Windows Plataforma e** clique em Mudar **Plataforma**.
1. Em **Configurações Windows Plataforma** Universal, verifique se o **SDK** é **Universal 10.**
1. Para Dispositivo de destino, deixe para **Qualquer Dispositivo** para exibições oclusivas ou alternar **para HoloLens**.
1. **O tipo de build UWP** deve ser **D3D.**
1. **O SDK da UWP** pode ser deixado em **Mais recente instalado.**
1. Clique em **Compilar**.
1. No explorador de arquivos, clique em **Nova Pasta** e nomeia a pasta **"Aplicativo".**
1. Com a **pasta Aplicativo** selecionada, clique no **botão Selecionar** Pasta.
1. Quando o Unity terminar de criar, uma Windows Explorador de Arquivos será exibida.
1. Abra a **pasta Aplicativo** no explorador de arquivos.
1. Abra a solução Visual Studio gerada (MixedRealityIntroduction.sln neste exemplo)

### <a name="compile-the-visual-studio-solution"></a>Compilar a solução Visual Studio dados

Por fim, compilaremos a solução Visual Studio exportação, a implantaremos e a testaremos no dispositivo.

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de **Depurar** para Versão **e** de **ARM** para **X86.**

As instruções diferem para implantar em um dispositivo em comparação com o emulador. Siga as instruções que corresponderem à sua configuração.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implantar no dispositivo de realidade misturada por Wi-Fi

1. Clique na seta ao lado do **botão Computador Local** e altere o destino de implantação para Computador **Remoto.**
2. Insira o endereço IP do dispositivo  de realidade misturada e altere o Modo de Autenticação para Universal (Protocolo Não Criptografado) para HoloLens e **Windows** para outros dispositivos.
3. Clique **em Depurar > Iniciar sem depurar**.

**Por HoloLens**, se esta for a primeira vez que você implanta em seu dispositivo, você precisará emparelhar [usando Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implantar no dispositivo de realidade misturada por USB

Verifique se o dispositivo está conectado por meio do cabo USB.

1. **Para HoloLens**, clique na seta ao lado do botão **Computador Local** e altere o destino de implantação para **Dispositivo**.
2. **Para direcionar dispositivos ocluídos anexados ao computador,** mantenha a configuração como Computador Local. Verifique se você tem o **Portal de Realidade Misturada** em execução.
3. Clique **em Depurar > Iniciar sem depurar**.

### <a name="deploy-to-emulator"></a>Implantar no Emulator

1. Clique na seta ao lado do **botão** Dispositivo e, na lista **HoloLens Emulator.**
2. Clique **em Depurar > Iniciar sem depurar**.

### <a name="try-out-your-app"></a>Experimentar seu aplicativo

Agora que seu aplicativo está implantado, tente mover todo o cubo e observe que ele permanece no mundo na sua frente.

## <a name="see-also"></a>Confira também

* [Visão geral do desenvolvimento do Unity](../unity-development-overview.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](../best-practices-for-working-with-unity-and-visual-studio.md)
* [Noções básicas do MR 101](holograms-101.md)
* [Noções básicas do MR 101E](holograms-101e.md)