---
title: Como atualizar projetos no Unreal
description: Fique atualizado com as etapas de atualização de versão, alterações de API e substituições para seus projetos do Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010046"
---
# <a name="upgrading-projects-in-unreal"></a>Como atualizar projetos no Unreal

Quando você fizer a atualização para uma nova versão do Unreal, as funções preteridas serão exibidas como avisos durante o build de blueprints ou o empacotamento do projeto.  As funções são preteridas quando uma nova função é adicionada e deve ser usada no lugar delas. 

## <a name="426-upgrades"></a>Atualizações da versão 4.26
 
Na versão 4.26, todas as plataformas de RA e VR foram refatoradas para adicionar interfaces comuns e manter o código de aplicativo independente de plataforma, de modo que você possa ver mais avisos do que o normal.  A atualização para as novas APIs é recomendada, de modo que o projeto possa ser portado com facilidade para outras plataformas.

As mensagens de aviso mostrarão a função preterida e indicarão a função que deverá ser usada no lugar dela.  Todas as funções preteridas continuarão funcionando nesta versão, mas podem não funcionar em versões futuras.  As funções preteridas também deixarão de ser listadas durante a pesquisa de funções em um blueprint.

![Blueprint da função Criar ARPin Nomeado](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Substituições da versão 4.25

| Função preterida | Nova função |
| --- | --- |
| CreateNamedARPin | ![Blueprint da função Fixar Componente](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Blueprint da função Carregar ARPins do Repositório Local](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Blueprint da função Salvar ARPin no Repositório Local](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Blueprint da função Remover ARPin do Armazenamento Local](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Blueprint da função Definir XRCamera Habilitada](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Blueprint da função Redimensionar XRCamera](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Blueprint da função Alternar ARCapture para iniciar a captura da câmera](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Blueprint da função Alternar ARCapture para interromper a captura da câmera](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Blueprint da função Alternar ARCapture para iniciar a captura do código QR](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Blueprint da função Alternar ARCapture para interromper a captura do código QR](images/unreal-porting-img-11.png) |
| Antes, na versão 4.25, o mapeamento espacial era iniciado automaticamente, mas agora, na versão 4.26, precisa ser alternado. | ![Blueprint da função Alternar ARCapture para habilitar o mapeamento espacial](images/unreal-porting-img-12.png) |
| ShowKeyboard | Removida da versão 4.26, pois o teclado é exibido automaticamente quando o foco está em um widget de texto. |
| HideKeyboard | Removida da versão 4.26, pois o teclado é ocultado automaticamente quando o foco não está em um widget de texto. |
| SupportsHandTracking | ![Blueprint da propriedade Suporte ao Acompanhamento da Mão](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Blueprint da propriedade IsDisplayOpaque](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Blueprint da função Obter Dados do Controlador de Movimentos](images/unreal-porting-img-15.png) |
| GetVersionString | ![Blueprint da função Obter Cadeia de Caracteres da Versão](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Blueprint da propriedade IsTrackingAvailable](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Use o sistema de ações de entrada do Unreal. |
| SetFocusPointForFrame | Removida da versão 4.26.  Anteriormente usado para reprojeção na comunicação remota, que agora dá suporte à reprojeção de profundidade. |

## <a name="426-changes"></a>Alterações na versão 4.26

A alteração significativa é que **Iniciar em VR** em **Editar > Configurações do Projeto > Projeto > Descrição > Configurações** é obrigatório para iniciar o plug-in do Windows Mixed Reality. Sem esse parâmetro, você não vê os hologramas no dispositivo.
