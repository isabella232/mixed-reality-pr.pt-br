---
title: Visão geral do sistema de câmeras
description: Página de aterrissagem do sistema de câmeras no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177040"
---
# <a name="camera-system-overview"></a>Visão geral do sistema de câmeras

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

### <a name="settings-providers"></a>Configurações provedores

![Provedores Configurações câmera](../images/camera-system/CameraSettingsProviders.png)

Os provedores de configuração de câmera habilitam a configuração específica da plataforma da câmera. Essas configurações podem incluir etapas de configuração personalizadas e/ou componentes.

Os provedores podem ser adicionados clicando no **botão Adicionar Câmera Configurações Provedor.** Eles podem ser removidos clicando **-** no botão à direita do nome do provedor.

> [!Note]
> Nem todas as plataformas exigirão um provedor de configurações de câmera. Se não houver provedores compatíveis com a plataforma na qual o aplicativo está sendo executado, o Microsoft Mixed Reality Toolkit aplicará padrões básicos.

### <a name="display-settings"></a>Configurações de vídeo

![Exibição da câmera Configurações](../images/camera-system/CameraDisplaySettings.png)

As configurações de exibição são especificadas para exibições opacas (por exemplo: Realidade Virtual) e transparentes (por exemplo, Microsoft HoloLens). A câmera é configurada, em tempo de executar, usando essas configurações.

**Próximo ao clipe**

O plano de clipe próximo é o mais próximo, em metros, que um objeto virtual pode ser da câmera e ainda ser renderizado. Para maior conforto do usuário, é recomendável tornar esse valor maior que zero. A imagem anterior contém valores que foram considerados confortável em uma variedade de dispositivos.

**Clipe distante**

O plano de clipe distante é o mais distante, em metros, que um objeto virtual pode ser para a câmera e ainda ser renderizado. Para dispositivos transparentes, é recomendável que esse valor seja relativamente próximo para não exceder muito o espaço do mundo real e quebrar as qualidades imersivas do aplicativo.

**Limpar sinalizadores**

O valor de sinalizadores claros indica como a exibição é limpa conforme ela é desenhada. Para experiências de realidade virtual, esse valor geralmente é definido como Skybox. Para exibições transparentes, é recomendável definir isso como Cor.

**Cor da tela de fundo**

Se os sinalizadores não definidos como Skybox, a propriedade de cor da tela de fundo será exibida.

**Configurações de Qualidade**

O valor de configurações de qualidade indica a qualidade dos gráficos que o Unity deve usar ao renderizar a cena. O nível de qualidade é uma configuração de nível de projeto e não é específico para nenhuma câmera. Para obter mais informações, consulte o [artigo Qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html) na documentação do Unity.

## <a name="see-also"></a>Confira também

- [Documentação da API do Sistema de Câmera](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Criando um provedor de Configurações câmera](create-settings-provider.md)
