---
title: Habilitando a segurança de conexão para a Holographic Remoting
description: Esta página explica como configurar o Holographic Remoting para usar conexões criptografadas e autenticadas entre o player e aplicativos remotos.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, segurança, autenticação, servidor para cliente
ms.openlocfilehash: fa23994ff4ab49d313fe24a67974bf4d90454e511658e0663c61d7b129b10f9e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223576"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Habilitando a segurança de conexão para a Holographic Remoting

>[!IMPORTANT]
>Essas diretrizes são específicas da Holographic Remoting no HoloLens 2.

Esta página fornece uma visão geral da segurança de rede para Comunicação Comunicação Remográfica Holográfica. Você encontrará informações sobre

* segurança no contexto de holographic remoting e por que você pode precisar dela
* medidas recomendadas com base em diferentes casos de uso
* implementando a segurança em sua solução de remoção holográfica

## <a name="holographic-remoting-security"></a>Segurança de remoção holográfica

A comunicação remográfica holográfica troca informações por uma rede. Se nenhuma medida de segurança estiver em uso, os adversários na mesma rede poderão comprometer a integridade da comunicação ou acessar informações confidenciais.

Os aplicativos de exemplo e o Holographic Remoting Player na Windows Store vêm com a segurança desabilitada. Fazer isso torna os exemplos mais fáceis de entender. Ele também ajuda você a começar mais rapidamente com o desenvolvimento.

Para teste de campo ou produção, é fortemente recomendável habilenciar a segurança em sua solução de Remoção Holográfica.

A segurança no Holographic Remoting, quando configurada corretamente para seu caso de uso, oferece as seguintes garantias:

* **Autenticidade:** o player e o aplicativo remoto podem ter certeza de que o outro lado é quem eles dizem ser
* **Confidencialidade:** nenhum terceiro pode ler as informações trocadas entre o player e o aplicativo remoto
* **Integridade:** o player e o remoto podem detectar alterações em trânsito em sua comunicação

>[!IMPORTANT]
>Para poder usar recursos de segurança, você precisará implementar um [player](holographic-remoting-create-player.md) personalizado e um aplicativo remoto personalizado usando apIs [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) [ou OpenXR.](holographic-remoting-create-remote-openxr.md)

