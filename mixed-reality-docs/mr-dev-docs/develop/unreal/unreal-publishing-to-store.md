---
title: Publicar na Microsoft Store
description: Saiba como empacotar, certificar e publicar seus aplicativos de Realidade Misturada do Unreal na Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, publicação, distribuição, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010016"
---
# <a name="publishing-to-the-microsoft-store"></a>Publicar na Microsoft Store

Quando estiver pronto para divulgar seu aplicativo Unreal para o mundo, haverá algumas configurações de projeto que precisam ser atualizadas antes de você enviá-lo à Microsoft Store. Todas essas configurações têm valores padrão, mas devem ser alteradas para produção a fim de melhor representar o aplicativo.

## <a name="project-settings-for-the-store-packaging"></a>Configurações de projeto para o empacotamento da loja

1. Primeiro, selecione **Configurações de Projeto > Descrição** e atualize as informações do jogo e do editor: 
    * O **Nome do Jogo** será exibido no bloco do aplicativo no HoloLens
    * O **Nome Diferenciado da Empresa** é usado ao gerar o certificado do projeto e deve estar no formato: 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:

![Captura de tela do editor do Unreal com a seção Descrição expandida em Configurações de Projeto](images/unreal-publishing-img-01.png)

2. Expanda a seção **HoloLens** das configurações de projeto e atualize os recursos de empacotamento.  Esses nomes de recursos serão mostrados na página da loja do aplicativo:

![Captura de tela do editor do Unreal com a seção Empacotamento expandida em Configurações de Projeto](images/unreal-publishing-img-02.png)

3. Expanda a seção **Imagens** e atualize as imagens da loja padrão com texturas que representam o aplicativo da loja.  Opcionalmente, marque a caixa de seleção **Logotipo 3D** para carregar um arquivo glb e usá-lo como um cubo 3D ao iniciar o aplicativo:

![Captura de tela do editor do Unreal com a seção Imagens expandida em Configurações de Projeto](images/unreal-publishing-img-03.png)

4. Por fim, selecione **Gerar Novo** para gerar um certificado de autenticação com base no nome do projeto e no nome diferenciado da empresa  
    * Defina uma **Cor da Tela de Fundo do Bloco**, que será exibida no lugar dos pixels transparentes nas imagens da loja.
    * Expanda a lista suspensa e habilite a opção **Usar o Ambiente da Microsoft Store de varejo** para execução em dispositivos bloqueados para varejo e não desbloqueados para desenvolvimento.

![Captura de tela do editor do Unreal com a seção Geração de certificado expandida em Configurações de Projeto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>Instalador de Aplicativo opcional

Um arquivo do Instalador de Aplicativo pode ser criado em **Configurações de Projeto > HoloLens**, que pode ser usado para distribuir o aplicativo fora da loja.  Habilite a caixa de seleção **Deve Criar Instalador de Aplicativo** e defina uma URL ou um caminho de rede no qual deseja que o appxbundle do jogo seja armazenado.  

![Captura de tela do editor do Unreal com a seção Instalador de Aplicativo expandida em Configurações de Projeto](images/unreal-publishing-img-05.png)

Quando o aplicativo estiver sendo empacotado, o appxbundle e o appinstaller serão gerados.  Carregue o appxbundle na URL de instalação e inicie o appinstaller para instalar o aplicativo por meio da localização de rede.

## <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

O SDK do Windows 10 é fornecido com o WACK (Kit de Certificação de Aplicativos Windows) para validar problemas comuns que possam afetar o upload de um pacote na loja.  Encontre o WACK no diretório Kits do Windows, geralmente no seguinte caminho: 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. Depois que o arquivo appx for empacotado para publicação, execute **appcertui.exe** e siga os avisos para verificar o appx:

![Captura de tela do aplicativo sendo selecionado para validação no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-06.png)

2. Selecione **Validar Aplicativo da Loja**:

![Captura de tela da seleção de validação no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-07.png)

3. Procure o appx na seção superior e selecione **Avançar**:

![Captura de tela da seleção de teste no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-08.png)

4. Selecione **Avançar** para executar os testes e criar um relatório:
    * Todos os testes disponíveis que podem ser executados no PC host serão habilitados por padrão

![Captura de tela do progresso de validação do aplicativo no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-09.png)

5. Aguarde a conclusão dos testes. Depois que os testes forem concluídos, a janela final mostrará um resultado de aprovação ou reprovação, que pode ser exibido no relatório salvo.

![Captura de tela dos resultados do relatório final no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>Falha conhecida do WACK na versão 4.25

O plug-in do Windows Mixed Reality no Unreal 4.25 causará uma falha no WACK devido à inclusão de alguns binários x64 durante o empacotamento para o HoloLens. A falha terá a seguinte aparência:

![Captura de tela de um resultado com falha devido ao analisador binário e às APIs compatíveis do Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-11.png)

Para corrigir o problema:
1. Procure a raiz do diretório de origem ou da instalação do Unreal abrindo um projeto do Unreal e clique com o botão direito do mouse no ícone do Unreal na barra de tarefas.
2. Clique com o botão direito do mouse em UE4Editor, selecione Propriedades e procure o caminho na entrada **Localização**:

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. Em **WindowsMixedRealityHMD.Build.cs**, modifique a linha **32** de:

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

para:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Feche o Unreal, reabra o projeto e recrie o pacote para o HoloLens.  Execute o WACK novamente e o erro deixará de ser exibido. 

## <a name="see-also"></a>Confira também

* [Como enviar um aplicativo para a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Kit de Certificação de Aplicativos Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [Criar manualmente um arquivo do Instalador de Aplicativo](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)