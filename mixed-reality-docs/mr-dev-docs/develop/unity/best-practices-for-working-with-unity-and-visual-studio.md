---
title: Unity e Visual Studio práticas recomendadas
description: Dicas e truques para simplificar o fluxo de trabalho de criação de um aplicativo de realidade misturada com o Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, headset imersivo, práticas recomendadas, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, UWP, Ferramentas do Visual Studio, SDK do Windows
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186876"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Melhores práticas para trabalhar com o Unity e o Visual Studio

Ao criar um aplicativo de realidade misturada com o Unity, você precisa alternar entre o Unity e o Visual Studio para criar e implantar o pacote de aplicativos em um HoloLens ou um headset imersivo. Por padrão, duas instâncias de Visual Studio são necessárias : uma instância para modificar scripts do Unity e outra para implantar no dispositivo e depurar. As instruções a seguir permitem que você desenvolva usando uma única instância Visual Studio, reduzindo a frequência de exportação de projetos do Unity e aprimora a experiência de depuração.

## <a name="improving-iteration-time"></a>Melhorando o tempo de iteração

O suporte para back-end de script do .NET no Unity foi preterido no Unity 2018 e removido a partir do Unity 2019+, portanto, é recomendável alternar para [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html) No entanto, você pode experimentar tempos de build mais longos do Unity para Visual Studio. Para melhorar a iteração mais rápida, configurar seu ambiente para melhores resultados de compilação:

1) Use a criação incremental criando seu projeto para o mesmo diretório toda vez, reutilando os arquivos pré-construídos lá
2) Desabilitar verificações de software anti malware para seu projeto & pastas de build
   - Abra **a proteção contra & contra ameaças de** vírus em seu aplicativo de Windows 10 configurações
   - Selecione **Gerenciar Configurações** em **Configurações de proteção contra ameaças & vírus**
   - Selecione **Adicionar ou remover exclusões** na seção **Exclusões**
   - Selecione **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto do Unity e as saídas de build
3) Usar um SSD para criação

Revise [Otimizando os tempos de build para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações. Além disso, revise [Depuração no back-end de script IL2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Considere instalar a [ *extensão de Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Essa ferramenta analisa seus scripts C# do Unity para código que pode ser escrito de maneira mais otimizada.

## <a name="visual-studio-tools-for-unity"></a>Ferramentas do Visual Studio para Unity

Baixar [Ferramentas do Visual Studio para Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Benefícios do Ferramentas do Visual Studio para Unity**
* Depure o modo de reprodução do Unity no editor Visual Studio colocando pontos de interrupção, avaliando variáveis e expressões complexas.
* Use o Unity Project Explorer para encontrar seu script com exatamente a mesma hierarquia exibida pelo Unity.
* Obter o console do Unity diretamente dentro Visual Studio.
* Use assistentes para criar ou navegar rapidamente para scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Expor variáveis de classe C# para facilitar o ajuste

Há duas maneiras de expor variáveis de classe. A maneira recomendada é adicionar o atributo [SerializeField] às suas variáveis privadas. Os campos serializados podem ser acessados do editor, mas não expostos programaticamente.  A outra opção é tornar as variáveis de classe C# públicas para expô-las na interface do usuário do editor. 

Ambas as abordagens possibilitam ajustar facilmente as variáveis durante a reprodução no editor, o que é especialmente útil para ajustar as propriedades da interação de interação.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regenerar soluções de Visual Studio UWP após Windows SDK ou atualização do Unity

As soluções Visual Studio UWP verificadas no controle do código-fonte podem ficar desagredas após a atualização para um novo SDK Windows ou mecanismo do Unity. Você pode resolver soluções des date-of-date depois criando uma nova solução UWP do Unity e mesclando diferenças na solução de check-in.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar ativos de formato de texto para facilitar a comparação de alterações de conteúdo

O armazenamento de ativos no formato de texto facilita a revisão das diferenças de alteração de conteúdo Visual Studio. Você pode armazenar ativos no formato de texto selecionando **Editar > Project Configurações > Editor** e altere o modo de **Serialização de** Ativos para Forçar **Texto.** No entanto, mesclar alterações de arquivo de ativos de texto é propensa a erros e não recomendada, portanto, considere habilenciar check-outs binários exclusivos em seu controle do código-fonte.

## <a name="see-also"></a>Consulte também
- [Ferramentas do Visual Studio para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Otimizando os tempos de build para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Extensão de Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)