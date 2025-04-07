
# Histórico do Windows

### Sistema operacional de 

Os primeiros computadores não tinham dispositivos de armazenamento modernos, como discos rígidos, unidades ópticas ou armazenamento flash. Os primeiros métodos de armazenamento usavam cartões perfurados, fita de papel, fita magnética e até cassetes de áudio.

Disquetes e armazenamento em disco rígido exigem software para ler, gravar e gerenciar os dados que eles armazenam. O sistema operacional de disco (DOS) é um sistema operacional que o computador usa para habilitar esses dispositivos de armazenamento de dados para ler e gravar arquivos. DOS fornece um sistema de arquivos que organiza os arquivos de uma forma específica no disco. A Microsoft comprou o DOS e desenvolveu o MS-DOS.

MS-DOS usou uma linha de comando como a interface para as pessoas criarem programas e manipularem arquivos de dados.

Com o MS-DOS, o computador tinha um conhecimento básico de trabalho de como acessar a unidade de disco e carregar os arquivos do sistema operacional diretamente do disco como parte do processo de inicialização. Quando ele foi carregado, o MS-DOS poderia acessar facilmente o disco porque ele foi incorporado no sistema operacional.

As primeiras versões do Windows consistiam em uma interface gráfica do usuário (GUI) que executava o MS-DOS, começando com o Windows 1.0 em 1985. O DOS ainda controlava o computador e seu hardware. Um sistema operacional moderno como o Windows 10 não é considerado um sistema operacional de disco. Ele é construído no Windows NT, que significa “Novas Tecnologias”. O próprio sistema operacional está no controle direto do computador e seu hardware. NT é um sistema operacional com suporte para vários processos de usuário. Isso é muito diferente do MS-DOS de um único processo e de usuário único.

Hoje, muitas coisas que costumavam ser realizadas através da interface de linha de comando do MS-DOS podem ser realizadas na GUI do Windows. Você ainda pode experimentar como era usar o MS-DOS abrindo uma janela de comando, mas o que você vê não é mais MS-DOS, é uma função do Windows. Para experimentar um pouco do que era trabalhar no MS-DOS, abra uma janela de comando digitando **cmd** na Pesquisa do Windows e pressionando **Enter**. A tabela lista alguns comandos que você pode usar. Digite **help** seguido do comando para saber mais sobre o comando.

![[Pasted image 20241213180057.png]]

### Versões do Windows

Desde 1993, houve mais de 20 lançamentos do Windows que são baseados no sistema operacional NT. A maioria dessas versões era para uso pelo público em geral e pelas empresas devido à segurança de arquivos oferecida pelo sistema de arquivos usado pelo sistema operacional NT. As empresas também adotaram sistemas operacionais Windows baseados em SO NT. Isso ocorre porque muitas edições foram criadas especificamente para estações de trabalho, profissionais, servidores, servidores avançados e servidores de datacenter, para citar apenas algumas das muitas versões criadas para fins específicos.

A partir do Windows XP, uma edição de 64 bits estava disponível. O sistema operacional de 64 bits era uma arquitetura totalmente nova. Ele tinha um espaço de endereço de 64 bits em vez de um espaço de endereço de 32 bits. Isto não é simplesmente o dobro da quantidade de espaço porque estes bits são números binários. Embora o Windows de 32 bits possa endereçar um pouco menos de 4 GB de RAM, o Windows de 64 bits pode, teoricamente, endereçar 16,8 milhões de terabytes. Quando o sistema operacional e o hardware suportam a operação de 64 bits, conjuntos de dados extremamente grandes podem ser usados. Esses grandes conjuntos de dados incluem bancos de dados muito grandes, computação científica e manipulação de vídeo digital de alta definição com efeitos especiais. Em geral, computadores e sistemas operacionais de 64 bits são compatíveis com programas mais antigos de 32 bits, mas programas de 64 bits não podem ser executados em hardware mais antigo de 32 bits.

