---
title: Gravação da animação de entrada
description: Documentação no sistema de gravação de animação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 1a900b7b419a0aca45c3601ed583ef6c2e326574cb9e732edd0474afe117b895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223054"
---
# <a name="input-animation-recording"></a>Gravação da animação de entrada

O MRTK apresenta um sistema de gravação pelo qual o movimento de cabeçalho e os dados de rastreamento de mão podem ser armazenados em arquivos de animação. Os dados gravados podem ser reproduzidos usando o [sistema de simulação de entrada](input-simulation-service.md).

A gravação de entrada é uma ferramenta útil em várias situações:

* Criando testes automatizados para interação, manipulações, resolvedores, etc. Criar a movimentação de controladores e mãos para esses testes pode ser demorado. A gravação direta da entrada pode acelerar o processo e fornecer dados do mundo real.
* Ensinando o uso de elementos UX por meio de animações.
  Mostrar aos usuários como interagir com botões e outros objetos pode suavizar a curva de aprendizado.
* Depuração de comportamento inesperado que pode ser encontrado durante o uso regular.
  O sistema de gravação dá suporte a um conceito de "buffer sem interrupção" que permite gravar entradas recentes em segundo plano.
  Consulte [serviço de registro de entrada](#input-recording-service).

## <a name="recording-and-playback-services"></a>Serviços de gravação e reprodução

Dois serviços do sistema de entrada são fornecidos para gravar e reproduzir a entrada, respectivamente.

### <a name="input-recording-service"></a>Serviço de registro de entrada

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) Obtém dados dos controladores de transformação da câmera principal e da mão ativa e os armazena em um buffer interno. Quando solicitado, esses dados são serializados em arquivos binários para armazenamento e reprodução posterior.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Gravando animação de entrada" width="80%" alt="Recording diagram" class="center" />
</a>

Para iniciar a gravação de entrada, chame a [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) função. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) pausará a gravação (mas não descartará os dados gravados até agora, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) para fazer isso, se necessário).

Por padrão, o tamanho do buffer de gravação é limitado a 30 segundos. Isso permite que o serviço de registro Continue gravando em segundo plano sem acumular muitos dados e, em seguida, salve os últimos 30 segundos quando necessário. O intervalo de tempo pode ser alterado usando a [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) propriedade, ou a gravação pode ser ilimitada usando a [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) opção.

Os dados no buffer de gravação podem ser salvos em um arquivo binário usando a função [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) .

Para obter detalhes sobre o formato de arquivo binário, consulte [especificação de formato de arquivo de animação de entrada](input-animation-file-format.md).

### <a name="input-playback-service"></a>Serviço de reprodução de entrada

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) lê um arquivo binário com dados de animação de entrada e, em seguida, aplica esses dados por meio do [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) para recriar os movimentos gravados.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Animação de entrada de retorno" width="80%" alt="Play Back diagram" class="center" />
</a>

Para começar a reproduzir a animação de entrada, ela deve ser carregada a partir de um arquivo usando a função [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) .

Chame [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)ou [pare](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) para controlar a reprodução da animação.

O tempo de animação atual também pode ser controlado diretamente com a propriedade [localtime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) .

> [!WARNING]
> O loop ou a redefinição da animação de entrada ou [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) da configuração diretamente pela depuração da linha do tempo pode gerar resultados inesperados ao manipular a cena! Somente os movimentos de entrada são registrados, quaisquer alterações adicionais como mover objetos ou inverter opções não serão redefinidas. Certifique-se de recarregar a cena se forem feitas alterações irreversíveis.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Ferramentas do editor para gravar e reproduzir a animação de entrada

Existem várias ferramentas no editor do Unity para gravar e examinar a animação de entrada. essas ferramentas podem ser acessadas na [janela ferramentas de simulação de entrada](input-simulation-service.md#input-simulation-tools-window), que podem ser abertas na _realidade misturada Toolkit > utilitários >_ menu de simulação de entrada.

> [!NOTE]
> A gravação e a reprodução de entrada funcionam somente durante o modo de reprodução.

A janela de gravação de entrada tem dois modos:

* _Gravação_ para gravar entrada durante o modo de reprodução e salvá-la em arquivos de animação.

  Ao alternar o botão de gravação, o [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) está habilitado para registrar a entrada.
  Ao alternar o botão de gravação, uma seleção de salvar arquivo é mostrada e a animação de entrada gravada é salva no destino selecionado.

  O limite de tempo do buffer também pode ser alterado nesse modo.

* _Reprodução_ para carregar arquivos de animação e, em seguida, recriar a entrada por meio do sistema de simulação de entrada.

  Uma animação deve ser carregada neste modo primeiro. Depois de gravar a entrada no modo de gravação, a animação resultante é carregada automaticamente. Como alternativa, clique no botão "carregar" para selecionar um arquivo de animação existente.

  Os botões de controle de tempo da esquerda para a direita são:

  * _Redefina_ o tempo de reprodução para o início da animação.
  * _Reproduzir_ a animação continuamente ao longo do tempo.
  * _Etapa avançar uma_ vez.

  O controle deslizante também pode ser usado para depurar a linha do tempo da animação.

> [!WARNING]
> Executar um loop ou redefinir a animação de entrada ou depurar a linha do tempo pode gerar resultados inesperados ao manipular a cena! Somente os movimentos de entrada são registrados, quaisquer alterações adicionais como mover objetos ou inverter opções não serão redefinidas. Certifique-se de recarregar a cena se forem feitas alterações irreversíveis.
