---
title: Habilitando a segurança de conexão para comunicação remota do Holographic
description: Esta página explica como configurar a comunicação remota do Holographic para usar conexões criptografadas e autenticadas entre o Player e os aplicativos remotos.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, segurança, autenticação, servidor para cliente
ms.openlocfilehash: b2c054d19044b89b487331806b8256de1379fd53
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443462"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Habilitando a segurança de conexão para comunicação remota do Holographic

>[!IMPORTANT]
>Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Esta página fornece uma visão geral da segurança de rede para a comunicação remota do Holographic. Você encontrará informações sobre

* segurança no contexto de comunicação remota do Holographic e por que você pode precisar dela
* medidas recomendadas com base em diferentes casos de uso
* Implementando a segurança em sua solução de comunicação remota do Holographic

## <a name="overview"></a>Visão geral

O Holographic remota troca informações em uma rede. Se nenhuma medida de segurança estiver em vigor, os adversários na mesma rede poderão comprometer a integridade da comunicação ou acessar informações confidenciais.

Os aplicativos de exemplo e o Holographic Remoting Player na Windows Store vêm com a segurança desabilitada. Fazer isso torna os exemplos mais fáceis de entender. Ele também ajuda você a começar com mais rapidez com o desenvolvimento.

No entanto, para teste de campo ou uso em produção, é altamente recomendável habilitar a segurança em sua solução de comunicação remota do Holographic.

A segurança na comunicação remota do Holographic, quando configurada corretamente para seu caso de uso, oferece as seguintes garantias:

* **Autenticidade:** o Player e o aplicativo remoto podem ter certeza de que o outro lado é quem eles alegam ser
* **Confidencialidade:** nenhum terceiro pode ler as informações trocadas entre o Player e o aplicativo remoto
* **Integridade:** o Player e o remoto podem detectar qualquer alteração em trânsito em sua comunicação

>[!IMPORTANT]
>Para poder usar os recursos de segurança, você precisará implementar um [player personalizado](holographic-remoting-create-player.md) e um aplicativo remoto personalizado usando a [realidade mista do Windows](holographic-remoting-create-remote-wmr.md) ou as APIs do [OpenXR](holographic-remoting-create-remote-openxr.md) .

