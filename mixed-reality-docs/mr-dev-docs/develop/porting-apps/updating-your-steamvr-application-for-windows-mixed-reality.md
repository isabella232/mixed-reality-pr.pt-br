---
title: Como atualizar aplicativos SteamVR para o Windows Mixed Reality
description: práticas recomendadas para atualizar seu aplicativo SteamVR para maximizar a compatibilidade com o Windows Mixed Reality headsets.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilidade, portabilidade, HoloLens 1ª gen, headset de realidade misturada, headset do windows mixed realm fone de ouvido, migração, Windows 10, fluxo, controladores de movimento, haptics
ms.openlocfilehash: ee72994691970a3701ec8462ab0f42b6d1da1820589ca68a92c9a78fe1c18a41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196186"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Como atualizar aplicativos SteamVR para o Windows Mixed Reality

incentivamos os desenvolvedores a testar e otimizar suas experiências de SteamVR para execução em Windows Mixed Reality headsets. Esta documentação aborda os aprimoramentos comuns que você pode fazer para que suas experiências sejam executadas com muita Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instruções de instalação inicial

para começar a testar seu jogo ou aplicativo em Windows Mixed Reality certifique-se de primeiro seguir nosso [guia de introdução.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>Modelos de controlador

1. Se seu aplicativo renderizar modelos de controlador:
    * usar os [modelos do controlador de movimento de Windows Mixed Reality](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Use IVRRenderModel:: getcomponentstate para obter transformações locais em partes de componente (por exemplo, pose de ponteiro)
2. Experiências que têm uma noção de destromente devem obter dicas das APIs de entrada para diferenciar controladores [(exemplo de Unity)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controles

Ao criar ou ajustar seu layout de controle, tenha em mente o seguinte conjunto de comandos reservados:
1. Ao clicar na **esquerda e à direita, a Thumbstick analógica** é reservada para o **painel de fluxo**.

> [!NOTE]
> Se você estiver usando um controlador de reverbo G2 HP, clicar no botão de menu à direita será reservado para o **painel de fluxo**.

2. o **botão de Windows** sempre retornará os usuários para a página inicial do Windows Mixed Reality.

se possível, o padrão é a teleportação baseada em thumbstick para corresponder ao comportamento de teleportabilidade [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home)

## <a name="tooltips-and-ui"></a>Dicas de ferramenta e interface do usuário

Muitos jogos de VR aproveitam as dicas de ferramentas e sobreposições do controlador de movimento para ensinar aos usuários seus aplicativos ou jogos os comandos mais importantes. ao ajustar seu aplicativo para Windows realidade misturada, é recomendável revisar essa parte da sua experiência para garantir que as dicas de ferramenta sejam mapeadas para os modelos do controlador Windows.

além disso, se houver pontos em sua experiência em que você exiba imagens dos controladores, certifique-se de fornecer imagens atualizadas usando os controladores de movimento de Windows Mixed Reality.

## <a name="haptics"></a>Haptics

a partir do [Windows 10 atualização de abril de 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics agora têm suporte para experiências de SteamVR em Windows Mixed Reality. se seu aplicativo ou jogo SteamVR já inclui suporte para haptics, ele agora deve funcionar (sem nenhum trabalho adicional) com [Windows Mixed Reality os controladores de movimento](../../design/motion-controllers.md).

Windows Mixed Reality os controladores de movimento usam um motor haptics padrão, ao contrário dos acionadores lineares encontrados em alguns outros controladores de movimento do SteamVR. Isso pode levar a uma experiência de usuário um pouco diferente do esperado. portanto, é recomendável testar e ajustar seu design de haptics com Windows Mixed Reality controladores de movimento. por exemplo, às vezes, os pulsos de haptic curtos (5-10 ms) são menos perceptíveis em Windows Mixed Reality controladores de movimento. Para produzir um pulso mais perceptível, experimente enviar um "clique" mais longo (40-70 ms) para dar ao motor mais tempo para ser girado antes de ser informado para desligar novamente.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>iniciando aplicativos SteamVR de Windows Mixed Reality menu Iniciar

para experiências de VR distribuídas por meio do vapor, atualizamos [Windows Mixed Reality para SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) juntamente com as versões mais recentes do [Windows](https://insider.windows.com). os títulos de SteamVR agora aparecem no Windows Mixed Reality menu Iniciar na lista "todos os aplicativos" automaticamente.

## <a name="windows-mixed-reality-logo"></a>logotipo de Windows Mixed Reality

para exibir Windows Mixed Reality suporte para seu título, vá para o link "editar página de repositório" na página de aterrissagem do aplicativo, selecione a guia "informações básicas" e role para baixo até "realidade Virtual". desmarque a "ocultar Windows Mixed Reality" e, em seguida, publique na loja.

## <a name="bugs-and-feedback"></a>Bugs e comentários

seus comentários são inúteis quando se trata de melhorar a experiência de Windows Mixed Reality SteamVR. envie todos os comentários e bugs por meio do [Hub do Windows Feedback](/windows/mixed-reality/enthusiast-guide/filing-feedback). Aqui estão algumas [dicas sobre como tornar seus comentários do SteamVR tão úteis quanto possível](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Se você tiver dúvidas ou comentários para compartilhar, também poderá entrar em contato conosco em nosso [Fórum de fluxo](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Perguntas frequentes e solução de problemas

Se você estiver executando problemas gerais Configurando ou jogando sua experiência, [Confira as etapas de solução de problemas mais recentes](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Veja também

* [Instalar as ferramentas](../install-the-tools.md)
* [Histórico do driver do controlador do headset e do Motion](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [diretrizes mínimas de compatibilidade de hardware do PC Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)