>[!NOTE]
> A partir da [versão 2.4.0,](holographic-remoting-version-history.md#v2.4.0) aplicativos remotos usando a [API openXR](../native/openxr.md) podem ser criados. Uma visão geral sobre como estabelecer uma conexão segura em um ambiente OpenXR pode ser encontrada [abaixo.](#secure-connection-using-the-openxr-api)

## <a name="planning-the-security-implementation"></a>Planejando a implementação de segurança

Quando você habilita a segurança na Comunicação Remográfica Holográfica, a biblioteca de comunicação remotária habilita automaticamente as verificações de criptografia e integridade de todos os dados trocados pela rede.

No entanto, garantir a autenticação adequada requer algum trabalho extra. O que você precisa fazer exatamente depende do seu caso de uso e o restante desta seção é descobrir as etapas necessárias.

>[!IMPORTANT]
> Este artigo só pode fornecer diretrizes gerais. Se você não tiver certeza, considere consultar um especialista em segurança que possa lhe dar diretrizes específicas para seu caso de uso.

Primeiro, alguma terminologia: ao descrever as conexões de rede, os termos _cliente_ e _servidor_ serão usados. O servidor é o lado que escuta conexões de entrada em um endereço de ponto de extremidade conhecido e o cliente é aquele que está se conectando ao ponto de extremidade do servidor.

>[!NOTE]
> As funções de cliente e e servidor não estão vinculadas a se um aplicativo está atuando como um player ou como um remoto. Embora os exemplos tenham o player na função de servidor, será fácil reverter as funções se ele se adequar melhor ao seu caso de uso.

### <a name="planning-the-server-to-client-authentication"></a>Planejando a autenticação de servidor para cliente

O servidor usa certificados digitais para provar sua identidade para o cliente. O cliente valida o certificado do servidor durante a fase de handshake de conexão. Se o cliente não confiar no servidor, ele encerrará a conexão neste ponto.

Como o cliente valida o certificado do servidor e quais tipos de certificados de servidor podem ser usados, depende do seu caso de uso.

**Caso de uso 1:** O nome do host do servidor não é corrigido ou o servidor não é endereçado pelo nome do host.

Nesse caso de uso, não é prático (nem mesmo possível) emitir um certificado para o nome do host do servidor. Recomendamos que você valide a impressão digital do certificado. Como uma impressão digital humana, a impressão digital identifica exclusivamente um certificado.

É importante comunicar a impressão digital para o cliente fora de banda. Isso significa que você não pode enviá-lo pela mesma conexão de rede usada para comunicação comunicação. Em vez disso, você pode inserir manualmente na configuração do cliente ou fazer com que o cliente digitalizar um código QR.

**Caso de uso 2:** O servidor pode ser alcançado em um nome de host estável.

Nesse caso de uso, o servidor tem um nome de host específico e você sabe que esse nome provavelmente não será alteração. Em seguida, você pode usar um certificado emitido para o nome do host do servidor. A confiança será estabelecida com base no nome do host e na cadeia de confiança do certificado.

Se você escolher essa opção, o cliente precisará saber o nome do host do servidor e o certificado raiz com antecedência.

### <a name="planning-the-client-to-server-authentication"></a>Planejando a autenticação de cliente para servidor

Os clientes são autenticados no servidor usando um token de forma livre. O que esse token deve conter dependerá novamente do seu caso de uso:

**Caso de uso 1:** Você só precisa verificar a identidade do aplicativo cliente.

Nesse caso de uso, um segredo compartilhado pode ser suficiente. Esse segredo deve ser complexo o suficiente para não ser adivinhado.

Um bom segredo compartilhado é um GUID aleatório, que é inserido manualmente na configuração do servidor e do cliente. Para criar um, você pode, por exemplo, usar o `New-Guid` comando no PowerShell.

Certifique-se de que esse segredo compartilhado nunca seja comunicado por canais inseguros. A biblioteca de remoting garante que o segredo compartilhado sempre seja enviado criptografado e somente para pares confiáveis.

**Caso de uso 2:** Você também precisa verificar a identidade do usuário do aplicativo cliente.

Um segredo compartilhado não será suficiente para cobrir esse caso de uso. Em vez disso, você pode usar tokens criados por um provedor de identidade. Um fluxo de trabalho de autenticação usando um provedor de identidade teria esta aparência:

* O cliente autoriza no provedor de identidade e solicita um token
* O provedor de identidade gera um token e o envia para o cliente
* O cliente envia esse token para o servidor por meio da Holographic Remoting
* O servidor valida o token do cliente em relação ao provedor de identidade

Um exemplo de um provedor de identidade é o [plataforma de identidade da Microsoft](/azure/active-directory/develop/).

Como no caso de uso anterior, certifique-se de que esses tokens não sejam enviados por canais inseguros ou expostos de outra forma.

## <a name="implementing-holographic-remoting-security"></a>Implementando a segurança de remoção holográfica

Lembre-se de que você precisa implementar aplicativos remotos e de player personalizados se quiser habilitar a segurança de conexão. Você pode usar os exemplos fornecidos como pontos de partida para seus próprios aplicativos.

Para habilitar a segurança, `ListenSecure()` chame em vez de e em vez de para estabelecer a conexão de conexão de `Listen()` `ConnectSecure()` `Connect()` remoção.

Essas chamadas exigem que você forneça implementações de determinadas interfaces para fornecer e validar informações relacionadas à segurança:

* O servidor precisa implementar um provedor de certificados e um validador de autenticação
* O cliente precisa implementar um provedor de autenticação e um validador de certificado.

Todas as interfaces têm uma função solicitando que você tome medidas, que recebe um objeto de retorno de chamada como parâmetro. Usando esse objeto, você pode implementar facilmente a manipulação assíncrona da solicitação. Mantenha uma referência a esse objeto e chame a função de conclusão quando a ação assíncrona for concluída. A função de conclusão pode ser chamada de qualquer thread.

>[!TIP]
>A implementação de interfaces WinRT pode ser feita facilmente usando C++/WinRT. O [capítulo ApIs de Autor com C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) descreve isso em detalhes.

>[!IMPORTANT]
>O `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` dentro do pacote NuGet contém documentação detalhada para a API relacionada a conexões seguras.

### <a name="implementing-a-certificate-provider"></a>Implementando um provedor de certificados

Os provedores de certificado fornecem ao aplicativo de servidor o certificado a ser usado. A implementação consiste em duas partes:

1) Um objeto de certificado, que implementa a `ICertificate` interface :

    * `GetCertificatePfx()` deve retornar o conteúdo binário de um armazenamento `PKCS#12` de certificados. Um `.pfx` arquivo contém dados para que seu conteúdo possa ser usado diretamente `PKCS#12` aqui.
    * `GetSubjectName()` deve retornar o nome amigável que identifica o certificado a ser usado. Se nenhum nome amigável for atribuído ao certificado, essa função deverá retornar o nome da assunto do certificado.
    * `GetPfxPassword()` deve retornar a senha necessária para abrir o armazenamento de certificados (ou uma cadeia de caracteres vazia se nenhuma senha for necessária).

2) Um provedor de certificados que implementa a `ICertificateProvider` interface :
    * `GetCertificate()` deve construir um objeto de certificado e devolvê-lo chamando `CertificateReceived()` no objeto de retorno de chamada.