Com cada versão subsequente do Windows, o sistema operacional tornou-se mais refinado ao incorporar mais recursos. O Windows 7 foi oferecido com seis edições diferentes, o Windows 8 com até cinco e o Windows 10 com oito edições diferentes! Cada edição não só oferece diferentes capacidades, mas também diferentes pontos de preço. A Microsoft disse que o Windows 10 é a última versão do Windows, e que o Windows se tornou um serviço em vez de apenas um sistema operacional. Eles dizem que, em vez de comprar novos sistemas operacionais, os usuários apenas atualizarão o Windows 10 em vez disso.

A tabela lista versões comuns do Windows.

![[Pasted image 20241213180322.png]]

### Vulnerabilidades do sistema operacional

O invasor pode então usar a vulnerabilidade para fazer com que o computador atue de forma fora do design pretendido. Em geral, o objetivo é obter controle não autorizado do computador, alterar permissões ou manipular ou roubar dados.

A tabela lista algumas recomendações comuns de Segurança do SO Windows.

![[Pasted image 20241213180518.png]]

# Arquitetura e operações do Windows

### Camada de abstração de hardware

Computadores Windows usam muitos tipos diferentes de hardware. O sistema operacional pode ser instalado em um computador comprado ou em um computador que é montado pelo usuário. Quando o sistema operacional está instalado, ele deve ser isolado das diferenças no hardware. A arquitetura básica do Windows é mostrada na figura.

![[Pasted image 20241213180621.png]]

### Modo de usuário e modo kernel

![[Pasted image 20241213180737.png]]

Os aplicativos instalados são executados no modo de usuário e o código do sistema operacional é executado no modo kernel. O código que está sendo executado no modo kernel tem acesso irrestrito ao hardware subjacente e é capaz de executar qualquer instrução de CPU. O código do modo kernel também pode referenciar qualquer endereço de memória diretamente. Geralmente reservado para as funções mais confiáveis do sistema operacional, falhas no código em execução no modo kernel param a operação de todo o computador. Por outro lado, programas como aplicativos de usuário são executados no modo de usuário e não têm acesso direto a locais de hardware ou memória. O código do modo de usuário deve passar pelo sistema operacional para acessar recursos de hardware. Devido ao isolamento fornecido pelo modo de usuário, as falhas no modo de usuário são restritas apenas ao aplicativo e são recuperáveis. A maioria dos programas no Windows são executados no modo de usuário. Drivers de dispositivo, peças de software que permitem que o sistema operacional e um dispositivo se comuniquem, podem ser executados no modo kernel ou usuário, dependendo do driver.

Todo o código que é executado no modo kernel usa o mesmo espaço de endereço. Os drivers de modo kernel não têm isolamento do sistema operacional. Se ocorrer um erro com o driver em execução no modo kernel e ele gravar no espaço de endereço errado, o sistema operacional ou outro driver de modo kernel pode ser afetado negativamente. A este respeito, o driver pode falhar, fazendo com que todo o sistema operacional falhe.

Quando o código de modo de usuário é executado, ele é concedido seu próprio espaço de endereço restrito pelo kernel, juntamente com um processo criado especificamente para o aplicativo. A razão para essa funcionalidade é principalmente para impedir que aplicativos alterem o código do sistema operacional que está sendo executado ao mesmo tempo. Ao ter seu próprio processo, esse aplicativo tem seu próprio espaço de endereço privado, tornando outros aplicativos incapazes de modificar os dados nele. Isso também ajuda a evitar que o sistema operacional e outros aplicativos falhe se esse aplicativo falhar.

### Sistemas de arquivos Windows

Um sistema de arquivos é como as informações são organizadas na mídia de armazenamento. Alguns sistemas de arquivos podem ser uma melhor opção para usar do que outros, dependendo do tipo de mídia que será usado. A tabela lista os sistemas de arquivos suportados pelo Windows.

![[Pasted image 20241213180943.png]]

