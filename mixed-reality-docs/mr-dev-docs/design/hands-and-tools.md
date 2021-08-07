---
title: Controladores de mãos e de movimento
description: Saiba mais sobre os modelos de interação dos controladores de movimentos e práticas, que podem remover o limite entre o virtual e o físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: realidade misturada, mãos, controladores de movimento, interação, design, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213680"
---
# <a name="hands-and-motion-controllers"></a>Controladores de mãos e de movimento

## <a name="scenarios"></a>Cenários

Depois de ler a [visão geral da interação](interaction-fundamentals.md), você escolhe o modelo de interação do controlador de mão e de movimento. Isso significa que você está desenvolvendo um aplicativo que exige que os usuários usem duas mãos para interagir com o mundo Holographic. Seu aplicativo vai atingir o objetivo de remover o limite entre virtual e físico.

Alguns cenários específicos podem ser:
* Fornecimento de telas virtuais 2D a profissionais da informação, com funcionalidades de UI (interface do usuário) para exibir e controlar o conteúdo
* Fornecendo tutoriais e guias de primeira linha aos funcionários para linhas de assembly de fábrica
* Desenvolvimento de ferramentas profissionais para auxiliar e orientar profissionais médicos  
* Uso de objetos virtuais 3D para decorar o mundo real ou criar um segundo mundo 
* Criação de serviços e jogos baseados em localização usando o mundo real como tela de fundo

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalidades de controladores de mãos e de movimento

:::row:::
    :::column:::
       [![Manipulação direta com as mãos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipulação direta com as mãos](direct-manipulation.md)<br>
       A modalidade aplica a potência das mãos que os usuários podem usar para tocar e manipular hologramas. Usando experiências diárias de vida e fornecendo capacidades visuais adequados, os usuários podem usar a mesma maneira de manipular objetos reais para interagir com os virtuais.
    :::column-end:::
    :::column:::
       [![Apontar e confirmar com as mãos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Apontar e confirmar com as mãos](point-and-commit.md)<br>
        Essa modalidade permite que os usuários interajam com os hologramas em uma distância. Ele permite que os usuários façam o melhor uso de arredores. Os usuários podem posicionar os hologramas em qualquer lugar e ainda acessá-los de qualquer distância. Os modelos mentales e gestos para controlar e manipular os hologramas 2D e 3D são altamente sincronizados com aqueles de manipulação direta.
    :::column-end:::
    :::column:::
       [![Controladores de movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Controladores de movimentos](motion-controllers.md)<br>
       Os controladores de movimento estendem os recursos físicos do usuário com interações precisas em um intervalo de distâncias durante o uso de uma ou de ambas as mãos. Esses acessórios de hardware fornecem atalhos para muitas interações usadas com frequência e fornecem comentários tactiles e com rodapé para várias ações. atualmente, os controladores de movimento só estão disponíveis para cenários de Windows Mixed Reality (WMR). 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Veja também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Mãos livres](hands-free.md)
