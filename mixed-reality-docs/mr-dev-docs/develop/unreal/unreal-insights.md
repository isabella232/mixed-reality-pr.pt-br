---
title: Criação de perfil com Insights do Unreal
description: Saiba como usar o Unreal Insights no HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, profling, unreal insights, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228576"
---
# <a name="profiling-with-unreal-insights"></a>Criação de perfil com Insights do Unreal 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) é um sistema de criação de perfil que coleta, analisa e visualiza dados do Unreal Engine. O sistema de criação de perfil pode ajudá-lo a encontrar gargalos de otimização e áreas em que o desempenho dos aplicativos pode usar um aumento. Normalmente, você habilita o Unreal Insights no editor, mas para HoloLens 2, você precisará usar a linha de comando.  

## <a name="setup"></a>Instalação

O Unreal permite que você crie e configure um "Perfil Personalizado" no HoloLens com os parâmetros de linha de comando que habilitam o Unreal Insights.

1.  Encontre o endereço IP do computador usando o **comando ipconfig** no prompt de comando. O endereço IP é o endereço IPv4 listado por ipconfig. Lembre-se disso para mais tarde quando você definir Parâmetros de Linha de Comando.

> [!IMPORTANT]
> Se você estiver atrás de uma VPN, talvez seja necessário fornecer o endereço IP fornecido por meio da VPN.

![Captura de tela dos resultados da linha de comando para o comando ipconfig](images/unreal-insights-img-01.png)

2.  Vá para a parte superior do painel do Unreal Engine e abra **Gerenciador de Dispositivos** no **botão** Iniciar:

![Captura de tela das opções de lançamento com o gerenciador de dispositivos realçada](images/unreal-insights-img-02.png)

3.  No Gerenciador de Dispositivos, selecione **Adicionar um dispositivo não selecionado:**

![Captura de tela do gerenciador de dispositivos aberto no mecanismo do Unreal](images/unreal-insights-img-03.png)

4. Clique **em Selecionar uma plataforma** e escolha **HoloLens:**

![Captura de tela da lista de menus suspenso adicionar dispositivo não listada com HoloLens realçada](images/unreal-insights-img-04.png)

5.  Se você estiver usando IPoverUSB, insira 127.0.0.1:10080 como o Identificador de Dispositivo. Insira seu HoloLens usuário e senha em seus respectivos campos e preencha **o Nome de Exibição** como desejar.

> [!IMPORTANT]
> O Identificador de Dispositivo é o endereço IP do HoloLens, NÃO do computador que executa o Unreal Insights encontrado na etapa 1.

![Captura de tela HoloLens detalhes do dispositivo no gerenciador de dispositivos](images/unreal-insights-img-05.png)

6.  Selecione **Adicionar** e o HoloLens deve aparecer na lista de dispositivos do gerenciador de dispositivos:

![Captura de tela HoloLens adicionada à lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a>Inicializar

1. Abra **Project Launcher** no painel UE4 sob o **botão** Iniciar:

![Captura de tela das opções de lançamento com o launcher do projeto realçada](images/unreal-insights-img-07.png)

2. Selecione o **+** botão para criar um perfil personalizado em **Perfis de Início Personalizados.** Depois de criado, você sempre poderá editar esse perfil mais tarde:

![Captura de tela do launcher do projeto com perfis de lançamento personalizados realçadas](images/unreal-insights-img-08.png)

3. Selecione **o botão Editar** perfil no HoloLens de lançamento personalizado e configure:
    * Selecione **Cook** to **The Book para** habilitar a cópia para o dispositivo
    * Talvez você queira verificar Deseja arquivar? na seção Arquivar para manter o .appxbundle gerado em vez de excluir para economizar espaço em disco.   Especifique um local para o .appxbundle e alternar para um build de desenvolvimento, se desejar

![Captura de tela das opções de chef na configuração de perfil com o cook pelo livro e HoloLens realçadas](images/unreal-insights-img-09.png)

4. De **definir Como você gostaria de implantar o build?** para Copiar para o dispositivo **para** ativar a seção Iniciar da interface do usuário: 

![Captura de tela do launcher do projeto com opções de implantação com cópia no dispositivo realçada](images/unreal-insights-img-10.png)

5. De **definir parâmetros de linha de comando** adicionais na **seção** Iniciar. Os parâmetros serão gravados em um arquivo ue4commandline.txt, empacotados no pacote e usados no lançamento. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Experimente estes para iniciantes: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
    * Você pode encontrar uma lista completa dos parâmetros de lançamento disponíveis na documentação de [referência do Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" é o endereço IP encontrado na etapa 1. Esse é o endereço IP do computador que executa o Unreal Insights, NÃO o endereço IP do HoloLens.

> [!IMPORTANT]
> Os rastreamentos podem ficar grandes muito rapidamente. Habilita somente os canais necessários para manter o tamanho do rastreamento baixo.

![Captura de tela das opções de configuração de lançamento](images/unreal-insights-img-11.png)

6. Iniciar o Unreal Insights antes da inicialização do aplicativo, caso contrário, o Unreal Insights poderá inicializar adequadamente antes do aplicativo:
    * O executável Insights Unreal é armazenado na pasta do mecanismo de binários, geralmente da seguinte forma: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de tela do executável do Unreal Insights em execução](images/unreal-insights-img-12.png)

6.  Selecione **Voltar** para retornar à raiz da caixa **de diálogo Project Launcher**
7.  De volta ao editor, clique em **Iniciar** em seu perfil de lançamento personalizado

![Captura de tela dos perfis de lançamento personalizados](images/unreal-insights-img-13.png)

8.  Observe como seu projeto é empacotado, instalado em seu dispositivo e lançado

## <a name="profiling"></a>Criação de perfil

De volta ao Unreal Insights, selecione a **conexão** ao vivo com seu dispositivo para iniciar a criação de perfil

O perfil personalizado é compartilhado entre projetos. Daqui em diante, você pode usar o perfil personalizado criado em vez de precisar fazer isso toda vez. Você só precisa recriar a conexão com o dispositivo sempre que iniciar o Unreal com as etapas 3 a 6 na seção [de instalação](#setup).

## <a name="see-also"></a>Confira também
* [Documentação Insights Unreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

