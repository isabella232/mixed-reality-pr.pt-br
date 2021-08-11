---
title: Notas sobre a versão – maio de 2016
description: Mantenha-se atualizado sobre as HoloLens de versão do Windows de maio de 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de versão, sistema operacional, recursos, build, plataforma
ms.openlocfilehash: fe93890300d46dc12041f198a772671c79c97af0d6be2fc959937932a1d108c3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202518"
---
# <a name="release-notes---may-2016"></a>Notas sobre a versão – maio de 2016

A HoloLens equipe do Windows Programa Insider está comprometida em fornecer as atualizações de recursos mais recentes e as principais correções por meio do Windows Programa Insider. Agradecemos a todas as suas sugestões. Continue nos [dando comentários por](/windows/mixed-reality/give-us-feedback) meio do Hub de Comentários, dos fóruns do [desenvolvedor](https://forums.hololens.com) e do Twitter por [meio do @HoloLens ](https://twitter.com/hololens).

**Versão de lançamento:** Windows Holographic May 2016 Update (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para atualizar para a versão atual, abra o *aplicativo Configurações,* acesse Atualizar & *Segurança* e, em seguida, selecione o botão Verificar *se há atualizações.*

## <a name="new-features"></a>Novos recursos

* Agora você pode executar até três aplicativos no modo **de exibição 2D** simultaneamente, o que permite casos de uso infinitos para várias tarefas em HoloLens. Tenha o novo Hub de Comentários com a lista de Buscas aberta enquanto explora os novos recursos neste voo.

  ![HoloLens pode executar três aplicativos ao mesmo tempo](images/img-3625-400px.jpg)<br>
  Executar até três aplicativos na exibição 2D simultaneamente

* Adicionamos novos comandos **de voz:**
   * Tente olhar para um holograma e gire-o dizendo "me enfrentar"
   * Altere seu tamanho dizendo "maior" ou "menor"
   * Mova um aplicativo dizendo "Olá, Cortana, mova o *nome do aplicativo* para aqui".
* Facilitamos o **desenvolvimento no HoloLens**. Agora você pode procurar, carregar e baixar arquivos por meio do [Windows Portal de Dispositivos](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal). Você pode acessar a pasta Documentos, a pasta Imagens e o armazenamento local para qualquer aplicativo que você carregou ou implantou por meio de Visual Studio.
* O **emulador** agora dá suporte ao logoff com uma conta microsoft, assim como você faria em um HoloLens real, que você pode habilitar no menu Ferramentas Adicionais ">>".
* **Os aplicativos 2D agora ocultam a barra de aplicativos** e o cursor ao assistir à tela inteira do vídeo para evitar a distração. Sua experiência de assistir a vídeo será ainda mais agradável no HoloLens.
* Você também pode **fixar fotos sem a barra de aplicativos** em seu mundo.

  ![A barra de aplicativos pode ser ocultada para aplicativos 2D, como fotos](images/img-3626-400px.jpg)<br>
  A barra de aplicativos pode ser ocultada para aplicativos com uma exibição 2D, como Fotos

* **O selador de** arquivos funciona da forma que você espera que ele funcione HoloLens.
* Atualizado o **navegador Edge** para mapear a experiência do usuário unificada com a área de trabalho e o telefone. Habilitamos várias instâncias do navegador, HoloLens página de nova guia personalizada, espiar tabulação e abrir em novas janelas, juntamente com melhorias de & desempenho.
* **Groove Música** aplicativo agora está HoloLens. Visite a loja para baixá-la e experimentar a reprodução em segundo plano.
* Você pode personalizar facilmente como os aplicativos são organizados em seu mundo. Tente **girar seus hologramas no modo** de ajuste simplesmente clicando e arrastando no círculo nos wireframes verticais intermediários. Você pode observar que os hologramas **têm caixas delimitadores** mais rígidas para garantir a interação maximizada. Você também pode reorganizar todos os aplicativos simples verticalmente (exceto os aplicativos Fotos e Holograma).

  ![Hologramas pode ser girado depois que você os coloca no mundo](images/img-3627-400px.jpg)<br>
  Girar hologramas depois de coloque-os em seu mundo

* Fizemos várias melhorias **de entrada** neste voo. Você pode conectar um mouse Bluetooth regular ao HoloLens. O clique foi ajustado para habilitar o re & movendo hologramas com um clique. O teclado também está sendo executado melhor do que nunca.
* Agora você pode tirar fotos **de realidade misturada** pressionando o volume para cima + volume para baixo simultaneamente. Você também pode compartilhar suas fotos capturadas de realidade misturada & vídeos para Facebook, Twitter e YouTube.
* O comprimento máximo de gravação de vídeos **de realidade** misturada foi aumentado para cinco minutos.
* **O aplicativo Photos** agora transmite vídeos OneDrive em vez de precisar baixar todo o vídeo antes da reprodução.
* Melhoramos como seus **hologramas estarão** exatamente onde você os deixou. Você também verá a opção de se reconectar Wi-Fi e tentar novamente se HoloLens não puder detectar onde eles estão.
* O teclado tem um **layout aprimorado** para inserir o endereço de email com chaves que permitem inserir os domínios de email mais populares com um único clique.
* Registro **de aplicativo mais** rápido e detecção automática de fuso **horário** durante o OOBE, dando a você a melhor experiência do usuário.
* **Armazenamento sentido permite** que você veja o espaço em disco restante e usado pelo sistema e pelos aplicativos no aplicativo de configurações.
* Convergimos o Aplicativo de Comentários e o Hub interno em um único  aplicativo Hub de **Comentários,** que é a ferramenta de acesso para nos dar comentários sobre os recursos que você adora, quais precisam de melhoria e quais você pode fazer sem eles. Ao ingressar no Programa Insider, você pode acompanhar as últimas notícias do **Insider,** os **builds** de taxa e as **buscas** de comentários do Hub de Comentários.
* Também publicamos [um build HoloLens Emulator](/windows/mixed-reality/develop/install-the-tools) atualização.
* Seus vídeos de realidade misturada agora parecem melhores devido à **estabilização automática de vídeo.**

## <a name="major-fixes"></a>Correções principais

Corrigimos problemas com espaços de holograma em que os espaços seriam lentos ou detectados incorretamente. Corrigimos um problema de desligamento que poderia continuar tentando iniciar o shell durante o desligamento.

Corrigimos um problema
* que bloqueia a capacidade de retomar um aplicativo XAML.
* em que uma falha poderia deixar uma tela preta e algumas linhas irregulares.
* às vezes, a rolagem fica na direção errada ao usar alguns aplicativos.
* os LEDs de energia podem indicar um estado desligado quando o dispositivo ainda estava conectado.
* O WiFi pode ser desligado depois de retomar o modo de espera.
* O provedor de identidade do Xbox oferece a configuração de gamertag e, em seguida, fica preso em um loop.
* O Shell ocasionalmente falha ao selecionar um arquivo baixado no OneDrive Seletor de Arquivos.
* pressionar e manter um link às vezes abre uma nova guia quebrada e abre um menu de contexto.
* em que o portal de dispositivos windows não permitia ajustes de IPD de 50 a 80

Corrigimos problemas com fotos em que
* uma imagem ocasionalmente exibiria girada porque ignorar a propriedade de orientação EXIF era ignorada.
* ele pode falhar durante a start-up em Fotos fixadas.
* os vídeos seriam reiniciados depois de pausar em vez de continuar do local em que a última pausa foi.
* A reprodução de um vídeo compartilhado poderá ser impedida se ele tiver sido compartilhado durante a reprodução.
* Captura de Realidade Misturada gravações começariam com 0,5 a 1 segundo de feed somente de áudio.
* o botão Sincronizar desaparece durante a Sincronização do OneDrive.

Corrigimos problemas com configurações em que
* uma atualização era necessária quando o ambiente muda.
* 'Enter' no teclado não se comportaria como clicar em Próximo em alguns diálogos.
* Era difícil saber quando o emparelhamento do clique falhou.
* ele pode se tornar sem resposta com WiFi desconectar e conectar.

Corrigimos problemas com o Cortana em que
* ele pode ficar preso exibindo a interface do usuário de escuta.
* perguntar "Olá Cortana, o que posso dizer" de um aplicativo de modo exclusivo ficaria preso se você respondesse talvez sim/não à solicitação para sair do aplicativo.
* O Cortana interface do usuário de escuta não será retomado corretamente se você Cortana para ir para sleep e, em seguida, retomar.
* as consultas "A qual rede estou conectado?" e o "Estou conectado?" poderá falhar quando o primeiro perfil de rede voltar sem conectividade.
* a interface do usuário começa a escutar "Escutando", mas ao sair de um aplicativo imediatamente começaria a fazer o reconhecimento de fala novamente.
* em que sair do Cortana aplicativo não permitirá que você entre novamente nele até uma reinicialização.
* ele não seria lançado quando Captura de Realidade Misturada interface do usuário estava ativa.

Corrigimos problemas com o Visual Studio em que
* A depuração da tarefa em segundo plano não funcionou.
* A análise de quadros no depurador de gráficos não funcionou.
* O HoloLens Emulator não foi exibido na lista lista Visual Studio, a menos que TargetPlatformVersion do projeto tenha sido definido como 10240.

## <a name="changes-from-previous-release"></a>Alterações da versão anterior
* O Cortana comando **Hey Cortana, reinicializar o dispositivo** não funcionará. O usuário pode dizer **Hey Cortana, restart** ou **Hey Cortana, reinicie o dispositivo**.
* O modo de quiosque foi removido do produto.

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Problemas conhecidos do HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Shell](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [Como atualizar aplicativos UWP 2D para realidade misturada](/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [Acessórios de hardware](/windows/mixed-reality/discover/hardware-accessories)
* [Captura de realidade mista](/windows/mixed-reality/mixed-reality-capture)
* [Entrada de voz](/windows/mixed-reality/design/voice-input)
* [Enviando um aplicativo para a Windows Store](/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [Usando o emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)