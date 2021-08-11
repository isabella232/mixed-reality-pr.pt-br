---
title: Entrada do HoloLens (1ª geração) 211 – Gestos
description: siga este passo a passo de codificação usando o Unity, Visual Studio e HoloLens para aprender os detalhes dos conceitos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academia, tutorial, gesto, HoloLens, reality academy, unity, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual, Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206412"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (1ª gen) entrada 211: gesto

>[!IMPORTANT]
>os tutoriais misturados do academia de realidade foram projetados com a HoloLens (1ª gen), o Unity 2017 e o headset de imersão de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes ou as interações usadas para o HoloLens 2 e podem não ser compatíveis com as versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

Os [gestos](../../../design/gaze-and-commit.md#composite-gestures) desativam a intenção do usuário. Com gestos, os usuários podem interagir com os hologramas. Neste curso, veremos como acompanhar as mãos do usuário, responder a entrada do usuário e fornecer comentários para o usuário com base no estado e no local.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

No [Sr basics 101](../../../develop/unity/tutorials/holograms-101.md), usamos um gesto simples de toque de ar para interagir com nossos hologramas. Agora, vamos passar além do gesto de toque do ar e explorar novos conceitos para:

* Detectar quando a mão do usuário está sendo acompanhada e fornecer comentários ao usuário.
* Use um gesto de navegação para girar nossos hologramas.
* Forneça comentários quando a mão do usuário estiver prestes a sair da exibição.
* Use eventos de manipulação para permitir que os usuários movam os hologramas com suas mãos.

Neste curso, Vamos revisitar o **Explorador de modelos** de projeto do Unity, que criamos no [Sr Input 210](holograms-210.md). Nosso amigo Astronaut está voltado a nos ajudar em nossa exploração desses novos conceitos de gesto.

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e a realidade misturada Toolkit. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada do MR 211: Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* um computador Windows 10 configurado com as ferramentas corretas [instaladas](../../../develop/install-the-tools.md).
* Uma capacidade básica de programação em C#.
* Você deve ter concluído o [Sr noções básicas 101](../../../develop/unity/tutorials/holograms-101.md).
* Você deve ter concluído o [Sr Input 210](holograms-210.md).
* um dispositivo HoloLens [configurado para desenvolvimento](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível em github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errata e observações

* "habilitar Apenas Meu Código" precisa ser desabilitado (*desmarcado*) em Visual Studio em ferramentas->opções->depuração para acessar os pontos de interrupção no código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0-configuração do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **Abrir**.
3. Navegue até a pasta de **gestos** que você cancelou anteriormente.
4. Localize e selecione a pasta **iniciando** o / **Gerenciador de modelos** .
5. Clique no botão **Selecionar pasta** .
6. no painel de **Project** , expanda a pasta **cenas** .
7. Clique duas vezes em cena **ModelExplorer** para carregá-la no Unity.

### <a name="building"></a>Construção

1. no Unity, selecione **arquivo > Build Configurações**.
2. Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **Adicionar cenas abertas** para adicionar a cena.
3. se você estiver desenvolvendo especificamente para HoloLens, defina o **dispositivo de destino** como **HoloLens**. Caso contrário, deixe em **qualquer dispositivo**.
4. Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).
5. Clique em **Compilar**.
6. Crie uma **nova pasta** chamada "app".
7. Clique uma vez na pasta do **aplicativo** .
8. Pressione **Selecionar pasta** e o Unity começará a compilar o projeto para Visual Studio.

Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.

1. Abra a pasta do **aplicativo** .
2. abra a **solução de Visual Studio ModelExplorer**.

Se estiver implantando no HoloLens:

1. usando a barra de ferramentas superior no Visual Studio, altere o destino de Debug para **Release** e de ARM para **x86**.
2. Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.
3. insira **o endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**. Clique em **Selecionar**. se você não souber o endereço IP do dispositivo, procure **Configurações > rede & opções avançadas de Internet >**.
4. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.

Se estiver implantando em um headset de imersão:

1. usando a barra de ferramentas superior no Visual Studio, altere o destino de Debug para **Release** e de ARM para **x64**.
2. Verifique se o destino de implantação está definido como **computador local**.
3. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
4. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.

>[!NOTE]
>você pode observar alguns erros vermelhos no painel Visual Studio erros. É seguro ignorá-los. Alterne para o painel saída para exibir o andamento real da compilação. Os erros no painel de saída exigirão que você faça uma correção (geralmente elas são causadas por um erro em um script).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1-comentários detectados

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Assine os eventos de acompanhamento do Hand.
* Use comentários do cursor para mostrar os usuários quando uma mão estiver sendo controlada.

>[!NOTE]
>no HoloLens 2, as mãos detectadas são acionadas sempre que as mãos estão visíveis (não apenas quando um dedo está apontando para cima).

### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda o objeto **InputManager** .
* Procure e selecione o objeto **GesturesInput** .

O script **InteractionInputSource. cs** executa estas etapas:

1. Assina os eventos InteractionSourceDetected e InteractionSourceLost.
2. Define o estado HandDetected.
3. Cancela a assinatura dos eventos InteractionSourceDetected e InteractionSourceLost.

Em seguida, atualizaremos nosso cursor da [entrada do sr 210](holograms-210.md) em um que mostre os comentários, dependendo das ações do usuário.

1. No painel **hierarquia** , selecione o objeto de **cursor** e exclua-o.
2. no painel de **Project** , procure **CursorWithFeedback** e arraste-o para o painel **hierarquia** .
3. Clique em **InputManager** no painel **hierarquia** e arraste o objeto **CursorWithFeedback** da **hierarquia** para o campo de **cursor** do **SimpleSinglePointerSelector** do InputManager, na parte inferior do **Inspetor**.
4. Clique em **CursorWithFeedback** na **Hierarquia**.
5. No painel **Inspetor,** expanda **Dados de Estado do Cursor** no script do **Cursor de** Objeto.

Os **Dados de Estado do Cursor** funcionam da mesma forma:

* Qualquer **estado** de Observação significa que nenhuma mão é detectada e o usuário está simplesmente observando.
* Qualquer **estado** de Interação significa que uma mão ou controlador é detectado.
* Qualquer **estado de** foco significa que o usuário está olhando para um holograma.

### <a name="build-and-deploy"></a>Compilar e implantar

* No Unity, use **File > Build Configurações** recomar o aplicativo.
* Abra a **pasta Aplicativo.**
* Se ainda não estiver aberto, abra a **solução ModelExplorer Visual Studio**.
  * (Se você já tiver criado/implantado esse projeto no Visual Studio durante a configuração, poderá abrir essa instância do VS e clicar em 'Recarregar Tudo' quando solicitado).
* No Visual Studio, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
* Depois que o aplicativo é implantado no HoloLens, descarte a caixa de ajuste usando o gesto de toque no ar.
* Mova a mão para a exibição e aponte o dedo indicador para o céu para iniciar o acompanhamento da mão.
* Mova a mão para a esquerda, para a direita, para cima e para baixo.
* Observe como o cursor muda quando sua mão é detectada e, em seguida, perdida da exibição.
* Se você estiver em um headset imersivo, será preciso conectar e desconectar o controlador. Esse feedback se torna menos interessante em um dispositivo imersivo, pois um controlador conectado sempre estará "disponível".

## <a name="chapter-2---navigation"></a>Capítulo 2 – Navegação

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use eventos de gesto de navegação para girar o astronautas.

### <a name="instructions"></a>Instruções

Para usar gestos de navegação em nosso aplicativo, vamos editar **GestureAction.cs** para girar objetos quando o gesto de navegação ocorrer. Além disso, adicionaremos comentários ao cursor para exibir quando a navegação estiver disponível.

1. No painel **Hierarquia,** expanda **CursorWithFeedback**.
2. Na pasta **Hologramas,** encontre o ativo **ScrollFeedback.**
3. Arraste e solte o **pré-fab ScrollFeedback** **no CursorWithFeedback** GameObject na **Hierarquia**.
4. Clique em **CursorWithFeedback.**
5. No painel **Inspetor,** clique no **botão Adicionar** Componente.
6. No menu, digite na caixa de pesquisa **CursorFeedback**. Selecione o resultado da pesquisa.
7. Arraste e solte o **objeto ScrollFeedback** da Hierarquia para a propriedade Scroll **Detected Game Object** no componente Comentários do **Cursor** no **Inspetor**. 
8. No painel **Hierarquia,** selecione o **objeto SempreMan.**
9. No painel **Inspetor,** clique no **botão Adicionar** Componente.
10. No menu, digite na caixa de pesquisa **Ação de Gesto**. Selecione o resultado da pesquisa.

Em seguida, **abra GestureAction.cs** Visual Studio. No exercício de codificação 2.c, edite o script para fazer o seguinte:

1. **Gire o objeto Sempre** que um gesto de navegação for executado.
2. Calcule **o rotationFactor** para controlar a quantidade de rotação aplicada ao objeto .
3. **Gire o objeto** em torno do eixo y quando o usuário mover a mão para a esquerda ou para a direita.

Conclua os exercícios de codificação 2.c no script ou substitua o código pela solução concluída abaixo:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Você observará que os outros eventos de navegação já estão preenchidos com algumas informações. Efetuar push do GameObject para a pilha modal do InputSystem do Toolkit, para que o usuário não tenha que manter o foco no Astronautas depois que a rotação tiver começado. Correspondentemente, podemos tirar o GameObject da pilha depois que o gesto for concluído.

### <a name="build-and-deploy"></a>Compilar e implantar

1. Recomposicionar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para ser executado no HoloLens.
2. Seta para o astronautas, duas setas devem aparecer em qualquer lado do cursor. Esse novo visual indica que o astronauta pode ser girado.
3. Coloque a mão na posição pronta (dedo indicador apontado para o céu) para que o HoloLens comece a rastrear sua mão.
4. Para girar o astronautas, baixe o dedo indicador para uma posição de pinçar e mova a mão para a esquerda ou para a direita para disparar o gesto NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3 – Diretrizes da mão

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use **a pontuação de diretrizes de** mão para ajudar a prever quando o acompanhamento de mão será perdido.
* Forneça **comentários sobre o cursor** para mostrar quando a mão do usuário se aproximar da borda de exibição da câmera.

### <a name="instructions"></a>Instruções

1. No painel **Hierarquia,** selecione o **objeto CursorWithFeedback.**
2. No painel **Inspetor,** clique no **botão Adicionar** Componente.
3. No menu, digite na caixa de pesquisa **Diretrizes de Mão**. Selecione o resultado da pesquisa.
4. No painel **Project** de **Hologramas,** encontre o ativo **HandGuidanceFeedback.**
5. Arraste e solte o **ativo HandGuidanceFeedback** na propriedade Indicador de Diretriz **de** Mão no **painel Inspetor.**

### <a name="build-and-deploy"></a>Compilar e implantar

* Recomposicionar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo no HoloLens.
* Leve sua mão para a exibição e aumente o dedo indicador para ser rastreado.
* Comece a girar o astronautas com o gesto de navegação (pinçar o dedo indicador e o polegar juntos).
* Mova a mão para a esquerda, para a direita, para cima e para baixo.
* Conforme sua mão se aproxima da borda do quadro de gestos, uma seta deve aparecer ao lado do cursor para avisar que o acompanhamento da mão será perdido. A seta indica qual direção mover a mão para evitar que o acompanhamento seja perdido.

## <a name="chapter-4---manipulation"></a>Capítulo 4 – Manipulação

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Use eventos de manipulação para mover o astronautas com as mãos.
* Forneça comentários sobre o cursor para que o usuário saiba quando a Manipulação pode ser usada.

### <a name="instructions"></a>Instruções

GestureManager.cs e AstronautManager.cs nos permitirão fazer o seguinte:

1. Use a palavra-chave de fala "**Move Astronaut**" para **habilitar** gestos de manipulação e "**Girar Astronautas**" para desabilitá-los.
2. Alternar para responder ao **Reconhecedor de Gestos de Manipulação**.

Vamos começar.

1. No painel **Hierarquia,** crie um novo GameObject vazio. Nomeia-o como "**AstronautManager**".
2. No painel **Inspetor,** clique no **botão Adicionar** Componente.
3. No menu, digite na caixa de pesquisa **Gerenciador de Astronautas**. Selecione o resultado da pesquisa.
4. No painel **Inspetor,** clique no **botão Adicionar** Componente.
5. No menu, digite na caixa de pesquisa Origem **de Entrada de Fala**. Selecione o resultado da pesquisa.

Agora, adicionaremos os comandos de fala necessários para controlar o estado de interação do astronautas.

1. Expanda **a seção Palavras-chave** no **Inspetor**.
2. Clique no **+** no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **Move Astronaut.** Sinta-se à vontade para adicionar um Atalho de Tecla, se desejado.
4. Clique no **+** no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **Girar Astronautas.** Sinta-se à vontade para adicionar um Atalho de Tecla, se desejado.
6. O código do manipulador correspondente pode ser encontrado em **GestureAction.cs**, no manipulador **ISpeechHandler.OnSpeechKeywordRecognized.**

![Como configurar a Fonte de Entrada de Fala para o capítulo 4](images/holograms211-speech.png)

Em seguida, configuraremos os comentários de manipulação no cursor.

1. Na pasta **Project** painel **Hologramas,** encontre o ativo **PathingFeedback.**
2. Arraste e solte o **pré-fab PathingFeedback** **no objeto CursorWithFeedback** na **Hierarquia**.
3. No painel **Hierarquia,** clique em **CursorWithFeedback**.
4. Arraste e solte o **objeto PathingFeedback** da Hierarquia para a propriedade **Pathing Detected Game Object** no componente Comentários do **Cursor** no **Inspetor**. 

Agora, precisamos adicionar código a **GestureAction.cs** para habilitar o seguinte:

1. Adicione código à **função IManipulationHandler.OnManipulationUpdated,** que move o astronautas quando um gesto **de** Manipulação é detectado.
2. Calcule **o vetor de** movimento para determinar para onde o astronautas deve ser movido com base na posição da mão.
3. **Mova** o astronautas para a nova posição.

Conclua o exercício de codificação 4.a **em GestureAction.cs** ou use nossa solução completa abaixo:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilar e implantar

* Recomando no Unity e, em seguida, crie e implante do Visual Studio para executar o aplicativo no HoloLens.
* Mova a mão para a frente do HoloLens e aumente o dedo indicador para que ele possa ser rastreado.
* Concentre o cursor sobre o astronautas.
* Diga "Mover o Astronautas" para mover o astronautas com um gesto de Manipulação.
* Quatro setas devem aparecer ao redor do cursor para indicar que o programa agora responderá aos eventos de Manipulação.
* Reduza o dedo indicador para baixo até o polegar e mantenha-os pinçados juntos.
* À medida que você mover a mão, o astronautas também se moverá (isso é Manipulação).
* Aumente o dedo indicador para parar de manipular o astronautas.
* Observação: se você não disser "Mover Astronautas" antes de mover a mão, o gesto de navegação será usado em vez disso.
* Diga "Girar Astronautas" para retornar ao estado rotativo.

## <a name="chapter-5---model-expansion"></a>Capítulo 5 – Expansão do modelo

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda o modelo de Astronautas em várias partes menores com as qual o usuário pode interagir.
* Mova cada peça individualmente usando gestos de Navegação e Manipulação.

### <a name="instructions"></a>Instruções

Nesta seção, realizaremos as seguintes tarefas:

1. Adicione uma nova palavra-chave "**Expand Model**" para expandir o modelo de astronautas.
2. Adicione uma nova palavra-chave "**Redefinir Modelo**" para retornar o modelo ao formulário original.

Faremos isso adicionando mais duas palavras-chave à Fonte de Entrada de Fala do capítulo anterior. Também demonstraremos outra maneira de lidar com eventos de reconhecimento.

1. Clique novamente em **AstronautManager** no **Inspetor e** expanda a seção **Palavras-chave** no **Inspetor**.
2. Clique no **+** no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **Expandir Modelo.** Sinta-se à vontade para adicionar um Atalho de Tecla, se desejado.
4. Clique no **+** no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **Redefinir Modelo**. Sinta-se à vontade para adicionar um Atalho de Tecla, se desejado.
6. No painel **Inspetor,** clique no **botão Adicionar** Componente.
7. No menu, digite na caixa de pesquisa Manipulador **de Entrada de Fala**. Selecione o resultado da pesquisa.
8. Check **Is Global Listener**, já que queremos que esses comandos funcionem independentemente do GameObject que estamos concentrando.
9. Clique no **+** botão e selecione Expandir Modelo **na** lista suspenso Palavra-chave.
10. Clique no **+** em Resposta e arraste o **AstronautManager** da **Hierarquia** para o campo **Nenhum (Objeto).**
11. Agora, clique no menu **suspenso Sem Função,** selecione **AstronautManager** e **ExpandModelCommand.**
12. Clique no botão do Manipulador de Entrada de **+** Fala e selecione **Redefinir Modelo** na lista suspenso Palavra-chave.
13. Clique no **+** em Resposta e arraste o **AstronautManager** da **Hierarquia** para o campo **Nenhum (Objeto).**
14. Agora, clique no menu **suspenso Sem Função,** selecione **AstronautManager** e, em **seguida, ResetModelCommand**.

![Como configurar a origem e o manipulador de entrada de fala para o capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilar e implantar

* Experimente! Crie e implante o aplicativo no HoloLens.
* Diga **Expanda Modelo** para ver o modelo de astronautas expandido.
* Use **Navegação para** girar partes individuais do fato de astronautas.
* Diga **Mover o Astronautas** e, em seguida, use a Manipulação para mover partes individuais do fato de astronautas. 
* Digamos **girar o Astronautas** para girar as partes novamente.
* Diga **Redefinir Modelo** para retornar o astronautas para sua forma original.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu a **Entrada do MR 211: Gesto**.

* Você sabe como detectar e responder a eventos de controle de mão, navegação e manipulação.
* Você entende a diferença entre gestos de navegação e manipulação.
* Você sabe como alterar o cursor para fornecer comentários visuais para quando uma mão é detectada, quando uma mão está prestes a ser perdida e para quando um objeto dá suporte a interações diferentes (Navegação versus Manipulação).