---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603700"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade misturada** na categoria **suporte à plataforma** :

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Configurando seu destino de compilação

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1. selecione **arquivo > Build Configurações...**
2. selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**
3. Defina **Arquitetura** como **ARM64**
4. Defina o **Dispositivo de destino** como **HoloLens**
5. Defina **Tipo de Build** como **Projeto D3D**
6. Definir a **versão do SDK de destino** para a **última instalação**

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plugin XR para OpenXR

Para definir OpenXR como o tempo de execução no Unity:

1. no Editor do Unity, navegue até **editar > Project Configurações**
2. na lista de Configurações, selecione **gerenciamento de Plugin XR** (já deve estar instalado se você instalou o plug-in OpenXR de realidade misturada usando MRFT)
3. Marque a caixa **inicializar XR na inicialização**
4. se for destinado à área de trabalho VR, permaneça na guia autônoma do PC (o monitor) e marque as caixas de **conjunto de recursos** **OpenXR** e Windows Mixed Reality
5. se estiver direcionando HoloLens 2, alterne para a guia Plataforma Universal do Windows (o logotipo Windows) e selecione as caixas **conjunto de recursos** **OpenXR** e Microsoft HoloLens

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso amarelo ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

se você estiver desenvolvendo para o HoloLens 2, selecione a **realidade misturada > Project > aplicar configurações de projeto recomendadas para o item de menu HoloLens 2** para obter melhor desempenho do aplicativo.

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](../../images/openxr-img-08.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para aprender a usar os exemplos de OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>projetos de exemplo do Unity para OpenXR e HoloLens 2

confira o [repositório de exemplos de realidade misturada do OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo do unity mostrando como criar aplicativos do unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR da realidade misturada.

Ou, se você estiver pronto para começar por conta própria em um projeto em branco, vá para o artigo de [configuração da câmera](../../camera-in-unity.md) .

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> o plug-in Windows XR foi preterido no unity 2021,1 e será removido no unity 2021,2.  Para o desenvolvimento do Unity 2020, a Microsoft recomenda o plug-in OpenXR.

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  selecione **arquivo > Build Configurações...**
2.  selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Defina **Arquitetura** como **ARM64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina **Tipo de Build** como **Projeto D3D**
6.  Definir a **versão do SDK de destino** para a **última instalação**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada:

1. no Editor do Unity, navegue até **editar > configurações de Project** e selecione **gerenciamento de Plugin XR**

2. Selecione **instalar o gerenciamento de plugin XR** se ele aparecer

![captura de tela da janela Project Configurações aberta no editor do unity com o gerenciamento de Plugin XR realçado](../../images/wmr-config-img-5.png)

3. selecione **inicializar XR na inicialização** e **Windows Mixed Reality**

![captura de tela da janela configurações de Project abrir no editor do unity com o gerenciamento de Plugin XR realçado](../../images/wmr-config-img-7.png)

4. selecione a seção Windows Mixed Reality de **gerenciamento de Plug-in do XR**  >   , marque todas as caixas e defina o **formato do buffer** de profundidade para o **Buffer de profundidade 16 bits**

![captura de tela da janela configurações de Project abrir no editor do unity com a seção Windows Mixed Reality realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

> [!CAUTION]
> O XR herdado é preterido no Unity 2019 e removido no Unity 2020.

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  selecione **arquivo > Build Configurações...**
2.  selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Defina **Arquitetura** como **ARM64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina **Tipo de Build** como **Projeto D3D**
6.  Definir a **versão do SDK de destino** para a **última instalação**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada.

1. abrir **Player Configurações...** do **Configurações de compilação... janela** e expandir o grupo de **Configurações XR**
2. na seção **Configurações do XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual
3. Defina o **formato de profundidade** como profundidade de **16 bits** e marque **Habilitar compartilhamento de buffer de profundidade**
4. Defina **Modo de renderização estéreo** como **Instanciado de passagem única**
5. Selecione **WSA Holographic Remoting com suporte** se você quiser usar a comunicação remota do modo de reprodução do Holographic

![captura de tela da janela configurações do Project abrir no editor do unity com a seção configurações do Player realçada](../../images/wmr-config-img-9.png)
