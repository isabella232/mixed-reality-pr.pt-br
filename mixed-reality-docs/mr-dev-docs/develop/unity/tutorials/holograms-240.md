---
title: Compartilhamento do HoloLens (1ª geração) 240 – Vários dispositivos HoloLens
description: Siga este passo a passo de codificação usando Unity, Visual Studio e HoloLens para saber os detalhes do compartilhamento de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sharing, networking, academy, tutorial, HoloLens, Mixed Reality Academy, unity, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208696"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (1ª geração) compartilhamento 240: vários HoloLens dispositivos

>[!IMPORTANT]
>Os tutoriais do Mixed Reality Academy foram projetados com HoloLens (1ª geração), Unity 2017 e Headsets Imersivos de Realidade Misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. Esses tutoriais não **_serão_** atualizados com os mais recentes toolsets ou interações que estão sendo usados para HoloLens 2 e podem não ser compatíveis com versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

Hologramas presença em nosso mundo permanecendo no lugar à medida que nos movemos no espaço. HoloLens mantém os hologramas no local usando vários sistemas [de coordenadas](../../../design/coordinate-systems.md) para controlar a localização e a orientação dos objetos. Quando compartilhamos esses sistemas de coordenadas entre dispositivos, podemos criar uma experiência compartilhada que nos permita participar de um mundo holográfico compartilhado.

Neste tutorial, nós iremos:

* Configurar uma rede para uma experiência compartilhada.
* Compartilhe hologramas entre HoloLens dispositivos.
* Descubra outras pessoas em nosso mundo holográfico compartilhado.
* Crie uma experiência interativa compartilhada na qual você pode direcionar outros jogadores – e iniciar projetos neles!

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Compartilhamento do MR 240: vários dispositivos HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um Windows 10 computador configurado com as ferramentas [corretas instaladas com](../../../develop/install-the-tools.md) acesso à Internet.
* Pelo menos dois HoloLens [configurados para desenvolvimento.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar do suporte do Unity 5.6, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)
  * Se você ainda precisar do suporte do Unity 5.5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se você ainda precisar do suporte do Unity 5.4, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)
* Desarmá-los na área de trabalho ou em outro local fácil de alcançar. Mantenha o nome da pasta **como SharedHolograms.**

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

Neste capítulo, configuraremos nosso primeiro projeto do Unity e passaremos pelo processo de build e implantação.

### <a name="objectives"></a>Objetivos

* Configure o Unity para desenvolver aplicativos holográficos.
* Veja seu holograma!

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **Abrir**.
* Insira local como a **pasta SharedHolograms** que você desarquixou anteriormente.
* Selecione **Project Nome e** clique em Selecionar **Pasta**.
* Na Hierarquia **,** clique com o botão direito do mouse **na Câmera Principal** e selecione **Excluir**.
* Na pasta **HoloToolkit-Sharing-240/Prefabs/Camera,** encontre **o** pré-fab Câmera Principal.
* Arraste e solte a **Câmera Principal** na **Hierarquia**.
* Na Hierarquia **,** clique em **Criar e** **Criar Vazio.**
* Clique com o botão direito do mouse **no novo GameObject** e selecione **Renomear**.
* Renomeie o GameObject como **HologramCollection.**
* Selecione o **objeto HologramCollection** na **Hierarquia**.
* No **Inspetor,** de definido **a posição de transformação** como: **X: 0, Y: -0,25, Z: 2**.
* Na pasta **Hologramas** no painel **Project ,** encontre o **ativo EnergyHub.**
* Arraste e solte o **objeto EnergyHub** do painel **Project** para a **Hierarquia** como um filho **de HologramCollection**.
* Selecione **Arquivo > Salvar Cena como...**
* Nomeia a **cena SharedHolograms** e clique em **Salvar**.
* Pressione o **botão Reproduzir** no Unity para visualizar seus hologramas.
* Pressione **Reproduzir uma** segunda vez para interromper o modo de visualização.

**Exportar o projeto do Unity para Visual Studio**

