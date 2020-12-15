---
title: Criação de perfil com informações inreais
description: Saiba como usar percepções inreais no HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Inreal, Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, contornar, insights, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486303"
---
# <a name="profiling-with-unreal-insights"></a>Criação de perfil com informações inreais 

[Insights inreais](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) é um sistema de criação de perfil que coleta, analisa e visualiza dados de um mecanismo inreal. O sistema de criação de perfil pode ajudá-lo a encontrar gargalos de otimização e áreas em que o desempenho de aplicativos poderia usar um aumento. Normalmente, você habilita informações inreais diretamente do editor, mas para o HoloLens 2, você precisará usar a linha de comando.  

## <a name="setup"></a>Instalação

Inreal permite que você crie e configure um "perfil personalizado" no iniciador do HoloLens com os parâmetros de linha de comando que habilitam insights inreais.

1.  Localize o endereço IP do seu computador usando o comando **ipconfig** no prompt de comando. O endereço IP é o endereço IPv4 listado por ipconfig. Tenha isso em mente para mais tarde quando você definir parâmetros de linha de comando.

> [!IMPORTANT]
> Se você estiver atrás de uma VPN, talvez seja necessário fornecer o endereço IP fornecido por meio da VPN.

![Captura de tela dos resultados da linha de comando para o comando ipconfig](images/unreal-insights-img-01.png)

2.  Vá para a parte superior do painel de mecanismo inreal e abra **Device Manager** no botão **Iniciar** :

![Captura de tela das opções de inicialização com o Gerenciador de dispositivos realçado](images/unreal-insights-img-02.png)

3.  Na Device Manager, selecione **Adicionar um dispositivo não listado**:

![Captura de tela do Gerenciador de dispositivos aberta no mecanismo inreal](images/unreal-insights-img-03.png)

4. Clique em **selecionar uma plataforma** e escolha **HoloLens**:

![Captura de tela de adicionar lista suspensa de dispositivos não listados com o HoloLens realçado](images/unreal-insights-img-04.png)

5.  Se você estiver usando IPoverUSB, digite 127.0.0.1:10080 como o identificador do dispositivo. Insira seu usuário e senha do HoloLens em seus respectivos campos e preencha o **nome de exibição** como desejar.

> [!IMPORTANT]
> O identificador de dispositivo é o endereço IP do HoloLens, não o computador que executa informações invisíveis encontradas na etapa 1.

![Captura de tela dos detalhes do dispositivo do HoloLens no Gerenciador de dispositivos](images/unreal-insights-img-05.png)

6.  Selecione **Adicionar** e seu HoloLens deve aparecer na lista de dispositivos do Gerenciador de dispositivos:

![Captura de tela do HoloLens adicionado à lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a>Inicializar

1. Abra o **inicializador de projeto** no painel UE4 no botão **Iniciar** :

![Captura de tela das opções de inicialização com o iniciador do projeto](images/unreal-insights-img-07.png)

2. Selecione o **+** botão para criar um perfil personalizado em **perfis de inicialização personalizados**. Depois de criado, você sempre poderá editar este perfil mais tarde:

![Captura de tela do iniciador de projeto com perfis de inicialização personalizados realçados](images/unreal-insights-img-08.png)

3. Selecione o botão **Editar perfil** no perfil de inicialização personalizada do HoloLens e configure:
    * Selecione o **Cookie** para **o livro** para habilitar a cópia para o dispositivo
    * Convém verificar se deseja **arquivar?** na seção **arquivo morto** para manter o. appxbundle gerado em vez de excluir para economizar espaço em disco. Especifique um local para o. appxbundle e alterne para uma compilação de desenvolvimento, se desejar

![Captura de tela de opções de Cook na configuração de perfil com o Cook pelo livro e o HoloLens realçado](images/unreal-insights-img-09.png)

4. Defina **como você deseja implantar a compilação?** para **copiar para o dispositivo** para ativar a seção de **inicialização** da interface do usuário:

![Captura de tela do iniciador de projeto com opções de implantação com cópia para dispositivo realçado](images/unreal-insights-img-10.png)

5. Defina **parâmetros de linha de comando adicionais** na seção **Iniciar** . Os parâmetros serão gravados em um arquivo ue4commandline.txt, empacotados no pacote e usados na inicialização. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Tente isso para os iniciantes: **-tracehost = IP_OF_YOUR_PC-Trace = log, indicador, quadro, CPU, GPU, loadtime, File, net**
    * Você pode encontrar uma lista completa dos parâmetros de inicialização disponíveis na [documentação de referência do insights não reais](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" é o endereço IP que encontramos na etapa 1. Esse é o endereço IP do computador que está executando insights inreais, não o endereço IP do HoloLens.

> [!IMPORTANT]
> Os rastreamentos podem ficar grandes muito rapidamente. Habilite somente os canais necessários para manter o tamanho do rastreamento baixo.

![Captura de tela das opções de configuração de inicialização](images/unreal-insights-img-11.png)

6. Inicie informações incorretas antes da inicialização do aplicativo; caso contrário, os insights não poderão ser inicializados adequadamente antes do aplicativo:
    * O executável insights não reais é armazenado na pasta do mecanismo de binários, geralmente da seguinte maneira: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de tela de executáveis insights em execução](images/unreal-insights-img-12.png)

6.  Selecione **voltar** para retornar à raiz da caixa de diálogo **iniciador do projeto**
7.  De volta ao editor, clique em **Iniciar** em seu perfil de inicialização personalizado

![Captura de tela de perfis de inicialização personalizados](images/unreal-insights-img-13.png)

8.  Assista à medida que seu projeto é empacotado, instalado em seu dispositivo e iniciado

## <a name="profiling"></a>Criação de perfil

De volta às informações inreais, selecione a conexão **dinâmica** com o dispositivo para iniciar a criação de perfil

O perfil personalizado é compartilhado entre projetos. Daqui em diante, você pode usar o perfil personalizado criado em vez de ter que fazer isso todas as vezes. Você só precisa recriar a conexão com o dispositivo toda vez que iniciar inreal com as etapas 3 a 6 na [seção de instalação](#setup).

## <a name="see-also"></a>Consulte também
* [Documentação de informações inreais](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

