---
title: Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para HoloLens
description: HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para HoloLens ajudar a criar experiências de holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, esboço, aplicativo
ms.openlocfilehash: 24929d38f97a3c02946a28184d7702c151dc22b2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757318"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para HoloLens

HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para HoloLens ajudar a criar experiências de holographic. o HoloSketch funciona com um teclado e mouse emparelhados Bluetooth, bem como comandos de voz e de gestos. A finalidade do HoloSketch é fornecer uma ferramenta de layout de UX simples para visualização e iteração rápidas.

![HoloSketch: um layout espacial e um aplicativo de esboço de UX para HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout espacial e aplicativo de esboço de UX para HoloLens*

![Uma ferramenta de layout de UX simples para visualização e iteração rápidas.](images/holosketch-image-02.png)<br>
*Uma ferramenta de layout de UX simples para visualização e iteração rápidas*

## <a name="features"></a>Recursos

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivos para estudos rápidos e criação de protótipos de escala

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para estudos rápidos de massa e criação de protótipos de escala.

### <a name="import-objects-through-onedrive"></a>Importar objetos por meio de OneDrive

![importando objetos](images/holosketch-importobjects-giphy.gif)

Importe imagens PNG/JPG ou objetos FBX 3D (requer empacotamento no Unity) no espaço da realidade misturada por meio de OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipulando objetos](images/manipulate-objects-640px.jpg)

Manipule objetos (move/gira/dimensionamento) com uma interface de objeto 3D familiar.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/teclado, gestos e comandos de voz

![dá suporte a Bluetooth](images/supports-bluetooth-640px.jpg)

o HoloSketch dá suporte a Bluetooth mouse/teclado, gestos e comandos de voz.

## <a name="background"></a>Segundo plano

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importância de experimentar seu design no dispositivo

quando você cria algo para HoloLens, é importante experimentar o design no dispositivo. Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil obter o sentido de escala, posição e profundidade, especialmente por meio de esboços 2D tradicionais.

### <a name="cost-of-2d-based-communication"></a>Custo da comunicação baseada em 2D

Para comunicar efetivamente fluxos e cenários de UX a outros, um designer pode acabar gastando muito tempo criando ativos usando ferramentas 2D tradicionais, como o Illustrator, o Photoshop e o PowerPoint. Esses designs 2D geralmente exigem um esforço adicional para convertê-los em 3D. Algumas ideias são perdidas nessa tradução de 2D para 3D.

### <a name="complex-deployment-process"></a>Processo de implantação complexo

Como a realidade misturada é uma nova tela para nós, ela envolve muita iteração de design e avaliação e erro por sua natureza. para o designer que não estão familiarizados com ferramentas como Unity e Visual Studio, não é fácil colocar algo junto em HoloLens. Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo. Essa era uma grande barreira para os designers Iterando rapidamente em ideias e cenários.

![Processo de implantação complexo](images/holosketch-image-03-1000px.png)<br>
*Processo de implantação*

### <a name="simplified-process-with-holosketch"></a>Processo simplificado com o HoloSketch

Com o HoloSketch, queríamos simplificar esse processo sem envolver as ferramentas de desenvolvimento e o emparelhamento do portal do dispositivo. usando OneDrive, os usuários podem facilmente colocar ativos 2d/3d em HoloLens.

