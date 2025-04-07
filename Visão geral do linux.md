
### O que é Linux?

Linux é um sistema operacional criado em 1991. O Linux é de código aberto, rápido, confiável e pequeno. Ele requer muito poucos recursos de hardware para ser executado e é altamente personalizável. Ao contrário de outros sistemas operacionais, como Windows e Mac OS X, Linux foi criado, e atualmente é mantido por, uma comunidade de programadores. Linux faz parte de várias plataformas e pode ser encontrado em dispositivos de qualquer lugar, desde “relógios de pulso a supercomputadores”.

Outro aspecto importante do Linux é que ele foi projetado para ser conectado à rede, o que torna muito mais simples escrever e usar aplicativos baseados em rede. Como o Linux é open source, qualquer pessoa ou empresa pode obter o código-fonte do kernel, inspecioná-lo, modificá-lo e recompilá-lo à vontade. Eles também estão autorizados a redistribuir o programa com ou sem encargos.

Uma distribuição Linux é o termo usado para descrever pacotes criados por diferentes organizações. Distribuições Linux (ou distros) incluem o kernel Linux com ferramentas personalizadas e pacotes de software. Embora algumas dessas organizações possam cobrar por seu suporte de distribuição Linux (voltado para empresas baseadas em Linux), a maioria delas também oferece sua distribuição gratuitamente sem suporte. Debian, Red Hat, Ubuntu, CentOS e SUSE são apenas alguns exemplos de distribuições Linux.

### O valor do Linux

O Linux é frequentemente o sistema operacional escolhido no Centro de Operações de Segurança (SOC). Estas são algumas das razões para escolher o Linux:

- **Linux é open source** - Qualquer pessoa pode adquirir Linux gratuitamente e modificá-lo para atender a necessidades específicas. Essa flexibilidade permite que analistas e administradores criem um sistema operacional especificamente para análise de segurança.
- **A CLI do Linux é muito poderosa** - Embora uma GUI torne muitas tarefas mais fáceis de executar, ela adiciona complexidade e requer mais recursos de computador para executar. A CLI (Command Line Interface) Linux é extremamente poderosa e permite que os analistas executem tarefas não apenas diretamente em um terminal, mas também remotamente.
- **O usuário tem mais controle sobre o sistema operacional** - O usuário administrador no Linux, conhecido como o usuário root, ou superusuário, tem poder absoluto sobre o computador. Ao contrário de outros sistemas operacionais, o usuário raiz pode modificar qualquer aspecto do computador com algumas teclas pressionadas. Essa capacidade é especialmente valiosa quando se trabalha com funções de baixo nível, como a pilha de rede. Ele permite que o usuário raiz tenha controle preciso sobre a maneira como os pacotes de rede são manipulados pelo sistema operacional.
- **Ele permite um melhor controle de comunicação de rede** - Controle é uma parte inerente do Linux. Como o sistema operacional pode ser ajustado em praticamente todos os aspectos, é uma ótima plataforma para a criação de aplicativos de rede. Esta é a mesma razão pela qual muitas grandes ferramentas de software baseadas em rede estão disponíveis apenas para Linux.

### Linux no SOC

A flexibilidade fornecida pelo Linux é um ótimo recurso para o SOC. Todo o sistema operacional pode ser adaptado para se tornar a plataforma de análise de segurança perfeita. Por exemplo, os administradores podem adicionar apenas os pacotes necessários ao sistema operacional, tornando-o simples e eficiente. Ferramentas de software específicas podem ser instaladas e configuradas para funcionar em conjunto, permitindo que os administradores criem um computador personalizado que se encaixe perfeitamente no fluxo de trabalho de um SOC.

Sguil, que é o console do analista de segurança cibernética em uma versão especial do Linux chamada Security Onion. O Security Onion é um conjunto de ferramentas de código aberto que trabalham juntas para análise de segurança de rede. Trabalharemos com Security Onion mais tarde neste curso.

A tabela lista algumas ferramentas que são freqüentemente encontradas em um SOC.
![[Pasted image 20241217194130.png]]

### Ferramentas Linux

