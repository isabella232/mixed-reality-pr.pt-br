---
title: Usando Microsoft Edge em Windows Mixed Reality
description: Prepare-se para as novas Microsoft Edge em Windows Mixed Reality. Inclui alterações a esperar, atualizações a procurar e problemas conhecidos.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Home, Navigate, Get around, apps, games, Microsoft Edge, chromium, Edge, 360, 360 vídeo, visualizador 360
ms.openlocfilehash: 3cdb051e9925338a5f0145e106e2213712eb611e575b9f5d7dd29342a52ff38d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199482"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality e o novo Microsoft Edge

O [novo Microsoft Edge](https://www.microsoft.com/edge) está disponível para download e começou a ser disponibilizado automaticamente para os clientes por meio do Windows Update. 

O novo Microsoft Edge [adota o Chromium de código aberto](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) na área de trabalho. Isso cria melhor compatibilidade para clientes e menos fragmentação para desenvolvedores da Web. Ele também dará suporte ao WebXR no lançamento, que é o novo padrão para criar experiências imersivas da Web para headsets de VR, no lugar de WebVR.

>[!IMPORTANT]
>Quando você instala Microsoft Edge em um dispositivo Windows 10 atualizado, ele substituirá a versão anterior (herdada) em seu computador.

## <a name="installing-the-new-microsoft-edge"></a>Instalando o novo Microsoft Edge 

Antes de instalar o novo Microsoft Edge, atualize para **o Windows 10 versão 1903** ou posterior para suporte a aplicativos Win32 nativos, como o novo Microsoft Edge no Windows Mixed Reality. Verifique Windows Atualizar [ou instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/software-download/windows10).

Depois de Windows 10 versão 1903 ou posterior, você estará pronto para o novo Microsoft Edge! A nova Microsoft Edge está sendo implantada por meio do Windows Update, mas você pode instalar manualmente o novo Microsoft Edge do site [do Microsoft Edge](https://www.microsoft.com/edge) se quiser mais cedo.

>[!IMPORTANT]
>O novo Microsoft Edge é lançado com suporte para WebXR, o novo padrão para criar experiências da Web imersivas para headsets vr. Ao instalar o novo Microsoft Edge, você não poderá mais reproduzir experiências webVR Microsoft Edge. 

## <a name="known-issues"></a>Problemas conhecidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para Windows 10 versão 1903 (ou posterior)

- Iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a exibição do headset congele brevemente.
- O Microsoft Edge de dados desaparece do Windows Mixed Reality menu Iniciar (você pode encontrá-lo na pasta "Aplicativos clássicos").
- Windows das versões Microsoft Edge são colocadas em torno da casa da realidade misturada, mas não podem ser usadas. A tentativa de ativar essas janelas inicia o Edge no aplicativo desktop.
- A seleção de um hiperlink na página base da realidade misturada inicia um navegador da Web na área de trabalho em vez da página da realidade misturada.
- O aplicativo WebVR Showcase está presente na página de realidade misturada, apesar do WebVR não ter mais suporte.
- Melhorias gerais no início e nos visuais do teclado.

### <a name="monitor-and-input-handling-issues"></a>Problemas de monitoramento e tratamento de entrada

Depois de fazer a atualização cumulativa de 2020-01 para a versão 1903 ou posterior do Windows 10, os monitores virtuais aparecerão como monitores físicos genéricos na exibição do > do Configurações > durante as sessões do **Windows Mixed Reality.** Alguns clientes, especialmente aqueles com mais de um monitor físico, podem observar problemas com o layout da área de trabalho e a manipulação de entrada como resultado.

**Por que isso acontece**

O suporte para aplicativos Win32 clássicos Windows Mixed Reality foi introduzido com o [Atualização de maio de 2019 para o Windows 10](/windows/mixed-reality/release-notes-may-2019). Para habilitar esse suporte, um monitor virtual deve ser criado para hospedar o aplicativo Win32. Sempre que um novo aplicativo Win32 é lançado, outro monitor virtual precisa ser criado. Infelizmente, a criação de um monitor virtual é uma tarefa intensiva que pode fazer com que a exibição do headset congele brevemente. Os clientes ofereceram comentários de que a experiência foi invasiva e interrupção. Devido a esse feedback, juntamente com o aumento do uso de aplicativos Win32, decidimos alocar previamente três monitores virtuais durante a inicialização do Windows Mixed Reality para evitar essa interrupção e permitir que os clientes iniciarem até três aplicativos Win32 simultâneos sem enfrentar o congelamento de exibição do headset.

**Solução alternativa**

Desde então, recebemos comentários de que alguns clientes, especialmente aqueles com vários monitores físicos, preferem desabilitar essa pré-alocação do monitor virtual. Para dar aos clientes mais controle, habilitamos uma solução alternativa que envolve alterar um valor de chave do Registro, disponível com as seguintes Windows Atualizações:

- Versão Prévia da Atualização Cumulativa 2020-07 Windows 10 versão 2004 (KB4568831)
- Versão prévia da atualização cumulativa 2020-10 Windows 10 versão 1909 (KB4580386)
- Versão prévia da atualização cumulativa 2020-10 Windows 10 versão 1903 (KB4580386)

>[!NOTE]
>A modificação dos valores de chave do Registro destina-se a usuários avançados.

>[!WARNING]
>Desabilitar a pré-alocação do monitor virtual pode fazer com que a exibição do headset congele brevemente quando você inicia um aplicativo Win32 (como o Steam, o novo Microsoft Edge ou o Google Chrome) no Windows Mixed Reality.

Para desabilitar a pré-alocação do monitor virtual:
1. Verifique **Windows atualizar para** uma das versões Windows 10 versão prévia da atualização cumulativa listadas acima e instale a atualização quando disponível. Você pode encontrar a atualização em **Atualizações opcionais** ou **Opções avançadas** na página Windows Configurações de atualização
2. Iniciar **o Editor do Registro**
3. Navegue até "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se o REG_DWORD "PreallocateVirtualMonitors" não estiver presente, crie-o selecionando Editar > Novo valor **DWORD (32 bits)** do > e inserindo PreallocateVirtualMonitors como o nome
5. Se o REG_DWORD "PreallocateVirtualMonitors" estiver presente (ou você acabou de criar), clique duas vezes na entrada e altere "Dados de valor" de 1 (seu valor padrão) para 0 (zero)
    * TRUE – 1
    * FALSE – 0

Os monitores virtuais agora serão alocados quando você tentar iniciar um aplicativo Win32 no Windows Mixed Reality em vez de pré-alocar. Para redefinir isso e reabilitar a pré-alocação do monitor virtual, retorne a DWORD "Dados de valor" para 1.

### <a name="other-known-issues"></a>Outros problemas conhecidos

-   Sites abertos no Windows Mixed Reality serão perdidos quando Portal de Realidade Misturada fechar, embora as janelas Microsoft Edge permaneçam onde foram colocadas na casa da realidade misturada.
- As experiências do WebXR, incluindo a extensão do Visualizador 360, podem não ser lançadas corretamente em PCs com uma configuração de GPU híbrida. Você pode resolver esse problema habilitando um recurso de visualização na nova Microsoft Edge. Navegue `edge://flags` até , pesquise "multi gpu" e habilita o sinalizador chamado Suporte a Multi GPU do **WebXR.**
-   O áudio Microsoft Edge janelas não é espacializado.
-   Corrigido na versão **2.3.8** da extensão do Visualizador 360: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode fazer com que o vídeo seja distorcido no headset. Reiniciar o Edge deve atualizar invisivelmente a extensão do Visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem inserindo na barra de endereços e selecionando o botão Expandir ao lado `edge://system/` de "extensões". 