### <a name="implementing-an-authentication-validator"></a>Implementando um validador de autenticação

Os validadores de autenticação recebem o token de autenticação enviado pelo cliente e respondem com o resultado da validação.

Implemente `IAuthenticationReceiver` a interface da seguinte forma:

* `GetRealm()` deve retornar o nome do realm de autenticação (um realm HTTP usado durante o handshake de conexão de conexão de remoção).
* `ValidateToken()` deve validar o token de autenticação do cliente e `ValidationCompleted()` chamar no objeto de retorno de chamada com o resultado da validação.

### <a name="implementing-an-authentication-provider"></a>Implementando um provedor de autenticação

Os provedores de autenticação geram ou recuperam o token de autenticação a ser enviado ao servidor.

Implemente `IAuthenticationProvider` a interface da seguinte forma:

* `GetToken()` deve gerar ou recuperar o token de autenticação a ser enviado. Quando o token estiver pronto, chame `TokenReceived()` o método no objeto de retorno de chamada.

### <a name="implementing-a-certificate-validator"></a>Implementando um validador de certificado

Validadores de certificado recebem a cadeia de certificados enviada pelo servidor e determinam se o servidor pode ser confiável.

Para validar certificados, você pode usar a lógica de validação do sistema subjacente. Essa validação do sistema pode dar suporte à sua própria lógica de validação ou substituí-la completamente. Se você não passar seu próprio validador de certificado ao solicitar uma conexão segura, a validação do sistema será usada automaticamente.

No Windows, a validação do sistema verificará se:

* Integridade da cadeia de certificados: os certificados formam uma cadeia consistente que termina em um certificado raiz confiável
* Validade do certificado: o certificado do servidor está dentro de seu período de validade e é emitido para autenticação de servidor
* Revogação: o certificado não foi revogado
* Corresponder ao nome: o nome do host do servidor corresponde a um dos nomes de host para o qual o certificado foi emitido

Implemente `ICertificateValidator` a interface da seguinte forma:

 * `PerformSystemValidation()` deverá retornar `true` se uma validação do sistema, conforme descrito acima, deve ser executada. Nesse caso, o resultado da validação do sistema é passado como uma entrada para o `ValidateCertificate()` método .
* `ValidateCertificate()` deve validar a cadeia de certificados e, `CertificateValidated()` em seguida, chamar no retorno de chamada passado com o resultado final da validação. Esse método aceita a cadeia de certificados, o nome do servidor com o quais a conexão está sendo estabelecida e se uma verificação de revogação deve ser forçada. Se a cadeia de certificados contiver vários certificados, o primeiro será o certificado de assunto.

>[!NOTE]
>Se o caso de uso exigir uma forma diferente de validação (consulte o caso de uso do certificado #1 acima), ignore totalmente a validação do sistema. Em vez disso, use qualquer API ou biblioteca que possa manipular certificados X.509 codificados em DER para decodificar a cadeia de certificados e executar as verificações necessárias para seu caso de uso.

## <a name="secure-connection-using-the-openxr-api"></a>Proteger a conexão usando a API do OpenXR

Ao usar a [API do OpenXR,](../native/openxr.md) toda a API relacionada à conexão segura está disponível como parte da extensão `XR_MSFT_holographic_remoting` openXR.

>[!IMPORTANT]
>Para saber mais sobre a API de extensão do [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) OpenXR de Remoção Holográfica, confira a especificação que pode ser encontrada no repositório [github de exemplos de Remo holográfica.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

Os principais elementos para conexão segura usando a `XR_MSFT_holographic_remoting` extensão OpenXR são os retornos de chamada a seguir.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, gera ou recupera o token de autenticação a ser enviado.
- `xrRemotingValidateServerCertificateCallbackMSFT`, valida a cadeia de certificados.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, valida o token de autenticação do cliente.
- `xrRemotingRequestServerCertificateCallbackMSFT`, fornecer o aplicativo de servidor com o certificado a ser usado.

Esses retornos de chamada podem ser fornecidos para o runtime do OpenXR de remoção por meio `xrRemotingSetSecureConnectionClientCallbacksMSFT` de e `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Além disso, a conexão segura precisa ser habilitada por meio do parâmetro secureConnection na estrutura ou na `XrRemotingConnectInfoMSFT` estrutura, dependendo de você `XrRemotingListenInfoMSFT` estar usando `xrRemotingConnectMSFT` ou `xrRemotingListenMSFT` .

Essa API é semelhante à API baseada em IDL descrita em [Implementando a segurança de remoção holográfica.](#implementing-holographic-remoting-security) No entanto, em vez de implementar interfaces, você deve fornecer implementações de retorno de chamada. Você pode encontrar um exemplo detalhado no aplicativo [de exemplo OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Consulte Também
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs Windows Mixed Reality holográficas](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de remoção holográfica](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)