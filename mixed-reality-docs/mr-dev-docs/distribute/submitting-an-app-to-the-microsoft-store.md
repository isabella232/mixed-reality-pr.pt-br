---
title: Como enviar um aplicativo para a Microsoft Store
description: Explora o processo de empacotamento, teste e envio de seus aplicativos de realidade misturada para o Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, headsets de imersão, aplicativo, UWP, envio, envio, filtros, metadados, requisitos do sistema, palavras-chave, wack, certificação, pacote, Appx, merchandising, fone de ouvido misto, headset de realidade misturada do Windows, headset da realidade virtual
ms.openlocfilehash: b5d25817afeb2d8d970d329c802b7eaabcdf7f35
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703112"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Como enviar um aplicativo para a Microsoft Store

Tanto o [HoloLens](../hololens-hardware-details.md) quanto o PC com Windows 10 que ligam o [headset de imersão](../discover/immersive-headset-hardware-details.md) executam plataforma universal do Windows aplicativos. Se você estiver enviando um aplicativo que dá suporte a HoloLens, PC ou ambos, o envio de aplicativos passará pelo [Partner Center](https://partner.microsoft.com/dashboard).

Se você ainda não tiver uma conta de desenvolvedor do Partner Center, [Inscreva-](https://developer.microsoft.com/store/register) se para uma antes de prosseguir.

## <a name="packaging-a-mixed-reality-app"></a>Empacotando um aplicativo de realidade misturada

Há várias etapas para empacotar um aplicativo de realidade misturada, incluindo:

* Preparando corretamente todos os ativos de imagem
* Escolhendo a imagem do bloco exibida no menu Iniciar do HoloLens
* Definindo o destino e a versão mínima do Windows para o aplicativo
* Configurando as famílias de dispositivos de destino nas dependências do aplicativo
* Adicionando metadados para associar o aplicativo ao Microsoft Store
* Criando um pacote de carregamento

Cada um desses estágios de envio é abordado em sua própria seção abaixo-é recomendável passar por eles de forma sequencial você não sai em sua primeira tentativa de envio.

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar os ativos de imagem incluídos no Appx

Os seguintes ativos de imagem são necessários para as ferramentas de criação de Appx criar seu aplicativo em um pacote Appx, que é necessário para o envio para o Microsoft Store. Você pode saber mais sobre as [diretrizes para ativos de bloco e ícone](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) no msdn.

| Ativo necessário | Escala recomendada | Formato de imagem | Onde o ativo é exibido? | 
|----------|----------|----------|------------------|
| Logotipo quadrado do 71 x 71 | Qualquer |  PNG | N/D | 
| Logotipo quadrado do 150x150 | 150x150 (100% Scale) ou 225x225 (150% Scale) | PNG | Iniciar Pins e todos os aplicativos (se 310 x 310 não for fornecido), sugestões de pesquisa de repositório, página de listagem de repositório, procurar na loja, pesquisa de loja | 
|  Logotipo de largo 310x150 largo |  Qualquer  |  PNG  |  N/D | 
|  Logotipo da Store |  75x75 (escala de 150%)  |  PNG  |  Partner Center, aplicativo de relatório, escrever uma revisão, minha biblioteca | 
|  Splash Screen |  930x450 (escala de 150%)  |  PNG  |  inicializador de aplicativo 2D (Slate) | 

Se você estiver desenvolvendo para o HoloLens, há ativos adicionais recomendados que você pode aproveitar:

| Ativos recomendados | Escala recomendada | Onde o ativo é exibido? | 
|----------|----------|----------|
|  Logotipo quadrado do 310 x 310 |  310 x 310 (escala de 150%) |  Iniciar Pins e todos os aplicativos | 

### <a name="live-tile-requirements"></a>Requisitos de bloco dinâmico

Por padrão, o menu iniciar no HoloLens usará a maior imagem de bloco quadrado incluída. Os aplicativos publicados pela Microsoft têm um iniciador 3D opcional, que pode ser adicionado ao seu aplicativo seguindo as instruções de [implementação do iniciador do aplicativo 3D](implementing-3d-app-launchers.md) .

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificando o destino e a versão mínima do Windows

Se o seu aplicativo de realidade misturada incluir recursos específicos de uma versão do Windows, é importante especificar o destino com suporte e as versões mínimas da plataforma.

**Preste atenção especial para aplicativos direcionados a [headsets de imersão de realidade mista do Windows](../discover/immersive-headset-hardware-details.md), que exigem pelo menos a atualização de criadores de outono do Windows 10 (10,0; Crie 16299) para funcionar corretamente.**

Você será solicitado a definir o destino e a versão mínima do Windows ao criar um novo projeto universal do Windows no Visual Studio. Para projetos existentes, você pode alterar essa configuração no menu **projeto** selecionando as **propriedades de><nome do seu aplicativo** na parte inferior do menu suspenso.

![Definindo as versões de plataforma mínima e de destino no Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Definindo as versões de plataforma mínima e de destino no Visual Studio*

### <a name="specifying-target-device-families"></a>Especificando famílias de dispositivos de destino

Os aplicativos de realidade mista do Windows (para os [headsets](../discover/immersive-headset-hardware-details.md)de [HoloLens](../hololens-hardware-details.md) e de imersão) fazem parte do plataforma universal do Windows, portanto, qualquer pacote de aplicativo com uma família de dispositivos **Windows. universal** [target](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) pode ser executado em computadores com o HoloLens ou Windows 10 com headsets de imersão. Se você não especificar uma família de dispositivos de destino em seu manifesto de aplicativo, você poderá abrir seu aplicativo inadvertidamente em dispositivos Windows 10 indesejados. Siga as etapas abaixo para especificar a família de dispositivos do Windows 10 pretendida e, em seguida, [Verifique se as famílias de dispositivos corretas estão definidas quando você carrega o pacote do aplicativo no Partner Center para envio de Microsoft Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Para definir esse campo no Visual Studio, clique com o botão direito do mouse em **Package. appxmanifest** e selecione **Exibir código** e localize o campo **nome do TargetDeviceFamily** . Por padrão, ele deve ser semelhante à seguinte entrada:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se você estiver criando um aplicativo do **hololens** , poderá verificar se ele está instalado apenas no HoloLens definindo a família do dispositivo de destino como **Windows. Holographic**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se seu aplicativo requer a funcionalidade de **HoloLens 2** , como olho ou acompanhamento de mão, você pode verificar se ele é destinado às versões 18362 ou superiores do Windows, definindo a família do dispositivo de destino como **Windows. Holographic** com **MinVersion** de 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Se seu aplicativo for criado para **headsets de imersão de realidade mista do Windows**, você poderá verificar se ele está instalado apenas em computadores Windows 10 com a atualização dos criadores de outono do Windows 10 (necessário para a realidade mista do Windows) definindo a família do dispositivo de destino como **Windows. desktop** com uma **MinVersion** de 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Por fim, se o seu aplicativo pretende executar tanto no **HoloLens** quanto em **headsets de imersão de realidade mista do Windows**, você pode verificar se o aplicativo está disponível apenas para essas duas famílias de dispositivos e garantir simultaneamente que cada destino tenha a versão mínima correta do Windows, incluindo uma linha para cada família de dispositivos de destino com sua respectiva MinVersion:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Você pode saber mais sobre como direcionar as famílias de dispositivos lendo a [documentação do TARGETDEVICEFAMILY UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associar o aplicativo à loja

Quando você associa seu aplicativo com o Microsoft Store, os seguintes valores são baixados para o arquivo de manifesto do aplicativo local dos projetos atuais:

* Package Display Name
* Nome do Pacote
* ID do fornecedor
* Nome de Exibição do Editor
* Versão

Se você estiver substituindo o arquivo Package. appxmanifest padrão por seu próprio arquivo. xml personalizado, não será possível associar seu aplicativo ao Microsoft Store. A associação de um arquivo de manifesto personalizado ao repositório resultará em uma mensagem de erro.

Você também pode testar os cenários de compra e de notificação acessando sua solução do Visual Studio e selecionando **o Project > Store > associar o aplicativo à loja**.

### <a name="creating-an-upload-package"></a>Criando um pacote de carregamento

Siga as diretrizes em [empacotamento de aplicativos universais do Windows para Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

A etapa final da criação de um pacote de carregamento é validar o pacote usando o [Kit de certificação de aplicativos para Windows](#windows-app-certification-kit).

Se você estiver adicionando um pacote específico do HoloLens a um produto existente que está disponível em outras famílias de dispositivos Windows 10, preste atenção a: 

* [Como os números de versão podem afetar quais pacotes são entregues a clientes específicos](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)
* [Como os pacotes são distribuídos para sistemas operacionais diferentes](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)

As diretrizes gerais são que o pacote com o número de versão mais alto para um dispositivo é aquele distribuído pelo repositório.

Em um cenário em que há um pacote **Windows. universal** e um pacote **Windows. Holographic** , e o pacote Windows. universal tem um número de versão mais alto, um usuário do HoloLens baixará o número de versão mais alto do pacote do Windows. universal em vez do pacote Windows. Holographic. 

Nos casos em que o cenário acima não é o resultado que você está procurando, há várias soluções disponíveis:

* Verifique se os pacotes específicos da plataforma, como Windows. Holographic, têm sempre um número de versão mais alto do que seus pacotes independentes de plataforma, como o Windows. universal
* Não empacote aplicativos como Windows. universal se você também tiver pacotes específicos da plataforma. em vez disso, empacote o pacote Windows. universal para as plataformas específicas nas quais você deseja disponibilizá-los
* Crie um único pacote Windows. universal que funcione em todas as plataformas. O suporte para essa opção não é ótimo no momento para que as soluções acima sejam recomendadas.

>[!NOTE]
> Para dar suporte ao seu aplicativo tanto no HoloLens (1º gen) quanto no HoloLen 2, você precisa carregar dois pacotes de aplicativos; um que contém x86 para HoloLens (1º gen) e um contendo ARM ou ARM64 para o HoloLens 2. 
> 
> Se você incluir o ARM e o ARM64 em seu pacote, a versão do ARM64 será a usada no HoloLens 2. 

>[!NOTE]
> Você pode declarar um único pacote para ser aplicável a várias famílias de dispositivos de destino

## <a name="testing-your-app"></a>Testando seu aplicativo

### <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Quando você cria pacotes de aplicativos para enviar ao Partner Center por meio do Visual Studio, o assistente para criar pacotes de aplicativos solicita que você execute o kit de certificação de aplicativos para Windows nos pacotes que são criados. Para ter um processo de envio suave na loja, é melhor verificar se a cópia local do seu aplicativo passa pelos testes do [Kit de certificação de aplicativos do Windows](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) antes de enviá-los para a loja. A execução do kit de certificação de aplicativos para Windows em um HoloLens remoto não tem suporte no momento.

### <a name="run-on-all-targeted-device-families"></a>Executar em todas as famílias de dispositivos de destino

A plataforma universal do Windows permite que você crie um único aplicativo que é executado em todas as famílias de dispositivos Windows 10. No entanto, ele não garante que os aplicativos universais do Windows funcionarão apenas em todas as famílias de dispositivos. É importante [testar seu aplicativo](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) em cada uma de suas famílias de dispositivos escolhidas para garantir uma boa experiência.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Enviando seu aplicativo de realidade misturada para a loja

Se você estiver enviando um aplicativo de realidade misturada baseado em um projeto do Unity, consulte este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) primeiro.

Em geral, o envio de um aplicativo de realidade mista do Windows que funciona em headsets de HoloLens e/ou de imersão é como enviar qualquer aplicativo UWP para o Microsoft Store. Depois de [criar seu aplicativo reservando seu nome](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), siga a lista de [verificação de envio do UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Uma das primeiras coisas que você fará é [selecionar uma categoria e uma subcategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) para sua experiência de realidade mista. É importante que você **escolha a categoria mais precisa para seu aplicativo**. As categorias ajudam a proteger seu aplicativo nas categorias de armazenamento corretas e a garantir que ele apareça usando consultas de pesquisa relevantes. **Listar seu título VR como um jogo não resultará em melhor exposição para seu aplicativo** e poderá impedi-lo de aparecer em categorias que estão mais ajustadas e menos lotadas.

No entanto, há quatro áreas principais no processo de envio, em que você desejará fazer seleções mistas específicas da realidade:
1. Na seção **[declarações de produto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** em [Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Na seção **[requisitos do sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** , em [Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. Na seção **[disponibilidade da família de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** , em [pacotes](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. Em vários campos da **[página de listagem de armazenamento](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Declarações de produto da realidade misturada

Na página **[Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[declarações de produto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** .

![Declarações de produto da realidade misturada](images/product-declarations-900px.png)<br>
Declarações de produto da realidade misturada

Primeiro, você precisa identificar os tipos de dispositivo para os quais seu aplicativo oferece uma experiência de realidade mista. Identificar tipos de dispositivo garante que seu aplicativo esteja incluído em coleções de realidade mista do Windows na loja.

Ao lado de "esta experiência foi projetada para a realidade mista do Windows em:"
* Marque a caixa **PC** se seu aplicativo oferecer uma experiência VR quando um headset de imersão estiver conectado ao PC do usuário. É recomendável marcar essa caixa se seu aplicativo estiver definido para ser executado exclusivamente em um headset de imersão ou se for um jogo de PC padrão ou um aplicativo que ofereça um modo de realidade misturada e/ou conteúdo de bônus quando um headset estiver conectado.
* Marque a caixa **HoloLens** somente se seu aplicativo oferecer uma experiência Holographic quando for executado no HoloLens.
* Marque **ambas as** caixas se seu aplicativo oferecer uma experiência de realidade mista em ambos os tipos de dispositivo.

Se você selecionou "PC" acima, convém definir a "configuração de realidade mista" (nível de atividade). Isso se aplica somente a experiências de realidade misturadas que são executadas em computadores conectados a headsets de alto-fones de ouvido, pois aplicativos de realidade misturados no HoloLens são de escala mundial e o usuário não define um limite durante a instalação.
* Escolha **encaixar + posição** se você tiver projetado seu aplicativo para que o usuário permaneça em uma posição. Por exemplo, em um jogo em que você está no controle de uma ferramenta cockpit de aeronave.
* Escolha **todas as experiências** se seu aplicativo for projetado com a intenção que o usuário percorre dentro de um limite definido definido durante a instalação. Por exemplo, pode ser um jogo no qual você passo a lado e o pato para ataques de subexposição.

### <a name="mixed-reality-system-requirements"></a>Requisitos de sistema de realidade misturada

Na página **[Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[requisitos do sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisitos do sistema](images/system-reqs-800px.png)<br>
Requisitos do sistema

Nesta seção, você identificará o hardware mínimo (necessário) e o hardware recomendado (opcional) para seu aplicativo de realidade misturada.

**Hardware de entrada:**

Use as caixas de seleção para informar aos clientes potenciais se seu aplicativo dá suporte a **microfone** para [entrada de voz](../design/voice-input.md)), **[controlador Xbox ou gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)** e/ou **[controladores de movimento do Windows Mixed Reality](../design/motion-controllers.md)**. Essas informações serão apresentadas na página de detalhes do produto do aplicativo na loja e ajudarão seu aplicativo a ser incluído nas coleções de jogos/aplicativos apropriadas. Por exemplo, pode haver uma coleção para todos os jogos que dão suporte a controladores de movimento.

Tenha em consideração a seleção de caixas de seleção para "hardware mínimo" ou "hardware recomendado" para tipos de entrada. 

Por exemplo: 
* Se o seu jogo exigir controladores de movimento, mas aceitar entrada de voz via microfone, marque a caixa de seleção "hardware mínimo" ao lado de "controladores de movimento de realidade do Windows misto", mas a caixa de seleção "hardware recomendado" ao lado de "microfone". 
* Se o jogo puder ser reproduzido com um controlador Xbox, gamepad ou controladores de movimento, você poderá marcar a caixa de seleção "hardware mínimo" ao lado de "controlador Xbox ou gamepad" e selecionar a caixa de seleção "hardware recomendado" ao lado de "controladores de movimento de realidade do Windows misto", já que os controladores de movimento provavelmente oferecerão um passo para uso do gamepad.

**Headset de imersão do Windows Mixed realm:**

Indicando se um headset de imersão é necessário para usar seu aplicativo, ou é opcional, é essencial para a satisfação e a educação do cliente.

Se seu aplicativo *só* puder ser usado por meio de um headset de imersão, marque a caixa de seleção "mínimo de hardware" ao lado de "headset de imersão do Windows Mixed Realm". Isso será exibido na página de detalhes do produto do aplicativo no repositório como um aviso acima do botão comprar para que os clientes não achem que estão comprando um aplicativo que funcionará em seu PC, como um aplicativo de desktop tradicional.

Se seu aplicativo for executado na área de trabalho, como um aplicativo de PC tradicional, mas oferecer uma experiência VR quando um headset de imersão estiver conectado (se o conteúdo completo do seu aplicativo estiver disponível ou apenas uma parte), marque a caixa de seleção "hardware recomendado" ao lado de "headset de imersão de realidade do Windows misto". Nenhum aviso será exibido acima do botão comprar na página de detalhes do produto do aplicativo se seu aplicativo funcionar como um aplicativo de área de trabalho tradicional sem um headset de imersão conectado.

**Especificações do PC:**

Se você quiser que seu aplicativo alcance o máximo possível de usuários com o fone de ouvido da realidade misturada do Windows, [direcione](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) as especificações do PC para [PCs com a realidade mista do Windows com gráficos integrados](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Se o seu aplicativo de realidade misturada tem como alvo os requisitos mínimos de PC do Windows Mixed Reality ou precisa de uma configuração de PC específica como a GPU dedicada de um [Windows Mixed Reality Ultra PC] ( https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines , você deve adicionar as especificações relevantes do PC na coluna "hardware mínimo".

Se o seu aplicativo de realidade misturada for projetado para melhorar o desempenho ou oferecer gráficos de resolução mais alta em uma configuração de PC ou placa gráfica específica, você deverá incluir as especificações relevantes do PC na coluna "hardware recomendado".

Isso só se aplica se o seu aplicativo de realidade misturada usar um headset de imersão conectado a um PC. Se seu aplicativo de realidade misturada só for executado no HoloLens, você não precisará indicar as especificações do PC, pois o HoloLens tem apenas uma configuração de hardware.

### <a name="device-family-availability"></a>Disponibilidade da família de dispositivos

Se você tiver [empacotado seu aplicativo corretamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) no Visual Studio, carregá-lo na página pacotes deve produzir uma tabela com as famílias de dispositivos disponíveis.

![Tabela de disponibilidade da família de dispositivos](images/device-family-table-900px.png)<br>
Tabela de disponibilidade da família de dispositivos

Se o seu aplicativo de realidade misturada funcionar em headsets de imersão, pelo menos "Windows 10 desktop" deverá ser selecionado na tabela. Se o seu aplicativo de realidade misturada funcionar no HoloLens, pelo menos "Windows 10 Holographic" deverá ser selecionado. Se seu aplicativo for executado em ambos os tipos de headset do Windows Mixed Reality, tanto "Windows 10 desktop" como "Windows 10 Holographic" devem ser selecionados.

>[!TIP]
>Muitos desenvolvedores se deparam com erros ao carregar o pacote do aplicativo relacionado a incompatibilidades entre o manifesto do pacote e as informações de sua conta de aplicativo/Publicador no Partner Center. Esses erros geralmente podem ser evitados entrando-se no Visual Studio com a mesma conta associada à sua conta de desenvolvedor do Windows (aquela que você usa para entrar no Partner Center). Se você usar a mesma conta, poderá associar seu aplicativo à sua identidade no Microsoft Store antes de empacotá-lo.

![Associar seu aplicativo ao Microsoft Store](images/associate-your-app-700px.png)<br>
Associar seu aplicativo ao Microsoft Store no Visual Studio

### <a name="store-listing-page"></a>Página de listagem de armazenamento

Na página de [listagem de armazenamento](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) do processo de envio de aplicativo, há vários lugares em que você pode adicionar informações úteis sobre seu aplicativo de realidade misturada.

>[!IMPORTANT]
>Para garantir que seu aplicativo seja Categorizado corretamente pela loja e tornar-se detectável para os clientes do Windows Mixed Reality, você deve adicionar **"realidade mista do Windows"** como um dos seus "termos de pesquisa" para o aplicativo (você pode encontrar termos de pesquisa expandindo a seção "campos compartilhados").

![Adicionar a realidade mista do Windows aos termos de pesquisa](images/search-terms-800px.png)<br>
Adicionar "realidade mista do Windows" aos termos de pesquisa

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Oferecendo uma avaliação gratuita para seu jogo ou aplicativo

Em muitos casos, seus consumidores terão se limitado a nenhuma experiência com a realidade virtual antes de comprar um headset de imersão de realidade mista do Windows. Eles podem não saber o que esperar de jogos intensos ou estar familiarizados com seu próprio limite de conforto em experiências de imersão. Muitos clientes também podem experimentar um headset de imersão de realidade misturada do Windows em computadores que não são crachás como [PCs com realidade do Windows Mixed](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Devido a essas considerações, é altamente recomendável que você considere a possibilidade de oferecer uma [avaliação gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para seu aplicativo de realidade mista ou jogo pago.

## <a name="see-also"></a>Veja também
* [O que é Realidade Misturada?](../discover/mixed-reality.md)
* [Visão geral do desenvolvimento](../develop/development.md)
* [Modos de exibição do aplicativo](../design/app-views.md)
* [Entendendo o desempenho da realidade misturada](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para o Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Como testar seu aplicativo no HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
