---
title: Windows Mixed Reality e o novo Microsoft Edge
description: saiba mais sobre os novos Microsoft Edge para realidade misturada, incluindo o que esperar, atualizações a serem verificadas e problemas conhecidos.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: Edge, novo, imersão Web, Microsoft Edge, navegador, VR, 360, 360 vídeo, 360 Viewer, webxr, webvr
ms.openlocfilehash: 51efc5c4d3afb4d46ba7722867514f740a9f60a4280652fdbd665134f83af23d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218818"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>o novo Microsoft Edge para Windows Mixed Reality

o [novo Microsoft Edge agora está disponível para download](https://blogs.windows.com/windowsexperience/?p=173496), mas os clientes também podem [aguardar uma atualização futura para instalá-lo com Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), seguindo uma abordagem medida de distribuição nos próximos meses. 

com essa notícia, **queríamos permitir que Windows Mixed Reality os clientes de fone de ouvido em VR saibam o que esperar do novo Microsoft Edge e mostraram atualizações pendentes para uma experiência de navegação aprimorada no Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Apresentando o novo Microsoft Edge

o novo Microsoft Edge [adota o Chromium projeto](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) de software livre na área de trabalho para criar uma melhor compatibilidade para os clientes e menos fragmentação da web para desenvolvedores da web. Ele também dará suporte a WebXR na inicialização, o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

>[!IMPORTANT]
>quando você instala Microsoft Edge em um dispositivo Windows 10 atualizado, ele substituirá a versão anterior (herdada) em seu computador.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Preparando-se para o novo Microsoft Edge

Windows Mixed Reality os clientes de headset de VR que desejam usar a nova Microsoft Edge na realidade misturada devem **atualizar para Windows 10 versão 1903 ou posterior para o suporte nativo de aplicativos Win32 (como o novo Microsoft Edge)** na casa da realidade misturada. verifique Windows Update ou [instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

para obter a melhor experiência de Microsoft Edge possível na casa de realidade misturada, também recomendamos aguardar **algumas otimizações de Windows Mixed Reality de chave para o novo Microsoft Edge chegando com a atualização cumulativa 2020-01 para Windows 10 versão 1903 (ou posterior)**, que deve estar disponível em Windows Update no final de janeiro.

>[!IMPORTANT]
>se você optar por baixar o novo Microsoft Edge antes de realizar essas atualizações, haverá alguns problemas conhecidos com seu comportamento no Windows Mixed Reality (que pode ser lido abaixo).

## <a name="known-issues"></a>Problemas conhecidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para Windows 10 versão 1903 (ou posterior)

- iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a tela do headset congele brevemente.
- o bloco Microsoft Edge desaparece da menu Iniciar de Windows Mixed Reality (você pode encontrá-lo na pasta "aplicativos clássicos").
- os Windows dos Microsoft Edge anteriores ainda são colocados em todo o início da realidade misturada, mas não podem ser usados. A tentativa de ativar essas janelas inicia a borda no aplicativo da área de trabalho.
- A seleção de um hiperlink na página inicial da realidade misturada inicia um navegador da Web na área de trabalho em vez da casa mistura de realidade.
- O aplicativo de demonstração do WebVR está presente na casa da realidade misturada, apesar de WebVR não ter mais suporte.
- Aprimoramentos gerais na inicialização e visuais do teclado.

### <a name="monitor-and-input-handling-issues"></a>Problemas de monitor e de tratamento de entrada

depois de fazer a atualização cumulativa 2020-01 para Windows 10 versão 1903 (ou posterior), os monitores virtuais serão exibidos como monitores físicos genéricos em **Configurações > sistema > exibição** durante as sessões de Windows Mixed Reality. Alguns clientes, especialmente com mais de um monitor físico, podem notar problemas com o layout de área de trabalho e o tratamento de entrada como resultado.

**Por que isso acontece**

o suporte para aplicativos Win32 clássicos no Windows Mixed Reality foi introduzido com o [Atualização de maio de 2019 para o Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Para habilitar esse suporte, um monitor virtual deve ser criado para hospedar o aplicativo Win32. Cada vez que um novo aplicativo Win32 é iniciado, outro monitor virtual precisa ser criado. Infelizmente, a criação de um monitor virtual é uma tarefa intensiva que pode fazer com que a tela do headset congele brevemente. Os clientes ofereciam comentários de que essa era uma experiência desconfortável e perturbadora. Devido a comentários e maior uso do aplicativo Win32, tomamos a decisão de alocar previamente três monitores virtuais durante a inicialização de Windows Mixed Reality. Isso impede a interrupção e permite que os clientes iniciem até três aplicativos Win32 simultâneos sem experimentar o congelamento de vídeo do headset.

**Solução alternativa**

Já que recebemos comentários de que alguns clientes, especialmente aqueles com vários monitores físicos, preferem desabilitar essa pré-alocação do monitor virtual. para dar aos clientes controle, habilitamos uma solução alternativa que envolve a alteração de um valor de chave do registro, que está disponível com as seguintes atualizações de Windows:

- 2020-07 versão prévia da atualização cumulativa para Windows 10 Version 2004 (KB4568831)
- 2020-10 versão prévia da atualização cumulativa para Windows 10 Version 1909 (KB4580386)
- 2020-10 versão prévia da atualização cumulativa para Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>A modificação de valores de chave do registro destina-se a usuários avançados.

>[!WARNING]
>desabilitar a pré-alocação do virtual monitor pode resultar na exibição resumida do fone de ouvido ao iniciar um aplicativo Win32 (como o fluxo, o novo Microsoft Edge ou o Google Chrome) no Windows Mixed Reality.

Para desabilitar a pré-alocação do monitor virtual:
1. verifique **Windows Update** uma das versões da versão prévia da atualização cumulativa Windows 10 listada acima e instale a atualização quando disponível. você pode encontrar a atualização em **atualizações opcionais** ou **opções avançadas** na página configurações de Windows Update
2. Iniciar **Editor do registro**
3. Navegue até "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se a REG_DWORD "PreallocateVirtualMonitors" não estiver presente, crie-a selecionando **editar > novo > valor DWORD (32 bits)** e inserindo PreallocateVirtualMonitors como o nome
5. Se a REG_DWORD "PreallocateVirtualMonitors" estiver presente (ou você acabou de criá-la), clique duas vezes na entrada e altere "dados do valor" de 1 (seu valor padrão) para 0 (zero)
    * TRUE-1
    * FALSE-0

os monitores virtuais agora serão alocados quando você tentar iniciar um aplicativo Win32 em Windows Mixed Reality em vez de pré-instalar. Para redefinir essa configuração e reabilitar a pré-alocação do monitor virtual, retorne o DWORD "value data" para 1.

### <a name="other-known-issues"></a>Outros problemas conhecidos

-   os sites abertos no Windows Mixed Reality serão perdidos quando o Portal da realidade misturada for fechado. o Microsoft Edge windows permanecerá em suas posições posicionadas na casa mistura de realidade.
- As experiências de WebXR, incluindo a extensão do visualizador 360, podem não ser iniciadas corretamente em PCs com uma configuração de GPU híbrida. Você pode contornar esse problema habilitando um recurso de visualização no novo Microsoft Edge. Navegue até `edge://flags` , pesquise "várias GPU" e habilite o sinalizador chamado **WEBXR multi GPU support**.
-   o áudio do Microsoft Edge windows não está espacial.
-   **corrigido na extensão do visualizador 360 versão 2.3.8**: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Reiniciar a borda deve atualizar invisivelmente a extensão do visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem digitando `edge://system/` na barra de endereços e selecionando o botão **expandir** ao lado de "extensões".