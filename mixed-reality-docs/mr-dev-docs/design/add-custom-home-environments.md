---
title: Projete seus próprios ambientes de imersão
description: Saiba como criar ambientes de início de realidade mista do Windows.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, Home, ambientes personalizados, lugares, Cliff House, skyloft, usuário, criar, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade mista
ms.openlocfilehash: ca6a41f8388a767b1191ddc3b377822567a603a6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583302"
---
# <a name="design-your-own-immersive-environments"></a>Projete seus próprios ambientes de imersão

>[!NOTE]
>Esse é um recurso experimental. Experimente e divirta-se com ele, mas não se surpreenda se tudo não funcionar tão bem quanto o esperado. Estamos avaliando a viabilidade desse recurso e interesse em usá-lo, portanto, conte-nos sobre sua experiência (e quaisquer bugs que você encontrar) nos [fóruns de desenvolvedores](https://forums.hololens.com/categories/custom-home-environments).

A partir da [atualização do Windows 10 de abril de 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), habilitamos um recurso experimental que permite adicionar ambientes personalizados ao seletor de locais (no menu Iniciar) para usar como a [página inicial do Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md). O Windows Mixed Reality tem dois ambientes padrão, Cliff House e Skyloft, que você pode escolher como sua casa. A criação de ambientes personalizados permite expandir a lista com suas próprias criações. Estamos disponibilizando esse recurso em um estado inicial para avaliar os juros de criadores e desenvolvedores. Veja que tipos de mundos você cria e entende como você trabalha com diferentes ferramentas de criação.

Ao usar um ambiente personalizado, você observará que o teleportamento, a interação com os aplicativos e o posicionamento de hologramas funciona exatamente como no Cliff House e Skyloft. Você pode navegar na Web em um cenário de fantasia ou preencher uma cidade fractais com hologramas-as possibilidades são infinitas!

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Ambientes domésticos personalizados</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Experimentando um ambiente de exemplo

Criamos um ambiente de exemplo que mostra algumas das possibilidades criativas de ambientes domésticos personalizados. Siga estas etapas para experimentar:
1. [Baixe nosso ambiente de ilha de fantasia de exemplo](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (pontos de link para o executável de extração automática).

    ![Ambiente de exemplo da ilha de fantasia](images/FantasyLand.jpg)<br>
    *Ambiente de exemplo da ilha de fantasia*<br>

2. Execute o arquivo de **Fantasy_Island.exe** que você baixou.

    > [!NOTE]
    > Ao tentar executar um arquivo. exe baixado da Web (como este), você pode encontrar um pop-up "protegido pelo Windows". Para executar Fantasy_Island.exe a partir desse pop-up, selecione **mais informações** e, em seguida, **executar mesmo assim**. Essa configuração de segurança destina-se a protegê-lo de baixar arquivos que talvez você não queira confiar, portanto, escolha apenas essa opção ao confiar na origem do arquivo.

3. Abra o **Explorador de arquivos** e navegue até a pasta ambientes colando o seguinte local de arquivo na barra de endereços: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .
4. Copie o ambiente de exemplo que você baixou para essa pasta.
5. Reinicie o **portal de realidade misturada** para atualizar a lista de ambientes no seletor de locais.
6. Coloque seu headset. Quando estiver em casa, abra o **menu iniciar** usando o botão do Windows seu controlador.
7. Selecione o ícone **locais** acima da lista de aplicativos fixados para escolher um ambiente doméstico.
8. Você encontrará o ambiente da ilha de fantasia que baixou na lista de locais. Selecione **ilha de fantasia** para entrar no seu novo ambiente doméstico personalizado!

## <a name="creating-your-own-custom-environment"></a>Criando seu próprio ambiente personalizado

Além de usar nossos ambientes de exemplo, você pode exportar seus próprios ambientes personalizados usando seu software de edição de 3D favorito. 

### <a name="modeling-guidelines"></a>Diretrizes de modelagem

Ao modelar seu ambiente, mantenha as seguintes recomendações em mente para que os usuários sejam gerados na orientação correta em um mundo believably:

1. Os usuários irão gerar em 0, 0, 0 portanto, centralizar o local de geração em relação à origem.
2. As unidades de trabalho devem ser definidas como medidores para que os ativos possam ser criados em escala mundial.
3. O eixo para cima deve ser definido como "Y".
4. O ativo deve enfrentar "encaminhar" em direção ao eixo Z positivo.
5. Você não precisa combinar todas as malhas, mas é recomendável se você estiver direcionando dispositivos com restrição de recursos.

### <a name="exporting-your-environment"></a>Exportando seu ambiente

A realidade mista do Windows depende do glTF binário (. glb) como o formato de entrega de ativos para ambientes. glTF é um padrão aberto isento de royalties para entrega de ativos 3D mantido pelo grupo Khronos. O suporte da Microsoft para o formato em aplicativos e experiências do Windows crescerá conforme o glTF evolui como um padrão da indústria para conteúdo 3D interoperável.

A primeira etapa na exportação de ativos a serem usados como ambientes domésticos personalizados é gerar um modelo glTF 2,0. O grupo de trabalho glTF mantém uma [lista de exportadores e conversores com suporte](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) para criar um modelo glTF 2,0. Para começar, use um dos programas listados nesta página para criar e exportar um modelo do glTF 2,0 ou Converta um modelo existente usando um dos conversores com suporte.

Além disso, confira [este artigo útil, que fornece uma visão geral de um fluxo de trabalho de arte para exportar modelos glTF do Blender e do 3DS Max diretamente. 

### <a name="environment-limits"></a>Limites de ambiente

Todos os ambientes devem ser < 256 MB. Ambientes maiores que 256 MBS não serão carregados e recorrerão a um mundo vazio com apenas o Skybox padrão em torno do usuário. Mantenha esse limite de tamanho de arquivo em mente ao criar seus modelos. Além disso, se você planeja otimizar seu ambiente usando o WindowsMRAssetConverter conforme descrito abaixo, seja Cognizant que o tamanho da textura aumentará conforme o otimizador cria texturas com um tamanho de arquivo maior, mas carregam mais rapidamente. 

### <a name="optimizing-your-environment"></a>Otimizando seu ambiente

O Windows Mixed Reality dá suporte a muitas otimizações opcionais que podem reduzir significativamente os tempos de carregamento do ambiente. Preste atenção especial com ambientes que têm muitas texturas, pois às vezes eles atingirão o tempo limite durante o carregamento. Em geral, recomendamos esta etapa para todos os ativos, no entanto, ambientes menores com poucas ou mais texturas de resolução nem sempre exigirão isso. 

Para facilitar esse processo, criamos o conversor de [ativos do Windows Mixed Reality (disponível no GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) para fazer suas otimizações. Essa ferramenta usa um conjunto de utilitários disponíveis no Microsoft glTF Toolkit para otimizar qualquer padrão 2,0 glTF ou. glb executando um empacotamento de textura extra, compactação e resolução vertical. 

Atualmente, o conversor dá suporte a vários sinalizadores para ajustar o comportamento exato das otimizações. Recomendamos a execução com os seguintes sinalizadores para obter os melhores resultados:

Sinalizador|Valor (es) recomendado (s)|Descrição
---|---|---
-Max-Texture-size|1024 ou 2048| Ajuste o valor para melhorar a qualidade das texturas, o padrão é 512x512. Um valor maior afetará significativamente o tamanho do arquivo do ambiente para manter o limite de 256 MB em mente
-min-versão|1803|Há suporte para ambientes personalizados apenas em versões do Windows >= 1803. Esse sinalizador removerá texturas de versões mais antigas e reduzirá o tamanho do arquivo do ativo final

Por exemplo:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Testando seu ambiente

Depois de ter seu ambiente. glb final, você estará pronto para testá-lo no headset. Comece na etapa 2 na seção ["experimentando um ambiente de exemplo"](#trying-a-sample-environment) para usar seu ambiente personalizado como a casa de realidade misturada. 

## <a name="sending-feedback"></a>Como enviar comentários

Enquanto estamos avaliando esse recurso experimental, estamos interessados em aprender como você está usando ambientes personalizados, todos os bugs que você pode encontrar e como gosta o recurso. Compartilhe comentários para criar e usar ambientes domésticos personalizados nos [fóruns de desenvolvedores](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Solução de problemas e dicas

### <a name="how-do-i-change-the-name-of-the-environment"></a>Como fazer alterar o nome do ambiente?

O nome do arquivo na pasta ambientes será usado no seletor de locais. Para alterar o nome do seu ambiente, renomeie o nome do arquivo de ambiente e reinicie o portal de realidade misturada.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Como fazer remover ambientes personalizados do meu seletor de locais?

Para remover um ambiente personalizado, abra a pasta ambientes no seu computador ( `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ) e exclua o ambiente. Depois de reiniciar o portal de realidade misturada, esse ambiente não aparecerá mais no seletor de locais. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Como fazer o padrão para meu ambiente personalizado favorito?

No momento, não é possível alterar o ambiente padrão. Sempre que reiniciar o portal de realidade misturada, você será devolvido ao ambiente da casa Cliff. 

### <a name="i-spawn-into-a-blank-space"></a>Eu faço uma geração em um espaço em branco

A realidade mista do Windows [não dá suporte a ambientes que excedem 256 MB](#environment-limits). Quando um ambiente excede esse limite, você vai para a caixa céu vazia sem modelo.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Leva muito tempo para carregar meu ambiente

Você pode adicionar otimizações opcionais ao seu ambiente para que ele seja carregado mais rapidamente. Consulte ["Otimizando seu ambiente"](#optimizing-your-environment) para obter detalhes.

### <a name="the-scale-of-my-environment-is-incorrect"></a>A escala do meu ambiente está incorreta

A realidade mista do Windows traduz as unidades de glTF para 1 medidor ao carregar ambientes. Se seu ambiente carregar uma escala inesperada, verifique novamente seu exportador para garantir que você esteja modelando em uma escala de 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>O local de geração no meu ambiente está incorreto

O local de geração padrão está localizado em 0, 0, 0 no ambiente. No momento, não é possível personalizar esse local, portanto, você deve modificar o ponto de geração exportando seu ambiente com a origem posicionada no ponto de geração desejado.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>O áudio não parece correto no ambiente

Quando você cria seu ambiente personalizado, ele usará uma simulação de renderização acústica que não corresponde ao espaço físico que você criou. O som pode vir de direções erradas e pode parecer muffled. 

## <a name="see-also"></a>Confira também
* [Conversor de ativos da realidade mista do Windows (no GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)