O NTFS é o sistema de arquivos mais utilizado para Windows por muitas razões. NTFS suporta arquivos e partições muito grandes e é muito compatível com outros sistemas operacionais. O NTFS também é muito confiável e oferece suporte a recursos de recuperação. Mais importante ainda, ele suporta muitos recursos de segurança. O controle de acesso a dados é alcançado através de descritores de segurança. Esses descritores de segurança contêm permissões e propriedade do arquivo até o nível do arquivo. O NTFS também controla muitos carimbos de data/hora para controlar a atividade do arquivo. Às vezes referido como MACE, os carimbos de data/hora Modificar, Access (acesso), Create (criar) e Entry Modified (entrada modificada) são frequentemente usados em investigações forenses para determinar o histórico de um arquivo ou pasta. O NTFS também suporta criptografia do sistema de arquivos para proteger toda a mídia de armazenamento.

Antes que um dispositivo de armazenamento, como um disco, possa ser usado, ele deve ser formatado com um sistema de arquivos. Por sua vez, antes que um sistema de arquivos possa ser colocado em prática em um dispositivo de armazenamento, o dispositivo precisa ser particionado. Um disco rígido é dividido em áreas denominadas partições. Cada partição é uma unidade lógica de armazenamento que pode ser formatada para armazenar informações, como arquivos de dados ou de aplicações. Durante o processo de instalação, a maioria dos sistemas operacionais particiona e formata automaticamente o espaço disponível na unidade com um sistema de arquivos como o NTFS.

A formatação NTFS cria estruturas importantes no disco para armazenamento de arquivos e tabelas para gravar os locais dos arquivos:

- **Setor de inicialização de partição** - Este é o primeiro 16 setores da unidade. Ele contém o local da tabela de arquivos mestre (MFT). Os últimos 16 setores contêm uma cópia do setor de inicialização.
- **Tabela de arquivos mestre (MFT)** - Esta tabela contém os locais de todos os arquivos e diretórios na partição, incluindo atributos de arquivo, como informações de segurança e carimbos de data/hora.
- **Arquivos de sistema** - São arquivos ocultos que armazenam informações sobre outros volumes e atributos de arquivo.
- **Área de arquivo** - A área principal da partição onde os arquivos e diretórios são armazenados.

**Observação**: Ao formatar uma partição, os dados anteriores ainda podem ser recuperáveis porque nem todos os dados são completamente removidos. O espaço livre pode ser examinado e os arquivos podem ser recuperados, o que pode comprometer a segurança. Recomenda-se executar um apagamento seguro em uma unidade que está sendo reutilizada. O apagamento seguro grava dados em toda a unidade várias vezes para garantir que não haja dados restantes.

### Fluxos de dados alternativos

NTFS armazena arquivos como uma série de atributos, como o nome do arquivo ou um carimbo de data/hora. Os dados que o arquivo contém são armazenados no atributo $DATA, e é conhecido como um fluxo de dados. Usando NTFS, você pode conectar fluxos de dados alternativos (ADSs) ao arquivo. Às vezes, isso é usado por aplicativos que estão armazenando informações adicionais sobre o arquivo. O ADS é um fator importante ao discutir malware. Isso ocorre porque é fácil ocultar dados em um ADS. Um invasor pode armazenar código mal-intencionado dentro de um ADS que pode ser chamado de um arquivo diferente.

No sistema de arquivos NTFS, um arquivo com um ADS é identificado após o nome do arquivo e dois pontos, por exemplo, **Testfile.txt:ADS**. Esse nome de arquivo indica que um ADS chamado ADS está associado ao arquivo chamado **Testfile.txt**. Um exemplo de ADS é mostrado na saída do comando.

![[Pasted image 20241213181740.png]]

### Processo de Inicialização do Windows

Muitas ações ocorrem entre o momento em que o botão liga/desliga do computador é pressionado e o Windows está totalmente carregado, como mostrado na figura. Isso é conhecido como o processo de inicialização do Windows.

