---
title: Como exportar e criar uma solução do Visual Studio do Unity
description: Este artigo descreve como exportar seu projeto de realidade misturada do Unity para que você possa criar e implantar no Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, exportar, criar, implantar, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, UWP, implantação
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203598"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Como exportar e criar uma solução do Visual Studio do Unity

Se seu aplicativo não precisar do teclado do sistema, nossa recomendação será usar *D3D* para que seu aplicativo use um pouco menos de memória e um tempo de lançamento mais rápido. No entanto, se você estiver usando o teclado do sistema por meio da API TouchScreenKeyboard, precisará exportar o projeto como *XAML.*

## <a name="how-to-export-from-unity"></a>Como exportar do Unity

![Configurações de build do Unity](images/unitybuildsettings-300px.png)<br>
*Configurações de build no editor do Unity*

1. Quando estiver pronto para exportar seu projeto do Unity, abra o **menu** Arquivo e selecione **Criar Configurações...**
2. Selecione **Adicionar Cenas Abertas** para adicionar sua cena ao build.
3. Na caixa **de Configurações** build, escolha as seguintes opções para exportar para HoloLens:
   * **Plataforma:** *Plataforma universal Windows e* certifique-se de selecionar **Alternar Plataforma** para que sua seleção entre em vigor.
   * **SDK:** *Universal 10.*
   * **Tipo de build UWP:** *D3D.*
4. **Opcional:** **Projetos C# do Unity:** verificados.

>[!NOTE]
>A verificação dessa caixa permite que você:
>* Depure seu aplicativo no Visual Studio depurador remoto.
>* Edite scripts no projeto C# do Unity ao usar o IntelliSense para APIs do WinRT.

5. Na janela **Criar Configurações...** , abra **Player Configurações...**
6. Selecione o **Configurações para a guia Plataforma Windows** Universal.
7. Expanda o grupo **Configurações de XR**.
8. Na seção **XR Configurações,** marque a caixa de seleção Realidade **Virtual** Com Suporte para adicionar uma nova lista de Dispositivos de Realidade **Virtual** e confirme se **"Windows Mixed Reality"** está listado como um dispositivo com suporte.
9. Retorne à caixa **de diálogo Configurações** build.
10. Selecione **Compilar**.
11. Na caixa de Windows Explorer exibida, crie uma nova pasta para manter a saída de build do Unity. Em geral, nomeiamos a pasta "Aplicativo".
12. Selecione a pasta recém-criada e **selecione Selecionar Pasta**.
13. Depois que o Unity terminar de criar, uma Windows Explorer será aberta no diretório raiz do projeto. Navegue até a pasta recém-criada.
14. Abra o arquivo de Visual Studio gerado localizado dentro dessa pasta.

## <a name="when-to-re-export-from-unity"></a>Quando exportar do Unity

A verificação da caixa de seleção Projetos em **C#** ao exportar seu aplicativo do Unity cria uma solução Visual Studio que inclui todos os arquivos de script do Unity. Ter todos os scripts em um só lugar permite iterar sem exportar de novo do Unity. No entanto, se você fizer alterações no projeto que não estão apenas alterando o conteúdo dos scripts, será necessário exportar de novo do Unity. Alguns exemplos de vezes que você precisa exportar de volta do Unity são:
* Adicione ou remova ativos na guia Project dados.
* Você altera qualquer valor na guia Inspetor.
* Você adiciona ou remove objetos da guia Hierarquia.
* Você altera as configurações de projeto do Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Criando e implantando uma solução de Visual Studio Unity

O restante da criação e implantação de aplicativos ocorre no [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Você precisará especificar uma configuração de build do Unity. As convenções de nomenba do Unity podem ser diferentes do que você está acostumado em Visual Studio:

|  Configuração  |  Explicação | 
|----------|----------|
|  Depurar  |  Todas as otimizações são desligadas e o profiler está habilitado. Usado para depurar scripts. | 
|  Principal  |  Todas as otimizações são activadas e o profiler está desabilitado. Usado para enviar aplicativos para a Store. | 
|  Versão  |  Todas as otimizações são ativadas e o profiler está habilitado. Usado para avaliar o desempenho do aplicativo. | 

Observe que a lista acima é um subconjunto dos gatilhos comuns que fará com que o Visual Studio projeto precise ser gerado. Em geral, editar arquivos .cs de dentro Visual Studio não exigirá que o projeto seja regenerado de dentro do Unity.

## <a name="troubleshooting"></a>Solução de problemas

Se você achar que as edições para seus arquivos .cs não estão sendo reconhecidas em seu projeto Visual Studio, verifique se os Projetos **C#** do Unity estão marcados quando você gera o projeto VS no menu Build do Unity.
