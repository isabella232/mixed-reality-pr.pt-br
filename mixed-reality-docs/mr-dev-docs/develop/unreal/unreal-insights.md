---
title: Criação de perfil com Insights do Unreal
description: saiba como usar Insights inreais no HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: inreal, Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, contornar, insights, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headsets de realidade misturada, headset de realidade mista do windows, headset da realidade virtual
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779355"
---
# <a name="profiling-with-unreal-insights"></a>Criação de perfil com Insights do Unreal

o [Insights inreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) é um sistema de criação de perfil que coleta, analisa e visualiza dados de um mecanismo inreal. O sistema de criação de perfil pode ajudá-lo a encontrar gargalos de otimização e áreas em que o desempenho de aplicativos poderia usar um aumento. normalmente, você habilita o inreal Insights diretamente do editor, mas, para HoloLens 2, você precisará usar a linha de comando.

## <a name="setup"></a>Instalação

inreal permite que você crie e configure um "perfil personalizado" no iniciador HoloLens com os parâmetros de linha de comando que habilitam Insightss inreais.

1. Localize o endereço IP do seu computador usando o comando **ipconfig** no prompt de comando. O endereço IP é o endereço IPv4 listado por ipconfig. Tenha isso em mente para mais tarde quando você definir parâmetros de linha de comando.

> [!IMPORTANT]
> Se você estiver atrás de uma VPN, talvez seja necessário fornecer o endereço IP fornecido por meio da VPN.

![Captura de tela dos resultados da linha de comando para o comando ipconfig](images/unreal-insights-img-01.png)

2. abra **Project Configurações** na barra de ferramentas "editar" na janela principal do editor.

![captura de tela de editar lista suspensa com Project Configurações realçado](images/unreal-insights-img-15.png)

3. Role para baixo no painel esquerdo até encontrar o cabeçalho **plataformas** e selecione **HoloLens**.

![captura de tela da seção plataformas na Project Configurações painel esquerdo com HoloLens realçado](images/unreal-insights-img-15.png)

4. Confirme se a seção de **recursos** tem "cliente de Internet", "servidor de cliente de Internet" e "servidor de cliente de rede privada" selecionado.

![Captura de tela de opções de recursos com o cliente de Internet, servidor de cliente de Internet e servidor de cliente de rede privada selecionado](images/unreal-insights-img-14.png)

## <a name="launch"></a>Inicializar

1. abra o **iniciador Project** no painel UE4 no botão **iniciar** :

![Captura de tela das opções de inicialização com o iniciador do projeto](images/unreal-insights-img-07.png)

2. Selecione o **+** botão para criar um perfil personalizado em **perfis de inicialização personalizados**. Depois de criado, você sempre poderá editar este perfil mais tarde:

![Captura de tela do iniciador de projeto com perfis de inicialização personalizados realçados](images/unreal-insights-img-08.png)

3. selecione o botão **editar perfil** na HoloLens perfil de inicialização personalizada. Na seção **Build** , marque a **compilação UAT** e defina **parâmetros de linha de comando adicionais**.
   - Tente isso para os iniciantes: **-tracehost = IP_OF_YOUR_PC-Trace = log, indicador, quadro, CPU, GPU, loadtime, File, net**
   - você pode encontrar uma lista completa dos parâmetros de inicialização disponíveis na [documentação de referência do Insights inreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" é o endereço IP que encontramos na etapa 1. esse é o endereço ip do computador que executa o Insights inreal, não o endereço ip do HoloLens.

> [!IMPORTANT]
> Os rastreamentos podem ficar grandes muito rapidamente. Habilite somente os canais necessários para manter o tamanho do rastreamento baixo.

![Captura de tela das opções de Build na configuração do perfil](images/unreal-insights-img-17.png)

4. Selecione enparar **pelo livro** **para habilitar** a cópia para o dispositivo. Verifique se os mapas estão selecionados em **Cooked mapas**.

![captura de tela das opções de cook na configuração de perfil com o cook pelo livro e HoloLens realçadas](images/unreal-insights-img-09.png)

5. Defina **como você deseja empacotar a compilação** para o **pacote & armazenar localmente**. Observe o caminho de arquivo escolhido, pois você precisará dele mais tarde.

![Captura de tela das opções de pacote no conjunto de configuração de perfil para empacotar e armazenar localmente](images/unreal-insights-img-18.png)

6. Defina **como você gostaria de implantar a compilação?** para **não implantar**.

![Captura de tela de opções de implantação na configuração de perfil com Deploy definido como não implantar](images/unreal-insights-img-19.png)

8. selecione **voltar** para retornar à raiz da caixa de diálogo **iniciador Project**
9. De volta ao editor, clique em **Iniciar** em seu perfil de inicialização personalizado

![Captura de tela de perfis de inicialização personalizados](images/unreal-insights-img-13.png)

10. observe que o projeto é criado e, em seguida, implante o appxbundle (no caminho do pacote da etapa 5) em seu HoloLens por meio do portal do dispositivo

11. Inicie o Insights inreal. o executável Insights inreal é armazenado na pasta do mecanismo de binários, geralmente da seguinte maneira: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de tela de executáveis insights em execução](images/unreal-insights-img-12.png)

12. Inicie o aplicativo no seu HoloLens.

## <a name="profiling"></a>Criação de perfil

de volta em Insights inreais, selecione a conexão **dinâmica** com seu dispositivo para iniciar a criação de perfil

O perfil personalizado é compartilhado entre projetos. Daqui em diante, você pode usar o perfil personalizado criado em vez de ter que fazer isso todas as vezes. Você só precisa recriar a conexão com o dispositivo toda vez que iniciar inreal com as etapas 3 a 6 na [seção de instalação](#setup).

## <a name="see-also"></a>Confira também

- [documentação de Insights inreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
