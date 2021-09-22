---
title: Modo de exibição Espectador
description: Visualize hologramas em um dispositivo externo para mostrar ou gravar uma experiência de realidade misturada em uma tela externa.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Modo de exibição Espectador, iPhone, iOS, iPad, OpenCV, câmera, ARKit, HoloLens, realidade misturada, MixedRealityToolkit, demonstração, gravar
ms.openlocfilehash: f30c745154056cda6b5ccf052efbbd0bb7f094ea
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779457"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Modo de exibição Espectador para o HoloLens e o HoloLens 2

> [!WARNING]
> A Microsoft vai preterir o exemplo Modo de exibição Espectador devido a incompatibilidades com a versão do pacote do SDK de Âncoras Espaciais do Azure em que o exemplo se baseia. Além disso, o exemplo poderá deixar de funcionar devido a outras alterações no ambiente do Unity à medida que os clientes mudarem para builds do LTS 2019 com suporte.
>
> Embora a Microsoft não esteja investindo recursos para resolver os problemas acima, existe a possibilidade de remover a funcionalidade de Âncoras Espaciais do Azure do exemplo e usar tecnologias como códigos QR para o alinhamento.   Se membros da comunidade enviarem PRs para resolver esses problemas, vamos revisá-los e aceitá-los por enquanto.

![Marker](images/SpecViewPhoneHero.jpg)

Quando você estiver usando um HoloLens, é fácil esquecer que uma pessoa que não o está usando possa ver as mesmas maravilhas que você. O modo de exibição Espectador permite que outras pessoas vejam o que um usuário do HoloLens vê em uma tela 2D. Também é uma abordagem rápida e acessível para a gravação de hologramas em HD com dispositivos móveis e a obtenção de gravações de ótima qualidade de hologramas com câmeras de vídeo.

## <a name="key-resources"></a>Principais recursos

* [**Modo de exibição Espectador no GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentação do Modo de exibição Espectador**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Amostras do Modo de exibição Espectador**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casos de uso

* Você pode gravar uma experiência de realidade misturada usando um dispositivo iPhone ou Android. Grave em full HD e aplique suavização a hologramas e sombra para ter uma forma econômica e rápida de capturar vídeo de hologramas.
* Transmita experiências de realidade misturada ao vivo para uma Apple TV diretamente no iPhone ou no iPad, sem retardos.
* Compartilhe a experiência com seus convidados: Permita que os usuários que não sejam do HoloLens experimentem os hologramas diretamente em seus respectivos telefones ou tablets.

## <a name="current-features"></a>Recursos atuais

* Sincronização espacial de hologramas, de modo que todos vejam os hologramas exatamente no mesmo local.
* Suporte para iOS (dispositivos habilitados para ARKit) e Android (dispositivos habilitados para ARCore).
Vários convidados do iOS.
Gravação de vídeo + hologramas + som ambiente + som de holograma.
Compartilhe a planilha para salvar um vídeo, enviá-lo por email ou compartilhá-lo com outros aplicativos de suporte.

![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)

A tabela a seguir mostra diferentes funcionalidades do Modo de exibição Espectador e seus recursos. Escolha a opção que melhor se adapte às suas necessidades de gravação de vídeo:

|      Funcionalidade                                | Móvel                  |                    Câmera de vídeo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualidade de HD                           |         Full HD         |        Filmagem de qualidade profissional (conforme determinado pela câmera de vídeo)      |
| Fácil movimento da câmera                 |            ✔            |                      ✔                      |
| Exibição de terceira pessoa                    |            ✔            |                      ✔                      |
| Pode ser transmitido para telas           |            ✔            |                      ✔                      |
| Portáteis                             |            ✔            |                                             |
| Sem fio                             |            ✔            |                                             |
| Hardware adicional necessário         |     Telefone Android, iPhone    | HoloLens + simulador + tripé + câmera de vídeo + computador + Unity |
| Investimento de hardware                  |           Baixo            |                     Alto                    |
| Plataforma cruzada                       |           Android, iOS   |                                             |
| Conteúdo sincronizado                 |            ✔            |                      ✔                      |
| Duração da instalação de runtime               |         Instantâneo          |                     Lento                    |
## <a name="see-also"></a>Confira também

* [Captura de realidade mista](/hololens/holographic-photos-and-videos) 
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)