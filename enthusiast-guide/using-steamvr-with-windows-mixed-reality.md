---
title: Usando o SteamVR com Windows Mixed Reality
description: Saiba como configurar e reproduzir jogos do SteamVR Windows Mixed Reality headsets e controladores com PCs compatíveis.
author: qianw211
ms.author: v-qianwen
ms.date: 9/23/2021
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, jogos, SteamVR, Steam, requisitos do sistema
ms.openlocfilehash: b06c5e0b9918a5277a2c31e391dbdbc1ef740110
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436708"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Usando o SteamVR com Windows Mixed Reality

Windows Mixed Reality para o SteamVR permite que os usuários executem experiências do SteamVR Windows Mixed Reality headsets imersivos. Depois de instalar o Windows Mixed Reality para o SteamVR, os usuários podem iniciar seus aplicativos Favoritos do SteamVR na área de trabalho ou na biblioteca do Steam e reproduzi-los diretamente no headset Windows web.

## <a name="get-your-pc-ready"></a>Preparar seu computador

* Certifique-se de que você não tem atualizações pendentes: selecione Iniciar > Configurações > Atualizar & **Segurança > Windows Atualizar**. Se as atualizações estão disponíveis, selecione **Instalar agora.** Se nenhuma atualização estiver disponível, selecione **Verificar se há atualizações** e, em seguida, instale as novas.
* Os requisitos de pc variam para os aplicativos e o conteúdo no Steam. Confira os requisitos mínimos por título. Um PC com uma placa gráfica GTX 1070 (ou equivalente) e um processador Intel® Core™ i7 deve oferecer uma boa experiência para uma ampla variedade de títulos.
* Configurar o [Windows Mixed Reality](set-up-windows-mixed-reality.md) se você ainda não tiver feito isso. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Configurar o Windows Mixed Reality para o SteamVR

