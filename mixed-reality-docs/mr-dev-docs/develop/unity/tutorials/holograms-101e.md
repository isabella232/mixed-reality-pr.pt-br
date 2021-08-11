---
title: Noções básicas do HoloLens (1ª geração) 101E – Projeto completo com emulador
description: Siga este passo a passo de codificação usando o Unity, Visual Studio e HoloLens Emulator para aprender os conceitos básicos de um aplicativo holográfico.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, Windows Mixed Reality, holograma, academy, tutorial, emulador, HoloLens, Mixed Reality Academy, unity, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, Windows 10, olhar, gestos, entrada de voz, som espacial, mapeamento espacial
ms.openlocfilehash: 3cbd1fbba8d4dac4a1d3d0ac1b78a38ed7c8bfa5a7f0b5b3b8d61e9a87f924dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200836"
---
# <a name="hololens-1st-gen-basics-101e-complete-project-with-emulator"></a>HoloLens (1ª geração) Noções básicas 101E: concluir projeto com emulador

>[!IMPORTANT]
>Os tutoriais do Mixed Reality Academy foram projetados com HoloLens (1ª geração), Unity 2017 e Headsets Imersivos de Realidade Misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. Esses tutoriais não **_serão_** atualizados com os mais recentes toolsets ou interações que estão sendo usados para HoloLens 2 e podem não ser compatíveis com versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Este tutorial mostrará um projeto completo, criado no Unity, que demonstra os principais recursos do Windows Mixed Reality no [](../../../design/spatial-sound.md) HoloLens incluindo o [olhar,](../../../design/gaze-and-commit.md)os [gestos,](../../../design/gaze-and-commit.md#composite-gestures)a entrada de [voz,](../../../design/voice-input.md)o som espacial e o mapeamento [espacial.](../../../design/spatial-mapping.md) O tutorial levará aproximadamente 1 hora para ser concluído.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Noções básicas do MR 101E: projeto completo com emulador</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um Windows 10 computador configurado com as ferramentas [corretas instaladas.](../../install-the-tools.md)

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar do suporte do Unity 5.6, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)
  * Se você ainda precisar do suporte do Unity 5.5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se você ainda precisar do suporte do Unity 5.4, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)
* Desarmá-los na área de trabalho ou em outro local fácil de alcançar. Mantenha o nome da pasta como **Origami.**

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – Mundo "Holo"

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

Neste capítulo, configuraremos nosso primeiro projeto do Unity e passaremos pelo processo de build e implantação.

### <a name="objectives"></a>Objetivos

* Configurar o Unity para desenvolvimento holográfico.
* Faça um holograma.
* Veja um holograma que você fez.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **Abrir**.
* Insira local como a **pasta Origami** que você desarmou anteriormente.
* Selecione **Origami** e clique **em Selecionar Pasta**.
* Salve a nova cena: **Arquivo Salvar**  /  **Cena como**.
* Nomeia a **cena como Origami** e pressione o **botão** Salvar.

#### <a name="setup-the-main-camera"></a>Configurar a câmera principal

* No **Painel de Hierarquia**, selecione **Câmera Principal**.
* No **Inspetor,** de definido sua posição de transformação **como 0,0,0**.
* Encontre a **propriedade Limpar Sinalizadores** e altere o menu suspenso de **Skybox** para **Cor sólida.**
* Clique no campo **Tela de fundo** para abrir um seletor de cor.
* Defina **R, G, B e A** para **0**.

#### <a name="setup-the-scene"></a>Configurar a cena

* No Painel **hierarquia ,** clique em **Criar e** **Criar Vazio.**
* Clique com o botão direito do mouse **no novo GameObject** e selecione Renomear. Renomeie o GameObject como **OrigamiCollection.**
* Na pasta **Hologramas** no painel **de Project :**
  * Arraste **Stage** para a Hierarquia para ser um filho de **OrigamiCollection.**
  * Arraste **Sphere1** para a Hierarquia para ser um filho de **OrigamiCollection.**
  * Arraste **Sphere2** para a Hierarquia para ser um filho de **OrigamiCollection.**
* Clique com o botão direito do mouse no objeto **Luz Direcional** no **Painel hierarquia** e selecione **Excluir**.
* Na pasta **Hologramas,** arraste **Luzes** para a raiz do **Painel de Hierarquia**.
* Na **Hierarquia**, selecione **OrigamiCollection**.
* No **Inspetor**, de definido a posição de transformação **como 0, -0,5, 2.0**.
* Pressione o **botão Reproduzir** no Unity para visualizar seus hologramas.
* Você deverá ver os objetos Origami na janela de visualização.
* Pressione **Reproduzir uma** segunda vez para interromper o modo de visualização.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar o projeto do Unity para Visual Studio

