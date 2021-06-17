---
title: Usando o SteamVR com Windows Mixed Reality
description: Saiba como configurar e reproduzir jogos do SteamVR Windows Mixed Reality headsets e controladores com PCs compatíveis.
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, jogos, SteamVR, Steam, requisitos do sistema
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110145"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Usando o SteamVR com Windows Mixed Reality

Windows Mixed Reality para o SteamVR permite que os usuários executem experiências do SteamVR Windows Mixed Reality headsets imersivos. Depois de instalar o Windows Mixed Reality para o SteamVR, os usuários podem iniciar seus aplicativos Favoritos do SteamVR na área de trabalho ou na biblioteca do Steam e reproduzi-los diretamente no headset do Windows.

## <a name="get-your-pc-ready"></a>Preparar seu computador

* Certifique-se de que não há atualizações pendentes: selecione Iniciar > **Configurações**> Atualizar & Segurança > Windows Update . Se as atualizações estão disponíveis, selecione **Instalar agora.** Se nenhuma atualização estiver disponível, selecione **Verificar se há atualizações** e, em seguida, instale as novas.
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

4. Para executar o SteamVR, clique duas vezes no arquivo "vrstartup.exe" localizado no *SteamVR\bin\win64\vrstartup.exe* ou *SteamVR\bin\win32\vrstartup.exe* se o computador de destino estiver executando uma versão de 32 bits do Windows.

