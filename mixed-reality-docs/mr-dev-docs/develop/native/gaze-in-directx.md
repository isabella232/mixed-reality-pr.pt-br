---
title: Olhar fixo com cabeça e olhos no DirectX
description: Saiba como solicitar, usar e desempacotar dados do raycasting de cabeça olhar e acompanhamento de olho em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: olho-olhar, cabeça olhar, controle de cabeça, controle ocular, DirectX, entrada, hologramas, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 8b3c63ac7a7edba0ce3173e024139e29d49757ab
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810172"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Cabeça-olhar e olho-olhar entrada no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.

No Windows Mixed Reality, os olhos e a entrada olhar de cabeça são usados para determinar o que o usuário está olhando. Você pode usar os dados para direcionar modelos de entrada primários, como [Head-olhar e commit](../../design/gaze-and-commit.md), e fornecer contexto para diferentes tipos de interação. Há dois tipos de vetores olhar disponíveis por meio da API: Head-olhar e olho-olhar.  Ambos são fornecidos como um raio tridimensional com uma origem e uma direção. Os aplicativos podem então raycastr em suas cenas ou no mundo real e determinar o que o usuário está direcionando.

**Head-olhar** representa a direção na qual a cabeça do usuário é apontada. Imagine olhar como a posição e direção de encaminhamento do próprio dispositivo, com a posição como o ponto central entre as duas exibições. O Head-olhar está disponível em todos os dispositivos de realidade misturada.

**Olho-olhar** representa a direção que os olhos do usuário estão procurando. A origem está localizada entre os olhos do usuário.  Ele está disponível em dispositivos com realidade misturada que incluem um sistema de controle de olho.

