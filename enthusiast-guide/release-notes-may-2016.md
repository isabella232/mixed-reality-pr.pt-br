---
title: Notas sobre a versão – maio de 2016
description: Mantenha-se atualizado sobre as notas de versão do HoloLens para o Windows Holographic pode atualizar 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de versão, so, recursos, compilação, plataforma
ms.openlocfilehash: db5e3b87eaf619a0f25e07d0698499a89a1b4b12
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009496"
---
# <a name="release-notes---may-2016"></a>Notas sobre a versão – maio de 2016

A equipe do HoloLens está comprometida em fornecer as atualizações de recursos mais recentes e as principais correções por meio do programa Windows Insider. Graças a todas as suas sugestões, levamos seus comentários para o coração. Continue a [enviar comentários](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback) por meio do hub de comentários, dos [fóruns de desenvolvedores](https://forums.hololens.com) e do [Twitter via @HoloLens ](https://twitter.com/hololens).

**Versão de lançamento:** Atualização do Windows Holographic maio de 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para atualizar para a versão atual, abra o aplicativo *configurações* , acesse *Atualizar & segurança* e, em seguida, selecione o botão *verificar atualizações* .

## <a name="new-features"></a>Novos recursos

* Agora você pode **executar até três aplicativos na exibição 2D simultaneamente**, o que permite casos de uso infinitos para várias tarefas no HoloLens. Tenha o novo hub de comentários com a lista de quests aberta ao explorar os novos recursos nesse vôo.

  ![O HoloLens pode executar três aplicativos ao mesmo tempo](images/img-3625-400px.jpg)<br>
  Executar até três aplicativos na exibição 2D simultaneamente

* Adicionamos novos **comandos de voz**:
   * Tente olhar para um holograma e girá-lo dizendo "fale comigo"
   * Altere seu tamanho dizendo "maior" ou "menor"
   * Mova um aplicativo dizendo "Ei Cortana, mova o *nome do aplicativo* aqui".
* Tornamos o **desenvolvimento no HoloLens mais fácil**. Agora você pode navegar, carregar e baixar arquivos por meio do [portal do dispositivo Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal). Você pode acessar a pasta documentos, a pasta imagens e o armazenamento local para qualquer aplicativo que você carregou ou implantou por meio do Visual Studio.
* O **emulador agora dá suporte ao logon com uma conta da Microsoft** , assim como você faria em um HoloLens real, que pode ser habilitado no menu ferramentas adicionais ">>".
* **os aplicativos 2D agora ocultam a barra de aplicativos e o cursor ao assistir vídeo em tela inteira** para evitar distração. Sua experiência de assistir ao vídeo será ainda mais agradável no HoloLens.
* Você também pode **fixar fotos sem a barra de aplicativos** em seu mundo.

  ![A barra de aplicativos pode ser ocultada para aplicativos 2D, como fotos](images/img-3626-400px.jpg)<br>
  A barra de aplicativos pode ser ocultada para aplicativos com uma exibição 2D, como fotos

* O **seletor de arquivos** funciona exatamente como você espera no HoloLens.
* Atualizado o **navegador Edge** para mapear a experiência do usuário unificada com o desktop e o telefone. Habilitamos várias instâncias do seu navegador, página nova guia personalizada do HoloLens, guia de exibição e abertura em novas janelas, juntamente com melhorias de desempenho do Power &.
* O aplicativo **Groove Music** agora está no HoloLens. Visite o repositório para baixá-lo e tente reproduzi-lo em segundo plano.
* Você pode personalizar facilmente como os aplicativos são organizados em seu mundo. Tente **girar seus hologramas** no modo de ajuste simplesmente clique e arraste no círculo nos delineados verticais do meio. Você pode notar que os hologramas têm **caixas delimitadas ajustadas** para garantir a interação maximizada. Você também pode redimensionar todos os aplicativos simples verticalmente (exceto fotos e aplicativos de holograma).

  ![Os hologramas podem ser girados depois de você colocá-los no mundo](images/img-3627-400px.jpg)<br>
  Gire os hologramas depois de colocá-los em seu mundo

* Fizemos várias melhorias de **entrada** nesse vôo. Você pode conectar um mouse Bluetooth regular ao HoloLens. O clico foi ajustado para habilitar o redimensionamento & a movimentação de hologramas com um cliquedor. O teclado também está sendo executado melhor do que nunca.
* Agora você pode tirar **fotos misturadas da realidade** , pressionando o volume para cima + volume para baixo simultaneamente. Você também pode compartilhar sua realidade misturada fotos & vídeos no Facebook, Twitter e YouTube.
* O tamanho máximo de gravação de **vídeos de realidade misturada** aumentou para cinco minutos.
* O **aplicativo de fotos** agora transmite vídeos do onedrive em vez de ter que baixar todo o vídeo antes da reprodução.
* Melhoramos o modo como os **hologramas serão bem onde você os deixou**. Você também verá a opção de reconectar-se a Wi-Fi e tentar novamente se o HoloLens não conseguir detectar onde eles estão.
* O teclado tem um **layout aprimorado para inserir o endereço de email** com chaves que permitem que você insira os domínios de email mais populares com um único clique.
* **Registro de aplicativo** mais rápido e **detecção automática de fuso horário** durante o OOBE, oferecendo a melhor experiência de usuário.
* O **sensor de armazenamento** permite exibir o espaço em disco restante e usado pelo sistema e aplicativos no aplicativo de configurações.
* Contratamos o aplicativo de comentários e dentro do Hub em um único **Hub de comentários** de aplicativo, que é a ferramenta de passagem para **fornecer comentários** sobre os recursos que você adora, quais precisam de melhoria e quais podem ser feitos sem. Ao ingressar no programa Insider, você pode acompanhar as **últimas notícias do insider**, **avaliar as compilações** e ir em **buscas de comentários** do hub de comentários.
* Também [publicamos um Build do emulador do HoloLens atualizado](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) .
* Seus vídeos de realidade misturada agora parecem melhores devido à **estabilização** automática de vídeo.

## <a name="major-fixes"></a>Principais correções

Corrigimos problemas com espaços de holograma em que os espaços seriam lentos ou foram detectados incorretamente. Corrigimos um problema de desligamento que pode continuar a tentar iniciar o shell durante o desligamento.

Corrigimos um problema
* que bloqueia a capacidade de retomar um aplicativo XAML.
* onde uma falha deixaria uma tela preta e algumas linhas denteadas.
* às vezes, a rolagem se encontrava na direção errada ao usar alguns aplicativos.
* os LEDs de energia podem indicar um estado desligado quando o dispositivo ainda estava ligado.
* O WiFi pode ser desativado após a retomada do modo de espera.
* o provedor de identidade do Xbox oferece configuração de jogador e, em seguida, fica preso em um loop.
* o Shell ocasionalmente falha ao selecionar um arquivo baixado no seletor de arquivos do OneDrive.
* pressionar e segurar em um link às vezes, ambos abre uma nova guia quebrada e abre um menu de contexto.
* onde o portal de dispositivos do Windows não permitia ajustes de IPD de 50 a 80

Corrigimos problemas com fotos em que
* uma imagem, ocasionalmente, exibiria girada porque ignorando a propriedade de orientação EXIF foi ignorada.
* Ele pode falhar durante a inicialização em fotos fixas.
* os vídeos reiniciarão após a pausa, em vez de continuar de onde foi a última pausa.
* a reprodução de um vídeo compartilhado pode ser evitada se foi compartilhada durante a execução.
* As gravações de captura de realidade misturada começarão com 0,5-1 segundo de feed apenas de áudio.
* o botão Sincronizar desaparece durante a sincronização inicial do OneDrive.

Corrigimos problemas com configurações em que
* uma atualização foi necessária quando o ambiente é alterado.
* ' Enter ' no teclado não se comportaria como clicar em avançar em algumas caixas de diálogo.
* era difícil saber quando o clico falhou ao emparelhar.
* pode deixar de responder com WiFi desconectar e conectar.

Corrigimos problemas com o Cortana em que
* pode ficar preso a exibição da interface do usuário de escuta.
* perguntar "Ei Cortana, o que posso dizer" de um aplicativo de modo exclusivo fica paralisado se você respondeu, talvez, sim/não à solicitação para sair do aplicativo.
* a interface do usuário de escuta da Cortana não será retomada corretamente se você pedir à Cortana para entrar em suspensão e depois retomar.
* as consultas "em que rede estou conectado?" e "estou conectado?" pode falhar quando o primeiro perfil de rede retornar sem conectividade.
* a interface do usuário froze "ouvindo", mas ao sair de um aplicativo imediatamente começou a fazer o reconhecimento de fala novamente.
* o local em que sair do aplicativo da Cortana não permitirá que você entre novamente até uma reinicialização.
* Ela não será iniciada quando a interface do usuário da captura de realidade misturada estava ativa.

Corrigimos problemas com o Visual Studio em que
* a depuração da tarefa em segundo plano não funcionou.
* a análise de quadros no depurador de gráficos não funcionou.
* o emulador do HoloLens não apareceu na lista suspensa do Visual Studio, a menos que o TargetPlatformVersion do seu projeto tenha sido definido como 10240.

## <a name="changes-from-previous-release"></a>Alterações da versão anterior
* O comando da Cortana **Ei Cortana, reinicializar o dispositivo** não funciona. O usuário pode dizer **Ei Cortana, reiniciar** ou **Ei Cortana, reiniciar o dispositivo**.
* O modo de quiosque foi removido do produto.

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Veja também
* [Problemas conhecidos do HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [Instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [Shell](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [Como atualizar aplicativos UWP 2D para realidade misturada](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [Acessórios de hardware](https://docs.microsoft.com/windows/mixed-reality/discover/hardware-accessories)
* [Captura de realidade mista](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture)
* [Entrada de voz](https://docs.microsoft.com/windows/mixed-reality/design/voice-input)
* [Enviando um aplicativo para a Windows Store](https://docs.microsoft.com/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [Usando o emulador do HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)
