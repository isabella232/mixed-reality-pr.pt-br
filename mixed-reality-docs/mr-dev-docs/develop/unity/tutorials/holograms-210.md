---
title: Entrada do HoloLens (1ª geração) 210 – Olhar
description: Siga este passo a passo de codificação usando o Unity, Visual Studio e HoloLens para aprender os detalhes dos conceitos de olhar.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze, HoloLens, Mixed Reality Academy, unity, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, Windows 10
ms.openlocfilehash: e0d761c6292502f381618f8efa1bed9d26f0e6fbac8dbdafa8085e0bb41676ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220962"
---
# <a name="hololens-1st-gen-input-210-gaze"></a>HoloLens (1ª geração) Entrada 210: Gaze

>[!IMPORTANT]
>Os tutoriais do Mixed Reality Academy foram projetados com HoloLens (1ª geração), Unity 2017 e Headsets Imersivos de Realidade Misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. Esses tutoriais não **_serão_** atualizados com os mais recentes toolsets ou interações que estão sendo usados para HoloLens 2 e podem não ser compatíveis com versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

[O](../../../design/gaze-and-commit.md) olhar é a primeira forma de entrada e revela a intenção e o reconhecimento do usuário. A Entrada 210 do MR (também Project Explorer) é uma análise profunda dos conceitos relacionados ao Windows Mixed Reality. Adicionaremos reconhecimento contextual ao cursor e hologramas, aproveitando ao máximo o que seu aplicativo sabe sobre o olhar do usuário.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Temos um astronauta amigável aqui para ajudá-lo a aprender conceitos de olhar. No [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), tínhamos um cursor simples que acabou de seguir seu olhar. Hoje, estamos movendo uma etapa além do cursor simples:

