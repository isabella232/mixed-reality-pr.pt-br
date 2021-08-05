---
title: Entrada do MR 213
description: Siga este tutorial de codificação usando o Unity, Visual Studio headsets imersivos e imersivos para aprender os detalhes dos controladores de movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, motion controller, academy, tutorial
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210086"
---
# <a name="mr-input-213-motion-controllers"></a>Entrada do MR 213: controladores de movimentos

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](../develop/unity/tutorials/mr-learning-base-01.md) foi postada para o HoloLens 2.

Controladores de movimento no mundo da realidade misturada adicionam outro nível de interatividade. Com [os controladores](../design/motion-controllers.md)de movimento, podemos interagir diretamente com objetos de maneira mais natural, semelhante às nossas interações físicas na vida real, aumentando a imersão e a satisfação em sua experiência de aplicativo.

Na Entrada 213 do MR, exploraremos os eventos de entrada do controlador de movimento criando uma experiência de pintura espacial simples. Com esse aplicativo, os usuários podem pintar em espaço tridimensional com vários tipos de pincéis e cores.

## <a name="topics-covered-in-this-tutorial"></a>Tópicos abordados neste tutorial

|![MixedReality213 Topic1](images/mr213-topic1.png)|![Tópico MixedReality2132](images/mr213-topic2.png)|![Tópico MixedReality2133](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualização do controlador**|**Eventos de entrada do controlador**|**Controlador personalizado e interface do usuário**|
|Saiba como renderizar modelos de controlador de movimento no modo de jogo e no runtime do Unity.|Entenda os diferentes tipos de eventos de botão e seus aplicativos.|Saiba como sobrepor elementos de interface do usuário sobre o controlador ou personalizá-lo totalmente.|

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada do MR 213: controladores de movimentos</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

Consulte a lista de verificação de instalação para headsets imersivos [nesta página](../develop/install-the-tools.md).

* Este tutorial requer [o Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Arquivos de projeto

* [Baixe os arquivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) exigidos pelo projeto e extraia os arquivos para a Área de Trabalho.

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Configuração do Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Otimizar o Unity para Windows Mixed Reality desenvolvimento
* Configuração Câmera de Realidade Misturada
* Ambiente de configuração

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **Abrir**.
* Navegue até sua Área de Trabalho e localisque a pasta **MixedReality213-master** que você desarquiva anteriormente.
* Clique em **Selecionar Pasta**.
* Depois que o Unity terminar de carregar arquivos de projeto, você poderá ver o editor do Unity.
* No Unity, selecione **Arquivo > Build Configurações**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Selecione **Plataforma Windows Universal** na lista **Plataforma** e clique no **botão Alternar Plataforma.**
* Definir Dispositivo de Destino como **Qualquer dispositivo**
* Defina o Tipo de Build como **D3D**
* Definir o SDK como **o mais recente instalado**
* Verificar **projetos C# do Unity**
    * Isso permite modificar arquivos de script no projeto Visual Studio sem recriar o projeto do Unity.
* Clique **em Player Configurações**.
* No painel **Inspetor,** role para baixo até a parte inferior
* No XR Configurações, verifique **Realidade Virtual Com Suporte**
* Em SDKs de Realidade Virtual, **selecione Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Feche **a janela Configurações** build.

### <a name="project-structure"></a>Estrutura do projeto

Este tutorial usa o **[Toolkit – Unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Você pode encontrar as versões [nesta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Cenas concluídas para sua referência**

* Você encontrará duas cenas completas do Unity na **pasta Cenas.**
    * **MixedReality213:** cena concluída com pincel único
    * **MixedReality213Advanced:** cena concluída para design avançado com vários pincéis

**Configuração de nova cena para o tutorial**

* No Unity, clique **em Arquivo > Nova Cena**
* Excluir **câmera principal e** luz **direcional**
* No painel **Project ,** pesquise e arraste os seguintes pré-requisitos para o **painel Hierarquia:**
    * Assets/HoloToolkit/Input/Prefabs/MixedRealityCamera
    * Ativos/AppPrefabs/Ambiente

    ![Câmera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* Há dois pré-requisitos de câmera no Mixed Reality Toolkit:
    * **MixedRealityCamera.prefab:** somente câmera
    * **MixedRealityCameraParent.prefab:** Câmera + Teletransporte + Limite
    * Neste tutorial, vamos usar **MixedRealityCamera sem** o recurso de teletransporte. Por isso, adicionamos  o pré-fab Ambiente simples, que contém um piso básico para fazer com que o usuário se sinta insosso.
    * Para saber mais sobre a teletransporte **com MixedRealityCameraParent,** consulte [Design avançado – Teletransportação e locomoção](#advanced-design---teleportation-and-locomotion)

**Configuração do Skybox**

* Clique **em Janela > Iluminação > Configurações**
* Clique no círculo no lado direito do campo **Material do Skybox**
* Digite "cinza" e selecione **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

    ![Configurando o skybox](images/mr123-skyboxsetting-400px.jpg)

* Marque **a opção Skybox** para poder ver o skybox de gradiente cinza atribuído

    ![Opção De alternar o skybox](images/mr213-skyboxcheck-400px.jpg)

* A cena com MixedRealityCamera, Ambiente e skybox cinza terá esta aparência.

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* Clique **em Arquivo > Salvar Cena como**
* **Salve** sua cena na pasta Cenas com qualquer nome

## <a name="chapter-1---controller-visualization"></a>Capítulo 1 – Visualização do controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Saiba como renderizar modelos de controlador de movimento no modo de jogo do Unity e em runtime.

Windows Mixed Reality fornece um modelo de controlador animado para visualização do controlador. Há várias abordagens que você pode usar para visualização do controlador em seu aplicativo:

* Padrão – Usando o controlador padrão sem modificação
* Híbrido – usando o controlador padrão, mas personalização de alguns de seus elementos ou sobreposição de componentes da interface do usuário
* Substituição – usando seu próprio modelo 3D personalizado para o controlador

Neste capítulo, aprenderemos sobre os exemplos dessas personalizações do controlador.

### <a name="instructions"></a>Instruções

* No painel **Project,** digite **MotionControllers** na caixa de pesquisa . Você também pode encontrá-lo em Ativos/HoloToolkit/Input/Prefabs/.
* Arraste o **pré-fab MotionControllers** para o **painel Hierarquia.**
* Clique no **pré-fab MotionControllers** no **painel Hierarquia.**

**Pré-fab MotionControllers**

O pré-fabricado **MotionControllers** tem um script **MotionControllerVisualizer** que fornece os slots para modelos de controlador alternativos. Se você atribuir seus próprios modelos 3D personalizados, como uma mão ou um uniforme e verificar "Sempre usar modelo alternativo à esquerda/direita", você os verá em vez do modelo padrão. Vamos usar esse slot no Capítulo 4 para substituir o modelo do controlador por um pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Instruções**

* No painel **Inspetor,** clique duas vezes **em MotionControllerVisualizer** script para ver o código no Visual Studio

**Script MotionControllerVisualizer**

As **classes MotionControllerVisualizer** e **MotionControllerInfo** fornecem os meios para acessar & modificar os modelos de controlador padrão. **MotionControllerVisualizer** assina o evento **InteractionSourceDetected** do Unity e instanciou automaticamente os modelos de controlador quando eles são encontrados.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Os modelos do controlador são entregues de acordo [com a especificação glTF](https://github.com/KhronosGroup/glTF). Esse formato foi criado para fornecer um formato comum, melhorando o processo por trás da transmissão e desempacotar ativos 3D. Nesse caso, precisamos recuperar e carregar os modelos do controlador em runtime, pois queremos tornar a experiência do usuário o mais perfeita possível e não há garantia de qual versão dos controladores de movimento o usuário pode estar usando. Este curso, por meio da Toolkit Mixed Reality, usa uma versão do projeto [UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)do Grupo Kronos .

Depois que o controlador tiver sido entregue, os scripts poderão usar **MotionControllerInfo** para encontrar as transformação para elementos específicos do controlador para que possam se posicionar corretamente.

Em um capítulo posterior, aprenderemos a usar esses scripts para anexar elementos da interface do usuário aos controladores.

*Em alguns scripts, você encontrará blocos de código com **#if! UNITY_EDITOR** ou **UNITY_WSA**. Esses blocos de código são executados somente no runtime da UWP quando você implanta no Windows. Isso porque o conjunto de APIs usadas pelo editor do Unity e pelo runtime do aplicativo UWP é diferente.*

* **Salve** a cena e clique no **botão reproduzir.**

Você poderá ver a cena com controladores de movimento em seu headset. Você pode ver animações detalhadas para cliques de botão, movimento de thumbstick e realçamento de toque do touchpad.

![MR213_Controller padrão de visualização](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2 – Anexando elementos da interface do usuário ao controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Saiba mais sobre os elementos dos controladores de movimento
* Saiba como anexar objetos a partes específicas dos controladores

Neste capítulo, você aprenderá a adicionar elementos de interface do usuário ao controlador que o usuário pode acessar e manipular facilmente a qualquer momento. Você também aprenderá a adicionar uma interface do usuário simples do seletor de cores usando a entrada do touchpad.

### <a name="instructions"></a>Instruções

* No painel **Project,** pesquise **script MotionControllerInfo.**
* No resultado da pesquisa, clique duas vezes **em Script MotionControllerInfo** para ver o código Visual Studio.

**Script MotionControllerInfo**

A primeira etapa é escolher a qual elemento do controlador você deseja que a interface do usuário anexe. Esses elementos são definidos **em ControllerElementEnum** em **MotionControllerInfo.cs.**

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Início**
* **Menu**
* **Agarrar**
* **Manípulo**
* **Selecionar**
* **Touchpad**
* **Pose apontando** – esse elemento representa a dica do controlador apontando para a direção.

**Instruções**

* No painel **Project,** pesquise o script **AttachToController.**
* No resultado da pesquisa, clique duas vezes em **AttachToController** script para ver o código Visual Studio.

**Script AttachToController**

O script **AttachToController** fornece uma maneira simples de anexar quaisquer objetos a um elemento e uma entrega de controlador especificados.

Em **AttachElementToController()**,

* Verificar a entrega usando **MotionControllerInfo.Handedness**
* Obter um elemento específico do controlador usando **MotionControllerInfo.TryGetElement()**
* Depois de recuperar a transformação do elemento do modelo de controlador, pai o objeto sob ele e definir a posição local do objeto & rotação como zero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type &quot; + element + &quot; under controller &quot; + newController.ControllerParent.name + &quot;; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

A maneira mais simples de usar o script **AttachToController** é herdar dele, como fizemos no caso de **ColorPickerWheel.** Basta substituir as funções **OnAttachToController** e **OnDetachFromController** para executar sua instalação/detalhamento quando o controlador for detectado/desconectado.

**Instruções**

* No painel **Project,** digite na caixa de pesquisa **ColorPickerWheel**. Você também pode encontrá-lo em Ativos/AppPrefabs/.
* Arraste **o pré-fab ColorPickerWheel** para o **painel Hierarquia.**
* Clique no **pré-fab ColorPickerWheel** no **painel Hierarquia.**
* No painel **Inspetor,** clique duas vezes em **ColorPickerWheel** Script para ver o código Visual Studio.

![Pré-fab ColorPickerWheel](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Como **ColorPickerWheel** **herda AttachToController**, ele mostra **Handedness** e **Element** no **painel Inspetor.** Anexaremos a interface do usuário ao elemento Touchpad no controlador esquerdo.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** substitui **OnAttachToController** e **OnDetachFromController** para assinar o evento de entrada que será usado no próximo capítulo para seleção de cores com entrada de touchpad.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Salve** a cena e clique no **botão reproduzir.**

**Método alternativo para anexar objetos aos controladores**

Recomendamos que seus scripts herdem **de AttachToController** e **substituam OnAttachToController**. No entanto, isso pode nem sempre ser possível. Uma alternativa é usá-lo como um componente autônomo. Isso pode ser útil quando você deseja anexar um pré-fab existente a um controlador sem refactorar seus scripts. Basta que sua classe aguarde que IsAttached seja definido como true antes de executar qualquer configuração. A maneira mais simples de fazer isso é usando uma coroutine para 'Start'.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3 – Trabalhando com a entrada do touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Saiba como obter eventos de dados de entrada do touchpad
* Saiba como usar informações de posição do eixo do touchpad para sua experiência de aplicativo

### <a name="instructions"></a>Instruções

* No painel **Hierarquia,** clique em **ColorPickerWheel**
* No painel **Inspetor,** em **Animator,** clique duas vezes **em ColorPickerWheelController**
* Você poderá ver a **guia Animator** aberta

**Mostrando/ocultando a interface do usuário com o controlador de animação do Unity**

Para mostrar e ocultar a interface **do usuário ColorPickerWheel** com animação, estamos usando o [sistema de animação do Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Definir a propriedade Visible do  **ColorPickerWheel** como gatilhos true ou false **Mostrar** e Ocultar **gatilhos** de animação. **Os** parâmetros **Show e Hide** são definidos no controlador de **animação ColorPickerWheelController.**

![Controlador de animação do Unity](images/mr123-animationcontroller-550px.jpg)

**Instruções**

* No painel **Hierarquia,** selecione **ColorPickerWheel** prefab
* No painel **Inspetor,** clique duas vezes em **Script ColorPickerWheel** para ver o código no Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** assina o evento **InteractionSourceUpdated** do Unity para escutar eventos do touchpad.

Em **InteractionSourceUpdated(),** o script primeiro verifica para garantir que:

* é, na verdade, um evento touchpad (obj.state.**touchpadTouched**)
* origina-se do controlador esquerdo (obj.state.source.**mãos**)

Se ambos forem verdadeiros, a posição do Touchpad (obj. State.**touchpadPosition**) é atribuído a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

Em **Update ()**, com base na propriedade **Visible** , ele dispara mostrar e ocultar gatilhos de animação no componente Animator do seletor de cores

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

Em **Update ()**, **selectorPosition** é usado para converter um raio no Colisor de malha da roda de cores, que retorna uma posição UV. Essa posição pode ser usada para localizar a coordenada de pixel e o valor de cor da textura da roda de cores. Esse valor é acessível a outros scripts por meio da propriedade **SelectedColor** .

![Seletor de cores raycasting de roda](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4-substituindo modelo de controlador

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Saiba como substituir o modelo do controlador por um modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instruções

* Clique em **MotionControllers** no painel **hierarquia** .
* Clique no círculo no lado direito do campo **controlador alternativo direito** .
* Digite **' BrushController**' e selecione o pré-fabricado do resultado. Você pode encontrá-lo em ativos/AppPrefabs/**BrushController**.
* Marque **sempre usar modelo alternativo correto**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

O **BrushController** pré-fabricado não precisa ser incluído no painel **hierarquia** . No entanto, para conferir seus componentes filho:

* no painel de **Project** , digite **BrushController** e arraste **BrushController** pré-fabricado para o painel **hierarquia** .

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Você encontrará o componente de **dica** em **BrushController**. Usaremos sua transformação para iniciar/parar as linhas de desenho.

* Exclua o **BrushController** do painel **hierarquia** .
* **Salve** a cena e clique no botão **reproduzir** . Você poderá ver o modelo de pincel substituiu o controlador de movimento à direita.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5-pintura com selecionar entrada

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Saiba como usar o evento de botão SELECT para iniciar e parar um desenho de linha

### <a name="instructions"></a>Instruções

* pesquise **BrushController** pré-fabricado no painel de **Project** .
* No painel **Inspetor** , clique duas vezes em **BrushController** script para ver o código em Visual Studio

**Script BrushController**

**BrushController** assina os eventos **InteractionSourcePressed** e **InteractionSourceReleased** de interactionmanager. Quando o evento **InteractionSourcePressed** é disparado, a propriedade **draw** do pincel é definida como true; Quando o evento **InteractionSourceReleased** é disparado, a propriedade **draw** do pincel é definida como false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Enquanto **draw** estiver definido como true, o pincel gerará pontos em um **LineRenderer** de Unity instanciado. Uma referência a esse pré-fabricado é mantida no campo de **pré-fabricado de traço** do pincel.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Para usar a cor atualmente selecionada na interface do usuário da roda do seletor de cores, **BrushController** precisa ter uma referência ao objeto **ColorPickerWheel** . Como o **BrushController** pré-fabricado é instanciado em tempo de execução como um controlador de substituição, todas as referências a objetos na cena precisarão ser definidas em tempo de execução. Nesse caso, usamos **gameobject. FindObjectOfType** para localizar o **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Salve** a cena e clique no botão **reproduzir** . Você poderá desenhar as linhas e pintar usando o botão Selecionar no controlador à direita.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6-gerando objeto com a entrada SELECT

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Saiba como usar os eventos de entrada do botão Selecionar e entender
* Saiba como criar uma instância de objetos

### <a name="instructions"></a>Instruções

* no painel de **Project** , digite **objectgerador** na caixa de pesquisa. Você também pode encontrá-lo em ativos/AppPrefabs/
* Arraste o **Objectgerador** pré-fabricado para o painel **hierarquia** .
* Clique em **Objectgerador** no painel **hierarquia** .
* **Objectgerador** tem um campo denominado **fonte de cores**.
* No painel **hierarquia** , arraste a referência **ColorPickerWheel** para esse campo.

    ![Inspetor de objeto](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Clique no pré-fabricado do **Objectgerador** no painel **hierarquia** .
* No painel **Inspetor** , clique duas vezes em script de **objectgerador** para ver o código em Visual Studio.

**Script objectgerador**

O **Objectgerador** instancia cópias de uma malha primitiva (cubo, esfera, cilindro) para o espaço. Quando um **InteractionSourcePressed** é detectado, ele verifica a destro/canhoto e, se for um evento **InteractionSourcePressType. Segure** ou **InteractionSourcePressType. Select** .

Para um evento **Segure** , ele incrementa o índice do tipo de malha atual (Sphere, Cube, cilindro)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Para um evento **Select** , em CodeObject **()**, um novo objeto é instanciado, não pai e liberado no mundo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

O **Objectgerador** usa o **ColorPickerWheel** para definir a cor do material do objeto de exibição. Os objetos gerados recebem uma instância desse material para que eles retenham sua cor.

* **Salve** a cena e clique no botão **reproduzir** .

Você poderá alterar os objetos com o botão compreender e gerar objetos com o botão Selecionar.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Criar e implantar o aplicativo no portal de realidade misturada

* no Unity, selecione **arquivo > Build Configurações**.
* Clique em **Adicionar abrir cenas** para adicionar a cena atual às **cenas na compilação**.
* Clique em **Compilar**.
* Crie uma **nova pasta** chamada "app".
* Clique uma vez na pasta do **aplicativo** .
* Clique em **Selecionar Pasta**.
* Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.
* Abra a pasta do **aplicativo** .
* clique duas vezes em **YourSceneName. sln** Visual Studio arquivo de solução.
* usando a barra de ferramentas superior no Visual Studio, altere o destino de Debug para **Release** e de ARM para **X64**.
* Clique na seta suspensa ao lado do botão dispositivo e selecione **computador local**.
* Clique em **depurar-> iniciar sem Depurar** no menu ou pressione **Ctrl + F5**.

Agora, o aplicativo é criado e instalado no portal de realidade misturada. você pode iniciá-lo novamente por meio de menu Iniciar no Portal de realidade misturada.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Design avançado – ferramentas de pincel com layout radial

![MixedReality213 principal](images/mr213-main-600px.jpg)

Neste capítulo, você aprenderá a substituir o modelo de controlador de movimento padrão por uma coleção de ferramentas de pincel personalizada. Para sua referência, você pode encontrar o **MixedReality213Advanced** de cena concluído na pasta de **cenas** .

### <a name="instructions"></a>Instruções

* no painel de **Project** , digite **BrushSelector** na caixa de pesquisa. Você também pode encontrá-lo em ativos/AppPrefabs/
* Arraste **BrushSelector** pré-fabricado para o painel **hierarquia** .
* Para a organização, crie um gameobject vazio chamado **pincéis**
* arraste o pré-fabricados a seguir do painel de **Project** para **pincéis**
    * Ativos/AppPrefabs/**BrushFat**
    * Ativos/AppPrefabs/**BrushThin**
    * Ativos/AppPrefabs/**borracha**
    * Ativos/AppPrefabs/**MarkerFat**
    * Ativos/AppPrefabs/**MarkerThin**
    * Ativos/AppPrefabs/**lápis**

    ![Pincéis](images/mixedreality213-brushes-250px.png)

* Clique em **MotionControllers** pré-fabricado no painel **hierarquia** .
* No painel **Inspetor** , desmarque **sempre usar o modelo alternativo à direita** no **Visualizador do controlador de movimento**
* No painel **hierarquia** , clique em **BrushSelector**
* **BrushSelector** tem um campo chamado **ColorPicker**
* No painel **Hierarquia,** arraste **o ColorPickerWheel para** **o campo ColorPicker** no **painel Inspetor.**

    ![Atribuir ColorPickerWheel ao Seletor de Pincel](images/mr213-brushselector-500px.jpg)

* No painel **Hierarquia,** em Pré-fab **BrushSelector,** selecione o **objeto Menu.**
* No painel **Inspetor,** no componente **LineObjectCollection,** abra o menu **suspenso Matriz de** objetos. Você verá seis slots vazios.
* No painel **Hierarquia,** arraste cada um dos pré-fabs pai sob o GameObject **brushes** para esses slots em qualquer ordem. (Certifique-se de que você está arrastando os pré-requisitos da cena, não os pré-requisitos na pasta do projeto.)

![Seletor de pincel](images/mr213-brushselectorbrushes-700px.jpg)

**Pré-fab BrushSelector**

Como **BrushSelector** herda **AttachToController**, ele mostra as **opções Handedness** e **Element** no **painel Inspetor.** Selecionamos **Right** e **Pointing Pose para** anexar ferramentas de pincel ao controlador à direita com direção para frente.

O **BrushSelector** usa dois utilitários:

* **Elipse: usada** para gerar pontos no espaço ao longo de uma forma de elipse.
* **LineObjectCollection:** distribui objetos usando os pontos gerados por qualquer classe line (por exemplo, Ellipse). Isso é o que vamos usar para colocar nossos pincéis ao longo da forma de Elipse.

Quando combinados, esses utilitários podem ser usados para criar um menu radial.

**Script LineObjectCollection**

**LineObjectCollection** tem controles para o tamanho, a posição e a rotação de objetos distribuídos ao longo de sua linha. Isso é útil para criar menus radiais como o seletor de pincel. Para criar a aparência de pincéis que são escalados para cima do nada conforme eles se aproximam da posição central selecionada, a curva **ObjectScale** atinge os picos no centro e toca para fora nas bordas.

**Script BrushSelector**

No caso do **BrushSelector**, optemos por usar a animação de procedimento. Primeiro, os modelos de pincel são distribuídos em uma elipse pelo script **LineObjectCollection.** Em seguida, cada pincel é responsável por manter sua posição na mão do usuário com base em seu **valor DisplayMode,** que muda com base na seleção. Escolhemos uma abordagem de procedimento devido à alta probabilidade de transições de posição do pincel serem interrompidas à medida que o usuário seleciona pincéis. Animações mecanim podem lidar com interrupções normalmente, mas tendem a ser mais complicadas do que uma operação lerp simples.

**BrushSelector** usa uma combinação de ambos. Quando a entrada do touchpad é detectada, as opções de pincel ficam visíveis e são dimensionadas ao longo do menu radial. Após um período de tempo máximo (o que indica que o usuário fez uma seleção), as opções de pincel são dimensionadas novamente, deixando apenas o pincel selecionado.

**Visualizando a entrada do touchpad**

Mesmo nos casos em que o modelo do controlador foi completamente substituído, pode ser útil mostrar a entrada nas entradas do modelo original. Isso ajuda a basear as ações do usuário na realidade. Para o **BrushSelector,** optemos por tornar o touchpad brevemente visível quando a entrada for recebida. Isso foi feito recuperando o elemento Touchpad do controlador, substituindo seu material por um material personalizado e aplicando um gradiente à cor do material com base na última vez em que a entrada do touchpad foi recebida.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Seleção de ferramenta de pincel com entrada de touchpad**

Quando o seletor de pincel detecta a entrada pressionada do touchpad, ele verifica a posição da entrada para determinar se ela estava à esquerda ou à direita.

**Espessura do traço com selectPressedAmount**

Em vez **do evento InteractionSourcePressType.Select** no **InteractionSourcePressed()**, você pode obter o valor análogo da quantidade pressionada por meio de **selectPressedAmount**. Esse valor pode ser recuperado em **InteractionSourceUpdated().**

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script de borracha**

**A borracha é** um tipo especial de pincel que substitui a **função** **DrawOverTime()** do pincel base. Embora Draw seja true, a borracha verifica se sua dica intersecção com algum traço de pincel existente. Se isso acontecer, eles serão adicionados a uma fila a ser reduzida e excluída.

## <a name="advanced-design---teleportation-and-locomotion"></a>Design avançado – Teletransportação e locomoção

Se você quiser permitir que o usuário se mova pela cena com o uso de thumbstick, use **MixedRealityCameraParent** em vez de **MixedRealityCamera**. Você também precisa adicionar **InputManager** e **DefaultCursor**. Como **MixedRealityCameraParent** já inclui **MotionControllers** e **Boundary** como componentes filho, você deve remover o **motionControllers** e o pré-fab **ambiente** existentes.

### <a name="instructions"></a>Instruções

* No painel **Hierarquia,** **exclua MixedRealityCamera,** **Environment** e **MotionControllers**
* No painel **Project ,** pesquise e arraste os seguintes pré-requisitos para o **painel Hierarquia:**
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![Câmera de Realidade Misturada pai](images/mr213-cameraparent-300px.png)

* No painel **Hierarquia,** clique em **Gerenciador de Entrada**
* No painel **Inspetor,** role para baixo até a **seção Seletor de Ponteiro** Único Simples
* No painel **Hierarquia,** arraste **DefaultCursor para** o **campo Cursor**

    ![Atribuindo DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Salve** a cena e clique no **botão reproduzir.** Você poderá usar o thumbstick para girar para a esquerda/direita ou para a direita.

## <a name="the-end"></a>Fim

E esse é o final deste tutorial! Você aprendeu a:

* Como trabalhar com modelos de controlador de movimento no modo de jogo e no runtime do Unity.
* Como usar diferentes tipos de eventos de botão e seus aplicativos.
* Como sobrepor elementos de interface do usuário sobre o controlador ou personalizá-lo totalmente.

Agora você está pronto para começar a criar sua própria experiência imersiva com controladores de movimento!

## <a name="completed-scenes"></a>Cenas concluídas

* No painel **de** Project do Unity, clique na **pasta Cenas.**
* Você encontrará duas cenas do Unity **MixedReality213** e **MixedReality213Advanced.**
    * **MixedReality213:** cena concluída com pincel único
    * **MixedReality213Adicionada:** cena concluída com vários pincéis com o exemplo de valor de pressionamento do botão de seleção

## <a name="see-also"></a>Confira também

* [Arquivos de projeto do MR Input 213](https://github.com/Microsoft/MixedReality213)
* [Realidade Misturada Toolkit – Cena de teste do controlador de movimento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Realidade Misturada Toolkit – Mecânica de Captura](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Diretrizes de desenvolvimento do controlador de movimento](../design/motion-controllers.md)