# Configuração e monitoramento do Windows

### Executar como Administrador

Como prática recomendada de segurança, não é aconselhável fazer logon no Windows usando a conta de Administrador ou uma conta com privilégios administrativos. Isso ocorre porque qualquer programa que é executado enquanto conectado com esses privilégios herdará privilégios administrativos. O malware que tem privilégios administrativos tem acesso total a todos os arquivos e pastas no computador.

Às vezes, é necessário executar ou instalar software que requer os privilégios do Administrador. Para conseguir isso, existem duas maneiras diferentes de instalá-lo.

Administrador:
Clique com o botão direito no comando no Explorador de Arquivos do Windows e escolha Executar como Administrador no Menu de Contexto.

Prompt de comando administrador:
Procure **command**, clique com o botão direito do mouse no arquivo executável e escolha Executar como administrador no Menu de contexto. Cada comando executado a partir desta linha de comando será realizado com os privilégios de Administrador, incluindo a instalação de software.

### Usuários e Domínios Locais

Quando inicia um novo computador pela primeira vez ou instala o Windows, será pedido para criar uma conta de usuário. Isso é conhecido como um usuário local. Essa conta conterá todas as configurações de personalização, permissões de acesso, locais de arquivos e muitos outros dados específicos do usuário. Há também duas outras contas presentes, o convidado e o administrador. Ambas as contas são desabilitadas por padrão.

Como prática recomendada de segurança, não habilite a conta Administrador e não conceda privilégios administrativos aos usuários padrão. Se um usuário precisar executar qualquer função que exija privilégios administrativos, o sistema solicitará a senha de Administrador e permitirá que somente essa tarefa seja executada como administrador. Exigir a senha de administrador protege o computador impedindo que qualquer software não autorizado instale, execute ou acesse arquivos.

A conta Convidados não deve ser ativada. A conta de convidado não tem uma senha associada a ela porque é criada quando um computador vai ser usado por muitas pessoas diferentes que não têm contas no computador. Cada vez que a conta de convidado faz logon, um ambiente padrão é fornecido a eles com privilégios limitados.

Para facilitar a administração de usuários, o Windows usa grupos. Um grupo terá um nome e um conjunto específico de permissões associadas a ele. Quando um usuário é colocado em um grupo, as permissões desse grupo são dadas a esse usuário. Um usuário pode ser colocado em vários grupos para ser fornecido com muitas permissões diferentes. Quando as permissões se sobrepõem, certas permissões, como “negar explicitamente”, substituirão a permissão fornecida por um grupo diferente. Há muitos grupos de usuários diferentes incorporados no Windows que são usados para tarefas específicas. Por exemplo, o grupo Usuários do Log de Desempenho permite que os membros agendem o log de contadores de desempenho e coletem logs localmente ou remotamente. Os usuários e grupos locais são gerenciados com o miniaplicativo do **lusrmgr.msc** painel de controle

Além dos grupos, o Windows também pode usar domínios para definir permissões. Um domínio é um tipo de serviço de rede onde todos os usuários, grupos, computadores, periféricos e configurações de segurança são armazenados e controlados por um banco de dados. Este banco de dados é armazenado em computadores especiais ou grupos de computadores chamados controladores de domínio (DCs). Cada utilizador e computador no domínio tem de autenticar contra o controlador de domínio para iniciar sessão e acessar os recursos de rede. As configurações de segurança para cada usuário e cada computador são definidas pelo controlador de domínio para cada sessão. Qualquer configuração fornecida pelo controlador de domínio padrão para o computador local ou configuração de conta de usuário.

### CLI e PowerShell

A interface de linha de comando (CLI) do Windows pode ser usada para executar programas, navegar no sistema de arquivos e gerenciar arquivos e pastas. Além disso, arquivos chamados de batch podem ser criados para executar vários comandos sucessivamente, assim como um script básico.

Para abrir a CLI do Windows, procure **cmd.exe** e clique no programa. Lembre-se que clicar com o botão direito do mouse no programa oferece a opção de Executar como administrador, dando muito mais poder aos comandos que serão usados.

