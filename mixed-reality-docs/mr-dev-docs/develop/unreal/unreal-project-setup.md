---
title: Configuração do projeto Unreal
description: Saiba como configurar seu projeto com a versão mais recente do Unreal Engine e a Ferramenta de recursos de Realidade Misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realidade misturada, desenvolvimento, recursos, novo projeto, emulador, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, atualizado, ferramentas, introdução, noções básicas, unreal, kit de ferramentas, hub, instalação, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905549"
---
# <a name="setting-up-your-unreal-project"></a>Configuração do projeto Unreal

Recomendamos instalar o [Unreal Engine versão 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou posterior para aproveitar ao máximo o suporte interno ao HoloLens.

Acesse a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** e clique em **Opções**. Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.
![Opção de instalação do Unreal para HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importar Kit de Ferramentas de Realidade Misturada para Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

O MRTK (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.

Se você ainda não tiver um projeto de realidade misturada, siga as três primeiras seções dos [Tutoriais de introdução ao HoloLens 2](tutorials/unreal-uxt-ch1.md) para preparar um projeto para o MRTK.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>Apresentando o Hub MRTK para Unreal

Recomendamos que você use o Hub MRTK para adquirir plug-ins do MRTK. É uma nova maneira para os desenvolvedores descobrirem e atualizarem plug-ins de Realidade Misturada da Microsoft e adicioná-los aos próprios projetos do Unreal. Você pode exibir os plug-ins, ver as dependências deles e instalá-los em seu projeto sem sair do editor do Unreal.

- Descubra novos plug-ins da Realidade Misturada da Microsoft e instale-os com as respectivas dependências em seu projeto do Unreal.
- Mantenha seus plug-ins da Realidade Misturada da Microsoft atualizados.
- Remova os plug-ins da Realidade Misturada da Microsoft do seu projeto se você não precisar mais deles.

> [!NOTE]
> O Hub MRTK para Unreal está disponível somente para o Unreal Engine versão 4.26 ou posterior. Para a versão do mecanismo Unreal 4.25, você pode obter plug-ins MRTK do Marketplace do Unreal Engine ou do GitHub conforme descrito na [seção Introdução](unreal-development-overview.md#1-getting-started).

#### <a name="installing-the-mrtk-hub"></a>Instalando o Hub MRTK

Baixe o plug-in do [Marketplace do Unreal Engine](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub), abra o projeto e, em seguida, habilite o plug-in na seção _realidade Misturada_ do menu _Plug-ins_. Quando solicitado, reinicie o editor.

![Habilitar o plug-in do Hub MRTK](images/hub-enable-plugin.png)

Depois que o plug-in estiver habilitado para o seu projeto, você poderá acessar o Hub no botão de barra de ferramentas.

![Abra a janela do Hub MRTK](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>Instalando plug-ins de realidade misturada

Para instalar um plug-in usando o Hub, selecione o plug-in que você deseja adicionar ao seu projeto e, em seguida, pressione o botão _Instalar_. Para baixar o plug-in, verifique se não há conflitos na caixa _Problemas_ e pressione _Confirmar_. Depois que o plug-in for baixado, você será solicitado a reiniciar o editor. Infelizmente, não é possível reiniciar automaticamente o editor para você. Às vezes, a nova instância do editor será iniciada antes da conclusão da instalação.

![Instalar um plug-in usando o Hub MRTK](images/hub-download.png)

Depois de fechar o editor, você verá um prompt de comando exibido com uma barra de progresso para o desempacotamento do plug-in baixado. Um prompt de comando será exibido para cada plug-in instalado. Quando o desempacotamento for concluído, você poderá reabrir o editor e continuar no [percurso de desenvolvimento da realidade misturada](unreal-quickstart.md).

![MRTK Hub desempacotando um plug-in via prompt de comando](images/hub-unpack.png)

> [!IMPORTANT]
> Depois que o plug-in for instalado, o check-in dele deverá ser realizado no controle do código-fonte como com qualquer outro plug-in em nível de projeto.

#### <a name="updating-mixed-reality-plugins"></a>Atualizando plug-ins de realidade misturada

Para atualizar um plug-in usando o Hub, selecione o plug-in a ser atualizado da lista e, em seguida, pressione o botão _Instalar_. Para baixar o plug-in atualizado, verifique se não há conflitos na caixa _Problemas_ e pressione _Confirmar_. Você será solicitado a reiniciar o editor para concluir a atualização. As atualizações de plug-in são feitas durante a inicialização do editor, portanto, não é necessário aguardar a conclusão de nenhum desempacotamento antes de reabrir o editor.

![Como atualizar um plug-in por meio do Hub MRTK](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>Como remover plug-ins de realidade misturada

Para desinstalar um plug-in usando o Hub, selecione o plug-in que você deseja remover e, em seguida, selecione a versão instalada no menu suspenso. Para remover o plug-in, verifique se não há conflitos na caixa _Problemas_ e pressione _Confirmar_. Você será solicitado a reiniciar o editor para concluir a remoção.

![Como remover um plug-in por meio do Hub MRTK](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>Revisando alterações e detectando incompatibilidades

Você pode exibir as alterações exatas que serão feitas em seu projeto na seção inferior da janela do Hub. Ali, você pode ver os plug-ins que serão adicionados ou removidos do seu projeto, juntamente com possíveis incompatibilidades que possam vir a causar problemas quando as alterações forem feitas.

> [!NOTE]
> A lista de _Problemas_ causará incompatibilidades nas versões de dependência do plug-in e na versão do Unreal Engine, mas não corrigirá automaticamente nem sugerirá correções para problemas.

![Tentando instalar um plug-in incompatível](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagem de logotipo do Unreal](../images/MRTK-Unreal-Banner.png)<br>**Kit de Ferramentas de Realidade Misturada – Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se você não quiser usar o MRTK para o Unreal, precisará criar o script de todas as interações e todos os comportamentos por conta própria.