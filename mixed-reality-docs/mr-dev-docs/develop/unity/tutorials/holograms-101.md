---
title: Noções básicas do HoloLens (1ª geração) 101 – Projeto completo com dispositivo
description: siga este passo a passo de codificação usando o Unity, Visual Studio e HoloLens para aprender os fundamentos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, Windows Mixed Reality, HoloLens, holograma, academia, tutorial, HoloLens, reality academy, unity, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual, Windows 10
ms.openlocfilehash: 63219edebeb63dbf4589e8162f8dc1bab83275c38f29b106db9bae234cdabde0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200956"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>noções básicas de HoloLens (1ª gen) 101: concluir o projeto com o dispositivo

<br>

>[!IMPORTANT]
>os tutoriais misturados do academia de realidade foram projetados com a HoloLens (1ª gen), o Unity 2017 e o headset de imersão de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes ou as interações usadas para o HoloLens 2 e podem não ser compatíveis com as versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

este tutorial guiará você por um projeto completo, interno do Unity, que demonstra os principais recursos de Windows Mixed Reality em HoloLens incluindo [olhar](../../../design/gaze-and-commit.md), [gestos](../../../design/gaze-and-commit.md#composite-gestures), [entrada de voz](../../../design/voice-input.md), [som espacial](../../../design/spatial-sound.md) e [mapeamento espacial](../../../design/spatial-mapping.md).

O tutorial levará aproximadamente 1 hora para ser concluído.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Noções básicas do MR 101: projeto completo com dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* um computador Windows 10 configurado com as ferramentas corretas [instaladas](../../install-the-tools.md).
* um dispositivo HoloLens [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar. Mantenha o nome da pasta como **origami**.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível em github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – mundo "holo"

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.

### <a name="objectives"></a>Objetivos

* Configure o Unity para o desenvolvimento de Holographic.
* Crie um holograma.
* Veja um holograma que você fez.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **Abrir**.
* Insira o local como a pasta de **origami** que você cancelou anteriormente.
* Selecione **origami** e clique em **Selecionar pasta**.
* Como o projeto de **origami** não contém uma cena, salve a cena padrão vazia em um novo arquivo usando: **arquivo**  /  **salvar cena como**.
* Nomeie o novo **origami** de cena e pressione o botão **salvar** .

#### <a name="setup-the-main-virtual-camera"></a>Configurar a câmera virtual principal

* No **Painel de Hierarquia**, selecione **Câmera Principal**.
* No **Inspetor** , defina sua posição de transformação como **0, 0, 0**.
* Localize a propriedade **limpar sinalizadores** e altere a lista suspensa de **Skybox** para **cor sólida**.
* Clique no campo **Tela de fundo** para abrir um seletor de cor.
* Defina **R, G, B e A** para **0**.

#### <a name="setup-the-scene"></a>Configurar a cena

* No **painel hierarquia**, clique em **criar** e em **criar vazio**.
* Clique com o botão direito do mouse no novo **gameobject** e selecione Renomear. Renomeie o gameobject para **origamicollection**.
* na pasta **Hologramas** no painel de Project (expanda ativos e selecione Hologramas ou clique duas vezes na pasta Hologramas no painel de Project):
  * Arraste o **estágio** para a hierarquia para ser um filho de **origamicollection**.
  * Arraste **Sphere1** para a hierarquia para ser um filho de **origamicollection**.
  * Arraste **Sphere2** para a hierarquia para ser um filho de **origamicollection**.
* Clique com o botão direito do mouse no objeto de **luz direcional** no **painel hierarquia** e selecione **excluir**.
* na pasta **Hologramas** , arraste **luzes** para a raiz do **painel hierarquia**.
* Na **hierarquia**, selecione o **origamicollection**.
* No **Inspetor**, defina a posição de transformação como **0,-0,5, 2,0**.
* Pressione o botão **reproduzir** no Unity para visualizar os hologramas.
* Você deve ver os objetos de origami na janela de visualização.
* Pressione **executar** uma segunda vez para parar o modo de visualização.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar o projeto do Unity para o Visual Studio

* em Unity, selecione **arquivo > Build Configurações**.
* selecione **Plataforma Universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
* Defina o **SDK** como **Universal 10** e o **tipo de compilação** como **D3D**.
* Verifique os **projetos do Unity C#**.
* Clique em **Adicionar abrir cenas** para adicionar a cena.
* Clique em **Compilar**.
* Na janela Explorador de arquivos que aparece, crie uma **nova pasta** chamada "aplicativo".
* Clique uma vez na **pasta do aplicativo**.
* Pressione **Selecionar pasta**.
* Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.
* Abra a pasta do **aplicativo** .
* Abra (clique duas vezes) **origami. sln**.
* usando a barra de ferramentas superior no Visual Studio, altere o destino de Debug para **Release** e de ARM para **X86**.
* Clique na seta ao lado do botão dispositivo e selecione **computador remoto** para implantar por Wi-Fi.
  * Defina o **endereço** para o nome ou endereço IP do seu HoloLens. se você não souber o endereço IP do dispositivo, procure em **Configurações > rede & opções avançadas da Internet >** ou pergunte ao Cortana **"ei Cortana, qual é meu endereço IP?"**
  * se o HoloLens estiver conectado via usb, você poderá selecionar o **dispositivo** a ser implantado sobre usb.
  * Deixe o **modo de autenticação** definido como **Universal**.
  * Clique em **Selecionar**

* Clique em **depurar > iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).

* o projeto de Origami agora será compilado, implantado em seu HoloLens e, em seguida, executado.
* coloque em sua HoloLens e procure ver os novos hologramas.

## <a name="chapter-2---gaze"></a>Capítulo 2 – olhar

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seus hologramas-- [olhar](../../../design/gaze-and-commit.md).

### <a name="objectives"></a>Objetivos

* Visualize seu olhar usando um cursor com bloqueio mundial.

### <a name="instructions"></a>Instruções

* volte ao seu projeto do Unity e feche a janela Build Configurações se ela ainda estiver aberta.
* selecione a pasta **Hologramas** no **painel de Project**.
* Arraste o objeto **cursor** para o **painel hierarquia** no nível raiz.
* Clique duas vezes no objeto de **cursor** para examiná-lo mais detalhadamente.
* clique com o botão direito do mouse na pasta **Scripts** no painel de Project.
* Clique no submenu **criar** .
* Selecione **script C#**.
* Nomeie o script **WorldCursor**. Observação: o nome diferencia maiúsculas de minúsculas. Você não precisa adicionar a extensão. cs.
* Selecione o objeto **cursor** no **painel hierarquia**.
* Arraste e solte o script **WorldCursor** no **painel Inspetor**.
* Clique duas vezes no script **WorldCursor** para abri-lo no Visual Studio.
* Copie e cole esse código em **WorldCursor. cs** e **Salve tudo**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* recompile o aplicativo do **arquivo > Build Configurações**.
* retorne para a solução de Visual Studio usada anteriormente para implantar em seu HoloLens.
* Selecione ' recarregar tudo ' quando solicitado.
* Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
* Agora, observe a cena e observe como o cursor interage com a forma de objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3-gestos

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

Neste capítulo, adicionaremos suporte para [gestos](../../../design/gaze-and-commit.md#composite-gestures). Quando o usuário seleciona uma esfera de papel, vamos fazer com que a esfera fique ativando a gravidade usando o mecanismo de física do Unity.

### <a name="objectives"></a>Objetivos

* Controle seus hologramas com o gesto de seleção.

### <a name="instructions"></a>Instruções

Vamos começar criando um script e, em seguida, pode detectar o gesto de seleção.

* Na pasta **scripts** , crie um script chamado **GazeGestureManager**.
* Arraste o script **GazeGestureManager** para o objeto **origamicollection** na hierarquia.
* abra o script **GazeGestureManager** em Visual Studio e adicione o seguinte código:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Crie outro script na pasta scripts, desta vez com o nome **SphereCommands**.
* Expanda o objeto **origamicollection** na exibição hierarquia.
* Arraste o script **SphereCommands** para o objeto **Sphere1** no painel hierarquia.
* Arraste o script **SphereCommands** para o objeto **Sphere2** no painel hierarquia.
* abra o script no Visual Studio para edição e substitua o código padrão por este:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exporte, compile e implante o aplicativo em seu HoloLens.
* Examine um dos seus próprios.
* Execute o gesto de seleção e observe a caixa de círculo na superfície abaixo.

## <a name="chapter-4---voice"></a>Capítulo 4-voz

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

Neste capítulo, adicionaremos suporte para dois comandos de [voz](../../../design/voice-input.md): "redefinir mundo" para retornar o separador para o local original e "soltar a esfera" para fazer a esfera cair.

### <a name="objectives"></a>Objetivos

* Adicione comandos de voz que sempre escutam em segundo plano.
* Crie um holograma que reage a um comando de voz.

### <a name="instructions"></a>Instruções

* Na pasta **scripts** , crie um script chamado **speechmanager**.
* Arraste o script **speechmanager** para o objeto **Origamicollection** na hierarquia
* Abra o script **speechmanager** no Visual Studio.
* Copie e cole esse código em **speechmanager. cs** e **Salve todos**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Abra o script **SphereCommands** no Visual Studio.
* Atualize o script para ler da seguinte maneira:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exporte, compile e implante o aplicativo em seu HoloLens.
* Examine uma das esferas e, em seguida, diga "**drop Sphere**".
* Diga "**Redefinir mundo**" para trazê-los de volta para suas posições iniciais.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5-som espacial

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

Neste capítulo, vamos adicionar música ao aplicativo e, em seguida, disparar efeitos sonoros em determinadas ações. Vamos usar o [som espacial](../../../design/spatial-sound.md) para dar sons a um local específico no espaço 3D.

### <a name="objectives"></a>Objetivos

* Ouça os hologramas em seu mundo.

### <a name="instructions"></a>Instruções

* em Unity, selecione no menu superior **editar > Project Configurações > áudio**
* No painel inspetor no lado direito, localize a configuração do **plug-in Spatializer** e selecione **MS HRTF Spatializer**.
* na pasta **Hologramas** no painel de Project, arraste o objeto **Ambience** para o objeto **origamicollection** no painel hierarquia.
* Selecione **origamicollection** e localize o componente **fonte de áudio** no painel inspetor. Altere estas propriedades:
  * Verifique a propriedade **espacialize** .
  * Verifique o **jogo em ativo**.
  * Altere a **mistura espacial** para **3D** arrastando o controle deslizante para a direita. O valor deve mudar de 0 para 1 quando você move o controle deslizante.
  * Verifique a propriedade **loop** .
  * expanda **Configurações de som 3d** e insira **0,1** para o **nível de Doppler**.
  * Definir **rolloff de volume** para **rolloff logarítmica**.
  * Defina a **distância máxima** como **20**.
* Na pasta **scripts** , crie um script chamado **SphereSounds**.
* Arraste e solte **SphereSounds** para os objetos **Sphere1** e **Sphere2** na hierarquia.
* abra **SphereSounds** no Visual Studio, atualize o código a seguir e **salve tudo**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Salve o script e retorne ao Unity.
* Exporte, compile e implante o aplicativo em seu HoloLens.
* Mova-se mais de perto do palco e gire-o lado a lado para ouvir a alteração dos sons.

## <a name="chapter-6---spatial-mapping"></a>Capítulo 6-mapeamento espacial

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Agora vamos usar o [mapeamento espacial](../../../design/spatial-mapping.md) para posicionar o tabuleiro em um objeto real no mundo real.

### <a name="objectives"></a>Objetivos

* Traga seu mundo real para o mundo virtual.
* Coloque seus hologramas onde forem mais importantes para você.

### <a name="instructions"></a>Instruções

* no Unity, clique na pasta **Hologramas** no painel de Project.
* Arraste o ativo de **mapeamento espacial** para a raiz da **hierarquia**.
* Clique no objeto de **mapeamento espacial** na hierarquia.
* No **painel Inspetor**, altere as seguintes propriedades:
  * Marque a caixa **desenhar malhas visuais** .
  * Localize **material de desenho** e clique no círculo à direita. Digite "**wireframe**" no campo de pesquisa na parte superior. Clique no resultado e feche a janela. Quando você fizer isso, o valor para o material de desenho deverá ser definido como wireframe.
* Exporte, compile e implante o aplicativo em seu HoloLens.
* Quando o aplicativo é executado, uma malha delineada se sobrepõe ao seu mundo real.
* Observe como uma esfera de rolagem ficará fora do palco e até o andar!

Agora, mostraremos como mover o Origamicollection para um novo local:

* Na pasta **scripts** , crie um script chamado **TapToPlaceParent**.
* Na **hierarquia**, expanda o **origamicollection** e selecione o objeto **Stage** .
* Arraste o script **TapToPlaceParent** para o objeto Stage.
* abra o script **TapToPlaceParent** no Visual Studio e atualize-o para o seguinte:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exportar, compilar e implantar o aplicativo.
* Agora você deve ser capaz de posicionar o jogo em um local específico por nuvens-lo, usando o gesto de seleção e, em seguida, movendo para um novo local e usando o gesto de seleção novamente.

## <a name="chapter-7---holographic-fun"></a>Capítulo 7 – diversão Holographic

### <a name="objectives"></a>Objetivos

* Revele a entrada para um Holographic Underworld.

### <a name="instructions"></a>Instruções

Agora, mostraremos como descobrir o Holographic Underworld:

* na pasta **Hologramas** no painel de Project:
  * Arraste **Underworld** para a hierarquia para ser um filho de **origamicollection**.
* Na pasta **scripts** , crie um script chamado **HitTarget**.
* Na **hierarquia**, expanda o **origamicollection**.
* Expanda o objeto de **estágio** e selecione o objeto de **destino** (ventilador azul).
* Arraste o script **HitTarget** para o objeto de **destino** .
* abra o script **HitTarget** no Visual Studio e atualize-o para o seguinte:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* No Unity, selecione o objeto de **destino** .
* Agora, duas propriedades públicas estão visíveis no componente de **destino de visita** e precisam fazer referência a objetos em nossa cena:
  * Arraste **Underworld** do painel **hierarquia** para a propriedade **Underworld** no componente de **destino de visita** .
  * Arraste o **estágio** do painel **hierarquia** até o **objeto para ocultar** a propriedade no componente de destino de **visita** .
* Exportar, compilar e implantar o aplicativo.
* Coloque a coleção de origami no piso e, em seguida, use o gesto de seleção para fazer uma queda de esfera.
* Quando a esfera atinge o destino (ventilador azul), ocorrerá uma explosão. A coleção será ocultada e um orifício para o Underworld será exibido.

## <a name="the-end"></a>Fim

E esse é o fim deste tutorial!

Você aprendeu a:

* Como criar um aplicativo Holographic no Unity.
* Como fazer uso de olhar, gesto, voz, som e mapeamento espacial.
* Como criar e implantar um aplicativo usando Visual Studio.

Agora você está pronto para começar a criar sua própria experiência de Holographic!

## <a name="see-also"></a>Confira também

* [Noções básicas do MR 101E: projeto completo com emulador](holograms-101e.md)
* [Foco](../../../design/gaze-and-commit.md)
* [Focar com a cabeça e confirmar](../../../design/gaze-and-commit.md)
* [Entrada de voz](../../../design/voice-input.md)
* [Som espacial](../../../design/spatial-sound.md)
* [Mapeamento espacial](../../../design/spatial-mapping.md)