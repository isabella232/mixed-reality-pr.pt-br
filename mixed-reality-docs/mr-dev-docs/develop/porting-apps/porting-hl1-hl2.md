---
title: Portabilidade dos aplicativos HoloLens (1ª geração) para o HoloLens 2
description: Criado para desenvolvedores que têm um aplicativo no HoloLens (1ª geração) e versões do MRTK mais antigas e buscam portá-lo para o MRTK versão 2 e o HoloLens 2.
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, MRTK, MRTK versão 2, HoloLens 2, unity, portabilidade, 1ª geração do HoloLens, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, migração, práticas recomendadas, ARM
ms.openlocfilehash: f7a70a8bd5a6d11d6502b431b17bbd3391d24ce4e19f0a842503ccae834589fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219272"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>Portabilidade dos aplicativos HoloLens (1ª geração) para o HoloLens 2

Este guia foi projetado para ajudar os desenvolvedores com um aplicativo do Unity para HoloLens (1ª geração) a portá-lo para o dispositivo HoloLens 2. Há quatro etapas principais para portar um aplicativo do Unity do HoloLens (1ª geração) para o HoloLens 2. 

As seções abaixo fornecem informações detalhadas para cada estágio:

| Etapa 1 | Etapa 2 | Etapa 3 | Etapa 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo do Visual Studio](../images/visualstudio_logo.png) | ![Logotipo do Unity](../../design/images/logo-unity.png)| ![Ícone do Unity](../unity/images/hololens2_icon.jpg) | ![Logotipo do MRTK](../../design/images/74-12.png) |
| Baixar as ferramentas mais recentes | Atualizar o projeto do Unity | Compilar para o ARM | Migrar para o MRTK v2

## <a name="prerequisites"></a>Pré-requisitos

**Recomendamos expressamente** que você use o controle do código-fonte para salvar um instantâneo do estado original dos seus aplicativos antes de iniciar o processo de portabilidade. Além disso, recomendamos *salvar* os estados de ponto de verificação em vários momentos durante o processo. Também pode ser útil ter outra instância no Unity do aplicativo original para comparação lado a lado durante o processo de portabilidade. 

