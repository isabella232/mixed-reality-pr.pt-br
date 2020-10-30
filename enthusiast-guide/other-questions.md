---
title: Outras perguntas
description: Dicas adicionais de solução de problemas do Windows Mixed realm que vão além da documentação de suporte padrão do consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade mista, realidade virtual, VR, MR, solucionar problemas, erros, ajuda, suporte, desinstalar a realidade mista do Windows, idiomas com suporte
appliesto:
- Windows 10
ms.openlocfilehash: aa61148a115ae295c1dc64b575a2fae7b0111470
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044457"
---
# <a name="other-questions"></a>Outras perguntas

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Não há suporte para meu driver de gráficos (estou recebendo erros de falha de driver de gráficos).

Pesquise e execute "dxdiag":

1.  Se o resultado for "processador básico", o driver de gráficos não será instalado. Para corrigir isso:
    * Vá para **Device Manager ação > > verificar se há alterações de hardware** .
    * Use Windows Update para atualizar o driver.
    * Se isso não corrigir o problema, vá para o site do fabricante e instale a atualização de driver mais recente. 
    * Se uma atualização não estiver disponível para sua GPU, WMR poderá não ter suporte em seu dispositivo. Se você considerar que deveria ser, entre em contato com o [suporte](https://support.microsoft.com).
2.  Se você receber um "WDDM 2,1" ou uma versão inferior, o driver de gráficos será instalado, mas poderá não ser a versão mais recente. Para obter a versão mais recente:
    * Use Windows Update para atualizar o driver.
    * Se essa atualização não corrigir o problema, vá para o site do fabricante e instale a atualização de driver mais recente. 
    * Se uma atualização não estiver disponível para sua GPU, WMR poderá não ter suporte em seu dispositivo. Se você considerar que deveria ser, entre em contato com o [suporte](https://support.microsoft.com).
    
Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Minha atualização do firmware Samsung Odyssey ou Odyssey + Headset está paralisada.

A Samsung possui e publica as atualizações de firmware do headset fornecidas por meio de seus aplicativos de dispositivo "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey + Setup". Para obter mais detalhes e ajuda com problemas de atualização de firmware do Samsung, entre em contato com o atendimento ao cliente da Samsung.

Se o processo de atualização de firmware estiver travando e não houve progresso por mais de cinco minutos:
* Desconecte todos os outros dispositivos USB temporariamente e repita a atualização do firmware.
* Conecte seu headset Samsung a uma porta USB 3,0 diferente em seu PC.
* Desabilite e/ou desinstale todos os softwares instalados que possam interferir nas atualizações de firmware, como AORUS de Gigabyte App Center.
* Use um computador diferente para executar a atualização de firmware do Samsung headset.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Como fazer acessar minha área de trabalho de PC em realidade misturada?
Inicie o aplicativo de desktop no botão de fone de ouvido do **Windows > todos os aplicativos > área de trabalho** para acessar a área de trabalho de seu PC em realidade misturada.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Como posso ver vários monitores em realidade misturada?
Por padrão, o aplicativo de desktop alterna automaticamente para exibir o monitor com foco. Se você quiser ver todos os monitores em realidade misturada: 
* Clique no ícone de monitor no canto superior esquerdo do aplicativo.
* Desabilite "alternar monitor automaticamente".
* Escolha o monitor que você deseja ver.
* Inicie outra instância do aplicativo de desktop.
* Escolha o monitor que você deseja ver nessa instância.
* Repita para todos os seus monitores físicos.
Observe que você precisará selecionar novamente o monitor para mostrar em cada aplicativo de desktop toda vez que reiniciar a realidade misturada. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Meu aplicativo de área de trabalho mostra apenas uma tela preta.
Se o seu computador tiver uma GPU híbrida Nvidia, o problema poderá ser causado pelo dispositivo NVIDIA executando o runtimebroker.exe na GPU discreta em vez de um integrado. Para corrigir esse problema, siga estas instruções em "[como fazer criar configurações de Optimus para um novo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" para adicionar C:\windows\system32\runtimebroker.exe e forçá-lo a ser executado no processador "gráficos integrados". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Minha Wi-Fi fica mais lento quando estou usando a realidade mista do Windows.

Se você estiver usando uma conexão de Wi-Fi de 2,4 GHz, seus controladores de movimento poderão retardar o Wi-Fi. Tente uma das seguintes opções:
* Alterne para uma conexão Wi-Fi de 5 GHz, se houver uma disponível. [Saiba mais](https://support.microsoft.com/en-us/help/4000461).
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao seu computador. Consulte [adaptadores recomendados](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Recebi uma mensagem que disse para conectar e encarregar meu PC. Por quê?

Se você estiver usando um laptop, a realidade mista do Windows funcionará melhor quando o PC for totalmente cobrado e conectado. 

## <a name="what-is-the-experience-options-setting"></a>O que é a configuração de opções de experiência?

Essa configuração ( **configurações > realidade misturada > exibição de fone de ouvido > opções de experiência** ) permite que você altere as configurações de desempenho da realidade mista do Windows. Isso permite que você escolha a melhor experiência para sua configuração de hardware em uma variedade de conteúdo. Estas são as opções:
* Automático: a realidade mista do Windows determinará a melhor experiência para sua configuração de hardware. Para a maioria das pessoas, essa é a melhor opção para começar.
* 60Hz: define a taxa de atualização para 60Hz e desativa determinados recursos, como captura de vídeo e visualização no portal de realidade misturada.
* 90Hz: define a taxa de atualização para 90Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quais idiomas têm suporte no Windows Mixed Reality?

A realidade mista do Windows está disponível nos seguintes idiomas:
* Chinês Simplificado (China)
* Inglês (Austrália)
* Inglês (Canadá)
* Inglês (Grã-Bretanha)
* Inglês (Estados Unidos)
* Francês (Canadá)
* Francês (França)
* Alemão (Alemanha)
* Italiano (Itália)
* Japonês (Japão)
* Espanhol (México)
* Espanhol (Espanha)

Você pode usar a realidade mista do Windows se seu PC estiver definido como um idioma diferente, mas a interface aparecerá em inglês (Estados Unidos), e os comandos de fala e o ditado não estarão disponíveis. O teclado da tela de realidade mista do Windows é inglês (Estados Unidos) apenas. Para inserir texto em outro idioma, use um teclado físico conectado ao seu PC. Você também pode usar o ditado em uma das linguagens de realidade mista do Windows listadas acima — Basta selecionar microfone no teclado da tela.

A realidade mista do Windows também está disponível nos seguintes idiomas sem comandos de fala ou recursos de ditado:
* Chinês tradicional (Taiwan e Hong Kong)
* Holandês (Países Baixos)
* Coreano (Coreia do Sul)
* Russo (Rússia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Tenho dúvidas sobre o meu hardware de headset.

Para obter detalhes sobre o headset, verifique com o fabricante. Pode haver um guia de produto na caixa, ou você pode experimentar o site do fabricante.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Como fazer desinstalar o Windows Mixed Reality?

1. Desconecte o headset do seu PC.
2. Feche o portal de realidade mista do Windows.
2. Vá para  **iniciar > configurações > realidade misturada** e selecione "Desinstalar".

Quando estiver pronto para começar a usar o headset novamente, conecte-o e o portal do Windows Mixed Reality o guiará pela instalação.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Recebi uma mensagem "não foi possível concluir a desinstalação do Windows Mixed Reality".

Alguns arquivos, incluindo informações sobre seu ambiente, ainda podem estar no seu computador. Isso pode causar problemas se você decidir reinstalar o Windows Mixed Reality posteriormente. Você pode remover manualmente todas as informações restantes da realidade do Windows mista do seu computador, modificando o registro e usando o Windows PowerShell para executar comandos. _Se você modificar o registro incorretamente, poderão ocorrer problemas sérios. Certifique-se de seguir estas etapas com cuidado. Para proteção adicional, faça backup do registro antes de modificá-lo para que você possa restaurá-lo se um problema ocorrer._ Para obter mais informações, consulte [como fazer backup e reconstituir o registro no Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Para desinstalar o Windows Mixed Reality usando estes comandos:
1. Reinicie o computador.
2. Na caixa de **pesquisa** , digite "regedit" e, em seguida, selecione "Sim".
3. Remova estes valores de registro:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, em seguida, exclua "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, em seguida, exclua "PreferDesktopSpeaker" e "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, em seguida, exclua "DisableSpeechInput". Observação: os itens do registro no HHKEY_CURRENT_USER devem ser excluídos para cada conta de usuário no computador que usou a realidade mista do Windows.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, em seguida, exclua "DeviceID" e "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, em seguida, exclua "OnDeviceLearningCompleted".</li> 
   </ul>
4. Remova as seguintes chaves do registro: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Feche o editor do registro.
6. Vá para **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** e exclua "RoomBounds.json". Repita isso para cada usuário que usou a realidade mista do Windows.
7. Abra o prompt do administrador CMD e vá para **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Exclua o conteúdo da pasta "HeadTracking data" (mas não a pasta em si).
8. Digite "PowerShell" na "caixa de pesquisa", clique com o botão direito do mouse em "Windows PowerShell" e selecione "executar como administrador".
9. No Windows PowerShell: <ul>
   <li>No prompt de comando, copie e cole <b>DISM/online/Get-Capabilities</b>e pressione Enter.</b></li> 
   <li>Copie a identidade de recurso que começa com Analog. Holographic. desktop (se não estiver lá, isso significa que esse item não está instalado. Nesse caso, pule para a etapa 10).</li> 
   <li>Copie e cole o seguinte prompt de comando e pressione ENTER: <b>DISM/online/remove-Capability/CapabilityName: a identidade de recurso copiada na última etapa</b></li>
   </ul>
10. Reinicie o computador.