* No Unity, **selecione Arquivo > Build Configurações**.
* Clique **em Adicionar Cenas Abertas** para adicionar a cena.
* Selecione **Plataforma Windows Universal** na lista **Plataforma** e clique em Mudar **Plataforma**.
* De **definir o SDK** **como Universal 10.**
* De **definir Dispositivo de** destino como **HoloLens** tipo de **build UWP e UWP** como **D3D.**
* Verifique **Projetos C# do Unity.**
* Clique em **Compilar**.
* Na janela do explorador de arquivos exibida, crie uma **Nova Pasta** chamada "Aplicativo".
* Clique com um único clique **na pasta** Aplicativo.
* Pressione **Selecionar Pasta**.
* Quando o Unity for feito, uma Explorador de Arquivos será exibida.
* Abra a **pasta Aplicativo.**
* Abra **SharedHolograms.sln** para iniciar o Visual Studio.
* Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para Versão **e** de ARM para **X86.**
* Clique na seta para baixo ao lado de Computador Local e selecione **Dispositivo Remoto.**
    * De definir **o Endereço** como o nome ou o endereço IP do seu HoloLens. Se você não sabe o endereço IP do dispositivo, procure opções avançadas > Internet Configurações > Network **& >** ou pergunte Cortana **"Hey Cortana, What's my IP address?"**
    * Deixe o **Modo de Autenticação** definido como **Universal.**
    * Clique em **Selecionar**
