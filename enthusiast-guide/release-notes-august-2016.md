---
title: Notas sobre a versão – agosto de 2016
description: Mantenha-se atualizado sobre as notas HoloLens de lançamento do Windows 10 de Aniversário para o Fall 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de versão, sistema operacional, plataforma, recursos, pacote comercial
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202448"
---
# <a name="release-notes---august-2016"></a>Notas sobre a versão – agosto de 2016

A HoloLens está escutando comentários dos desenvolvedores no Windows Programa Insider priorizar nosso trabalho. Continue nos [dando comentários por](/windows/mixed-reality/give-us-feedback) meio do Hub de Comentários, dos fóruns do [desenvolvedor](https://forums.hololens.com) e do Twitter por [meio do @HoloLens ](https://twitter.com/hololens). À medida Windows 10 a Atualização de Aniversário, a equipe HoloLens tem o prazer de melhorar ainda mais a experiência holográfica. Nesta atualização, nos concentramos em correções principais, melhorias e introdução de recursos solicitados por empresas e disponíveis no Microsoft HoloLens Commercial Suite.

**Versão mais recente:** Windows atualização de agosto de 2016 do Holographic (**10.0.14393.0**, Windows 10 de aniversário)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para [atualizar para a versão atual,](/windows/mixed-reality/updating-hololens)abra o aplicativo *Configurações,* acesse Atualizar & *Segurança* e, em seguida, selecione o botão Verificar se *há atualizações.*

## <a name="new-features"></a>Novos recursos

**Anexar para processar a depuração** HoloLens agora dá suporte à depuração anexar ao processo. Você pode usar Visual Studio Atualização 3 de 2015 para se conectar a um aplicativo em execução em um HoloLens e começar a [depurá-lo.](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app) Isso funciona sem a necessidade de implantar de um Visual Studio projeto.

**Atualização HoloLens Emulator** Também lançamos uma versão atualizada do HoloLens Emulator.

**Suporte ao Gamepad** Agora você pode emparelhar e usar Bluetooth gamepads com HoloLens! Os recursos do Xbox Wireless Controller S recém-lançados Bluetooth recursos e podem ser usados para reproduzir seus jogos e aplicativos favoritos habilitados para gamepad. Uma [atualização do controlador](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) deve ser aplicada antes que você possa conectar o Controlador Sem Fio do Xbox S ao HoloLens. O controlador sem fio do Xbox S é suportado pelo [XInput e](/windows/win32/xinput/xinput-game-controller-apis-portal) [Windows. APIs Gaming.Input.](/uwp/api/Windows.Gaming.Input) Você pode acessar mais Bluetooth de controladores por meio do [Windows. API Gaming.Input.](/uwp/api/Windows.Gaming.Input)

## <a name="improvements-and-fixes"></a>Aperfeiçoamentos e correções

Estamos em sincronia com o restante da atualização de aniversário do Windows 10, portanto, além das correções específicas do HoloLens, você também está recebendo todos os detalhes da atualização do Windows para aumentar a confiabilidade e o desempenho da plataforma. Seus comentários são altamente valiosos e priorizados para correções na versão.

Melhoramos as seguintes experiências:
* experiências de logoff.
* workplaces join.
* eficiência de energia para transições de estado de energia do dispositivo.
* estabilidade com Capturas de Realidade Misturada.
* confiabilidade para Bluetooth conectividade
* persistência de holograma no cenário de vários aplicativos.

Corrigimos os seguintes problemas:
* O Visual Studio perfil e o depurador de gráficos falham ao se conectar.
* fotos & documentos não aparecem no explorador de arquivos no portal do dispositivo.
* a Barra de Aplicativos pode piscar quando o cursor é colocado acima dele enquanto está no modo Ajuste.
* Quando estiver no modo Ajuste, o cursor do ponto de olhar será altere para o cursor de seta 4 um pouco mais lentamente.
* "Hey Cortana reproduzir música" não inicia Groove.
* após a atualização anterior, dizer "Ir para Casa" não exibe o painel de pinos corretamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introdução Microsoft HoloLens Commercial Suite

O Microsoft HoloLens Commercial Suite está pronto para implantação corporativa. Adicionamos vários recursos comerciais altamente [solicitados de](/windows/mixed-reality/commercial-features) nossos primeiros parceiros de negócios.

Entre em contato com o conta Microsoft local para comprar o Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Principais recursos comerciais 

* **Modo de quiosque.** Com HoloLens de quiosque, você pode limitar quais aplicativos executar para habilitar experiências de demonstração ou demonstração.<br>
  ![Com o modo de quiosque, HoloLens é lançado diretamente no aplicativo de sua escolha.](images/201608-kioskmode-400px.png)
* **MDM (Gerenciamento de Dispositivo Móvel) para HoloLens.** Seu departamento de TI pode gerenciar vários HoloLens simultaneamente usando soluções como Microsoft Intune. Você pode gerenciar configurações, selecionar aplicativos para instalar e definir configurações de segurança personalizadas de acordo com a necessidade da sua organização.<br>
  ![Os Gerenciamento de Dispositivos dispositivos móveis HoloLens o gerenciamento de dispositivos de nível empresarial em vários dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update para Empresas.** Atualizações controladas do sistema operacional para dispositivos e suporte para o branch de manutenção de longo prazo.
* **Segurança de dados.** A criptografia de dados do BitLocker está habilitada no HoloLens para fornecer o mesmo nível de proteção de segurança que qualquer outro dispositivo Windows.
* **Acesso corporativo.** Qualquer pessoa em sua organização pode se conectar remotamente à rede corporativa por meio da rede virtual privada em um HoloLens. O HoloLens também pode acessar redes Wi-Fi que exigem credenciais.
* **Microsoft Store para Empresas.** Seu departamento de IT também pode configurar um armazenamento privado corporativo, contendo apenas os aplicativos da sua empresa para seu uso HoloLens específico. Distribua os softwares corporativos com segurança ao grupo selecionado de usuários corporativos.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition vs. Commercial Suite

<table>
<tr>
<th>Recursos</th><th>Development Edition</th><th>Pacote Comercial</th>
</tr><tr>
<td>Criptografia do Dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>VPN (Rede Privada Virtual)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Modo de quiosque</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gerenciamento e implantação</th>
</tr><tr>
<td>Gerenciamento de Dispositivos Móveis (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidade de bloquear o cancelamento de registro</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acesso corporativo baseado em certificado Wi-Fi certificado</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Consumidor)</td><td style="text-align: center;">Consumidor</td><td style="text-align: center;">Filtragem por meio do MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Portal Comercial da Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Segurança e identidade</th>
</tr><tr>
<td>Fazer logo Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Fazer logoff com a MSA (Conta da Microsoft)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciais da Próxima Geração com desbloqueio de PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Inicialização segura</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Manutenção e suporte</th>
</tr><tr>
<td>Atualizações automáticas do sistema ao chegarem</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Branch de manutenção em longo prazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Problemas conhecidos do HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Recursos comerciais](/windows/mixed-reality/commercial-features)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Usando o emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)