---
title: Guia de configuração da realidade misturada
description: Documentação para configurar o MRTK no Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143573"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Guia de configuração do perfil do reality Toolkit misto

![Logotipo do MRTK](../features/images/MRTK_Logo_Rev.png)

O kit de ferramentas de realidade misturada centraliza a maior parte da configuração necessária para gerenciar o kit de ferramentas o máximo possível (exceto para "coisas" de tempo de execução verdadeiras).

Este guia é uma explicação simples para cada uma das telas de perfil de configuração disponíveis atualmente para o kit de ferramentas.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>O principal Perfil de configuração do kit de ferramentas de realidade misturada

O principal Perfil de configuração, que é anexado ao gameobject *MixedRealityToolkit* em sua cena, fornece o ponto de entrada principal para o kit de ferramentas em seu projeto.

> [!NOTE]
> O kit de ferramentas de realidade misturada "bloqueia" as telas de configuração padrão para garantir que você sempre tenha um ponto de partida comum para seu projeto e seja incentivado a começar a definir suas próprias configurações à medida que seu projeto evolui. A configuração MRTK não é editável durante o modo de reprodução.

![Perfil de configuração do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Todos os perfis "padrão" do kit de ferramentas de realidade misturada podem ser encontrados no projeto do SDK na pasta ativos/MRTK/SDK/perfis.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile é otimizado para o HoloLens 2. Consulte [perfis](../features/profiles/profiles.md) para obter os detalhes.

Ao abrir o principal Perfil de configuração do kit de ferramentas de realidade misturada, você verá a tela a seguir no Inspetor:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Se você selecionar um ativo MixedRealityToolkitConfigurationProfile sem o MixedRealityToolkit na cena, ele perguntará se você deseja que o MRTK configure automaticamente a cena para você. Isso é opcional, no entanto, deve haver um objeto MixedRealityToolkit ativo na cena para acessar todas as telas de configuração.

Isso abriga a configuração atual de tempo de execução ativo para o projeto.

A partir daqui, você pode navegar para todos os perfis de configuração para o MRTK, incluindo:

- [Guia de configuração do perfil do reality Toolkit misto](#mixed-reality-toolkit-profile-configuration-guide)
  - [O principal Perfil de configuração do kit de ferramentas de realidade misturada](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Configurações da experiência](#experience-settings)
  - [Configurações da câmera](#camera-settings)
  - [Configurações do sistema de entrada](#input-system-settings)
  - [Configurações de visualização de limite](#boundary-visualization-settings)
  - [Seleção do sistema de teletransporte](#teleportation-system-selection)
  - [Configurações de reconhecimento espacial](#spatial-awareness-settings)
  - [Configurações de diagnóstico](#diagnostics-settings)
  - [Configurações do sistema de cena](#scene-system-settings)
  - [Configurações de serviços adicionais](#additional-services-settings)
  - [Configurações de ações de entrada](#input-actions-settings)
  - [Regras de ações de entrada](#input-actions-rules)
  - [Configuração do ponteiro](#pointer-configuration)
  - [Configuração de gestos](#gestures-configuration)
  - [Comandos de fala](#speech-commands)
  - [Configuração de mapeamento do controlador](#controller-mapping-configuration)
  - [Configurações de visualização do controlador](#controller-visualization-settings)
  - [Utilitários do editor](#editor-utilities)
    - [Inspetores de serviço](#service-inspectors)
    - [Renderização de buffer de profundidade](#depth-buffer-renderer)
  - [Alterando perfis em runtime](#changing-profiles-at-runtime)
    - [Opção de perfil de inicialização do MRTK](#pre-mrtk-initialization-profile-switch)
    - [Opção de perfil ativo](#active-profile-switch)
  - [Consulte também](#see-also)

Esses perfis de configuração são detalhados abaixo em suas seções relevantes:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Configurações da experiência

Localizada na página principal de configuração do kit de ferramentas de realidade misturada, essa configuração define a operação padrão da [escala de ambiente da realidade misturada](/windows/mixed-reality/coordinate-systems-in-unity) para o seu projeto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Configurações da câmera

As configurações da câmera definem como a câmera será configurada para o projeto de realidade misturada, definindo as configurações de recorte genérico, qualidade e transparência.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Configurações do sistema de entrada

O projeto de realidade misturada fornece um sistema de entrada robusto e bem treinado para rotear todos os eventos de entrada em relação ao projeto que é selecionado por padrão.

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

O projeto de realidade mista fornece um sistema de teleportabilidade completo para gerenciar eventos de teleportação no projeto que é selecionado por padrão.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Configurações de conscientização espacial

O projeto de realidade misturada fornece um sistema de conscientização espacial recriado para trabalhar com sistemas de verificação espacial no projeto que é selecionado por padrão.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

A configuração de reconhecimento espacial do kit de ferramentas de realidade misturada permite que você personalize a forma como o sistema é iniciado, seja automaticamente quando o aplicativo é iniciado ou mais tarde de forma programática, bem como a definição das extensões para o campo de exibição.

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

Uma das áreas mais avançadas do kit de ferramentas de realidade misturada é sua implementação de [padrão de localizador de serviço](https://en.wikipedia.org/wiki/Service_locator_pattern) que permite o registro de qualquer "serviço" com a estrutura. Isso permite que a estrutura seja estendida com novos recursos/sistemas facilmente, mas também permite que os projetos aproveitem esses recursos para registrar seus próprios componentes de tempo de execução.

Qualquer serviço registrado ainda Obtém a vantagem total de todos os eventos do Unity, sem a sobrecarga e o custo da implementação de padrões de desajeitado ou monocomportamento. Isso permite componentes C# puros sem sobrecarga de cena para executar processos em primeiro plano e em segundo plano, por exemplo, gerar sistemas, lógica de jogo de runtime ou praticamente qualquer outra coisa.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Configurações de ações de entrada

As ações de entrada fornecem uma maneira de abstrair quaisquer interações físicas e entradas de um projeto de runtime. Toda a entrada física (de controladores/mãos/mouse/etc) é convertida em em uma ação de entrada lógica para uso em seu projeto de runtime. Isso garante que, independentemente de onde a entrada venha, seu projeto simplesmente implementa essas ações como "Coisas a fazer" ou "Interagir com" em suas cenas.

Para criar uma nova ação de entrada, basta clicar no botão "Adicionar uma nova ação" e inserir um nome de texto amigável para o que ela representa. Em seguida, você só precisa selecionar um eixo (o tipo de dados) ao qual a ação deve ser transmitida ou, no caso de controladores físicos, o tipo de entrada física ao qual ele pode ser anexado, por exemplo:

| Restrição de eixo | Tipo de Dados | Descrição | Uso de exemplo |
| :--- | :--- | :--- | :--- |
| Nenhum | Sem dados | Usado para uma ação ou evento vazio | Gatilho de evento |
| Bruto (reservado) | objeto | Reservado para uso futuro | N/D |
| Digital | bool | Um booliana em dados de tipo de ou para fora | Um botão do controlador |
| Eixo único | FLOAT | Um único valor de dados de precisão | Uma entrada de intervalo, por exemplo, um gatilho |
| Eixo duplo | Vector2 | Uma data de tipo float duplo para vários eixos | Um Dpad ou thumbstick |
| Posição de três dof | Vector3 | Dados de tipo posicional de com 3 eixos float | controlador de apenas estilo de posição 3D |
| Rotação de três DOF | Quatérnion | Entrada somente rotacional com 4 eixos float | Um controlador de três graus estilo, por exemplo, Oculus go Controller |
| Seis DOF | Pose de realidade misturada (Vector3, Quaternion) | Uma entrada de estilo de posição e rotação com componentes Vector3 e Quaternion | Um ponteiro ou controlador de movimento |

Eventos que utilizam ações de entrada não são limitados a controladores físicos e ainda podem ser utilizados dentro do projeto para que os efeitos de tempo de execução gerem novas ações.

> [!NOTE]
> As ações de entrada são um dos poucos componentes que não são editáveis em tempo de execução, são apenas uma configuração de tempo de design. Esse perfil não deve ser trocado enquanto o projeto está em execução devido à dependência da estrutura (e de seus projetos) na geração da ID para cada ação.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regras de ações de entrada

As regras de ação de entrada fornecem uma maneira de converter automaticamente um evento gerado para uma ação de entrada em ações diferentes com base em seu valor de dados. Eles são gerenciados diretamente dentro da estrutura e não incorrem em custos de desempenho.

Por exemplo, converter o único evento de entrada de eixo duplo de um DPad em para as 4 correspondentes às ações "Dpad up"/"DPad Down"/"Dpad Left"/"Dpad Right" (conforme mostrado na imagem abaixo).

Isso também pode ser feito em seu próprio código. No entanto, visto que esse era um padrão muito comum, a estrutura fornece um mecanismo para fazer isso "pronto para uso"

As regras de ação de entrada podem ser configuradas para qualquer um dos eixos de entrada disponíveis. No entanto, as ações de entrada de um tipo de eixo podem ser convertidas em outra ação de entrada do mesmo tipo de eixo. Você pode mapear uma ação de eixo duplo para outra ação de eixo duplo, mas não para uma ação digital ou nenhuma.

![Perfil de regras de ação de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configuração do ponteiro

Ponteiros são usados para impulsionar a interatividade na cena de qualquer dispositivo de entrada, dando uma direção e um teste de ocorrência com qualquer objeto em uma cena (que tem um colisor anexado ou é um componente da interface do usuário). Os ponteiros são configurados automaticamente por padrão para controladores, headsets (foco/foco) e entrada de mouse/toque.

Os ponteiros também podem ser visualizados na cena ativa usando um dos muitos componentes de linha fornecidos pelo Kit de Ferramentas de Realidade Misturada ou qualquer um dos seus se implementarem a interface IMixedRealityPointer do MRTK.

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
> A implementação atual de Gestos é apenas para o HoloLens e será aprimorada para outros sistemas à medida que eles são adicionados ao Kit de Ferramentas no futuro (ainda não há datas).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandos de fala

Assim como os gestos, algumas plataformas de runtime também fornecem funcionalidades de "Conversão de Fala em Texto" inteligentes com a capacidade de gerar comandos que podem ser recebidos por um projeto do Unity. Esse perfil de configuração permite que você configure o seguinte:

1. Configurações gerais – "comportamento inicial" definido como início automático ou início manual determina se o KeywordRecognizer deve ser inicializado na inicialização do sistema de entrada ou permite que o projeto decida quando inicializar o KeywordRecognizer. "Nível de confiança de reconhecimento" é usado para inicializar a [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) do Unity
2. Comandos de fala – registra "palavras" e as converte em ações de entrada que podem ser recebidas pelo seu projeto. Eles também podem ser anexados a ações de teclado, se necessário.

> [!IMPORTANT]
> Atualmente, o sistema só dá suporte à fala quando executado em plataformas Windows 10, por exemplo, HoloLens e Windows 10 desktop e será aprimorado para outros sistemas à medida que eles forem adicionados ao MRTK no futuro (sem datas ainda).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configuração de mapeamento de controlador

Uma das telas principais de configuração do kit de ferramentas de realidade misturada é a capacidade de configurar e mapear os vários tipos de controladores que podem ser utilizados pelo seu projeto.

A tela de configuração abaixo permite que você configure qualquer um dos controladores atualmente reconhecidos pelo kit de ferramentas.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

O MRTK fornece uma configuração padrão para os seguintes controladores/sistemas:

- Mouse (incluindo suporte a mouse espacial 3D)
- Tela touch
- Controladores do Xbox
- Controladores de realidade do Windows Mixed
- Gestos do HoloLens
- Controladores de varinha Naopak do HTC
- Controladores de toque Oculus
- Controlador remoto Oculus
- Dispositivos OpenVR genéricos (somente para usuários avançados)

Clicar na imagem para qualquer um dos sistemas de controlador pré-criados permite que você configure uma única ação de entrada para todas as suas entradas correspondentes, por exemplo, consulte a tela de configuração do Oculus Touch Controller abaixo:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

Também há uma tela avançada para configurar outros controladores de entrada OpenVR ou Unity que não são identificados acima.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Configurações de visualização do controlador

Além do mapeamento do controlador, um perfil de configuração separado é fornecido para personalizar como os controladores são apresentados em suas cenas.

Isso pode ser configurado em um "Global" (todas as instâncias de um controlador para uma mão específica) ou específico para um tipo/mão de controlador individual.

O MRTK também dá suporte a modelos nativos de controlador do SDK para Windows Mixed Reality e OpenVR. Eles são carregados como GameObjects em sua cena e posicionados usando o acompanhamento do controlador da plataforma.

Se a representação do controlador na cena precisar ser deslocada da posição do controlador físico, basta definir esse deslocamento em relação ao pré-padrão do modelo do controlador (por exemplo, definir a posição de transformação do pré-padrão do controlador com uma posição de deslocamento).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilitários do editor

Os utilitários a seguir funcionam somente no editor e são úteis para melhorar a produtividade do desenvolvimento.

![Utilitários de configuração do Editor do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Inspetores de serviço

Os Inspetores de Serviço são um recurso somente editor que gera objetos na cena que representam serviços ativos. Selecionar esses objetos exibe inspetores que oferecem links de documentação, controle sobre visualizações do editor e insights sobre o estado do serviço.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Você pode habilitar inspetores de serviço marcando *Usar Inspetores de Serviço* em *Configurações do Editor* no Perfil de Configuração.

### <a name="depth-buffer-renderer"></a>Renderização de buffer de profundidade

Compartilhar o buffer de profundidade com algumas plataformas de realidade misturada pode melhorar a [estabilização do holograma.](../performance/hologram-stabilization.md) Por exemplo, a Windows Mixed Reality pode modificar a cena renderizada por pixel para levar em conta os movimentos sutis de cabeça durante o tempo necessário para renderizar um quadro. No entanto, essas técnicas exigem buffers de profundidade com dados precisos para saber onde e a distância da geometria do usuário.

Para garantir que uma cena renderiza todos os dados *necessários* para o buffer de profundidade, os desenvolvedores podem alternar o recurso *Buffer* de Profundidade de Renderização em Configurações do Editor no Perfil de Configuração. Isso usará o buffer de profundidade atual e o processará como cor para a exibição de cena aplicando um efeito de pós-processamento, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , à câmera principal.

![Utilitário ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>de buffer de profundidade de renderização o cilindro azul na cena tem um material com ZWrite desativado, portanto, nenhum dado de profundidade é gravado</sup>

## <a name="changing-profiles-at-runtime"></a>Alterando perfis em tempo de execução

É possível atualizar perfis em tempo de execução e, em geral, há dois cenários e horários diferentes nos quais isso é útil:

1. **Opção de perfil de inicialização MRTK**: na inicialização, antes que o MRTK seja inicializado e o perfil se torne ativo, substituindo o perfil ainda não utilizado para habilitar/desabilitar recursos diferentes com base nos recursos do dispositivo. Por exemplo, se a experiência estiver em execução em VR que não tem um hardware de mapeamento espacial, provavelmente não fará sentido ter o componente de mapeamento espacial habilitado.
1. **Opção de perfil ativo**: após a inicialização, depois que o MRTK for inicializado e um perfil se tornar ativo, alternando o perfil atualmente em uso para alterar a forma com que determinados recursos se comportam. Por exemplo, pode haver uma subexperiência específica no aplicativo que desejasse os ponteiros de extrema mão completamente removidos.

### <a name="pre-mrtk-initialization-profile-switch"></a>Opção de perfil de inicialização MRTK

Isso pode ser feito anexando um monocomportamento (exemplo abaixo), que é executado antes da inicialização do MRTK (ou seja, ativo ()). Observe que o script (ou seja, chamada para `SetProfileBeforeInitialization` ) precisa ser executado antes do `MixedRealityToolkit` script, o que pode ser obtido definindo [as configurações de ordem de execução de script](https://docs.unity3d.com/Manual/class-MonoManager.html).

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

Em vez de "profileToUse", é possível ter algum conjunto arbitrário de perfis que se aplicam a plataformas específicas (por exemplo, um para o HoloLens 1, um para VR, um para o HoloLens 2, etc.). É possível usar vários outros indicadores (por exemplo https://docs.unity3d.com/ScriptReference/SystemInfo.html , ou se a câmera é opaca/transparente), para descobrir qual perfil deve ser carregado.

### <a name="active-profile-switch"></a>Opção de perfil ativo

Isso pode ser feito definindo a `MixedRealityToolkit.Instance.ActiveProfile` propriedade para um novo perfil, substituindo o perfil ativo.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Observe que, ao definir durante o runtime, a destruição dos serviços em execução no momento ocorrerá após o último LateUpdate() de todos os serviços, e a insta instaência e a inicialização dos serviços associados ao novo perfil ocorrerão antes da primeira Atualização() de todos os `ActiveProfile` serviços.

Um aplicativo perceptível pode ocorrer durante esse processo. Além disso, qualquer script com prioridade mais alta do `MixedRealityToolkit` que o script pode inserir sua Atualização antes que o novo perfil seja configurado corretamente. Confira [Configurações de Ordem de Execução de](https://docs.unity3d.com/Manual/class-MonoManager.html) Script para obter mais informações sobre a prioridade do script.

No processo de alternação de perfil, a câmera da interface do usuário existente permanecerá inalterada, garantindo que os componentes da interface do usuário do Unity que exigem tela ainda funcionem após a opção.

## <a name="see-also"></a>Confira também

- [Estabilização de holograma](../performance/hologram-stabilization.md)