* No Unity, **selecione Arquivo > Build Configurações**.
* Selecione **Windows Store na** lista **Plataforma** e clique em Mudar **Plataforma**.
* De **definir o SDK** **como Universal 10** e **Tipo de Build** como **D3D.**
* Verifique **Projetos C# do Unity.**
* Clique **em Adicionar Cenas Abertas** para adicionar a cena.
* Clique **em Player Configurações...**.
* No Painel inspetor, selecione o **logotipo Windows Store.** Em seguida, **selecione Publicação Configurações**.
* Na seção **Funcionalidades,** selecione os **recursos Microfone** e **SpatialPerception.**
* De volta à janela Criar Configurações, clique em **Criar**.
* Crie uma **nova pasta** chamada "Aplicativo".
* Clique com um único clique **na Pasta do Aplicativo**.
* Pressione **Selecionar Pasta**.
* Quando o Unity for feito, uma Explorador de Arquivos será exibida.
* Abra a **pasta Aplicativo.**
* Abra a **solução Visual Studio Origami**.
* Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para Versão **e** de ARM para **X86.**
  * Clique na seta ao lado do botão Dispositivo e selecione **HoloLens Emulator**.
  * Clique **em Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
  * Após algum tempo, o emulador começará com o projeto Origami. Ao iniciar o [emulador](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)pela primeira vez, pode levar até 15 minutos para o emulador iniciar. Depois de iniciado, não feche-o.

## <a name="chapter-2---gaze"></a>Capítulo 2 – Olhar

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

Neste capítulo, apresentaremos a primeira das três maneiras de interagir com seus hologramas – [o olhar](../../../design/gaze-and-commit.md).

### <a name="objectives"></a>Objetivos

* Visualize seu olhar usando um cursor bloqueado pelo mundo.

### <a name="instructions"></a>Instruções

* Go back seu projeto do Unity e feche a janela Configurações build se ela ainda estiver aberta.
* Selecione a **Hologramas** no painel **Project .**
* Arraste o **objeto Cursor** para o **painel Hierarquia** no nível raiz.
* Clique duas vezes no **objeto Cursor** para dar uma olhada mais de perto nele.
* Clique com o botão direito do mouse **na pasta Scripts** no painel Project dados.
* Clique **no** sub menu Criar.
* Selecione **Script C#.**
* Nomeia o script **WorldCursor**. Observação: o nome faz a ressição de minúsculas. Você não precisa adicionar a extensão .cs.
* Selecione o **objeto Cursor** no **painel Hierarquia**.
* Arraste e solte o script **WorldCursor** no **painel Inspetor**.
* Clique duas vezes no script **WorldCursor** para abri-lo Visual Studio.
* Copie e copie esse código em **WorldCursor.cs** e **salve tudo.**

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

            // Move thecursor to the point where the raycast hit.
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

* Recomar o aplicativo do **Arquivo > Build Configurações**.
* Retorne à solução Visual Studio usada anteriormente para implantar no emulador.
* Selecione "Recarregar Tudo" quando solicitado.
* Clique **em Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
* Use o controlador Xbox para dar uma olhada na cena. Observe como o cursor interage com a forma dos objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3 – Gestos

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