Além das ferramentas específicas de SOC, os computadores Linux que são usados no SOC geralmente contêm ferramentas de teste de penetração. Também conhecido como Pentesting, um teste de penetração é o processo de procurar vulnerabilidades em uma rede ou computador atacando-o. Geradores de pacotes, scanners de porta e explorações de prova de conceito são exemplos de ferramentas Pentesting.

Kali Linux é uma distribuição Linux agrupa muitas ferramentas de penetração juntas em uma única distribuição Linux. Kali contém uma grande variedade de ferramentas.

# Trabalhando no Linux Shell

No Linux, o usuário se comunica com o SO usando a CLI ou a GUI. O Linux geralmente inicia na GUI por padrão. Isso oculta a CLI do usuário. Uma maneira de acessar a CLI a partir da GUI é por meio de um aplicativo de emulador de terminal. Esses aplicativos fornecem acesso do usuário ao CLI e geralmente são nomeados como uma variação da palavra "terminal". No Linux, emuladores de terminal populares são Terminator, eterm, xterm, konsole e gnome-terminal.

Fabrice Bellard criou JSLinux que permite que uma versão emulada do Linux seja executada em um navegador. Procure por ele na internet. Abra um console Linux em JSLinux e digite o **ls** comando para listar o conteúdo do diretório atual. Mantenha a guia aberta se você gostaria de experimentar alguns dos outros comandos discutidos neste capítulo.

A figura mostra o gnome-terminal, um emulador de terminal Linux popular.

**Observação**: Os termos shell, console, janela do console, terminal da CLI e janela do terminal são frequentemente usados de forma intercambiável.

### Comandos básicos

Os comandos Linux são programas criados para executar uma tarefa específica. Use o **man** comando (abreviação para manual) para obter documentação sobre comandos. Como exemplo, **man ls** fornece documentação sobre o **ls** comando a partir do manual do usuário.

Como os comandos são programas armazenados no disco, quando um usuário digita um comando, o shell deve encontrá-lo no disco antes que ele possa ser executado. O shell procurará comandos digitados pelo usuário em diretórios específicos e tentará executá-los. A lista de diretórios verificados pelo shell é chamada de caminho. O caminho contém muitos diretórios comumente usados para armazenar comandos. Se um comando não estiver no caminho, o usuário deve especificar sua localização, ou o shell não será capaz de encontrá-lo. Os usuários podem facilmente adicionar diretórios ao caminho, se necessário.

Para invocar um comando através do shell, basta digitar seu nome. O shell tentará encontrá-lo no caminho do sistema e executá-lo.

A tabela lista comandos básicos do Linux e suas funções.
![[Pasted image 20241218201756.png]]

### Comandos de arquivo e diretório

Muitas ferramentas de linha de comando estão incluídas no Linux por padrão. Para ajustar a operação do comando, os usuários podem passar parâmetros e opções junto com o comando. A tabela lista alguns dos comandos mais comuns relacionados a arquivos e diretórios.
![[Pasted image 20241218201855.png]]

### Trabalhando com Arquivos de Texto

Linux tem muitos editores de texto diferentes, com vários recursos e funções. Alguns editores de texto incluem interfaces gráficas, enquanto outros são apenas ferramentas de linha de comando. Cada editor de texto inclui um conjunto de recursos projetado para suportar um tipo específico de tarefa. Alguns editores de texto se concentram no programador e incluem recursos como realce de sintaxe, parênteses e verificação de parênteses e outros recursos focados na programação.

Embora os editores de texto gráficos sejam convenientes e fáceis de usar, os editores de texto baseados em linha de comando são muito importantes para os usuários do Linux. O principal benefício dos editores de texto baseados em linha de comando é que eles permitem a edição de arquivos de texto a partir de um computador remoto.

Considere o seguinte cenário: um usuário deve executar tarefas administrativas em um computador Linux, mas não está sentado na frente desse computador. Usando SSH, o usuário inicia um shell remoto para o computador remoto. Sob o shell remoto baseado em texto, a interface gráfica não está disponível, o que torna impossível confiar em ferramentas como editores de texto gráficos. Neste tipo de situação, programas baseados em texto são cruciais.