* Estamos tornando o cursor e nossos hologramas com o olhar atento: ambos mudarão com base no local em que o usuário está procurando ou onde o usuário *não está* procurando. Isso os torna cientes de contexto.
* Adicionaremos comentários ao cursor e hologramas para dar ao usuário mais contexto sobre o que está sendo direcionado. Os comentários podem ser áudio e visual.
* Mostraremos técnicas de direcionamento para ajudar os usuários a atingir destinos menores.
* Mostraremos como chamar a atenção do usuário para seus hologramas com um indicador direcional.
* Ensinaremos técnicas para levar seus hologramas com o usuário enquanto ela se move em seu mundo.

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos abaixo foram gravados usando uma versão mais antiga do Unity e o Toolkit. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão des date. Os vídeos permanecem incluídos para a posteridade e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada do MR 210: Focar</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um Windows 10 computador configurado com as ferramentas [corretas instaladas.](../../../develop/install-the-tools.md)
* Alguma capacidade básica de programação em C#.
* Você deve ter concluído o [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Um HoloLens configurado [para desenvolvimento.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
* Desarmá-los na área de trabalho ou em outro local fácil de alcançar.

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errata e observações

* No Visual Studio, "Apenas Meu Código" precisa ser desabilitado (desmarcado) em Ferramentas->Opções >Depuração para atingir pontos de interrupção em seu código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 – Instalação do Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento no HoloLens.
* Importar ativos e configurar a cena.
* Veja o astronautas na HoloLens.

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **Novo Projeto**.
3. Nomeia o **projeto ModelExplorer**.
4. Insira local como a **pasta Gaze** que você desarmou anteriormente.
5. Verifique se o projeto está definido como **3D**.
6. Clique **em Criar Project**.

### <a name="unity-settings-for-hololens"></a>Configurações do Unity para HoloLens

Precisamos permitir que o Unity saiba que o aplicativo [](../../../design/app-views.md) que estamos tentando exportar deve criar uma exibição imersiva em vez de uma exibição 2D. Fazemos isso adicionando HoloLens como um dispositivo de realidade virtual.

1. Vá para **Editar > Project Configurações > Player**.
2. No Painel **inspetor do** player Configurações, selecione o ícone **Windows Store.**
3. Expanda o grupo **Configurações de XR**.
4. Na seção **Renderização**, marque a caixa de seleção **Realidade Virtual Compatível** para adicionar uma nova lista de **SDKs de Realidade Virtual**.
5. Verifique se **Windows Mixed Reality** aparece na lista. Caso não, selecione **+** o botão na parte inferior da lista e escolha Windows **Holographic.**

Em seguida, precisamos definir nosso back-end de script como .NET.

1. Vá para **Editar > Project Configurações > Player** (você ainda pode ter isso na etapa anterior).
2. No Painel **inspetor do** player Configurações, selecione o ícone **Windows Store.**
3. Na seção **Outras configurações Configurações,** certifique-se de que **o Back-end de Script** está definido como **.NET**

Por fim, atualizaremos nossas configurações de qualidade para obter um desempenho rápido em HoloLens.

1. Vá para **Editar > Project Configurações > Qualidade.**
2. Clique na seta para baixo apontando para baixo **na linha** Padrão sob o ícone Windows Store.
3. Selecione **Muito Baixo para** **aplicativos Windows Store.**

### <a name="import-project-assets"></a>Importar ativos do projeto

1. Clique com o botão **direito do** mouse na pasta Ativos **no Project** painel.
2. Clique em **Importar Pacote > Pacote Personalizado**.
3. Navegue até os arquivos de projeto baixados e clique **em ModelExplorer.unitypackage**.
4. Clique em **Abrir**.
5. Depois que o pacote é carregado, clique no **botão Importar.**

### <a name="setup-the-scene"></a>Configurar a cena

1. Na Hierarquia, exclua a **Câmera Principal.**
2. Na pasta **HoloToolkit,** abra a **pasta Entrada** e, em seguida, abra a **pasta Prefabs.**
3. Arraste e solte o pré-fab **MixedRealityCameraParent** da pasta **Prefabs** para a **Hierarquia**.
4. Clique com o botão direito do mouse na Luz **Direcional** na Hierarquia e selecione **Excluir**.
5. Na pasta **Hologramas,** arraste e solte os seguintes ativos na raiz da **Hierarquia**:
    * **SempreMan**
    * **Luzes**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Inicie **o Modo** de ▶ para exibir o astronautas.
7. Clique **em Modo de** ▶ novamente para **Parar**.
8. Na pasta **Hologramas,** encontre o ativo **fitbox** e arraste-o para a raiz da **Hierarquia**.
9. Selecione o **Fitbox** no **painel Hierarquia.**
10. Arraste a **coleção Cadaman** da **Hierarquia para** a propriedade Coleção **de Hologramas** do Fitbox no **painel Inspetor.**

### <a name="save-the-project"></a>Salvar o projeto

1. Salve a nova cena: **Arquivo > Salvar Cena como**.
2. Clique **em Nova Pasta** e nomeia a pasta **Cenas**.
3. Nomeia o arquivo "**ModelExplorer**" e salve-o na **pasta Cenas.**

### <a name="build-the-project"></a>Compilar o projeto

1. No Unity, selecione **Arquivo > Build Configurações**.
2. Clique **em Adicionar Cenas Abertas** para adicionar a cena.
3. Selecione **Plataforma Windows Universal** na lista **Plataforma** e clique em Mudar **Plataforma**.
4. Se você estiver desenvolvendo especificamente para HoloLens, de definido **Dispositivo de destino** como **HoloLens**. Caso contrário, deixe-o **em Qualquer dispositivo**.
5. Verifique **se o Tipo** de Build está definido como **D3D** e se **o SDK** está definido como Mais recente instalado **(que** deve ser o SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Crie uma **nova pasta** chamada "Aplicativo".
8. Clique com um único clique **na pasta** Aplicativo.
9. Pressione **Selecionar Pasta**.

Quando o Unity for feito, uma Explorador de Arquivos será exibida.

1. Abra a **pasta Aplicativo.**
2. Abra a **Solução de Visual Studio ModelExplorer**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para **Versão** e do ARM para **x86.**
2. Clique na seta para baixo ao lado do botão Computador Local e selecione **Computador Remoto.**
3. Insira **seu HoloLens IP do dispositivo** e descriptografe o Modo de Autenticação como Universal **(Protocolo Não Criptografado).** Clique em **Selecionar**. Se você não sabe o endereço IP do dispositivo, procure Configurações > Rede & **Internet > Opções Avançadas**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você implanta em seu dispositivo, você precisará [emparelhá-lo com Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Quando o aplicativo for implantado, descarte o **Fitbox** com um **gesto de seleção**.

Se estiver implantando em um headset imersivo:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para Versão **e** de ARM para **x64**.
2. Certifique-se de que o destino de implantação está definido como **Computador Local.**
3. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
4. Quando o aplicativo for implantado, descarte o **Fitbox** e esvaia o gatilho em um controlador de movimento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2 – Cursor e comentários de destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Comportamento e design visual do cursor.
* Comentários sobre cursor baseado em olhar.
* Comentários do holograma baseado em olhar.

Vamos basear nosso trabalho em alguns princípios de design de cursor, ou seja:

* O cursor está sempre presente.
* Não deixe o cursor ficar muito pequeno ou grande.
* Evite obstruir o conteúdo.

### <a name="instructions"></a>Instruções

1. Na pasta **HoloToolkit\Input\Prefabs,** encontre o **ativo InputManager.**
2. Arraste e solte **o InputManager** na **Hierarquia**.
3. Na pasta **HoloToolkit\Input\Prefabs,** encontre o **ativo Cursor.**
4. Arraste e solte o **Cursor** na **Hierarquia**.
5. Selecione o **objeto InputManager** na **Hierarquia**.
6. Arraste o objeto Cursor **da** Hierarquia para o campo **Cursor** **SimpleSinglePointerSelector** do InputManager, na parte inferior do **Inspetor.** 

![Configuração simples do seletor de ponteiro único](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilar e implantar

1. Recomar o aplicativo do **Arquivo > Build Configurações**.
2. Abra a **pasta Aplicativo**.
3. Abra a **Solução de Visual Studio ModelExplorer**.
4. Clique **em Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
5. Observe como o cursor é desenhado e como ele altera a aparência se está tocando em um holograma.

### <a name="instructions"></a>Instruções

1. No painel **Hierarquia,** expanda o **objeto GEO_G** ->  -> **Back_Center** Hierarquia.
2. Clique duas vezes **em Interactible.cs** para abri-lo Visual Studio.
3. Descomente as linhas nos retornos de chamada **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** em **Interactible.cs.** Eles são chamados pelo InputManager do Toolkit Mixed Reality quando o foco (por foco ou apontando pelo controlador) entra e sai do colisor do GameObject específico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Usamos `EnableKeyword` e `DisableKeyword` acima. Para usá-los em seu próprio aplicativo com o sombreador Standard do Toolkit, você precisará seguir as diretrizes do Unity para acessar materiais por meio do [script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). Nesse caso, já incluímos as três [variantes](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) de material realçada necessárias na pasta Recursos (procure os três materiais com realçamento no nome).

### <a name="build-and-deploy"></a>Compilar e implantar

1. Como antes, crie o projeto e implante no HoloLens.
2. Observe o que acontece quando o olhar se destina a um objeto e quando não está.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3 – Técnicas de direcionamento

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Facilitar o direcionamento de hologramas.
* Estabilizar movimentos de cabeça natural.

### <a name="instructions"></a>Instruções

1. No painel **Hierarquia,** selecione o **objeto InputManager.**
2. No painel **Inspetor,** encontre o script **do Gaze Stabilizer.** Clique nele para abrir Visual Studio, se você quiser dar uma olhada.
    * Esse script itera sobre exemplos de dados do Raycast e ajuda a estabilizar o olhar do usuário para direcionamento de precisão.
3. No **Inspetor**, você pode editar o **valor Exemplos de Estabilidade Armazenados.** Esse valor representa o número de amostras em que o estabilizador itera para calcular o valor estabilizado.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4 – Indicador direcional

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Adicione um indicador direcional no cursor para ajudar a encontrar hologramas.

### <a name="instructions"></a>Instruções

Vamos usar o arquivo **DirectionIndicator.cs** que vai:

1. Mostre o indicador direcional se o usuário não estiver olhando para os hologramas.
2. Ocultar o indicador direcional se o usuário estiver olhando para os hologramas.
3. Atualize o indicador direcional para apontar para os hologramas.

Vamos começar.

1. Clique no **objeto Cadaman** no painel **Hierarquia** e clique **na seta** para expandi-lo.
2. No painel **Hierarquia,** selecione o **objeto DirectionalIndicator** em **CadaMan.**
3. No painel **Inspetor,** clique no **botão Adicionar** Componente.
4. No menu, digite na caixa de pesquisa Indicador **de Direção**. Selecione o resultado da pesquisa.
5. No painel **Hierarquia,** arraste e solte o **objeto Cursor** na **propriedade Cursor** no **Inspetor.**
6. No painel **Project,** na pasta **Hologramas,** arraste e solte o ativo **DirectionalIndicator** na propriedade **Indicador** Direcional no **Inspetor**.
7. Crie e implante o aplicativo.
8. Observe como o objeto indicador direcional ajuda você a encontrar o astronautas.

## <a name="chapter-5---billboarding"></a>Capítulo 5 – Minguação

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Use o uso de cartazes para que os hologramas sempre se deem a você.

Vamos usar o arquivo **Dem.cs** para manter um GameObject orientado, de forma que ele está sempre voltado para o usuário.

1. No painel **Hierarquia,** selecione o **objeto SempreMan.**
2. No painel **Inspetor,** clique no **botão Adicionar** Componente.
3. No menu, digite na caixa de pesquisa **Box .** Selecione o resultado da pesquisa.
4. No **Inspetor,** de acordo com **o Eixo Pivô** como **Y.**
5. Experimente! Crie e implante o aplicativo como antes.
6. Veja como o objeto Demão enfrenta você, independentemente de como você altera o ponto de vista.
7. Exclua o script **do SempreMan** por enquanto.

## <a name="chapter-6---tag-along"></a>Capítulo 6 – Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Use Tag-Along para que nossos hologramas nos sigam pela sala.

À medida que trabalharmos nesse problema, vamos ser guiados pelas seguintes restrições de design:

* O conteúdo sempre deve ser um relance.
* O conteúdo não deve estar no caminho.
* O conteúdo de bloqueio de cabeça é estranho.

A solução usada aqui é usar uma abordagem de "tag-along".

Um objeto de marcação nunca deixa totalmente a exibição do usuário. Você pode pensar no tag along como sendo um objeto anexado à cabeça do usuário por faixas de elástico. À medida que o usuário se move, o conteúdo ficará dentro de uma visão fácil deslizando até a borda da exibição sem sair completamente. Quando o usuário se volta para o objeto tag-along, ele fica mais totalmente em exibição.

Vamos usar o arquivo **SimpleTagalong.cs** que vai:

1. Determine se o Tag-Along objeto está dentro dos limites da câmera.
2. Se não estiver dentro da exibição, posicione o Tag-Along parcialmente dentro do frustum da exibição.
3. Caso contrário, posicione o Tag-Along a uma distância padrão do usuário.

Para fazer isso, primeiro precisamos alterar o script **Interactible.cs** para chamar **o TagalongAction.**

1. Edite **Interactible.cs** concluindo o exercício de codificação 6.a (sem comentários das linhas 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

O script **InteractibleAction.cs,** emparelhado com **Interactible.cs,** executa ações personalizadas quando você toca em hologramas. Nesse caso, vamos usar um especificamente para o tag-along.

* Na pasta **Scripts,** clique no ativo **TagalongAction.cs** para abrir no Visual Studio.
* Conclua o exercício de codificação ou altere-o para este:
  * Na parte superior da Hierarquia , **na** barra de pesquisa, digite **ChestButton_Center** e selecione o resultado.
  * No painel **Inspetor,** clique no **botão Adicionar** Componente.
  * No menu, digite na caixa de pesquisa **Ação Tagalong**. Selecione o resultado da pesquisa.
  * Na **Hologramas,** encontre o **ativo Tagalong.**
  * Selecione o **ChestButton_Center** na **Hierarquia**. Arraste e solte o **objeto TagAlong** do painel **Project** para **o Inspetor** na propriedade Object **To Tagalong.**
  * Arraste o **objeto Tagalong Action** do **Inspetor para** o campo Ação **Interacionável** no script **Interactible.**
* Clique duas vezes no script **TagalongAction** para abri-lo Visual Studio.

![Configuração do Interactible](images/holograms210-interactible.png)

Precisamos adicionar o seguinte:

* Adicione funcionalidade à função PerformAction no script TagalongAction (herdado de InteractibleAction).
* Adicione o controle ao objeto com o olhar e de definido o eixo pivô como XY.
* Em seguida, adicione Tag-Along simples ao objeto .

Aqui está nossa solução, de **TagalongAction.cs:**

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Experimente! Crie e implante o aplicativo.
* Observe como o conteúdo segue o centro do ponto de atenção, mas não continuamente e sem bloqueá-lo.