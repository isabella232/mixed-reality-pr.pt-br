---
title: Perguntas frequentes sobre hardware imersivo realado
description: Dicas Windows Mixed Reality de solução de problemas adicionais que vão além da nossa documentação de suporte ao consumidor padrão.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte, Desinstalação Windows Mixed Reality, Idiomas com Suporte
appliesto:
- Windows 10
ms.openlocfilehash: ede2620ca6a47b085a3d7b54fd6df073bfaa528e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196591"
---
# <a name="other-questions"></a>Outras perguntas

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Não há suporte para meu driver gráfico (estou recebendo erros de falha do driver gráfico).

Pesquise e execute "dxdiag":

1.  Se o resultado for "Renderer Básico", o driver de gráficos não será instalado. Para corrigir isso:
    * Vá para **Gerenciador de Dispositivos > ação > verificar se há alterações de hardware.**
    * Use Windows Update para atualizar o driver.
    * Se isso não corrigir o problema, acesse o site do fabricante e instale a atualização mais recente do driver. 
    * Se uma atualização não estiver disponível para sua GPU, o WMR poderá não ter suporte em seu dispositivo. Se você achar que deve ser, entre em contato com o [suporte do](https://support.microsoft.com).
2.  Se você receber uma versão "WDDM 2.1" ou inferior, o driver gráfico será instalado, mas talvez não seja a versão mais recente. Para obter a versão mais recente:
    * Use Windows Update para atualizar o driver.
    * Se essa atualização não corrigir o problema, acesse o site do fabricante e instale a atualização mais recente do driver. 
    * Se uma atualização não estiver disponível para sua GPU, o WMR poderá não ter suporte em seu dispositivo. Se você achar que deve ser, entre em contato com o [suporte do](https://support.microsoft.com).

Se Windows Mixed Reality a sua placa gráfica não atender aos requisitos e você achar que sim, certifique-se de que o headset esteja conectado ao cartão correto.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Minha atualização de firmware de headset Samsung Firmwarey ou Firmwarey+ está parada.

A Samsung possui e publica atualizações de firmware de headset entregues por meio de seus aplicativos de dispositivo "Configuração da Samsung HMD Setup" e "Samsung HMD Setup+". Para obter mais detalhes e ajuda com problemas de atualização de firmware Samsung, entre em contato com o atendimento ao cliente da Samsung.

Se o processo de atualização de firmware estiver travando e não houve progresso por mais de cinco minutos:

* Desconecte todos os outros dispositivos USB temporariamente e repita a atualização do firmware.
* Conecte seu headset Samsung a uma porta USB 3,0 diferente em seu PC.
* Desabilite ou desinstale qualquer software instalado que possa interferir nas atualizações de firmware, como o AORUS de Gigabyte App Center.
* Use um PC diferente para atualizar o firmware do Samsung headset.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Como fazer acessar minha área de trabalho de PC em realidade misturada?
Inicie o aplicativo de desktop no botão de fone de ouvido do **Windows > todos os aplicativos > área de trabalho** para acessar a área de trabalho de seu PC em realidade misturada.

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

Se o seu computador tiver uma GPU híbrida Nvidia, o dispositivo NVIDIA que executa o runtimebroker.exe na GPU discreta em vez de uma integrada pode ser o culpado. Para corrigir esse problema, siga estas instruções em "[Como fazer criar configurações ideais para um novo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" para adicionar C:\windows\system32\runtimebroker.exe e forçá-lo a ser executado no processador "Gráficos integrados". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meu Wi-Fi diminui quando estou usando Windows Mixed Reality.

Se você estiver usando uma conexão de Wi-Fi de 2,4 GHz, os controladores de movimento poderão reduzir o Wi-Fi:

* Alternar para uma conexão de Wi-Fi de 5 GHz, se uma estiver disponível. [Saiba mais](https://support.microsoft.com/help/4000461).
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao computador. Consulte [adaptadores recomendados.](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Recebi uma mensagem que diz para conectar e cobrar meu computador. Por quê?

Se você estiver usando um laptop, o Windows Mixed Reality funcionará melhor quando o computador estiver totalmente carregado e conectado.

## <a name="what-is-the-experience-options-setting"></a>O que é a configuração Opções de experiência?

**As configurações > realidade misturada > de** exibição do headset > experiência permitem que você altere as configurações Windows Mixed Reality desempenho. Isso permite que você escolha a melhor experiência para sua configuração de hardware em uma variedade de conteúdo. Você tem três opções de experiência para escolher:
* Automático: Windows Mixed Reality determinará a melhor experiência para sua configuração de hardware. Para a maioria das pessoas, essa é a melhor opção para começar.
* 60 Hz: define a taxa de atualização como 60 Hz e desliga determinados recursos, como captura de vídeo e visualização no Portal de Realidade Misturada.
* 90 Hz: define a taxa de atualização como 90 Hz.

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

Você poderá usar Windows Mixed Reality se o computador estiver definido como um idioma diferente. No entanto, a interface será exibida em inglês (Estados Unidos) e os comandos de fala e o ditado não estarão disponíveis. O teclado da tela de realidade mista do Windows é inglês (Estados Unidos) apenas. Para inserir texto em outro idioma, use um teclado físico conectado ao seu PC. Você também pode usar o ditado em uma das linguagens de realidade mista do Windows listadas acima — Basta selecionar microfone no teclado da tela.

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

Alguns arquivos, incluindo informações sobre seu ambiente, ainda podem estar no seu computador. Isso pode causar problemas se você decidir reinstalar o Windows Mixed Reality posteriormente. Você pode remover manualmente todas as informações restantes da realidade do Windows mista do seu computador, modificando o registro e usando o Windows PowerShell para executar comandos. _Se você modificar o registro incorretamente, poderão ocorrer problemas sérios. Certifique-se de seguir estas etapas com cuidado. Para proteção adicional, faça backup do registro antes de modificá-lo para que você possa restaurá-lo se ocorrer um problema._ Para obter mais informações, consulte [como fazer backup e reconstituir o registro no Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Para desinstalar a realidade misturada do Windows usando estes comandos:
1. Reinicie o computador.
2. Na caixa **Pesquisar,** digite "regedit" e selecione "Sim".
3. Remova esses valores do Registro:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, exclua "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, exclua "PreferDesktopSpeaker" e "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>e, em seguida, exclua "DisableSpeechInput". Observação: os itens do Registro HHKEY_CURRENT_USER devem ser excluídos para cada conta de usuário no PC que tenha usado Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, exclua "DeviceID" e "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, exclua "OnDeviceLearningCompleted".</li> 
   </ul>
4. Remova as seguintes chaves do Registro: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Feche o Editor do Registro.
6. Acesse **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** e exclua "RoomBounds.json". Repita isso para cada usuário que usou Windows Mixed Reality.
7.Abra o prompt de cmd do administrador e vá **para C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors.** Exclua o conteúdo da pasta "Dados de HeadTracking" (mas não a pasta em si).
8. Digite "powershell" na "Caixa de pesquisa", clique com o botão direito do mouse em "Windows PowerShell" e selecione "Executar como administrador".
9. Em Windows PowerShell: <ul>
   <li>No prompt de comando, copie e cole <b>DISM/online/Get-Capabilities</b>e pressione Enter.</b></li> 
   <li>Copie a identidade de recurso que começa com Analog. Holographic. desktop. Se não estiver lá, o item não será instalado e você poderá passar para a etapa 10).</li> 
   <li>Copie e cole o seguinte prompt de comando e pressione ENTER: <b>DISM/online/remove-Capability/CapabilityName: a identidade de recurso copiada na última etapa</b></li>
   </ul>
10. Reinicie o computador.

