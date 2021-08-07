---
title: Estudo de caso – Criando HoloSketch, um layout espacial e um aplicativo de esboço de experiência do HoloLens
description: O HoloSketch é um layout espacial no dispositivo e uma ferramenta de esboço de experiência do usuário para HoloLens ajudar a criar experiências holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, esboço, aplicativo
ms.openlocfilehash: 614572c91067399cc0235ef2570543aa81e2c24ab36a7b9e9bfa03b77e452420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213780"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Estudo de caso – Criando HoloSketch, um layout espacial e um aplicativo de esboço de experiência do HoloLens

O HoloSketch é um layout espacial no dispositivo e uma ferramenta de esboço de experiência do usuário para HoloLens ajudar a criar experiências holográficas. O HoloSketch funciona com um teclado Bluetooth e mouse emparelhados, bem como comandos de gesto e voz. A finalidade do HoloSketch é fornecer uma ferramenta de layout de UX simples para visualização rápida e iteração.

![HoloSketch: um layout espacial e um aplicativo de esboço de experiência do HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout espacial e aplicativo de esboço de experiência do HoloLens*

![Uma ferramenta de layout de UX simples para visualização rápida e iteração.](images/holosketch-image-02.png)<br>
*Uma ferramenta de layout de UX simples para visualização rápida e iteração*

## <a name="features"></a>Recursos

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivos para estudos rápidos e criação de protótipos de escala

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para estudos de massa rápida e criação de protótipos de escala.

### <a name="import-objects-through-onedrive"></a>Importar objetos por meio OneDrive

![importando objetos](images/holosketch-importobjects-giphy.gif)

Importe imagens PNG/JPG ou objetos FBX 3D (requer empacotamento no Unity) para o espaço de realidade misturada por meio de OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipulando objetos](images/manipulate-objects-640px.jpg)

Manipular objetos (mover/girar/dimensionar) com uma interface de objeto 3D conhecida.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/teclado, gestos e comandos de voz

![dá suporte Bluetooth](images/supports-bluetooth-640px.jpg)

O HoloSketch dá suporte Bluetooth comandos de mouse/teclado, gestos e voz.

## <a name="background"></a>Tela de fundo

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importância de experimentar seu design no dispositivo

Quando você projeta algo para HoloLens, é importante experimentar seu design no dispositivo. Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil obter a noção de escala, posição e profundidade, especialmente por meio de esboços 2D tradicionais.

### <a name="cost-of-2d-based-communication"></a>Custo da comunicação baseada em 2D

Para comunicar efetivamente fluxos e cenários de UX a outras pessoas, um designer pode acabar gastando muito tempo criando ativos usando ferramentas 2D tradicionais, como o Illustrator, o PowerPoint. Esses designs 2D geralmente exigem esforço adicional para convertê-los em 3D. Algumas ideias são perdidas nessa tradução de 2D para 3D.

### <a name="complex-deployment-process"></a>Processo de implantação complexo

Como a realidade misturada é uma nova tela para nós, ela envolve muita iteração de design, avaliação e erro por sua natureza. Para designers que não estão familiarizados com ferramentas como o Unity e Visual Studio, não é fácil reunir algo no HoloLens. Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo. Essa era uma grande barreira para designers iterando em ideias e cenários rapidamente.

![Processo de implantação complexo](images/holosketch-image-03-1000px.png)<br>
*Processo de implantação*

### <a name="simplified-process-with-holosketch"></a>Processo simplificado com HoloSketch

Com o HoloSketch, queríamos simplificar esse processo sem envolver ferramentas de desenvolvimento e emparelhamento do portal de dispositivos. Usando OneDrive, os usuários podem facilmente colocar ativos 2D/3D em HoloLens.

