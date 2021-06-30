---
title: Práticas recomendadas do Unity e do Visual Studio
description: Dicas e truques para simplificar o fluxo de trabalho de criação de um aplicativo de realidade misturada com o Unity e o Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implantar, Unity, Visual Studio, HoloLens, HoloLens 2, headset de imersão, práticas recomendadas, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, UWP, Ferramentas do Visual Studio, SDK do Windows
ms.openlocfilehash: edd79b95d02cfeb1da4effc485fc57078e3d24a3
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042257"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Melhores práticas para trabalhar com o Unity e o Visual Studio

Ao criar um aplicativo de realidade misturada com o Unity, você precisa alternar entre o Unity e o Visual Studio para criar e implantar o pacote do aplicativo para o HoloLens ou um headset de imersão. Por padrão, duas instâncias do Visual Studio são necessárias – uma instância para modificar scripts de Unity e outra para implantar no dispositivo e depurar. As instruções a seguir permitem desenvolver usando uma única instância do Visual Studio, reduzindo a frequência de exportação de projetos de Unity e aprimorando a experiência de depuração.

## <a name="improving-iteration-time"></a>Melhorando o tempo de iteração

O suporte para o back-end de script do .NET no Unity foi preterido no Unity 2018 e removido a partir do Unity 2019 +, portanto, recomendamos que você alterne para [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). No entanto, você pode experimentar tempos de compilação mais longos do Unity para o Visual Studio. Para melhorar a iteração mais rápida, configure seu ambiente para obter melhores resultados de compilação:

1) Use a criação incremental criando seu projeto para o mesmo diretório a cada vez, reutilizando os arquivos pré-criados lá
2) Desabilitar verificações de software antimalware para seu projeto & criar pastas
   - Abra o **vírus & proteção contra ameaças** em seu aplicativo de configurações do Windows 10
   - Selecione **gerenciar configurações** em **vírus & ameaças proteção configurações**
   - Selecione **Adicionar ou remover exclusões** na seção **exclusões**
   - Selecione **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto de Unity e as saídas de compilação
3) Usar um SSD para compilação

Examine [otimizar os tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações. Além disso, examine [depuração em IL2CPP scripting back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Considere instalar a [extensão do Visual Studio *UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Essa ferramenta analisa seus scripts do Unity C# para o código que pode ser escrito de maneira mais otimizada.

## <a name="visual-studio-tools-for-unity"></a>Ferramentas do Visual Studio para Unity

Baixar [Ferramentas do Visual Studio para Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Benefícios do Ferramentas do Visual Studio para Unity**
* Depure o modo de reprodução do Unity no editor do Visual Studio colocando pontos de interrupção, avaliando variáveis e expressões complexas.
* Use o explorador de projeto do Unity para localizar o script com exatamente a mesma hierarquia que o Unity exibe.
* Obtenha o console do Unity diretamente dentro do Visual Studio.
* Use assistentes para criar ou navegar rapidamente para scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Expor variáveis de classe C# para facilitar o ajuste

Há duas maneiras de expor variáveis de classe. A maneira recomendada é adicionar o atributo [Serializefield] às suas variáveis privadas. Os campos serializados podem ser acessados no editor, mas não são expostos programaticamente.  A outra opção é tornar as variáveis de classe do C# públicas para expô-las na interface do usuário do editor. 

Ambas as abordagens possibilitam o ajuste fácil de variáveis durante a execução no editor, o que é especialmente útil para ajustar propriedades mecânicas de interação.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regenerar soluções do Visual Studio UWP após a atualização do SDK do Windows ou do Unity

As soluções UWP do Visual Studio com check-in no controle do código-fonte podem ficar desatualizadas após a atualização para um novo SDK do Windows ou mecanismo do Unity. Você pode resolver soluções desatualizadas depois de criar uma nova solução UWP do Unity e mesclar as diferenças na solução com check-in.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar ativos de formato de texto para uma comparação fácil de alterações de conteúdo

O armazenamento de ativos em formato de texto facilita a revisão de diferenciações de alteração de conteúdo no Visual Studio. Você pode armazenar ativos em formato de texto selecionando **editar > configurações do projeto > editor** e alterar o modo de **serialização do ativo** para **forçar o texto**. No entanto, mesclar alterações de arquivo de ativo de texto é propenso a erros e não é recomendado, portanto, considere habilitar check-outs binários exclusivos no controle do código-fonte.

## <a name="see-also"></a>Confira também
- [Ferramentas do Visual Studio para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Otimizando os tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Extensão do Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)