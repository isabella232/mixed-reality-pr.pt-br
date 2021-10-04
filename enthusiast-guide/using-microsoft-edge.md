---
title: usando Microsoft Edge no Windows Mixed Reality
description: prepare-se para o novo Microsoft Edge no Windows Mixed Reality. Inclui alterações esperadas, atualizações a serem verificadas e problemas conhecidos.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, Home, navegar, contornar, aplicativos, jogos, Microsoft Edge, chromium, Edge, 360, 360 vídeo, 360 viewer
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436691"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality e o novo Microsoft Edge

a [nova Microsoft Edge](https://www.microsoft.com/edge) está disponível para download e começou a ser distribuída automaticamente aos clientes via Windows Update. 

o novo Microsoft Edge [adota o Chromium projeto](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) de software livre na área de trabalho. Isso cria uma melhor compatibilidade para os clientes e menos fragmentação para desenvolvedores da Web. Ele também dará suporte a WebXR na inicialização, que é o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

>[!IMPORTANT]
>quando você instala Microsoft Edge em um dispositivo Windows 10 ou Windows 11 atualizado, ele substituirá a versão anterior (herdada) em seu computador.

## <a name="installing-the-new-microsoft-edge"></a>Instalando o novo Microsoft Edge 

antes de instalar o novo Microsoft Edge, **atualize para Windows 10 versão 1903 ou posterior ou Windows 11 para suporte a aplicativos Win32 nativo como o novo Microsoft Edge** em Windows Mixed Reality. verifique Windows Update ou [instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/software-download/windows10) ou Windows 11.

quando tiver Windows 10 versão 1903 ou posterior ou Windows 11, você estará pronto para o novo Microsoft Edge! a nova Microsoft Edge está sendo distribuída via Windows Update, mas você pode instalar manualmente o novo Microsoft Edge do [site Microsoft Edge](https://www.microsoft.com/edge) se você quiser mais cedo.

>[!IMPORTANT]
>o novo Microsoft Edge é iniciado com suporte para WebXR, o novo padrão para a criação de experiências de imersão da web para headsets de VR. ao instalar o novo Microsoft Edge, você não poderá mais reproduzir experiências de WebVR no Microsoft Edge. 

## <a name="known-issues"></a>Problemas conhecidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para Windows 10 versão 1903 (ou posterior)

- iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a tela do headset congele brevemente.
- o bloco Microsoft Edge desaparece da menu Iniciar de Windows Mixed Reality (você pode encontrá-lo na pasta "aplicativos clássicos").
- os Windows dos Microsoft Edge anteriores ainda são colocados em todo o início da realidade misturada, mas não podem ser usados. A tentativa de ativar essas janelas inicia a borda no aplicativo da área de trabalho.
- A seleção de um hiperlink na página inicial da realidade misturada inicia um navegador da Web na área de trabalho em vez da casa mistura de realidade.
- O aplicativo de demonstração do WebVR está presente na casa da realidade misturada, apesar de WebVR não ter mais suporte.
- Aprimoramentos gerais na inicialização e visuais do teclado.

### <a name="monitor-and-input-handling-issues"></a>Problemas de monitor e de tratamento de entrada

depois de obter a atualização cumulativa 2020-01 para Windows 10 versão 1903 ou posterior, os monitores virtuais aparecerão como monitores físicos genéricos em **Configurações > sistema > exibição** durante as sessões de Windows Mixed Reality. Alguns clientes, especialmente aqueles com mais de um monitor físico, podem notar problemas com o layout de área de trabalho e o tratamento de entrada como resultado.

**Por que isso acontece**

o suporte para aplicativos Win32 clássicos no Windows Mixed Reality foi introduzido com o [Atualização de maio de 2019 para o Windows 10](/windows/mixed-reality/release-notes-may-2019). Para habilitar esse suporte, um monitor virtual deve ser criado para hospedar o aplicativo Win32. Cada vez que um novo aplicativo Win32 é iniciado, outro monitor virtual precisa ser criado. Infelizmente, a criação de um monitor virtual é uma tarefa intensiva que pode fazer com que a tela do headset congele brevemente. Os clientes ofereciam comentários de que a experiência ficou desconfortável e com interrupções. por causa desses comentários, junto com o aumento do uso de aplicativos Win32, decidimos alocar previamente três monitores virtuais durante a inicialização de Windows Mixed Reality para evitar essa interrupção e permitir que os clientes iniciem até três aplicativos simultâneos do Win32 sem experimentar o congelamento do headset.

**Solução alternativa**

Já que recebemos comentários de que alguns clientes, especialmente aqueles com vários monitores físicos, preferem desabilitar essa pré-alocação do monitor virtual. para fornecer aos clientes mais controle, habilitamos uma solução alternativa que envolve a alteração de um valor de chave do registro, disponível com as seguintes atualizações de Windows:

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

-   os sites abertos no Windows Mixed Reality serão perdidos quando o Portal da realidade misturada for fechado, embora o Microsoft Edge Windows permaneça onde eles foram colocados na casa misturada da realidade.
- As experiências de WebXR, incluindo a extensão do visualizador 360, podem não ser iniciadas corretamente em PCs com uma configuração de GPU híbrida. Você pode contornar esse problema habilitando um recurso de visualização no novo Microsoft Edge. Navegue até `edge://flags` , pesquise "várias GPU" e habilite o sinalizador chamado **WEBXR multi GPU support**.
-   o áudio do Microsoft Edge windows não está espacial.
-   **corrigido na extensão do visualizador 360 versão 2.3.8**: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Reiniciar a borda deve atualizar invisivelmente a extensão do visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem digitando `edge://system/` na barra de endereços e selecionando o botão **expandir** ao lado de "extensões".