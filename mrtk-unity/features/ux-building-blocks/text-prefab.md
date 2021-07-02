---
title: Pré-fab de texto
description: Visão geral do TextPrefab no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, TMP,
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175642"
---
# <a name="text-prefab"></a>Pré-fab de texto

Esses pré-requisitos são otimizados para a qualidade de renderização Windows Mixed Reality. Para obter mais informações, leia a diretriz [Texto no Unity](/windows/mixed-reality/text-in-unity) no Microsoft Windows Centro de Desenvolvimento.

## <a name="prefabs"></a>Pré-requisitos

### <a name="3dtextprefab"></a>3DTextPrefab

Pré-fab de Malha de Texto 3D (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros. (Leia as instruções abaixo)

### <a name="uitextprefab"></a>UITextPrefab

Pré-fab de Malha de Texto da Interface do Usuário (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros. (Leia as instruções abaixo)

## <a name="fonts"></a>Fontes

Fontes de código aberto (Ativos/MRTK/Core/StandardAssets/Fontes) incluídas no Mixed Reality Toolkit.

> [!IMPORTANT]
> O Pré-fab de Texto usa a fonte de código aberto 'Selawik'. Para usar o Pré-fab de Texto com uma fonte diferente, importe o arquivo de fonte e siga as instruções abaixo. O exemplo abaixo mostra como usar a fonte "Segoe UI" com o Pré-fab de Texto.

![Importando Segoe UI de fonte](../images/text-prefab/TextPrefabInstructions01.png)

1. Atribua textura de fonte ao material 3DTextSânciaUI.mat.

    ![Atribuindo textura de fonte](../images/text-prefab/TextPrefabInstructions02.png)

1. No material 3DTextSeroeUI.mat, selecione o sombreador Custom/3DTextShader.shader.

    ![Atribuindo sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. Atribua Segoe UI fonte e o material 3DTextSui aos componentes de texto nos pré-requisitos.

    ![Atribuindo o material e o arquivo de fonte](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Trabalhando com fontes no Unity

Ao adicionar um novo TextMesh 3D a uma cena no Unity, há dois problemas que são visualmente aparentes. Uma, a fonte aparece muito grande e duas, a fonte aparece muito desfoque. Também é interessante observar que o valor padrão tamanho da fonte está definido como zero no Inspetor. Substituir esse valor zero por 13 não mostrará nenhuma diferença no tamanho, pois 13 é, na verdade, o valor padrão.

O Unity presume que todos os novos elementos adicionados a uma cena são 1 Unidade do Unity em tamanho ou escala de transformação de 100%, o que se traduz em cerca de 1 medidor no HoloLens. No caso de fontes, a caixa delimitada para um TextMesh 3D entra, por padrão, com cerca de 1 medidor de altura.

### <a name="font-scale-and-font-sizes"></a>Escala de fonte e tamanhos de fonte

A maioria dos designers visuais usa Pontos para definir tamanhos de fonte no mundo real, bem como seus programas de design. Há cerca de 2835 (2.834,645666399962) pontos em 1 medidor. Com base na conversão do sistema de pontos em 1 medidor e no Tamanho da Fonte TextMesh padrão do Unity de 13, a matemática simples de 13 dividida por 2835 é igual a 0,0046 (0,0045861111116 para ser exato) fornece uma boa escala padrão para começar, embora alguns possam querer arredondá-los para 0,005.

De qualquer forma, dimensionar o objeto Text ou o contêiner para esses valores não permitirá apenas a conversão 1:1 de tamanhos de fonte de um programa de design, mas também fornece um padrão para manter a consistência em todo o aplicativo ou jogo.

### <a name="ui-text"></a>Texto da interface do usuário

Ao adicionar uma interface do usuário ou elemento Text baseado em tela a uma cena, a disparidade de tamanho ainda é maior. As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de Texto baseados na interface do usuário a 0,00046 (0,00045861111116 para ser exato) ou 0,0005 para o valor arredondado.

**Aviso de isenção de** responsabilidade: o valor padrão de qualquer fonte pode ser efetivado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base na fonte Arial padrão no Unity, bem como em outra fonte importada.

![Tamanho da fonte com fatores de dimensionamento](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSerikik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material para 3DTextPrefab com suporte para oclusão. Requer 3DTextShader.shader

![Material de fonte padrão versus material 3DTextSngoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Sombreador para 3DTextPrefab com suporte para oclusão.
