---
title: HoloLens (1ª geração) e Azure 303 – LUIS (Natural Language Understanding)
description: Conclua este curso para aprender a implementar o LUIS (Serviço de Inteligência Reconhecimento vocal Azure) em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade misturada, academy, unity, tutorial, API, serviço de inteligência de compreensão de linguagem, luis, hololens, imersivo, vr, Windows 10, Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217942"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (1ª geração) e Azure 303: LUIS (Natural Language Understanding)

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

<br>

Neste curso, você aprenderá a integrar o Reconhecimento vocal a um aplicativo de realidade misturada usando Serviços Cognitivos do Azure, com a API Reconhecimento vocal.

![Resultado do laboratório](images/AzureLabs-Lab3-000.png)

*Reconhecimento vocal (LUIS)* é um serviço Microsoft Azure, que fornece aos aplicativos a capacidade de fazer significado com a entrada do usuário, como por meio da extração do que uma pessoa pode querer, em suas próprias palavras. Isso é feito por meio do aprendizado de máquina, que compreende e aprende as informações de entrada e, em seguida, pode responder com informações detalhadas, relevantes. Para obter mais informações, visite [a página do LUIS (Azure Reconhecimento vocal).](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)

Depois de concluir este curso, você terá um aplicativo de headset imersivo de realidade misturada que poderá fazer o seguinte:

1.  Capture a fala de entrada do usuário usando o Microfone anexado ao headset imersivo. 
2.  Envie o ditado capturado para o LUIS (ServiçoInteligente Reconhecimento vocal *Azure).* 
3.  Fazer com que o LUIS extraia o significado das informações de envio, que serão analisadas, e tente determinar a intenção da solicitação do usuário.

O desenvolvimento incluirá a criação de um aplicativo em que o usuário poderá usar voz e/ou olhar para alterar o tamanho e a cor dos objetos na cena. O uso de controladores de movimento não será abordado.

Em seu aplicativo, você deve saber como integrar os resultados ao seu design. Este curso foi projetado para ensinar como integrar um Serviço do Azure ao seu Project Unity. É seu trabalho usar o conhecimento que você ganha com este curso para aprimorar seu aplicativo de realidade misturada.