![[Pasted image 20241213181806.png]]

Existem dois tipos de firmware de computador:

- **Sistema básico de entrada-saída (BIOS)** - o firmware do BIOS foi criado no início da década de 1980 e funciona da mesma forma que quando foi criado. À medida que os computadores evoluíram, tornou-se difícil para o firmware do BIOS suportar todos os novos recursos solicitados pelos usuários.
- **UEFI (Unified Extensible Firmware Interface)** - O UEFI foi projetado para substituir o BIOS e suportar os novos recursos.

No firmware do BIOS, o processo começa com a fase de inicialização do BIOS. Isso ocorre quando os dispositivos de hardware são inicializados e um POST (Power On Self-Test) é executado para garantir que todos esses dispositivos estejam se comunicando. Quando o disco do sistema é descoberto, o POST termina. A última instrução no POST é procurar o registro mestre de inicialização (MBR).

A MBR contém um pequeno programa que é responsável por localizar e carregar o sistema operacional. O BIOS executa esse código e o sistema operacional começa a carregar.

Em contraste com o firmware do BIOS, o firmware UEFI tem muita visibilidade sobre o processo de inicialização. O UEFI inicializa carregando arquivos de programa EFI, armazenados como arquivos.efi em uma partição de disco especial, conhecida como EFI System Partition (ESP).

**Nota**: Um computador que usa UEFI armazena o código de inicialização no firmware. Isso ajuda a aumentar a segurança do computador no momento da inicialização porque o computador entra diretamente no modo protegido.

Se o firmware é BIOS ou UEFI, depois que uma instalação válida do Windows é localizada, o arquivo **Bootmgr.exe** é executado. **Bootmgr.exe** alterna o sistema do modo real para o modo protegido para que toda a memória do sistema possa ser usada.

**Bootmgr.exe** lê o Banco de Dados de Configuração de Inicialização (BCD). O BCD contém qualquer código adicional necessário para iniciar o computador, juntamente com uma indicação de se o computador está saindo da hibernação ou se este é um arranque a frio. Se o computador estiver saindo da hibernação, o processo de inicialização continuará com **Winresume.exe**. Isso permite que o computador leia o arquivo **Hiberfil.sys** que contém o estado do computador quando ele foi colocado em hibernação.

Se o computador estiver sendo inicializado a partir de um início a frio, o arquivo **Winload.exe** será carregado. O arquivo **Winload.exe** cria um registro da configuração de hardware no registro. O registro é um registro de todas as configurações, opções, hardware e software do computador. O registro será explorado em profundidade mais adiante neste capítulo. **Winload.exe** também usa o Kernel Mode Code Signing (KMCS) para garantir que todos os drivers sejam assinados digitalmente. Isso garante que os drivers são seguros para carregar à medida que o computador é iniciado.

Depois que os drivers foram examinados, **Winload.exe** é executado **Ntoskrnl.exe** que inicia o kernel do Windows e configura o HAL. Finalmente, o Subsistema do Gestor de Sessões (SMSS) lê o registo para criar o ambiente do utilizador, iniciar o serviço Winlogon e preparar a área de trabalho de cada utilizador à medida que inicia sessão.

### Inicialização do Windows

Há dois itens de registro importantes que são usados para iniciar automaticamente aplicativos e serviços:

- **HKEY\ _LOCAL\ _MACHINE** - Vários aspectos da configuração do Windows são armazenados nesta chave, incluindo informações sobre serviços que começam com cada inicialização.
- **HKEY\ _CURRENT\ _USER** - Vários aspectos relacionados ao usuário conectado são armazenados nesta chave, incluindo informações sobre serviços que iniciam somente quando o usuário faz logon no computador.

O registro será discutido mais adiante neste tópico.

