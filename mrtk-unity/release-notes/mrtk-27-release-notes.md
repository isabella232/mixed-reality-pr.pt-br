---
title: Notas sobre a versão do MRTK 2.7
description: Notas sobre a versão do MRTK versão 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, XRSDK, XR Herdado, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 921cdb4d9643e55841bc7c979066c276f5fd80998ad97d19332c528cebe05c37
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203468"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notas sobre a versão do Kit de Ferramentas de Realidade Misturada 2.7 da Microsoft

## <a name="whats-new-in-272"></a>Novidades na versão 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Corrigido um problema de dependência de pacote UPM

Havia um problema com os pacotes UPM do MRTK 2.7.1 em que as dependências não eram configuradas corretamente. O problema fazia com que a Ferramenta de Recursos de Realidade Misturada não importasse corretamente os pacotes do MRTK 2.7.1. Agora o problema está resolvido na versão 2.7.2. Não houve alteração de código nesta versão em comparação com a 2.7.1.


## <a name="whats-new-in-271"></a>Novidades na versão 2.7.1

### <a name="show-version"></a>Mostrar versão

O menu `Mixed Reality` > `Toolkit` agora contém uma entrada `Show version...` que examina o pacote do Kit de Ferramentas de Realidade Misturada Foundation para determinar a versão do MRTK que está sendo usada pelo projeto.

![Mostrar menu de versão](images/ShowVersionMenu.png)

![Caixa de diálogo de versão do MRTK](images/VersionDialog.png)