> [!NOTE]
> Antes da portabilidade, verifique se você tem as ferramentas mais recentes instaladas para o desenvolvimento do Windows Mixed Reality. Para a maioria dos desenvolvedores existentes do HoloLens, isso envolve a atualização para a última versão do Visual Studio 2019 e a instalação do SDK apropriado do Windows. O conteúdo abaixo se aprofunda ainda mais em diferentes versões do Unity e no MRTK (Kit de ferramentas de realidade misturada) versão 2.
>
> Para obter mais informações, confira [Instalar as ferramentas](../install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Migrar o projeto para a última versão do Unity

Se você estiver usando o [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), recomenda-se atualizar para o MRTK 2,7 antes de atualizar seu projeto para o [Unity 2020,3 LTS](../unity/choosing-unity-version.md). O MRTK 2.7 é compatível com Unity 2018, 2019 e 2020, o que garante que seu projeto está pronto para o Unity 2020, mesmo antes de atualizar o Unity. Avalie as [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) atualmente existentes no projeto e determine se essas DLLs podem ser criadas para o ARM64. Para projetos com um plug-in dependente do ARM64, talvez seja necessário continuar criando seu aplicativo para o ARM.

## <a name="update-sceneproject-settings-in-unity"></a>Atualizar as configurações de cena/projeto no Unity

Após a atualização para o [Unity 2020.3 LTS](https://unity3d.com/unity/qa/lts-releases), recomenda-se atualizar as configurações específicas no Unity para obter melhores resultados no dispositivo. Essas configurações são descritas detalhadamente em [Configurações recomendadas para o Unity](../unity/Recommended-settings-for-Unity.md).

Reiteramos que o [back-end de script do .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) está sendo preterido no Unity 2018 e **removido** no Unity 2019. É altamente recomendável que os desenvolvedores mudem seu projeto para [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).

> [!NOTE]
> O back-end de script do IL2CPP pode causar tempos de build mais longos do Unity para o Visual Studio e, portanto, os desenvolvedores devem configurar seus computadores de desenvolvedor para [otimização dos tempos de build do IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Além disso, também pode ser benéfico configurar um [Servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo arquivos de script) ou que estejam constantemente alterando cenas e ativos. Ao abrir um projeto, o Unity armazena os ativos qualificados em um formato de cache interno no computador do desenvolvedor. Os itens precisam ser importados novamente e processados novamente quando modificados. Esse processo pode ser feito uma vez e salvo em um servidor de cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores processarem a nova importação de novas alterações localmente.

Depois de resolver as alterações da falha devido à migração para a versão atualizada do Unity, compile e teste seus aplicativos atuais no HoloLens (1ª geração). Esse é um bom momento para criar e salvar uma confirmação no controle do código-fonte.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilar dependências/plug-ins para o processador ARM

O HoloLens (1ª geração) executa aplicativos em um processador x86, enquanto o HoloLens 2 usa um processador ARM. Portanto, é necessário portar os aplicativos HoloLens existentes para que eles deem suporte ao ARM. Conforme indicado anteriormente, o Unity 2018 LTS é compatível com a compilação de aplicativos ARM32, enquanto o Unity 2019.x é compatível com a compilação de aplicativos ARM32 e ARM64. O desenvolvimento para aplicativos ARM64 é preferível, pois há uma diferença substancial de desempenho. No entanto, isso exige que todas as [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) também sejam compiladas para o ARM64.

Examine todas as dependências de DLL em seu aplicativo. Recomendamos a remoção de dependências que não são mais necessárias para seu projeto. Para os plug-ins restantes que são necessários, ingira os respectivos binários do ARM32 ou do ARM64 no projeto do Unity.

Após a ingestão das DLLs relevantes, compile uma solução do Visual Studio por meio do Unity e, em seguida, compile um AppX para ARM no Visual Studio para testar se o aplicativo pode ser compilado para processadores ARM. É recomendável salvar o aplicativo como uma confirmação na solução de controle do código-fonte.

> [!IMPORTANT]
> O uso do MRTK v1 do aplicativo pode ser executado no HoloLens 2 após a alteração do destino de build para o ARM, supondo que todos os outros requisitos sejam atendidos. Isso inclui verificar se todos os plug-ins têm versões do ARM. No entanto, seu aplicativo não terá acesso a funções específicas do HoloLens 2, como acompanhamento ocular e mão articulada. O MRTK v1 e o MRTK v2 têm namespaces diferentes que permitem que ambas as versões estejam no mesmo projeto, o que é útil para fazer a transição de uma para a outra.

## <a name="update-to-mrtk-version-2"></a>Atualizar para o MRTK versão 2

[A versão 2 do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity) é o novo kit de ferramentas baseado no Unity que dá suporte ao HoloLens (1ª geração) e ao HoloLens 2. É nela também em que todas as funcionalidades do HoloLens 2 foram adicionadas, como interações com as mãos e acompanhamento ocular.

Confira os seguintes recursos para obter mais informações sobre como usar o MRTK versão 2:

- [MRTK – Página inicial da documentação](/windows/mixed-reality/mrtk-unity)
- [Guia de instalação](/windows/mixed-reality/mrtk-unity/install-the-tools)
- [MRTK – Acompanhamento da mão](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
- [MRTK – Acompanhamento ocular](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

### <a name="prepare-for-the-migration"></a>Preparar a migração

Antes da ingestão dos novos arquivos [*.unitypackage para o MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), é recomendável fazer um inventário de **1) qualquer código personalizado integrado ao MRTK v1** e **2) qualquer código personalizado para interações de entrada ou componentes de experiência do usuário**. O conflito mais comum e predominante para um desenvolvedor de realidade misturada que ingere o MRTK v2 envolve a entrada e as interações. É recomendável começar a ler e entender o [modelo de entrada do MRTK v2](/windows/mixed-reality/mrtk-unity/features/input/overview).

Por fim, o novo [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) fez a transição de um modelo de scripts e objetos de gerenciador na cena para uma configuração e uma arquitetura de provedor de serviços. Isso resulta em um modelo de arquitetura e hierarquia de cena mais limpo, mas exige uma curva de aprendizado para entender os novos perfis de configuração. Leia o [Guia de Configuração do Kit de Ferramentas de Realidade Misturada](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) para começar a se familiarizar com os perfis e as configurações importantes para se ajustar às necessidades de seu aplicativo.

### <a name="migrating-the-project"></a>Migrar o projeto

Após a importação do [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), provavelmente, seu projeto do Unity terá muitos erros relacionados ao compilador. Esses se devem comumente à nova estrutura de namespace e aos novos nomes de componentes. Continue resolvendo esses erros por meio da modificação dos scripts para os novos namespaces e componentes.

Para obter informações sobre as diferenças de API específicas entre o HTK/MRTK e o MRTK v2, confira o guia de portabilidade no [wiki do MRTK versão 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide).

### <a name="best-practices"></a>Práticas recomendadas

- Prefira o uso do [sombreador padrão do MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).
- Trabalhe em um tipo de alteração da falha por vez (por exemplo: IFocusable para [IMixedRealityFocusHandler](/dotnet/api/microsoft.mixedreality.toolkit.input.imixedrealityfocushandler)).
- Faça um teste após cada alteração e use o controle do código-fonte.
- Use a experiência do usuário padrão do MRTK (botões, imagens fixas e assim por diante), quando possível.
- Evite modificar os arquivos do MRTK diretamente; em vez disso, crie wrappers em torno de componentes do MRTK.
  - Essa ação facilita futuras ingestões e atualizações do MRTK.
- Examine e explore cenas de exemplo fornecidas no MRTK, especialmente *HandInteractionExamples.scene*.
- Recompile a interface do usuário baseada em tela com quadrantes, colisores e texto do TextMeshPro.
- Habilite o [Compartilhamento de buffer de profundidade](../unity/camera-in-unity.md#sharing-depth-buffers) ou [defina o ponto de foco](../unity/focus-point-in-unity.md); prefira usar um buffer de profundidade de 16 bits para ter melhor desempenho. Verifique se, ao renderizar a cor, você também renderiza a profundidade. O Unity geralmente não grava profundidade para gameobjects de texto e transparentes.
- Defina o caminho de renderização instanciado de passagem única.
- Usar o [perfil de configuração do HoloLens 2 para MRTK](/windows/mixed-reality/mrtk-unity/features/profiles/profiles#hololens-2-profile)

### <a name="testing-your-application"></a>Testando seu aplicativo

No MRTK Versão 2, você pode simular as interações com as mãos diretamente no Unity e desenvolver novas APIs para interações com as mãos e acompanhamento ocular. O dispositivo HoloLens 2 é necessário para criar uma experiência de usuário satisfatória. Para adquirir uma melhor compreensão, é recomendável que você comece a estudar a documentação e as ferramentas. O [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) é compatível com o desenvolvimento no HoloLens (1ª geração) e, assim, os modelos de entrada tradicionais (tais como selecionar por meio do gesto de fechar e abrir dedos indicador e polegar) podem ser testados no HoloLens (1ª geração). 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Como atualizar o modelo de interação para o HoloLens 2

> [!CAUTION]
> Se o seu projeto está usando uma das APIs do XR.WSA, elas estão sendo desativadas em favor das novas APIs de entrada de XR do Unity nas versões futuras do Unity. Encontre mais informações sobre as [APIs de entrada de XR aqui](https://docs.unity3d.com/Manual/xr_input.html).

Depois que o aplicativo for portado e preparado para o HoloLens 2, você estará pronto para considerar a atualização do modelo de interação e dos posicionamentos de design dos hologramas.
No HoloLens (1ª geração), o aplicativo provavelmente tem um modelo de interação de foco e confirmação com hologramas relativamente distantes para se ajustarem ao campo de visão.

Etapas para atualizar o design de seu aplicativo a fim de torná-lo mais adequado para o HoloLens 2:
1.  Componentes do MRTK: De acordo com o trabalho prévio, se você tiver adicionado o [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), haverá vários componentes/scripts a serem aproveitados que foram projetados e otimizados para o HoloLens 2.

2.  Modelo de interação: Considere a atualização do modelo de interação. Para a maioria dos cenários, recomendamos a alternância do foco e da confirmação com as mãos. Com os hologramas normalmente ficando fora do alcance dos braços, a alternância para as mãos resulta em raios de apontador de interação e gestos de segurar distantes.

3.  Posicionamento de hologramas: Depois de alternar para um modelo de interação com as mãos, considere a aproximação de alguns hologramas, a fim de interagir diretamente com eles usando gestos de segurar com interação próxima com as mãos. Os tipos de hologramas recomendados para aproximação a fim de segurar ou interagir diretamente são menus de destino menores, controles, botões e hologramas menores que se ajustam ao campo de visão do HoloLens 2 ao segurar e inspecionar o holograma.
<br>
Cada aplicativo e cenário é diferente. Continuaremos refinando e postando diretrizes de design com base nos comentários e em aprendizados contínuos.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Advertências e aprendizados adicionais sobre como mover aplicativos do x86 para o ARM

- Os aplicativos diretos do Unity são simples porque você pode criar um pacote de aplicativo ARM ou implantá-lo diretamente no dispositivo para que o pacote seja executado. Alguns plug-ins nativos do Unity podem apresentar certos desafios de desenvolvimento. Por isso, você deve atualizar todos os plug-ins nativos do Unity para o Visual Studio 2019 e, em seguida, recompilar para o ARM.

- Um aplicativo usou o plug-in AudioKinetic Wwise para Unity, e essa versão do Unity não tinha um plug-in do ARM para UWP. Como resultado, houve um esforço considerável para recriar as funcionalidades de som no aplicativo em questão para execução no ARM. Verifique se todos os plug-ins necessários para os planos de desenvolvimento estão instalados e disponíveis no Unity.

- Em alguns casos, um plug-in do UWP/ARM pode não existir para os plug-ins requeridos pelo aplicativo, o que bloqueia a capacidade de portar o aplicativo e executá-lo no HoloLens 2. Entre em contato com seu provedor de plug-in para resolver o problema e fornecer suporte para o ARM.

- O minfloat (e variantes como min16float, minint e assim por diante) em sombreadores pode se comportar de modo diferente no HoloLens 2 comparado ao HoloLens (1ª geração). Especificamente, eles garantem que pelo menos o número especificado de bits seja usado. Em GPUs da Intel/da NVIDIA, os minfloats são basicamente tratados como 32 bits. No ARM, o número de bits especificado é realmente respeitado. Isso significa que, na prática, esses números podem ter menos precisão ou alcance no HoloLens 2 do que tinham no HoloLens (1ª geração).

- As instruções de _asm não parecem funcionar no ARM, o que significa que qualquer código que use as instruções de _asm precisa ser reescrito.

- O ARM não dá suporte à instrução SIMD definida porque vários cabeçalhos, como xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h, não estão disponíveis no ARM.

- O compilador de sombreador no ARM é executado durante a primeira chamada de desenho depois que o sombreador é carregado ou algo do qual o sombreador depende é alterado, não no tempo de carregamento do sombreador. O impacto na taxa de quadros pode ser perceptível, dependendo de quantos sombreadores precisam ser compilados, com implicações de como os sombreadores devem ser tratados, empacotados e atualizados de maneira diferente no HoloLens 2 versus HoloLens (1ª geração).

## <a name="see-also"></a>Veja também

* [Instalar as ferramentas](../install-the-tools.md)
* [MRTK – Guia de instalação](/windows/mixed-reality/mrtk-unity/install-the-tools)
* [MRTK – Página inicial da documentação](/windows/mixed-reality/mrtk-unity)
* [Portabilidade do HoloToolkit/MRTK para o MRTK versão 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
* [Configurações recomendadas do Unity](../unity/recommended-settings-for-unity.md)
* [Noções básicas sobre o desempenho da Realidade Misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)