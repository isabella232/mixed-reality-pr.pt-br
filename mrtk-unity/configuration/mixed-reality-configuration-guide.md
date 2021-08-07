---
title: Guia de configuração do perfil do MRTK
description: Documentação para configurar o MRTK no Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: e18695610b5e07c4f811e7c43bc13607857a9459407f9b16f39d4f7350f354e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214862"
---
# <a name="mrtk-profile-configuration-guide"></a>Guia de configuração do perfil do MRTK

a realidade misturada Toolkit centralizar a maior parte da configuração necessária para gerenciar o kit de ferramentas o mais possível (exceto para "coisas" de tempo de execução verdadeiras).

Este guia é uma explicação simples para cada uma das telas de perfil de configuração disponíveis atualmente para o kit de ferramentas.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>a principal realidade misturada Toolkit perfil de configuração

o principal perfil de configuração, que é anexado ao gameobject *MixedRealityToolkit* em sua cena, fornece o ponto de entrada principal para o Toolkit em seu projeto.

> [!NOTE]
> a realidade misturada Toolkit "bloqueia" as telas de configuração padrão para garantir que você sempre tenha um ponto de partida comum para seu projeto e seja incentivado a começar a definir suas próprias configurações à medida que seu projeto evolui. A configuração MRTK não é editável durante o modo de reprodução.

