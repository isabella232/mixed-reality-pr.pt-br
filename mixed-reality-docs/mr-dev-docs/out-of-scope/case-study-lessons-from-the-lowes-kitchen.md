---
title: Estudo de caso – Lições da cozinha do Lowe
description: A HoloLens de segurança deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto de HoloLens Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, cozinha, estudo de caso
ms.openlocfilehash: f2428a23e07d62156d38f43dfd5d6ddda20d57340d17908cf326ca9f37d223b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210386"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Estudo de caso – Lições da cozinha do Lowe

A HoloLens de segurança deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto de HoloLens Lowe. Veja abaixo um vídeo da lista de HoloLens lowe projetada demonstrada na nota de teclas do Ignite de 2016 da Satya.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Práticas recomendadas de HoloLens Lowe

Os dois vídeos abrangem as práticas recomendadas que foram derivadas do piloto de HoloLens Lowe que está em duas lojas do Lowe desde abril de 2016. Os principais tópicos são:
* Maximizar o desempenho de um dispositivo móvel
* Criar métodos de UX com um quadro holográfico completo (2ª conversa)
* Alinhamento de precisão (2ª conversa)
* Experiências holográficas compartilhadas (2ª palestra)
* Interagindo com clientes (2ª conversa)

## <a name="video-1"></a>Vídeo 1

**Maximizar o desempenho de um dispositivo** HoloLens dispositivo móvel é um dispositivo não conectado com todo o processamento que ocorre no dispositivo. Isso requer uma plataforma móvel e requer uma mentalidade semelhante à criação de aplicativos móveis. A Microsoft recomenda que seu aplicativo HoloLens mantenha 60FPS para fornecer uma experiência incrível para seus usuários. Ter FPS baixo pode resultar em hologramas instável.

Algumas das coisas mais importantes a se ver ao desenvolver no HoloLens é a otimização/acimação de ativos, usando sombreadores personalizados (disponíveis gratuitamente no [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)). Outra consideração importante é medir a taxa de quadros desde o início do projeto. Dependendo do projeto, a ordem de exibição de seus ativos também pode ser um grande colaborador
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Vídeo 2

**Criar métodos de UX com um quadro holográfico completo** É importante entender o posicionamento dos hologramas em um mundo físico. Com o Lowe, falamos sobre diferentes métodos de experiência do usuário que ajudam os usuários a experimentar hologramas de perto enquanto ainda estão vendo o ambiente maior dos hologramas.

**Alinhamento de precisão** Para o cenário do Lowe, foi fundamental para a experiência ter alinhamento de precisão dos hologramas para a cozinha física. Discutimos técnicas que ajudam a garantir uma experiência que desmente os usuários de que seu ambiente físico foi alterado.

**Experiências holográficas compartilhadas** Os casais são a principal maneira como a experiência do Lowe é consumida. Uma pessoa pode alterar a contrapeso e a outra pessoa verá as alterações. Chamamos isso de "experiências compartilhadas".

**Interagindo com clientes** Os designers de Lowe não estão usando um HoloLens, mas precisam ver o que os clientes estão vendo. Mostramos como capturar o que o cliente está vendo em um aplicativo UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
