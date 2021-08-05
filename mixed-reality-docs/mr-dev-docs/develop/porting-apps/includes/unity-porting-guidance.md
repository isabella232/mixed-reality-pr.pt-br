---
ms.openlocfilehash: e7f298b9d587df2243601670e187c109bb674a278deb67862b517568ca5198d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213501"
---
# <a name="project-settings"></a>[Configurações do projeto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Revise as etapas comuns de portação listadas acima

Revise as etapas comuns listadas acima para garantir que seu ambiente de desenvolvimento está definido corretamente. Na etapa #3, se você estiver usando Visual Studio selecione a carga de trabalho Desenvolvimento de Jogos **com Unity.** Você pode desmarcar o componente "Editor do Unity opcional", pois instalará uma versão mais recente do Unity na próxima etapa.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Atualizar para o build público mais recente do Unity com suporte Windows MR
1. Baixe o build [público recomendado mais recente do Unity com](../../install-the-tools.md) suporte à realidade misturada.
2. Salve uma cópia do seu projeto antes de começar
3. Revise a [documentação](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponível no Unity sobre como atualizar se o projeto foi criado em uma versão mais antiga do Unity.
4. Siga as [instruções](https://docs.unity3d.com/Manual/APIUpdater.html) no site do Unity para usar o atualizador automático de API
5. Verifique e veja se há alterações adicionais que você precisa fazer para executar seu projeto e trabalhar com erros e avisos restantes. 

> [!Note] 
> Se você tiver um middleware do que depende, verifique se está usando a versão mais recente (mais detalhes na etapa 3 abaixo).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. Atualizar seu middleware para as versões mais recentes

Com qualquer atualização do Unity, há uma boa chance de você precisar atualizar um ou mais pacotes de middleware dos qual seu jogo ou aplicativo depende. Além disso, estar atualizado com o middleware mais recente aumenta a probabilidade de sucesso em todo o restante do processo de portação.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Direcionar seu aplicativo para ser executado no Win32

De dentro de seu aplicativo unity:

* Navegue até Arquivo -> Build Configurações
* Selecione "PC, Mac, Linux Autônomo"
* Definir a plataforma de destino como "Windows"
* Definir arquitetura como "x86" Selecione "Alternar Plataforma"

> [!NOTE] 
> Se o aplicativo tiver dependências de serviços específicos do dispositivo, como a complicação de match do Steam, você precisará desabilitá-los nesta etapa. Você pode se conectar aos serviços equivalentes que Windows fornece mais tarde.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Configurar o hardware Windows Mixed Reality dispositivo
1. Revisar as etapas [na instalação do headset imersivo](/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Saiba mais [sobre Como usar o simulador Windows Mixed Reality e](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) navegar pelo Windows Mixed Reality [página](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Direcionar seu aplicativo para ser executado no Windows Mixed Reality
1. Primeiro, você deve remover ou compilar condicionalmente qualquer outra biblioteca com suporte específico para um SDK de VR específico. Esses ativos frequentemente alteram configurações e propriedades em seu projeto de maneiras incompatíveis com outros SDKs de VR, como Windows Mixed Reality.
    * Por exemplo, se seu projeto referenciar o SDK do SteamVR, você precisará atualizar seu projeto para usar as APIs de VR comuns do Unity que suportam o Windows Mixed Reality e o SteamVR.
    * Etapas específicas para excluir condicionalmente outros SDKs de VR em breve.
2. Em seu projeto do Unity, [o SDK Windows 10 destino](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Para cada cena, [configure a câmera](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. Usar o estágio para colocar o conteúdo no chão

Você pode criar experiências de Realidade Misturada em uma ampla variedade de [escalas de experiência.](../../../design/coordinate-systems.md)

Se você estiver portando uma experiência de escala de **sated,** deverá garantir que o Unity esteja definido como o **tipo de** espaço de acompanhamento estacionário:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Este código acima define o sistema de coordenadas do mundo do Unity para acompanhar o [quadro estacionário de referência](../../../design/coordinate-systems.md#spatial-coordinate-systems). No modo de acompanhamento estacionário, o conteúdo colocado no editor logo na frente do local padrão da câmera (a frente é -Z) aparece na frente do usuário quando o aplicativo é lançado. Para reativar a origem do usuário, você pode chamar o XR do [Unity. Método InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

Se você estiver portando uma experiência **em** escala permanente ou uma experiência de escala **de** sala, colocará o conteúdo em relação ao chão. Você se preocupa com o piso do usuário usando o estágio espacial **[,](../../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa a origem definida no nível do piso do usuário e o limite de sala opcional, configurada durante a primeira operação. Para essas experiências, você deve garantir que o Unity seja definido como o tipo de espaço de acompanhamento **RoomScale.** Embora RoomScale seja o padrão, você vai querer defini-lo explicitamente e garantir que você volte a ser verdadeiro, para capturar situações em que o usuário tenha movido o computador para fora da sala calibrada:

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

Depois que o aplicativo define com êxito o tipo de espaço de acompanhamento RoomScale, o conteúdo colocado no plano y=0 será exibido no chão. A origem em (0, 0, 0) será o local específico no chão em que o usuário ficou durante a instalação da sala, com -Z representando a direção para frente que ele estava enfrentando durante a instalação.

No código de script, você pode chamar o método TryGetGeometry em que você é o tipo UnityEngine.Experimental.XR.Boundary para obter um polígono de limite, especificando um tipo de limite de TrackedArea. Se o usuário definiu um limite (você obter de volta uma lista  de vértices), é seguro fornecer uma experiência de escala de sala para o usuário, em que ele pode dar uma olhada na cena que você cria.

O sistema renderizará automaticamente o limite quando o usuário se aproximar dele. Seu aplicativo não precisa usar esse polígono para renderizar o limite em si.

Para obter mais informações, consulte a [página Sistemas de coordenadas no Unity.](../../unity/coordinate-systems-in-unity.md)

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Exemplo de resultados:

![Exemplo de resultados](../../porting-apps/images/largestrectangle-400px.jpg)

O algoritmo é baseado em um blog de Daniel Smilkov: [maior retângulo em um polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. Trabalhar com seu modelo de entrada

Cada jogo ou aplicativo destinado a um HMD existente terá um conjunto de entradas que ele trata, tipos de entradas de que precisa para a experiência e APIs específicas que ele chama para obter essas entradas. Investimos em tentar torná-lo o mais simples e simples possível para aproveitar as entradas disponíveis no Windows Mixed Reality.

Leia o [guia de portação](../porting-guides.md?tabs=input) de entrada do Unity na guia adjacente para obter detalhes sobre como o Windows Mixed Reality expõe a entrada e como isso é mapeado para o que seu aplicativo pode fazer hoje.

### <a name="9-performance-testing-and-tuning"></a>9. Teste e ajuste de desempenho

Windows Mixed Reality estará disponível em uma ampla classe de dispositivos, desde PCs de jogos de alto nível até PCs de mercado amplos. Dependendo de qual mercado você está direcionando, há uma diferença significativa nos orçamentos de computação e gráficos disponíveis para seu aplicativo. Durante este exercício de portação, você provavelmente está aproveitando um pc premium e teve orçamentos de computação e gráficos significativos disponíveis para seu aplicativo. Se você quiser disponibilizar seu aplicativo para um público-alvo mais amplo, teste e faça o perfil do aplicativo no hardware representativo que deseja [direcionar ao](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

O [Unity](https://docs.unity3d.com/Manual/Profiler.html) e o [Visual Studio](/visualstudio/profiling/index) incluem os profilers de desempenho e as diretrizes de publicação da [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e da [Intel](https://software.intel.com/articles/vr-content-developer-guide) na criação de perfil e otimização de desempenho. Há uma ampla discussão sobre o desempenho disponível em Noções [básicas sobre o desempenho para realidade misturada.](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Além disso, há detalhes específicos para o Unity em [Desempenho Recomendações para Unity.](../../unity/performance-recommendations-for-unity.md)

# <a name="input-mapping"></a>[Mapeamento de entrada](#tab/input)

Você pode portar sua lógica de entrada para Windows Mixed Reality usando uma das duas abordagens, as APIs Input.GetButton/GetAxis gerais do Unity que abrangem várias plataformas ou o XR Windows específico do Windows. Wsa. APIs de entrada que oferecem dados mais rico especificamente para controladores de movimento e HoloLens mãos.

> [!IMPORTANT]
> Se você estiver usando controladores HP Reverb G2, consulte este [artigo](../../unity/unity-reverb-g2-controllers.md) para obter instruções adicionais de mapeamento de entrada.

## <a name="unity-xr-input-apis"></a>APIs de entrada do Unity XR

Para novos projetos, é recomendável usar as novas APIs de entrada XR desde o início. 

Você pode encontrar mais informações sobre as [APIs XR aqui](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="inputgetbuttongetaxis-apis"></a>Input.GetButton/GetAxis APIs

Atualmente, o Unity usa suas APIs Input.GetButton/Input.GetAxis gerais para expor a entrada para o [SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e o [SDK do OpenVR.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Se seus aplicativos já estão usando essas APIs para entrada, esse é o caminho mais fácil para dar suporte a controladores de movimento no Windows Mixed Reality: você deve apenas precisar remapear botões e eixos no Gerenciador de Entrada.

Para obter mais informações, consulte a tabela de mapeamento de [eixo/botão](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) do Unity e a [visão geral das APIs comuns do Unity.](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR específico. Wsa. APIs de entrada

> [!CAUTION]
> Se o projeto estiver usando qualquer um dos XR. APIs do WSA, elas estão sendo desaparadas em favor do SDK do XR em versões futuras do Unity. Para novos projetos, recomendamos usar o SDK do XR desde o início. Você pode encontrar mais informações sobre o sistema de [Entrada XR e as APIs aqui](https://docs.unity3d.com/Manual/xr_input.html).

Se seu aplicativo já criar uma lógica de entrada personalizada para cada plataforma, você poderá optar por usar as APIs de entrada espaciais específicas do Windows no namespace **UnityEngine.XR.WSA.Input.** Isso permite que você acesse informações adicionais, como a precisão da posição ou o tipo de origem, o que permite separar as mãos e os controladores HoloLens.

> [!NOTE]
> Se você estiver usando controladores HP Reverb G2, todas as APIs de entrada continuarão a funcionar, exceto **interactionSource.supportsTouchpad,** que retornará false sem dados de touchpad.

Para obter mais informações, consulte a [visão geral das APIs UnityEngine.XR.WSA.Input.](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Pose da mão versus pose apontando

Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador diferente em sua relação entre a posição da mão do usuário e a direção natural de "avançar" que os aplicativos devem usar para apontar ao renderizar o controlador.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação:

* A **mão representa**, representando o local da mão de uma mão detectada por um HoloLens ou da mão que mantém um controlador de movimento.
    * Em headsets imersivos, essa pose é mais bem usada para **renderizar** a mão do usuário ou um objeto mantido na mão do **usuário,** como um capacete ou umaada.
    * A **posição da mão:** o centroide da mão ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralar a posição dentro da mão.
    * Eixo direito da orientação da **mão:** quando você abre completamente a mão para formar uma pose de 5 dedos simples, o raio que é normal para sua mão (para frente da mão esquerda, para trás da mão direita)
    * Eixo **de** avanço da orientação da mão: quando você fecha a mão parcialmente (como se estivesse segurando o controlador), o raio que aponta para "para frente" pelo sinal formado pelos dedos não polegares.
    * Eixo **para cima da orientação da** mão: o eixo Para cima implícito nas definições Direita e Avanço.
    * Você pode acessar a pose de controle por meio da API de entrada entre fornecedores do Unity **[(XR). InputTracking.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html) GetLocalPosition/Rotation**) ou por meio da API específica do Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando a pose de mão).
* O **ponteiro representa**, representando a dica do controlador apontando para frente.
    * Essa pose é melhor usada para raycast **ao apontar para** a interface do usuário quando você estiver renderizar o próprio modelo de controlador.
    * Atualmente, a pose do ponteiro está disponível somente por meio da API específica Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando a pose De ponteiro).

Todas essas coordenadas de pose são expressas em coordenadas do mundo do Unity.