---
title: Usando o Microsoft Edge no Windows Mixed Reality
description: Prepare-se para o novo Microsoft Edge no Windows Mixed Reality. Inclui alterações esperadas, atualizações a serem verificadas e problemas conhecidos.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, página inicial, navegar, contornar, aplicativos, jogos, Microsoft Edge, Chromium, Edge, 360, 360 vídeo, 360 Viewer
ms.openlocfilehash: d3ed8f95285eefacf43177915d512bfb41730243
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725777"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Realidade mista do Windows e o novo Microsoft Edge

O [novo Microsoft Edge](https://www.microsoft.com/edge) está disponível para download e começou a distribuir automaticamente para os clientes por meio de Windows Update. 

O novo Microsoft Edge [adota o projeto de código-fonte aberto Chromium](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) na área de trabalho. Isso cria uma melhor compatibilidade para os clientes e menos fragmentação para desenvolvedores da Web. Ele também dará suporte a WebXR na inicialização, que é o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

>[!IMPORTANT]
>Quando você instalar o Microsoft Edge em um dispositivo Windows 10 atualizado, ele substituirá a versão anterior (herdada) em seu computador.

## <a name="installing-the-new-microsoft-edge"></a>Instalando o novo Microsoft Edge 

Antes de instalar o novo Microsoft Edge, **atualize para o Windows 10 versão 1903 ou posterior para suporte de aplicativo Win32 nativo como o novo Microsoft Edge** no Windows Mixed Reality. Verifique Windows Update ou [Instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/software-download/windows10).

Quando tiver o Windows 10 versão 1903 ou posterior, você estará pronto para o novo Microsoft Edge! O novo Microsoft Edge é distribuído por meio de Windows Update, mas você pode instalar manualmente o novo Microsoft Edge no [site do Microsoft Edge](https://www.microsoft.com/edge) se desejar mais cedo.

>[!IMPORTANT]
>O novo Microsoft Edge é iniciado com suporte para WebXR, o novo padrão para a criação de experiências de imersão da Web para headsets de VR. Ao instalar o novo Microsoft Edge, você não poderá mais reproduzir experiências de WebVR no Microsoft Edge. 

## <a name="known-issues"></a>Problemas conhecidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior)

- Iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a tela do headset congele brevemente.
- O bloco Microsoft Edge desaparece do menu Iniciar do Windows Mixed Reality (você pode encontrá-lo na pasta "aplicativos clássicos").
- As janelas do Microsoft Edge anterior ainda são colocadas em todo o início da realidade misturada, mas não podem ser usadas. A tentativa de ativar essas janelas inicia a borda no aplicativo da área de trabalho.
- A seleção de um hiperlink na página inicial da realidade misturada inicia um navegador da Web na área de trabalho em vez da casa mistura de realidade.
- O aplicativo de demonstração do WebVR está presente na casa da realidade misturada, apesar de WebVR não ter mais suporte.
- Aprimoramentos gerais na inicialização e visuais do teclado.

### <a name="monitor-and-input-handling-issues"></a>Problemas de monitor e de tratamento de entrada

Depois de fazer a atualização cumulativa 2020-01 para o Windows 10 versão 1903 ou posterior, os monitores virtuais aparecerão como monitores físicos genéricos em **configurações > sistema > exibido** durante sessões de realidade mista do Windows. Alguns clientes, especialmente aqueles com mais de um monitor físico, podem notar problemas com o layout de área de trabalho e o tratamento de entrada como resultado.

**Por que isso acontece**

O suporte para aplicativos Win32 clássicos no Windows Mixed Reality foi introduzido com a [atualização do Windows 10 de maio de 2019](https://docs.microsoft.com/windows/mixed-reality/release-notes-may-2019). Para habilitar esse suporte, um monitor virtual deve ser criado para hospedar o aplicativo Win32. Cada vez que um novo aplicativo Win32 é iniciado, outro monitor virtual precisa ser criado. Infelizmente, a criação de um monitor virtual é uma tarefa intensiva que pode fazer com que a tela do headset congele brevemente. Os clientes ofereciam comentários de que a experiência ficou desconfortável e com interrupções. Por causa desses comentários, junto com o aumento do uso de aplicativos Win32, decidimos alocar previamente três monitores virtuais durante a inicialização da realidade mista do Windows para evitar essa interrupção e permitir que os clientes iniciem até três aplicativos simultâneos do Win32 sem experimentar o congelamento de vídeo do headset.

**Solução alternativa**

Já que recebemos comentários de que alguns clientes, especialmente aqueles com vários monitores físicos, preferem desabilitar essa pré-alocação do monitor virtual. Para fornecer aos clientes mais controle, habilitamos uma solução alternativa que envolve a alteração de um valor de chave do registro, disponível com as seguintes atualizações do Windows:

- Versão prévia da atualização cumulativa 2020-07 para Windows 10 2004 (KB4568831)
- Versão prévia da atualização cumulativa 2020-10 para Windows 10 1909 (KB4580386)
- Versão prévia da atualização cumulativa 2020-10 para Windows 10 1903 (KB4580386)

>[!NOTE]
>A modificação de valores de chave do registro destina-se a usuários avançados.

>[!WARNING]
>Desabilitar a pré-alocação do virtual monitor pode resultar na exibição resumida do fone de ouvido ao iniciar um aplicativo Win32 (como o fluxo, o novo Microsoft Edge ou o Google Chrome) no Windows Mixed Reality.

Para desabilitar a pré-alocação do monitor virtual:
1. Verifique **Windows Update** para uma das versões de visualização de atualização cumulativa do Windows 10 listadas acima e instale a atualização quando disponível. Você pode encontrar a atualização em **atualizações opcionais** ou **Opções avançadas** na página Configurações de Windows Update
2. Iniciar **Editor do registro**
3. Navegue até "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se a REG_DWORD "PreallocateVirtualMonitors" não estiver presente, crie-a selecionando **editar > novo > valor DWORD (32 bits)** e inserindo PreallocateVirtualMonitors como o nome
5. Se a REG_DWORD "PreallocateVirtualMonitors" estiver presente (ou você acabou de criá-la), clique duas vezes na entrada e altere "dados do valor" de 1 (seu valor padrão) para 0 (zero)
    * TRUE-1
    * FALSE-0

Os monitores virtuais agora serão alocados quando você tentar iniciar um aplicativo Win32 no Windows Mixed Reality em vez de pré-instalar. Para redefinir essa configuração e reabilitar a pré-alocação do monitor virtual, retorne o DWORD "value data" para 1.

### <a name="other-known-issues"></a>Outros problemas conhecidos

-   Os sites abertos no Windows Mixed Realm serão perdidos quando o portal da realidade misturada for fechado, embora as janelas do Microsoft Edge permaneçam onde foram colocadas na casa misturada da realidade.
- As experiências de WebXR, incluindo a extensão do visualizador 360, podem não ser iniciadas corretamente em PCs com uma configuração de GPU híbrida. Você pode contornar esse problema habilitando um recurso de visualização no novo Microsoft Edge. Navegue até `edge://flags` , pesquise "várias GPU" e habilite o sinalizador chamado **WEBXR multi GPU support**.
-   O áudio do Microsoft Edge Windows não está espacial.
-   **Corrigido na extensão do visualizador 360 versão 2.3.8**: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Reiniciar a borda deve atualizar invisivelmente a extensão do visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem digitando `edge://system/` na barra de endereços e selecionando o botão **expandir** ao lado de "extensões".
