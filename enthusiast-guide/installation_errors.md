---
title: Erros de instalação
description: Solução de problemas de erro de instalação avançada do Windows Mixed Reality que vai além da nossa documentação de suporte de consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, instalação
appliesto:
- Windows 10
ms.openlocfilehash: 56ead28a5809eadef1797507168b68cbaf79953e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726057"
---
# <a name="installation-errors"></a>Erros de instalação

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Seu PC não pode executar a realidade mista do Windows"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para executar a realidade mista do Windows. A configuração de hardware do seu computador pode não ser compatível com a realidade mista do Windows ou você pode precisar [atualizar para a versão mais recente do Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

A realidade mista do Windows requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2. Verifique se você tem a atualização de driver mais recente do fabricante. Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Você está quase lá – este PC não atende aos requisitos mínimos necessários para executar a realidade mista do Windows"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para a melhor experiência no Windows Mixed Reality. Seu PC pode ser capaz de executar um headset de imersão, mas pode enfrentar problemas de desempenho e não ser capaz de executar determinados aplicativos.

A realidade mista do Windows requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2. Verifique se você tem a atualização de driver mais recente do fabricante. Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Antes que possamos configurar o Windows Mixed Reality, o administrador precisará habilitá-lo para sua organização. Saiba mais "

Provavelmente, você está em uma rede gerenciada pela empresa e sua organização está usando o Windows Server Update Services (WSUS). Essas e outras políticas que podem bloquear o download. Entre em contato com o departamento de ti ou o administrador do sistema da sua organização para [habilitar a realidade mista do Windows](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Não foi possível baixar o software de realidade misturada" ou "parar de responder enquanto fazemos algum download"

* Às vezes, uma atualização pendente pode bloquear o download de software da realidade mista. Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações em espera. Se você receber um erro de Windows Update, Obtenha ajuda [aqui](https://support.microsoft.com/help/10164/fix-windows-update-errors).
* Verifique se o computador está conectado à Internet e tem pelo menos 2 GB de espaço livre de armazenamento. Verifique seu status de rede em: **configurações > rede & status de > de Internet**. Se você não conseguir se conectar à Internet, Obtenha ajuda [aqui](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues).  
* Reinicie o computador e tente novamente. 

Se essas soluções não funcionarem, tente:
* Se a conexão de rede Wi-Fi estiver definida como [medida](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq), altere-a para não medido. Para desativar uma conexão limitada, acesse: **configurações > rede & Internet > Status > alterar propriedades de conexão > definir como conexão limitada** e selecione "desativado".  
* Se você instalou uma atualização recentemente, isso pode causar problemas. Não recomendamos a remoção de quaisquer atualizações instaladas, especialmente atualizações de segurança que mantêm seu computador seguro. No entanto, às vezes, remover a atualização mais recente pode ajudar a determinar a origem do problema: 
    * Vá para **configurações > atualização & segurança > exibir o histórico de atualizações instalado > desinstalar atualizações**
    * Selecione a última atualização instalada e "Desinstalar".
    * Quando solicitado "tem certeza de que deseja desinstalar esta atualização?" responder "Sim". Se você receber um erro ao tentar essas etapas, obtenha mais detalhes sobre como corrigir os [erros do Windows Update](https://support.microsoft.com//help/10164/fix-windows-update-errors). 
    * Reinicie o computador e tente novamente. 
    * Se o Windows Mixed Reality for instalado corretamente, reinstale as atualizações mais recentes em **configurações > Windows Update > verificar se há atualizações** e ver se o Windows Mixed Reality continua funcionando. Se ele não for instalado corretamente, reinstale as atualizações e contate o suporte do Windows. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Algo deu errado e não foi possível iniciar a realidade do Windows Mixed"
Para obter mais informações sobre um código de erro específico, veja [aqui](error-codes.md). Você também pode tentar:

* Desconecte ambos os cabos de headset do PC.
* Reinicie o computador.
* Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Baixe e instale todas as atualizações em espera.
* Reconecte o headset ao PC e tente a instalação novamente.

Se essas etapas não funcionarem, desinstale e reinstale a realidade mista do Windows:
* Vá para **configurações > realidade misturada > desinstalar** e selecione "Desinstalar". 
* Reinicie o computador. 
* Para iniciar o processo de instalação novamente, basta conectar seu headset ao seu PC.
