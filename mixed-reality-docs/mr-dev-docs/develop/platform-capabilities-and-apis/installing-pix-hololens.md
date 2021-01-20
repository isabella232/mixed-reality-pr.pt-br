---
title: Como instalar o PIX para o HoloLens 2
description: Saiba como instalar o PIX para dispositivos do HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, captura, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 29cb741cd986fbb98dabb1faf2051450fd0286c3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583093"
---
# <a name="installing-pix-for-hololens-2"></a>Como instalar o PIX para o HoloLens 2

O [PIX](https://devblogs.microsoft.com/pix) é uma ferramenta de ajuste e depuração de desempenho para aplicativos DirectX 12 no Windows. 

## <a name="setup"></a>Instalação

1. Obtenha a [versão]( https://devblogs.microsoft.com/pix/download) mais recente do PIX do seu PC host e conecte o seu HoloLens 2 ao seu PC por meio de um cabo USB.

2. Se o seu HoloLens 2 estiver em um [Build do Windows Insider](https://insider.windows.com) ou tiver uma configuração que interrompa o PIX,  [repisque seu dispositivo](/hololens/hololens-recovery) para apagar todos os dados.

3. Habilitar o **modo de desenvolvedor** e o portal do **dispositivo**:

* Abra **as configurações** do início da realidade misturada:

![Captura de tela do menu do HoloLens com o botão Configurações realçado](images/pix-img-01.jpg)

* Selecione **Atualizar segurança &**:

![Captura de tela da janela de configurações aberta no HoloLens com o botão de atualização e segurança realçado](images/pix-img-02.jpg)

* Selecione **para desenvolvedores**:

![Captura de tela da janela segurança e atualizações abrir com o botão desenvolvedores realçado](images/pix-img-03.jpg)

* Ativar o **uso de recursos de desenvolvedor** e **habilitar o portal do dispositivo**

![Captura de tela da janela para desenvolvedores abrir em configurações com o botão habilitar portal do dispositivo realçado](images/pix-img-04.jpg)

![Captura de tela da janela para desenvolvedores abrir em configurações com a opção usar desenvolver recursos alternar realçada](images/pix-img-05.jpg)

* Com o dispositivo ainda conectado, ativo e com o usuário conectado, inicie o Visual Studio.

> [!IMPORTANT]
> Verifique se o dispositivo não está no modo de espera ou em suspensão. Se você estiver tendo problemas com essa etapa, consulte as [instruções do portal de dispositivo do Windows](./using-the-windows-device-portal.md).

## <a name="preparing-for-deployment"></a>Preparando para implantação

1. No Visual Studio, defina **ARM64** como a plataforma e o **dispositivo** como o dispositivo:

![Captura de tela da solução Visual estúdios com as configurações de plataforma e dispositivo realçadas](images/pix-img-06.png)

2. Quando o Visual Studio solicitar um **PIN** do dispositivo:

![Captura de tela do pop-up do Visual Studio solicitando PIN](images/pix-img-07.png)

* Selecione **as configurações** do Shell
* Selecione **Atualizar segurança &**
* Selecione **para desenvolvedores** e pressione o par em **descoberta de dispositivo** 

![Captura de tela da janela para desenvolvedores abrir em configurações com descoberta de dispositivo realçada](images/pix-img-08.jpg)

![Captura de tela do pop-up do dispositivo pago com o código de registro realçado](images/pix-img-09.jpg)

* Insira o número de PIN gerado no Visual Studio

3. O Visual Studio implantará o aplicativo no HoloLens 2 conectado, o que pode levar alguns minutos, dependendo do aplicativo.

## <a name="launching-pix"></a>Iniciando o PIX

Primeiro, use o portal do dispositivo para verificar se o aplicativo não está em execução no HoloLens 2. Em seguida, inicie o PIX, conecte-se ao seu dispositivo e selecione **início**:

![Captura de tela da página inicial do aplicativo PIX](images/pix-img-10.png)

* Selecione **conectar** no menu do lado esquerdo:

![Captura de tela do menu do lado esquerdo do aplicativo PIX com o botão conectar realçado](images/pix-img-11.png)

2. Na guia **computador** , selecione **Adicionar** e insira as seguintes credenciais:
    * Alias: até o critério do usuário
    * Nome do host ou endereço IP: 127.0.0.1

3. Selecione **conectar** no canto inferior direito da guia **computador** :

![Captura de tela da janela de conexão de aplicativo do PIX com alias, nome do host, endereço IP e botão Adicionar realçado](images/pix-img-12.png)

> [!NOTE]
> A primeira conexão é sempre mais lenta porque os binários estão sendo copiados.

4. Quando o PIX tiver se conectado ao HoloLens 2, localize seu aplicativo na seção **selecionar processo de destino** na guia Iniciar UWP e selecione **Iniciar**:

![Captura de tela do aplicativo PIX com a janela Selecionar processo de destino e o botão iniciar realçado](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU capturada

1. Inicie a captura de GPU clicando em **foto** na seção de **captura de GPU** :

![Captura de tela do aplicativo PIX com o painel de conexão do PC aberto com a captura de GPU realçada](images/pix-img-14.png)

2. Abra a captura para análise clicando na captura de tela gerada no painel de **captura de GPU** :

![Captura de tela do aplicativo PIX com a seção de captura de GPU aberta com o painel de captura de GPU realçado](images/pix-img-15.png)

3. Pressione **Iniciar** para iniciar a análise:

![Captura de tela do aplicativo PIX o botão iniciar realçado](images/pix-img-16.png)

> [!IMPORTANT]
> Se você coletar dados de tempo depois de fazer uma captura de GPU, será necessário reinicializar o headset. Este é um reinício único do dispositivo e é necessário para a coleta de dados de tempo.

O PIX agora está pronto para uso!

## <a name="see-also"></a>Confira também
* [Home Page do PIX](https://devblogs.microsoft.com/pix)