>[!NOTE]
> A partir da versão [2.4.0](holographic-remoting-version-history.md#v2.4.0) , os aplicativos remotos usando a [API OpenXR](../native/openxr.md) podem ser criados. Uma visão geral sobre como estabelecer uma conexão segura em um ambiente OpenXR pode ser encontrada [abaixo](#secure-connection-using-the-openxr-api).

## <a name="planning-the-security-implementation"></a>Planejando a implementação de segurança

Quando você habilita a segurança na comunicação remota do Holographic, a biblioteca de comunicação remota habilitará automaticamente as verificações de criptografia e integridade para todos os dados trocados pela rede.

No entanto, garantir a autenticação adequada requer algum trabalho extra. O que exatamente você precisa fazer depende de seu caso de uso e o restante desta seção é sobre como descobrir as etapas necessárias.

>[!IMPORTANT]
> Este artigo só pode fornecer diretrizes gerais. Se você não tiver certeza, considere consultar um especialista em segurança que possa fornecer orientação específica ao seu caso de uso.

Primeiro, uma terminologia: ao descrever as conexões de rede, os termos _cliente_ e _servidor_ serão usados. O servidor é o lado de escuta de conexões de entrada em um endereço de ponto de extremidade conhecido e o cliente é aquele que se conecta ao ponto de extremidade do servidor.

>[!NOTE]
> As funções de cliente e servidor não são ligadas a se um aplicativo está agindo como um player ou como um remoto. Embora os exemplos tenham o Player na função de servidor, é fácil reverter as funções se ele se adequar melhor ao seu caso de uso.

### <a name="planning-the-server-to-client-authentication"></a>Planejando a autenticação de servidor para cliente

O servidor usa certificados digitais para provar sua identidade para o cliente. O cliente valida o certificado do servidor durante a fase de handshake de conexão. Se o cliente não confiar no servidor, ele encerrará a conexão neste ponto.

Como o cliente valida o certificado do servidor e quais tipos de certificados de servidor podem ser usados, depende de seu caso de uso.

**Caso de uso 1:** O nome do host do servidor não está corrigido ou o servidor não é endereçado por nomes de host.

Nesse caso de uso, não é prático (ou até mesmo possível) emitir um certificado para o nome de host do servidor. A recomendação aqui é validar a impressão digital do certificado em vez disso. Como uma impressão digital humana, a impressão digital identifica exclusivamente um certificado.

É importante comunicar a impressão digital para o cliente fora de banda. Isso significa que você não pode enviá-lo pela mesma conexão de rede usada para comunicação remota. Em vez disso, você pode inseri-lo manualmente na configuração do cliente ou fazer com que o cliente verifique um código QR.

**Caso de uso 2:** O servidor pode ser acessado por um nome de host estável.

Nesse caso de uso, o servidor tem um nome de host específico e você sabe que esse nome não é provavelmente alterado. Você pode usar um certificado emitido para o nome de host do servidor. A relação de confiança será estabelecida com base no nome do host e na cadeia de confiança do certificado.

Se você escolher essa opção, o cliente precisará saber o nome do host do servidor e o certificado raiz com antecedência.

### <a name="planning-the-client-to-server-authentication"></a>Planejando a autenticação de cliente para servidor

Os clientes se autenticam no servidor usando um token de forma livre. O que esse token deve conter dependerá novamente do seu caso de uso:

**Caso de uso 1:** Você só precisa verificar a identidade do aplicativo cliente.

Nesse caso de uso, um segredo compartilhado pode ser suficiente. Esse segredo deve ser complexo o suficiente para que não possa ser adivinhado.

Um bom segredo compartilhado é um GUID aleatório, que é inserido manualmente na configuração do cliente e do servidor. Para criar um, você pode, por exemplo, usar o `New-Guid` comando no PowerShell.

Verifique se esse segredo compartilhado nunca se comunica em canais inseguros. A biblioteca de comunicação remota garante que o segredo compartilhado sempre seja enviado criptografado e somente a pares confiáveis.

**Caso de uso 2:** Você também precisa verificar a identidade do usuário do aplicativo cliente.

Um segredo compartilhado não será suficiente para cobrir esse caso de uso. Em vez disso, você pode usar tokens criados por um provedor de identidade. Um fluxo de trabalho de autenticação usando um provedor de identidade ficaria assim:

* O cliente autoriza no provedor de identidade e solicita um token
* O provedor de identidade gera um token e o envia para o cliente
* O cliente envia esse token ao servidor por meio de comunicação remota do Holographic
* O servidor valida o token do cliente em relação ao provedor de identidade

Um exemplo de um provedor de identidade é a [plataforma Microsoft Identity](https://docs.microsoft.com/azure/active-directory/develop/).

Como no caso de uso anterior, verifique se esses tokens não são enviados por meio de canais inseguros ou expostos de outra forma.

## <a name="implementing-holographic-remoting-security"></a>Implementando a segurança de comunicação remota do Holographic

Lembre-se de que você precisa implementar aplicativos remotos e de Player personalizados se desejar habilitar a segurança da conexão. Você pode usar os exemplos fornecidos como pontos de partida para seus próprios aplicativos.

Para habilitar a segurança, chame `ListenSecure()` em vez de e `Listen()` `ConnectSecure()` em vez de `Connect()` para estabelecer a conexão remota.

Essas chamadas exigem que você forneça implementações de determinadas interfaces para fornecer e validar informações relacionadas à segurança:

* O servidor precisa implementar um provedor de certificado e um validador de autenticação
* O cliente precisa implementar um provedor de autenticação e um validador de certificado.

Todas as interfaces têm uma função solicitando que você execute uma ação, que recebe um objeto de retorno de chamada como parâmetro. Usando esse objeto, você pode implementar facilmente a manipulação assíncrona da solicitação. Mantenha uma referência a esse objeto e chame a função de conclusão quando a ação assíncrona for concluída. A função de conclusão pode ser chamada de qualquer thread.

>[!TIP]
>A implementação de interfaces do WinRT pode ser feita facilmente usando C++/WinRT. O capítulo [criar APIs com C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) descreve isso em detalhes.

>[!IMPORTANT]
>O `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` dentro do pacote NuGet contém documentação detalhada para a API relacionada a conexões seguras.

### <a name="implementing-a-certificate-provider"></a>Implementando um provedor de certificados

Os provedores de certificado fornecem o aplicativo de servidor com o certificado a ser usado. A implementação consiste em duas partes:

1) Um objeto de certificado, que implementa a `ICertificate` interface:

    * `GetCertificatePfx()` deve retornar o conteúdo binário de um `PKCS#12` repositório de certificados. Um `.pfx` arquivo contém `PKCS#12` dados, portanto, seu conteúdo pode ser usado diretamente aqui.
    * `GetSubjectName()` deve retornar o nome amigável que identifica o certificado a ser usado. Se nenhum nome amigável for atribuído ao certificado, essa função deverá retornar o nome da entidade do certificado.
    * `GetPfxPassword()` deve retornar a senha necessária para abrir o repositório de certificados (ou uma cadeia de caracteres vazia se nenhuma senha for necessária).

2) Um provedor de certificados que implementa a `ICertificateProvider` interface:
    * `GetCertificate()` deve construir um objeto de certificado e retorná-lo chamando `CertificateReceived()` no objeto de retorno de chamada.