![Perfil de configuração do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

todos os perfis "padrão" para a realidade misturada Toolkit podem ser encontrados no projeto do SDK na pasta ativos/MRTK/SDK/perfis.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile é otimizado para o HoloLens 2. Consulte [perfis](../features/profiles/profiles.md) para obter os detalhes.

ao abrir a realidade mista principal Toolkit perfil de configuração, você verá a seguinte tela no inspetor:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Se você selecionar um ativo MixedRealityToolkitConfigurationProfile sem o MixedRealityToolkit na cena, ele perguntará se você deseja que o MRTK configure automaticamente a cena para você. Isso é opcional, no entanto, deve haver um objeto MixedRealityToolkit ativo na cena para acessar todas as telas de configuração.

Isso abriga a configuração atual de tempo de execução ativo para o projeto.

A partir daqui, você pode navegar para todos os perfis de configuração para o MRTK, incluindo:

- [guia de configuração do perfil da realidade mista Toolkit](#mrtk-profile-configuration-guide)
  - [a principal realidade misturada Toolkit perfil de configuração](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Configurações da experiência](#experience-settings)
  - [Configurações da câmera](#camera-settings)
  - [Configurações do sistema de entrada](#input-system-settings)
  - [Configurações de visualização de limite](#boundary-visualization-settings)
  - [Seleção do sistema de teleportabilidade](#teleportation-system-selection)
  - [Configurações de conscientização espacial](#spatial-awareness-settings)
  - [Configurações de diagnóstico](#diagnostics-settings)
  - [Configurações do sistema de cena](#scene-system-settings)
  - [Configurações de serviços adicionais](#additional-services-settings)
  - [Configurações de ações de entrada](#input-actions-settings)
  - [Regras de ações de entrada](#input-actions-rules)
  - [Configuração do ponteiro](#pointer-configuration)
  - [Configuração de gestos](#gestures-configuration)
  - [Comandos de fala](#speech-commands)
  - [Configuração de mapeamento de controlador](#controller-mapping-configuration)
  - [Configurações de visualização do controlador](#controller-visualization-settings)
  - [Utilitários do editor](#editor-utilities)
    - [Inspetores de serviço](#service-inspectors)
    - [Renderizador de buffer de profundidade](#depth-buffer-renderer)
  - [Alterando perfis em tempo de execução](#changing-profiles-at-runtime)
    - [Opção de perfil de inicialização MRTK](#pre-mrtk-initialization-profile-switch)
    - [Opção de perfil ativo](#active-profile-switch)
  - [Consulte também](#see-also)

Esses perfis de configuração são detalhados abaixo em suas seções relevantes:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Configurações da experiência

localizada na página principal de configuração Toolkit reality, essa configuração define a operação padrão da [escala de ambiente da realidade misturada](/windows/mixed-reality/coordinate-systems-in-unity) para o seu projeto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Configurações da câmera

As configurações da câmera definem como a câmera será configurada para o projeto de realidade misturada, definindo as configurações de recorte genérico, qualidade e transparência.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Configurações do sistema de entrada

a realidade misturada Project fornece um sistema de entrada robusto e bem treinado para rotear todos os eventos de entrada em todo o projeto que é selecionado por padrão.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Por trás do sistema de entrada fornecido pelo MRTK são vários outros sistemas, eles ajudam a impulsionar e gerenciar o complexo weavings necessário para abstrair as complexidades de uma estrutura de realidade mista de várias plataformas.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Cada um dos perfis individuais é detalhado abaixo:

- Configurações de foco
- [Configurações de ações de entrada](#input-actions-settings)
- [Regras de ações de entrada](#input-actions-rules)
- [Configuração do ponteiro](#pointer-configuration)
- [Configuração de gestos](#gestures-configuration)
- [Comandos de fala](#speech-commands)
- [Configuração de mapeamento de controlador](#controller-mapping-configuration)
- [Configurações de visualização do controlador](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Configurações de visualização de limite

O sistema de limite traduz o limite percebido relatado pelo sistema de limite/guardião de plataformas subjacentes. A configuração do Visualizador de limite fornece a capacidade de mostrar automaticamente o limite registrado em sua cena em relação à posição do usuário. O limite também reagirá/será atualizado com base em onde o usuário portará dentro da cena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Seleção do sistema de teleportabilidade

a realidade misturada Project fornece um sistema de teleportabilidade completo para gerenciar eventos de teleportação no projeto que é selecionado por padrão.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Configurações de conscientização espacial

a realidade misturada Project fornece um sistema de conscientização espacial recriado para trabalhar com sistemas de verificação espacial no projeto que é selecionado por padrão.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

a realidade misturada Toolkit configuração de conscientização espacial permite que você personalize a forma como o sistema é iniciado, se ele é automaticamente quando o aplicativo inicia ou posteriormente de forma programática, bem como a definição das extensões para o campo de exibição.

Ele também permite que você defina as configurações de malha e superfície, personalizando ainda mais a forma como o seu projeto compreende o ambiente em relação a você.

Isso só é aplicável a dispositivos que podem fornecer um ambiente examinado.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Configurações de diagnóstico

Um recurso opcional, mas altamente útil do MRTK, é a funcionalidade de diagnóstico de plug-in.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

O perfil de diagnóstico fornece vários sistemas simples para monitorar enquanto o projeto está em execução, incluindo uma opção de ligar/desligar útil para habilitar/desabilitar o painel de exibição na cena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Configurações do sistema de cena

O MRTK fornece esse serviço opcional para ajudá-lo a gerenciar o carregamento/descarregamento de uma cena aditiva complexa. Para decidir se o sistema de cena seria uma boa opção para seu projeto, leia o [Guia de introdução do sistema de cena.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Configurações de serviços adicionais

uma das áreas mais avançadas da realidade misturada Toolkit é sua implementação de [padrão de localizador de serviço](https://en.wikipedia.org/wiki/Service_locator_pattern) que permite o registro de qualquer "serviço" com a estrutura. Isso permite que a estrutura seja estendida com novos recursos/sistemas facilmente, mas também permite que os projetos aproveitem esses recursos para registrar seus próprios componentes de tempo de execução.

Qualquer serviço registrado ainda Obtém a vantagem total de todos os eventos do Unity, sem a sobrecarga e o custo da implementação de padrões de desajeitado ou monocomportamento. Isso permite componentes puros do C# sem sobrecarga de cena para a execução de processos em primeiro plano e em segundo plano, por exemplo, sistemas de geração, lógica de jogo em tempo de execução ou praticamente qualquer outra coisa.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Configurações de ações de entrada

As ações de entrada fornecem uma maneira de abstrair quaisquer interações físicas e entradas de um projeto de tempo de execução. Todas as entradas físicas (de controladores/mãos/mouse/etc.) são convertidas em uma ação de entrada lógica para uso em seu projeto de tempo de execução. Isso garante que, independentemente de onde venha a entrada, seu projeto simplesmente implemente essas ações como "coisas para fazer" ou "interagir com" em seus bastidores.

Para criar uma nova ação de entrada, basta clicar no botão "adicionar uma nova ação" e inserir um nome de texto amigável para o que ele representa. Em seguida, você só precisa selecionar um eixo (o tipo de dados) que a ação deve transmitir, ou no caso de controladores físicos, o tipo de entrada física ao qual ele pode ser anexado, por exemplo:

| Restrição de eixo | Tipo de Dados | Descrição | Uso de exemplo |
| :--- | :--- | :--- | :--- |
| Nenhum | Sem dados | Usado para uma ação ou evento vazio | Gatilho de evento |
| Bruto (reservado) | objeto | Reservado para uso futuro | N/D |
| Digital | bool | Um booliana em dados de tipo de ou para fora | Um botão do controlador |
| Eixo único | FLOAT | Um único valor de dados de precisão | Uma entrada de intervalo, por exemplo, um gatilho |
| Eixo duplo | Vector2 | Uma data de tipo float duplo para vários eixos | Um Dpad ou thumbstick |
| Posição de três dof | Vector3 | Dados de tipo posicional de com 3 eixos flutuantes | Controlador somente de estilo de posição 3D |
| Rotação de três dof | Quatérnion | Entrada somente rotacional com quatro eixos flutuantes | Um controlador de estilo de três graus, por exemplo, o controlador Oculus Go |
| Seis Dof | Pose de realidade misturada (Vector3, Quatternion) | Uma entrada de estilo de posição e rotação com componentes Vector3 e Quaternion | Um controlador de movimento ou ponteiro |

Eventos que utilizam ações de entrada não são limitados a controladores físicos e ainda podem ser utilizados dentro do projeto para que os efeitos de runtime gerem novas ações.

> [!NOTE]
> As ações de entrada são um dos poucos componentes que não são editáveis em runtime, são apenas uma configuração de tempo de design. Esse perfil não deve ser trocado enquanto o projeto estiver em execução devido à dependência da estrutura (e seus projetos) nas IDs geradas para cada ação.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regras de ações de entrada

As regras de ação de entrada fornecem uma maneira de converter automaticamente um evento gerado para uma ação de entrada em para ações diferentes com base em seu valor de dados. Eles são gerenciados perfeitamente dentro da estrutura e não incorrem em custos de desempenho.

Por exemplo, convertendo o único evento de entrada de eixo duplo de um DPad em para as quatro ações correspondentes "Dpad Up" /"DPad Down" /"Dpad Left" /"Dpad Right" (conforme mostrado na imagem abaixo).

Isso também pode ser feito em seu próprio código. No entanto, como esse era um padrão muito comum, a estrutura fornece um mecanismo para fazer isso "fora da caixa"

As regras de ação de entrada podem ser configuradas para qualquer um dos eixos de entrada disponíveis. No entanto, as ações de entrada de um tipo de eixo podem ser convertida em outra ação de entrada do mesmo tipo de eixo. Você pode mapear uma ação de eixo duplo para outra ação de eixo duplo, mas não para uma ação digital ou nenhuma.

![Perfil de regras de ação de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configuração do ponteiro

Ponteiros são usados para impulsionar a interatividade na cena de qualquer dispositivo de entrada, dando uma direção e um teste de ocorrência com qualquer objeto em uma cena (que tem um colisor anexado ou é um componente da interface do usuário). Os ponteiros são configurados automaticamente por padrão para controladores, headsets (foco/foco) e entrada de mouse/toque.

Os ponteiros também podem ser visualizados na cena ativa usando um dos muitos componentes de linha fornecidos pelo Toolkit de Realidade Misturada ou qualquer um dos seus se implementarem a interface IMixedRealityPointer do MRTK.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Apontando extensão: determina a extensão de apontar global para todos os ponteiros, incluindo o olhar.
- Apontando máscaras de camada raycast: determina em quais camadas os ponteiros serão raycast.
- Depurar raios que apontam para desenho: um auxiliar de depuração para visualizar os raios usados para raycasting.
- Cores dos raios de desenho de depuração: um conjunto de cores a ser usado para visualização.
- Pré-fab do cursor de olhar: facilita a especificação de um cursor de olhar global para qualquer cena.

Há um botão auxiliar adicional para ir rapidamente para o Provedor de Foco para substituir alguns valores específicos para o Foco, se necessário.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configuração de gestos

Gestos são uma implementação específica do sistema que permite atribuir ações de entrada aos vários métodos de entrada "Gesto" fornecidos por vários SDKs (por exemplo, HoloLens).

> [!NOTE]
> A implementação atual de Gestos é apenas para o HoloLens e será aprimorada para outros sistemas à medida que eles são adicionados ao Toolkit no futuro (ainda não há datas).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandos de fala

Assim como os gestos, algumas plataformas de runtime também fornecem funcionalidades de "Conversão de Fala em Texto" inteligentes com a capacidade de gerar comandos que podem ser recebidos por um projeto do Unity. Esse perfil de configuração permite que você configure o seguinte:

1. Geral Configurações – "Comportamento de Início" definido como Início Automático ou Início Manual determina se é preciso inicializar KeywordRecognizer na inicialização do sistema de entrada ou permitir que o projeto decida quando inicializar o KeywordRecognizer. O "Nível de Confiança de Reconhecimento" é usado para inicializar a [API KeywordRecognizer do](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity
2. Comandos de Fala – registra "palavras" e as converte em ações de entrada que podem ser recebidas pelo seu projeto. Eles também podem ser anexados às ações de teclado, se necessário.

> [!IMPORTANT]
> Atualmente, o sistema dá suporte apenas à fala durante a execução em plataformas Windows 10, por exemplo, HoloLens e Windows 10 desktop e será aprimorado para outros sistemas à medida que eles são adicionados ao MRTK no futuro (ainda não há datas).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configuração de mapeamento do controlador

Uma das principais telas de configuração para o Toolkit realidade misturada é a capacidade de configurar e mapear os vários tipos de controladores que podem ser utilizados pelo seu projeto.

A tela de configuração abaixo permite que você configure qualquer um dos controladores atualmente reconhecidos pelo kit de ferramentas.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

O MRTK fornece uma configuração padrão para os seguintes controladores/sistemas:

- Mouse (incluindo suporte ao mouse espacial 3D)
- Tela touch
- Controladores Xbox
- Windows Mixed Reality controladores
- HoloLens Gestos
- Controladores de controladores HTC Vive
- Controladores touch do Oculus
- Controlador remoto do Oculus
- Dispositivos OpenVR genéricos (somente usuários avançados)

Clicar na Imagem para qualquer um dos sistemas de controlador pré-criado permite configurar uma única ação de entrada para todas as suas entradas correspondentes, por exemplo, consulte a tela de configuração do controlador Oculus Touch abaixo:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

Também há uma tela avançada para configurar outros controladores de entrada OpenVR ou Unity que não são identificados acima.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Configurações de visualização do controlador

Além do mapeamento do controlador, um perfil de configuração separado é fornecido para personalizar como os controladores são apresentados em suas cenas.

Isso pode ser configurado em um "Global" (todas as instâncias de um controlador para uma mão específica) ou específico para um tipo/mão de controlador individual.

O MRTK também dá suporte a modelos de controlador SDK nativos para Windows Mixed Reality e OpenVR. Eles são carregados como GameObjects em sua cena e posicionados usando o acompanhamento do controlador da plataforma.

Se a representação do controlador na cena precisar ser deslocada da posição do controlador físico, basta definir esse deslocamento em relação ao pré-padrão do modelo do controlador (por exemplo, definir a posição de transformação do pré-padrão do controlador com uma posição de deslocamento).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilitários do editor

Os utilitários a seguir funcionam somente no editor e são úteis para melhorar a produtividade do desenvolvimento.

![Utilitários de configuração do Editor do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Inspetores de serviço

Os Inspetores de Serviço são um recurso somente editor que gera objetos na cena que representam serviços ativos. Selecionar esses objetos exibe inspetores que oferecem links de documentação, controle sobre visualizações do editor e insights sobre o estado do serviço.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Você pode habilitar inspetores de serviço verificando *Usar Inspetores de Serviço* em Editor *Configurações* no Perfil de Configuração.

### <a name="depth-buffer-renderer"></a>Renderização de buffer de profundidade

Compartilhar o buffer de profundidade com algumas plataformas de realidade misturada pode melhorar a [estabilização do holograma.](../performance/hologram-stabilization.md) Por exemplo, a Windows Mixed Reality pode modificar a cena renderizada por pixel para levar em conta os movimentos sutis de cabeça durante o tempo necessário para renderizar um quadro. No entanto, essas técnicas exigem buffers de profundidade com dados precisos para saber onde e a distância da geometria do usuário.

Para garantir que uma cena renderiza todos os dados necessários para o buffer de profundidade, os desenvolvedores podem alternar o recurso *Buffer* de Profundidade de Renderização em *Editor Configurações* no Perfil de Configuração. Isso pegará o buffer de profundidade atual e o renderizará como cor para a exibição da cena aplicando um efeito pós-processamento, , à [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) câmera principal.

![Utilitário de buffer de profundidade de renderização O cilindro azul na cena tem um material com ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>ZWrite desligado para</sup> que nenhum dado de profundidade seja gravado

## <a name="changing-profiles-at-runtime"></a>Alterando perfis em runtime

É possível atualizar perfis em runtime e geralmente há dois cenários e horas diferentes nos quais isso é útil:

1. Opção de perfil de inicialização do **MRTK** anterior: na inicialização, antes que o MRTK seja inicializado e o perfil se torne ativo, substituindo o perfil ainda não em uso para habilitar/desabilitar diferentes recursos com base nas funcionalidades do dispositivo. Por exemplo, se a experiência estiver em execução em VR que não tem hardware de mapeamento espacial, provavelmente não fará sentido ter o componente de mapeamento espacial habilitado.
1. **Opção de perfil ativo:** após a inicialização, depois que o MRTK for inicializado e um perfil tiver se tornado ativo, alternar o perfil atualmente em uso para alterar a maneira como determinados recursos se comportam. Por exemplo, pode haver uma sub-experiência específica no aplicativo que deseja que os ponteiros de mão distante sejam completamente removidos.

### <a name="pre-mrtk-initialization-profile-switch"></a>Opção de perfil de inicialização do MRTK

Isso pode ser feito anexando um MonoBehaviour (exemplo abaixo) que é executado antes da inicialização do MRTK (ou seja, Awake()). Observe que o script (ou seja, chamada para ) precisa ser executado antes do script, o que pode ser obtido definindo as configurações de Ordem de Execução `SetProfileBeforeInitialization` `MixedRealityToolkit` de [Script](https://docs.unity3d.com/Manual/class-MonoManager.html).

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

Em vez de "profileToUse", é possível ter algum conjunto arbitrário de perfis que se aplicam a plataformas específicas (por exemplo, um para HoloLens 1, outro para VR, um para o HoloLens 2 etc.). É possível usar vários outros indicadores (por exemplo, ou se a câmera é ou não opaca/transparente) para descobrir qual perfil https://docs.unity3d.com/ScriptReference/SystemInfo.html carregar.

### <a name="active-profile-switch"></a>Opção de perfil ativo

Isso pode ser feito definindo `MixedRealityToolkit.Instance.ActiveProfile` a propriedade como um novo perfil substituindo o perfil ativo.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Observe que, ao definir durante o runtime, a destruição dos serviços em execução no momento ocorrerá após o último LateUpdate() de todos os serviços, e a insta instaência e a inicialização dos serviços associados ao novo perfil ocorrerão antes da primeira Atualização() de todos os `ActiveProfile` serviços.

Um aplicativo perceptível pode ocorrer durante esse processo. Além disso, qualquer script com prioridade mais alta do `MixedRealityToolkit` que o script pode inserir sua Atualização antes que o novo perfil seja configurado corretamente. Confira [Configurações de Ordem de Execução de](https://docs.unity3d.com/Manual/class-MonoManager.html) Script para obter mais informações sobre a prioridade do script.

No processo de alternação de perfil, a câmera da interface do usuário existente permanecerá inalterada, garantindo que os componentes da interface do usuário do Unity que exigem tela ainda funcionem após a opção.

## <a name="see-also"></a>Confira também

- [Estabilização do holograma](../performance/hologram-stabilization.md)