* Clique **em Depurar > Iniciar Sem depuração** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você implanta em seu dispositivo, você precisará [emparelhá-lo com Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
* Coloque sua HoloLens e encontre o holograma do EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2 – Interação

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

Neste capítulo, interagiremos com nossos hologramas. Primeiro, adicionaremos um cursor para visualizar nosso [Gaze.](../../../design/gaze-and-commit.md) Em seguida, adicionaremos [Gestos e](../../../design/gaze-and-commit.md#composite-gestures) usaremos nossa mão para colocar nossos hologramas no espaço.

### <a name="objectives"></a>Objetivos

* Use a entrada de olhar para controlar um cursor.
* Use a entrada de gesto para interagir com hologramas.

### <a name="instructions"></a>Instruções

**Foco**

* No painel **Hierarquia,** selecione o **objeto HologramCollection.**
* No painel **Inspetor, clique** no **botão Adicionar** Componente.
* No menu, digite na caixa de pesquisa Gerenciador **de Olhar**. Selecione o resultado da pesquisa.
* Na pasta **HoloToolkit-Sharing-240\Prefabs\Input,** encontre o **ativo Cursor.**
* Arraste e solte o **ativo Cursor** na **Hierarquia**.

**Gesto**

* No painel **Hierarquia,** selecione o **objeto HologramCollection.**
* Clique **em Adicionar Componente** e digite Gerenciador de **Gestos** no campo de pesquisa. Selecione o resultado da pesquisa.
* No painel **Hierarquia ,** expanda **HologramCollection**.
* Selecione o objeto **filho EnergyHub.**
* No painel **Inspetor, clique** no **botão Adicionar** Componente.
* No menu, digite na caixa de pesquisa Posicionamento **do holograma**. Selecione o resultado da pesquisa.
* Salve a cena selecionando **Arquivo > Salvar Cena**.

**Implantar e aproveitar**

* Crie e implante em seu HoloLens, usando as instruções do capítulo anterior.
* Depois que o aplicativo é HoloLens, mova a cabeça e observe como o EnergyHub segue seu olhar.
* Observe como o cursor aparece quando você se volta para o holograma e muda para uma luz de ponto quando não está olhando para um holograma.
* Execute um toque de ar para colocar o holograma. Neste momento em nosso projeto, você só pode colocar o holograma uma vez (reimplantar para tentar novamente).

## <a name="chapter-3---shared-coordinates"></a>Capítulo 3 – Coordenadas Compartilhadas

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

É divertido ver e interagir com hologramas, mas vamos além. Configuraremos nossa primeira experiência compartilhada – um holograma que todos podem ver juntos.

### <a name="objectives"></a>Objetivos

* Configurar uma rede para uma experiência compartilhada.
* Estabelecer um ponto de referência comum.
* Compartilhar sistemas de coordenadas entre dispositivos.
* Todos veem o mesmo holograma!

>[!NOTE]
>Os **recursos InternetClientServer** e **PrivateNetworkClientServer** devem ser declarados para que um aplicativo se conecte ao servidor de compartilhamento. Isso é feito para você já Hologramas 240, mas tenha isso em mente para seus próprios projetos.

>1. No Editor do Unity, acesse as configurações do player navegando até "Editar > Project Configurações > Player"
>2. Clique na guia "Windows Store"
>3. Na seção "Funcionalidades de Configurações > publicação", verifique a funcionalidade **InternetClientServer** e a funcionalidade **PrivateNetworkClientServer**

### <a name="instructions"></a>Instruções

* No painel **Project, navegue** até a **pasta HoloToolkit-Sharing-240\Prefabs\Sharing.**
* Arraste e solte **o** pré-fab Compartilhamento no painel **Hierarquia**.

Em seguida, precisamos iniciar o serviço de compartilhamento. Somente **um computador** na experiência compartilhada precisa fazer essa etapa.

* No Unity – no menu superior – selecione o **menu HoloToolkit-Sharing-240**.
* Selecione o **item Iniciar Serviço de** Compartilhamento na lista listada.
* Marque a **opção Rede Privada** e clique em Permitir **Acesso** quando o prompt de firewall for exibido.
* Anote o endereço IPv4 exibido na janela do console do Serviço de Compartilhamento. Esse é o mesmo IP que o computador em que o serviço está sendo executado.

Siga o restante das instruções em todos **os PCs** que ingressarão na experiência compartilhada.

* Na Hierarquia **,** selecione o **objeto Sharing.**
* No **Inspetor**, no componente **Estágio**  de Compartilhamento, altere o Endereço do Servidor de 'localhost' para o endereço IPv4 do computador que executa SharingService.exe.
* Na **Hierarquia,** selecione o **objeto HologramCollection.**
* No **Inspetor,** clique no **botão Adicionar** Componente.
* Na caixa de pesquisa, digite **Importar Gerenciador de Âncoras de Exportação**. Selecione o resultado da pesquisa.
* No painel **Project,** navegue até a **pasta Scripts.**
* Clique duas vezes no script **HologramPlacement** para abri-lo Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* De volta ao Unity, selecione **HologramCollection** no **painel Hierarquia**.
* No painel **Inspetor, clique** no **botão Adicionar** Componente.
* No menu, digite na caixa de pesquisa **Gerenciador de Estado do Aplicativo**. Selecione o resultado da pesquisa.

**Implantar e aproveitar**

* Crie o projeto para seus HoloLens dispositivos.
* Designe um HoloLens para implantar primeiro. Você precisará aguardar até que a Âncora seja carregada no serviço antes de colocar o EnergyHub (isso pode levar cerca de 30 a 60 segundos). Até que o upload seja feito, os gestos de toque serão ignorados.
* Depois que o EnergyHub tiver sido colocado, sua localização será carregada no serviço e você poderá implantar em todos os outros HoloLens dispositivos.
* Quando um novo HoloLens pela primeira vez insinte na sessão, o local do EnergyHub pode não estar correto nesse dispositivo. No entanto, assim que as localizações de âncora e EnergyHub foram baixadas do serviço, o EnergyHub deve ir para o novo local compartilhado. Se isso não acontecer dentro de aproximadamente 30 a 60 segundos, vá até o local em que o HoloLens original estava ao definir a âncora para coletar mais pistas de ambiente. Se o local ainda não bloquear, reimplante no dispositivo.
* Quando todos os dispositivos estão prontos e executando o aplicativo, procure o EnergyHub. Todos vocês podem concordar sobre o local do holograma e para qual direção o texto está voltado?

## <a name="chapter-4---discovery"></a>Capítulo 4 – Descoberta

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Agora todos podem ver o mesmo holograma! Agora, vamos ver todos os outros conectados ao nosso mundo holográfico compartilhado. Neste capítulo, vamos pegar o local da cabeça e a rotação de todos os outros HoloLens dispositivos na mesma sessão de compartilhamento.

### <a name="objectives"></a>Objetivos

* Descubra um ao outro em nossa experiência compartilhada.
* Escolha e compartilhe um avatar do jogador.
* Anexe o avatar do jogador ao lado da cabeça de todos.

### <a name="instructions"></a>Instruções

* No painel **Project, navegue** até a **pasta Hologramas** dados.
* Arraste e solte **o PlayerAvatarStore** na **Hierarquia**.
* No painel **Project,** navegue até a **pasta Scripts.**
* Clique duas vezes no script **AvatarSelector** para abri-lo Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* Na **Hierarquia,** selecione o **objeto HologramCollection.**
* No **Inspetor, clique** em **Adicionar Componente**.
* Na caixa de pesquisa, digite **Gerenciador de Player Local.** Selecione o resultado da pesquisa.
* Na **Hierarquia,** selecione o **objeto HologramCollection.**
* No **Inspetor, clique** em **Adicionar Componente**.
* Na caixa de pesquisa, digite **Gerenciador de Player Remoto.** Selecione o resultado da pesquisa.
* Abra o script **HologramPlacement** Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Abra o script **AppStateManager** no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Implantar e aproveitar**

* Crie e implante o projeto em seus HoloLens dispositivos.
* Quando você ouvir um som de ping, encontre o menu de seleção de avatar e selecione um avatar com o gesto de toque de ar.
* Se você não estiver olhando para nenhum holograma, a luz de ponto ao redor do cursor transformará uma cor diferente quando o HoloLens estiver se comunicando com o serviço: inicializando (roxo escuro), baixando a âncora (verde), importando/exportando dados de local (amarelo), carregando a âncora (azul). Se a luz de ponto ao redor do cursor for a cor padrão (roxo claro), você estará pronto para interagir com outros jogadores em sua sessão!
* Veja outras pessoas conectadas ao seu espaço – haverá um robô holográfico flutuando acima de seus olhos e imitando seus movimentos de cabeça!

## <a name="chapter-5---placement"></a>Capítulo 5 – Posicionamento

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

Neste capítulo, tornaremos a âncora capaz de ser colocada em superfícies do mundo real. Vamos usar coordenadas compartilhadas para colocar essa âncora no ponto central entre todos conectados à experiência compartilhada.

### <a name="objectives"></a>Objetivos

* Coloque hologramas na malha de mapeamento espacial com base na posição da cabeça dos jogadores.

### <a name="instructions"></a>Instruções

* no **painel de Project** , navegue até a pasta **Hologramas** .
* Arraste e solte o **CustomSpatialMapping** pré-fabricado na **hierarquia**.
* no **painel de Project** , navegue até a pasta **Scripts** .
* Clique duas vezes no script **AppStateManager** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* no **painel de Project** , navegue até a pasta **Scripts** .
* Clique duas vezes no script **HologramPlacement** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Implantar e desfrutar**

* crie e implante o projeto em seus dispositivos HoloLens.
* Quando o aplicativo estiver pronto, aguarde um círculo e observe como o EnergyHub aparece no centro de todos.
* Toque para posicionar o EnergyHub.
* Experimente o comando de voz "redefinir destino" para escolher o EnergyHub de backup e trabalhar juntos como um grupo para mover o holograma para um novo local.

## <a name="chapter-6---real-world-physics"></a>Capítulo 6-Real-World física

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

Neste capítulo, adicionaremos hologramas que separam superfícies do mundo real. Assista ao seu espaço preencha com projetos iniciados por você e seus amigos!

### <a name="objectives"></a>Objetivos

* Inicie o projéteis que salta as superfícies do mundo real.
* Compartilhe o projéteis para que outros jogadores possam vê-los.

### <a name="instructions"></a>Instruções

* Na **hierarquia** , selecione o objeto **hologramacollection** .
* No **Inspetor** , clique em **Adicionar componente**.
* Na caixa de pesquisa, digite **Projectile Launcher**. Selecione o resultado da pesquisa.

**Implantar e desfrutar**

* crie e implante em seus dispositivos HoloLens.
* Quando o aplicativo estiver em execução em todos os dispositivos, execute um toque de ar para iniciar o Projectile em superfícies do mundo real.
* Veja o que acontece quando seu Projectile colide com o Avatar de outro jogador!

## <a name="chapter-7---grand-finale"></a>Capítulo 7 – final geral

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

Neste capítulo, vamos descobrir um portal que só pode ser descoberto com a colaboração.

### <a name="objectives"></a>Objetivos

* Trabalhe em conjunto para iniciar o projéteis suficiente na âncora para descobrir um portal secreto!

### <a name="instructions"></a>Instruções

* no **painel de Project** , navegue até a pasta **Hologramas** .
* Arraste e solte o ativo **Underworld** como um **filho de hologramacollection**.
* Com o **hologramacollection** selecionado, clique no botão **Adicionar componente** no **Inspetor**.
* No menu, digite na caixa de pesquisa **ExplodeTarget**. Selecione o resultado da pesquisa.
* Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **EnergyHub** para o campo de **destino** no **Inspetor**.
* Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **Underworld** para o campo **Underworld** no **Inspetor**.

**Implantar e desfrutar**

* crie e implante em seus dispositivos HoloLens.
* Quando o aplicativo for iniciado, colabore em conjunto para iniciar o projéteis no EnergyHub.
* Quando o Underworld for exibido, inicie projéteis em Underworld robots (pressione um robô três vezes para diversão extra).