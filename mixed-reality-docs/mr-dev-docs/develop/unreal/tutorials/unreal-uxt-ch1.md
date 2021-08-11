---
title: 1. Introdução
description: Parte 1 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 26493f48418e36c2441eada17a764dc18d73e90bf34e0c35b4412e7a38c9fe41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226670"
---
# <a name="1-getting-started"></a>1. Introdução

Se você está começando a usar a realidade misturada agora ou já é um profissional experiente, você está no lugar certo para iniciar seu percurso do [HoloLens 2](../../../index.yml) e do [Unreal Engine](https://www.unrealengine.com/en-US/). Esta série de tutoriais fornecerá um guia passo a passo sobre como criar um aplicativo de xadrez interativo com o [plug-in de Ferramentas de Experiência de Usuário](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte do [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). O plug-in ajudará você a adicionar recursos comuns de UX a seus projetos pelo uso de código, blueprints e exemplos. 

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

Ao final da série, você terá experiência em:
* Criar um projeto
* Configurar a realidade misturada
* Trabalhar com a entrada do usuário
* Adicionar botões
* Jogar em um emulador ou dispositivo

## <a name="prerequisites"></a>Pré-requisitos

Verifique se você instalou o seguinte antes de começar:
* Windows 10 1809 ou posterior
* SDK do Windows 10 10.0.18362.0 ou posterior
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 ou posterior
* Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou [Emulador](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* Visual Studio 2019 com as cargas de trabalho abaixo

### <a name="installing-visual-studio-2019"></a>Instalação do Visual Studio 2019

Primeiro, verifique a configuração com todos os pacotes do Visual Studio necessários:
1. Instale a versão mais recente do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
1. Instale as seguintes [cargas de trabalho](/visualstudio/install/modify-visual-studio#modify-workloads):
    * Desenvolvimento para desktop com C++
    * Desenvolvimento para área de trabalho com .NET
    * Desenvolvimento para a Plataforma Universal do Windows
1. Expanda o desenvolvimento da Plataforma Universal do Windows e selecione: 
    * Conectividade de dispositivos USB
    * Ferramentas da Plataforma Universal do Windows do C++ (v142)

1. Instale os seguintes [componentes](/visualstudio/install/modify-visual-studio#modify-individual-components):
    * Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)

Confirme a instalação com a imagem a seguir

![Tiques importantes no instalador do VS](images/unreal-uxt/1-install-the-tools.png)

Pronto! Você está pronto para prosseguir para a inicialização do projeto de xadrez.

[Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo](unreal-uxt-ch2.md)