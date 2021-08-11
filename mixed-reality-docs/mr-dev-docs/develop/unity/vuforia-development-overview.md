---
title: Como usar o Vuforia com o Unity
description: Use o Vuforia para criar Windows Mixed Reality aplicativos no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, quadro de referência, acompanhamento, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity, HoloLens, acompanhamento de dispositivo, modo de desempenho, Vuforia Portal do Desenvolvedor
ms.openlocfilehash: dd5153b5e4986ebf1ecc2c133f3d431de08ce5b923cc7d2327d9cbda4f4df61c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216412"
---
# <a name="using-vuforia-engine-with-unity"></a>Usando o Mecanismo vuforia com o Unity

O Mecanismo Vuforia traz uma funcionalidade importante para HoloLens – o poder de conectar experiências de RA a imagens e objetos específicos no ambiente. Você pode usar essa funcionalidade para sobrepor instruções passo a passo guiadas sobre o computador para a empresa industrial ou adicionar recursos digitais e experiências a um produto físico ou jogo.

O Mecanismo Vuforia oferece uma ampla variedade de recursos e destinos para tornar seu processo de desenvolvimento de RA mais flexível. Um dos nossos recursos mais novos, o Vuforia Model Targets, é uma funcionalidade fundamental para usos comerciais e industriais. Os Destinos de Modelo permitem que os aplicativos reconheçam objetos físicos como máquinas, automóveis ou brinquedos e os rastreiam com base em um modelo CAD ou digital 3D. Para usos industriais, esse recurso pode fornecer aos funcionários de assembly e técnicos de serviço instruções de trabalho de RA e diretrizes de procedimento enquanto estão na fábrica ou fora do campo.

Os aplicativos do Mecanismo vuforia existentes que foram construídos para telefones e tablets podem ser facilmente configurados no Unity para serem executados HoloLens. Você pode até mesmo usar o Mecanismo vuforia para levar seu novo aplicativo HoloLens para tablets Windows 10 como o Surface Pro e Surface Book.


## <a name="get-the-tools"></a>Obter as ferramentas

[Instale as versões recomendadas](../install-the-tools.md) do Visual Studio Unity e, em seguida, configure o Unity para usar Visual Studio e o IDE e compilador preferenciais. 

Ao instalar o Unity, certifique-se de instalar o back-Windows de script IL2CPP do Windows Store".

Adicione o pacote mecanismo Vuforia conforme descrito [aqui.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html).

## <a name="getting-started-with-vuforia-engine"></a>Como começar a trabalhar com o Mecanismo vuforia

O melhor ponto de partida para aprender sobre o Mecanismo vuforia e HoloLens é o exemplo de HoloLens [Mecanismo vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponível no Unity Asset Store). O exemplo fornece um projeto HoloLens completo, incluindo cenas pré-configuradas que podem ser implantadas em um HoloLens.

As cenas mostram como usar Destinos de Imagem vuforia para reconhecer uma imagem e au incrementá-la com conteúdo digital em uma HoloLens experiência. O exemplo de HoloLens Mecanismo vuforia também inclui uma cena mostrando o uso de Destinos de Modelo e VuMarks no HoloLens. Você pode facilmente substituir seu próprio conteúdo nas cenas para experimentar a criação de aplicativos HoloLens que usam o Mecanismo Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurando um aplicativo Vuforia para HoloLens

