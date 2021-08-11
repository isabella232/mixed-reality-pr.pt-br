---
title: Perguntas frequentes sobre relacionadas de hardware de imersão
description: outras Windows Mixed Reality dicas de solução de problemas que vão além da nossa documentação padrão de suporte ao consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, desinstalação Windows Mixed Reality, idiomas com suporte
appliesto:
- Windows 10
ms.openlocfilehash: 9de3ecfe2f2fc58a0afee0d7702b15131b15b12086d9f4f9851b3a9d4920afe3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219712"
---
# <a name="other-questions"></a>Outras perguntas

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Não há suporte para meu driver de gráficos (estou recebendo erros de falha de driver de gráficos).

Pesquise e execute "dxdiag":

1.  Se o resultado for "processador básico", o driver de gráficos não será instalado. Para corrigir isso:
    * Vá para **Gerenciador de dispositivos ação > > verificar se há alterações de hardware**.
    * Use Windows Update para atualizar o driver.
    * Se isso não corrigir o problema, vá para o site do fabricante e instale a atualização de driver mais recente. 
    * Se uma atualização não estiver disponível para sua GPU, WMR poderá não ter suporte em seu dispositivo. Se você considerar que deveria ser, entre em contato com o [suporte](https://support.microsoft.com).
2.  Se você receber um "WDDM 2,1" ou uma versão inferior, o driver de gráficos será instalado, mas poderá não ser a versão mais recente. Para obter a versão mais recente:
    * Use Windows Update para atualizar o driver.
    * Se essa atualização não corrigir o problema, vá para o site do fabricante e instale a atualização de driver mais recente. 
    * Se uma atualização não estiver disponível para sua GPU, WMR poderá não ter suporte em seu dispositivo. Se você considerar que deveria ser, entre em contato com o [suporte](https://support.microsoft.com).

se Windows Mixed Reality instalação indicar que a placa gráfica não atende aos requisitos e você considerar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Minha atualização do firmware Samsung Odyssey ou Odyssey + Headset está paralisada.

A Samsung possui e publica as atualizações de firmware do headset fornecidas por meio de seus aplicativos de dispositivo "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey + Setup". Para obter mais detalhes e ajuda com problemas de atualização de firmware Samsung, entre em contato com o atendimento ao cliente da Samsung.

Se o processo de atualização de firmware estiver travando e não houve progresso por mais de cinco minutos:

* Desconecte todos os outros dispositivos USB temporariamente e repita a atualização do firmware.
* Conexão seu headset Samsung a uma porta USB 3,0 diferente em seu PC.
* Desabilite ou desinstale qualquer software instalado que possa interferir nas atualizações de firmware, como o AORUS de Gigabyte App Center.
* Use um PC diferente para atualizar o firmware do Samsung headset.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Como fazer acessar minha área de trabalho de PC em realidade misturada?
inicie o aplicativo de área de trabalho no botão de fone de ouvido do **Windows > todos os aplicativos > área** de trabalho para acessar seu computador desktop em realidade misturada.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Como posso ver vários monitores em realidade misturada

Por padrão, o aplicativo de desktop alterna automaticamente para exibir o monitor com foco. Se você quiser ver todos os monitores em realidade misturada:

* Selecione o ícone de monitor no canto superior esquerdo do aplicativo.
* Desabilite "alternar monitor automaticamente".
* Escolha o monitor que você deseja ver.
* Inicie outra instância do aplicativo de desktop.
* Escolha o monitor que você deseja ver nessa instância.
* Repita para todos os seus monitores físicos.
Você precisará selecionar novamente o monitor para mostrar em cada aplicativo de desktop toda vez que reiniciar a realidade misturada.

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Meu aplicativo de área de trabalho mostra apenas uma tela preta

Se o seu computador tiver uma GPU híbrida Nvidia, o dispositivo NVIDIA que executa o runtimebroker.exe na GPU discreta em vez de uma integrada pode ser o culpado. Para corrigir esse problema, siga estas instruções em "[como fazer criar configurações de Optimus para um novo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" para adicionar C:\windows\system32\runtimebroker.exe e forçá-lo a ser executado no processador "gráficos integrados". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Minha Wi-Fi fica mais lento quando estou usando Windows Mixed Reality.

Se você estiver usando uma conexão Wi-Fi de 2,4 GHz, seus controladores de movimento poderão tornar o seu Wi-Fi mais lento:

* Mude para uma conexão de 5 GHz Wi-Fi, se houver uma disponível. [Saiba mais](https://support.microsoft.com/help/4000461).
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao seu PC. Consulte [adaptadores recomendados](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Recebi uma mensagem que disse para conectar e encarregar meu PC. Por quê?

se você estiver usando um laptop, Windows Mixed Reality funcionará melhor quando o PC for totalmente cobrado e conectado.

## <a name="what-is-the-experience-options-setting"></a>O que é a configuração de opções de experiência?

**Configurações > realidade mista > o Headset exibir > opções de experiência** permite alterar as configurações de desempenho do Windows Mixed Reality. Isso permite que você escolha a melhor experiência para sua configuração de hardware em uma variedade de conteúdo. Você tem três opções de experiência para escolher:
* automático: Windows Mixed Reality determinará a melhor experiência para sua configuração de hardware. Para a maioria das pessoas, essa é a melhor opção para começar.
* 60 Hz: define a taxa de atualização para 60 Hz e desativa determinados recursos, como captura de vídeo e visualização no portal de realidade misturada.
* 90 Hz: define a taxa de atualização para 90 Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quais idiomas têm suporte no Windows Mixed Reality

Windows Mixed Reality está disponível nos seguintes idiomas:

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

você pode usar Windows Mixed Reality se o seu PC estiver definido como um idioma diferente. No entanto, a interface será exibida em inglês (Estados Unidos) e os comandos de fala e o ditado não estarão disponíveis. o teclado da tela de Windows Mixed Reality é somente inglês (Estados Unidos). Para inserir texto em outro idioma, use um teclado físico conectado ao seu PC. você também pode usar o ditado em um dos idiomas de Windows Mixed Reality com suporte listados acima — basta selecionar microfone no teclado da tela.

Windows Mixed Reality também está disponível nos seguintes idiomas sem comandos de fala ou recursos de ditado:
* Chinês tradicional (Taiwan e Hong Kong)
* Holandês (Países Baixos)
* Coreano (Coreia do Sul)
* Russo (Rússia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Tenho dúvidas sobre o meu hardware de headset.

Para obter detalhes sobre o headset, verifique com o fabricante. Pode haver um guia de produto na caixa, ou você pode experimentar o site do fabricante.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Como fazer desinstalar Windows Mixed Reality?

1. Desconecte o headset do seu PC.
2. feche Windows Mixed Reality Portal.
2. acesse **iniciar > Configurações > realidade mista** e selecione "desinstalar".

quando estiver pronto para começar a usar o headset novamente, conecte-o e Windows Mixed Reality Portal o guiará durante a instalação.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>recebi uma mensagem "não foi possível concluir a desinstalação do Windows Mixed Reality".

Alguns arquivos, incluindo informações sobre seu ambiente, ainda podem estar no seu computador. isso pode causar problemas se você decidir reinstalar o Windows Mixed Reality mais tarde. você pode remover manualmente qualquer informação Windows Mixed Reality restante do seu computador modificando o registro e usando Windows PowerShell para executar comandos. _Se você modificar o registro incorretamente, poderão ocorrer problemas sérios. Certifique-se de seguir estas etapas com cuidado. Para proteção adicional, faça backup do registro antes de modificá-lo para que você possa restaurá-lo se ocorrer um problema._ Para obter mais informações, consulte [como fazer backup e reconstituir o registro no Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

para desinstalar Windows realidade mista usando estes comandos:
1. Reinicie o computador.
2. Na caixa de **pesquisa** , digite "regedit" e, em seguida, selecione "Sim".
3. Remova estes valores de registro:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, em seguida, exclua "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, em seguida, exclua "PreferDesktopSpeaker" e "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Configurações \Holographic</b>, em seguida, exclua "DisableSpeechInput". Observação: os itens de registro no HHKEY_CURRENT_USER devem ser excluídos para cada conta de usuário no computador que usou Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, em seguida, exclua "DeviceID" e "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, em seguida, exclua "OnDeviceLearningCompleted".</li> 
   </ul>
4. Remova as seguintes chaves do registro: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Feche o editor do registro.
6.Vá para **C:\Users\user name\AppData\Local\Packages\Microsoft. Windows. HolographicFirstRun_cw5n1h2txyewy \LocalState** e excluir "RoomBounds.json". Repita isso para cada usuário que usou Windows Mixed Reality.
7. Abra o prompt do administrador CMD e vá para **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**. Exclua o conteúdo da pasta "HeadTracking data" (mas não a pasta em si).
8.digite "powershell" na "caixa de pesquisa", clique com o botão direito do mouse em "Windows PowerShell" e selecione "executar como administrador".
9.Em Windows PowerShell: <ul>
   <li>No prompt de comando, copie e cole <b>DISM/online/Get-Capabilities</b>e pressione Enter.</b></li> 
   <li>Copie a identidade de recurso que começa com Analog. Holographic. desktop. Se não estiver lá, o item não será instalado e você poderá passar para a etapa 10).</li> 
   <li>Copie e cole o seguinte prompt de comando e pressione ENTER: <b>DISM/online/remove-Capability/CapabilityName: a identidade de recurso copiada na última etapa</b></li>
   </ul>
10. Reinicie o computador.

