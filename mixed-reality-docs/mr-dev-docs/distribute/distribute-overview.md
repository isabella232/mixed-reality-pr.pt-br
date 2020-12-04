---
title: Distribuindo seus aplicativos
description: Uma visão geral das diferentes opções de distribuição para várias plataformas com suporte e armazenamentos de publicação.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: HoloLens, realidade misturada, headsets de imersão, aplicativo, UWP, envio, envio, filtros, metadados, requisitos de sistema, palavras-chave, wack, certificação, pacote, Appx, merchandising
ms.openlocfilehash: 4ea60d2111f99924eaa417d4ff6fa8830934588c
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578875"
---
# <a name="distributing-your-apps"></a>Distribuindo seus aplicativos

![Lancher de aplicativo 3D de pássaro flutuante na página inicial do WMR](images/distribute-hero-image.png)

Colocar seus aplicativos em mãos de seus usuários ou de fora do mundo é o mais importante, e às vezes criteriosa, faz parte de qualquer esforço de desenvolvimento. Simplificamos o processo em um conjunto de recursos listados abaixo, todos eles dependem do cenário de distribuição e implantação mais adequado para você ou sua equipe.

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
    <td><strong>Instalação do dispositivo local</strong></td>
    <td><strong>Compartilhar com qualquer pessoa</strong></td>
    <td><strong>Compartilhar com uma organização</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador do aplicativo</strong></a> (por meio de <a href="https://docs.microsoft.com/hololens/hololens-insider">compilações do Windows Insider</a>)</td>
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
    <td><a href="#additional-scenarios"><strong>Implantação personalizada do Win32</strong></a> (não disponível para dispositivos do HoloLens-Veja abaixo)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> O instalador do aplicativo não está disponível no momento para dispositivos gerenciados ou dispositivos HoloLens (1º gen).

## <a name="additional-scenarios"></a>Cenários adicionais

* Para a implantação de aplicativos Win32, incluindo o fluxo e o jogo pass, você pode produzir um Win32. Arquivo EXE usando o destino de Build do PC autônomo do Unity e envie seus aplicativos normalmente para a plataforma escolhida. 

* Se você precisar instalar um aplicativo do HoloLens 2 enquanto estiver offline, consulte as instruções [offline seguras do hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) ou instale o aplicativo por meio de um pacote de provisionamento sem habilitar o modo de desenvolvedor.

* Você também pode implantar compilações em seu dispositivo e compartilhá-las com outros desenvolvedores que têm o modo de desenvolvedor habilitado [Implantando e Depurando com o Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou [instalando um pacote de aplicativos com o portal do dispositivo](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).

## <a name="see-also"></a>Confira também
* [Localizando, instalando e desinstalando aplicativos do Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
