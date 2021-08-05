---
title: Habilitar posicionamento de modelos 3D na página inicial
description: Saiba como colocar modelos 3D do seu site ou aplicativo na Windows Mixed Reality página inicial.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, colocação em casa, lugar, mundo, modelagem, home de realidade misturada, Web, aplicativo, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186792"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Habilitar o posicionamento de modelos 3D na página inicial da realidade misturada

> [!NOTE]
> Esse recurso foi adicionado como parte do Windows 10 [de abril de 2018.](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) Versões mais antigas Windows não são compatíveis com esse recurso.

A [Windows Mixed Reality início é](../discover/navigating-the-windows-mixed-reality-home.md) o ponto de partida em que os usuários são lançados antes de iniciar aplicativos. Em alguns cenários, aplicativos 2D (como o aplicativo Hologramas) permitem o posicionamento de modelos 3D diretamente na casa da realidade misturada como decorações ou para inspeção posterior em 3D completo. O protocolo add *model* permite que você envie um modelo 3D do seu site ou aplicativo diretamente para a página inicial do Windows Mixed Reality, em que ele persistirá como os iniciadores de aplicativo [3D,](3d-app-launcher-design-guidance.md)aplicativos 2D e hologramas. 

Por exemplo, se você estiver desenvolvendo um aplicativo que revela um catálogo de  móveis 3D para criar um espaço, use o protocolo adicionar modelo para permitir que os usuários coloquem esses modelos de móveis 3D do catálogo. Depois de colocados no mundo, os usuários podem mover, reize e remover esses modelos 3D, assim como outros hologramas na casa. Este artigo fornece uma visão geral da implementação do protocolo *add model* para permitir que os usuários decorem seu mundo com objetos 3D do seu aplicativo ou da Web.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Adicionar protocolo de modelo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Noções básicas

Há duas etapas para habilenciar o posicionamento de modelos 3D no Windows Mixed Reality home:
1. [Verifique se o modelo 3D é compatível com o Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implemente *o protocolo add model* em seu aplicativo ou página da Web (este artigo).

## <a name="implementing-the-add-model-protocol"></a>Implementando o *protocolo add model*

Depois de ter um modelo [3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)compatível, você poderá implementar o protocolo add *model* ativando o seguinte URI de qualquer página da Web ou aplicativo:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se o URI aponta para um recurso remoto, ele será baixado e colocado automaticamente na casa. Os recursos locais serão copiados para a pasta de dados do aplicativo da página de realidade misturada antes de serem colocados na página base. É recomendável projetar sua experiência para levar em conta cenários em que o usuário pode estar executando uma versão mais antiga do Windows que não dá suporte a esse recurso ocultando o botão ou desabilitando-o, se possível. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocando o protocolo *add model de* um aplicativo plataforma Windows Universal:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocando o protocolo *add model de* uma página da Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerações para headsets imersivos (VR)

* Para headsets imersivos (VR), o Portal de Realidade Misturada não precisa estar em execução antes de invocar o *protocolo add model*. Nesse caso, o *protocolo add model* iniciará o Portal de Realidade Misturada e colocará o objeto diretamente no local em que o headset está procurando quando você chegar à casa da realidade misturada. 
* Ao invocar o protocolo *add model da* área de trabalho com o Portal de Realidade Misturada já em execução, verifique se o headset está "acionado". Caso não seja, o posicionamento não terá êxito. 

## <a name="see-also"></a>Consulte também

* [Criando modelos 3D para uso no Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Como navegar na página inicial do Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)