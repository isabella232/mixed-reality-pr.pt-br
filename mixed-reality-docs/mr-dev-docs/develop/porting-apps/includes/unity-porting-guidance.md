---
ms.openlocfilehash: 487118403c2a8af1a6b54bc9aa9245fbe9d0568a
ms.sourcegitcommit: bec6029b2780c54cc04a45ef7ae5df3f5b4727c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96476500"
---
# <a name="project-settings"></a>[Configurações do projeto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Examine as etapas de portabilidade comuns listadas acima

Examine as etapas comuns listadas acima para verificar se o ambiente de desenvolvimento está configurado corretamente. Na etapa #3, se você estiver usando o Visual Studio, deverá selecionar o **desenvolvimento do jogo com** a carga de trabalho do Unity. Você pode cancelar a seleção do componente "editor do Unity opcional", já que você instalará uma versão mais recente do Unity na próxima etapa.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. atualize para a compilação pública mais recente do Unity com o suporte do Windows Sr
1. Baixe a [compilação pública mais recente recomendada do Unity](../../install-the-tools.md) com suporte misto à realidade.
2. Salve uma cópia do seu projeto antes de começar
3. Examine a [documentação](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponível no Unity em atualizando se seu projeto foi criado em uma versão mais antiga do Unity.
4. Siga as [instruções](https://docs.unity3d.com/Manual/APIUpdater.html) no site do Unity para usar o atualizador automático de API
5. Verifique e veja se há alterações adicionais que você precisa fazer para que seu projeto seja executado e trabalhe com quaisquer erros e avisos restantes. 

> [!Note] 
> Se você tiver um middleware do qual depende, verifique se está usando a versão mais recente (mais detalhes na etapa 3 abaixo).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. atualize seu middleware para as versões mais recentes

Com qualquer atualização do Unity, há uma boa chance de que você precise atualizar um ou mais pacotes de middleware dos quais seu jogo ou aplicativo depende. Além disso, estar atualizado com o middleware mais recente aumenta a probabilidade de sucesso ao longo do restante do processo de portabilidade.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Direcione seu aplicativo para ser executado no Win32

De dentro de seu aplicativo de Unity:

* Navegue até arquivo-> configurações de compilação
* Selecione "PC, Mac, Linux autônomo"
* Definir plataforma de destino como "Windows"
* Defina a arquitetura como "x86" selecione "alternar plataforma"

> [!NOTE] 
> Se seu aplicativo tiver quaisquer dependências de serviços específicos do dispositivo, como a realização de correspondência do fluxo, você precisará desabilitá-los nesta etapa. Você pode conectar-se aos serviços equivalentes que o Windows fornece posteriormente.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. configurar o hardware do Windows Mixed Reality
1. Examinar as etapas na [configuração do headset de imersão](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Saiba como [usar o simulador de realidade do Windows Mixed](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) e [navegar na página inicial do Windows Mixed Reality](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Direcione seu aplicativo para ser executado no Windows Mixed Reality
1. Primeiro, você deve remover ou compilar condicionalmente qualquer outro suporte de biblioteca específico para um determinado SDK do VR. Esses ativos freqüentemente alteram as configurações e propriedades em seu projeto de maneiras incompatíveis com outros SDKs de VR, como a realidade mista do Windows.
    * Por exemplo, se o seu projeto fizer referência ao SDK do SteamVR, você precisará atualizar seu projeto para usar as APIs comuns de VR do Unity que dão suporte tanto ao Windows Mixed Reality quanto ao SteamVR.
    * Etapas específicas para excluir condicionalmente outros SDKs de VR serão disponibilizadas em breve.
2. Em seu projeto do Unity, [direcione o SDK do Windows 10](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Para cada cena, [Configure a câmera](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. Use o estágio para posicionar o conteúdo no chão

Você pode criar experiências de realidade misturadas em uma ampla variedade de [escalas de experiência](../../../design/coordinate-systems.md).

Se você estiver portando uma **experiência de escala em** posição, deverá garantir que o Unity esteja definido para o tipo de espaço de rastreamento **estacionário** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Este código acima define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro de referência estacionário](../../../design/coordinate-systems.md#spatial-coordinate-systems). No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparece na frente do usuário quando o aplicativo é iniciado. Para recentralizar a origem colocada do usuário, você pode chamar o XR da Unity [. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Se você estiver portando uma experiência de **escala em pé** ou uma **experiência em escala de sala**, colocará o conteúdo em relação ao chão. Você se deparar com o andar do usuário usando o **[estágio espacial](../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução. Para essas experiências, você deve garantir que o Unity esteja definido como o tipo de espaço de rastreamento **RoomScale** . Embora RoomScale seja o padrão, você desejará defini-lo explicitamente e garantir que você se torne verdadeiro, para detectar situações em que o usuário moveu o computador para fora da sala que eles calibraram:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão. A origem em (0, 0) será o local específico no andar em que o usuário se baseou durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.

No código de script, você pode chamar o método TryGetGeometry em você é o tipo UnityEngine. experimental. XR. limite para obter um polígono de limite, especificando um tipo de limite de TrackedArea. Se o usuário definiu um limite (você obtém uma lista de vértices), é seguro fornecer uma **experiência de escala de sala** ao usuário, na qual eles podem percorrer a cena que você criar.

O sistema irá renderizar automaticamente o limite quando o usuário o aproximar. Seu aplicativo não precisa usar este polígono para renderizar o limite em si.

Para obter mais informações, consulte a página [coordenar sistemas no Unity](../../unity/coordinate-systems-in-unity.md) .

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Exemplo de resultados:

![Exemplo de resultados](../../porting-apps/images/largestrectangle-400px.jpg)

O algoritmo se baseia em um blog por Daniel Smilkov: [retângulo maior em um polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. trabalhar com seu modelo de entrada

Cada jogo ou aplicativo direcionado a um HMD existente terá um conjunto de entradas que ele manipula, tipos de entradas que ele precisa para a experiência e APIs específicas que ele chama para obter essas entradas. Investimos na tentativa de torná-lo tão simples e direto possível de aproveitar as informações disponíveis no Windows Mixed Reality.

Leia o [Guia de porta de entrada para o Unity](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) na guia adjacente para obter detalhes sobre como a realidade mista do Windows expõe a entrada e como isso é mapeado para o que seu aplicativo pode fazer hoje.

### <a name="9-performance-testing-and-tuning"></a>9. testes e ajustes de desempenho

A realidade mista do Windows estará disponível em uma ampla classe de dispositivos, desde PCs de jogos de ponta, até os principais PCs de mercado. Dependendo do mercado que você está direcionando, há uma diferença significativa nos orçamentos de computação e gráficos disponíveis para seu aplicativo. Durante esse exercício de portabilidade, você provavelmente está aproveitando um PC Premium e teve orçamentos de computação e gráficos significativos disponíveis para seu aplicativo. Se desejar disponibilizar seu aplicativo para um público mais amplo, você deverá testar e criar o perfil de seu aplicativo no [hardware representativo que deseja direcionar](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

O [Unity](https://docs.unity3d.com/Manual/Profiler.html) e o [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluem os infileres de desempenho e as diretrizes de publicação da [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e da [Intel](https://software.intel.com/articles/vr-content-developer-guide) sobre a criação de perfil de desempenho e otimização. Há uma ampla discussão sobre o desempenho disponível em [noções básicas sobre o desempenho para realidade misturada](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Além disso, há detalhes específicos para o Unity em [recomendações de desempenho para o Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Mapeamento de entrada](#tab/input)

Você pode portar sua lógica de entrada para a realidade mista do Windows usando uma das duas abordagens, as APIs de entrada geral do Unity e do getbutton/getaxis que se estendem por várias plataformas ou pelo XR específico do Windows. WSA. APIs de entrada que oferecem dados mais ricos especificamente para controladores de movimento e mãos de HoloLens.

> [!IMPORTANT]
> Se você estiver usando os controladores de reverberação da HP, consulte [Este artigo](../../unity/unity-reverb-g2-controllers.md) para obter instruções adicionais de mapeamento de entrada.

## <a name="unity-xr-input-apis"></a>APIs de entrada do Unity XR

Para novos projetos, é recomendável usar as novas APIs de entrada XR desde o início. 

Você pode encontrar mais informações sobre as [APIs XR aqui](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="inputgetbuttongetaxis-apis"></a>APIs de entrada. getbutton/getaxis

No momento, o Unity usa suas APIs Input. getbutton/Input. getaxis gerais para expor a entrada para [o SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [o SDK do OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se seus aplicativos já estiverem usando essas APIs para entrada, este é o caminho mais fácil para dar suporte a controladores de movimento no Windows Mixed Reality: você deve apenas precisar remapear botões e eixos no Gerenciador de entrada.

Para obter mais informações, consulte a [tabela de mapeamento de botões/eixo do Unity](../../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e a [visão geral das APIs comuns do Unity](../../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específico do Windows. WSA. APIs de entrada

> [!CAUTION]
> Se o seu projeto estiver usando qualquer uma das XR. APIs de WSA, que estão sendo divididas em favor do SDK do XR em versões futuras do Unity. Para novos projetos, é recomendável usar o SDK do XR desde o início. Você pode encontrar mais informações sobre as [APIs e o sistema de entrada XR aqui](https://docs.unity3d.com/Manual/xr_input.html).

Se seu aplicativo já criar uma lógica de entrada personalizada para cada plataforma, você poderá optar por usar as APIs de entrada espaciais específicas do Windows no namespace **UnityEngine. XR. WSA. Input** . Isso permite que você acesse informações adicionais, como precisão de posição ou tipo de fonte, permitindo que você informe as mãos e os controladores no HoloLens.

> [!NOTE]
> Se você estiver usando os controladores de reverberação do HP, todas as APIs de entrada continuarão funcionando, exceto para **interactionname. supportsTouchpad**, que retornará false sem dados de touchpad.

Para obter mais informações, consulte a [visão geral das APIs UnityEngine. XR. WSA. Input](../../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, sendo que o design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controlador.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação:

* A **alça de fixação**, que representa o local da palma de uma mão detectada por um HoloLens ou o Palm que possui um controlador de movimento.
    * Em headsets de imersão, essa pose é melhor usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma.
    * A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.
    * O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
    * O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
    * O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.
    * Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) ou por meio da API específica do Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, solicitando a pose de alça).
* A **pose do ponteiro**, representando a ponta do controlador apontando para frente.
    * Essa pose é mais bem usada para Raycast ao apontar para a **interface do usuário** quando você está renderizando o próprio modelo do controlador.
    * Atualmente, a pose do ponteiro está disponível somente por meio da API específica do Windows (**SourceState. sourcePose. TryGetPosition/Rotation**, solicitando a pose do ponteiro).

Essas coordenadas de pose são todas expressas nas coordenadas do mundo do Unity.