Entradas diferentes nesses locais de registro definem quais serviços e aplicativos serão iniciados, conforme indicado pelo tipo de entrada. Esses tipos incluem Run, RunOnce, RunServices, RunServicesOnce e Userinit. Essas entradas podem ser inseridas manualmente no registro, mas é muito mais seguro usar a ferramenta **Msconfig.exe** Esta ferramenta é usada para exibir e alterar todas as opções de inicialização do computador. Use a caixa de pesquisa para localizar e abrir a ferramenta Msconfig.

### Desligamento do Windows

É sempre melhor executar um desligamento adequado para desligar o computador. Arquivos que são deixados abertos, serviços que são fechados fora de ordem e aplicativos que travam podem ser danificados se a energia for desligada sem primeiro informar o sistema operacional. O computador precisa de tempo para fechar cada aplicativo, desligar cada serviço e registrar quaisquer alterações de configuração antes que a energia seja perdida.

Durante o desligamento, o computador fechará os aplicativos do modo de usuário primeiro, seguido pelos processos do modo kernel. Se um processo de modo de usuário não responder dentro de um determinado período de tempo, o sistema operacional exibirá a notificação e permitirá que o usuário aguarde a aplicação responder ou encerre o processo forçosamente. Se um processo de modo kernel não responder, o desligamento parecerá travar e poderá ser necessário desligar o computador com o botão liga/desliga.

Existem várias maneiras de desligar um computador Windows: Opções de energia do menu Iniciar, o comando da linha de comando **shutdown** e usando **Ctrl+Alt+Delete** e clicando no ícone de energia. Existem três opções diferentes para escolher ao desligar o computador:

- **Desligamento** - Desliga o computador (desliga).
- **Reiniciar** - Reinicializa o computador (desligar e ligar).
- **Hibernate** - Registra o estado atual do ambiente do computador e do usuário e o armazena em um arquivo. A hibernação permite que o usuário continue de onde parou muito rapidamente com todos os seus arquivos e programas ainda abertos.

### Processos, Threads e Serviços

Um aplicativo do Windows é composto de processos. O aplicativo pode ter um ou muitos processos dedicados a ele. Um processo é qualquer programa em execução no momento. Cada processo que é executado é composto de pelo menos uma thread. Uma thread é uma parte do processo que pode ser executado. O processador executa cálculos na thread. Para configurar processos do Windows, procure o Gerenciador de Tarefas

Todos os threads dedicados a um processo estão contidos no mesmo espaço de endereço. Isso significa que esses threads podem não acessar o espaço de endereço de qualquer outro processo. Isso evita a corrupção de outros processos. Como Windows é multitarefas, vários threads podem ser executados ao mesmo tempo. A quantidade de threads que podem ser executados ao mesmo tempo depende do número de processadores do computador.

Alguns dos processos executados pelo Windows são serviços. Estes são programas que são executados em segundo plano para suportar o sistema operacional e as aplicações. Eles podem ser configurados para iniciar automaticamente quando o Windows for inicializado ou podem ser iniciados manualmente. Eles também podem ser interrompidos, reiniciados ou desativados.

Os serviços fornecem funcionalidade de longa execução, como sem fio ou acesso a um servidor FTP. Para configurar os Serviços do Windows, procure serviços.

Tenha muito cuidado ao manipular as configurações desses serviços. Alguns programas dependem de um ou mais serviços para funcionar corretamente. Encerrar um serviço pode afetar negativamente aplicativos ou outros serviços.

### Alocação e identificadores de memória

Um computador funciona armazenando instruções na RAM até que a CPU os processe. O espaço de endereço virtual para um processo é o conjunto de endereços virtuais que o processo pode usar. O endereço virtual não é o local físico real na memória, mas uma entrada em uma tabela de página que é usada para traduzir o endereço virtual para o endereço físico.

Cada processo em um computador Windows de 32 bits suporta um espaço de endereço virtual que permite endereçar até 4 gigabytes. Cada processo num computador Windows de 64 bits suporta um espaço de endereço virtual de 8 terabytes.

