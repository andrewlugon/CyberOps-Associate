# Segurança do Windows

### Comando netstat

Quando o malware está presente em um computador, ele geralmente abre portas de comunicação no host para enviar e receber dados. O comando **netstat** pode ser usado para procurar conexões de entrada ou saída que não estão autorizadas. Quando usado por conta própria, o comando **netstat** exibirá todas as conexões TCP ativas.

Examinando essas conexões, é possível determinar quais dos programas estão escutando conexões que não estão autorizadas. Quando um programa é suspeito de ser malware, uma pequena pesquisa pode ser realizada para determinar sua legitimidade. A partir daí, o processo pode ser encerrado com o Gerenciador de Tarefas, e o software de remoção de malware pode ser usado para limpar o computador.

Para facilitar esse processo, você pode vincular as conexões aos processos em execução que as criaram no Gerenciador de Tarefas. Para fazer isso, abra um prompt de comando com privilégios administrativos e digite o comando **netstat -abno**

**bservação**: Se você não estiver no modo administrador, uma mensagem “A operação solicitada requer elevação” será exibida. Pesquise Prompt de Comando. Clique com o botão direito do mouse em **Prompt de comando** e escolha **Executar como administrador.**

Examinando as conexões TCP ativas, um analista deve ser capaz de determinar se há algum programa suspeito que esteja escutando conexões de entrada no host. Você também pode rastrear esse processo para o Gerenciador de Tarefas do Windows e cancelar o processo. Pode haver mais de um processo listado com o mesmo nome. Se este for o caso, use o PID para encontrar o processo correto. Cada processo em execução no computador tem um PID exclusivo. Para exibir os PIDs dos processos no Gerenciador de Tarefas, abra o **Gerenciador de Tarefas**, clique com o botão direito do mouse no cabeçalho da tabela e selecione **PID**.

### Visualizador de Eventos

O Visualizador de Eventos do Windows registra o histórico de eventos de aplicativos, segurança e sistema. Esses arquivos de log são uma valiosa ferramenta de solução de problemas porque fornecem informações para identificar um problema. Para abrir o Visualizador de Eventos, procure-o e clique no ícone do programa

O Windows inclui duas categorias de logs de eventos: Logs do Windows e Logs de Aplicativos e Serviços. Cada uma dessas categorias tem vários tipos de log. Os eventos exibidos nesses logs têm um nível: informações, aviso, erro ou crítico. Eles também têm a data e hora em que o evento ocorreu, juntamente com a origem do evento e um ID que se relaciona com esse tipo de evento.

Também é possível criar uma visualização personalizada. Isso é útil ao procurar certos tipos de eventos, encontrar eventos que aconteceram durante um determinado período de tempo, exibir eventos de um determinado nível e muitos outros critérios. Há uma exibição personalizada interna chamada Eventos administrativos que mostra todos os eventos críticos, de erro e de aviso de todos os logs administrativos. Esta é uma boa visão para começar ao tentar solucionar um problema.

Os logs de eventos de segurança são encontrados em Logs do Windows. Eles usam IDs de evento para identificar o tipo de evento.

### Configurações do Windows Update

Nenhum software é perfeito e o sistema operacional Windows não é exceção. Os invasores estão constantemente criando novas maneiras de comprometer computadores e explorar códigos ruins. Alguns desses ataques vêm tão rapidamente que as defesas contra eles ainda não foram criadas e distribuídas. Estes são chamados de ataque de dia zero. Microsoft e desenvolvedores de software de segurança estão sempre tentando ficar à frente dos atacantes, mas eles nem sempre são bem-sucedidos. Para garantir o mais alto nível de proteção contra esses ataques, certifique-se sempre de que o Windows está atualizado com os service packs e patches de segurança mais recentes.

Os patches são atualizações de código que os fabricantes fornecem para evitar que um vírus ou um worm recém-descoberto façam um ataque bem-sucedido. De tempos em tempos, os fabricantes combinam patches e atualizações em uma aplicação completa de atualização chamada de service pack. Muitos ataques devastadores de vírus poderiam ter sido muito menos graves, se mais usuários tivessem baixado e instalado o service pack mais recente. É altamente desejável que as empresas utilizem sistemas que distribuam, instalam e rastreiam automaticamente as atualizações de segurança.

O Windows verifica, regularmente, o site Windows Update, por atualizações de alta prioridade e que podem ajudar a proteger o computador contra as mais recentes ameaças de segurança. Essas atualizações incluem atualizações de segurança, atualizações críticas e service packs. Dependendo da configuração escolhida, o Windows baixa e instala, automaticamente, todas as atualizações de alta prioridade que o computador precisar, ou notifica o usuário, conforme essas atualizações estiverem disponíveis. Para configurar as configurações da atualização do Windows, procure o Windows Update e clique no aplicativo.

Há também configurações para as horas em que o computador não será reiniciado automaticamente, por exemplo, durante o horário comercial regular. Você também pode escolher quando reiniciar o computador após uma atualização, se necessário, com as opções Reiniciar. Opções avançadas também estão disponíveis para escolher como as atualizações são instaladas como outros produtos da Microsoft são atualizados.

### Ferramenta de Política de Segurança Local

Uma política de segurança é um conjunto de objetivos que garante a segurança de uma rede, dos dados e dos sistemas de computador em uma organização. A política de segurança é um documento em constante desenvolvimento, baseado em mudanças na tecnologia, nos negócios e nas necessidades dos funcionários.

