---
title: TextPrefab
description: Visão geral do TextPrefab no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489286"
---
# <a name="text-prefab"></a>Pré-fab de texto

Esses pré-requisitos são otimizados para a qualidade de renderização Windows Mixed Reality. Para obter mais informações, leia a diretriz [Texto no Unity](/windows/mixed-reality/text-in-unity) no Microsoft Centro de Desenvolvimento do Windows.

## <a name="prefabs"></a>Pré-requisitos

### <a name="3dtextprefab"></a>3DTextPrefab

Pré-fab de Malha de Texto 3D (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros. (Leia as instruções abaixo)

### <a name="uitextprefab"></a>UITextPrefab

Pré-fab de Malha de Texto da Interface do Usuário (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros. (Leia as instruções abaixo)

## <a name="fonts"></a>Fontes

Fontes de código aberto (Ativos/MRTK/Core/StandardAssets/Fontes) incluídas no Kit de Ferramentas de Realidade Misturada.

> [!IMPORTANT]
> O Pré-fab de Texto usa a fonte de código aberto 'Selawik'. Para usar o Pré-fab de Texto com uma fonte diferente, importe o arquivo de fonte e siga as instruções abaixo. O exemplo abaixo mostra como usar a fonte "Segoe UI" com o Pré-fab de Texto.

![Importando Segoe UI de fonte](../images/text-prefab/TextPrefabInstructions01.png)

1. Atribua textura de fonte ao material 3DTextSânciaUI.mat.

    ![Atribuindo textura de fonte](../images/text-prefab/TextPrefabInstructions02.png)

1. No material 3DTextSegoeUI. passe-partout, selecione o sombreador personalizado/3DTextShader. sombreador.

    ![Atribuindo sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. Atribua Segoe UI fonte e material 3DTextSegoeUI aos componentes de texto no pré-fabricados.

    ![Atribuindo material e arquivo de fonte](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Trabalhando com fontes no Unity

Ao adicionar uma nova textmesh 3D a uma cena no Unity, há dois problemas que são visualmente aparentes. Uma delas, a fonte aparece muito grande e duas, a fonte aparece muito borrada. Também é interessante observar que o valor do tamanho da fonte padrão é definido como zero no Inspetor. Substituir esse valor zero por 13 não mostrará nenhuma diferença no tamanho, porque 13 é, na verdade, o valor padrão.

O Unity pressupõe que todos os novos elementos adicionados a uma cena tenham uma unidade Unity de tamanho ou uma escala de transformação de 100%, o que traduz em cerca de 1 metro no HoloLens. No caso de fontes, a caixa delimitadora de uma telemalha 3D entra, por padrão, em cerca de 1 metro de altura.

### <a name="font-scale-and-font-sizes"></a>Escala de fonte e tamanhos de fonte

A maioria dos designers visuais usa pontos para definir tamanhos de fonte no mundo real, bem como seus programas de design. Há cerca de 2835 pontos (2, 834.645666399962) em 1 metro. Com base na conversão do sistema de ponto para 1 medidor e tamanho de fonte de textmesh padrão de Unity de 13, a matemática simples de 13 dividido por 2835 é igual a 0, 46 (0.004586111116 a ser exato) fornece uma boa escala padrão para começar, embora alguns possam desejar arredondar para 0, 5.

De qualquer forma, dimensionar o objeto de texto ou o contêiner para esses valores não só permitirá a conversão 1:1 de tamanhos de fonte de um programa de design, mas também fornecerá um padrão para manter a consistência em todo o aplicativo ou jogo.

### <a name="ui-text"></a>Texto da interface do usuário

Ao adicionar um elemento de texto baseado na interface do usuário ou tela a uma cena, o tamanho da disparidade ainda é maior. As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de texto baseados na interface do usuário a 0, 46 (0.0004586111116 para ser exato) ou 0, 5 para o valor arredondado.

**Isenção de responsabilidade**: o valor padrão de qualquer fonte pode ser afetado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base na fonte Arial padrão no Unity, bem como em outra fonte importada.

![Tamanho da fonte com fatores de dimensionamento](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSerikik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material para 3DTextPrefab com suporte para oclusão. Requer 3DTextShader.shader

![Material de fonte padrão versus material 3DTextSngoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Sombreador para 3DTextPrefab com suporte para oclusão.