1. [Baixe e instale o SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Quando estiver pronto, inicie o SteamVR. O Tutorial do SteamVR deve começar automaticamente.

> **Observação:** Para solucionar problemas avançados de sua configuração do SteamVR, certifique-se de ter os seguintes componentes de software instalados:
> 1. Instale [o Steam](http://store.steampowered.com/about/) e faça **logon** **ou crie uma nova conta.**
> 2. Instale [o SteamVR.](https://store.steampowered.com/app/250820/SteamVR/) Com o headset conectado, iniciar o Steam e você verá uma caixa de diálogo solicitando que você instale o SteamVR. Siga os prompts na caixa de diálogo para instalá-lo.
    * Se você não vir o pop-up, instale o SteamVR navegando até a seção *Ferramentas* da *biblioteca*. Localize o SteamVR na lista e clique com o botão direito do mouse e selecione *Instalar Jogo*.
> 3. Instale [Windows Mixed Reality para o SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Configurar o Windows Mixed Reality para o SteamVR em um ambiente sem acesso à Internet

**Armazenar a mídia necessária em um dispositivo de armazenamento portátil**
1. Instale [o SteamVR](https://store.steampowered.com/app/250820/SteamVR/) [e Windows Mixed Reality para o SteamVR,](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) conforme indicado acima, [usando o Steam](http://store.steampowered.com/about/) em um computador com acesso completo à Internet.
2. No Steam, abra a seção Biblioteca e encontre a parte rotulada como "Ferramentas".
3. Depois que o SteamVR estiver instalado, clique com o botão direito do mouse na entrada "SteamVR" e, no menu pop-up resultante, clique na entrada "Propriedades".
4. Uma nova janela com várias guias será aberta. Selecione a guia "ARQUIVOS LOCAIS" e clique no botão rotulado "PROCURAR ARQUIVOS LOCAIS".
5. O diretório que contém o Runtime do SteamVR será aberto. Copie todo esse diretório (chamado SteamVR) em uma mídia portátil de sua escolha (por exemplo, uma unidade usb).
6. Faça o mesmo com Windows Mixed Reality para o SteamVR e quaisquer aplicativos compatíveis com o SteamVR que você gostaria de instalar no computador de destino.

**Executar o SteamVR no computador de destino**
1. Depois de conectar o dispositivo de armazenamento portátil ao computador de destino, mova o SteamVR, MixedRealityVRDriver e outras pastas para um local conveniente no computador de destino.
![SteamVR e Windows Mixed Reality para o SteamVR instalados no computador de destino](images/steamvr-install-files.png)

2. Garantindo que o SteamVR e MixedRealityVRDriver estão na mesma pasta, abra um prompt de comando. Para este exemplo, vamos supor que a pasta que contém está *em C:\SteamVRInstall.* Nesse caso, no prompt de comando, você deve executar:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(Observe que, se você estiver executando uma versão de 32 bits do Windows, a parte do caminho `win64` acima deverá ser em vez `win32` disso.)

Isso permitirá que o runtime encontre o Windows Mixed Reality para o driver SteamVR em sua instalação personalizada.

4. Para executar o SteamVR, clique duas vezes no arquivo "vrstartup.exe" localizado em *SteamVR\bin\win64\vrstartup.exe* ou *SteamVR\bin\win32\vrstartup.exe* se o computador de destino estiver executando uma versão de 32 bits do Windows.

Consulte a página [de documentação do Steamworks para obter mais informações e solução de problemas.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Jogar jogos do SteamVR

1. Conexão headset no computador e ativar os controladores de movimento.
2. Depois que o Windows Mixed Reality home tiver sido carregado e os controladores ficam visíveis, abra o aplicativo Steam na área de trabalho.
3. Use o aplicativo Steam para iniciar um jogo do SteamVR de sua biblioteca do Steam.

**Dica:** para iniciar jogos do SteamVR sem tirar o headset, use o aplicativo desktop ( Iniciar **> Desktop**) para exibir e interagir com a área de trabalho do computador dentro Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Usando controladores de movimento com o SteamVR

Você usará seus controladores de movimento de maneira diferente em jogos diferentes. Aqui estão algumas noções básicas para ajudá-lo a começar:

* Para abrir o painel do Steam, pressione diretamente no thumbstick esquerdo ou direito.
* Para sair de um jogo do SteamVR e retornar ao Windows Mixed Reality, pressione o botão Windows entrada.

## <a name="changing-the-resolution"></a>Alterando a resolução

Você pode ajustar o controle deslizante resolução de aplicativos na janela Aplicativos > Configurações -> SteamVR a qualquer momento se quiser jogar em uma resolução mais alta. **Ao usar um multiplicador de resolução mais alta, você pode esperar que o jogo coloque mais pressão em seu computador. Se você aumentar o multiplicador e vir o desempenho degradado, reajuste o controle deslizante para o nível padrão e reinicie o jogo para garantir que a alteração entre em vigor.![Ajustar a resolução de aplicativos](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Usando vários headsets

Se você for um entusiado de VR, poderá usar regularmente mais de um headset vr no mesmo computador. Se esse for o caso, observe que, quando um headset Windows Mixed Reality estiver conectado, os jogos do SteamVR sempre serão lançados no headset Windows Mixed Reality dispositivo. Se você quiser iniciar jogos do SteamVR em outro headset, primeiro desconectar o headset Windows Mixed Reality antes de continuar.

## <a name="preview-programs"></a>Programas de visualização

Lançamos atualizações regulares para melhorar o desempenho, a confiabilidade e a experiência geral de usar o SteamVR Windows Mixed Reality headsets imersivos. Embora nenhum desses programas de visualização seja necessário, incentivamos você a incentivá-los se quiser obter atualizações mais cedo e com mais frequência (e nos dê comentários sobre essas atualizações!).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality para SteamVR Beta

Windows Mixed Reality para o SteamVR é o componente que você instala da Loja do Steam que permite que o SteamVR funcione com seu headset Windows Mixed Reality serviço.  Publicamos atualizações para essa "ponte" regularmente e o Steam as instala automaticamente.

Se você quiser obter atualizações com mais frequência, incentivamos você a ingressar em nosso Beta público.  As atualizações vão primeiro para nosso público Beta e usamos seus comentários para garantir que as atualizações sejam de alta qualidade antes de publicá-las para todos os usuários.  Se você não estiver em nosso programa Beta, eventualmente obterá todas as mesmas correções e recursos, mas depois que eles foram testados por nossos usuários Beta.

Para ingressar:

  1. No Steam, use a lista suspenso no menu **Biblioteca** para filtrar para **Software**.
  2. Na lista, clique com o botão direito **do Windows Mixed Reality para o SteamVR** e selecione **Propriedades**.
  3. Selecione a **guia Betas.**
  4. Escolha **"beta – beta público"** e selecione **Fechar** para confirmar. O campo de código de acesso beta deve ser deixado em branco.
  
### <a name="steamvr-beta"></a>SteamVR Beta

O SteamVR é criado e lançado pela Valve e é comum em todos os headsets do SteamVR.  Ele segue um modelo semelhante de liberação de atualizações para membros Beta antes da publicação para todos os usuários.

Para ingressar:

  1. No Steam, use a lista suspenso no menu **Biblioteca** para filtrar para **Ferramentas**.
  2. Na lista, clique com o botão direito **do mouse em SteamVR** e selecione **Propriedades**.
  3. Selecione a **guia Betas.**
  4. Escolha **"beta – beta público"** e selecione **Fechar** para confirmar.  O campo de código de acesso beta deve ser deixado em branco. ![ Alternar para o SteamVR beta na caixa de diálogo de propriedades para o SteamVR](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Programa Windows Insider

Windows Mixed Reality faz parte do Windows 10 e Windows 11.  Muitas correções e recursos que afetam os usuários do SteamVR vêm com o Windows sistema operacional.  Se você quiser experimentar os builds Windows 10 versão prévia Windows 11, recomendamos que você participe do [Windows Programa Insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Habilitando a reprojetação de movimento para aplicativos SteamVR

Windows Mixed Reality para o SteamVR tem um recurso de reprodução de movimento experimental para tornar a reprojeção de 90 FPS mais suave.

Quando a reprojeção de movimento estiver habilitada, todos os jogos de VR do Steam renderizarão nominalmente a uma taxa de quadros de 1/2 (45 fps em vez de 90 FPS), enquanto o Windows Mixed Reality para SteamVR usa vetores de movimento gerados pela GPU para extrapolar o próximo quadro. Para jogos do SteamVR que atingem 60 FPS+ de forma confiável em um determinado pc, isso deve resultar em uma experiência sólida de 90 FPS com artefatos ocasionais, mantendo uma experiência confortável.

Os modos de reprodução de movimento disponíveis são os seguinte:

* **Configuração de SteamVR** por aplicativo: permite controlar a reprojeção de movimento por meio da interface do usuário Configurações SteamVR. Em seguida, você pode abrir o Configurações SteamVR, ir para Video > Per-Application Video Configurações e selecionar uma opção para "Suavização de movimento".
* **Auto:** permite que a reprojeção de movimento seja ativada automaticamente quando um jogo estiver renderizar muito lentamente para manter 90 FPS. Quando um jogo começa a manter 90 FPS ou começa a renderizar com menos de 45 FPS, a reprojeção de movimento será desligada. A reprojeção rotacional assíncrona está sempre habilitada.
* **Vetor de** Movimento: força o aplicativo a ser sempre executado na taxa de meio quadro com a reprojeção de vetor de movimento.
* **Nenhum:** desabilita a reprojeção de movimento.

**Visual Artifacts** 

1. Ao usar uma resolução de aplicativo maior que 150%, você pode ter desfocado. Ao usar a reprojeção de movimento, é recomendável usar um valor menor que 150%.
2. Bordas de contraste nítido ou texto, especialmente em HUDs ou menus no jogo, podem parecer temporariamente distorcidos ou distorcidos devido à disocclusão.
3. O SteamVR Home e muitos outros jogos que não atingem de forma confiável 50 a 60 FPS em seu computador continuarão a ter uma experiência ruim com esse modo.
4. Alguns jogos foram relatados para ser executados a 50% de velocidade ou com maior latência (retardo). Reporte esses jogos por meio [das Hub do Windows Feedback](filing-feedback.md) abaixo.

Inicialmente, temos suporte experimental para GPUs NVidia de geração recente. Continuamos iterando e melhorando nosso suporte à reprojeção de movimento em mais GPUs e estamos ansiosos para ouvir seus comentários.

**GPUs com suporte:** Nvidia GeForce GTX1060, AMD RX470 ou melhor, com Windows Mixed Reality drivers gráficos compatíveis instalados.

Para habilitar a reprojetação de movimento:

1. Certifique-se de que você optou pelo Windows Mixed Reality **para o SteamVR Beta** usando as instruções acima.
2. Abra o painel do SteamVR.
3. Selecione o botão no lado esquerdo com o logotipo Windows Mixed Reality para abrir o Windows Mixed Reality **para o Configurações.**
4. Na interface do usuário que aparece, selecione a guia Gráficos.
5. Selecione "Auto" para "Modo de reprojeção de movimento do aplicativo SteamVR padrão" para habilitar a reprodução automática de movimento.

![Habilitar o indicador LSR & LSR com SettingsUX](images/settingsux-enable-lsr.gif)

**Indicador de reprojeção de movimento**

O indicador de reprojeção de movimento ajuda a diagnosticar problemas com o recurso de reprojeção de movimento automático experimental. Quando definido como true, você verá um indicador no canto superior esquerdo da exibição do headset durante a reprodução automática de movimento. A cor e a posição desse indicador correspondem ao modo de reprojeção de movimento atual – consulte o diagrama abaixo para ver exemplos.

![Indicador mvLSR](images/mvLSRIndicator.png)

Verde = a reprojeção de movimento está desligada porque o aplicativo pode renderizar com taxa de quadros completa.

Cyan = a reprojeção de movimento está ligada porque o aplicativo está vinculado à CPU.

Blue = a reprojeção de movimento está ligada porque o aplicativo está vinculado à GPU.

Vermelho = a reprojeção de movimento está desligada porque o aplicativo está em execução com menos de metade da taxa de quadros; tente reduzir a super amostragem se habilitada.

Verde + Ciano + Azul = a reprojeção de movimento está no modo de taxa de meio quadro ou a reprojeção de movimento solicitada pelo aplicativo.

## <a name="sharing-feedback-on-steamvr"></a>Compartilhar comentários no SteamVR

Seus comentários são valiosas quando se trata de melhorar a Windows Mixed Reality do SteamVR. Envie todos os comentários e bugs por meio [do Hub do Windows Feedback](filing-feedback.md). Siga estas sugestões para nos ajudar a obter o máximo de seus comentários:

1. No Hub de Comentários, indique que você está relatando um novo problema em "Que tipo de comentários é?" na parte superior.
2. Selecione a **categoria Realidade Misturada** e **a** subcategoria Aplicativos.
3. Coloque a palavra "SteamVR" no resumo do problema. Isso nos ajuda a encontrar seus comentários.
4. Descreva qual jogo ou aplicativo do SteamVR você estava usando quando se deparou com o problema.
5. Considere anexar um relatório do sistema SteamVR aos seus comentários. Isso fornece mais logs que podem nos ajudar a diagnosticar seu problema.
    1. Na Janela Do SteamVR (as janelas pequenas que mostram o status do controlador) selecione o título para abrir o menu.
    2. Selecione "Criar Relatório do Sistema".
    3. Salve em Arquivo.
    4. Anexe o arquivo gerado à entrada do Hub de Comentários diretamente.
6. Se seus comentários são sobre o desempenho do SteamVR, colete um rastreamento de Desempenho de Realidade Misturada: 
    1. Selecione o **botão Recriar meu** Problema.
    2. Na lista de opções ao lado de "incluir dados sobre", selecione **Desempenho de Realidade Misturada.**
    3. Certifique-se de que o jogo está em execução e selecione **Iniciar Captura**.
    4. Passe alguns segundos no jogo para capturar o rastreamento. Não capture o rastreamento por mais de 10 a 15 segundos ou ele será muito grande para enviar.
    5. Selecione **Parar Captura**.
7. Selecione **Enviar** depois de concluir o restante dos campos.

Se você tiver dúvidas ou comentários para compartilhar, também poderá nos encontrar em nosso fórum [do Steam.](http://steamcommunity.com/app/719950/discussions/)

## <a name="see-also"></a>Confira também

* [Solução de problemas do SteamVR com Windows Mixed Reality](steamvr-questions.md)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Usando controladores HP no Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Usando controladores HP no Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Enviar bugs e comentários](filing-feedback.md)