A figura mostra **nano**, um editor de texto de linha de comando popular. O administrador está editando regras de firewall. Editores de texto são frequentemente usados para configuração e manutenção do sistema no Linux.

Devido à falta de suporte gráfico, nano (ou GNU nano) só pode ser controlado com o teclado. Por exemplo, **CTRL+O** salva o arquivo atual; **CTRL+W** abre o menu de pesquisa. GNU nano usa uma barra de atalho de duas linhas na parte inferior da tela, onde os comandos para o contexto atual são listados. Pressione **CTRL+G** para obter a tela de ajuda e uma lista completa de comandos.

### A importância dos arquivos de texto no Linux

No Linux, tudo é tratado como um arquivo. Isso inclui a memória, os discos, o monitor e os diretórios. Por exemplo, do ponto de vista do sistema operacional, mostrar informações na tela significa gravar no arquivo que representa o dispositivo de exibição. Não deve ser surpresa que o próprio computador esteja configurado através de arquivos. Conhecidos como arquivos de configuração, eles geralmente são arquivos de texto usados para armazenar ajustes e configurações para aplicativos ou serviços específicos. Praticamente tudo no Linux depende de arquivos de configuração para funcionar. Alguns serviços têm não um, mas vários arquivos de configuração.

Os usuários com níveis de permissão adequados podem usar editores de texto para alterar o conteúdo dos arquivos de configuração. Depois que as alterações são feitas, o arquivo é salvo e pode ser usado pelo serviço ou aplicativo relacionado. Os usuários podem especificar exatamente como querem que qualquer aplicativo ou serviço se comporte. Quando iniciados, serviços e aplicativos verificam o conteúdo de arquivos de configuração específicos para ajustar seu comportamento de acordo.

Na figura, o administrador abriu o arquivo de configuração do host **nano** para edição. O arquivo host contém mapeamentos estáticos de endereços IP do host para nomes. Os nomes servem como atalhos que permitem a conexão com outros dispositivos usando um nome em vez de um endereço IP. Somente o superusuário pode alterar o arquivo host.

**Observação**: O administrador usou o comando **sudo nano /etc/hosts** para abrir o arquivo. O comando **sudo** (abreviação de “superusuário do”) invoca o privilégio de superusuário para usar o editor de texto nano para abrir o arquivo host.

# Servidores e clientes Linux

Os servidores são computadores com software instalado que lhes permite fornecer serviços aos clientes em toda a rede. Existem muitos tipos de serviços. Alguns fornecem recursos externos, como arquivos, mensagens de e-mail ou páginas da Web para clientes mediante solicitação. Outros serviços executam tarefas de manutenção, como gerenciamento de registros, gerenciamento de memória, varredura de disco e muito mais. Cada serviço exige um software de servidor separado.

### Servidores, serviços e suas portas

Para que um computador possa ser o servidor de vários serviços, as portas são usadas. Uma porta é um recurso de rede reservado usado por um serviço. Um servidor é dito estar “escutando” em uma porta quando ele se associou a essa porta.

Embora o administrador possa decidir qual porta usar com qualquer serviço específico, muitos clientes são configurados para usar uma porta específica por padrão. É prática comum deixar o serviço em execução em sua porta padrão. A tabela lista algumas portas comumente usadas e seus serviços. Estes também são chamados de “portas bem conhecidas”.
![[Pasted image 20241218202641.png]]

### Clientes

Os clientes são programas ou aplicativos projetados para se comunicar com um tipo específico de servidor. Também conhecidos como aplicativos cliente, os clientes usam um protocolo bem definido para se comunicar com o servidor. Os navegadores da Web são clientes da Web que são usados para se comunicar com servidores Web por meio do Hyper Text Transfer Protocol (HTTP) na porta 80. O cliente FTP (File Transfer Protocol) é um software usado para se comunicar com um servidor FTP.

# Administração Básica do Servidor

### Arquivos de configuração de serviço