O prompt exibe o local atual dentro do sistema de arquivos. Estas são algumas coisas a serem lembradas ao usar a CLI:

- Os nomes de arquivo e caminhos não diferenciam maiúsculas de minúsculas, por padrão.
- Os dispositivos de armazenamento recebem uma letra para referência. A letra da unidade é seguida por dois pontos e barra invertida (). Isso indica a raiz, ou nível mais alto, do dispositivo. A hierarquia de pastas e arquivos no dispositivo é indicada separando-os com uma barra invertida. Por exemplo, o caminho C: \ Users \ Jim \ Desktop \ file.txt se refere a um arquivo chamado file.txt que está na pasta Desktop dentro da pasta Jim dentro da pasta Usuários na raiz da unidade C:.
- Comandos que têm opções opcionais usam a barra (/) para delinear entre o comando e a opção.
- Você pode usar a tecla **Tab** para completar automaticamente comandos quando diretórios ou arquivos são referenciados.
- O Windows mantém um histórico dos comandos inseridos durante uma sessão da CLI. Acesse comandos inseridos anteriormente usando as teclas de seta para cima e para baixo.
- Para alternar entre dispositivos de armazenamento, digite a letra do dispositivo, seguida de dois pontos e pressione **Enter**.

Mesmo que a CLI tenha muitos comandos e recursos, ela não pode funcionar em conjunto com o núcleo do Windows ou a GUI. Outro ambiente, chamado Windows PowerShell, pode ser usado para criar scripts para automatizar tarefas que a CLI normal não consegue criar. O PowerShell também fornece uma CLI para iniciar comandos. O PowerShell é um programa integrado no Windows e pode ser aberto pesquisando por “powershell” e clicando no programa. Assim como a CLI, o PowerShell também pode ser executado com privilégios administrativos.

Estes são os tipos de comandos que o PowerShell pode executar:

- **cmdlets** - Esses comandos executam uma ação e retornam uma saída ou objeto para o próximo comando que será executado.
- **Scripts do PowerShell** - São arquivos com uma extensão **.ps1** que contêm comandos do PowerShell executados.
- **Funções do PowerShell** - São partes de código que podem ser referenciadas em um script.

Para ver mais informações sobre o Windows PowerShell e começar a usá-lo, digite **help** no PowerShell

Há quatro níveis de ajuda no Windows PowerShell:

- **get-help** _PS command_ - Exibe a ajuda básica para um comando
- **get-help** _PS command_\ [_\ -examples_] - Exibe a ajuda básica para um comando com exemplos
- **get-help** _PS command_\ [_\ -detailed_] - Exibe ajuda detalhada para um comando com exemplos
- **get-help** _PS command_\ [_\ -full_] - Exibe todas as informações de ajuda de um comando com exemplos em maior profundidade

### Instrumentação de Gerenciamento do Windows

A Instrumentação de Gerenciamento do Windows (WMI) é usada para gerenciar computadores remotos. Ele pode recuperar informações sobre componentes de computador, estatísticas de hardware e software e monitorar a integridade de computadores remotos. Para abrir o controle WMI a partir do Painel de Controle, clique duas vezes em **Ferramentas Administrativas > Gerenciamento do Computador** para abrir a janela Gerenciamento do Computador, expanda a árvore **Serviços e Aplicativos** e clique com o botão direito do mouse no **ícone Controle WMI** **>** **Propriedades**.

Estas são as quatro guias na janela Propriedades de Controle WMI:

- **Geral** - Informações resumidas sobre o computador local e o WMI
- **Backup/Restore** - Permite backup manual de estatísticas coletadas pelo WMI
- **Segurança** - Configurações para configurar quem tem acesso a diferentes estatísticas WMI
- **Avançado** - Configurações para configurar o namespace padrão para WMI

Alguns ataques hoje usam o WMI para se conectar a sistemas remotos, modificar o registro e executar comandos. O WMI ajuda-os a evitar a detecção porque é tráfego comum, na maioria das vezes confiável pelos dispositivos de segurança de rede e os comandos WMI remotos geralmente não deixam evidências no host remoto. Devido a isso, o acesso WMI deve ser estritamente limitado.

