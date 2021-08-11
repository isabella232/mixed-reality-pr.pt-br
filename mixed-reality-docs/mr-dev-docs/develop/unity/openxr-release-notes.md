---
title: Notas de versão do plug-in OpenXR de Realidade Misturada
description: Fique por dentro das últimas notas de versão e atualizações do plug-in OpenXR de Realidade Misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 568d5f25eceed385a1331cd2cf5fe6e3adb6f8228e85d6d2d316749fc2ee431c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187617"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Notas de versão do plug-in OpenXR de Realidade Misturada

## <a name="100---current-release"></a>1.0.0 - Versão atual

* Correção de um bug em que um XRAnchorSubsystem sempre foi iniciado na inicialização do aplicativo, independentemente do ARAnchorManager presente.
* Um bug onde o modo de reprojeção não funcionou corretamente foi corrigido.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 - 2021-06-14

* Depende do plug-in OpenXR 1.2.2 do Unity.
* Os recursos de Comunicação Remota Holográfica foram alterados para grupos de recursos individuais.
* Um bug onde "Aplicar configurações de projeto do HoloLens 2" altera o espaço de cores do projeto foi corrigido. Isso não é mais necessário após o plug-in 1.2.0 OpenXR do Unity.
* Um bug onde um dispositivo de entrada é conectado sem desconectar após o aplicativo ser suspenso e retomado foi corrigido.
* Suporte adicionado para detectar plug-in e estados de acompanhamento atuais via ARSession.
* Um bug onde o "Plano Padrão AR" ARFoundation pré-fabricado não estaria visível foi corrigido.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 - 2021-06-02

* Dá suporte a extensões MSFT de reconhecimento de cena do OpenXR em vez de extensões de visualização.
* A detecção de plano no HoloLens 2 não requer mais versões prévias dos tempos de execução OpenXR de Realidade Misturada.

## <a name="095---2021-05-21"></a>0.9.5 - 2021-05-21

* Depende do Plug-in OpenXR 1.2.0 do Unity
* Adaptado para a nova interface do usuário do recurso (no Plug-in 1.2.0 do OpenXR) para configuração.
* Um bug onde o provedor da câmera localizável não estava cancelando o registro corretamente foi corrigido.
* Alguns usos extras de [Preserve] foram limpos.
* Atualize o nome "HP Reverb G2 Controller (OpenXR)" na interface do usuário do sistema de entrada.

## <a name="094---2021-05-20"></a>0.9.4 - 2021-05-20

* Depende do Plug-in OpenXR 1.2.0 do Unity.
* Uma API do C# nova foi adicionada para obter o modelo de glTF do controlador de movimentos.
* Uma API do C# nova foi adicionada para obter as configurações de exibição habilitadas e definir as configurações de reprojeção.
* Uma API do C# nova foi adicionada para definir configurações adicionais para malhas de computação com XRMeshSubsystem.
* Uma API do C# nova foi adicionada para configurar e assinar eventos de reconhecimento de gestos.
* Windows->XR->Diálogo das configurações de Comunicação Remota do Editor adicionado.
* Suporte adicionado à ARM para aplicativos HoloLens UWP.

## <a name="093---2021-04-29"></a>0.9.3 - 2021-04-29

* Um bug onde a conexão remota Holographic não é confiável foi corrigido
* Um bug onde o desempenho de renderização VR está abaixo do ideal após a atualização para o plug-in OpenXR 1.1.1 do Unity foi corrigido.

## <a name="092---2021-04-21"></a>0.9.2 - 2021-04-21

* A detecção de plano no HoloLens 2 na versão 0.9.1 do plug-in funcionará com a versão 105 do tempo de execução da verão prévia do OpenXR de Realidade Misturada.
* A detecção de plano no HoloLens 2 na versão 0.9.2 do plug-in funcionará com a versão 106 do tempo de execução da verão prévia do OpenXR de Realidade Misturada.
* Foram removidos alguns retornos de chamada não utilizados do Inputprovider para evitar que chamadas como XRInputSubsystem.* GetTrackingOriginMode (que não são gerenciadas pelo nosso sistema de entrada) retornem com êxito com valores enganosos.
* Divida a versão preterida do XRAnchorStore em seu próprio arquivo para impedir o aviso do console do Unity.

## <a name="091---2021-04-20"></a>0.9.1 - 2021-04-20

* Depende do Plug-in OpenXR 1.1.1 do Unity.
* Suporte adicionado ao aplicativo de Comunicação Remota Holográfica para a plataforma UWP.
* Corrija a UnityException onde XRAnchorStore estava tentando obter uma instância de configurações fora da thread principal.

## <a name="090---2021-03-29"></a>0.9.0 - 2021-03-29

* Suporte adicionado ao mapeamento espacial por meio do XRMeshSubsystem e ARMeshManager.
* Uma API do C# nova foi adicionada para obter identificadores de OpenXR para dar suporte a outros pacotes do Unity que consomem extensões OpenXR.
* Uma API do C# nova foi adicionada à interoperabilidade com Windows. APIs de Percepção para dar suporte a outros pacotes do Unity consumindo APIs WinRT de Percepção.
* Perfis de interação removidos dos recursos necessários no conjunto de recursos do Windows Mixed Reality, para que os desenvolvedores possam escolher os controladores de movimento com os quais eles testaram.
* Validador de recursos de comunicação remota do editor do Holographic adicionado para ajudar os usuários a configurar corretamente a comunicação remota do editor.
* Um bug onde o editor do Unity falha ao sair do modo de comunicação remota do editor de Holographic após a falha de conexão foi corrigido.
* Um bug onde texturas alfa não pré-multiplicadas levam a um desempenho abaixo do ideal no HoloLens 2 foi corrigido.
* Um bug onde o acompanhamento da mão não estava localizado corretamente quando a origem da cena estava no nível do chão foi corrigido.
* Um bug onde o acompanhamento de malha à mão desaparece após sair e carregar uma nova cena foi corrigido.
* Um bug onde o provedor de câmera localizável não foi limpo corretamente foi corrigido.
* Namespace da API XRAnchorStore revisado para Microsoft.MixedReality.OpenXR.