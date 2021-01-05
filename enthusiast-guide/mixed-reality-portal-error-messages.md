---
title: Mensagens de erro do portal de realidade misturada
description: Soluções avançadas do portal de realidade mista do Windows para solução de problemas que vão além da nossa documentação de suporte padrão do consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, portal de realidade misturada
appliesto:
- Windows 10
ms.openlocfilehash: 2beb063afb3aea5f44be116e6cb906312447dbd8
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726037"
---
# <a name="mixed-reality-portal-error-messages"></a>Mensagens de erro do portal de realidade misturada

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Recebi uma mensagem de erro "algo deu errado" ou estou tendo problemas no portal de realidade misturada.

Reinicie a realidade mista do Windows:
1. Desconecte ambos os cabos de headset do seu PC.
2. Reinicie o computador.
3. Reconecte seu headset.

Se isso não funcionar, verifique se o seu PC reconhece o headset:
1. Selecione Iniciar.
2. Digite "Gerenciador de dispositivos" na caixa de pesquisa e selecione-o na lista. 
3. Expanda "dispositivos de realidade misturada" e veja se o headset está listado. 

Se não estiver listado:
1. Conecte o headset em portas diferentes no computador, se disponível.
2. Verifique as atualizações de software mais recentes do Windows Update.
3. Desinstalar e reinstalar o Windows Mixed Reality:
    1. Desconecte ambos os cabos de headset do seu PC.
    2. Selecione **configurações > realidade misturada > desinstalar**.
    3. Selecione **configurações > dispositivos > Bluetooth & outros dispositivos** para desemparelhar seus controladores de movimento. Selecione cada controlador e, em seguida, selecione "remover dispositivo".
    4. Conecte seu headset ao seu PC para reinstalar a realidade mista do Windows.
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>Estou recebendo uma mensagem de erro "verificar o cabo USB".

Conecte seu headset a uma porta USB diferente (e verifique se é um SuperSpeed USB 3,0). Além disso, tente remover todos os extensores ou hubs entre o headset e o computador.

## <a name="im-getting-a-check-your-display-cable-error-message"></a>Estou recebendo uma mensagem de erro "Verifique seu cabo de vídeo".

Use as etapas a seguir para solucionar o problema:
* Conecte seu headset a um DisplayPort 1,2 ou posterior, ou HDMI 1,4 ou posterior. Verifique se a porta corresponde à placa gráfica mais avançada em seu computador.
* Se você estiver usando um adaptador, certifique-se de que seu 4K é compatível.
* Tente usar uma porta HDMI diferente.
* Se você tiver um monitor externo conectado a uma porta HDMI, tente conectá-lo em um DisplayPort em vez disso e use a porta HDMI para o headset.