> [!NOTE]
> Se o MRTK tiver sido clonado do [repositório do GitHub](https://aka.ms/mrtk), as informações sobre a versão não terão sido definidas.
>
> ![Impossível determinar a versão](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Lista de autores

A partir do MRTK 2.7.1, o arquivo com a lista de autores é incluído no pacote do Kit de Ferramentas de Realidade Misturada Foundation.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>Configuração integrada do projeto OpenXR no fluxo de configuração do Configurador

Do MRTK 2.7.1 em diante, os usuários do plug-in OpenXR de Realidade Misturada receberão instruções sobre como configurar esse plug-in com o MRTK. Há uma opção para que os usuários que visam ao HoloLens 2 apliquem automaticamente as configurações recomendadas.

![Janela do Configurador com instruções de configuração do OpenXR](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Alterações e correções de bugs importantes

- Unity Joystick Manager marcado como compatível no pipeline do SDK de XR [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- Adicionadas verificações ao código inspetor interativo para evitar erros nulos [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- Adicionar provedor de malha OpenXR à cena de exemplo do sombreador de pulso [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- Restaurar o perfil de física manual para a cena de exemplo [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- Algumas limpezas para os scripts HandConstraint* [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- Correção de alguns bugs que afetavam a criação e a clonagem de perfis [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>Novidades na versão 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>Agora o OpenXR é oficialmente compatível com o MRTK

À medida que os novos plug-ins do OpenXR estão se tornando cada vez mais maduros, o MRTK agora é oficialmente compatível com o OpenXR. Em comparação com as versões anteriores, adicionamos os seguintes recursos aos projetos que usam o OpenXR:

- [Suporte para o modelo de controlador de movimentos fornecido pelo sistema](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Suporte para gestos do WinMR (selecionar, segurar, manipular e navegar) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Suporte para controlador tátil](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Suporte para malha de mão articulada no HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Suporte para Mapeamento Espacial no HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Suporte para Compreensão de Cena no HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

Se você estiver visando ao HoloLens 2 ou aos headsets do Windows Mixed Reality por meio do OpenXR, instale/atualize para o **plug-in OpenXR de Realidade Misturada versão 0.9.5 ou posterior** por meio da [Ferramenta de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool), caso contrário, você poderá perder algumas das melhorias acima.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Provedores de Dados de XR Herdados e do SDK de XR agora podem ser usados dentro do mesmo perfil

Os provedores de dados agora também só serão carregados quando o pipeline apropriado estiver selecionado, permitindo que os provedores de dados de XR Herdados e do SDK de XR coexistam dentro do mesmo perfil. Para acomodar isso, os Provedores de Dados de XR Herdados e do SDK de XR agora são organizados em guias diferentes dentro da exibição de perfil, ajudando os usuários a determinar se estão com o perfil correto para o pipeline de XR visado por eles.

![Os provedores de dados de XR Herdados e do SDK de XR agora podem ser unificados em um único perfil](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Para acomodar isso, os provedores de dados nulos agora não serão mais carregados e exibidos no inspetor de perfil. Os usuários podem alternar `Show null data providers in the profile inspector` em **Editar -> Configurações de Projeto -> Kit de Ferramentas de Realidade Misturada** para depurar comportamentos inesperados com provedores de dados ausentes.

![Os provedores de dados nulos agora ficam ocultos por padrão](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Alternar para mostrar provedores de dados nulos no inspetor de perfil](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Adicionadas Configurações de Experiência e um comportamento associado ao Conteúdo da Cena de Realidade Misturada

Agora, os usuários podem definir [Configurações de Experiência](../features/experience-settings/experience-settings.md), o que permitirá ao MRTK exibir o [Conteúdo da Cena de Realidade Misturada](../features/experience-settings/scene-content.md) adequadamente com base na experiência visada.

Se as configurações anteriores de Escala de Experiência do usuário não corresponderem ao novo Perfil de Configurações de Experiência, ele será solicitado a corrigi-lo no inspetor

![Migração de escala da experiência](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>O Configurador Reprojetado agora orienta o usuário ao longo do processo de configuração

O novo configurador do MRTK fornece aos usuários orientações passo a passo para configurar corretamente o projeto para desenvolvimento e uso de XR com o MRTK. Ele aborda a seleção do pipeline de XR, a obtenção dos plug-ins específicos da plataforma, a importação do TextMeshPro, a exibição dos exemplos (ao usar o UPM) e outras configurações recomendadas incluídas anteriormente no projeto.

![Configurador mostrando a lista de pipelines](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Hotspot de teletransporte graduado

Um novo [componente de hotspot de teletransporte](../features/teleport-system/teleport-hotspot.md) foi graduado. Você pode adicionar um hotspot de teletransporte ao seu GameObject para garantir que o usuário esteja em uma determinada posição e orientação quando se teletransportar para aquele local.

![Exemplo de Hotspot de Teletransporte](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Mudança de nível do recurso de espera

O recurso de espera e o exemplo saíram do nível experimental. Novos exemplos de botões volumétricos no estilo do HoloLens 2 foram incluídos na cena de exemplo.

![Destaque do recurso de espera](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Adicionado suporte para Módulos do Leap Motion no Unity versão 4.6.0, 4.7.0, 4.7.1 e 4.8.0

O suporte para as últimas versões dos [Módulos do Leap Motion no Unity](https://developer.leapmotion.com/unity) agora são compatíveis com o MRTK 2.7.0. Confira [Como configurar o MRTK para o Leap Motion](../supported-devices/leap-motion-mrtk.md) a fim de obter mais informações.

Muito obrigado a @jackyangzzh por contribuir com a nova cena LeapMotionOrientationExample.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Os eventos de fala direcionados gerados não são mais restritos aos ponteiros de foco

Anteriormente, os eventos de fala direcionados só podiam ser gerados em objetos focados com o ponteiro de foco. Agora, os objetos poderão receber eventos de fala se forem focados com qualquer ponteiro.

![Eventos de Fala com Ponteiros Distantes](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>TextToSpeech portado do HTK para o MRTK

Agora o amado script TextToSpeech está finalmente disponível no MRTK para ajudar a converter texto em fala na plataforma UWP usando [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer). Também foi adicionada uma cena de exemplo para demonstrar o recurso.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Suporte para o modelo de controlador de movimentos fornecido pelo sistema no OpenXR

Adicionado suporte, tanto no editor quanto no runtime, para o modelo de controlador de movimentos fornecido pelo sistema no OpenXR.

![Janela do editor mostrando dois modelos de controlador de movimentos](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Suporte para malha manual articulada do HoloLens 2 no OpenXR

![A malha manual em execução no dispositivo em uma cena de exemplo do MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Suporte para controladores táteis no WMR herdado, no Plug-in de XR do Windows e no OpenXR

Adicionado suporte para controladores táteis no WMR herdado, no Plug-in de XR do Windows e no OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Suporte para acompanhamento ocular no Plug-in de XR do Windows

Adicionado suporte para o foco ocular ao usar as versões mínimas do Plug-in de XR do Windows de 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) e 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Alterações e correções de bugs importantes

- A detecção do gesto de pinçagem tornou-se mais suave. Agora está mais difícil soltar acidentalmente o gesto de pinçagem. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Os objetos com o componente Manipulador de Objetos agora mantêm consistentemente a velocidade na versão quando o sinalizador está definido. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Agora, o deslocamento para trás verifica se há um piso, ajudando a evitar situações em que a câmera era deslocada para dentro do ambiente ou do local em que o usuário ficava flutuando no espaço vazio. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject agora é uma propriedade virtual, permitindo mais flexibilidade ao estender o ponteiro de esfera ou de apontar. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Agora os botões exibem a palavra-chave apropriada ao mostrar o comando de fala disponível. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Os Controladores Oculus agora usam seu próprio visualizador autônomo, impedindo que a visualização do MRTK entre em conflito com a visualização do Pacote de Integração do Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Scripts relacionados ao teclado foram alterados para se alinhar ao comportamento nas últimas versões do Unity (2019.4.25+ e 2020.3.2+). Desde o lançamento, ainda há um bug no preenchimento automático e um bug no campo de entrada TMP (ambos são externos ao MRTK) que impactam o HoloLens. Para obter mais informações, confira [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) e [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Melhorado o desempenho da coleção de objetos de rolagem. Também foi corrigido um problema que fazia com que o GameObject dentro da coleção perdesse material ao ser duplicado. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- No script de demonstração para Compreensão da Cena, adicionada a função `GetSceneObjectsOfType` para recuperar todos os objetos de um determinado tipo na cena em observação. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Na ferramenta de build da linha de comando, somente as cenas especificadas pelos sinalizadores `sceneList` ou `sceneListFile` (quando qualquer sinalizador estiver presente) serão incluídas no build. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Na ferramenta de build, há uma nova opção para especificar um caminho para `nuget.exe` e usá-lo para executar a restauração do pacote em vez de usar `msbuild` (a opção padrão). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Correção do problema em que usar o Plug-in de XR do Windows podia resultar em junções manuais obsoletas e malhas manuais duplas. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Corrigido o problema em que o uso do recurso de controle remoto automático do Plug-in de XR do Windows levava à perda de entradas e interações. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Corrigido o problema em que o BuildDeployWindow tentava consultar uma chave de registro inválida para o caminho do SDK do Windows. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Os importadores de glTF do MRTK agora são opcionais. Se houver vários importadores de glTF presentes, os do MRTK poderão ser desabilitados adicionando-se `MRTK_GLTF_IMPORTER_OFF` aos símbolos de definição de scripting personalizado. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Corrigido o problema em que os controladores Knuckles do OpenVR não estavam sendo detectados corretamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Reduza o número de alocações por quadro ao visualizar a malha manual [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Adicionado um item de menu para iniciar o pacote de exemplos do MRTK (no Gerenciador de Pacotes do Unity) para facilitar a importação de exemplos [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Reduzido o número de avisos sobre o tempo de carga ao usar o Unity 2020.3.
- Adicionada a documentação de recurso da Janela de Build: [visite a página](../features/tools/build-window.md)

## <a name="known-issues"></a>Problemas conhecidos

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Falta um arquivo asmdef nas demonstrações de áudio (pacote UPM)

Ao importar o MRTK por meio da Ferramenta de Recursos de Realidade Misturada, os exemplos e as demonstrações são adicionados ao projeto usando a interface do usuário do Gerenciador de Pacotes do Unity. Após importar as demonstrações de áudio, a cena `WindowsMicrophoneStreamDemo.unity` não se comportará corretamente. Isso é resultado da falta de um arquivo. asmdef no exemplo.

Para contornar esse [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), execute as seguintes etapas:

- Copie Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef para a pasta "Assets/Samples/Mixed Reality Toolkit Examples"
- Renomeie o arquivo copiado para Exemplos
- Abra o arquivo Exemplos
- Na caixa Nome, substitua o conteúdo por Exemplos
- Clique em Aplicar
- Criar e implantar

Esse problema será corrigido em uma versão futura do MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>A janela de build do MRTK aciona a caixa de diálogo indefinida "Importando ativos" no Unity 2020.3

Há um [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) conhecido com a janela de build do MRTK no Unity 2020.3 que faz com que a caixa de diálogo "Importando ativos" não seja concluída após executar com sucesso um build da UWP. Esse problema está sendo investigado em parceria com o Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avisos do Renderizador de Telas do Text Mesh Pro no Unity 2020

O seguinte aviso é registrado na maioria das cenas de exemplo do MRTK ao usar o Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Avisos do Renderizador de Telas foram adicionados ao [TextMeshPro versão 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3). Esses avisos não têm impacto sobre as cenas de exemplo do MRTK e podem ser apagados do console. Confira o [problema 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) para obter mais detalhes.