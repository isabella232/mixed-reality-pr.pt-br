---
ms.openlocfilehash: c5276943bab0ddc961342f879c0cf4f8986aa7b4f67b16c9c8b5415ca6fc58fd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202694"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Instale o plug-in OpenXR com o novo aplicativo Ferramenta de Recursos de Realidade Misturada. Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR de Realidade Misturada** na categoria **Suporte à** Plataforma:

![Janela de pacotes da Ferramenta de Recursos de Realidade Misturada com o plug-in xr aberto realçada](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Definindo seu destino de build

Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela Configurações build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando HoloLens 2, será necessário alternar para a Plataforma de Windows Universal:

1. Selecione **Arquivo > Build Configurações...**
2. Selecione **Plataforma Windows Universal** na lista Plataforma e selecione **Alternar Plataforma**
3. Defina **Arquitetura** como **ARM64**
4. Defina o **Dispositivo de destino** como **HoloLens**
5. Defina **Tipo de Build** como **Projeto D3D**
6. Definir **a versão do SDK de Destino** como a mais recente **instalada**

![Captura de tela da janela Configurações build aberta no editor do Unity com a Plataforma universal Windows realçada](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plug-in XR para OpenXR

Para definir o OpenXR como o runtime no Unity:

1. No Editor do Unity, navegue até **Editar > Project Configurações**
2. Na lista de Configurações, selecione Gerenciamento de **Plug-in XR** (já deve estar instalado se você instalou o plug-in OpenXR de Realidade Misturada usando o MRFT)
3. Marque a **caixa Inicializar XR na inicialização**
4. Se estiver direcionando a VR da Área de Trabalho, permaneça na guia PC Autônomo (o monitor) e marque as caixas de conjunto de recursos **OpenXR** **e Windows Mixed Reality aplicativo**
5. Se estiver direcionando HoloLens 2, alternar para a guia Plataforma Universal Windows (o logotipo do Windows) e selecione **as caixas** de conjunto de recursos **OpenXR** e Microsoft HoloLens

![Captura de tela do painel de configurações do projeto aberto no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso amarelo ao lado de **Plug-in OpenXR,** clique no ícone e selecione **Corrigir Tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Se você estiver desenvolvendo para o HoloLens 2, selecione o item de menu Aplicar configurações de projeto > Project > Realidade Misturada para HoloLens **2** para obter um melhor desempenho do aplicativo.

![Captura de tela do item de menu de realidade misturada aberto com OpenXR selecionado](../../images/openxr-img-08.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para saber como usar os exemplos do OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Projetos de exemplo do Unity para OpenXR e HoloLens 2

Confira o repo de exemplos do [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos do Unity de exemplo mostrando como criar aplicativos unity para headsets do HoloLens 2 ou realidade misturada usando o plug-in OpenXR de Realidade Misturada.

Ou, se você estiver pronto para começar por conta própria de um projeto em branco, vá para o [artigo Configuração da](../../camera-in-unity.md) câmera.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

> [!CAUTION]
> O Windows plug-in XR foi preterido no Unity 2021.1 e será removido no Unity 2021.2.  Para o desenvolvimento do Unity 2020, a Microsoft recomenda o plug-in OpenXR.

Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela Configurações build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando HoloLens 2, será necessário alternar para a Plataforma de Windows Universal:

1.  Selecione **Arquivo > Build Configurações...**
2.  Selecione **Plataforma Windows Universal** na lista Plataforma e selecione **Alternar Plataforma**
3.  Defina **Arquitetura** como **ARM64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina **Tipo de Build** como **Projeto D3D**
6.  Definir **a versão do SDK de Destino** como a mais recente **instalada**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela Configurações build aberta no editor do Unity com a Plataforma universal Windows realçada](../../images/wmr-config-img-4.png)

Depois de configurar sua plataforma, você precisa [](../../../../design/app-views.md) permitir que o Unity saiba para criar uma exibição imersiva em vez de uma exibição 2D quando exportada:

1. No Editor do Unity, navegue até **Editar > Project configurações e** selecione Gerenciamento de **Plug-in XR**

2. Selecione **Instalar o Gerenciamento de Plug-in XR** se ele aparecer

![Captura de tela Project Configurações janela aberta no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/wmr-config-img-5.png)

3. Selecione **Inicializar XR na Inicialização** **e Windows Mixed Reality**

![Captura de tela Project janela configurações aberta no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/wmr-config-img-7.png)

4. Selecione a seção Gerenciamento de **Plug-inS XR** Windows Mixed Reality, marque todas as caixas e de conjunto Formato do Buffer de Profundidade como  >   Buffer de **Profundidade 16 Bits** 

![Captura de tela Project janela configurações aberta no editor do Unity com a Windows Mixed Reality realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

> [!CAUTION]
> O XR herdado foi preterido no Unity 2019 e removido no Unity 2020.

Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela Configurações build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

Se você estiver direcionando HoloLens 2, será necessário alternar para a Plataforma de Windows Universal:

1.  Selecione **Arquivo > Build Configurações...**
2.  Selecione **Plataforma Windows Universal** na lista Plataforma e selecione **Alternar Plataforma**
3.  Defina **Arquitetura** como **ARM64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina **Tipo de Build** como **Projeto D3D**
6.  Definir **a versão do SDK de Destino** como a mais recente **instalada**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela Configurações build aberta no editor do Unity com a Plataforma universal Windows realçada](../../images/wmr-config-img-4.png)

Depois de configurar sua plataforma, você precisa permitir que o Unity saiba para criar uma [exibição](../../../../design/app-views.md) imersiva em vez de uma exibição 2D quando exportada.

1. Abra **o player Configurações...** no **build Configurações... janela** e expanda o **grupo de Configurações** XR
2. Na seção **XR Configurações,** selecione **Realidade Virtual Com** Suporte para adicionar a lista Dispositivos de Realidade Virtual
3. Definir **formato de profundidade** como profundidade de **16 bits e marque** Habilitar **Compartilhamento de Buffer de Profundidade**
4. Defina **Modo de renderização estéreo** como **Instanciado de passagem única**
5. Selecione **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting

![Captura de tela Project janela configurações aberta no editor do Unity com a seção Configurações do player realçada](../../images/wmr-config-img-9.png)
