---
title: Depuração gerenciada com o Unity IL2CPP
description: Este artigo aborda como executar um depurador gerenciado em seu projeto do IL2CPP UWP do Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuração, il2cpp, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010237"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuração gerenciada com o Unity IL2CPP

Siga estas etapas para anexar um depurador gerenciado à sua compilação do IL2CPP UWP do Unity para o HoloLens e o HoloLens 2.

1. Você precisará estar em uma rede que dá suporte a [multicast](https://en.wikipedia.org/wiki/Multicast).
2. Vá para **configurações de publicação de UWP recursos** e verifique **InternetClientServer** e **PrivateNetworkClientServer**:

    ![Funcionalidades de configurações de publicação do UWP](images/il2cpp-debugging-capabilities.png)

3. Defina as configurações de Build do Unity UWP:
    - Build de desenvolvimento
    - Depuração de scripts
    - Aguardar o depurador gerenciado (opcional)

    ![Configurações de Build do UWP](images/il2cpp-debugging-build.png)

4. Compilar no Unity.
5. Crie e implante a partir da solução do Visual Studio para seu dispositivo. Você deve criar com as configurações de **depuração** ou de **versão** . A configuração **mestra** desabilita o Unity Profiler e pode impedir a depuração ideal. Opcionalmente, verifique a **Internet (cliente & Server)** e as **redes privadas (cliente & Server)** na lista de recursos em Package. appxmanifest na solução.
6. Verifique se o dispositivo está conectado à mesma rede que o seu PC e inicie o aplicativo em seu dispositivo.
7. Verifique se o dispositivo **não está** conectado ao seu PC via USB.
8. Clique duas vezes em um dos seus scripts no Unity e vá para a solução do Visual Studio que é aberta para exibir e editar.
9. Debug-> anexar o depurador Unity.

    ![Anexar depurador do Unity](images/il2cpp-debugging-attach.png)

10. Selecione seu dispositivo na lista e clique em "OK" para anexar.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
