---
title: Notas de versão do MRTK 2,7
description: notas de versão do MRTK versão 2,7
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, XRSDK, Legacy XR, movimento Leap, Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897399"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notas de versão do Microsoft Mixed Reality Toolkit 2,7

## <a name="whats-new-in-270"></a>O que há de novo no 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>O OpenXR agora é oficialmente suportado em MRTK

Como os novos plug-ins OpenXR estão se tornando cada vez mais maduros, o MRTK agora dá suporte oficialmente a OpenXR. Em comparação com as versões anteriores, adicionamos os seguintes recursos aos projetos usando o OpenXR:

- [Suporte para o modelo de controlador de movimento fornecido pelo sistema](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Suporte para gestos de WinMR (seleção, retenção, manipulação e navegação) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Suporte para controlador haptics](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Suporte para malha de lado articulado no HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Suporte para mapeamento espacial em [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)do HoloLens 2, [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Suporte para a compreensão da cena no HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Os provedores de dados do SDK XR e XR herdados agora podem ser usados dentro do mesmo perfil

Os provedores de dados agora também serão carregados apenas quando o pipeline apropriado for selecionado, permitindo que ambos os provedores de dados do SDK XR e XR herdados coexistam no mesmo perfil. Para acomodar isso, os provedores de dados do SDK XR e XR herdados agora estão organizados em guias diferentes na exibição de perfil, ajudando os usuários a determinar se eles têm o perfil correto para seu pipeline de XR direcionado.

![Os provedores de dados SDK do XR e do Legacy agora podem ser unificados em um único perfil](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Para acomodar isso, os provedores de dados nulos agora não serão mais carregados e exibidos no Inspetor de perfil. Os usuários podem alternar `Show null data providers in the profile inspector` em **configurações de projeto de > de edição – > kit de ferramentas de realidade misturada** para depurar comportamentos inesperados com provedores de dados ausentes.

![Os provedores de dados nulos agora estão ocultos por padrão ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ Alternar mostrar provedores de dados nulos no Inspetor de perfil](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Foram adicionadas configurações de experiência e um comportamento de conteúdo de cena de realidade misturada associado

Agora, os usuários podem configurar [as configurações de experiência](../features/experience-settings/experience-settings.md), o que permitirá que o MRTK exiba o [conteúdo da cena de realidade misturada](../features/experience-settings/scene-content.md) adequadamente com base na experiência de destino.

Se as configurações de escala de experiência anterior do usuário não corresponderem ao novo perfil de configurações de experiência, elas serão solicitadas a corrigi-lo no Inspetor

![Migração de escala de experiência](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>O configurador reprojetado agora orienta o usuário por meio do processo de instalação

O novo MRTK Configurator fornece instruções passo a passo para configurar corretamente o projeto para o desenvolvimento e o uso do XR com o MRTK. Ele aborda a seleção do pipeline XR, obtendo os plugins específicos da plataforma, importando TextMeshPro, exibindo os exemplos (ao usar o UPM) e outras configurações recomendadas anteriormente incluídas para o projeto.

![Configurador mostrando a lista de pipelines](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>HotSpot teleport graduado

Um novo [componente de HotSpot teleport](../features/teleport-system/teleport-hotspot.md) foi graduado. Você pode adicionar um ponto de teleport hotspot ao seu gameobject para garantir que o usuário esteja em uma determinada posição e orientação quando teleport a esse local.

![Exemplo de HotSpot teleport](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Pesquisa graduada

O recurso de pesquisa e o exemplo agora estão graduados de forma experimental. Novos exemplos de botões de estilo volumétricos HoloLens 2 estão incluídos na cena de exemplo.

![Herói de pesquisa](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Suporte adicionado para módulos do Unity de movimento Leap versão 4.6.0, 4.7.0, 4.7.1 e 4.8.0

O suporte para as versões mais recentes dos [módulos do movimento Leap do Unity](https://developer.leapmotion.com/unity) agora é compatível com MRTK 2.7.0.  Consulte [como configurar o MRTK para o movimento Leap](../supported-devices/leap-motion-mrtk.md) para obter mais informações.

Muito obrigado @jackyangzzh por contribuir com a nova cena de LeapMotionOrientationExample!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Eventos de fala de destino gerados não são mais restritos a ponteiros olhar

Anteriormente, os eventos de fala direcionados só podiam ser gerados em objetos que se concentraram no ponteiro olhar. Agora, os objetos podem receber eventos de fala se estiverem concentrados por qualquer ponteiro.

![Eventos de fala com ponteiros distantes](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>TextToSpeech portado de HTK para MRTK

O script amada TextToSpeech agora é finalmente disponibilizado no MRTK para ajudá-lo a gerar fala de texto na plataforma UWP usando o [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . Também foi adicionada uma cena de exemplo para demonstrar o recurso.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Suporte para o modelo de controlador de movimento fornecido pelo sistema em OpenXR

Suporte adicionado, tanto no editor quanto em tempo de execução, para o modelo de controlador de movimento fornecido pelo sistema em OpenXR.

![Janela do editor mostrando dois modelos de controlador de movimento](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Suporte para a malha do HoloLens 2 articulada no OpenXR

![A malha do lado em execução no dispositivo em uma cena de exemplo do MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Suporte para controlador haptics entre WMR herdados, plug-in Windows XR e OpenXR

Adição de suporte para controlador haptics entre WMR herdados, plug-in do Windows XR e OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Suporte para acompanhamento de olho no plug-in Windows XR

Adicionado suporte para olhar de olho ao usar as versões mínimas do plug-in do Windows XR do 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) e 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Bugs e alterações notáveis

- Detecção de pinçagem tornada mais suave. Agora é mais difícil descartar acidentalmente o gesto de pinçagem. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Objetos com o componente manipulador do objeto agora mantêm consistentemente a velocidade na liberação quando o sinalizador é definido. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- O back-strafing agora verifica se há um andar, ajudando a evitar situações em que a câmera pode ser recortada no ambiente ou onde o usuário está passando o mouse sobre o espaço vazio. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- Já é uma propriedade virtual, que permite mais flexibilidade ao estender o ponteiro de esfera ou de uma subseção. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Agora, os botões exibem a palavra-chave apropriada ao mostrar o comando de fala disponível. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Os controladores Oculus agora usam seu próprio visualizador autônomo, impedindo que a visualização do MRTK entre em conflito com a visualização do pacote de integração do Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Os scripts relacionados ao teclado foram alterados para alinhar-se com o comportamento nas versões mais recentes do Unity (2019.4.25 + & 2020.3.2 +). Desde o lançamento, ainda há um bug de preenchimento automático e um bug de campo de entrada TMP (ambos são externos ao MRTK) impactando o HoloLens. Para obter mais informações, consulte [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) e [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Melhorou o desempenho da coleta de objetos de rolagem. Também foi corrigido um problema que faz com que gameobject na coleção perca material quando duplicado. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- No script de demonstração de compreensão da cena, adicionou a `GetSceneObjectsOfType` função para recuperar todos os objetos de cena observados de um determinado tipo. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Na ferramenta de Build de linha de comando, somente as cenas especificadas pelos `sceneList` `sceneListFile` sinalizadores ou (quando qualquer sinalizador estiver presente) serão incluídas na compilação. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Na ferramenta de compilação, há uma nova opção para especificar um caminho `nuget.exe` e usá-lo para executar a restauração do pacote em vez de usar `msbuild` (a opção padrão). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Correção do problema em que usar o plug-in do Windows XR pode resultar em junções de mão obsoleta e malhas duplas. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Correção do problema em que o recurso de comunicação remota do plugin do Windows XR está sendo usado para a entrada e as interações ausentes. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Correção do problema em que o BuildDeployWindow tentaria consultar uma chave de reg inválida para o caminho de SDK do Windows. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Os importadores de glTF de MRTK agora são opcionais. Se vários importadores glTF estiverem presentes, o MRTK poderá ser desabilitado adicionando-se `MRTK_GLTF_IMPORTER_OFF` ao script personalizado definir símbolos. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Corrigido o problema em que os controladores Knuckles no OpenVR não estavam sendo detectados corretamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Reduza o número de alocações por quadro ao visualizar a malha à mão [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Adicionado um item de menu para iniciar o pacote de exemplos do MRTK (no Gerenciador de pacotes do Unity) para facilitar a importação de amostras [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Redução do número de avisos de tempo de carga ao usar o Unity 2020,3.
- Adicionada a documentação do recurso de janela de compilação: [visite a página](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Problemas conhecidos

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Um arquivo asmdef está faltando em demonstrações de áudio (pacote UPM)

Ao importar MRTK por meio da ferramenta de recursos misturados de realidade, os exemplos e as demonstrações são adicionados ao projeto usando a interface do usuário do Gerenciador de pacotes do Unity. Depois de importar as demonstrações de áudio, a `WindowsMicrophoneStreamDemo.unity` cena não se comportará corretamente. Isso é resultado de um arquivo. asmdef ausente para o exemplo.

Para contornar esse [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), execute as seguintes etapas:

- Copiar biblioteca/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...] /MRTK. Exemplos. asmdef na pasta "ativos/exemplos/exemplos do kit de ferramentas de realidade misturada"
- Renomeie o arquivo copiado para exemplos
- Abra o arquivo de exemplos
- Na caixa nome, substitua o conteúdo por exemplos
- Clique em aplicar
- Criar e implantar

Esse problema será corrigido em uma próxima versão do MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>A janela de Build do MRTK aciona a caixa de diálogo "importar ativos" indefinido no Unity 2020,3

Há um [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) conhecido com a janela de Build do MRTK no Unity 2020,3, em que, depois de executar com êxito uma compilação UWP, a caixa de diálogo "importando ativos" não é concluída. Esse problema está sendo investigado em parceria com o Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avisos do renderizador de Canvas pro de malha de texto no Unity 2020

O aviso a seguir é registrado na maioria das cenas de exemplo de MRTK ao usar o Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

O aviso do processador de tela foi adicionado no [TextMeshPro versão 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).  Esses avisos não têm impacto sobre as cenas de exemplo de MRTK e podem ser apagados do console. Consulte o [problema 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) para obter mais detalhes.