No Linux, os serviços são gerenciados usando arquivos de configuração. As opções comuns nos arquivos de configuração são o número da porta, a localização dos recursos hospedados e os detalhes da autorização do cliente. Quando o serviço é iniciado, ele procura seus arquivos de configuração, carrega-os na memória e se ajusta de acordo com as configurações nos arquivos. As modificações do arquivo de configuração geralmente exigem a reinicialização do serviço antes que as alterações entrem em vigor.

Como os serviços geralmente exigem privilégios de superusuário para serem executados, os arquivos de configuração de serviço geralmente exigem privilégios de superusuário para editar.

Não há regra para um formato de arquivo de configuração; é a escolha do desenvolvedor do serviço. No entanto, o formato **option = value** é freqüentemente usado. Por exemplo, na última saída do comando, a variável **ipvar** é configurada com várias opções. A primeira opção, HOME_NET, tem o valor 209.165.200.224/27. O caractere hash (**#**) é usado para indicar comentários.

### Fortalecimento de Dispositivos (hardering)

O fortalecimento (hardering) do dispositivo envolve a implementação de métodos comprovados de proteção do dispositivo e proteção de seu acesso administrativo. Alguns desses métodos envolvem a manutenção de senhas, a configuração de recursos avançados de login remoto e a implementação de login seguro com SSH. A definição de funções administrativas em termos de acesso é outro aspecto importante da proteção dos dispositivos de infraestrutura, pois nem todo o pessoal de tecnologia da informação deve ter o mesmo nível de acesso aos dispositivos de infraestrutura.

Dependendo da distribuição Linux, muitos serviços são habilitados por padrão. Alguns desses recursos estão habilitados por motivos históricos, mas não são mais necessários. Parar esses serviços e garantir que eles não iniciem automaticamente no momento da inicialização é outra técnica de fortalecimento (hardering) do dispositivo.

As atualizações do sistema operacional também são extremamente importantes para manter um dispositivo reforçado. Novas vulnerabilidades são descobertas todos os dias. Os desenvolvedores de SO criam e emitem correções e patches regularmente. Um computador atualizado é menos provável que seja comprometido.

A seguir estão as práticas recomendadas básicas para o fortalecimento (hardering) do dispositivo.

- Garantir a segurança física
- Minimizar pacotes instalados
- Desativar serviços não utilizados
- Usar SSH e desabilitar o login da conta raiz por SSH
- Manter o sistema atualizado
- Desativar a detecção automática de USB
- Aplicar senhas fortes
- Forçar mudanças de senha periódicas
- Manter os usuários de reutilizarem senhas antigas

Muitas outras etapas existem e muitas vezes dependem do serviço ou do aplicativo.

### Logs de serviço de monitoramento

Arquivos de log são os registros que um computador armazena para manter o controle de eventos importantes. Kernel, serviços e eventos de aplicativos são todos registrados em arquivos de log. É muito importante que um administrador revise periodicamente os logs de um computador para mantê-lo saudável. Ao monitorar arquivos de log do Linux, um administrador obtém uma visão clara do desempenho do computador, status de segurança e quaisquer problemas subjacentes. A análise do arquivo de log permite que um administrador proteja contra problemas futuros antes que eles ocorram.

No Linux, os arquivos de log podem ser categorizados como:

- Logs de aplicativos
- Logs de eventos
- Registros de serviço
- Logs do sistema

Alguns logs contêm informações sobre daemons que estão sendo executados no sistema Linux. Um daemon é um processo em segundo plano que é executado sem a necessidade de interação do usuário. Por exemplo, o System Security Services Daemon (SSSD) gerencia o acesso remoto e a autenticação para recursos de logon único.

A tabela lista alguns arquivos de log populares do Linux e suas funções
![[Pasted image 20241218204045.png]]

# O sistema de arquivos Linux

### Os tipos de sistema de arquivos no Linux

Existem muitos tipos diferentes de sistemas de arquivos, variando em propriedades de velocidade, flexibilidade, segurança, tamanho, estrutura, lógica e muito mais. Cabe ao administrador decidir qual tipo de sistema de arquivos melhor se adequa ao sistema operacional e aos arquivos que ele armazenará.

A tabela lista alguns tipos de sistema de arquivos comumente encontrados e suportados pelo Linux.
![[Pasted image 20241218204436.png]]
![[Pasted image 20241218204446.png]]

Montagem é o termo usado para o processo de atribuição de um diretório a uma partição. Após uma operação de montagem bem-sucedida, o sistema de arquivos contido na partição é acessível através do diretório especificado. Neste contexto, o diretório é chamado de ponto de montagem para esse sistema de arquivos. Os usuários do Windows podem estar familiarizados com um conceito semelhante; a letra da unidade.

A saída do comando mostra a saída do comando **mount** emitido na VM Cisco CyberOps.
Quando emitido sem opções, **mount** retorna a lista de sistemas de arquivos atualmente montados em um computador Linux. Embora muitos dos sistemas de arquivos mostrados estejam fora do escopo deste curso, observe o sistema de arquivos raiz (destacado). O sistema de arquivos raiz é representado pelo símbolo “/” e contém todos os arquivos no computador por padrão. Também é mostrado na saída que o sistema de arquivos raiz foi formatado como ext4 e ocupa a primeira partição da primeira unidade (/dev/sda1).

### Funções do Linux e permissões de arquivo

No Linux, a maioria das entidades do sistema são tratadas como arquivos. Para organizar o sistema e impor limites dentro do computador, o Linux usa permissões de arquivo. As permissões de arquivo são incorporadas à estrutura do sistema de arquivos e fornecem um mecanismo para definir permissões em cada arquivo. Cada arquivo no Linux carrega suas permissões de arquivo, que definem as ações que o proprietário, o grupo e outros podem executar com o arquivo. Os direitos de permissão possíveis são Ler, Gravar e Executar. O comando **ls** com o **-l** parâmetro lista informações adicionais sobre o arquivo.

Considere a saída do comando **ls -l** na saída do comando.
![[Pasted image 20241218204706.png]]O arquivo **space.txt** tem as seguintes permissões:

- O traço (-) significa que este é um arquivo. Para diretórios, o primeiro traço seria um “d”.
- O primeiro conjunto de caracteres é para permissão do usuário (O). O usuário, **analyst** do **rwx**, que possui o arquivo pode Ler, Gravar e eXECute o arquivo.
- O segundo conjunto de caracteres é para permissões de grupo (**rw-**). O grupo, **staff**, que possui o arquivo pode Ler e WRite para o arquivo.
- O terceiro conjunto de caracteres é para qualquer outra permissão de usuário ou grupo (**). Qualquer outro usuário ou grupo no computador só pode ler o arquivo.

O segundo campo define o número de links rígidos para o arquivo (o número**1**após as permissões). Um link rígido cria outro arquivo com um nome diferente vinculado ao mesmo lugar no sistema de arquivos (chamado de inode). Isso está em contraste com um link simbólico, que é discutido na próxima página.

O terceiro e quarto campos exibem o usuário (**analyst**) e o grupo (**staff**) que possuem o arquivo, respectivamente.

O quinto campo exibe o tamanho do arquivo em bytes. O arquivo**space.txt** tem 253 bytes.

O sexto campo exibe a data e hora da última modificação.

O sétimo campo exibe o nome do arquivo.

A figura mostra uma divisão das permissões de arquivo no Linux.
![[Pasted image 20241218204821.png]]
Use valores octais para definir permissões.
![[Pasted image 20241218204844.png]]

Permissões de arquivo são uma parte fundamental do Linux e não podem ser quebradas. Um usuário tem apenas os direitos de um arquivo que as permissões de arquivo permitem. O único usuário que pode substituir a permissão de arquivo em um computador Linux é o usuário root. Como o usuário root tem o poder de substituir as permissões de arquivo, o usuário root pode gravar em qualquer arquivo. Como tudo é tratado como um arquivo, o usuário root tem controle total sobre um computador Linux. O acesso como root é muitas vezes necessário antes de realizar tarefas administrativas e de manutenção. Devido ao poder do usuário raiz, as credenciais raiz devem usar senhas fortes e não ser compartilhadas com ninguém além de administradores de sistema e outros usuários de alto nível.

### Links rígidos e links simbólicos

Um link rígido é outro arquivo que aponta para o mesmo local que o arquivo original. Use o comando **ln** para criar um link rígido. O primeiro argumento é o arquivo existente e o segundo argumento é o novo arquivo. Como mostrado na saída do comando, o arquivo **space.txt** é vinculado **space.hard.txt** e o campo de link agora mostra 2.
![[Pasted image 20241218204948.png]]
Ambos os arquivos apontam para o mesmo local no sistema de arquivos. Se você alterar um arquivo, o outro também será alterado. O comando **echo** é usado para adicionar algum texto ao **space.txt**. Observe que o tamanho do arquivo para ambos **space.txt** e **space.hard.txt** aumentou para 257 bytes. Se você excluir o space.hard.txt com o comando (remover) **rm**, o arquivo **space.txt** ainda existe, conforme verificado com o comando **more space.txt**.

Um link simbólico, também chamado de link simbólico ou link suave, é semelhante a um link rígido em que a aplicação de alterações ao link simbólico também mudará o arquivo original. Como mostrado na saída do comando abaixo, use o comando **ln** com a opção **-s** para criar um link simbólico.
![[Pasted image 20241218205046.png]]

Observe que a adição de uma linha de texto **test.txt** também adiciona a linha **mytest.txt**. No entanto, ao contrário de um link rígido, excluir o arquivo **text.txt** original significa que agora **mytext.txt** está vinculado a um arquivo que não existe mais, como mostrado com os comandos **more mytest.txt** e **ls -l mytest.txt**.

Embora links simbólicos tenham um único ponto de falha (o arquivo subjacente), links simbólicos têm vários benefícios sobre links rígidos:

- Localizar links físicos é mais difícil. Links simbólicos mostram a localização do arquivo original no comando **ls -l**, conforme mostrado na última linha de saída no comando anterior. (**mytest.txt -> test.txt**).
- Links rígidos são limitados ao sistema de arquivos no qual eles são criados. Links simbólicos podem ser vinculados a um arquivo em outro sistema de arquivos.
- Links rígidos não podem se vincular a um diretório porque o próprio sistema usa links rígidos para definir a hierarquia da estrutura de diretórios. No entanto, links simbólicos podem se vincular a diretórios.

# Trabalhando com a GUI Linux

### Sistema X Window

A interface gráfica presente na maioria dos computadores Linux é baseada no X Window System. Também conhecido como X ou X11, X Window é um sistema de janelas projetado para fornecer a estrutura básica para uma GUI. X inclui funções para desenhar e mover janelas no dispositivo de exibição e interagir com um mouse e teclado.

X funciona como um servidor que permite que um usuário remoto use a rede para se conectar, iniciar um aplicativo gráfico e ter a janela gráfica aberta no terminal remoto. Enquanto o aplicativo em si é executado no servidor, o aspecto gráfico dele é enviado por X pela rede e exibido no computador remoto.

Observe que X não especifica a interface do usuário, deixando para outros programas, como gerenciadores de janelas, definir todos os componentes gráficos. Essa abstração permite grande flexibilidade e personalização, pois componentes gráficos, como botões, fontes, ícones, bordas de janelas e esquemas de cores são definidos pelo aplicativo do usuário. Devido a essa separação, a GUI do Linux varia muito de distribuição para distribuição. Exemplos de gerenciadores de janelas são o Gnome e o KDE. Embora a aparência dos gerenciadores de janelas variem, os componentes principais ainda estão presentes.

### A GUI do Linux

Embora um sistema operacional não exija uma GUI para funcionar, as GUIs são consideradas mais fáceis de usar do que a CLI. A GUI Linux como um todo pode ser facilmente substituída pelo usuário. Como resultado do grande número de distribuições Linux, este capítulo se concentra no Ubuntu ao cobrir o Linux, porque é uma distribuição muito popular e amigável.

Ubuntu Linux usa Gnome 3 como sua GUI padrão. O objetivo do Gnome 3 é tornar o Ubuntu ainda mais amigável. A tabela lista os principais componentes da interface do usuário do Unity.
![[Pasted image 20241218205259.png]]

# Trabalhando em um host Linux

### Instalação e execução de aplicativos em um host Linux

Muitos aplicativos de usuário final são programas complexos escritos em linguagens compiladas. Para ajudar no processo de instalação, o Linux geralmente inclui programas chamados gerenciadores de pacotes. Um pacote é o termo usado para se referir a um programa e todos os seus arquivos de suporte. Ao usar um gerenciador de pacotes para instalar um pacote, todos os arquivos necessários são colocados no local correto do sistema de arquivos.

Os gerenciadores de pacotes variam dependendo das distribuições do Linux. Por exemplo, **pacman** é usado pelo Arch Linux enquanto **dpkg** (pacote Debian) e **apt** (Advanced Packaging Tool) são usados em distribuições Debian e Ubuntu Linux. Para este curso, usaremos o gerenciador de **pacman** pacotes.

O comando **apt-get update** é usado para obter a lista de pacotes do repositório de pacotes e atualizar o banco de dados de pacotes local. O comando **apt-get upgrade** é usado para atualizar todos os pacotes atualmente instalados para suas versões mais recentes.

### Mantendo o sistema atualizado

ambém conhecido como patches, as atualizações do sistema operacional são lançadas periodicamente por empresas de sistema operacional para resolver quaisquer vulnerabilidades conhecidas em seus sistemas operacionais. Embora as empresas tenham programações de atualização, o lançamento de atualizações não programadas do sistema operacional pode acontecer quando uma vulnerabilidade importante é encontrada no código do sistema operacional. Os sistemas operacionais modernos alertarão o usuário quando atualizações estiverem disponíveis para download e instalação, mas o usuário pode verificar as atualizações a qualquer momento.

A tabela a seguir compara os comandos de distribuição Arch Linux e Debian / Ubuntu Linux para realizar operações básicas do sistema de pacotes.

![[Pasted image 20241218205445.png]]

Uma GUI do Linux também pode ser usada para verificar e instalar manualmente as atualizações. No Ubuntu, por exemplo, para instalar atualizações, clique em **Dash Search Box** ,**software updater** digite e clique no **ícone Atualizador de** Software

### Processos e Forks

Um processo é uma instância em execução de um programa de computador. Os sistemas operacionais multitarefa podem executar muitos processos ao mesmo tempo.

Bifurcação é um método que o kernel usa para permitir que um processo crie uma cópia de si mesmo. Os processos precisam de uma maneira de criar novos processos em sistemas operacionais multitarefa. A operação bifurcação (fork) é a única maneira de fazer isso no Linux.

A bifurcação (fork) é importante por muitos motivos. Um deles está relacionado à escalabilidade do processo. Apache, um servidor web popular, é um bom exemplo. Ao se bifurcar, o Apache é capaz de atender a um grande número de solicitações com menos recursos do sistema do que um servidor baseado em processo único.

Quando um processo é bifurcado (fork), o processo do chamador se torna o processo pai, com o processo recém-criado referido como seu filho. Depois da bifurcação, os processos são, até certo ponto, processos independentes; eles têm IDs de processo diferentes, mas executam o mesmo código de programa.

A tabela lista três comandos usados para gerenciar processos.
![[Pasted image 20241218205606.png]]

### Malware em um host Linux

Embora indiscutivelmente mais protegido, o Linux não é imune a malware. Muitas vulnerabilidades foram encontradas e exploradas no Linux. Estes variam de software de servidor a vulnerabilidades de kernel. Os atacantes são capazes de explorar essas vulnerabilidades e comprometer o alvo. Como o Linux é de código aberto, correções e patches são frequentemente disponibilizados em poucas horas após a descoberta de tais problemas.

Se um programa malicioso for executado, ele causará danos, independentemente da plataforma. Um vetor de ataque Linux comum é seus serviços e processos. Vulnerabilidades são freqüentemente encontradas no código de servidor e processo em execução em computadores conectados à rede. Uma versão desatualizada do servidor web Apache poderia conter uma vulnerabilidade não corrigida que pode ser explorada por um invasor, por exemplo. Os invasores geralmente testam portas abertas para avaliar a versão e a natureza do servidor em execução nessa porta. Com esse conhecimento, os atacantes podem pesquisar se há algum problema conhecido com essa versão específica desse servidor específico para dar suporte ao ataque. Como acontece com a maioria das vulnerabilidades, manter o computador atualizado e fechar todos os serviços e portas não utilizados é uma boa maneira de reduzir as oportunidades de ataque em um computador Linux.

A saída do comando mostra um invasor usando o comando Telnet para testar a natureza e a versão de um servidor Web (porta 80).
![[Pasted image 20241218205722.png]]

O invasor descobriu que o servidor em questão está executando o nginx versão 1.12.0. O próximo passo seria pesquisar vulnerabilidades conhecidas no código nginx 1.12.0.

**Nota**: Você aprenderá mais sobre esse ataque mais tarde no curso.

### Verificação de Rootkit

Um rootkit é um tipo de malware projetado para aumentar os privilégios de um usuário não autorizado ou conceder acesso a partes do software que normalmente não devem ser permitidas. Rootkits também são frequentemente usados para proteger uma porta traseira para um computador comprometido.

A instalação de um rootkit pode ser automatizada (feita como parte de uma infecção) ou um invasor pode instalá-lo manualmente após comprometer um computador. Um rootkit é destrutivo porque ele muda o código do kernel e seus módulos, alterando as operações mais fundamentais do próprio sistema operacional. Com um nível tão profundo de comprometimento, os rootkits podem ocultar a intrusão, remover quaisquer faixas de instalação e até mesmo adulterar ferramentas de diagnóstico e solução de problemas para que sua saída agora esconda a presença do rootkit. Embora algumas vulnerabilidades do Linux ao longo do histórico tenham permitido a instalação do rootkit através de contas de usuário regulares, a grande maioria dos compromissos do rootkit requer acesso root ou administrador.

Como a própria natureza do computador está comprometida, a detecção de rootkit pode ser muito difícil. Os métodos de detecção típicos geralmente incluem a inicialização do computador a partir de mídia confiável, como um CD ativo do sistema operacional de diagnóstico. A unidade comprometida é montada e, a partir do conjunto de ferramentas do sistema confiável, ferramentas de diagnóstico confiáveis podem ser iniciadas para inspecionar o sistema de arquivos comprometido. Os métodos de inspeção incluem métodos baseados em comportamento, varredura de assinatura, varredura de diferenças e análise de despejo de memória.

A remoção do Rootkit pode ser complicada e muitas vezes impossível, especialmente nos casos em que o rootkit reside no kernel; a reinstalação do sistema operacional geralmente é a única solução real para o problema. Os rootkits de firmware geralmente requerem substituição de hardware.

**chkrootkit** é um programa popular baseado em Linux projetado para verificar o computador em busca de rootkits conhecidos. É um script shell que usa ferramentas comuns do Linux, como **strings** e **grep** para comparar as assinaturas de programas principais. Ele também procura discrepâncias à medida que atravessa o sistema de arquivos /proc comparando as assinaturas encontradas lá com a saída de **ps**.

Embora útil, tenha em mente que os programas para verificar se há rootkits não são 100% confiáveis.

A saída do comando mostra a saída de **chkrootkit** em um Ubuntu Linux.
![[Pasted image 20241218205927.png]]

### Comandos de piping

Embora as ferramentas de linha de comando geralmente sejam projetadas para executar uma tarefa específica e bem definida, muitos comandos podem ser combinados para executar tarefas mais complexas por uma técnica conhecida como piping. Nomeado após seu caractere definidor, o pipe (**|**), tubulação consiste em encadear comandos juntos, alimentando a saída de um comando na entrada de outro.

Por exemplo, o comando **ls** é usado para exibir todos os arquivos e diretórios de um determinado diretório. O comando **grep** compara pesquisas através de um arquivo ou texto procurando a string especificada. Se encontrado, **grep** exibe todo o conteúdo da pasta onde a string foi encontrada.

Os dois comandos, **ls** e **grep**, podem ser canalizado juntos para filtrar a saída de **ls**. Isto é mostrado na saída do comando **ls -l | grep host** e do comando **ls -l | grep file** .