---
title: Distribuindo seus aplicativos
description: Uma visão geral das diferentes opções de distribuição para várias plataformas com suporte e armazenamentos de publicação.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realidade misturada, headsets de imersão, aplicativo, UWP, envio, envio, filtros, metadados, requisitos de sistema, palavras-chave, wack, certificação, pacote, Appx, merchandising
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215971"
---
# <a name="distributing-your-apps"></a>Distribuindo seus aplicativos

![Lancher de aplicativo 3D de pássaro flutuante na página inicial do WMR](images/distribute-hero-image.png)

Colocar seus aplicativos em mãos de seus usuários ou de fora do mundo é o mais importante, e às vezes criteriosa, faz parte de qualquer esforço de desenvolvimento. Simplificamos o processo em um conjunto de recursos, que dependem do cenário de distribuição e implantação mais adequado para você ou sua equipe.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opções de distribuição

> [!IMPORTANT]
> * Se você estiver compartilhando seu aplicativo com outra parte, será necessário compilar e fornecer o arquivo Appx. 
>     * Se estiver usando o instalador do aplicativo, você também precisará compartilhar o certificado com o usuário.
> 
> * Se você estiver compartilhando com uma organização, precisará de uma conta corporativa ou de estudante e acessar a infraestrutura [MDM (gerenciamento de dispositivo móvel)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) das organizações.  
>    * Se você for a parte compartilhada, precisará ser um administrador em seu locatário e usar o [centro de administração do Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) para disponibilizar o aplicativo. Outra opção é compartilhar o arquivo Appx e as dependências do aplicativo com o usuário final.
>    * Se você for o usuário final, o aplicativo será baixado automaticamente ou estará disponível para download depois que você se registrar no locatário da organização de compartilhamento. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Cenário</strong></td>
    <td><strong>Instalações de dispositivo local</strong></td>
    <td><strong>Compartilhar com qualquer pessoa</strong></td>
    <td><strong>Compartilhar com uma organização</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador do aplicativo</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portal da Empresa</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM – instalação necessária do aplicativo</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Pacote de provisionamento</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Implantação personalizada do Win32</strong></a> (não disponível para dispositivos do HoloLens-Veja abaixo)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> O instalador do aplicativo não está disponível no momento para dispositivos gerenciados ou dispositivos HoloLens (1º gen).

## <a name="other-scenarios"></a>Outros cenários

* Você pode produzir um Win32. Arquivo EXE usando o destino de Build do PC autônomo do Unity para a implantação do aplicativo Win32, incluindo o fluxo e o jogo pass. Quando você tiver o. EXE, você pode enviar seus aplicativos normalmente para a plataforma escolhida. 

* Se você precisar instalar um aplicativo do HoloLens 2 enquanto estiver offline, consulte as instruções [offline seguras do hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) ou instale o aplicativo por meio de um pacote de provisionamento sem habilitar o modo de desenvolvedor.

* Você também pode implantar compilações em seu dispositivo e compartilhá-las com outros desenvolvedores que têm o modo de desenvolvedor habilitado [Implantando e Depurando com o Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou [instalando um pacote de aplicativos com o portal do dispositivo](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Confira também
* [Localizando, instalando e desinstalando aplicativos do Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