### <a name="implementing-an-authentication-validator"></a>Implementando um validador de autenticação

Os validadores de autenticação recebem o token de autenticação enviado pelo cliente e respondem com o resultado da validação.

Implemente a `IAuthenticationReceiver` interface da seguinte maneira:

* `GetRealm()` deve retornar o nome do realm de autenticação (um realm de HTTP usado durante o handshake de conexão remota).
* `ValidateToken()` deve validar o token de autenticação do cliente e chamar `ValidationCompleted()` o objeto de retorno de chamada com o resultado da validação.

### <a name="implementing-an-authentication-provider"></a>Implementando um provedor de autenticação

Os provedores de autenticação geram ou recuperam o token de autenticação a ser enviado ao servidor.

Implemente a `IAuthenticationProvider` interface da seguinte maneira:

* `GetToken()` deve gerar ou recuperar o token de autenticação a ser enviado. Quando o token estiver pronto, chame o `TokenReceived()` método no objeto de retorno de chamada.

### <a name="implementing-a-certificate-validator"></a>Implementando um validador de certificado

Os validadores de certificado recebem a cadeia de certificados enviada pelo servidor e determinam se o servidor pode ser confiável.

Para validar certificados, você pode usar a lógica de validação do sistema subjacente. Essa validação de sistema pode dar suporte a sua própria lógica de validação ou substituí-la completamente. Se você não passar seu próprio validador de certificado ao solicitar uma conexão segura, a validação do sistema será usada automaticamente.

No Windows, a validação do sistema verificará se há:

* Integridade da cadeia de certificados: os certificados formam uma cadeia consistente que termina em um certificado raiz confiável
* Validade do certificado: o certificado do servidor está dentro de seu período de validade e é emitido para fins de autenticação do servidor
* Revogação: o certificado não foi revogado
* Correspondência de nome: o nome de host do servidor corresponde a um dos nomes de host para os quais o certificado foi emitido

Implemente a `ICertificateValidator` interface da seguinte maneira:

 * `PerformSystemValidation()` deve retornar `true` se uma validação do sistema, conforme descrito acima, deve ser executada. Nesse caso, o resultado da validação do sistema é passado como uma entrada para o `ValidateCertificate()` método.
* `ValidateCertificate()` deve validar a cadeia de certificados e, em seguida, chamar `CertificateValidated()` o retorno de chamada passado com o resultado de validação final. Esse método aceita a cadeia de certificados, o nome do servidor com o qual a conexão está sendo estabelecida e se uma verificação de revogação deve ser forçada. Se a cadeia de certificados contiver vários certificados, o primeiro será o certificado do assunto.

>[!NOTE]
>Se o caso de uso exigir uma forma diferente de validação (consulte o caso de uso de certificado #1 acima), ignore a validação do sistema inteiramente. Em vez disso, use qualquer API ou biblioteca que possa manipular certificados X. 509 codificados em DER para decodificar a cadeia de certificados e executar as verificações necessárias para seu caso de uso.

## <a name="secure-connection-using-the-openxr-api"></a>Conexão segura usando a API OpenXR

Ao usar a API do [OpenXR](../native/openxr.md) , toda a conexão segura relacionada está disponível como parte da `XR_MSFT_holographic_remoting` extensão OpenXR.

>[!IMPORTANT]
>Para saber mais sobre a API de extensão de OpenXR de comunicação remota Holographic, confira a [especificação](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) que pode ser encontrada no [repositório GitHub de exemplos de comunicação remota Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Os principais elementos para conexão segura usando a `XR_MSFT_holographic_remoting` extensão OpenXR são os seguintes retornos de chamada.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, gera ou recupera o token de autenticação a ser enviado.
- `xrRemotingValidateServerCertificateCallbackMSFT`, valida a cadeia de certificados.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, valida o token de autenticação do cliente.
- `xrRemotingRequestServerCertificateCallbackMSFT`, forneça o aplicativo de servidor com o certificado a ser usado.

Esses retornos de chamada podem ser fornecidos para o tempo de execução do OpenXR remoto via `xrRemotingSetSecureConnectionClientCallbacksMSFT` e `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Além disso, a conexão segura precisa ser habilitada por meio do parâmetro secureConnection na `XrRemotingConnectInfoMSFT` estrutura ou da `XrRemotingListenInfoMSFT` estrutura, dependendo se você estiver usando o `xrRemotingConnectMSFT` ou o `xrRemotingListenMSFT` .

Essa API é bastante semelhante à API baseada em IDL descrita em [implementando a segurança de comunicação remota do Holographic](#implementing-holographic-remoting-security) , mas em vez de implementar interfaces, você deve fornecer implementações de retorno de chamada. Você pode encontrar um exemplo detalhado como parte do aplicativo de exemplo OpenXR encontrado no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Consulte Também
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando as APIs do Windows Mixed Realiy](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