Desenvolver um aplicativo mecanismo Vuforia para HoloLens é fundamentalmente o mesmo que desenvolver aplicativos do Mecanismo Vuforia para outros dispositivos. Em seguida, você pode aplicar as configurações e as configurações de build descritas na seção abaixo. Isso é tudo o que é necessário para permitir que o Mecanismo vuforia funcione com o HoloLens de mapeamento espacial e sistemas de acompanhamento posicionais.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Criar e executar o exemplo de mecanismo Vuforia para HoloLens
1.  Baixe o [exemplo de mecanismo Vuforia para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) do Asset Store do Unity
2.  Aplicar as [opções recomendadas do mecanismo do Unity para energia e desempenho](performance-recommendations-for-unity.md)
3.  Adicione as cenas de exemplo a **Cenas** no **Build.**
4.  Em **Build Configurações**, mude a plataforma de build para **uWP** clicando no botão Adicionar Cenas **Abertas.**
![imagem](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Selecione o **botão Configurações** Player.  
   * Selecione o **ícone UWP** e expanda a **seção Configurações XR.**
   * Verifique se **a Realidade Virtual Com Suporte** está habilitada.    
   * Em **SDKs de Realidade Virtual,** verifique se:
     * **O Window Mixed Reality** está incluído na lista e habilitar **o compartilhamento de buffer** de profundidade está habilitado. 
     * O **Formato de Profundidade** é definido como profundidade de **16 bits.** 
   * Verifique se o Modo **de Renderização** Estéreo está definido **como Instância de Passagem Única.**
6.  Expanda **a seção Configurações** publicação.
   * Em **Funcionalidades,** verifique se **Cliente da Internet, WebCam, Microfone** e **SpatialPerception** estão selecionados.
   * **OBSERVAÇÃO: SpatialPerception** só deverá ser selecionado se você pretende usar a API do Surface Observer.
   * Em **Famílias de Dispositivos Com** Suporte , verifique se **Holographic** está selecionado. 
7.  Expanda a **seção Resolução e** Apresentação.
   * Desabilite **Executar em Segundo** Plano para que o Mecanismo Vuforia pause quando o aplicativo for colocado em segundo plano e possa acessar a câmera novamente quando o aplicativo for retomado. 
   * No menu **suspenso Orientação** Padrão, verifique se **Paisagem Esquerda** está selecionada.
8.  Retorne à janela **Criar Configurações** e selecione **Criar** para gerar um Visual Studio projeto.
9.  Crie o executável do Visual Studio e instale-o em seu HoloLens.

## <a name="the-vuforia-developer-portal"></a>O vuforia Portal do Desenvolvedor

Os desenvolvedores que buscam criar suas próprias experiências de RA com o Mecanismo vuforia e HoloLens devem se inscrever em nosso vuforia Portal do Desenvolvedor no [developer.vuforia.com](https://developer.vuforia.com/). No portal, os desenvolvedores têm acesso aos Fóruns do [Mecanismo vuforia](https://developer.vuforia.com/forum) em que podem participar de discussões da comunidade, uma biblioteca com documentação detalhada sobre todos os Recursos do Mecanismo vuforia e o Gerenciador de Destino [](https://library.vuforia.com/) [Vuforia](https://developer.vuforia.com/target-manager) em que os usuários podem criar seus próprios Destinos personalizados. Os desenvolvedores também podem se inscrever para uma Licença de Desenvolvedor gratuita usando [o Gerenciador de Licenças vuforia.](https://developer.vuforia.com/license-manager)

## <a name="device-tracking-with-vuforia"></a>Acompanhamento de dispositivo com Vuforia

[O Acompanhamento de](https://library.vuforia.com/features/environments/device-tracker-overview.html) Dispositivos mantém o acompanhamento mesmo quando um destino não está mais em exibição. Ele é habilitado automaticamente para todos os destinos quando o Rastreador de Dispositivo Posicional está habilitado. Para HoloLens aplicativos, o Rastreador de Dispositivo Posicional é iniciado automaticamente no Unity.

O Mecanismo Vuforia combina automaticamente as poses do acompanhamento da câmera e o acompanhamento espacial do HoloLens para fornecer poses de destino estáveis, independentemente de o destino ser visto pela câmera ou não.

Como o processo é tratado automaticamente, ele não exige nenhuma programação pelo desenvolvedor.


**Veja a seguir uma descrição de alto nível do processo:**
1. O rastreador de destino do Vuforia reconhece o destino
2. O acompanhamento de destino é inicializado
3. A posição e a rotação do destino são analisadas para fornecer uma estimativa de pose robusta para a HoloLens
4. O Mecanismo Vuforia transforma a pose do destino no espaço de coordenadas HoloLens mapeamento espacial
5. HoloLens assumirá o controle se o destino não estiver mais em exibição. Sempre que você olhar novamente para o destino, Vuforia continuará acompanhando as imagens e objetos com precisão.

Destinos detectados, mas que não estão mais em exibição, são relatados como EXTENDED_TRACKED. Nesses casos, o script DefaultTrackableEventHandler usado em todos os destinos continua renderizar o conteúdo de aumento. O desenvolvedor pode controlar esse comportamento implementando um script de manipulador de eventos rastreável personalizado.

## <a name="performance-mode-with-vuforia-engine"></a>Modo de desempenho com o mecanismo Vuforia 

É possível por meio do Mecanismo Vuforia gerenciar o desempenho no HoloLens até a extensão de experiências de RA e reduzir a carga de trabalho na CPU. O Mecanismo Vuforia oferece três modos que podem ser selecionados: padrão, para otimizar a velocidade e para otimizar a qualidade. 

*   MODE_OPTIMIZE_SPEED permite minimizar a carga de trabalho no dispositivo HoloLens e é ótimo para estender as experiências de RA. É recomendável para situações em que o aplicativo está acompanhando objetos/destinos estáticos.
*   MODE_DEFAULT é o modo normal, que pode ser usado na maioria dos cenários.
*   MODE_OPTIMIZE_QUALITY é melhor para acompanhar destinos móveis ou destinos de modelo que você espera que sejam escolhidos.

**Definindo o modo**

Para alterar o modo de desempenho no Unity, navegue até Configuração de Vuforia (Ctrl+Shift+V/Cmd+Shift+V) que está localizado como um componente no ARCamera GameObject. 
*   Selecione o menu suspenso do Modo de Dispositivo da Câmera e selecione uma das três opções.


## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Mapeamento espacial](../../design/spatial-mapping.md)
* [Câmera no Unity](camera-in-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentação do Vuforia: Ponto de Partida com o Mecanismo vuforia para Windows 10 desenvolvimento](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Documentação do Vuforia: Ponto de Partida com o Mecanismo Vuforia no Unity](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Documentação do Vuforia: trabalhando com o exemplo HoloLens no Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Documentação do Vuforia: Acompanhamento de dispositivos no Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentação do Vuforia: Taxa de quadros e otimização de desempenho](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
