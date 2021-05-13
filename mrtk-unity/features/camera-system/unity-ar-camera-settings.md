---
title: UnityArCameraSettings
description: Documentação para usar a câmera AR no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera AR,
ms.openlocfilehash: 15aacae4cb543a3a94660ef1ab057ad0febcb715
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850412"
---
# <a name="unity-ar-camera-settings-provider"></a>Provedor de configurações de câmera AR do Unity

O provedor de configurações de câmera AR do Unity é um componente experimental do MRTK que permite que aplicativos de realidade misturada executem em dispositivos Android e iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Opções do provedor de configurações de câmera ar do Unity

![Configuração de configurações da câmera AR do Unity](../images/camera-system/UnityArSettingsConfiguration.png)

Para ver um guia sobre como adicionar o provedor à sua cena: [Como configurar o MRTK para iOS e Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Configurações de acompanhamento

O provedor de configurações de câmera AR do Unity permite opções de configuração para como o acompanhamento é executado. Essas configurações são específicas para a implementação do provedor de configurações de câmera ar do Unity.

**Origem de pose**

A origem de pose define os tipos disponíveis de poses de acompanhamento de realidade aumentada. Em geral, esses valores são mapeados para um componente do dispositivo no qual o aplicativo está em execução.

As opções disponíveis são descritas na tabela a seguir.

| Opção | Descrição |
| --- | --- |
| Centro | O olho central de um dispositivo montado na cabeça. |
| Câmera de cores | A câmera de cores de um dispositivo móvel. |
| Head | O olho da cabeça de um dispositivo montado na cabeça, geralmente um pouco acima do olho central. |
| Olho esquerdo | O olho à esquerda de um dispositivo montado no cabeçalho. |
| Pose esquerda | O controlador esquerdo é composto. |
| Olho à direita | O olho certo de um dispositivo montado na cabeça. |
| Pose direita | A pose do controlador à direita. |

O valor padrão da origem da pose é a **câmera colorida**, para habilitar uma exibição transparente em dispositivos móveis, como um telefone ou Tablet.

**Tipo de rastreamento**

O tipo de rastreamento define as partes da pose que serão usadas para acompanhamento.

As opções disponíveis são descritas na tabela a seguir.

| Opção | Descrição |
| --- | --- |
| Posição | A posição do dispositivo. |
| Rotação | A rotação do dispositivo. |
| Rotação e posição | A posição e a rotação do dispositivo. |

O valor padrão para o tipo de rastreamento é **rotação e posição**, para habilitar a experiência de controle mais rica.

**Tipo de atualização**

O tipo de atualização define em quais pontos, durante o processamento de quadros, os dados de pose serão amostrados.

As opções disponíveis são descritas na tabela a seguir.

| Opção | Descrição |
| --- | --- |
| Antes da renderização | Logo antes da renderização. |
| Atualizar | Durante a fase de atualização do quadro. |
| Atualizar e antes de renderizar | Durante a fase de atualização e logo antes da renderização. |

O valor padrão para o tipo de rastreamento **é Update And Before Render**, para habilitar a menor latência de acompanhamento.

## <a name="see-also"></a>Confira também

- [Visão geral do sistema de câmera](camera-system-overview.md)
- [Criando um provedor de configurações de câmera](create-settings-provider.md)
