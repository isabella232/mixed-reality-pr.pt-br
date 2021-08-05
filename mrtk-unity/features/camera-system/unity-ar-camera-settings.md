---
title: Configurações da câmera de RA do Unity
description: Documentação para usar a câmera AR no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, câmera AR,
ms.openlocfilehash: a2d145823557b473bd7d34170b283e782151c24277b8f16586516ffe78f8e735
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210056"
---
# <a name="unity-ar-camera-settings-provider"></a>Provedor de configurações da câmera do Unity AR

O provedor de configurações da câmera do Unity AR é um componente MRTK experimental que permite que aplicativos de realidade misturada sejam executados em dispositivos Android e iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Opções do provedor de configurações da câmera do Unity AR

![Configuração de configurações da câmera do Unity AR](../images/camera-system/UnityArSettingsConfiguration.png)

Para obter um guia sobre como adicionar o provedor à sua cena: [como configurar o MRTK para IOS e Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Configurações de controle

O provedor de configurações da câmera do Unity AR permite opções de configuração para o modo como o rastreamento é executado. Essas configurações são específicas para a implementação do provedor de configurações da câmera do Unity AR.

**Origem da pose**

A origem da pose define os tipos disponíveis de poses de acompanhamento da realidade aumentada. Em geral, esses valores são mapeados para um componente do dispositivo no qual o aplicativo está sendo executado.

As opções disponíveis são descritas na tabela a seguir.

| Opção | Descrição |
| --- | --- |
| Centro | O olho central de um dispositivo montado na cabeça. |
| Câmera colorida | A câmera colorida de um dispositivo móvel. |
| Head | O olho de um dispositivo montado na cabeça, geralmente um pouco acima do olho central. |
| Olho à esquerda | O olho à esquerda de um dispositivo montado no cabeçalho. |
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
| Atualizar e antes do processamento | Durante a fase de atualização e logo antes da renderização. |

O valor padrão para o tipo de rastreamento é **Update e antes de render**, para habilitar a latência de rastreamento mais baixa.

## <a name="see-also"></a>Confira também

- [Visão geral do sistema de câmera](camera-system-overview.md)
- [criando um provedor de Configurações de câmera](create-settings-provider.md)