Na maioria das redes que usam computadores Windows, o Active Directory é configurado com domínios em um servidor Windows. Computadores Windows ingressam no domínio. O administrador configura uma Política de Segurança de Domínio que se aplica a todos os computadores que ingressam no domínio. As políticas de conta são definidas automaticamente quando um usuário efetua login em um computador que é membro de um domínio. A Política de Segurança Local do Windows, mostrada na figura, pode ser usada para computadores autônomos que não fazem parte de um domínio do Active Directory. Para abrir o aplicativo Política de Segurança Local, procure Política de Segurança Local e clique no programa.
![[Pasted image 20241217192751.png]]

As diretrizes de senha são um componente importante de uma política de segurança. Qualquer usuário que fizer logon em um computador ou se conectar a um recurso de rede deve ter uma senha. As senhas ajudam a evitar roubo de dados e atos mal-intencionados. As senhas também ajudam a confirmar se o registro de eventos é válido, garantindo que o usuário seja quem diz ser. Na Política de Segurança Local, a Política de Senha é encontrada em Políticas de Conta e define os critérios para as senhas para todos os utilizadores no computador local.

Use a Diretiva de Bloqueio de Conta em Diretivas de Conta, para impedir tentativas de login por força bruta. Por exemplo, você pode definir a política para permitir que o usuário insira um nome de usuário e / ou senha incorretos cinco vezes. Após cinco tentativas, a conta é bloqueada por 30 minutos. Depois de 30 minutos, o número de tentativas é redefinido para zero e o usuário pode tentar entrar novamente.

É importante garantir que os computadores estejam seguros, quando os usuários estiverem ausentes. Uma política de segurança deve conter uma regra sobre a necessidade de se bloquear um computador, quando a proteção de tela for iniciada. Isso garantirá que, depois de um curto período de tempo longe do computador, a proteção de tela será iniciada e o computador não poderá ser usado, até que o usuário faça login novamente.

Se a política de segurança local em cada computador autônomo for a mesma, use o recurso Exportar política. Salve a diretiva com um nome, como workstation.inf. Copie o arquivo de política para uma mídia externa ou unidade de rede para usar em outros computadores independentes. Isso é particularmente útil quando o administrador precisa configurar diretivas locais abrangentes para direitos de usuário e opções de segurança.

O miniaplicativo Diretiva de Segurança Local contém muitas outras configurações de segurança que se aplicam especificamente ao computador local. Você pode configurar Direitos de Usuário, Regras de Firewall e até mesmo a capacidade de restringir os arquivos que os usuários ou grupos têm permissão para executar com o AppLocker.

### Windows Defender

Malware inclui vírus, worms, cavalos de Troia, keyloggers, spyware, e adware. Eles são projetados para invadir a privacidade, roubar informações, danificar o computador ou corromper dados. É importante que você proteja os computadores e dispositivos móveis com software antimalware de qualidade. Os seguintes tipos de programas antimalware estão disponíveis:

- **Proteção antivírus** - Este programa monitora continuamente a existência de vírus. Quando um vírus é detectado, o usuário é avisado e o programa tenta colocar o vírus em quarentena ou excluí-lo.
- **Proteção de adware** - Este programa procura continuamente programas que exibem anúncios em seu computador.
- **Proteção contra phishing** - este programa bloqueia os endereços IP de sites de phishing conhecidos e avisa o usuário sobre sites suspeitos.
- **Proteção contra spyware** - este programa verifica a existência de keyloggers e outros spywares.
- **Fontes confiáveis / não confiáveis** - Este programa avisa sobre programas inseguros prestes a serem instalados ou sites inseguros antes de serem visitados.

Pode ser necessário usar vários programas diferentes e fazer várias varreduras para remover completamente todos os softwares mal-intencionados. Execute apenas um programa de proteção contra malware por vez.

Várias empresas de segurança confiáveis, como McAfee, Symantec e Kaspersky, oferecem proteção completa contra malware para computadores e dispositivos móveis. O Windows possui proteção interna contra vírus e spyware chamada Windows Defender, como mostrado na figura. O Windows Defender está ativado por padrão para fornecer proteção em tempo real contra infecções.

Para abrir o Windows Defender, procure-o e clique no programa. Embora o Windows Defender funcione em segundo plano, você pode executar varreduras manuais do computador e dispositivos de armazenamento. Você também pode atualizar manualmente as definições de vírus e spyware na guia **Atualizar**. Além disso, para ver todos os itens encontrados durante varreduras anteriores, clique na guia **Histórico**.

### Firewall do Windows Defender

Um firewall nega, seletivamente, o tráfego a um computador ou a um segmento de rede. Os firewalls trabalham, geralmente, abrindo e fechando as portas usadas por vários aplicativos. Ao abrir apenas as portas necessárias em um firewall, você está implementando uma política de segurança restritiva. Qualquer pacote não explicitamente permitido é negado. Ao contrário, uma política de segurança permissiva permite acesso por todas as portas, exceto aquelas explicitamente negadas. Antigamente, software e hardware eram enviados com configurações permissivas. Como os usuários negligenciavam a configuração do equipamento, as configurações permissivas padrão deixavam muitos dispositivos expostos a invasores. Agora, a maioria dos dispositivos é enviada com configurações o mais restritivas possível, mesmo que permitindo ainda uma configuração fácil.

Para permitir o acesso ao programa através do Firewall do Windows Defender, procure por **Painéis de Controle**. Em **Sistemas e Segurança**, localize o **Firewall do Windows Defender**. Clique em **Permitir um aplicativo ou recurso por meio do Firewall do Windows Defender**, conforme mostrado na figura.

Se desejar usar um firewall por software diferente, você precisará desativar o firewall do Windows. Para desativar o Firewall do Windows, clique em **Ativar ou desativar o Firewall do Windows.**

Muitas configurações adicionais podem ser encontradas em **Configurações avançadas**. Aqui você pode criar regras de tráfego de entrada ou saída com base em critérios diferentes. Você também pode importar e exportar políticas ou monitorar diferentes aspectos do firewall.