Os raios de cabeça e olho-olhar podem ser acessados por meio da API do  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Chame [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose no [sistema](coordinate-systems-in-directx.md)de carimbo de data e hora especificado. Este SpatialPointerPose contém uma origem e direção olhar. Ele também contém uma origem e direção olhar, se o acompanhamento dos olhos estiver disponível.

### <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Recurso</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Foco com a cabeça</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Olho-olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Usando Head-olhar

Para acessar o Head-olhar, comece chamando  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose. Passe os parâmetros a seguir.
 - Um [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas que você deseja para o olhar. Isso é representado pela variável *coordinateSystem* no código a seguir. Para obter mais informações, visite nosso guia do desenvolvedor de [sistemas de coordenadas](coordinate-systems-in-directx.md) .
 - Um [carimbo de data/](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) hora que representa o tempo exato necessário para a pose de cabeçalho.  Normalmente, você usará um carimbo de data/hora que corresponde ao horário em que o quadro atual será exibido. Você pode obter esse carimbo de data/hora de exibição previsto de um objeto  [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que é acessível por meio do [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)atual.  Esse objeto HolographicFramePrediction é representado pela variável de *previsão* no código a seguir.

 Quando você tiver um SpatialPointerPose válido, a posição de cabeçalho e a direção de encaminhamento serão acessíveis como propriedades.  O código a seguir mostra como acessá-los.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Usando os olhos-olhar

Para que os usuários usem a entrada olhar, cada usuário precisa passar por uma [calibragem de usuário com acompanhamento de olho](/hololens/hololens-calibration) na primeira vez que usar o dispositivo. A API de olho-olhar é semelhante ao olhar.
Ele usa a mesma API [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que fornece uma Ray Origin e uma direção que você pode Raycast em sua cena.  A única diferença é que você precisa habilitar explicitamente o controle de olho antes de usá-lo:
1. Solicite permissão do usuário para usar o acompanhamento de olho em seu aplicativo.
2. Habilite a funcionalidade de "entrada olhar" no manifesto do pacote.

### <a name="requesting-access-to-eye-gaze-input"></a>Solicitando acesso à entrada de olhar de olho

Quando seu aplicativo estiver sendo inicializado, chame [EyesPose:: RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao controle ocular. O sistema solicitará o usuário se necessário e retornará [GazeInputAccessStatus:: allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso tiver sido concedido. Essa é uma chamada assíncrona, portanto, requer um pouco de gerenciamento extra. O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que ele armazena em uma variável de membro chamada *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas. Você também pode usar a nova funcionalidade [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) com suporte do C++/WinRT.
Aqui está outro exemplo para solicitar permissão de usuário:
-   EyesPose:: IsSupported () permite que o aplicativo dispare a caixa de diálogo de permissão somente se houver um rastreador ocular.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up do prompt de permissão repetidamente.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>Declarando o recurso de *entrada olhar*

Clique duas vezes no arquivo appxmanifest em *Gerenciador de soluções*.  Em seguida, navegue até a seção de *recursos* e verifique o recurso de *entrada olhar* . 

![Funcionalidade de entrada do olhar](images/gaze-input-capability.png)

Isso adiciona as seguintes linhas à seção *Package* no arquivo appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obtendo o olhar Ray

Depois de ter recebido o acesso ao ET, você fica livre para pegar o olhar Ray a cada quadro.
Como com o Head-olhar, obtenha o [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data/hora desejado e sistema de coordenadas. O SpatialPointerPose contém um objeto [EyesPose](/uwp/api/windows.perception.people.eyespose) por meio da propriedade [Eyes](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . Isso será não nulo somente se o controle de olho estiver habilitado. A partir daí, você pode verificar se o usuário no dispositivo tem uma calibragem de acompanhamento de olho chamando [EyesPose:: IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Em seguida, use a propriedade [olhar](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obter o [SpatialRay](/uwp/api/windows.perception.spatial.spatialray) que contém a posição e a direção do olhar de olho. Às vezes, a propriedade olhar pode ser nula, portanto certifique-se de verificar isso. Isso pode acontecer se um usuário calibrado fechar temporariamente seus olhos.

O código a seguir mostra como acessar o olhar Ray.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>Fallback quando o controle de olho não está disponível

Conforme mencionado em nossos [documentos de design de acompanhamento de olho](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), os designers e desenvolvedores devem estar cientes das instâncias em que os dados de controle de olho podem não estar disponíveis.

Há várias razões para os dados estarem indisponíveis:
* Um usuário não está sendo calibrado
* Um usuário negou o acesso do aplicativo aos seus dados de controle de olho
* As interferências temporárias, como manchas no visor do HoloLens ou cabelo occluding os olhos do usuário. 

Embora algumas das APIs já tenham sido mencionadas neste documento, a seguir, fornecemos um resumo de como detectar que o acompanhamento de olho está disponível como uma referência rápida: 

* Verifique se o sistema dá suporte a acompanhamento de olho. Chame o seguinte *método*: [Windows. percepção. Peoples. EyesPose. IsSupported ()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Verifique se o usuário está calibrado. Chame a seguinte *Propriedade*: [Windows. percepção. People. EyesPose. IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Verifique se o usuário recebeu a permissão do seu aplicativo para usar seus dados de acompanhamento de olho: recupere o _' GazeInputAccessStatus '_ atual. Um exemplo de como fazer isso é explicado em [solicitando acesso à entrada olhar](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input). 

Você também pode querer verificar se os dados de controle de olho não estão obsoletos adicionando um tempo limite entre atualizações de dados de acompanhamento de olho recebido e, de outra forma, fallback para o Head-olhar, conforme discutido abaixo.   
Visite nossas [considerações de design de fallback](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) para obter mais informações.

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlacionando olhar com outras entradas

Às vezes, você pode achar que precisa de um [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponda a um evento no passado. Por exemplo, se o usuário fizer um toque de ar, seu aplicativo poderá querer saber o que ele estava observando. Para essa finalidade, simplesmente usar [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o tempo de quadro previsto não seria preciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição. Além disso, se estiver usando olhar de olho para direcionamento, nossos olhos tendem a se mover até mesmo antes de concluir uma ação de confirmação. Isso é menos um problema para um toque simples de ar, mas se torna mais crítico ao combinar comandos de voz longos com movimentos de olho rápido. Uma maneira de lidar com esse cenário é fazer uma chamada adicional para  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de data/hora histórico que corresponde ao evento de entrada.  

No entanto, para entrada que roteiam o SpatialInteractionManager, há um método mais fácil. O [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem sua própria função [TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Chamar isso fornecerá um [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfeitamente correlacionado sem as suposições. Para saber mais sobre como trabalhar com o SpatialInteractionSourceStates, confira os [controladores de mãos e de movimento na documentação do DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Calibragem

Para que o acompanhamento de olho funcione com precisão, cada usuário precisa passar por uma [calibragem do usuário com acompanhamento de olho](/hololens/hololens-calibration). Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição de qualidade mais confortável e mais segura para o usuário e para garantir o acompanhamento preciso do controle de olho ao mesmo tempo. Os desenvolvedores não precisam fazer nada em sua extremidade para gerenciar a calibragem do usuário. O sistema garantirá que o usuário receba uma solicitação para calibrar o dispositivo nas seguintes circunstâncias:
* O usuário está usando o dispositivo pela primeira vez
* O usuário optou anteriormente pelo processo de calibragem
* O processo de calibragem não teve sucesso na última vez em que o usuário usava o dispositivo

Os desenvolvedores devem certificar-se de fornecer suporte adequado para usuários onde os dados de acompanhamento de olho podem não estar disponíveis. Saiba mais sobre considerações para soluções de fallback em [acompanhamento de olho no HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Confira também

* [Calibragem](/hololens/hololens-calibration)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Olho-olhar no HoloLens 2](../../design/eye-tracking.md)
* [Olhar e confirmar modelo de entrada](../../design/gaze-and-commit.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)