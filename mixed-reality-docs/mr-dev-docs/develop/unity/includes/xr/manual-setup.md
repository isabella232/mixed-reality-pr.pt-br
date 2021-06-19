---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394580"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Configurando seu destino de compilação

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1. Selecione **arquivo > configurações de Build...**
2. Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3. Defina a **Arquitetura** como **ARM 64**
4. Defina o **Dispositivo de destino** como **HoloLens**
5. Defina o **Tipo de Build** como **D3D**
6. Defina o **SDK do UWP** como **Último instalado**

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plugin XR para OpenXR

Para definir OpenXR como o tempo de execução no Unity:

1. No editor do Unity, navegue até **editar > configurações do projeto**
2. Na lista de configurações, selecione **Gerenciamento de plugin XR**
3. Verifique as caixas **inicializar XR nas Startup** e **OpenXR**
4. Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](../../images/openxr-img-08.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso amarelo ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para aprender a usar os exemplos de OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Projetos de exemplo do Unity para OpenXR e HoloLens 2

Confira o [repositório de exemplos de realidade misturada OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo de Unity mostrando como criar aplicativos de Unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR de realidade misturada.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  Selecione **arquivo > configurações de Build...**
2.  Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Defina a **Arquitetura** como **ARM 64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina o **Tipo de Build** como **D3D**
6.  Defina o **SDK do UWP** como **Último instalado**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada:

1. No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**

2. Selecione **instalar o gerenciamento de plugin XR**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](../../images/wmr-config-img-5.png)

3. Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](../../images/wmr-config-img-7.png)

4. Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**
5. Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar a realidade do **OpenXR** ou do **Windows Mixed**. 
    * Você pode escolher qualquer tempo de execução.  Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir experimentar o **OpenXR**, selecione a caixa OpenXR e examine nosso guia para [usar o plug-in de realidade misturada do OpenXR para](../../openxr-getting-started.md) que o Unity se prepare corretamente para esses dispositivos antes de retornar a este tutorial

> [!NOTE]
> A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.  À medida que migramos para esse caminho, no Unity 2021,1, o plug-in do Windows XR será preterido e removido em 2021,2, tornando OpenXR o único caminho com suporte. Você pode encontrar mais informações sobre como [usar o plug-in OpenXR de realidade misturada](../../openxr-getting-started.md).

6. Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  Selecione **arquivo > configurações de Build...**
2.  Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Defina a **Arquitetura** como **ARM 64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina o **Tipo de Build** como **D3D**
6.  Defina o **SDK do UWP** como **Último instalado**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada.

> [!CAUTION]
> O XR herdado é preterido no Unity 2019 e removido no Unity 2020.

1. Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**
2. Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual
3. Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**
4. Definir **modo de renderização estéreo** para **instância de passagem única**
5. Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](../../images/wmr-config-img-9.png)