---
title: Configuração do projeto Unreal
description: Saiba como configurar seu projeto com a versão mais recente do Unreal Engine e a Ferramenta de recursos de Realidade Misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realidade misturada, desenvolvimento, recursos, novo projeto, emulador, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade misturada do windows, headset de realidade virtual
ms.openlocfilehash: 546dcbac09600402b50408e016507b4d15fac22c58be8c1b3d68331dc5320252
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225394"
---
# <a name="setting-up-your-unreal-project"></a>Configuração do projeto Unreal

Recomendamos instalar o [Unreal Engine versão 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou posterior para aproveitar ao máximo o suporte interno ao HoloLens.

Acesse a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** e clique em **Opções**. Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.
![Opção de instalação do Unreal para HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importar Kit de Ferramentas de Realidade Misturada para Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

O MRTK (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.

Para a instalação, recomendamos a conclusão da [seção Introdução](unreal-development-overview.md#1-getting-started) do nosso [percurso de desenvolvimento do Unreal](unreal-development-overview.md) estruturado. Se você já está seguindo o percurso de desenvolvimento do Unreal, conclua o restante das etapas de instalação listadas abaixo e avance para os [tutoriais de Introdução do HoloLens 2](tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagem do logotipo do Unity](../images/MRTK-Unreal-Banner.png)<br>**Kit de Ferramentas de Realidade Misturada – Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se você não quiser usar o MRTK para o Unreal, precisará criar o script de todas as interações e todos os comportamentos por conta própria.