Neste capítulo, adicionaremos suporte para [gestos](../../../design/gaze-and-commit.md#composite-gestures). Quando o usuário selecionar uma esfera de papel, faremos com que a esfera caia, aciona a gravidade usando o mecanismo de física do Unity.

### <a name="objectives"></a>Objetivos

* Controle seus hologramas com o gesto Selecionar.

### <a name="instructions"></a>Instruções

Vamos começar criando um script do que pode detectar o gesto Selecionar.

* Na pasta **Scripts,** crie um script chamado **GazeGestureManager.**
* Arraste o script **GazeGestureManager** para o **objeto OrigamiCollection** na Hierarquia.
* Abra o script **GazeGestureManager** no Visual Studio e adicione o seguinte código:

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
    void Start()
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

* Crie outro script na pasta Scripts, desta vez chamado **SphereCommands**.
* Expanda **o objeto OrigamiCollection** na exibição Hierarquia.
* Arraste o script **SphereCommands** para o **objeto Sphere1** no painel Hierarquia.
* Arraste o script **SphereCommands** para o **objeto Sphere2** no painel Hierarquia.
* Abra o script no Visual Studio para edição e substitua o código padrão por este:

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

* Exportar, criar e implantar o aplicativo no HoloLens emulador.
* Procure em volta da cena e centralmente em uma das esferas.
* Pressione o **botão A** no controlador Xbox ou pressione a Barra de Espaços para simular o gesto Selecionar.

## <a name="chapter-4---voice"></a>Capítulo 4 – Voz

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

Neste capítulo, adicionaremos suporte para dois comandos de [voz:](../../../design/voice-input.md)"Redefinir mundo" para retornar as esferas soltas para seu local original e "Soltar esfera" para fazer a esfera cair.

### <a name="objectives"></a>Objetivos

* Adicione comandos de voz que sempre escutam em segundo plano.
* Crie um holograma que reage a um comando de voz.

### <a name="instructions"></a>Instruções

* Na pasta **Scripts,** crie um script chamado **SpeechManager.**
* Arraste o script **SpeechManager** para o **objeto OrigamiCollection** na Hierarquia
* Abra o script **SpeechManager** no Visual Studio.
* Copie e copie esse código em **SpeechManager.cs** e **salve todos:**

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

* Abra o script **SphereCommands** Visual Studio.
* Atualize o script para ler da seguinte forma:

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

* Exportar, criar e implantar o aplicativo no HoloLens emulador.
* O emulador dará suporte ao microfone do computador e responderá à sua voz: ajuste a exibição para que o cursor seja em uma das esferas e diga "Drop Sphere".
* Diga "**Redefinir Mundo**" para voltar às posições iniciais.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5 – Som espacial

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

Neste capítulo, adicionaremos música ao aplicativo e dispararemos efeitos de som em determinadas ações. Vamos usar o som [espacial para](../../../design/spatial-sound.md) dar aos sons um local específico no espaço 3D.

### <a name="objectives"></a>Objetivos

* Ouvir hologramas em seu mundo.

### <a name="instructions"></a>Instruções

* No Unity, selecione no menu superior **Editar > Project Configurações > Áudio**
* Encontre a **configuração Plug-in** do Spatializer e selecione **Espacializador MS HRTF**.
* Na pasta **Hologramas,** arraste o objeto **Ambience** para o **objeto OrigamiCollection** no Painel de Hierarquia.
* Selecione **OrigamiCollection e** encontre o componente **Fonte de** Áudio. Altere estas propriedades:
  * Verifique a **propriedade Spatialize.**
  * Verifique a **reprodução ao ser acoada.**
  * Altere **o Spatial Blend** para **3D** arrastando o controle deslizante até a direita.
  * Verifique a **propriedade Loop.**
  * Expanda **Som 3D Configurações** e insira **0,1** para **Nível do Doppler.**
  * De **definido Volume Rolloff** como **Logarithmic Rolloff**.
  * De **acordo com a Distância Máxima** como **20**.
* Na pasta **Scripts,** crie um script chamado **SphereSounds.**
* Arraste **SphereSounds** para os **objetos Sphere1** e **Sphere2** na Hierarquia.
* Abra **SphereSounds** no Visual Studio, atualize o código a seguir e **Salve Tudo.**

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
* Exportar, criar e implantar o aplicativo no HoloLens emulador.
* Use fones de ouvido para obter o efeito total e mova-se cada vez mais para perto do Estágio para ouvir os sons mudarem.

## <a name="chapter-6---spatial-mapping"></a>Capítulo 6 – Mapeamento espacial

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Agora, vamos usar o mapeamento [espacial para](../../../design/spatial-mapping.md) colocar o tabuleiro do jogo em um objeto real no mundo real.

### <a name="objectives"></a>Objetivos

* Traga seu mundo real para o mundo virtual.
* Coloque seus hologramas onde eles são mais importantes para você.

### <a name="instructions"></a>Instruções

* Clique na pasta **Hologramas** no painel Project dados.
* Arraste o **ativo mapeamento** espacial para a raiz da **Hierarquia**.
* Clique no **objeto Mapeamento** Espacial na Hierarquia.
* No painel **Inspetor ,** altere as seguintes propriedades:
  * Marque a **caixa Desenhar Malhas** Visuais.
  * Localize **Desenhar Material** e clique no círculo à direita. Digite "**wireframe**" no campo de pesquisa na parte superior. Clique no resultado e feche a janela.
* Exportar, criar e implantar o aplicativo no HoloLens emulador.
* Quando o aplicativo for executado, uma malha de uma sala de estar do mundo real digitalizada anteriormente será renderizada em wireframe.
* Observe como uma esfera rolante cairá do estágio e no chão!

Agora, mostraremos como mover o OrigamiCollection para um novo local:

* Na pasta **Scripts,** crie um script chamado **TapToPlaceParent.**
* Na Hierarquia **,** expanda **OrigamiCollection** e selecione o **objeto** Stage.
* Arraste o script **TapToPlaceParent** para o objeto Stage.
* Abra o script **TapToPlaceParent** Visual Studio e atualize-o para que ele seja o seguinte:

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

* Exportar, criar e implantar o aplicativo.
* Agora você deve ser capaz de colocar o jogo em um local específico olhando para ele, usando o gesto Selecionar (**A** ou Barra de Espaços) e, em seguida, movendo para um novo local e usando o gesto Selecionar novamente.

## <a name="the-end"></a>Fim

E esse é o final deste tutorial!

Você aprendeu a:

* Como criar um aplicativo holográfico no Unity.
* Como usar o olhar, o gesto, a voz, os sons e o mapeamento espacial.
* Como criar e implantar um aplicativo usando Visual Studio.

Agora você está pronto para começar a criar seus próprios aplicativos holográficos!

## <a name="see-also"></a>Confira também

* [Noções básicas do MR 101: projeto completo com dispositivo](holograms-101.md)
* [Foco](../../../design/gaze-and-commit.md)
* [Focar com a cabeça e confirmar](../../../design/gaze-and-commit.md)
* [Entrada de voz](../../../design/voice-input.md)
* [Som espacial](../../../design/spatial-sound.md)
* [Mapeamento espacial](../../../design/spatial-mapping.md)