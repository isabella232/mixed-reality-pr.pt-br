---
title: Visão geral do sistema de câmeras
description: Página de aterrissagem do sistema de câmera no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, câmera,
ms.openlocfilehash: 3c9bdbc96688c4df6ee2f39be2c8bb2023817f9081b5366308ba8b4c2590568d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211439"
---
# <a name="camera-system-overview"></a>Visão geral do sistema de câmeras

o sistema de câmera permite que a realidade misturada da Microsoft Toolkit configurar e otimizar a câmera do aplicativo para uso em aplicativos de realidade misturada. usando o sistema de câmera, os aplicativos podem ser escritos para dar suporte a dispositivos opacos (ex: virtual reality) e transparent (ex: Microsoft HoloLens) sem a necessidade de escrever código para distinguir entre e acomodar cada tipo de exibição.

## <a name="enabling-the-camera-system"></a>Habilitando o sistema de câmera

O sistema de câmera é gerenciado pelo objeto MixedRealityToolkit (ou outro componente registrador de serviço).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![MRTK hierarquia de cena configurada](../images/MRTK_ConfiguredHierarchy.png)

2. Navegue pelo painel Inspetor até a seção sistema de câmera e verifique se a opção **habilitar sistema de câmera** está marcada.

    ![Habilitando o sistema de câmera](../images/camera-system/EnableCameraSystem.png)

3. Selecione a implementação do sistema de câmera. A implementação de classe padrão fornecida pelo MRTK é o `MixedRealityCameraSystem` .

    ![Selecione a implementação do sistema de câmera](../images/camera-system/SelectCameraSystemType.png)

4. Selecionar o perfil de configuração desejado

    ![Selecionar perfil do sistema de câmera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configurando o sistema de câmera

### <a name="settings-providers"></a>provedores de Configurações

![provedores de Configurações de câmera](../images/camera-system/CameraSettingsProviders.png)

Os provedores de configuração da câmera habilitam a configuração específica da plataforma da câmera. Essas configurações podem incluir etapas de configuração personalizadas e/ou componentes.

os provedores podem ser adicionados clicando no botão **adicionar câmera Configurações provedor** . Eles podem ser removidos clicando no **-** botão à direita do nome do provedor.

> [!Note]
> Nem todas as plataformas precisarão de um provedor de configurações de câmera. se não houver provedores compatíveis com a plataforma na qual o aplicativo está sendo executado, a realidade misturada da Microsoft Toolkit aplicará padrões básicos.

### <a name="display-settings"></a>Configurações de vídeo

![Configurações de exibição da câmera](../images/camera-system/CameraDisplaySettings.png)

as configurações de exibição são especificadas para exibições opacas (ex: Virtual reality) e transparente (ex: Microsoft HoloLens). A câmera está configurada, em tempo de execução, usando essas configurações.

**Clipe próximo**

O plano próximo é o mais próximo, em metros, que um objeto virtual pode ser para a câmera e ainda ser renderizado. Para maior conforto ao usuário, é recomendável tornar esse valor maior que zero. A imagem anterior contém valores que foram considerados confortáveis em uma variedade de dispositivos.

**Clipe distante**

O plano de clipe distante é o mais distante, em metros, que um objeto virtual pode ser para a câmera e ainda assim ser renderizado. Para dispositivos transparentes, é recomendável que esse valor seja relativamente próximo de exceder excessivamente o espaço real do mundo e interromper as qualidades de imersão do aplicativo.

**Limpar sinalizadores**

O valor limpar sinalizadores indica como a exibição é limpa, pois é desenhada. Para experiências de realidade virtual, esse valor é definido com mais frequência como Skybox. Para exibições transparentes, é recomendável defini-lo para cor.

**Cor do plano de fundo**

Se os sinalizadores claros não estiverem definidos como Skybox, a propriedade cor do plano de fundo será exibida.

**Configurações de Qualidade**

O valor das configurações de qualidade indica a qualidade de gráficos que o Unity deve usar ao renderizar a cena. O nível de qualidade é uma configuração de nível de projeto e não é específico de uma câmera. Para obter mais informações, consulte o artigo [qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html) na documentação do Unity.

## <a name="see-also"></a>Confira também

- [Documentação da API do sistema de câmera](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [criando um provedor de Configurações de câmera](create-settings-provider.md)