Cada processo de espaço do usuário é executado em um espaço de endereço privado, separado de outros processos de espaço do usuário. Quando o processo de espaço do usuário precisa acessar recursos do kernel, ele deve usar um identificador de processo. Isso ocorre porque o processo de espaço do usuário não tem permissão para acessar diretamente esses recursos do kernel. O identificador do processo fornece o acesso necessário para o processo de espaço do usuário sem uma conexão direta com ele.

Uma ferramenta poderosa para visualizar a alocação de memória é RAMMap, que é mostrado na figura. RAMMap faz parte do conjunto de ferramentas do Windows Sysinternals. Ele pode ser baixado da Microsoft. RAMMap fornece uma riqueza de informações sobre como o Windows alocou memória do sistema para o kernel, processos, drivers e aplicativos.

### O Registro do Windows

O Windows armazena todas as informações sobre hardware, aplicativos, usuários e configurações do sistema em um banco de dados grande conhecido como o Registro. As formas como esses objetos interagem também são registradas, como quais arquivos um aplicativo abre e todos os detalhes de propriedade de pastas e aplicativos. O registro é um banco de dados hierárquico onde o nível mais alto é conhecido como um ramo, abaixo existem chaves, seguido por subchaves. Os valores armazenam dados e são armazenados nas chaves e subchaves. Uma chave do Registro pode ter até 512 níveis de profundidade.

A tabela lista os cinco ramos do registro do Windows.

![[Pasted image 20241213182837.png]]

Novas seções (hives) não podem ser criadas. As chaves do Registro e os valores nas seções podem ser criados, modificados ou excluídos por uma conta com privilégios administrativos. Como mostrado na figura, a ferramenta **regedit.exe** é usada para modificar o registro. Tenha muito cuidado ao usar esta ferramenta. Alterações menores no registro podem ter efeitos maciços ou mesmo catastróficos.

A navegação no registro é muito semelhante ao explorador de arquivos do Windows. Use o painel esquerdo para navegar nas seções (hives) e na estrutura abaixo dele e use o painel direito para ver o conteúdo do item realçado no painel esquerdo. Com tantas chaves e subchaves, o caminho da chave pode se tornar muito longo. O caminho é exibido na parte inferior da janela para referência. Como cada chave e subchave é essencialmente um contêiner, o caminho é representado muito parecido com uma pasta em um sistema de arquivos. A barra invertida () é usada para diferenciar a hierarquia do banco de dados.

As chaves do Registro podem conter uma subchave ou um valor. Os diferentes valores que as chaves podem conter são os seguintes:

- **REG\ _BINARY** - Números ou valores booleanos
- **REG\ _DWORD** - Números maiores que 32 bits ou dados brutos
- **REG\ _SZ** - Valores de cadeia

Como o registro contém quase toda infomação do sistema operacional e do usuário, é essencial garantir que ele não seja comprometido. Aplicativos potencialmente mal-intencionados podem adicionar chaves do Registro para que elas sejam iniciadas quando o computador for iniciado. Durante uma inicialização normal, o usuário não verá o programa iniciar porque a entrada está no registro e o aplicativo não exibe janelas ou indicação de início quando o computador for inicializado. Um keylogger, por exemplo, seria devastador para a segurança de um computador se ele fosse iniciado na inicialização sem o conhecimento ou consentimento do usuário. Ao executar auditorias de segurança normais ou corrigir um sistema infectado, revise os locais de inicialização do aplicativo no registro para garantir que cada item seja conhecido e seguro para ser executado.

O registro também contém a atividade que um usuário executa durante o uso diário normal do computador. Isso inclui o histórico de dispositivos de hardware, incluindo todos os dispositivos que foram conectados ao computador, incluindo o nome, o fabricante e o número de série. Outras informações, como quais documentos um usuário e um programa abriram, onde eles estão localizados e quando foram acessados, são armazenadas no registro. Isso tudo é uma informação muito útil quando uma investigação forense precisa ser realizada.