Esteja preparado para treinar o LUIS várias vezes, o que é abordado [no Capítulo 12.](#chapter-12--improving-your-luis-service) Você obterá melhores resultados quanto mais vezes o LUIS tiver sido treinado.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>MR e Azure 303: LUIS (Natural Language Understanding)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente Windows Mixed Reality headsets imersivos (VR), você também pode aplicar o que aprende neste curso para Microsoft HoloLens. Conforme você acompanha o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a HoloLens. Ao usar HoloLens, você pode observar algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com Unity e C#. Lembre-se também de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da redação (maio de 2018). Você é livre para usar o software [](../../install-the-tools.md) mais recente, conforme listado no artigo Instalar as ferramentas, embora não seja preciso assumir que as informações neste curso corresponderão perfeitamente ao que você encontrará em software mais recente do que o listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um pc de desenvolvimento [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headset imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md)
- [O SDK Windows 10 mais recente](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Um [headset Windows Mixed Reality imersivo (VR)](../../../discover/immersive-headset-hardware-details.md) ou um Microsoft HoloLens [com](/hololens/hololens1-hardware) o modo desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um microfone interno e alto-falantes)
- Acesso à Internet para instalação do Azure e recuperação do LUIS

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas ao criar este projeto, é fortemente sugerido que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas no tempo de build). 
2.  Para permitir que seu computador habilita o Ditado, acesse Windows Configurações > Privacidade > **Fala, Inking & Digitando** e pressione o botão Ativar serviços de fala e digitar sugestões **.**
3.  O código neste tutorial permitirá que você grave do Dispositivo de **Microfone** Padrão definido em seu computador. Certifique-se de que o Dispositivo de Microfone Padrão está definido como aquele que você deseja usar para capturar sua voz.
4.  Se o headset tiver um microfone interno, certifique-se de que a opção *"Quando* eu usar meu headset, alternar para o microfone do headset" está 1000% Portal de Realidade Misturada *configurações.*

    ![Configurando o headset imersivo](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1 – Configurar o Portal do Azure

Para usar *o Reconhecimento vocal* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Faça logoff no [Portal do Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, precisará criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ajuda ao instrutor ou a um dos proctors para configurar sua nova conta.

2.  Quando você está conectado,  clique em Novo no canto superior esquerdo e pesquise por Reconhecimento vocal *e* clique em **Inserir**. 

    ![Criar recurso LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > A palavra **Novo** pode ter sido substituída por **Criar um recurso**, em portais mais novos.
 
3.  A nova página à direita fornecerá uma descrição do Reconhecimento vocal serviço. Na parte inferior esquerda desta página, selecione o **botão** Criar para criar uma instância desse serviço.

    ![Criação do serviço LUIS – aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Depois de clicar em Criar:

    1. Insira o Nome desejado **para** essa instância de serviço.
    2. Selecione uma **Assinatura**.
    3. Selecione o **Tipo de** Preço apropriado para você, se esta for a primeira vez que você cria um Serviço *LUIS,* uma camada gratuita (chamada F0) deve estar disponível para você. A alocação gratuita deve ser mais do que suficiente para este curso.
    4. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comum. 

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, [visite o artigo do grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Determine o **Local** do grupo de recursos (se você estiver criando um novo Grupo de Recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.
    6. Você também precisará confirmar que entendeu os Termos e Condições aplicados a esse Serviço.
    7. Selecione **Criar**.

        ![Criar serviço LUIS – entrada do usuário](images/AzureLabs-Lab3-03.png)
 
5.  Depois de clicar em **Criar**, você terá que aguardar até que o serviço seja criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal depois que a instância de serviço for criada. 
 
    ![Nova imagem de notificação do Azure](images/AzureLabs-Lab3-04.png)

7.  Clique na notificação para explorar sua nova instância de serviço.

    ![Notificação de criação de recursos bem-sucedida](images/AzureLabs-Lab3-05.png)
 
8.  Clique no **botão Ir para o** recurso na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço do LUIS. 
 
    ![Acessando chaves do LUIS](images/AzureLabs-Lab3-06.png)

9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito usando a Chave de Assinatura do serviço.
10. Na  página Início rápido, do serviço de *API do LUIS,* navegue até a primeira *etapa,* Pegue suas chaves e clique em Chaves **(você** também pode fazer isso clicando nas Teclas de hiperlink azul, localizadas no menu de navegação de serviços, anotadas pelo ícone de chave). Isso revelará suas chaves *de serviço.*
11. Fazer uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 
12. Na página *Serviço,* clique em *Reconhecimento vocal Portal* para ser redirecionado para a página da Web que você usará para criar seu novo Serviço, dentro do Aplicativo LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2 – O portal Reconhecimento vocal dados

Nesta seção, você aprenderá a fazer um aplicativo LUIS no Portal do LUIS. 

> [!IMPORTANT]
> Lembre-se de que a configuração de *Entidades,* Intenções e *Enunciados* neste capítulo é apenas a primeira etapa na criação do serviço LUIS: você também precisará treinar o serviço, várias vezes, para torná-lo mais preciso. O novo treinamento do serviço é abordado [no último Capítulo](#chapter-12--improving-your-luis-service) deste curso, portanto, certifique-se de que você o conclua.

1.  Ao acessar o *portal Reconhecimento vocal*, talvez seja necessário fazer logon, se ainda não estiver, com as mesmas credenciais que seu portal do Azure. 

    ![Página de logon do LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas para encontrar e clicar no botão Criar **aplicativo LUIS.**

    ![Página Criar aplicativo LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Depois de conectado, clique **Meus aplicativos** (se você não estiver nessa seção no momento). Em seguida, você pode clicar **em Criar novo aplicativo.**

    ![LUIS – imagem de meus aplicativos](images/AzureLabs-Lab3-09.png)
 
4.  Dê um Nome ao *seu aplicativo.*
5.  Se o aplicativo deve entender um idioma diferente do inglês, você deve alterar a *Cultura* para o idioma apropriado.
6.  Aqui você também pode adicionar uma *Descrição* do novo aplicativo LUIS.

    ![LUIS – criar um novo aplicativo](images/AzureLabs-Lab3-10.png)

7.  Depois de pressionar **Done**, você entrará na página *Build* do novo *aplicativo LUIS.*
8.  Há alguns conceitos importantes a entender aqui:

    -   *Intent*, representa o método que será chamado após uma consulta do usuário. Uma *INTENT* pode ter uma ou mais *entidades*.
    -   *Entity*, é um componente da consulta que descreve informações relevantes para a *INTENÇÃO*.
    -   *Enunciados*, são exemplos de consultas fornecidas pelo desenvolvedor, que o LUIS usará para treinar a si mesmo.

Se esses conceitos não são perfeitamente claros, não se preocupe, pois este curso os esclarecerá ainda mais neste capítulo.

Você começará criando as *Entidades necessárias* para criar este curso.

9.  No lado esquerdo da página, clique em *Entidades* e, em seguida, clique **em Criar nova entidade.**

    ![Criar nova entidade](images/AzureLabs-Lab3-11.png)

10. Chame a nova cor *da entidade*, de definido seu tipo *como Simples* e pressione **Done**.

    ![Criar entidade simples – cor](images/AzureLabs-Lab3-12.png)
 
11. Repita esse processo para criar três (3) entidades simples chamadas:

    -   *upsize*
    -   *Reduzir*
    -   *destino*

O resultado deve ser parecido com a imagem abaixo:

![Resultado da criação da entidade](images/AzureLabs-Lab3-13.png)
 
Neste ponto, você pode começar a criar *Intenções*. 

> [!WARNING]
> Não exclua a **intenção** None.

12. No lado esquerdo da página, clique em **Intenções** e, em seguida, clique **em Criar nova intenção.**

    ![Criar novas intenções](images/AzureLabs-Lab3-14.png)

13. Chame a nova *Intenção* **ChangeObjectColor.**

    > [!IMPORTANT]
    > Esse *Nome* de intenção é usado no código posteriormente neste curso, portanto, para melhores resultados, use esse nome exatamente como fornecido.

Depois de confirmar o nome, você será direcionado para a Página de Intenções.

![LUIS – página intenções](images/AzureLabs-Lab3-15.png)

Você observará que há uma caixa de texto solicitando que você digite 5 ou mais *enunciados diferentes.*

> [!NOTE]
> O LUIS converte todos os Enunciados em casos inferiores.

14. Insira o *enunciado a seguir* na caixa de texto superior (atualmente com o texto Digite cerca de *5 exemplos...* ) e pressione **Enter**:

```
The color of the cylinder must be red
```

Você observará que o novo *Enunciado* aparecerá em uma lista abaixo.

Seguindo o mesmo processo, insira os seguintes seis (6) enunciados:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada enunciado que você criou, você deve identificar quais palavras devem ser usadas pelo LUIS como Entidades. Neste exemplo, você precisa rotular todas as cores como uma entidade de cor e toda *a* referência possível a um destino como uma *Entidade de* destino.

15. Para fazer isso, tente clicar na palavra *cilindro* no primeiro Enunciado e selecione *o destino*.

    ![Identificar destinos de enunciado](images/AzureLabs-Lab3-16.png)
 
16. Agora, clique na palavra *vermelha* no primeiro Enunciado e selecione *a cor*.

    ![Identificar entidades de enunciado](images/AzureLabs-Lab3-17.png)
 
17. Rotule a próxima linha também, em *que cubo* deve ser um *destino* e *preto* deve ser uma *cor*. Observe também o uso das palavras *'this',* *'it'* e *'this object',* que estamos fornecendo, para que também tenham tipos de destino não específicos disponíveis. 

18. Repita o processo acima até que todos os Enunciados tenham as Entidades rotuladas. Veja a imagem abaixo se precisar de ajuda.

    > [!TIP]
    > Ao selecionar palavras para rotulá-las como entidades:
    > - Para palavras simples, basta clicar neles.
    > - Para um conjunto de duas ou mais palavras, clique no início e, em seguida, no final do conjunto.

    > [!NOTE]
    > Você pode usar o botão *de alternância Exibição* de Tokens para alternar entre **Entidades/Exibição de Tokens**!

19. Os resultados devem ser vistos nas imagens abaixo, mostrando a **Exibição de Entidades/Tokens**:

    ![Tokens & exibições de entidades](images/AzureLabs-Lab3-18.png)
  
20. Neste ponto, pressione **o botão** Treinar no canto superior direito da página e aguarde até que o indicador pequeno arredonde para ficar verde. Isso indica que o LUIS foi treinado com êxito para reconhecer essa Intenção.

    ![Treinar LUIS](images/AzureLabs-Lab3-19.png)
 
21. Como um exercício para você, crie uma nova Intenção chamada **ChangeObjectSize**, usando as Entidades de *destino,* *upsize* e *downsize*.
22. Seguindo o mesmo processo que a Intenção anterior, insira os seguintes oito (8) Enunciados para Alteração *de* tamanho:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. O resultado deve ser como aquele na imagem abaixo:

    ![Configurar os tokens/entidades ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Depois que ambas as Intenções, **ChangeObjectColor** e **ChangeObjectSize**, foram criadas e treinadas, clique no **botão PUBLICAR** na parte superior da página.

    ![Publicar serviço LUIS](images/AzureLabs-Lab3-21.png)

25. Na página *Publicar,* você finalizará e publicará seu aplicativo LUIS para que ele possa ser acessado pelo seu código.

    1. De acordo com a lista *de lista de 100000001,* publique como **Produção.**
    2. De definir *o fuso horário* como seu fuso horário.
    3. Marque a caixa Incluir **todas as pontuações de intenção previstas.**
    4. Clique em **Publicar no Slot de Produção.**

        ![Configurações de publicação](images/AzureLabs-Lab3-22.png)

26. Na seção Recursos *e Chaves*:

    1.  Selecione a região definida para a instância de serviço no Portal do Azure.
    2.  Você observará um **Starter_Key** abaixo, ignore-o.
    3.  Clique em **Adicionar Chave** e insira a *Chave* que você obteve no Portal do Azure quando criou sua instância de serviço. Se o Azure e o portal do LUIS estão conectados ao mesmo usuário, você receberá menus suspensos para Nome do locatário, Nome da Assinatura e Chave que deseja usar (terá o mesmo nome fornecido anteriormente no Portal do Azure. 

    > [!IMPORTANT] 
    > Sob *o ponto de* extremidade , use uma cópia do ponto de extremidade correspondente à Chave inserida. Você a usará em seu código em breve.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3 – Configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra *o Unity* e clique em **Novo.** 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab3-24.png)

2.  Agora você precisará fornecer um nome de Project Unity, inserindo **MR_LUIS**. Certifique-se de que o tipo de projeto está definido **como 3D.** De definir **o Local** como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio**. Vá para Editar > Preferências e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script** Externo para Visual Studio **2017.** Feche a **janela Preferências.**

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab3-26.png)
 
4.  Em seguida, vá para Arquivo **> Criar Configurações** e alternar a plataforma para Plataforma **Universal** Windows , clicando no **botão Alternar Plataforma.**

    ![Criar Configurações janela, alternar plataforma para UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vá para **Arquivo > Build Configurações** e certifique-se de que:

    1. **O Dispositivo de** Destino está definido **como Qualquer Dispositivo**

        > Para o Microsoft HoloLens, de definido **Dispositivo de Destino** como *HoloLens*.

    2. **O tipo de** build é definido como **D3D**
    3. **O SDK** está definido como **Mais recente instalado**
    4. **Visual Studio versão** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab3-28.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_LuisScene** e pressione **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab3-30.png)

    7. as configurações restantes, no *Build Configurações*, devem ser deixadas como padrão por enquanto.

6. na janela *criar Configurações* , clique no botão **Configurações do Player** , isso abrirá o painel relacionado no espaço onde o *inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab3-31.png) 
 
7. Nesse painel, algumas configurações precisam ser verificadas:

    1. na guia **outros Configurações** :

        1. A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab3-32.png)
      
    2. na guia **publicação Configurações** , em **recursos**, marque:

        1. **InternetClient**
        2. **Microfone**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab3-33.png)

    3. mais adiante no painel, em **XR Configurações** (encontrado abaixo **Configurações de publicação**), **há suporte para a realidade Virtual** de tique, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![atualize o Configurações X R.](images/AzureLabs-Lab3-34.png)

8.  de volta ao *Build Configurações* projetos do _Unity C#_ não estão mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela Configurações de Build.
10. salve sua cena e Project (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4 – criar a cena

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **plano**.

    ![Crie um plano.](images/AzureLabs-Lab3-35.png)

2.  Lembre-se de que, ao clicar com o botão direito do mouse na *hierarquia* novamente para criar mais objetos, se você ainda tiver o último objeto selecionado, o objeto selecionado será o pai do novo objeto. Evite clicar em um espaço vazio dentro da hierarquia e clicar com o botão direito do mouse.

3.  Repita o procedimento acima para adicionar os seguintes objetos:

    1. *Sphere*
    2. *Cilindro*
    3. *Simples*
    4. *Texto 3D*

4.  A *hierarquia* de cena resultante deve ser parecida com a da imagem abaixo:

    ![Configuração da hierarquia de cena.](images/AzureLabs-Lab3-36.png)
 
5.  Clique com o botão esquerdo na **câmera principal** para selecioná-lo, examine o *painel Inspetor* . você verá o objeto Camera com todos os seus componentes.
6.  Clique no botão **Adicionar componente** localizado na parte inferior do *painel Inspetor*.

    ![Adicionar fonte de áudio](images/AzureLabs-Lab3-37.png)
 
7.  Pesquise o componente chamado *fonte de áudio*, conforme mostrado acima.
8.  Além disso, verifique se o componente de *transformação* da câmera principal está definido como (0, 0, 0). isso pode ser feito pressionando o ícone de **engrenagem** ao lado do componente de *transformação* da câmera e selecionando **Redefinir**. O componente de *transformação* deve ter a seguinte aparência:

    1.  A *posição* é definida como **0, 0,** 0.
    2.  A *rotação* está definida como **0, 0, 0**.

    > [!NOTE] 
    > para o Microsoft HoloLens, você também precisará alterar o seguinte, que fazem parte do componente da **câmera** , que está em sua **câmera principal**:
    > - **Limpar sinalizadores:** Cor sólida.
    > - **Plano de fundo** ' Black, Alpha 0 ' – cor hexadecimal: #00000000.

9.  Clique com o botão esquerdo do **plano** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |   Eixo X    | Eixo Y |   Eixo Z    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. Clique com o botão esquerdo do **círculo** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |   Eixo X    | Eixo Y |   Eixo Z    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. Clique com o botão esquerdo do **cilindro** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |   Eixo X    | Eixo Y |   Eixo Z    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. Clique com o botão esquerdo do **cubo** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |        | Transformação- *posição* |       |  \| |       | Transformação- *rotação* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **S**                   | **Z** |  \| | **X** | **S**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Clique no botão esquerdo do novo objeto de **texto** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |       | Transformação- *posição* |       |  \| |       | Transformar em *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **S**                  | **Z** |  \| | **X** | **S**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Altere o **tamanho da fonte** no componente de malha de **texto** para **50**.
15. Altere o *nome* do objeto de **malha de texto** para texto de **ditado**.

    ![Criar objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. A estrutura do painel de hierarquia agora deve ser assim:

    ![malha de texto na exibição de cena](images/AzureLabs-Lab3-38b.png)


17. A cena final deve ser parecida com a imagem abaixo:

    ![A exibição de cena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5 – criar a classe microphonemanager

O primeiro script que você pretende criar é a classe *microphonemanager* . Depois disso, você criará o *LuisManager*, a classe de *comportamentos* e, por fim, a classe *olhar* (fique à vontade para criar todos eles agora, embora ele seja coberto à medida que você atingir cada capítulo).

A classe *microphonemanager* é responsável por:

-   Detectando o dispositivo de gravação conectado ao headset ou ao computador (o que for o padrão).
-   Capture o áudio (voz) e use o ditado para armazená-lo como uma cadeia de caracteres.
-   Depois que a voz for pausada, envie o ditado para a classe *LuisManager* . 

Para criar esta classe: 

1.  clique com o botão direito do mouse no *painel de Project*, **crie > pasta**. Chame os **scripts** da pasta. 

    ![Criar pasta de scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Com a pasta **scripts** criada, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse em **criar > script C#**. Nomeie o script *microphonemanager*. 

3.  Clique duas vezes em *microfonemanager* para abri-lo com *Visual Studio*.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *microphonemanager* :

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado. Eles serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Agora você precisa do método que o aplicativo usa para iniciar e parar a captura de voz e passá-la para a classe *LuisManager* , que será criada em breve. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Adicione um *manipulador de ditado* que será invocado quando a voz pausar. Esse método passará o texto do ditado para a classe *LuisManager* .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Exclua o método *Update ()* , pois essa classe não o usará.

9.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

    > [!NOTE]
    > Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe *LuisManager* , que você criará no próximo capítulo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6 – criar a classe LUISManager

É hora de criar a classe *LuisManager* , que fará a chamada para o serviço Luis do Azure. 

A finalidade dessa classe é receber o texto do ditado da classe *microphonemanager* e enviá-lo para o *API de reconhecimento vocal do Azure* a ser analisado.

Essa classe desserializará a resposta *JSON* e chamará os métodos apropriados da classe de *comportamentos* para disparar uma ação.

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie o script *LuisManager*. 
3.  Clique duas vezes no script para abri-lo com Visual Studio.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Você começará criando três classes **dentro** da classe *LuisManager* (dentro do mesmo arquivo de script, acima do método *Start ()* ) que representará a resposta JSON desserializada do Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Em seguida, adicione as seguintes variáveis dentro da classe *LuisManager* :
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Certifique-se de colocar seu ponto de extremidade do LUIS agora (que você terá do seu portal do LUIS).

8.  O código para o método *ativo ()* agora precisa ser adicionado. Esse método será chamado quando a classe inicializar:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Agora você precisa dos métodos que esse aplicativo usa para enviar o ditado recebido da classe *microphonemanager* para *Luis* e, em seguida, receber e desserializar a resposta. 
10. Depois que o valor da intenção e as entidades associadas forem determinados, eles serão passados para a instância da classe de *comportamentos* para disparar a ação pretendida.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Crie um novo método chamado *AnalyseResponseElements ()* que lerá o *AnalysedQuery* resultante e determine as entidades. Depois que essas entidades forem determinadas, elas serão passadas para a instância da classe de *comportamentos* a ser usada nas ações.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.

12. certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

> [!NOTE]
> Neste ponto, você observará que vários erros aparecem no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe de *comportamentos* que você criará no próximo capítulo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7 – criar a classe de comportamentos

A classe de *comportamentos* irá disparar as ações usando as entidades fornecidas pela classe *LuisManager* .

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie os *comportamentos* do script. 
3.  Clique duas vezes no script para abri-lo com *Visual Studio*.
4.  Em seguida, adicione as seguintes variáveis dentro da classe de *comportamentos* :

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Adicione o código do método *ativo ()* . Esse método será chamado quando a classe inicializar:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Os métodos a seguir são chamados pela classe *LuisManager* (que você criou anteriormente) para determinar qual objeto é o destino da consulta e, em seguida, disparar a ação apropriada.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Adicione o método *FindTarget ()* para determinar qual *Gameobjects* é o destino da tentativa atual. Esse método padroniza o destino para o *gameobject* como "gazed" se nenhum destino explícito for definido nas entidades.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.

8.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8 – criar a classe olhar

A última classe que será necessária para concluir esse aplicativo é a classe *olhar* . Essa classe atualiza a referência ao *gameobject* no momento no foco visual do usuário.

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie o script *olhar*. 
3.  Clique duas vezes no script para abri-lo com *Visual Studio*.
4.  Insira o seguinte código para esta classe:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9 – concluindo a configuração da cena

1.  Para concluir a configuração da cena, arraste cada script que você criou da pasta scripts para o objeto da **câmera principal** no *painel hierarquia*.
2.  Selecione a **câmera principal** e examine o *painel Inspetor*, você deve ser capaz de ver cada script que você anexou e observará que há parâmetros em cada script que ainda devem ser definidos.

    ![Definindo os destinos de referência da câmera.](images/AzureLabs-Lab3-41.png)

3.  Para definir esses parâmetros corretamente, siga estas instruções:

    1. *Microfonemanager*:

        - No *painel hierarquia*, arraste o objeto de **texto ditado** para a caixa valor do parâmetro **texto do ditado** .

    2. *Comportamentos*, no *painel hierarquia*:

        - Arraste o objeto de **esfera** para a caixa destino de referência de *esfera* .
        - Arraste o **cilindro** para a caixa destino de referência do *cilindro* .
        - Arraste o **cubo** para a caixa destino de referência do *cubo* .

    3. *Olhar*:

        - Defina a *distância máxima olhar* como **300** (se ainda não estiver). 

4.  O resultado deve ser semelhante à imagem abaixo:

    ![Mostrando os destinos de referência da câmera, agora definido.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10 – testar no editor do Unity

Teste se a configuração de cena está implementada corretamente.

Verifique se:

-   Todos os scripts são anexados ao objeto da **câmera principal** . 
-   Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.

1.  Pressione o botão **reproduzir** no *Editor do Unity*. O aplicativo deve estar em execução no headset de imersão anexado.

2.  Experimente alguns declarações, como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se você vir um erro no console do Unity sobre a alteração do dispositivo de áudio padrão, a cena poderá não funcionar conforme o esperado. Isso ocorre devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que os têm. Se você vir esse erro, simplesmente pare a cena e inicie-a novamente e as coisas devem funcionar conforme o esperado.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11 – criar e sideloadr a solução UWP

Depois de garantir que o aplicativo está funcionando no editor do Unity, você estará pronto para compilar e implantar.

Para compilar:

1.  Salve a cena atual clicando em **arquivo > salvar**.
2.  vá para **arquivo > Build Configurações**.
3.  Marque a caixa chamada **projetos do Unity C#** (útil para ver e depurar seu código depois que o projeto UWP for criado.
4.  Clique em **Adicionar e abrir cenas** e em **Compilar**.

    ![compilar Configurações janela](images/AzureLabs-Lab3-43.png)

4.  Você será solicitado a selecionar a pasta na qual deseja criar a solução. 

5.  Crie uma pasta *Builds* e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha. 
6.  Clique em **Selecionar pasta** para iniciar a compilação nesse local.
 
    ![Criar pasta builds ](images/AzureLabs-Lab3-44.png)
     ![ Selecionar pasta builds](images/AzureLabs-Lab3-45.png)
 
7.  Depois de concluir a compilação do Unity (pode levar algum tempo), ele deve abrir uma janela do **Explorador de arquivos** no local de sua compilação.

Para implantar no computador local:

1.  no *Visual Studio*, abra o arquivo de solução que foi criado no [capítulo anterior](#chapter-10--test-in-the-unity-editor).
2.  Na **plataforma da solução**, selecione **x86**, **computador local**.
3.  Na **configuração da solução** , selecione **depurar**.

    > para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - conheça o **endereço IP** do seu HoloLens, que pode ser encontrado na *Configurações > rede & Internet > Wi-Fi opções avançadas*; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *Configurações > atualização & > de segurança para desenvolvedores*.

    ![Implantar o Aplicativo](images/AzureLabs-Lab3-46.png)
 
4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.
5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado!
6.  Depois de iniciado, o aplicativo solicitará que você autorize o acesso ao _microfone_. Use os *controladores de movimento* ou a *entrada de voz* ou o *teclado* para pressionar o botão **Sim** . 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12 – melhorando seu serviço LUIS

>[!IMPORTANT] 
> Este capítulo é incrivelmente importante e pode precisar ser iterado várias vezes, pois isso ajudará a melhorar a precisão do seu serviço LUIS: Certifique-se de concluir isso.

Para melhorar o nível de compreensão fornecido pelo LUIS, você precisa capturar novos declarações e usá-los para treinar novamente seu aplicativo LUIS.

Por exemplo, você pode ter treinado LUIS para entender "aumentar" e "upsizing", mas não iria querer que seu aplicativo também entenda palavras como "ampliar"?

Depois de usar seu aplicativo algumas vezes, tudo o que você disse será coletado pelo LUIS e disponível no PORTAL do LUIS.

1.  Acesse o aplicativo do portal seguindo este [link](https://www.luis.ai/home)e faça logon.
2.  Depois de fazer logon com suas credenciais do MS, clique no *nome do aplicativo*.
3.  Clique no botão **examinar ponto de extremidade declarações** à esquerda da página.

    ![Examinar declarações](images/AzureLabs-Lab3-47.png)
 
4.  Você verá uma lista dos declarações que foram enviados ao LUIS pelo seu aplicativo de realidade misturada.

    ![Lista de declarações](images/AzureLabs-Lab3-48.png)
 
Você observará algumas *entidades* realçadas. 

Ao focalizar cada palavra realçada, você pode examinar cada expressão e determinar qual entidade foi reconhecida corretamente, quais entidades estão erradas e quais entidades estão ausentes.

No exemplo acima, foi detectado que a palavra "Spear" foi realçada como um destino, portanto, é necessário corrigir o erro, o que é feito ao passar pela palavra com o mouse e clicar em **remover rótulo**.

![Verificar declarações ](images/AzureLabs-Lab3-49.png)
 ![ remover rótulo de imagem](images/AzureLabs-Lab3-50.png)
 
5.  Se encontrar declarações que estejam completamente errados, você poderá excluí-los usando o botão **excluir** no lado direito da tela.

    ![Excluir declarações incorretos](images/AzureLabs-Lab3-51.png)

6.  Ou se sentir que o LUIS interpretou o expressão corretamente, você poderá validar sua compreensão usando o botão **Adicionar à intenção alinhada** .

    ![Adicionar à intenção alinhada](images/AzureLabs-Lab3-52.png)

7.  Depois de classificar todos os declarações exibidos, tente e recarregue a página para ver se há mais informações disponíveis.
8.  É muito importante repetir esse processo tantas vezes quanto possível para melhorar a compreensão do seu aplicativo. 

**Divirta-se!**

## <a name="your-finished-luis-integrated-application"></a>Seu aplicativo LUIS Integrated concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço do Azure Reconhecimento vocal Intelligence, para entender o que um usuário diz e agir sobre essas informações.

![Resultado do laboratório](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Ao usar esse aplicativo, você pode notar que, se olhar no objeto Floor e pedir para alterar sua cor, ele fará isso. Você pode solucionar como impedir que seu aplicativo altere a cor do piso?

### <a name="exercise-2"></a>Exercício 2

Tente estender os recursos de LUIS e de aplicativo, adicionando funcionalidades adicionais para objetos em cena; como exemplo, crie novos objetos no ponto de acesso olhar, dependendo do que o usuário diz e, em seguida, use esses objetos junto com os objetos de cena atuais, com os comandos existentes.