### O comando net

O Windows tem muitos comandos que podem ser inseridos na linha de comando. Um comando importante é o comando **net**, que é usado na administração e manutenção do sistema operacional. O comando **net** suporta muitos subcomandos que seguem o comando **net** e podem ser combinados com opões para focar na saída específica.

Para ver uma lista de muitos comandos **net**, escreva **net help** na linha de comandos. A saída do comando mostra os comandos que o comando **net** pode usar. Para ver ajuda detalhada sobre qualquer um dos comandos net, digite C:\ > **net help**

A tabela lista alguns comandos **net** comuns.

![[Pasted image 20241217190333.png]]

### Gerenciador de tarefas e Monitor de recursos

Existem duas ferramentas muito importantes e úteis para ajudar um administrador a compreender os vários aplicativos, serviços e processos diferentes que estão sendo executados em um computador Windows. Essas ferramentas também fornecem informações sobre o desempenho do computador, como CPU, memória e uso da rede. Essas ferramentas são especialmente úteis ao investigar um problema em que o malware é suspeito. Quando um componente não está executando da maneira que deveria ser, essas ferramentas podem ser usadas para determinar qual o problema pode ser.

**Gerenciador de Tarefas**

O Gerenciador de Tarefas, que é mostrado na figura, fornece muitas informações sobre o software em execução e o desempenho geral do computador.

A tabela descreve as sete guias no Gerenciador de Tarefas.
![[Pasted image 20241217190533.png]]

**Monitor de recursos**

Quando forem necessárias informações mais detalhadas sobre o uso de recursos, você poderá usar o Monitor de Recursos.

Ao procurar o motivo pelo qual um computador pode estar agindo de forma irregular, o Monitor de Recursos pode ajudar a encontrar a origem do problema.

A tabela descreve as cinco guias do Monitor de Recursos.

![[Pasted image 20241217190616.png]]

### Redes

Um dos recursos mais importantes de qualquer sistema operacional é a capacidade do computador se conectar a uma rede. Sem esse recurso, não há acesso aos recursos de rede ou à internet. Para configurar as propriedades de rede do Windows e testar as configurações de rede, o Centro de Rede e Compartilhamento é usado. A maneira mais fácil de executar esta ferramenta é procurá-la e clicar nela. Use o Centro de Rede e Compartilhamento para verificar ou criar conexões de rede, configurar o compartilhamento de rede e alterar as configurações do adaptador de rede.

**Centro de Rede e Compartilhamento**

**Alterar as configurações do adaptador**

Para configurar um adaptador de rede, escolha **Alterar configurações do adaptador** no Centro de Rede e Compartilhamento para mostrar todas as conexões de rede disponíveis. Selecione o adaptador que você deseja configurar. Neste caso, alteramos um adaptador Ethernet para adquirir seu endereço IPv4 automaticamente da rede.

![[Pasted image 20241217190924.png]]
![[Pasted image 20241217190942.png]]
![[Pasted image 20241217190954.png]]

**nslookup and netstat**