![Processo simplificado com HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo simplificado com HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incentivando soluções e raciocínio de design tridimensional

Acreditamos que essa ferramenta dará aos designers a oportunidade de explorar soluções em um espaço realmente tridimensional e não ficar presa em 2D. Eles não precisam pensar em criar um plano de fundo 3D para a interface do usuário, pois o plano de fundo é o mundo real no caso de HoloLens. O HoloSketch abre uma maneira para os designers explorarem facilmente o design 3D em HoloLens.

## <a name="get-started"></a>Começar agora

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Como importar imagens 2D (JPG/PNG) para o HoloSketch

* Upload Imagens JPG/PNG para sua pasta OneDrive "Documentos/HoloSketch".
* No menu OneDrive no HoloSketch, você poderá selecionar e colocar a imagem no ambiente.

![Importando imagens 2D](images/import-2d-images-1000px.jpg)<br>
*Importando imagens e objetos 3D por meio OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Como importar objetos 3D para o HoloSketch

Antes de carregar em sua pasta OneDrive, siga as etapas abaixo para empacotar seus objetos 3D em um pacote de ativos do Unity. Usando esse processo, você pode importar seus arquivos FBX/OBJ de software 3D, como Maya, 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Atualmente, há suporte para a criação do pacote de ativos com o Unity versão 5.4.5f1.

1. Baixe e abra o projeto do Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Este projeto do Unity inclui o script para a geração de ativos do pacote.
2. Crie um novo GameObject.
3. Nomeia o GameObject com base no conteúdo.
4. No painel Inspetor, clique em 'Adicionar Componente' e adicione 'Colisor de Caixa'. 

   ![No painel Inspetor, clique em 'Adicionar Componente' e adicione 'Colisor de Caixa'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel Inspetor, clique em 'Adicionar Componente' e adicione 'Colisor de Caixa' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe o arquivo FBX 3D arrastando-o para o painel do projeto.
6. Arraste o objeto para o painel Hierarquia **sob o novo GameObject.**

   ![Arraste o objeto para o painel Hierarquia sob o novo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste a dimensão do colisor se ela não corresponder ao objeto . Gire o objeto para o eixo **Z de face**.

   ![Ajuste a dimensão do colisor se ela não corresponder ao objeto .](images/holosketch-13-assetbundles-1000px.png)

8. Arraste o objeto do painel Hierarquia para o painel Project para **torná-lo pré-fab**.
9. Na parte inferior do painel do inspetor, clique no menu suspenso, crie e atribua um novo nome exclusivo. O exemplo abaixo mostra como adicionar e atribuir 'brownchair' ao Nome assetBundle. 

   ![Na parte inferior do painel do inspetor, clique no menu suspenso e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. Prepare uma imagem em miniatura para o objeto de modelo. 
   ![Arraste uma imagem para o painel do projeto e atribua o nome usado para o objeto .](images/holosketch-15-assetbundles-1000px.png)

11. Crie uma pasta chamada 'Assetbundles' na pasta 'Asset' do projeto do Unity.

12. No menu Ativos, selecione 'Criar AssetBundles' para gerar o arquivo. 
   ![No menu Ativos, selecione 'Criar AssetBundles' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)


13. **Upload o arquivo gerado para a pasta /Files/Documents/HoloSketch no OneDrive.** Upload o arquivo asset_unique_name somente. Você não precisa carregar arquivos de manifesto ou arquivo AssetBundles. <br>
![Adicionar arquivos à pasta Files/Documents/HoloSketch/ Você verá o objeto 3D adicionado no menu de OneDrive ](images/holosketch-onedriveupload-1000px.png)
 ![ holoSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Como manipular os objetos

O HoloSketch dá suporte à interface tradicional amplamente usada em software 3D. Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse. Você pode alternar rapidamente entre diferentes modos com voz ou teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulação de objeto

![Como manipular os objetos](images/holosketch-image-06-1000px.png)<br>
*Como manipular os objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menus contextuais e de faixa de ferramentas

**Usando o menu contextual**

Toque duplo no ar para abrir o Menu Contextual. 

Itens de menu:
* **Superfície de layout:** Esse é um sistema de grade 3D em que você pode layout de vários objetos e gerenciá-los como um grupo. Toque de ar duplo na Superfície de Layout para adicionar objetos a ela.
* **Primitivos:** Use cubos, esferas, cilindros e casquinhas para estudos de massa.
* **OneDrive:** Abra o menu OneDrive para importar objetos.
* **Ajuda:** Exibe a tela de ajuda.

![Menu contextual](images/holosketch-image-07.png)<br>
*Menu contextual*

**Usando o menu da correia de ferramentas**

Mover, girar, dimensionar, salvar e carregar a cena está disponível no menu da correia de ferramentas. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usando teclado, gestos e comandos de voz

![Teclado, gestos e comandos de voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos e comandos de voz*

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
* Atualmente, há suporte para a criação do pacote de ativos com o **Unity versão 5.4.5 F1.**
* dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se tiver parado durante o carregamento de OneDrive conteúdo
* Atualmente, o recurso salvar e carregar só dá suporte a objetos primitivos
* Os menus de texto, som, vídeo e foto estão desabilitados no menu contextual
* O botão reproduzir no menu da correia de ferramenta limpa o utensílios de manipulação

## <a name="sharing-your-sketches"></a>Compartilhando seus esboços

você pode usar o recurso de gravação de vídeo no HoloLens dizendo ' ei Cortana, iniciar/parar gravação '. Pressione a tecla volume para cima/para baixo para tirar uma foto do seu esboço.

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