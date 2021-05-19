---
title: Visão geral do sistema de câmera
description: Página de aterrissagem do sistema de câmeras no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera,
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144474"
---
# <a name="camera-system"></a>Sistema de câmeras

O sistema de câmeras permite que o Microsoft Mixed Reality Toolkit configure e otimize a câmera do aplicativo para uso em aplicativos de realidade misturada. Usando o sistema de câmeras, os aplicativos podem ser escritos para dar suporte a dispositivos opacos (por exemplo: realidade virtual) e transparentes (por exemplo: Microsoft HoloLens) sem a necessidade de escrever código para distinguir e acomodar cada tipo de exibição.

## <a name="enabling-the-camera-system"></a>Habilitando o sistema de câmeras

O Sistema de Câmera é gerenciado pelo objeto MixedRealityToolkit (ou outro componente do registrador de serviços).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Navegue pelo painel Inspetor até a seção sistema de câmeras e verifique se **Habilitar Sistema de Câmera** está marcado.

    ![Habilitando o sistema de câmeras](../images/camera-system/EnableCameraSystem.png)

3. Selecione a implementação do sistema de câmera. A implementação de classe padrão fornecida pelo MRTK é o `MixedRealityCameraSystem` .

    ![Selecionar a implementação do sistema de câmeras](../images/camera-system/SelectCameraSystemType.png)

4. Selecione o perfil de configuração desejado

    ![Selecionar perfil do sistema de câmera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configurando o sistema de câmeras

### <a name="settings-providers"></a>Provedores de configurações

![Provedores de configurações da câmera](../images/camera-system/CameraSettingsProviders.png)

Os provedores de configuração da câmera habilitam a configuração específica da plataforma da câmera. Essas configurações podem incluir etapas de configuração personalizadas e/ou componentes.

Os provedores podem ser adicionados clicando no botão **Adicionar provedor de configurações de câmera** . Eles podem ser removidos clicando no **-** botão à direita do nome do provedor.

> [!Note]
> Nem todas as plataformas precisarão de um provedor de configurações de câmera. Se não houver provedores compatíveis com a plataforma na qual o aplicativo está sendo executado, o kit de ferramentas do Microsoft Mixed Reality aplicará padrões básicos.

### <a name="display-settings"></a>Configurações de vídeo

![Configurações de vídeo da câmera](../images/camera-system/CameraDisplaySettings.png)

As configurações de exibição são especificadas para exibições opacas (ex: virtual reality) e Transparent (ex: Microsoft HoloLens). A câmera está configurada, em tempo de execução, usando essas configurações.

**Clipe próximo**

O plano próximo é o mais próximo, em metros, que um objeto virtual pode ser para a câmera e ainda ser renderizado. Para maior conforto ao usuário, é recomendável tornar esse valor maior que zero. A imagem anterior contém valores que foram considerados confortáveis em uma variedade de dispositivos.

**Clipe distante**

O plano de clipe distante é o mais distante, em metros, que um objeto virtual pode ser para a câmera e ainda assim ser renderizado. Para dispositivos transparentes, é recomendável que esse valor seja relativamente próximo de exceder excessivamente o espaço real do mundo e interromper as qualidades de imersão do aplicativo.

**Limpar sinalizadores**

O valor limpar sinalizadores indica como a exibição é limpa, pois é desenhada. Para experiências de realidade virtual, esse valor é definido com mais frequência como Skybox. Para exibições transparentes, é recomendável definir isso como Cor.

**Cor da tela de fundo**

Se os sinalizadores não definidos como Skybox, a propriedade de cor da tela de fundo será exibida.

**Configurações de Qualidade**

O valor de configurações de qualidade indica a qualidade dos gráficos que o Unity deve usar ao renderizar a cena. O nível de qualidade é uma configuração de nível de projeto e não é específico para nenhuma câmera. Para obter mais informações, consulte o [artigo Qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html) na documentação do Unity.

## <a name="see-also"></a>Confira também

- [Documentação da API do Sistema de Câmera](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Criando um provedor de configurações de câmera](create-settings-provider.md)