O Sistema de Nomes de Domínio (DNS, Domain Name System) também deve ser testado porque é essencial encontrar o endereço dos hosts traduzindo-o a partir de um nome, como uma URL. Use o comando **nslookup** para testar o DNS. Digite **nslookup [cisco.com](http://cisco.com)** no prompt de comando para localizar o endereço do servidor Web Cisco. Quando o endereço é retornado, você sabe que o DNS está funcionando corretamente. Você também pode verificar quais portas estão abertas, onde elas estão conectadas e qual é seu status atual. Digite **netstat** na linha de comando para ver detalhes das conexões de rede ativas, conforme mostrado na saída do comando. O comando **netstat** será examinado mais adiante neste módulo.

### Acessando recursos de rede

Como outros sistemas operacionais, o Windows usa rede para muitos aplicativos diferentes, como serviços da Web, email e arquivos. Originalmente desenvolvido pela IBM, a Microsoft ajudou no desenvolvimento do protocolo SMB (Server Message Block) para compartilhar recursos de rede. O SMB é usado principalmente para acessar arquivos em hosts remotos. O formato UNC (Universal Naming Convention) é usado para se conectar a recursos, por exemplo:

**\\ nome_do_servidor\ nome_do_compartilhamento\arquivo**

No UNC, nome_do_servidor é o servidor que está hospedando o recurso. Pode ser um nome DNS, um nome NetBIOS ou simplesmente um endereço IP. O nome do compartilhamento é a raiz da pasta no sistema de arquivos no host remoto, enquanto o arquivo é o recurso que o host local está tentando encontrar. O arquivo pode estar mais profundo dentro do sistema de arquivos e essa hierarquia precisará ser indicada.

Ao compartilhar recursos na rede, a área do sistema de arquivos que será compartilhada precisará ser identificada. O controle de acesso pode ser aplicado às pastas e arquivos para restringir usuários e grupos a funções específicas, como ler, gravar ou negar. Há também compartilhamentos especiais que são criados automaticamente pelo Windows. Essas ações são chamadas de ações administrativas. Um compartilhamento administrativo é identificado pelo cifrão ($) que vem após o nome do compartilhamento. Cada volume de disco tem um compartilhamento administrativo, representado pela letra do volume e o $, como C$, D$ ou E$. A pasta de instalação do Windows é compartilhada como admin$, a pasta das impressoras é compartilhada como print$ e há outros compartilhamentos administrativos que podem ser conectados. Somente usuários com privilégios administrativos podem acessar esses compartilhamentos.

A maneira mais fácil de se conectar a um compartilhamento é digitar o UNC do compartilhamento no Explorador de Arquivos do Windows, na caixa na parte superior da tela que mostra a listagem de rastreamento do local atual do sistema de arquivos. Quando o Windows tentar se conectar ao compartilhamento, você será solicitado a fornecer credenciais para acessar o recurso. Lembre-se de que, como o recurso está em um computador remoto, as credenciais precisam ser para o computador remoto, não para o computador local.

Além de acessar compartilhamentos em hosts remotos, você também pode fazer login em um host remoto e manipular esse computador, como se fosse local, para fazer alterações de configuração, instalar software ou solucionar um problema. No Windows, esse recurso usa o protocolo RDP (Remote Desktop Protocol). Ao investigar incidentes de segurança, um analista de segurança usa o RDP frequentemente para acessar computadores remotos. Para iniciar o RDP e conectar-se a um computador remoto, procure área de trabalho remota e clique no aplicativo. A janela Conexão de área de trabalho remota é mostrada na figura.

Como o RDP foi projetado para permitir que usuários remotos controlem hosts individuais, ele é um alvo natural para atores de ameaças. Deve-se ter cuidado ao ativar o RDP, especialmente em versões legado sem os patches do Windows, como aquelas que ainda são encontradas em sistemas de controle industrial. Deve-se ter cuidado para limitar a exposição do RDP à internet, e abordagens de segurança e políticas de controle de acesso, como Zero Trust, devem ser usadas para limitar o acesso a hosts internos.

### Servidor Windows

A maioria das instalações do Windows são executadas como instalações de área de trabalho em desktops e laptops. Há outra edição do Windows que é usada principalmente em data centers chamado Windows Server. Esta é uma família de produtos Microsoft que começou com o Windows Server 2003. O Windows Server hospeda muitos serviços diferentes e pode desempenhar funções diferentes dentro de uma empresa.

**Nota**: Embora exista um Windows Server 2000, é considerada uma versão cliente do Windows NT 5.0. O Windows Server 2003 é um servidor baseado no NT 5.2 e inicia uma nova família de versões do Windows Server.

Estes são alguns dos serviços que o Windows Server fornece:

- **Serviços de Rede** - DNS, DHCP, Serviços de Terminal, Controlador de Rede e Virtualização de Rede Hyper-V
- **Serviços de Arquivo** - SMB, NFS e DFS
- **Serviços Web** - FTP, HTTP e HTTPS
- **Gerenciamento** - Diretiva de grupo e controle de serviços de domínio do Active Directory