Consulte a página [de documentação do Steamworks para obter mais informações e solução de problemas.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Jogar jogos do SteamVR

1. Conecte o headset ao computador e a ligue os controladores de movimento.
2. Depois que o Windows Mixed Reality home tiver sido carregado e seus controladores ficam visíveis, abra o aplicativo Steam na área de trabalho.
3. Use o aplicativo Steam para iniciar um jogo do SteamVR de sua biblioteca do Steam.

**Dica:** para iniciar jogos do SteamVR sem tirar o headset, use o aplicativo desktop ( Iniciar **> Desktop**) para exibir e interagir com a área de trabalho do computador dentro Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Usando controladores de movimento com o SteamVR

Você usará seus controladores de movimento de maneira diferente em jogos diferentes. Aqui estão algumas noções básicas para ajudá-lo a começar:

* Para abrir o painel do Steam, pressione diretamente no thumbstick esquerdo ou direito.
* Para sair de um jogo do SteamVR e retornar ao Windows Mixed Reality, pressione o botão Windows.

## <a name="changing-the-resolution"></a>Alterando a resolução

Você pode ajustar o controle deslizante resolução de aplicativos na janela Configurações > do SteamVR -> Aplicativos a qualquer momento se você quiser jogar jogos em uma resolução mais alta. **Ao usar um multiplicador de resolução mais alta, você pode esperar que o jogo coloque mais pressão em seu computador. Se você aumentar o multiplicador e vir o desempenho degradado, reajuste o controle deslizante para o nível padrão e reinicie o jogo para garantir que a alteração entre em vigor.![Ajustar a resolução de aplicativos](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Usando vários headsets

Se você for um entusiado de VR, poderá usar regularmente mais de um headset de VR no mesmo computador. Se esse for o caso, observe que, quando um headset Windows Mixed Reality estiver conectado, os jogos do SteamVR sempre serão lançados no headset Windows Mixed Reality dispositivo. Se você quiser iniciar jogos do SteamVR em outro headset, primeiro desconectar o headset Windows Mixed Reality antes de continuar.

## <a name="preview-programs"></a>Programas de visualização

Lançamos atualizações regulares para melhorar o desempenho, a confiabilidade e a experiência geral de usar o SteamVR Windows Mixed Reality headsets imersivos. Embora nenhum desses programas de visualização seja necessário, incentivamos você a incentivá-los se quiser obter atualizações mais cedo e com mais frequência (e nos dê comentários sobre essas atualizações!).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality para SteamVR Beta

Windows Mixed Reality para o SteamVR é o componente que você instala da Loja do Steam que permite que o SteamVR funcione com seu headset Windows Mixed Reality serviço.  Publicamos atualizações para essa "ponte" regularmente e o Steam as instala automaticamente.

Se você quiser obter atualizações com mais frequência, incentivamos você a ingressar em nosso Beta público.  As atualizações vão primeiro para nosso público Beta e usamos seus comentários para garantir que as atualizações sejam de alta qualidade antes de publicá-las para todos os usuários.  Se você não estiver em nosso programa Beta, eventualmente obterá todas as mesmas correções e recursos, mas depois que eles foram testados por nossos usuários Beta.

Para ingressar:

  1. No Steam, use a lista suspenso no menu **Biblioteca** para filtrar para **Software**.
  2. Na lista, clique com o botão direito **do Windows Mixed Reality para SteamVR** e selecione **Propriedades**.
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

Windows Mixed Reality faz parte do Windows 10.  Muitas correções e recursos que afetam os usuários do SteamVR vêm com o sistema operacional Windows.  Se você quiser experimentar os builds Windows 10 versão prévia mais recentes, recomendamos que você participe do [Programa Windows Insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Habilitando a reprojetação de movimento para aplicativos SteamVR

Windows Mixed Reality para o SteamVR tem um recurso de reprodução de movimento experimental para tornar a reprojeção de 90 FPS mais suave.

Quando a reprojeção de movimento estiver habilitada, todos os jogos de VR do Steam renderizarão nominalmente a uma taxa de quadros de 1/2 (45 fps em vez de 90 FPS), enquanto o Windows Mixed Reality para SteamVR usa vetores de movimento gerados pela GPU para extrapolar o próximo quadro. Para jogos do SteamVR que atingem 60 FPS+ de forma confiável em um determinado pc, isso deve resultar em uma experiência sólida de 90 FPS com artefatos ocasionais, mantendo uma experiência confortável.

Os modos de reprodução de movimento disponíveis são os seguinte:

* **Configuração de SteamVR por aplicativo:** permite controlar a reprojeção de movimento por meio da interface do usuário de Configurações do SteamVR. Em seguida, você pode abrir Configurações do SteamVR, ir para Vídeo > Per-Application Configurações de Vídeo e selecionar uma opção para "Suavização de movimento".
* **Automático**: permite que a Reprojeção de movimento seja ativada automaticamente quando um jogo está sendo renderizado muito lentamente para manter 90 fps. Quando um jogo começa a manter 90 FPS ou inicia a renderização com menos de 45 FPS, a Reprojeção de movimento será desativada. A Reprojeção de rodízio assíncrona está habilitada sempre.
* **Vetor de movimento**: força o aplicativo a ser sempre executado com metade da taxa de quadros com a Reprojeção do vetor de movimento.
* **Nenhum**: desabilita a Reprojeção de movimento.

**Artefatos visuais esperados** 

1. Ao usar uma resolução de aplicativo maior que 150%, você pode enfrentar o desfoque. Ao usar a Reprojeção de movimento, é recomendável usar um valor menor que 150%.
2. Bordas ou texto de contraste nítido, especialmente em HUDs ou menus no jogo, podem parecer temporariamente distorcidos ou distorcidas devido a disocclusion.
3. SteamVR Home e muitos outros jogos que não atingirem 50-60 FPS em seu PC continuarão a ter uma experiência ruim com esse modo.
4. Alguns jogos foram relatados para serem executados às 50% de velocidade ou com latência maior (retardo). Relate esses jogos por meio das instruções do [Hub de comentários do Windows](filing-feedback.md) abaixo.

Inicialmente, temos suporte experimental para GPUs NVidia de geração recente. Estamos continuando a iterar e melhorar nosso suporte de Reprojeção de movimento em mais GPUs e estamos ansiosos para ouvir seus comentários.

**GPUs com suporte:** NVIDIA GeForce GTX1060, AMD RX470 ou superior, com drivers gráficos compatíveis com o Windows Mixed Reality instalados.

Para habilitar a Reprojeção de movimento:

1. Certifique-se de ter optado pelo **Windows Mixed Reality for SteamVR beta** usando as instruções acima.
2. Abra o painel do SteamVR.
3. Selecione o botão no lado esquerdo com o logotipo do Windows Mixed Reality para abrir as configurações **do Windows Mixed Reality for SteamVR** .
4. Na interface do usuário exibida, selecione a guia gráficos.
5. Selecione "auto" para "modo de Reprojeção de movimento de aplicativo padrão SteamVR" para habilitar a Reprojeção de movimento automático.

![Habilitar LSR & indicador LSR com SettingsUX](images/settingsux-enable-lsr.gif)

**Indicador de Reprojeção de movimento**

O indicador de Reprojeção de movimento ajuda a diagnosticar problemas com o recurso de Reprojeção de movimento automático experimental. Quando definido como true, você verá um indicador no canto superior esquerdo da tela do headset durante a Reprojeção de movimento automático. A cor e a posição desse indicador correspondem ao modo de Reprojeção de movimento atual-consulte o diagrama abaixo para obter exemplos.

![Indicador de mvLSR](images/mvLSRIndicator.png)

Verde = a Reprojeção de movimento está desativada porque o aplicativo pode ser renderizado em uma taxa de quadros completa.

Ciano = a Reprojeção de movimento está ativada porque o aplicativo está associado à CPU.

Blue = a Reprojeção de movimento está ativada porque o aplicativo está associado à GPU.

Vermelho = a Reprojeção de movimento está desativada porque o aplicativo está sendo executado com menos de meia taxa de quadros; Tente reduzir a Superamostragem se estiver habilitado.

Verde + ciano + azul = a Reprojeção de movimento está no modo de meia-taxa de bits ou o aplicativo solicitou a Reprojeção de movimento.

## <a name="sharing-feedback-on-steamvr"></a>Compartilhando comentários no SteamVR

Seus comentários são inúteis quando se trata de melhorar a experiência de SteamVR do Windows Mixed Reality. Envie todos os comentários e bugs por meio do [Hub de comentários do Windows](filing-feedback.md). Siga estas sugestões para nos ajudar a obter o máximo de seus comentários:

1. No Hub de comentários, indique que você está relatando um novo problema no "que tipo de comentário é?" na parte superior.
2. Selecione a categoria de **realidade misturada** e a subcategoria **aplicativos** .
3. Coloque a palavra "SteamVR" no resumo do problema. Isso nos ajuda a encontrar seus comentários.
4. Descreva o que SteamVR o jogo ou o aplicativo que você estava usando quando se deparar com o problema.
5. Considere anexar um relatório do sistema SteamVR aos seus comentários. Isso fornece mais logs que podem nos ajudar a diagnosticar seu problema.
    1. Na janela SteamVR (as pequenas janelas que mostram o status do controlador), selecione no título para abrir o menu.
    2. Selecione "criar relatório do sistema".
    3. Salvar no arquivo.
    4. Anexe o arquivo gerado à entrada do hub de comentários diretamente.
6. Se seus comentários forem sobre o desempenho do SteamVR, colete um rastreamento de desempenho de realidade misturada: 
    1. Selecione o botão **recriar meu problema** .
    2. Na lista suspensa ao lado de "incluir dados sobre", selecione **desempenho de realidade misturada**.
    3. Verifique se o jogo está em execução e selecione **Iniciar captura**.
    4. Gaste alguns segundos jogando o jogo para capturar o rastreamento. Não Capture o rastreamento por mais de 10-15 segundos ou ele será muito grande para ser enviado.
    5. Selecione **parar captura**.
7. Selecione **Enviar** depois de concluir o restante dos campos.

Se você tiver dúvidas ou comentários para compartilhar, também poderá entrar em contato conosco em nosso [Fórum de fluxo](http://steamcommunity.com/app/719950/discussions/).

## <a name="see-also"></a>Confira também

* [Solução de problemas do SteamVR com o Windows Mixed Reality](steamvr-questions.md)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Usando controladores HP no Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Usando controladores HP em um não real](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Enviar bugs e comentários](filing-feedback.md)
