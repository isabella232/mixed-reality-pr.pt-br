---
title: Erros de instalação
description: solução de problemas de erro de instalação avançada Windows Mixed Reality que vai além da nossa documentação de suporte de consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, instalação
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213184"
---
# <a name="installation-errors"></a>Erros de instalação

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Seu PC não pode executar Windows Mixed Reality"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para executar Windows Mixed Reality. a configuração de hardware do seu computador pode não ser compatível com Windows Mixed Reality, ou talvez seja necessário [atualizar para a versão mais recente do Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

Windows Mixed Reality requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2. Verifique se você tem a atualização de driver mais recente do fabricante. se Windows Mixed Reality instalação indicar que a placa gráfica não atende aos requisitos e você considerar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Você está quase lá – este computador não atende aos requisitos mínimos necessários para executar o Windows Mixed Reality"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para a melhor experiência em Windows Mixed Reality. Seu PC pode ser capaz de executar um headset de imersão, mas pode enfrentar problemas de desempenho e não ser capaz de executar determinados aplicativos.

Windows Mixed Reality requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2. Verifique se você tem a atualização de driver mais recente do fabricante. se Windows Mixed Reality instalação indicar que a placa gráfica não atende aos requisitos e você considerar que ela faz, verifique se o headset está conectado ao cartão correto.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"antes que possamos configurar Windows Mixed Reality, o administrador precisará habilitá-lo para sua organização. Saiba mais "

provavelmente, você está em uma rede gerenciada pela empresa e sua organização está usando o Windows Server Update Services (WSUS). Essas e outras políticas que podem bloquear o download. Contate o departamento de ti ou o administrador do sistema de sua organização para [habilitar Windows Mixed Reality](/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Não foi possível baixar o software de realidade misturada" ou "parar de responder enquanto fazemos algum download"

* Às vezes, uma atualização pendente pode bloquear o download de software da realidade mista. vá para **Configurações > atualizar & > de segurança Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações em espera. se você receber um erro de Windows Update, obtenha ajuda [aqui](https://support.microsoft.com/help/10164/fix-windows-update-errors).
* Verifique se o computador está conectado à Internet e tem pelo menos 2 GB de espaço livre de armazenamento. verifique seu status de rede em: **Configurações > rede & status de > da Internet**. Se você não conseguir se conectar à Internet, Obtenha ajuda [aqui](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues).  
* Reinicie o computador e tente novamente. 

Se essas soluções não funcionarem, tente:
* Se a conexão de rede Wi-Fi estiver definida como [medida](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq), altere-a para não medido. para desativar uma conexão limitada, acesse: **Configurações > rede & Status da Internet > > alterar propriedades de conexão > definir como conexão limitada** e selecione "desativado".  
* Se você instalou uma atualização recentemente, isso pode causar problemas. Não recomendamos a remoção de quaisquer atualizações instaladas, especialmente atualizações de segurança que mantêm seu computador seguro. No entanto, às vezes, remover a atualização mais recente pode ajudar a determinar a origem do problema: 
    * vá para **Configurações > atualizar & segurança > exibir o histórico de atualizações instalado > desinstalar atualizações**
    * Selecione a última atualização instalada e "Desinstalar".
    * Quando solicitado "tem certeza de que deseja desinstalar esta atualização?" responder "Sim". Se você receber um erro ao tentar essas etapas, obtenha mais detalhes sobre como corrigir os [erros do Windows Update](https://support.microsoft.com//help/10164/fix-windows-update-errors). 
    * Reinicie o computador e tente novamente. 
    * se Windows Mixed Reality for instalado corretamente, reinstale as atualizações mais recentes em **Configurações > Windows Update > verifique** se há atualizações e veja se Windows Mixed Reality continua a funcionar. se ele não for instalado corretamente, reinstale as atualizações e contate o suporte do Windows. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Algo deu errado e não foi possível iniciar o Windows Mixed Reality"
Para obter mais informações sobre um código de erro específico, veja [aqui](error-codes.md). Você também pode tentar:

* Desconecte ambos os cabos de headset do PC.
* Reinicie o computador.
* vá para **Configurações > atualizar & > de segurança Windows Update** e verifique se Windows Update está ativado. Baixe e instale todas as atualizações em espera.
* Reconecte o headset ao PC e tente a instalação novamente.

Se essas etapas não funcionarem, desinstale e reinstale Windows Mixed Reality:
* vá para **Configurações > realidade mista > desinstalar** e selecione "desinstalar". 
* Reinicie o computador. 
* Para iniciar o processo de instalação novamente, basta conectar seu headset ao seu PC.