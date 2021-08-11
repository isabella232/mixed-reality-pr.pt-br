---
title: Notas sobre a versão – abril de 2018
description: Mantenha-se atualizado sobre HoloLens e Windows Mixed Reality de versão do Windows 10 atualização de abril de 2018/RS4.
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: notas de versão, versão, windows 10, build, rs4, so
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202428"
---
# <a name="release-notes---april-2018"></a>Notas sobre a versão – abril de 2018

A Windows 10 de abril de **[2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (também conhecida como RS4) inclui novos recursos para headsets HoloLens e Windows Mixed Reality imersivos conectados a PCs. 

Para atualizar para a versão mais recente de qualquer tipo de dispositivo, abra o aplicativo **Configurações,** acesse Atualizar **& Segurança** e selecione o botão Verificar se há **atualizações.** Em um Windows 10, você também pode instalar manualmente o Windows 10 de abril de 2018 usando a [ferramenta de criação Windows de mídia.](https://www.microsoft.com/software-download/windows10)

**Versão mais recente para Desktop: Windows 10** de abril de 2018 (**10.0.17134.1**)<br>
**Versão mais recente HoloLens: Windows 10** de abril de 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Uma mensagem de Alex Ltdman e uma visão geral dos novos recursos de realidade misturada na atualização de Windows 10 de abril de 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para headsets Windows Mixed Reality imersivos

A Windows 10 de abril de 2018 inclui muitas melhorias para o uso de headsets imersivos (VR) Windows Mixed Reality com seu computador desktop, como: 

* **Novos ambientes para a** página de realidade misturada – escolha entre  o Casa no Penhasco e o novo ambiente do Skyloft selecionando Locais no menu Iniciar. Também adicionamos um [recurso experimental que](/windows/mixed-reality/design/add-custom-home-environments) permitirá que você use ambientes personalizados que você criou.
* **Acesso rápido** captura de realidade misturada – tire fotos de realidade misturada usando um controlador de movimento em ambientes e aplicativos, mas não capturará o conteúdo protegido com DRM. Mantenha o Windows e, em seguida, toque no gatilho. .
* **Novas opções para iniciar e reizingar** conteúdo – os aplicativos agora são colocados automaticamente na sua frente quando você os inicia do menu Iniciar. Agora você também pode reorganizar aplicativos 2D arrastando as bordas e os cantos da janela.
* Ir facilmente para o conteúdo com o comando de voz **"voice"** – rapidamente na frente do conteúdo no Windows Mixed Reality página, olhando o conteúdo e dizendo "voice".
* **[Iniciadores de aplicativo 3D animados](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines) e [objetos 3D decorativos](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home) para a página de realidade misturada.** Agora você pode adicionar animação a iniciadores de aplicativo 3D e permitir que os usuários coloquem modelos 3D decorativos de uma página da Web ou aplicativo 2D na página Windows Mixed Reality página inicial.
* Melhorias no Windows Mixed Reality para **[o SteamVR](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** – o Windows Mixed Reality para SteamVR está fora do "acesso antecipado" com novas atualizações, incluindo: comentários aprimorados ao usar controladores de movimento, desempenho e confiabilidade aprimorados e melhorias na aparência dos controladores de movimento no SteamVR.
* **Outros aprimoramentos** – as configurações de desempenho automático atualizadas fornecem uma experiência mais otimizada (você pode [substituir manualmente](#visual-quality) essa configuração). A instalação agora fornece informações mais detalhadas sobre problemas comuns de compatibilidade com controladores USB 3.0 e placas gráficas.

## <a name="new-features-for-hololens"></a>Novos recursos para HoloLens

A Windows 10 de abril de 2018 chegou para todos os HoloLens clientes! Essa atualização é empacotada com melhorias introduzidas desde a última versão principal do HoloLens software em [agosto de 2016.](release-notes-august-2016.md)

### <a name="for-everyone"></a>Para todos

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Posicionamento automático de conteúdo 2D e 3D no lançamento</td><td>Um launcher de aplicativo 2D ou um aplicativo UWP 2D coloca automaticamente no mundo em um tamanho e uma distância ideais quando lançado, em vez de exigir que o usuário o coloque. Se <a href="/windows/mixed-reality/design/app-views"></a> um aplicativo imersivo usar um launcher de aplicativo 2D em vez de um launcher de aplicativo <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3D,</a>o aplicativo imersivo será lançado automaticamente do launcher do aplicativo 2D, da mesma forma que no RS1.<br><br>Um launcher de aplicativo 3D da menu Iniciar também coloca automaticamente no mundo. Em vez de iniciar automaticamente o aplicativo, os usuários podem clicar no launcher para iniciar o aplicativo imersivo. O conteúdo 3D aberto do aplicativo Hologramas e do Edge também coloca automaticamente no mundo.</td><td>Ao abrir um aplicativo do menu Iniciar, não será solicitado que você o coloque no mundo.<br><br>Se o posicionamento do launcher de aplicativo<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">2D/3D</a> não for ideal, você poderá movê-los facilmente usando novas manipulações de aplicativo fluido descritas abaixo. Você também pode reposicionar o conteúdo do 3D/launcher do aplicativo 2D dizendo "Move this" e, em seguida, usando o olhar para reposicionar o conteúdo.</td>
  </tr>
  <tr>
    <td>Manipulação de aplicativo fluido</td><td>Mova, reize e gire conteúdo 2D e 3D sem precisar entrar no modo "Ajustar".</td><td>Para mover um aplicativo UWP 2D ou um launcher de aplicativo 2D, basta olhar para a barra de aplicativos e, em seguida, usar o gesto de toque + segurar + arrastar. Você pode mover o conteúdo 3D olhando para qualquer lugar no objeto e, em seguida, usando toque em + manter + arrastar.<br><br>Para ressarcar o conteúdo 2D, ata ao seu canto. O cursor de olhar se transformará em um cursor de reeslização e, em seguida, você poderá tocar em + segurar + arrastar para ressilar. Você também pode tornar o conteúdo 2D mais alto ou mais largo observando suas bordas e arrastando.<br><br>Para reorganizar o conteúdo 3D, eleva as duas mãos para o quadro de gestos, com os dedos para cima na posição pronta. Você verá o cursor se transformar em um estado com duas mãos pequenas. Toque e segure o gesto com as duas mãos. Mover as mãos para mais perto ou mais distantes altera o tamanho do objeto. Mover as mãos para frente e para trás em relação umas às outras girará o objeto. Você também pode reessar/girar o conteúdo 2D dessa maneira.</td>
  </tr>
  <tr>
    <td>Replicação horizontal do aplicativo 2D com refluxo</td><td>Tornar um aplicativo UWP 2D mais amplo na taxa de proporção para ver mais conteúdo do aplicativo. Por exemplo, tornando o aplicativo Mail amplo o suficiente para mostrar o Painel de Visualização.</td><td>Basta olhar para a borda esquerda ou direita do aplicativo UWP 2D para ver o cursor de reessar e, em seguida, usar o gesto de toque + segurar + arrastar para ressilar.</td>
  </tr>
  <tr>
    <td>Suporte a comandos de voz expandido</td><td>Você pode fazer mais simplesmente usando sua voz.</td><td>Experimente estes comandos de voz:<ul><li>"Go to Start" – apresenta o menu Iniciar ou sai de um aplicativo <a href="/windows/mixed-reality/design/app-views">imersivo.</a></li><li>"Move this" – permite mover um objeto .</li></ul></td>
  </tr>
  <tr>
    <td>Aplicativos Hologramas e Fotos atualizados</td><td>Atualização Hologramas aplicativo com novos hologramas. Aplicativo Fotos atualizado.</td><td>Você observará uma aparência atualizada para os aplicativos Hologramas e Fotos. O Hologramas aplicativo inclui vários novos Hologramas e um criador de rótulos para facilitar a criação de texto.</td>
  </tr>
  <tr>
    <td>Captura de realidade misturada aprimorada</td><td>Vídeo do MRC de início e término de atalho de hardware.</td><td>Mantenha o volume para cima + para baixo por 3 segundos para iniciar a gravação de vídeo do MRC. Toque em ambos novamente ou use o gesto de bloom para terminar.</td>
  </tr>
  <tr>
    <td>Espaços consolidados</td><td>Simplifique o gerenciamento de espaço para hologramas em um único espaço.</td><td>HoloLens encontra seu espaço automaticamente e não exige mais que você gerencie ou selecione espaços. Se você tiver problemas com hologramas ao seu redor, poderá ir para Configurações > <b>Sistema > Hologramas > Remover hologramas próximos.</b> Se necessário, você também pode selecionar <b>Remover todos os hologramas.</b></td>
  </tr>
  <tr>
    <td>Imersão de áudio aprimorada</td><td>Agora você pode ouvir HoloLens em ambientes barulhentos e experimentar um som mais realista de aplicativos porque o som é obscurecido por paredes reais detectadas pelo dispositivo.</td><td>Você não precisa fazer nada para aproveitar o som espacial aprimorado.</td>
  </tr>
  <tr>
    <td>Explorador de Arquivos</td><td>Mova e exclua arquivos de dentro HoloLens.</td><td>Você pode usar o <b>aplicativo Explorador de Arquivos</b> para mover e excluir arquivos de dentro HoloLens.<br><br><b>Dica:</b> Se você não vir nenhum arquivo, o filtro "Recente" poderá estar ativo (o ícone de relógio está realçada no painel esquerdo). Para corrigir, selecione Este ícone de documento do dispositivo no painel esquerdo (abaixo do ícone do relógio) ou abra o menu e </b> <b>selecione Este Dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Suporte a MTP (Protocolo de Transferência de Mídia)</td><td>Permite que seu computador desktop acesse suas bibliotecas (fotos, vídeos, documentos) HoloLens fácil transferência.</td><td>Semelhante <b>a</b> outros dispositivos móveis, conecte seu HoloLens ao computador para abrir Explorador de Arquivos para acessar suas bibliotecas HoloLens (fotos, vídeos, documentos) para facilitar a transferência.<br><br><b>Dicas:</b><ul><li>Se você não vir nenhum arquivo, entre em seu HoloLens para habilitar o acesso aos seus dados.</li><li>No <b>Explorador de Arquivos</b> no computador, você pode <b></b> selecionar Propriedades do dispositivo para ver Windows número de versão do sistema operacional holográfico (versão do firmware) e o número de série do dispositivo.</li></ul><b>Problema conhecido:</b> Renomear HoloLens por <b>Explorador de Arquivos</b> no computador não está habilitado.</td>
  </tr>
  <tr>
    <td>Suporte de rede do captive portal durante a instalação</td><td>Agora você pode configurar seu HoloLens em uma rede de convidado em hotéis, centros de conferência, lojas de varejo ou empresas que usam o portal cativo.</td><td>Durante a instalação, selecione a rede, marque Conectar automaticamente e insira as informações de rede conforme solicitado.</td>
  </tr>
  <tr>
    <td>Sincronização de fotos e vídeos por meio OneDrive aplicativo</td><td>Suas fotos e vídeos do HoloLens agora serão sincronizados por meio do aplicativo OneDrive do Microsoft Store em vez do aplicativo Fotos.</td><td>Para configurar isso, baixe e OneDrive aplicativo da Loja. Na primeira, você será solicitado a carregar automaticamente suas fotos no OneDrive. Se esse prompt não aparecer, você poderá encontrar a opção nas configurações do aplicativo.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desenvolvedores

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Melhorias de mapeamento espacial</td><td>Melhorias de qualidade, simplificação e desempenho.</td><td>A malha de mapeamento espacial aparecerá mais limpa – é necessário um número menor de triângulos para representar o mesmo nível de detalhe. Você pode notar alterações na densidade do triângulo na cena.</td>
  </tr>
  <tr>
    <td>Seleção automática de ponto de foco com base no buffer de profundidade</td><td>o envio de um buffer de profundidade para Windows permite que HoloLens selecione um ponto de foco automaticamente para otimizar a estabilidade do holograma.</td><td>no Unity, vá para <b>editar > Project Configurações > Player > Plataforma Universal do Windows guia > XR Configurações</b>, expanda o item <b>Windows Mixed Reality SDK</b> e marque <b>habilitar o compartilhamento de Buffer de profundidade</b>. Isso será automaticamente verificado em busca de novos projetos.<br><br>Para aplicativos do DirectX, certifique-se de chamar o método <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> em <b>HolographicRenderingParameters</b> cada quadro para fornecer o buffer de profundidade a Windows.
</td>
  </tr>
  <tr>
    <td>Modos de Reprojeção do Holographic</td><td>agora você pode desabilitar a reprojeção posicional em HoloLens para melhorar a estabilidade do holograma de conteúdo com bloqueio de corpo rígido, como vídeo de 360 graus.</td><td>No Unity, defina <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings. reprojemode</a> como <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode. OrientationOnly</a> quando todo o conteúdo na exibição for um corpo rigidamente bloqueado.<br><br>Para aplicativos do DirectX, defina <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters. reprojemode</a> como <a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode. OrientationOnly</a> quando todo o conteúdo na exibição estiver com rigidez de corpo-bloqueado.</td>
  </tr>
  <tr>
    <td>APIs de personalização de aplicativo</td><td>Windows as APIs sabem mais sobre onde seu aplicativo está em execução, como se a exibição do dispositivo é transparente (HoloLens) ou opaca (headset de imersão) e se a exibição 2d do aplicativo UWP está aparecendo no shell holographic.</td><td>O Unity anteriormente expôs <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings. IsDisplayOpaque</a> de uma maneira que funcionou antes dessa compilação.<br><br>Para aplicativos do DirectX, agora você pode acessar APIs existentes como <a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault (). isopaco</a> e <a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview. IsCurrentViewPresentedOnHolographicDisplay</a> em HoloLens também.
</td>
  </tr>
  <tr>
      <td>Modo de pesquisa</td><td>permite que os desenvolvedores acessem os principais sensores de HoloLens ao criar aplicativos acadêmicos e industriais para testar novas ideias nos campos de visão computacional e robótica, incluindo:<ul><li>As quatro câmeras de acompanhamento de ambiente</li><li>Duas versões dos dados da câmera de mapeamento de profundidade</li><li>Duas versões de um fluxo IR-reflectivity</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">Documentação do modo de pesquisa</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicativos de exemplo do modo de pesquisa</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para clientes comerciais

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>usar várias contas de usuário Azure Active Directory em um único dispositivo</td><td>compartilhe um HoloLens com vários usuários do Azure AD, cada um com suas próprias configurações de usuário e dados de usuário no dispositivo.</td><td><a href="/hololens/hololens-multiple-users">centro de ti Pro: compartilhar HoloLens com várias pessoas</a></td>
  </tr>
  <tr>
    <td>Alterar Wi-Fi rede ao entrar</td><td>Altere Wi-Fi rede antes de entrar para permitir que outro usuário entre com sua conta de usuário do Azure AD pela primeira vez, permitindo que os usuários compartilhem dispositivos em vários locais e sites de trabalho.</td><td>Na tela de entrada, você pode usar o ícone de rede abaixo do campo senha para se conectar a uma rede. Isso é útil quando essa é a primeira vez que se conecta a um dispositivo.</td>
  </tr>
  <tr>
    <td>Registro unificado</td><td>agora, é fácil para um usuário HoloLens que configura o dispositivo com um conta Microsoft pessoal para adicionar uma conta corporativa (Azure AD) e ingressar o dispositivo em seu servidor MDM.</td><td>Entre com uma conta do Azure AD e o registro ocorre automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronização de email sem registro de MDM</td><td>suporte para sincronização de email Exchange Active Sync (EAS) sem a necessidade de registro de MDM.</td><td>Agora você pode sincronizar emails sem registro no MDM. Você pode configurar o dispositivo com uma conta da Microsoft, baixar e instalar o aplicativo de email e adicionar uma conta de email de trabalho diretamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profissionais de TI

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>novo nome do sistema operacional "Windows Holographic for Business"</td><td>Limpe a nomenclatura de edição para reduzir a confusão no aplicativo de licença de atualização de edição quando os recursos do pacote comercial estiverem habilitados no HoloLens.</td><td>você pode ver qual edição do Windows Holographic está em seu dispositivo em <b>Configurações > > do sistema</b>. "Windows Holographic for Business" será exibido se uma atualização de edição tiver sido aplicada para habilitar os recursos do pacote comercial. saiba como <a href="/hololens/hololens-upgrade-enterprise">desbloquear recursos de Windows Holographic for Business</a>.</td>
  </tr>
  <tr>
  <td>Windows Designer de configuração (WCD)</td><td>crie e edite pacotes de provisionamento para configurar HoloLens por meio do aplicativo WCD atualizado. assistente de HoloLens simples para atualização de edição, OOBE configurável, região/fuso horário, token em massa do Azure AD, rede e CSP do desenvolvedor. editor avançado filtrado para HoloLens opções com suporte, incluindo o acesso atribuído e os CSPs de gerenciamento de conta.</td><td><a href="/hololens/hololens-provisioning">centro de Pro de ti: configurar HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Configuração configurável (OOBE)</td><td>Ocultar a calibragem, treinamento de gesto/olhar e Wi-Fi telas de configuração durante a instalação.</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">centro de Pro de ti: configurar HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Suporte a token em massa do Azure AD</td><td>Pré-Registre o dispositivo no locatário do diretório do Azure AD para um fluxo de instalação de usuário mais rápido.</td><td><a href="/hololens/hololens-provisioning">centro de Pro de ti: configurar HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP DeveloperSetup</td><td>implante o perfil para configurar o HoloLens no modo de desenvolvedor. Útil para dispositivos de desenvolvimento e demonstração.</td><td><a href="/hololens/hololens-provisioning">centro de Pro de ti: configurar HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP AccountManagement</td><td>compartilhe um dispositivo HoloLens e remova os dados do usuário após os limites de saída ou de inatividade/armazenamento para uso temporário. Dá suporte a contas do Azure AD.</td><td><a href="/hololens/hololens-provisioning">centro de Pro de ti: configurar HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>Acesso atribuído</td><td>Windows acesso atribuído para os funcionários ou demonstrações de primeira linha. Bloqueio de um ou vários aplicativos. Não é necessário desbloquear o desenvolvedor.</td><td><a href="/hololens/hololens-kiosk">centro de Pro de ti: configurar HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
  <td>Acesso de convidado para dispositivos de quiosque</td><td>Windows acesso atribuído com uma conta de convidado sem senha para demonstrações. Bloqueio de um ou vários aplicativos. Não é necessário desbloquear o desenvolvedor.</td><td><a href="/hololens/hololens-kiosk#guest">centro de Pro de ti: configurar HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
    <td>Diagnóstico de configuração (OOBE)</td><td>obtenha logs de diagnóstico do HoloLens para que você possa solucionar problemas de falhas de entrada do Azure AD (antes que o Hub de comentários esteja disponível para o usuário cuja entrada falhou).</td><td>Quando a instalação ou a entrada falhar, escolha a nova opção <b>coletar informações</b> para obter os logs de diagnóstico para solução de problemas.</td>
  </tr>
  <tr>
    <td>Expiração de senha indefinida de conta local</td><td>Remova a interrupção da redefinição do dispositivo quando a senha da conta local expirar.</td><td>ao provisionar uma conta local, você não precisa mais alterar a senha a cada 42 dias em <b>Configurações</b>, pois a senha da conta não expira mais.</td>
  </tr>
  <tr>
    <td>Status e detalhes da sincronização de MDM</td><td>a funcionalidade padrão Windows para entender o status de sincronização do MDM e detalhes de dentro de HoloLens.</td><td>você pode verificar o status de sincronização de MDM para um dispositivo em <b>contas de Configurações > > acessar informações de > corporativa ou de estudante</b>. Na <b> seção status de sincronização do dispositivo <b> , você pode iniciar uma sincronização, ver áreas gerenciadas pelo MDM e criar e exportar um relatório de diagnóstico avançado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos

trabalhamos duro para fornecer uma ótima experiência de Windows Mixed Reality, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, envie [-nos seus comentários](/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Após a atualização

Você pode observar os seguintes problemas após a atualização do RS1 para o RS4 no seu HoloLens:
* **Pins redefinidos** -os aplicativos de 3x3 fixados ao seu menu Iniciar serão redefinidos para os padrões após a atualização. 
* **Redefinição de aplicativos** e hologramas colocados – os aplicativos colocados em seu mundo serão removidos após a atualização e precisarão ser reposicionadas em todo o seu espaço. 
* **O Hub** de Comentários pode não ser lançado imediatamente – imediatamente após a atualização, levará alguns minutos para que você possa iniciar alguns aplicativos de caixa de entrada, como o Hub de Comentários, enquanto eles se atualizam. 
* **Certificados Wi-Fi corporativos** precisam ser sincronizados novamente – estamos investigando um problema que exige que o HoloLens esteja conectado a uma rede diferente para que os certificados corporativos sejam sincronizados novamente com o dispositivo antes que ele possa se reconectar às redes corporativas usando certificados. 
* A Reprodução de Vídeo **H.265 HEVC** não funciona – Aplicativos que tentam reproduzir vídeos H.265 receberão uma mensagem de erro. A solução alternativa é acessar [o Windows Portal de Dispositivos](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal), selecionar **Aplicativos** na barra de navegação esquerda e **remover** o aplicativo HEVC. Em seguida, instale o [Extensão de Vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) mais recente do Microsoft Store. Estamos investigando o problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para desenvolvedores: atualizando HoloLens para dispositivos que executam Windows 10 de abril de 2018

Juntamente com uma ótima lista de novos [recursos,](#new-features-for-hololens)o RS4 (Atualização de abril de 2018) do Windows 10 HoloLens impõe alguns comportamentos de código que as versões anteriores não iam:
* Solicitações de permissão para usar recursos confidenciais **(câmera,** microfone e assim por diante) – O RS4 no HoloLens imporá solicitações de permissão para aplicativos que pretendem acessar recursos confidenciais, como a câmera ou o microfone. RS1 no HoloLens não forçaram esses prompts, portanto, se seu aplicativo assumir acesso imediato a esses recursos, ele poderá falhar no RS4 (mesmo que o usuário conceda permissão ao recurso solicitado). Leia o artigo declarações de funcionalidade do [aplicativo UWP relevante para](/windows/uwp/packaging/app-capability-declarations) obter mais informações.
* **Chamadas para aplicativos fora do seu** próprio – O RS4 HoloLens imporá o uso adequado do [ *Windows.System. Classe launcher*](/uwp/api/Windows.System.Launcher) para iniciar outro aplicativo por conta própria. Por exemplo, vimos problemas com aplicativos que chamam *Windows.System. Launcher.LaunchUriForResultsAsync* de um thread não ASTA (interface do usuário). Isso seria bem-sucedido no RS1 HoloLens, mas o RS4 exige que a chamada seja executada no thread da interface do usuário.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality na Área de Trabalho

#### <a name="visual-quality"></a>Qualidade visual

* Se você observar após a atualização de abril de 2018 do Windows 10 que os gráficos estão mais desfocados do que antes ou que o campo de exibição parece menor no headset, a configuração de desempenho automático pode ter sido alterada para manter uma taxa de quadros suficiente em uma placa gráfica menos poderosa (como nvidia 1050). Você pode substituir manualmente isso (se você escolher) navegando até Configurações > Opções de experiência de exibição do Headset > **>** de realidade misturada > Alterar e alterar "Automático" para "90 Hz". Você também pode tentar alterar **a qualidade do Visual** (na mesma página Configurações) para "Alta".

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configuração

* Ao configurar o Windows com um headset conectado, o monitor do computador poderá ficar em branco. Desconectar o headset para habilitar a saída para o monitor do computador para concluir Windows configuração.
* Se você não tiver fones de ouvido conectados, poderá perder dicas ao visitar o Windows Mixed Reality home.
* Outros Bluetooth podem causar interferência com controladores de movimento. Se os controladores de movimento têm problemas de conexão/emparelhamento/acompanhamento, certifique-se de que o rádio Bluetooth (se um dongle externo) está conectado a um local não desobstruído e não imediatamente ao lado de outro Bluetooth dongle. Além disso, tente a energia de Bluetooth periféricos durante Windows Mixed Reality sessões para ver se ajuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Jogos e aplicativos da Microsoft Store

* Alguns jogos graficamente intensivos, como ForzaVsport 7, podem causar problemas de desempenho em PCs menos capazes quando tocadas dentro Windows Mixed Reality.

#### <a name="audio"></a>Áudio

* Se Cortana estiver habilitado no computador host antes de usar o headset do Windows Mixed Reality, você poderá perder a simulação de som espacial aplicada aos aplicativos que você coloca em torno do Windows Mixed Reality home. 
   * A explicação é habilitar "Windows Sonic para Fones de Ouvido" em todos os dispositivos de áudio anexados ao computador, até mesmo no dispositivo de áudio conectado ao headset:
      1. Clique com o botão esquerdo do mouse no ícone do locutor na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
      2. Clique com o botão direito do mouse no ícone do locutor na barra de tarefas da área de trabalho e selecione "Windows Sonic para Fones de Ouvido" no menu "Configuração do locutor".
      3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
   * Outra opção é desligar "Cortana responder ao Hey Cortana" no Configurações Cortana na área de trabalho antes de iniciar  >   Windows Mixed Reality.
* Quando outro dispositivo USB multimídia (como uma câmera da Web) compartilha o mesmo hub USB (externo ou dentro do computador) com o headset do Windows Mixed Reality, em casos raros, os fones de áudio/fones de ouvido podem ter um som de ruído ou nenhum áudio. Você pode corrigir isso pelo headset em uma porta USB que não compartilha o mesmo hub que o outro dispositivo ou desconectar/desabilitar seu outro dispositivo multimídia USB.
* Em casos raros, o hub USB do computador host não pode fornecer energia suficiente para o headset Windows Mixed Reality e você pode notar um estouro de ruído dos fones de ouvido conectados ao headset.

#### <a name="holograms"></a>Hologramas

* Se você tiver colocado um grande número de hologramas em sua Windows Mixed Reality, alguns poderão desaparecer e reaparecer à medida que você olhar ao redor. Para evitar isso, remova alguns dos hologramas nessa área do Windows Mixed Reality página.

#### <a name="motion-controllers"></a>Controladores de movimento

* Se a entrada não estiver sendo roteada para o headset, o controlador de movimento desaparecerá brevemente ao ser mantido ao lado do limite da sala. Pressionar Win+Y para garantir que haja uma faixa azul no monitor da Área de Trabalho resolverá isso. 
* Ocasionalmente, quando você clicar em uma página da Web Microsoft Edge, o conteúdo será ampliado em vez de clicar.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicativo da área de trabalho na Windows Mixed Reality página

* Ferramenta de Captura funciona no aplicativo desktop.
* O aplicativo da área de trabalho não persiste na configuração de relançamento.
* Se você estiver usando Portal de Realidade Misturada visualização na área de trabalho, ao abrir o aplicativo da área de trabalho na Windows Mixed Reality página inicial, poderá notar o efeito espelho infinito. 
* A execução do aplicativo da Área de Trabalho pode causar problemas de desempenho em computadores que não são Windows Mixed Reality Ultra; não é recomendado.  
* O aplicativo da área de trabalho pode ser lançado automaticamente porque uma janela invisível na Área de Trabalho tem foco. 
* O prompt Controle de Conta de Usuário da Área de Trabalho fará com que o headset seja exibido em preto até que o prompt seja concluído.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality para SteamVR

* Talvez seja necessário iniciar o Portal de Realidade Misturada após a atualização para garantir que as atualizações de software necessárias para a atualização de Windows 10 de abril de 2018 tenham sido concluídas antes de iniciar o SteamVR. 
* Você deve estar em uma versão recente do Windows Mixed Reality para que o SteamVR permaneça compatível com a atualização de Windows 10 de abril de 2018. Certifique-se de que as atualizações automáticas estão Windows Mixed Reality para o SteamVR, que está localizado na seção "Software" de sua biblioteca no Steam.  

#### <a name="other-issues"></a>Outros problemas

>[!IMPORTANT]
>Uma versão anterior da atualização de Windows 10 de abril de 2018 por meio do insiders (versão 17134.5) não tinha uma parte do software necessária para executar Windows Mixed Reality. Recomendamos evitar essa versão se estiver usando Windows Mixed Reality. 

Identificamos uma regressão de desempenho ao usar o Surface Book 2 na versão inicial dessa atualização (10.0.17134.1) que estamos trabalhando para corrigir em um patch de atualização futuro. Sugerimos aguardar até que isso tenha sido corrigido antes de atualizar manualmente ou aguardar a atualização ser ressarçada normalmente.

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relatar problemas

Use o [aplicativo Hub de Comentários em seu computador HoloLens ou Windows 10 para](/windows/mixed-reality/give-us-feedback) fornecer comentários e relatar problemas. Usar o Hub de Comentários garante que todas as informações de diagnóstico necessárias sejam incluídas para ajudar nossos engenheiros a depurar e resolver o problema rapidamente.

>[!NOTE]
>Certifique-se de aceitar o prompt que pergunta se você gostaria que o Hub de Comentários acessasse sua pasta Documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Suporte ao headset imersivo (link externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Fornecer comentários](/windows/mixed-reality/give-us-feedback)