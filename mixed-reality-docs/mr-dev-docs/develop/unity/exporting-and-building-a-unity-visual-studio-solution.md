---
title: Como exportar e criar uma solução do Visual Studio do Unity
description: Este artigo descreve como exportar seu projeto de realidade misturada do Unity para que você possa compilar e implantar no Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, exportar, compilar, implantar, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, UWP, implantação
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010407"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Como exportar e criar uma solução do Visual Studio do Unity

Se seu aplicativo não precisar do teclado do sistema, nossa recomendação é usar o *D3D* para que seu aplicativo use um pouco menos de memória e um tempo de inicialização mais rápido. No entanto, se você estiver usando o teclado do sistema por meio da API do TouchScreenKeyboard, você precisará exportar o projeto como *XAML*.

## <a name="how-to-export-from-unity"></a>Como exportar do Unity

![Configurações de Build do Unity](images/unitybuildsettings-300px.png)<br>
*Configurações de compilação no editor do Unity*

1. Quando você estiver pronto para exportar seu projeto do Unity, abra o menu **arquivo** e selecione **configurações de compilação...**
2. Selecione **Adicionar abrir cenas** para adicionar sua cena à compilação.
3. Na caixa de diálogo **configurações de compilação** , escolha as seguintes opções para exportar para o HoloLens:
   * **Plataforma:** *plataforma universal do Windows* e certifique-se de selecionar **alternar plataforma** para sua seleção entrar em vigor.
   * **SDK:** *Universal 10*.
   * **Tipo de compilação UWP:** *D3D*.
4. **Opcional**: **projetos do Unity C#:** marcado.

>[!NOTE]
>Marcar essa caixa permite que você:
>* Depure seu aplicativo no depurador remoto do Visual Studio.
>* Edite scripts no projeto do Unity C# ao usar o IntelliSense para APIs do WinRT.

5. Na janela **configurações de compilação...** , abra **as configurações do Player...**
6. Selecione as **configurações para plataforma universal do Windows** guia.
7. Expanda o grupo **Configurações de XR**.
8. Na seção **configurações de XR** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **dispositivos de realidade virtual** e confirme se **"realidade mista do Windows"** está listado como um dispositivo com suporte.
9. Retorne para a caixa de diálogo **configurações de compilação** .
10. Selecione **Compilar**.
11. Na caixa de diálogo do Windows Explorer que aparece, crie uma nova pasta para manter a saída de Build do Unity. Em geral, nomeamos a pasta "app".
12. Selecione a pasta recém-criada e selecione **Selecionar pasta**.
13. Depois de concluir a compilação do Unity, uma janela do Windows Explorer será aberta para o diretório raiz do projeto. Navegue até a pasta recém-criada.
14. Abra o arquivo de solução do Visual Studio gerado localizado dentro dessa pasta.

## <a name="when-to-re-export-from-unity"></a>Quando exportar novamente do Unity

Marcar a caixa de seleção **projetos C#** ao exportar seu aplicativo do Unity cria uma solução do Visual Studio que inclui todos os arquivos de script do Unity. Ter todos os seus scripts em um único lugar permite que você itere sem exportar novamente do Unity. No entanto, se você fizer alterações em seu projeto que não estejam apenas alterando o conteúdo dos scripts, você precisará exportar novamente do Unity. Alguns exemplos de vezes que você precisa exportar novamente do Unity são:
* Você adiciona ou remove ativos na guia projeto.
* Você altera qualquer valor na guia inspetor.
* Você adiciona ou remove objetos da guia hierarquia.
* Você altera as configurações de projeto de Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Criando e implantando uma solução do Unity Visual Studio

O restante da criação e implantação de aplicativos acontece no [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Será necessário especificar uma configuração de compilação do Unity. As convenções de nomenclatura do Unity podem diferir do que você está acostumado no Visual Studio:

|  Configuração  |  Explicação | 
|----------|----------|
|  Depurar  |  Todas as otimizações desativadas e o criador de perfil está habilitado. Usado para depurar scripts. | 
|  Principal  |  Todas as otimizações são ativadas e o criador de perfil está desabilitado. Usado para enviar aplicativos para a loja. | 
|  Versão  |  Todas as otimizações são ativadas e o criador de perfil está habilitado. Usado para avaliar o desempenho do aplicativo. | 

Observe que a lista acima é um subconjunto dos gatilhos comuns que farão com que o projeto do Visual Studio precise ser gerado. Em geral, a edição de arquivos. cs de dentro do Visual Studio não exigirá que o projeto seja regenerado de dentro do Unity.

## <a name="troubleshooting"></a>Solução de problemas

Se você achar que as edições em seus arquivos. cs não estão sendo reconhecidas em seu projeto do Visual Studio, verifique se os **projetos do Unity C#** são verificados quando você gera o projeto do vs no menu de compilação do Unity.
