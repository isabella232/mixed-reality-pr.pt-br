---
title: Como enviar um aplicativo para a Microsoft Store
description: Explora o processo de empacotamento, teste e envio de seus aplicativos de realidade misturada para o Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, headsets imersivos, aplicativo, uwp, envio, envio, filtros, metadados, requisitos do sistema, palavras-chave, organização, certificação, pacote, appx, merchandising, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197700"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Como enviar um aplicativo para a Microsoft Store

> [!IMPORTANT]
> Se você estiver enviando um aplicativo Unreal, siga as instruções **[de publicação](../develop/unreal/unreal-publishing-to-store.md)** antes de continuar.

## <a name="prerequisites"></a>Pré-requisitos

Tanto [HoloLens](/hololens/hololens1-hardware) quanto o computador Windows 10 a energia do headset imersivo, executem [aplicativos](../discover/immersive-headset-hardware-details.md) da Plataforma universal Windows. Se você estiver enviando um aplicativo que dá suporte HoloLens, PC ou ambos, o envio do aplicativo passa pelo [Partner Center](https://partner.microsoft.com/dashboard).

Se você ainda não tiver uma conta Partner Center desenvolvedor, [inscreva-se](https://developer.microsoft.com/store/register) em uma antes de continuar. Você pode encontrar mais informações sobre diretrizes de envio e listas de verificação neste artigo [de envios de aplicativo](/windows/uwp/publish/app-submissions).

> [!IMPORTANT]
> Você não poderá enviar nenhum aplicativo para o Microsoft Store se sua conta de desenvolvedor do Partner Center falhar na verificação de emprego. Entre em contato com a Partner Center [de suporte do Partner Center](https://developer.microsoft.com/windows/support) para obter mais detalhes.

## <a name="packaging-a-mixed-reality-app"></a>Empacotando um aplicativo de Realidade Misturada

Há várias etapas para empacotar um aplicativo de Realidade Misturada, incluindo:

* Preparando corretamente todos os ativos de imagem
* Escolhendo a imagem de lado exibida no HoloLens menu Iniciar
* Definindo a versão de destino e Windows mínima para o aplicativo
* Definindo as famílias de dispositivos de destino nas dependências do aplicativo
* Adicionar metadados para associar o aplicativo ao Microsoft Store
* Criando um pacote de upload

Cada um desses estágios de envio é abordado em sua própria seção abaixo – é recomendável passar por eles sequencialmente, você não deixa nenhum fora em sua primeira tentativa de envio.

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar ativos de imagem incluídos no appx

Os ativos de imagem a seguir são necessários para que as ferramentas de criação appx criem seu aplicativo em um pacote appx, que é necessário para envio para o Microsoft Store. Você pode saber mais sobre as [diretrizes para ativos de ícones e](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) deile no MSDN.

| Ativo necessário | Escala recomendada | Formato de imagem | Onde o ativo é exibido? | 
|----------|----------|----------|------------------|
| Logotipo do Square 71x71 | Qualquer |  PNG | N/D | 
| Logotipo square 150x150 | 150 x 150 (escala de 100% ) ou 225 x 225 (escala de 150%) | PNG | Iniciar pins e Todos os Aplicativos (se 310x310 não for fornecido), Sugestões de Pesquisa da Loja, Página de Listagem da Loja, Procurar na Loja, Pesquisa de Loja | 
|  Logotipo wide 310x150 |  Qualquer  |  PNG  |  N/D | 
|  Logotipo da Store |  75 x 75 (escala de 150%)  |  PNG  |  Partner Center, Aplicativo de Relatório, Escrever uma Revisão, Minha Biblioteca | 
|  Splash Screen |  930x450 (escala de 150%)  |  PNG  |  Launcher de aplicativo 2D (slate) | 

Se você estiver desenvolvendo para HoloLens, há outros ativos recomendados que você pode aproveitar:

| Ativos recomendados | Escala recomendada | Onde o ativo é exibido? | 
|----------|----------|----------|
|  Logotipo do Square 310x310 |  310 x 310 (escala de 150%) |  Iniciar pins e Todos os Aplicativos | 

### <a name="live-tile-requirements"></a>Bloco Dinâmico requisitos

O menu Iniciar em HoloLens usará a maior imagem de lado quadrado incluída por padrão. Os aplicativos publicados pela Microsoft têm um launcher 3D opcional, que você pode adicionar ao seu aplicativo seguindo as instruções de implementação do launcher de aplicativo [3D.](implementing-3d-app-launchers.md)

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificando o destino e a versão mínima do Windows

Se seu aplicativo de Realidade Misturada incluir recursos específicos de uma versão Windows, será importante especificar as versões de plataforma mínima e de destino com suporte.

**Preste atenção especial para aplicativos [destinados Windows Mixed Reality headsets imersivos,](../discover/immersive-headset-hardware-details.md)que exigem pelo menos o Windows 10 Fall Creators Update (10.0; Build 16299) para funcionar corretamente.**

Você será solicitado a definir o destino e a versão mínima do Windows ao criar um novo Windows Project Universal Visual Studio. Para projetos existentes, você pode alterar essa configuração no menu **Project** **>** selecionando<Propriedades do nome do aplicativo na parte inferior do menu suspenso.

![Definindo versões mínimas e de plataforma de destino Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Definindo versões mínimas e de plataforma de destino Visual Studio*

### <a name="specifying-target-device-families"></a>Especificando famílias de dispositivos de destino

Windows Mixed Reality aplicativos (para headsets [HoloLens](/hololens/hololens1-hardware) e [imersivos)](../discover/immersive-headset-hardware-details.md)fazem parte da Plataforma Universal do Windows, portanto, qualquer pacote de aplicativos com um **Windows. A família** [de dispositivos de](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) destino universal pode ser HoloLens ou Windows 10 PCs com headsets imersivos. Se você não especificar uma família de dispositivos de destino no manifesto do aplicativo, poderá abrir inadvertidamente seu aplicativo para dispositivos Windows 10 não intencionais. Siga as etapas abaixo para especificar a família de dispositivos Windows 10 pretendido e verifique se você definiu as famílias de dispositivos corretas ao carregar seu pacote de aplicativos no Partner Center para Microsoft Store [envio.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Para definir esse campo Visual Studio, clique com o botão direito do mouse em **Package.appxmanifest** e selecione Exibir Código **e,** em seguida, localizar o campo Nome de **TargetDeviceFamily.** Por padrão, ele deve se parecer com a seguinte entrada:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se estiver criando um aplicativo **HoloLens,** você poderá garantir que ele esteja instalado somente no HoloLens definindo a família de dispositivos de destino como **Windows. Holographic**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se seu aplicativo exigir **HoloLens 2,** como acompanhamento ocular ou manual, você poderá garantir que ele seja direcionado para as versões 18362 ou superior do Windows, definindo a família de dispositivos de destino como **Windows. Holographic** com um **MinVersion** de 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Se seu aplicativo for criado para **headsets imersivos** do Windows Mixed Reality , você poderá garantir que ele seja instalado somente em PCs do Windows 10 com o Windows 10 Fall Creators Update (necessário para Windows Mixed Reality) definindo a família de dispositivos de destino como **Windows. Área** de trabalho **com um MinVersion** de 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Por fim, se o aplicativo se destina a ser executado em headsets **imersivos** HoloLens e Windows Mixed Reality , você pode garantir que o aplicativo só está disponível para essas duas famílias de dispositivos e garantir simultaneamente que cada destino tenha a versão mínima correta do Windows incluindo uma linha para cada família de **dispositivos** de destino com sua respectiva MinVersion:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Saiba mais sobre como direcionar famílias de dispositivos lendo a documentação da [UWP TargetDeviceFamily](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associar o aplicativo à Store

Quando você associa seu aplicativo ao Microsoft Store, os seguintes valores são baixados no arquivo de manifesto do aplicativo local de projetos atuais:

* Package Display Name
* Nome do Pacote
* ID do fornecedor
* Nome de Exibição do Editor
* Versão

Se você estiver substituindo o arquivo package.appxmanifest padrão por seu próprio arquivo .xml personalizado, não poderá associar seu aplicativo ao Microsoft Store. Associar um arquivo de manifesto personalizado ao Store resultará em uma mensagem de erro.

Você também pode testar cenários de compra e notificação indo para sua solução Visual Studio e selecionando **Project > Store > Associar Aplicativo à Loja**.

### <a name="creating-an-upload-package"></a>Criando um pacote de upload

Siga as diretrizes em [Empacotando aplicativos Windows Universal para Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

A etapa final da criação de um pacote de upload é validar o pacote usando o [kit de certificação Windows aplicativo.](#windows-app-certification-kit)

Se você estiver adicionando um HoloLens específico a um produto existente que está disponível em outras Windows 10 de dispositivos, preste atenção a: 

* [Como os números de versão podem afetar quais pacotes são entregues a clientes específicos](/windows/uwp/publish/package-version-numbering)
* [Como os pacotes são distribuídos para diferentes sistemas operacionais](/windows/uwp/publish/guidance-for-app-package-management)

A orientação geral é que o pacote com o número de versão mais alto para um dispositivo é aquele distribuído pela Store.

Em um cenário em que há um **Windows. Pacote** universal e um **Windows. Pacote holográfico** e o Windows. O pacote universal tem um número de versão mais alto, HoloLens usuário baixará o número de versão mais alto Windows. Pacote universal em vez do Windows. Pacote holográfico. 

Nos casos em que o cenário acima não é o resultado que você está procurando, há várias soluções disponíveis:

* Verifique se os pacotes específicos da plataforma, como Windows. Holographic, sempre tem um número de versão maior do que os pacotes agnósticos da plataforma, como Windows. Universal
* Não empacote aplicativos como Windows. Universal se você também tiver pacotes específicos da plataforma – em vez disso, empacote o Windows. Pacote universal para as plataformas específicas em que você deseja que ele seja disponibilizado
* Crie um único Windows. Pacote universal que funciona em todas as plataformas. O suporte para essa opção não é ótimo no momento, portanto, as soluções acima são recomendadas.

>[!NOTE]
> Para dar suporte ao aplicativo no HoloLens (1ª geração) e no HoloLen 2, você precisa carregar dois pacotes de aplicativos; um que contém x86 para HoloLens (1ª geração) e outro contendo ARM ou ARM64 para HoloLens 2. 
> 
> se você incluir o ARM e o ARM64 em seu pacote, a versão do ARM64 será a usada no HoloLens 2. 

>[!NOTE]
> Você pode declarar um único pacote para ser aplicável a várias famílias de dispositivos de destino

## <a name="testing-your-app"></a>Testando seu aplicativo

### <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

quando você cria pacotes de aplicativos para enviar ao Partner Center por meio de Visual Studio, o assistente para criar pacotes de aplicativos solicita que você execute o Kit de certificação de aplicativo Windows nos pacotes que são criados. para ter um processo de envio suave para a loja, é melhor verificar se a cópia local do seu aplicativo passa os [testes do Kit de certificação de aplicativo Windows](/previous-versions/windows/apps/jj657973(v=win.10)) antes de enviá-los para a loja. atualmente, não há suporte para a execução do Kit de certificação de aplicativo Windows em um HoloLens remoto.

### <a name="run-on-all-targeted-device-families"></a>Executar em todas as famílias de dispositivos de destino

a plataforma Universal Windows permite que você crie um único aplicativo que é executado em todas as famílias de dispositivos Windows 10. no entanto, ele não garante que os aplicativos de Windows Universal só funcionarão em todas as famílias de dispositivos. É importante [testar seu aplicativo](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) em cada uma de suas famílias de dispositivos escolhidas para garantir uma boa experiência.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Enviando seu aplicativo de realidade misturada para a loja

Se você estiver enviando um aplicativo de realidade misturada baseado em um projeto do Unity, consulte este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) primeiro.

em geral, o envio de um aplicativo Windows Mixed Reality que funciona em headsets HoloLens ou de imersão é como o envio de qualquer aplicativo UWP para o Microsoft Store. Depois de [criar seu aplicativo reservando seu nome](/windows/uwp/publish/create-your-app-by-reserving-a-name), siga a lista de [verificação de envio do UWP](/windows/uwp/publish/app-submissions).

Uma das primeiras coisas que você fará é [selecionar uma categoria e uma subcategoria](/windows/uwp/publish/category-and-subcategory-table) para sua experiência de realidade mista. É importante que você **escolha a categoria mais precisa para seu aplicativo**. As categorias ajudam a proteger seu aplicativo nas categorias de armazenamento corretas e a garantir que ele apareça usando consultas de pesquisa relevantes. **Listar seu título VR como um jogo não resultará em melhor exposição para seu aplicativo** e poderá impedi-lo de aparecer em categorias que estão mais ajustadas e menos lotadas.

No entanto, há quatro áreas principais no processo de envio, em que você desejará fazer seleções mistas específicas da realidade:
1. Na seção **[declarações de produto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** em [Propriedades](/windows/uwp/publish/enter-app-properties).
2. Na seção **[requisitos do sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** , em [Propriedades](/windows/uwp/publish/enter-app-properties).
3. Na seção **[disponibilidade da família de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** , em [pacotes](/windows/uwp/publish/upload-app-packages).
4. Em vários campos da **[página de listagem de armazenamento](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Declarações de produto da realidade misturada

Na página **[Propriedades](/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[declarações de produto](/windows/uwp/publish/app-declarations)** .

![Declarações de produto da realidade misturada](images/product-declarations-900px.png)<br>
Declarações de produto da realidade misturada

Primeiro, você precisa identificar os tipos de dispositivo para os quais seu aplicativo oferece uma experiência de realidade mista. identificar tipos de dispositivo garante que seu aplicativo esteja incluído em coleções de Windows Mixed Reality na loja.

ao lado de "esta experiência foi projetada para Windows Mixed Reality em:"
* Marque a caixa **PC** se seu aplicativo oferecer uma experiência VR quando um headset de imersão estiver conectado ao PC do usuário. É recomendável marcar essa caixa se seu aplicativo estiver definido para ser executado exclusivamente em um headset de imersão ou se for um jogo de PC padrão ou um aplicativo que ofereça um modo de realidade misturada ou conteúdo de bônus quando um headset estiver conectado.
* marque a caixa de **HoloLens** somente se seu aplicativo oferecer uma experiência holographic quando for executado em HoloLens.
* Marque **ambas as** caixas se seu aplicativo oferecer uma experiência de realidade mista em ambos os tipos de dispositivo.

Se você selecionou "PC" acima, convém definir a "configuração de realidade mista" (nível de atividade). isso se aplica somente a experiências de realidade misturadas que são executadas em computadores conectados a headsets de imersão, como aplicativos de realidade misturados em HoloLens são de escala mundial e o usuário não define um limite durante a instalação.
* Escolha **encaixar + posição** se você tiver projetado seu aplicativo para que o usuário permaneça em uma posição. Por exemplo, em um jogo em que você está no controle de uma ferramenta cockpit de aeronave.
* Escolha **todas as experiências** se seu aplicativo for projetado com a intenção que o usuário percorre dentro de um limite definido definido durante a instalação. Por exemplo, pode ser um jogo no qual você passo a lado e o pato para ataques de subexposição.

### <a name="mixed-reality-system-requirements"></a>Requisitos de sistema de realidade misturada

Na página **[Propriedades](/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[requisitos do sistema](/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisitos do sistema](images/system-reqs-800px.png)<br>
Requisitos de sistema

Nesta seção, você identificará o hardware mínimo (necessário) e o hardware recomendado (opcional) para seu aplicativo de realidade misturada.

**Hardware de entrada:**

Use as caixas de seleção para informar aos clientes potenciais se seu aplicativo dá suporte a **microfone** para [entrada de voz](../design/voice-input.md)), **[controlador Xbox ou gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)** ou **[Windows Mixed Reality controladores de movimento](../design/motion-controllers.md)**. Essas informações serão apresentadas na página de detalhes do produto do aplicativo na loja e ajudarão seu aplicativo a ser incluído nas coleções de jogos/aplicativos apropriadas. Por exemplo, pode haver uma coleção para todos os jogos que dão suporte a controladores de movimento.

Tenha em consideração a seleção de caixas de seleção para "hardware mínimo" ou "hardware recomendado" para tipos de entrada. 

Por exemplo: 
* se seu jogo exigir controladores de movimento, mas aceitar entrada de voz via microfone, marque a caixa de seleção "hardware mínimo" ao lado de "Windows Mixed Reality controladores de movimento", mas a caixa de seleção "hardware recomendado" ao lado de "microfone". 
* se o jogo puder ser reproduzido com um controlador Xbox, gamepad ou controladores de movimento, você poderá marcar a caixa de seleção "hardware mínimo" ao lado de "controlador xbox ou gamepad" e selecionar a caixa de seleção "hardware recomendado" ao lado de "controladores de movimento de Windows Mixed Reality", já que os controladores de movimento provavelmente oferecerão um passo em diante na experiência do gamepad.

**Windows Mixed Reality headsets de imersão:**

Indicando se um headset de imersão é necessário para usar seu aplicativo, ou é opcional, é essencial para a satisfação e a educação do cliente.

se seu aplicativo *só* puder ser usado por meio de um headset de imersão, marque a caixa de seleção "mínimo de hardware" ao lado de "Windows Mixed Reality fone de ouvido". Isso será exibido na página de detalhes do produto do aplicativo no repositório como um aviso acima do botão comprar para que os clientes não achem que estão comprando um aplicativo que funcionará em seu PC, como um aplicativo de desktop tradicional.

se seu aplicativo for executado na área de trabalho como um aplicativo de PC tradicional, mas oferecer uma experiência VR quando um headset de imersão estiver conectado (se o conteúdo completo do seu aplicativo estiver disponível ou apenas uma parte), marque a caixa de seleção "hardware recomendado" ao lado de "Windows Mixed Reality headset". Nenhum aviso será exibido acima do botão comprar na página de detalhes do produto do aplicativo se seu aplicativo funcionar como um aplicativo de área de trabalho tradicional sem um headset de imersão conectado.

**Especificações do PC:**

se você quiser que seu aplicativo alcance o máximo possível Windows Mixed Reality usuários de headsets de imersão, [direcione](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) as especificações do PC para [Windows Mixed Reality PCs com gráficos integrados](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

se o seu aplicativo de realidade misturada tem como alvo os requisitos mínimos de Windows Mixed Reality pc ou precisa de uma configuração de pc específica como a GPU dedicada de um [Windows Mixed Reality Ultra PC] ( https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines , você deve adicionar as especificações relevantes do pc na coluna "hardware mínimo".

Se o seu aplicativo de realidade misturada for projetado para melhorar o desempenho ou oferecer gráficos de resolução mais alta em uma configuração de PC ou placa gráfica específica, você deverá incluir as especificações relevantes do PC na coluna "hardware recomendado".

Isso só se aplica se o seu aplicativo de realidade misturada usar um headset de imersão conectado a um PC. se seu aplicativo de realidade misturada só for executado em HoloLens, você não precisará indicar as especificações do PC, pois HoloLens tem apenas uma configuração de hardware.

### <a name="device-family-availability"></a>Disponibilidade da família de dispositivos

se você tiver [empacotado seu aplicativo corretamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) no Visual Studio, carregá-lo na página pacotes deve produzir uma tabela com as famílias de dispositivos disponíveis.

![Tabela de disponibilidade da família de dispositivos](images/device-family-table-900px.png)<br>
Tabela de disponibilidade da família de dispositivos

se o seu aplicativo de realidade misturada funcionar em headsets de imersão, pelo menos "Windows 10 área de trabalho" deve ser selecionado na tabela. se o seu aplicativo de realidade misturada funcionar em HoloLens, pelo menos "Windows 10 Holographic" deverá ser selecionado. se seu aplicativo for executado em ambos os tipos de Windows Mixed Reality headset, "Windows 10 área de trabalho" e "Windows 10 Holographic" devem ser selecionados.

>[!TIP]
>Muitos desenvolvedores se deparam com erros ao carregar o pacote do aplicativo relacionado a incompatibilidades entre o manifesto do pacote e as informações de sua conta de aplicativo/Publicador no Partner Center. esses erros geralmente podem ser evitados entrando em Visual Studio com a mesma conta associada à sua conta de desenvolvedor de Windows (aquela que você usa para entrar no Partner Center). se você usar a mesma conta, poderá associar seu aplicativo à sua identidade no Microsoft Store antes de empacotá-lo.

![Associar seu aplicativo ao Microsoft Store](images/associate-your-app-700px.png)<br>
associe seu aplicativo ao Microsoft Store no Visual Studio

### <a name="store-listing-page"></a>Página de listagem de armazenamento

Na página de [listagem de armazenamento](/windows/uwp/publish/create-app-store-listings) do processo de envio de aplicativo, há vários lugares em que você pode adicionar informações úteis sobre seu aplicativo de realidade misturada.

>[!IMPORTANT]
>para garantir que seu aplicativo seja categorizado corretamente pela loja e tornar-se detectável para Windows Mixed Reality clientes, você deve adicionar **"Windows Mixed Reality"** como um dos seus "termos de pesquisa" para o aplicativo (você pode encontrar termos de pesquisa expandindo a seção "campos compartilhados").

![adicionar Windows Mixed Reality aos termos de pesquisa](images/search-terms-800px.png)<br>
adicionar "Windows Mixed Reality" aos termos de pesquisa

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Oferecendo uma avaliação gratuita para seu jogo ou aplicativo

em muitos casos, seus consumidores terão se limitado a nenhuma experiência com a realidade virtual antes de comprar um Windows Mixed Reality headsets de imersão. Eles podem não saber o que esperar de jogos intensos ou estar familiarizados com seu próprio limite de conforto em experiências de imersão. muitos clientes também podem experimentar um Windows Mixed Reality headset de imersão em computadores que não são crachás como [Windows Mixed Reality PCs](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Devido a essas considerações, é altamente recomendável que você considere a possibilidade de oferecer uma [avaliação gratuita](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para seu aplicativo de realidade mista ou jogo pago.

## <a name="see-also"></a>Confira também
* [O que é Realidade Misturada?](../discover/mixed-reality.md)
* [Visão geral do desenvolvimento](../develop/development.md)
* [Modos de exibição do aplicativo](../design/app-views.md)
* [Entendendo o desempenho da realidade misturada](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Como testar seu aplicativo no HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [diretrizes mínimas de compatibilidade de hardware do PC Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)