---
title: Como instalar o PIX para o HoloLens 2
description: Saiba como instalar o PIXEL para HoloLens 2 dispositivos.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, VR, captura, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217252"
---
# <a name="installing-pix-for-hololens-2"></a>Como instalar o PIX para o HoloLens 2

[OJUST](https://devblogs.microsoft.com/pix) é uma ferramenta de ajuste e depuração de desempenho para aplicativos DirectX 12 Windows. 

## <a name="setup"></a>Instalação

1. Pegue a versão MAIS [recente]( https://devblogs.microsoft.com/pix/download) do BLOOM do computador host e conecte o HoloLens 2 ao computador por meio de um cabo USB.

2. Se o HoloLens 2 estiver em um [build do Windows Insider](https://insider.windows.com) ou tiver uma configuração que interrompe o HAS, [reflash](/hololens/hololens-recovery) seu dispositivo para apagar todos os dados.

3. **Habilita o Modo** de Desenvolvedor e **Portal de Dispositivos**:

* Abra **Configurações** página da Página De Realidade Misturada:

![Captura de tela do menu HoloLens com o botão de configurações realçada](images/pix-img-01.jpg)

* Selecione **Atualizar & Segurança:**

![Captura de tela da janela de configurações aberta HoloLens com o botão de atualização e segurança realçada](images/pix-img-02.jpg)

* Selecione **Para Desenvolvedores:**

![Captura de tela da janela de segurança e atualizações aberta com o botão para desenvolvedores realçada](images/pix-img-03.jpg)

* Ativar Usar **recursos de desenvolvedor e** **habilitar Portal de Dispositivos**

![Captura de tela da janela para desenvolvedores aberta nas configurações com o botão Habilitar portal do dispositivo realçada](images/pix-img-04.jpg)

![Captura de tela da janela para desenvolvedores aberta nas configurações com a alternância Desenvolver recursos realçada](images/pix-img-05.jpg)

* Com o dispositivo ainda conectado, acionada e com o usuário conectado, Visual Studio.

> [!IMPORTANT]
> Certifique-se de que seu dispositivo não está no modo de espera ou está em espera. Se você estiver tendo problemas com esta etapa, consulte as instruções [Windows Portal de Dispositivos .](./using-the-windows-device-portal.md)

## <a name="preparing-for-deployment"></a>Preparando-se para implantação

1. No Visual Studio, de definir **ARM64** como a plataforma e **Dispositivo** como o dispositivo:

![Captura de tela da solução de estúdios visuais com as configurações de plataforma e dispositivo realçadas](images/pix-img-06.png)

2. Quando Visual Studio solicita um **PIN** do dispositivo:

![Captura de tela do pop-up do Visual Studio solicitando PIN](images/pix-img-07.png)

* Selecione **Configurações** shell
* Selecione **Atualizar & Segurança**
* Selecione **Para Desenvolvedores e** pressione Emparelhar em Descoberta de **Dispositivo** 

![Captura de tela da janela para desenvolvedores aberta nas configurações com a descoberta de dispositivo realçada](images/pix-img-08.jpg)

![Captura de tela do pop-up de dispositivo pago com o código de registro realçada](images/pix-img-09.jpg)

* Insira o número do PIN gerado Visual Studio

3. Visual Studio implantará o aplicativo no HoloLens 2 conectado, o que pode levar alguns minutos, dependendo do aplicativo.

## <a name="launching-pix"></a>Iniciando o BLOOM

Primeiro, use Portal de Dispositivos para verificar se o aplicativo não está em execução no HoloLens 2. Em seguida, iniciar o BLOOM, conectar-se ao seu dispositivo e selecionar **Página Início:**

![Captura de tela da tela inicial do aplicativo PIXEL](images/pix-img-10.png)

* Selecione **Conexão** no menu do lado esquerdo:

![Captura de tela do menu do lado esquerdo do aplicativo PIXEL com o botão Conectar realçada](images/pix-img-11.png)

2. Na guia **Computador,** selecione **Adicionar** e insira as seguintes credenciais:
    * Alias: a critério do usuário
    * Nome do host ou endereço IP: 127.0.0.1

3. Selecione **Conexão** no canto inferior direito da **guia** Computador:

![Captura de tela da janela de conexão de aplicativos DOD com alias, nome do host, endereço IP e botão adicionar realçada](images/pix-img-12.png)

> [!NOTE]
> A primeira conexão é sempre mais lenta porque os binários estão sendo copiados.

4. Quando o RATE estiver conectado ao HoloLens 2,  encontre seu aplicativo na seção Selecionar Processo de Destino na guia Iniciar UWP e selecione **Iniciar**:

![Captura de tela do aplicativo PIXEL com a janela selecionar processo de destino e o botão iniciar realçadas](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU capturada

1. Inicie a captura de GPU clicando em **Foto** na seção **Captura de GPU:**

![Captura de tela do aplicativo PIXEL com o painel de conexão do COMPUTADOR aberto com a captura de GPU realçada](images/pix-img-14.png)

2. Abra a captura para análise clicando na captura de tela gerada no painel **Captura de GPU:**

![Captura de tela do aplicativo PIXEL com a seção captura de GPU aberta com o painel de captura de GPU realçada](images/pix-img-15.png)

3. Pressione **Iniciar** para iniciar a análise:

![Captura de tela do aplicativo PIXEL realçada pelo botão Iniciar](images/pix-img-16.png)

> [!IMPORTANT]
> Se você coletar dados de tempo depois de fazer uma captura de GPU, será necessário reinicializar o headset. Essa é uma reinicialização única do dispositivo e é necessária para a coleta de dados de tempo.

AGORA, o BLOOM está pronto para uso!

## <a name="see-also"></a>Confira também
* [Home page do BLOOM](https://devblogs.microsoft.com/pix)