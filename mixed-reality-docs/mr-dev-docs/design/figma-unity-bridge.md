---
title: Ponte figma do MRTK para Unity
description: A Ponte figma do MRTK para Unity permite que você traga o layout do Figma Toolkit para o Unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, Sketch, Adobe XD, design, designer, arquivo de design, design de UX, HoloLens, MRTK, Realidade Misturada Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053765"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>Ponte figma do MRTK para Unity (Beta)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

A Ponte figma do MRTK para Unity permite que você traga o layout do Figma Toolkit para o Unity. A ponte pode importar o layout da interface do usuário criado com o MRTK Figma Toolkit e, em seguida, cria uma instaência de pré-fabs do MRTK correspondentes com a posição e o tamanho apropriados. O Figma Bridge ajudará a projetar o processo de integração e a colaboração entre designers e desenvolvedores.


Confira a [página Toolkit figma do MRTK](figma-toolkit.md) para saber mais sobre o Figma Toolkit que é o arquivo de design com HoloLens de interface do usuário no estilo 2.

## <a name="prerequisites"></a>Pré-requisitos
- Confira [Instalar as ferramentas para](/windows/mixed-reality/develop/install-the-tools) o software necessário para o desenvolvimento de Realidade Misturada
- Unity 2019 ou superior
- [MRTK-Unity 2.7.0 ou superior](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Requer MRTK-Unity 2.7.0 ou superior**
> 
> Como o Figma Toolkit e o Figma Bridge são baseados em pré-fabs do MRTK 2.7.0, o MRTK 2.7.0 ou versão superior é necessário. Quando usado com a versão inferior do MRTK, alguns componentes não serão traduzidos corretamente.

## <a name="how-to-use-mrtk-figma-bridge"></a>Como usar a Ponte figma do MRTK

### <a name="1-installation"></a>1. Instalação

A Ponte do Figma Unity pode ser instalada por meio da [Ferramenta de Recursos de Realidade Misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Baixe e execute a Ferramenta de Recursos de Realidade Misturada.

Na **página Descobrir recursos,** na seção **Realidade Misturada Toolkit,** selecione **Ponte do MrTK Figma Unity**. Siga as etapas para concluir a Ferramenta de Recursos do MR e volte para seu projeto do Unity. O Unity importa o pacote para a Ponte Figma do MRTK.

### <a name="2-open-figma-bridge-window"></a>2. Abrir a janela ponte figma

Depois que o processo de importação for feito, você poderá encontrar o Figma Bridge no menu **Realidade Misturada > Toolkit > Figma Bridge**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Gerar e inserir seu Token Figma

No site do Figma, clique no menu Figma no canto superior esquerdo, abra Ajuda e conta > Configurações da conta. Gere um novo token de acesso pessoal na seção 'Tokens de acesso pessoal'.

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Insira a ID de um documento do Figma
Cada documento figma tem uma ID exclusiva na URL. Copie e copie essa ID na Ponte figma.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Clique **em Obter Arquivo** para baixar o arquivo Figma. Você pode baixar outros arquivos Figma inserindo uma nova ID.

Clique **em Carregar Arquivo** para abrir um arquivo Figma.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. Criar uma página

A Ponte figma exibirá a lista de páginas no arquivo Figma. Verifique as páginas que você deseja criar no Unity. Clique **no botão Criar páginas.**

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. Atualizar um documento para alterações

Você pode modificar o arquivo Figma na Web (ou usando o editor da área de trabalho) e clicar **em Atualizar** para recuperar as alterações. Clique **em Criar páginas** para criar com atualizações. Dessa forma, você pode iterar facilmente seu design no Figma e vê-lo no Unity.



## <a name="see-also"></a>Veja também
* [Kit de ferramentas do Figma](figma-toolkit.md)
* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)
