---
title: Como estabelecer uma conexão segura com o Holographic Remoting
description: Esta página explica como estabelecer uma conexão segura criptografada ao usar a comunicação remota do Holographic.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91674981"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Como estabelecer uma conexão segura com o Holographic Remoting

>[!IMPORTANT]
>Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Esta página explica como estabelecer uma conexão segura criptografada ao usar a comunicação remota do Holographic.

Ao transmitir conteúdo para o HoloLens 2 em uma rede insegura, como uma Wi-Fi aberta ou a Internet, é altamente recomendável usar uma conexão criptografada.

>[!IMPORTANT]
>Mesmo ao usar um WiFi local confiável usando uma conexão criptografada deve ser considerado.

Para poder usar uma conexão criptografada, você precisará implementar um [player personalizado](holographic-remoting-create-player.md) e um [aplicativo remoto personalizado](holographic-remoting-create-host.md).

A criptografia é obtida usando a implementação de TLS de plataformas subjacentes.

## <a name="basics-of-an-encrypted-connection"></a>Noções básicas de uma conexão criptografada

Os objetos a seguir precisam ser implementados para permitir uma troca de certificado.

>[!TIP]
>A implementação de interfaces do WinRT pode ser feita facilmente usando C++/WinRT. O capítulo [criar APIs com C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) descreve isso em detalhes.

>[!IMPORTANT]
>O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API relacionada a conexões seguras.

1) Um objeto de certificado, que precisa implementar a ```ICertificate``` interface.

    * Retornar o conteúdo binário do certificado pfx por meio do ```GetCertificatePfx``` método. O mesmo que o conteúdo binário de um arquivo. pfx.
    * Retornar o nome da entidade do certificado por meio de ```GetSubjectName``` .
    * Retornar a senha pfx por meio de ```GetPfxPassword``` . Retornar uma cadeia de caracteres vazia para um pfx desprotegido.

2) Um provedor de certificados que implementa a ```ICertificateProvider``` interface que fornece um certificado quando solicitado pelo ```GetCertificate``` método.

3) Um validador de certificado que implementa a ```ICertificateValidator``` interface. Sua tarefa é verificar os certificados de entrada.
    * O ```PerformSystemValidation``` método deve retornar ```true``` quando a plataforma subjacente deve validar a cadeia de certificados de entrada, ```false``` caso contrário.
    * ```ValidateCertificate``` é chamado pelo contexto do cliente para solicitar a validação de um certificado. Esse método aceita a cadeia de certificados (com o primeiro certificado sendo o certificado da entidade), o nome do servidor com o qual a conexão está sendo estabelecida e se uma verificação de revogação deve ser forçada. O resultado da validação do sistema será fornecido se a validação do sistema subjacente tiver sido solicitada. Para continuar o processamento ```CertificateValidated``` com o resultado apropriado ou ```Cancel``` para cancelar, a validação precisa ser chamada no passado ```ICertificateValidationCallback``` .

Além disso, para permitir a troca de um token seguro, os objetos a seguir precisam ser implementados.

1) Um provedor de autenticação que implementa a ```IAuthenticationProvider``` interface. Seu ```GetToken``` método é chamado pelo contexto do cliente para solicitar um token para autenticação de cliente. Para continuar a ```TokenReceived``` fornecer o token de autenticação e continuar o processo de conexão ou ```Cancel``` para cancelar, o processo precisa ser chamado no passado ```IAuthenticationProviderCallback``` .
2) Um receptor de autenticação que implementa a ```IAuthenticationReceiver``` interface. Sua tarefa é validar tokens de entrada.
    * O ```GetRealm``` método deve retornar o nome do realm de autenticação.
    * O ```ValidateToken``` método é chamado pelo contexto de rede do servidor para solicitar a validação de um token de autenticação de cliente. Para continuar a chamada ```ValidationCompleted``` para a conclusão do sinal da validação ou ```Cancel``` para rejeitar a conexão do cliente. A conexão do cliente será admitida ou rejeitada com base no resultado da validação passado para ```ValidationCompleted``` . 

Depois que esses objetos são implementados ```ListenSecure``` precisam ser chamados em vez de ```Listen``` e em vez de ```ConnectSecure``` ```Connect``` no contexto remoto e no contexto do Player, respectivamente. ```ListenSecure``` requer um provedor de certificado adicional e receptor de autenticação sobre o ```Listen``` . ```ConnectSecure``` requer um provedor de autenticação adicional e um validador de certificado ```Connect``` .

## <a name="see-also"></a>Consulte Também
* [Como criar um aplicativo remoto de comunicação remota holográfica](holographic-remoting-create-host.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
