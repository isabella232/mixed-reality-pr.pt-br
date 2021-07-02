---
title: Gravação de animação de entrada
description: Documentação sobre o sistema de gravação de animação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6bdb764c5905352b9aec7c1512a73e727b60573a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176945"
---
# <a name="input-animation-recording"></a>Gravação de animação de entrada

O MRTK apresenta um sistema de gravação pelo qual os dados de movimentação de cabeça e acompanhamento de mão podem ser armazenados em arquivos de animação. Em seguida, os dados gravados podem ser interpretados usando o sistema [de simulação de entrada](input-simulation-service.md).

A entrada de gravação é uma ferramenta útil em uma variedade de situações:

* Criando testes automatizados para interação, manipulações, solucionadores etc. A criação da movimentação de controladores e mãos para esses testes pode ser demorada. Registrar a entrada diretamente pode acelerar o processo e fornecer dados do mundo real.
* Ensinando o uso de elementos de UX por meio de animações.
  Mostrar aos usuários como interagir com botões e outros objetos pode suavizar a curva de aprendizado.
* Depuração de comportamento inesperado que pode ser encontrado durante o uso regular.
  O sistema de gravação dá suporte a um conceito de "buffer sem rolagem" que permite a gravação de entrada recente em segundo plano.
  Consulte [Serviço de Gravação de Entrada](#input-recording-service).

## <a name="recording-and-playback-services"></a>Serviços de gravação e reprodução

Dois serviços de sistema de entrada são fornecidos para registrar e reproduzir a entrada, respectivamente.

### <a name="input-recording-service"></a>Serviço de gravação de entrada

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) O recebe dados da transformação principal da câmera e dos controladores de mão ativos e os armazena em um buffer interno. Quando solicitado, esses dados são serializados em arquivos binários para armazenamento e reprodução posterior.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Animação de entrada de gravação" width="80%" alt="Recording diagram" class="center" />
</a>

Para iniciar a gravação de entrada, chame a [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) função . [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) pausa a gravação (mas não descarta os dados registrados até agora, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) para fazer isso, se necessário).

Por padrão, o tamanho do buffer de gravação é limitado a 30 segundos. Isso permite que o serviço de gravação continue gravando em segundo plano sem acumular muitos dados e salve os últimos 30 segundos quando necessário. O intervalo de tempo pode ser alterado usando a [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) propriedade ou a gravação pode ser ilimitada usando a opção [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) .

Os dados no buffer de gravação podem ser salvos em um arquivo binário usando a [função SaveInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*)

Para obter detalhes sobre o formato de arquivo binário, consulte Especificação de formato de arquivo de [animação de entrada](input-animation-file-format.md).

### <a name="input-playback-service"></a>Serviço de reprodução de entrada

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) lê um arquivo binário com dados de animação de entrada e, em seguida, aplica esses dados por meio de [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) para recriar os movimentos gravados.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Animação de entrada de reprodução" width="80%" alt="Play Back diagram" class="center" />
</a>

Para começar a reprodução da animação de entrada, ela deve ser carregada de um arquivo usando a [função LoadInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*)

Chame [Reproduzir,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [Pausar](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)ou [Parar para](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) controlar a reprodução da animação.

O tempo de animação atual também pode ser controlado diretamente com a [propriedade LocalTime.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime)

> [!WARNING]
> Fazer loop ou redefinir a animação de entrada ou a configuração diretamente depurando a linha do tempo pode gerar [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) resultados inesperados ao manipular a cena! Somente os movimentos de entrada são registrados, quaisquer alterações adicionais, como mover objetos ou alternar comutadores, não serão redefinidas. Certifique-se de recarregar a cena se alterações irreversíveis foram feitas.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Ferramentas do editor para gravação e reprodução de animação de entrada

Existem várias ferramentas no editor do Unity para gravar e examinar a animação de entrada. Essas ferramentas podem ser acessadas na janela ferramentas de simulação de entrada [,](input-simulation-service.md#input-simulation-tools-window)que pode ser aberta no menu Realidade _Misturada Toolkit > Utilitários > Simulação de_ Entrada.

> [!NOTE]
> A gravação e a reprodução de entrada só funcionam durante o modo de reprodução.

A janela de gravação de entrada tem dois modos:

* _Gravação_ para gravar a entrada durante o modo de reprodução e salvá-la em arquivos de animação.

  Ao ativar o botão de gravação, o [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) está habilitado para registrar a entrada.
  Ao desligar o botão de gravação, uma seleção de salvar arquivo é mostrada e a animação de entrada gravada é salva no destino selecionado.

  O limite de tempo do buffer também pode ser alterado nesse modo.

* _Reprodução_ para carregar arquivos de animação e recriar a entrada por meio do sistema de simulação de entrada.

  Uma animação deve ser carregada nesse modo primeiro. Depois de gravar a entrada no modo de gravação, a animação resultante é carregada automaticamente. Como alternativa, clique no botão "Carregar" para selecionar um arquivo de animação existente.

  Os botões de controle de tempo da esquerda para a direita são:

  * _Redefinir_ o tempo de reprodução para o início da animação.
  * _Reproduzir_ animação continuamente ao longo do tempo.
  * _Avance_ uma etapa.

  O controle deslizante também pode ser usado para limpar a linha do tempo de animação.

> [!WARNING]
> Fazer loop ou redefinir a animação de entrada ou depurar a linha do tempo pode gerar resultados inesperados ao manipular a cena! Somente os movimentos de entrada são registrados, quaisquer alterações adicionais, como mover objetos ou alternar comutadores, não serão redefinidas. Certifique-se de recarregar a cena se alterações irreversíveis foram feitas.