![Processo simplificado com o HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo simplificado com o HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incentivando a reflexão e as soluções de design tridimensionais

Achamos que essa ferramenta daria aos designers uma oportunidade de explorar soluções em um espaço verdadeiramente tridimensional e que não estaria presa em 2D. Eles não precisam pensar em criar um plano de fundo 3D para sua interface do usuário, pois o plano de fundo é o mundo real no caso de HoloLens. O HoloSketch abre uma maneira de os designers explorarem facilmente o design 3D em HoloLens.

## <a name="get-started"></a>Introdução

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Como importar imagens 2D (JPG/PNG) para o HoloSketch

* Upload imagens JPG/PNG para a pasta OneDrive ' documents/HoloSketch '.
* no menu OneDrive no HoloSketch, você poderá selecionar e posicionar a imagem no ambiente.

![Importando imagens 2D](images/import-2d-images-1000px.jpg)<br>
*Importando imagens e objetos 3D por meio de OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Como importar objetos 3D para o HoloSketch

antes de carregar em sua pasta OneDrive, siga as etapas abaixo para empacotar seus objetos 3d em um pacote de ativos do Unity. Usando esse processo, você pode importar seus Arquivos FBX/OBJ de software 3D, como Maya, cinema 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Atualmente, a criação do pacote de ativos tem suporte com o Unity versão 5.4.5 F1.

1. Baixe e abra o projeto do Unity [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Esse projeto de Unity inclui o script para a geração de ativos do pacote.
2. Crie um novo gameobject.
3. Nomeie o gameobject com base no conteúdo.
4. No painel Inspetor, clique em "Adicionar componente" e adicione "cocolisorr". 

   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa" #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe o arquivo 3D FBX arrastando-o para o painel projeto.
6. Arraste o objeto para o painel hierarquia **em seu novo gameobject**.

   ![Arraste o objeto para o painel hierarquia em seu novo gameobject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste a dimensão do colisor se ele não corresponder ao objeto. Gire o objeto para a face do **eixo Z**.

   ![Ajuste a dimensão do colisor se ele não corresponder ao objeto.](images/holosketch-13-assetbundles-1000px.png)

8. arraste o objeto do painel hierarquia para o painel de Project para **torná-lo pré-fabricado**.
9. Na parte inferior do painel Inspetor, clique no menu suspenso, crie e atribua um novo nome exclusivo. O exemplo abaixo mostra como adicionar e atribuir ' brownchair ' para o nome do AssetBundle. 

   ![Na parte inferior do painel Inspetor, clique na lista suspensa e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. Prepare uma imagem em miniatura para o objeto de modelo. 
   ![Arraste uma imagem para o painel projeto e atribua o nome usado para o objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Crie uma pasta chamada ' Assetbundles ' na pasta ' Asset ' do projeto de Unity.

12. No menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo. 
   ![No menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)


13. **Upload o arquivo gerado para a pasta/Files/Documents/HoloSketch em OneDrive.** Upload somente o arquivo de asset_unique_name. Você não precisa carregar arquivos de manifesto ou arquivo AssetBundles. <br>
![adicionar arquivos a arquivos/documentos/HoloSketch/pasta ](images/holosketch-onedriveupload-1000px.png)
 ![ você verá o objeto 3d adicionado no menu de OneDrive do HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Como manipular os objetos

O HoloSketch dá suporte à interface tradicional que é amplamente usada em software 3D. Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse. Você pode alternar rapidamente entre modos diferentes com voz ou teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulação de objeto

![Como manipular os objetos](images/holosketch-image-06-1000px.png)<br>
*Como manipular os objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menus contextuais e da correia de ferramenta

**Usando o menu contextual**

Toque de ar duplo para abrir o menu contextual. 

Itens de menu:
* **Superfície de layout:** Esse é um sistema de grade 3D no qual você pode fazer o layout de vários objetos e gerenciá-los como um grupo. Air de toque duplo na superfície de layout para adicionar objetos a ele.
* **Primitivos:** Use cubos, por meio de cilindros e cones para estudos em massa.
* **Onedrive:** abra o menu OneDrive para importar objetos.
* **Ajuda:** Exibe a tela de ajuda.

![Menu contextual](images/holosketch-image-07.png)<br>
*Menu contextual*

**Usando o menu faixa de ferramentas**

Move, Rotate, Scale, Save e Load Scene estão disponíveis no menu Faixa de Ferramentas. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usando comandos de teclado, gestos e voz

![Comandos de teclado, gestos e voz](images/holosketch-image-08-1000px.png)<br>
*Comandos de teclado, gestos e voz*

## <a name="download-the-app"></a>Baixar o aplicativo

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Baixe e instale o aplicativo HoloSketch gratuitamente no Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos
* Atualmente, há suporte para a criação do pacote de ativos com **o Unity versão 5.4.5f1.**
* Dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se ele tivesse parado durante o carregamento OneDrive conteúdo
* Atualmente, o recurso Salvar e Carregar dá suporte apenas a objetos primitivos
* Os menus Texto, Som, Vídeo e Foto estão desabilitados no menu contextual
* O botão Reproduzir no menu Faixa de Ferramentas limpa as ferramentas de manipulação

## <a name="sharing-your-sketches"></a>Compartilhando seus esboços

Você pode usar o recurso de gravação de vídeo HoloLens dizendo "Hey Cortana, Start/Stop recording". Pressione a tecla para cima/para baixo do volume para tirar uma foto do esboço.

## <a name="about-the-authors"></a>Sobre os autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Designer de UX @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Desenvolvedor @Microsoft</td>
</tr>
</table> 