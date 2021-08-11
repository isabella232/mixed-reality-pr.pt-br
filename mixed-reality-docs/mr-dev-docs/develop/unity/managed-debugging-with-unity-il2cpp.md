---
title: Depuração gerenciada com o Unity
description: Este artigo aborda como executar um depurador gerenciado em seu projeto UWP do Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, depuração, il2cpp, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, UWP
ms.openlocfilehash: 92b730768b6402b356e550d8f01d85e654832aef1ac382d8f992df615a9ce1b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196522"
---
# <a name="managed-debugging-with-unity"></a>Depuração gerenciada com o Unity

Siga estas etapas para anexar um depurador gerenciado ao build UWP do Unity IL2CPP para HoloLens e HoloLens 2.

1. Você precisará estar em uma rede que dá suporte a [multicast.](https://en.wikipedia.org/wiki/Multicast)
2. Vá para **Funcionalidades de Configurações UWP** e verifique **InternetClientServer** e **PrivateNetworkClientServer:**

    ![Funcionalidades de Configurações UWP](images/il2cpp-debugging-capabilities.png)

3. De acordo com as configurações de build da UWP do Unity:
    - Build de desenvolvimento
    - Depuração de scripts
    - Aguardar o Depurador Gerenciado (opcional)

    ![UWP Build Configurações](images/il2cpp-debugging-build.png)

4. Criar no Unity.
5. Crie e implante da solução Visual Studio para seu dispositivo. Você deve criar com as **configurações de Depuração** **ou** Versão. A **configuração** Mestre desabilita o profiler do Unity e pode impedir a depuração ideal. Opcionalmente, verifique **Internet (Servidor & Cliente)** e Redes Privadas **(Cliente & Server)** na lista de funcionalidades em Package.appxmanifest na solução.
6. Certifique-se de que seu dispositivo esteja conectado à mesma rede que o computador e inicie o aplicativo em seu dispositivo.
7. Certifique-se de que **o dispositivo não esteja** conectado ao computador via USB.
8. Clique duas vezes em um de seus scripts no Unity e vá para a Visual Studio que é aberta para exibir e editar.
9. Depurar -> Anexar Depurador do Unity.

    ![Anexar o depurador do Unity](images/il2cpp-debugging-attach.png)

10. Selecione seu dispositivo na lista e clique em "OK" para anexar.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Confira também 

* [Depuração de C#](/visualstudio/get-started/csharp/tutorial-debugger)
