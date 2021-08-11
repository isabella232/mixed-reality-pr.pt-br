---
title: Notas sobre a versão – outubro de 2018
description: Mantenha-se atualizado sobre as HoloLens e Windows Mixed Reality de versão do Windows 10 de outubro de 2018/RS5.
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: notas de versão, versão, windows 10, build, rs5, so
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219958"
---
# <a name="release-notes---october-2018"></a>Notas sobre a versão – outubro de 2018

O **[Atualização de outubro de 2018 para o Windows 10](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (também conhecido como RS5) inclui novos recursos para headsets HoloLens e Windows Mixed Reality imersivos conectados a PCs. 

Para atualizar para a versão mais recente no HoloLens ou pc (para headsets imersivos (VR) do Windows Mixed Reality), abra o aplicativo **Configurações,** acesse Atualizar **& Security** e selecione o botão Verificar se há **atualizações.** Em um Windows 10, você também pode instalar manualmente o Atualização de outubro de 2018 para o Windows 10 usando a [Windows de criação de mídia.](https://www.microsoft.com/software-download/windows10)

**Versão mais recente para Desktop:** Atualização de outubro de 2018 para o Windows 10 (**10.0.17763.107**)<br>
**Versão mais recente HoloLens:** Atualização de outubro de 2018 para o Windows 10 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para headsets Windows Mixed Reality imersivos

O Atualização de outubro de 2018 para o Windows 10 inclui muitas melhorias para usar Windows Mixed Reality headsets imersivos (VR) com seu computador desktop.

### <a name="for-everyone"></a>Para todos

* **Confusão de Realidade** Misturada – abra um portal no mundo real para encontrar o teclado, ver alguém próximo ou dar uma olhada em seu ambiente sem remover o headset! Você pode ativar a Luz da Realidade Misturada menu Iniciar, pressionando Windows + Segurar no controlador de movimento ou dizendo "Ativar/desativar a câmera". Aponte o controlador na direção do que você deseja ver, como usar uma sombra no escuro.

    ![Economia de realidade misturada](images/mr-flashlight.png)

* **Novos aplicativos e maneiras de iniciar o conteúdo na página de realidade misturada**
    * Se você estiver usando o [Windows Mixed Reality para o SteamVR,](./using-steamvr-with-windows-mixed-reality.md)os títulos do SteamVR agora aparecerão no menu Iniciar e os iniciadores de aplicativo para cada um deles poderão ser colocados na casa da realidade misturada.
    
        ![Iniciadores de aplicativos do SteamVR](images/steamvr-launchers.png)
        
    * Novo *aplicativo 360 Vídeos* para descobrir uma seleção regularmente de vídeos de 360 graus.
    * Novo *aplicativo WebVR Showcase* para descobrir uma seleção regularmente de experiências webVR.
    * Os clientes Windows Mixed Reality pela primeira vez inserirão o Casa no Penhasco e o encontrarão preenchido previamente com os iniciadores de aplicativos 3D para alguns dos nossos aplicativos e jogos imersivos favoritos do Microsoft Store.
    * Microsoft Edge janelas agora incluem um *botão* Compartilhar.
* Menu Ações rápidas **–** de dentro de um aplicativo imersivo de realidade misturada, você pode pressionar o botão Windows para acessar um novo menu de ações rápidas, com acesso fácil ao *menu SteamVR,* captura de *fotos/vídeo,* uma imbuil e uma página *principal.*
* **Suporte para PCs** de treinamento – Windows Mixed Reality headsets imersivos (VR) são executados em PCs de treinamento sem a necessidade de um emulador de exibição após a conclusão da instalação.
* **Novos** recursos de áudio – agora você pode espelhar o áudio de uma experiência de  Windows Mixed Reality para o conector de áudio (ou fones de ouvido) no headset e um dispositivo de áudio conectado ao computador (como alto-falantes externos). Também adicionamos um indicador visual para o nível de volume na exibição do headset.
* **Outras melhorias**
    * Portal de Realidade Misturada atualizações agora são entregues por meio do Microsoft Store, permitindo atualizações mais rápidas entre as principais Windows versões. Observe que isso só se aplica ao aplicativo da área de trabalho e a experiência Windows Mixed Reality headset ainda é atualizada com o sistema operacional. 
    * Quando os headsets ficam em suspensão, Windows Mixed Reality aplicativos são suspensos em vez de encerrados (até que Portal de Realidade Misturada seja fechado).
    
### <a name="for-developers"></a>Para desenvolvedores

* Acompanhamento de código **[QR](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** – habilita o acompanhamento de código QR em seu aplicativo de realidade misturada, permitindo Windows Mixed Reality headsets imersivos (VR) para verificar códigos QR e reportá-los de volta para aplicativos interessados.
* Suporte a DRM de hardware para **aplicativos imersivos** – os desenvolvedores agora podem solicitar texturas de backbuffer protegidas por hardware se o hardware de exibição tiver suporte, permitindo que os aplicativos usem conteúdo protegido por hardware de fontes como o PlayReady.
* Integrar [a](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) interface do usuário de captura de realidade misturada em aplicativos imersivos – os desenvolvedores podem integrar a captura de realidade misturada em seus **[aplicativos](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** usando a interface do usuário de captura de câmera Windows integrada com apenas algumas linhas de código.

## <a name="new-features-for-hololens"></a>Novos recursos para HoloLens

O Atualização de outubro de 2018 para o Windows 10 está disponível publicamente para todos os HoloLens clientes e inclui várias melhorias, como:

### <a name="for-everyone"></a>Para todos

* Menu Ações rápidas **–** de dentro de um aplicativo de realidade misturada imersiva, você pode pressionar o botão Windows para acessar um novo menu de ações rápidas, com acesso fácil para Iniciar a gravação de *vídeo,* Tirar *fotos,* Página Inicial da Realidade *Misturada,* Change volume e *Conexão*.
* **Iniciar/parar** captura de vídeo no menu Iniciar ou ações rápidas – se você iniciar a captura de vídeo no menu menu Iniciar ou ações rápidas, poderá interromper a gravação no mesmo local. (Não se esqueça, você sempre pode fazer isso com comandos de voz também.)
* **Project** um dispositivo habilitado para Miracast – Project seu conteúdo HoloLens para um dispositivo Surface ou TV/monitor próximo se estiver usando uma exibição ou adaptador habilitado para Miracast dispositivo.
* **Novas notificações –** exibir e responder a notificações no HoloLens, assim como você faz em um computador.  
* Sobreposições úteis em **aplicativos imersivos** de realidade misturada – agora você verá sobreposições como teclado, caixas de diálogo, selador de arquivos etc. ao usar aplicativos imersivos de realidade misturada.
* **Indicador visual para** alteração de volume – quando você usa os botões de volume para cima/para baixo no HoloLens você verá um indicador visual do nível de volume no headset.
* **Novos visuais para inicialização do dispositivo** – um indicador de carregamento foi adicionado durante o processo de inicialização para fornecer comentários visuais que o sistema está carregando.
* **Compartilhamento próximo** – a Windows de compartilhamento próximo permite que você compartilhe uma captura com um dispositivo Windows próximo.  
* **Compartilhar do Microsoft Edge** - Microsoft Edge agora inclui um *botão* Compartilhar. 

### <a name="for-developers"></a>Para desenvolvedores

* Integrar [a](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) interface do usuário de captura de realidade misturada em aplicativos imersivos – os desenvolvedores podem integrar a captura de realidade misturada em seus **[aplicativos](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** usando a interface do usuário de captura de câmera Windows integrada com apenas algumas linhas de código.

### <a name="for-commercial-customers"></a>Para clientes comerciais

* **Habilitar o provisionamento pós-instalação** – agora você pode aplicar um pacote de provisionamento de runtime a qualquer momento usando Configurações.
* Acesso atribuído com grupos do **Azure AD** – agora você pode usar grupos do Azure AD para a configuração de Windows acesso atribuído para configurar a configuração de quiosque de um ou vários aplicativos.
* **Entrada de PIN na opção de** perfil da tela de entrada – a entrada do PIN agora está disponível para "Outro Usuário" na tela de entrada. 
* Ler informações de hardware do dispositivo por **meio do MDM** – os administradores de IT podem ver e acompanhar HoloLens pelo número de série do dispositivo no console do MDM.
* Definir HoloLens do dispositivo por meio do **MDM (renomear)** – os administradores de IT podem ver e renomear HoloLens dispositivos no console do MDM.

### <a name="for-international-customers"></a>Para clientes internacionais

Agora você pode usar HoloLens interface do usuário localizada para chinês simplificado ou japonês, incluindo teclado pinyin localizado, ditado, TTS (texto em fala) e comandos de voz.

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos muito para oferecer uma ótima experiência Windows Mixed Reality, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, [dê-nos comentários.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Após a atualização
Você pode observar os seguintes problemas ao usar o Atualização de outubro de 2018 para o Windows 10 em seu HoloLens:
* **Os aplicativos** podem acabar em um loop de login quando lançados de uma notificação – alguns aplicativos que exigem a login podem terminar em um loop de login infinito quando lançados de uma notificação. Por exemplo, isso pode acontecer depois de instalar o aplicativo Microsoft Portal da Empresa do Microsoft Store e inolá-lo da notificação de conclusão da instalação.
* A página de login do aplicativo pode ser concluída com uma página em branco – em alguns casos, quando um prompt de login aparece no aplicativo, após **a** conclusão, a página de login não fecha e, em vez disso, mostra uma página em branco (preta). Você pode fechar a página em branco ou movê-la para descobrir o aplicativo abaixo. Por exemplo, isso pode acontecer ao entrar durante o registro do MDM no Configurações aplicativo. 

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relatar problemas

Use o aplicativo [Hub de Comentários em seu computador HoloLens ou Windows 10 para](/windows/mixed-reality/give-us-feedback) fornecer comentários e relatar problemas. Usar o Hub de Comentários garante que todas as informações de diagnóstico necessárias sejam incluídas para ajudar nossos engenheiros a depurar e resolver o problema rapidamente.

>[!NOTE]
>Certifique-se de aceitar o prompt que pergunta se você gostaria que o Hub de Comentários acessasse sua pasta Documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Suporte ao headset imersivo (link externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Fornecer comentários](/windows/mixed-reality/give-us-feedback)