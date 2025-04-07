# Processo de comunicação de rede

### Redes de Vários Tamanhos

**Redes domésticas pequenas**

As redes domésticas pequenas conectam alguns computadores entre si e com a Internet.

**Redes para pequenos escritórios e escritórios domésticos**

A rede SOHO permite que computadores em um escritório em casa ou em um escritório remoto se conectem a uma rede corporativa, ou acessem recursos compartilhados centralizados.

**Redes médias a grandes**

Redes de médio a grande porte, como as usadas por empresas e escolas, podem ter muitos locais com centenas ou milhares de hosts interconectados.

**Rede Mundial**

A internet é uma rede de redes que conecta centenas de milhões de computadores em todo o mundo.

### Comunicações cliente-servidor

Todos os computadores que estão conectados a uma rede e participam diretamente da comunicação em rede são classificados como hosts. Os hosts também são chamados de dispositivos finais, terminais ou nós. Grande parte da interação entre dispositivos finais é o tráfego cliente-servidor. Por exemplo, quando você acessa uma página da Web na Internet, seu navegador (o cliente) está acessando um servidor. Quando você envia uma mensagem de e-mail, seu cliente de e-mail se conectará a um servidor de e-mail.

Servidores são simplesmente computadores com software especializado. Este software permite que os servidores forneçam informações a outros dispositivos finais na rede. Um servidor pode ser de propósito único, fornecendo apenas um serviço, como páginas da Web. Um servidor pode ser multiuso, fornecendo uma variedade de serviços, como páginas da Web, e-mail e transferências de arquivos.

Os computadores cliente têm software instalado, como navegadores da Web, clientes de email e aplicativos de transferência de arquivos. Este software permite que eles solicitem e exibam as informações obtidas do servidor. Um único computador pode também executar vários tipos de software cliente. Por exemplo, um usuário pode verificar e-mail e visualizar uma página da web enquanto ouve rádio na Internet.

- **Servidor de arquivos** - o servidor de arquivos armazena arquivos corporativos e de usuários em um local central.
- **Servidor Web** - O servidor web executa software de servidor web que permite que muitos computadores acessem páginas da web.
- **Servidor de e-mail** - O servidor de e-mail executa o software de servidor de e-mail que permite que os e-mails sejam enviados e recebidos.

1. O servidor de arquivos armazena arquivos corporativos e de usuários em um local central. Os dispositivos clientes acessam esses arquivos com softwares clientes, como o Windows Explorer.
    
2. O servidor da Web executa um software de servidor da Web e os clientes usam seu software de navegador, como o Windows Microsoft Edge, para acessar páginas da Web no servidor.
    
3. O Servidor de e-mail executa o software do servidor de e-mail. Os clientes usam o software de cliente de e-mail, como o Microsoft Outlook, para acessar os e-mails no servidor.

### Sessões Típicas

Um usuário típico de rede na escola, em casa ou no escritório normalmente usa algum tipo de dispositivo de computação para estabelecer muitas conexões com servidores de rede. Esses servidores podem estar localizados na mesma sala ou em todo o mundo.

### Traçando o Caminho

Nós tendemos a pensar sobre as redes de dados que usamos em nossas vidas diárias como pensamos em dirigir um carro. Nós realmente não nos importamos com o que acontece no motor, desde que o carro nos leve para onde queremos ir. No entanto, assim como o mecânico de um carro conhece os detalhes de como um carro opera, analistas de segurança cibernética precisam ter uma compreensão profunda de como as redes operam.

Quando nos conectamos a um site para ler mídias sociais ou fazer compras, raramente nos preocupamos com como nossos dados chegam ao site e como os dados do site nos acessam. Não estamos cientes das muitas tecnologias que nos permitem usar a internet. Uma combinação de cabos de cobre e fibra óptica que passam por terra e sob o oceano transportam tráfego de dados. Tecnologias sem fio e satélite de alta velocidade também são usadas. Essas conexões conectam instalações de telecomunicações e provedores de serviços de internet (ISP) que são distribuídos em todo o mundo, como mostrado na figura. Esses ISPs globais de Nível 1 e Nível 2 conectam partes da Internet, geralmente por meio de um Ponto de Troca de Internet (IXP). Redes maiores se conectarão a redes Nível 2 por meio de um Ponto de Presença (PoP), que geralmente é um local no edifício onde as conexões físicas com o ISP são feitas. Os ISPs de Nível 3 conectam residências e empresas à Internet.

Devido às diferentes relações entre ISPs e empresas de telecomunicações, o tráfego de um computador para um servidor de Internet pode tomar muitos caminhos. O tráfego de um usuário em um país pode tomar um caminho muito indireto para chegar ao seu destino. O tráfego pode primeiro viajar do ISP local para uma instalação que tenha conexões com muitos outros ISPs. O tráfego de internet de um usuário pode ir muitas centenas de milhas em uma direção apenas para ser roteado em uma direção completamente diferente para chegar ao seu destino. Parte do tráfego pode tomar certas rotas para chegar ao destino e, em seguida, tomar rotas completamente diferentes para retornar.

Os analistas de segurança cibernética devem ser capazes de determinar a origem do tráfego que entra na rede e o destino do tráfego que a deixa. Entender o caminho que o tráfego de rede leva é essencial para isso.

# Protocolos de comunicação

### O que são Protocolos?

Simplesmente ter uma conexão física com ou sem fio entre os dispositivos finais não é suficiente para permitir a comunicação. Para que ocorra comunicação, os dispositivos devem saber “como” se comunicar. A comunicação, seja cara a cara ou em rede, é governada por regras chamadas de protocolos. Esses protocolos são específicos para o tipo de método de comunicação em questão.

Por exemplo, considere duas pessoas se comunicando cara a cara. Antes da comunicação, devem concordar sobre como se comunicar. Se a comunicação for através de voz, devem primeiro acordar o idioma. Em seguida, quando há uma mensagem para compartilhar, eles devem formatar a mensagem de forma que seja compreensível. Por exemplo, se alguém usa o idioma inglês, mas a estrutura de frases for fraca, a mensagem poderá facilmente ser mal interpretada.

Da mesma forma, os protocolos de rede especificam muitos recursos da comunicação de rede.

### Protocolos de rede

Os protocolos de rede fornecem os meios para que os computadores se comuniquem em redes. Os protocolos de rede determinam as opções de codificação, formatação, encapsulamento, tamanho, tempo e entrega da mensagem. Os protocolos de rede definem um formato e um conjunto de regras comuns para a troca de mensagens entre dispositivos. Estes são alguns protocolos de rede comuns: Hypertext Transfer Protocol (HTTP), Transmission Control Protocol (TCP) e Internet Protocol (IP). Como analista de segurança cibernética, você deve estar muito familiarizado com a estrutura dos dados de protocolo e como os protocolos funcionam nas comunicações de rede.

**Observação**: neste curso, IP se refere aos protocolos IPv4 e IPv6. IPv6 é a versão mais recente do IP e eventualmente substituirá o IPv4 mais comum.

### Conjunto de protocolos TCP/IP

Hoje, o conjunto de protocolos TCP/IP inclui muitos protocolos e continua a evoluir para oferecer suporte a novos serviços. A Figura mostra alguns dos mais populares.
![[Pasted image 20241219205701.png]]

TCP/IP é o conjunto de protocolos usado pela internet e as redes de hoje. O TCP/IP tem dois aspectos importantes para fornecedores e fabricantes:

- **Conjunto de protocolos de padrão aberto** - Isso significa que está disponível gratuitamente ao público e pode ser usado por qualquer fornecedor em seu hardware ou software.
- **Conjunto de protocolos com base em padrões** - isso significa que foi endossado pela indústria de rede e aprovado por uma organização de padrões. Isso garante que produtos de diferentes fabricantes possam interoperar com êxito.

**Camada de aplicação**

Sistema de nomes

- **DNS** - Sistema de nomes de domínio. Converte nomes de domínio, como cisco.com, em endereços IP.

Configuração de hosts

- **DHCPv4** - Protocolo de configuração de host dinâmico para IPv4. Um servidor DHCPv4 atribui dinamicamente informações de endereçamento IPv4 aos clientes DHCPv4 na inicialização e permite que os endereços sejam reutilizados quando não forem mais necessários.
- **DHCPv6** - Protocolo de Configuração do Host Dinâmico para IPv6. DHCPv6 é semelhante ao DHCPv4. Um servidor DHCPv6 atribui dinamicamente informações de endereçamento IPv6 aos clientes DHCPv6 na inicialização.
- **SLAAC** - Configuração automática de endereço sem estado. Um método que permite que um dispositivo obtenha suas informações de endereçamento IPv6 sem usar um servidor DHCPv6.

E-mail

- **SMTP** -Protocolo de transferência de correio simples. Permite que os clientes enviem e-mails para um servidor de e-mail e permite que os servidores enviem e-mails para outros servidores.
- **POP3** - Post Office Protocol versão 3. Permite que os clientes recuperem e-mails de um servidor de e-mail e baixem o e-mail para o aplicativo de e-mail local do cliente.
- **IMAP** - Protocolo de Acesso à Mensagem na Internet. Permite que os clientes acessem o e-mail armazenado em um servidor de e-mail e também mantenham o e-mail no servidor.

Transferência de arquivos

- **FTP** - Protocolo de transferência de arquivos. Define as regras que permitem que um usuário em um host acesse e transfira arquivos para e de outro host em uma rede. O FTP é um protocolo de entrega de arquivos confiável, orientado a conexão e reconhecido.
- **SFTP** - Protocolo de transferência de arquivos SSH. Como uma extensão do protocolo Secure Shell (SSH), o SFTP pode ser usado para estabelecer uma sessão segura de transferência de arquivos na qual a transferência é criptografada. SSH é um método para login remoto seguro que normalmente é usado para acessar a linha de comando de um dispositivo.
- **TFTP** - Protocolo de Transferência de Arquivos Trivial. Um protocolo de transferência de arquivos simples e sem conexão com entrega de arquivos não confirmada e de melhor esforço. Ele usa menos sobrecarga que o FTP.

Web e serviço Web

- **HTTP** - Protocolo de transferência de hipertexto. Um conjunto de regras para a troca de texto, imagens gráficas, som, vídeo e outros arquivos multimídia na World Wide Web.
- **HTTPS** - HTTP seguro. Uma forma segura de HTTP que criptografa os dados que são trocados pela World Wide Web.
- **REST** - Representational State Transfer. Um serviço Web que utiliza interfaces de programação de aplicações (APIs) e pedidos HTTP para criar aplicações Web.

**Camada de transporte**

Conexão orientada

- **TCP** - Protocolo de controle de transmissão. Permite a comunicação confiável entre processos executados em hosts separados e fornece transmissões confiáveis e reconhecidas que confirmam a entrega bem-sucedida.

Sem Conexão

- **UDP** - Protocolo de datagrama do usuário. Permite que um processo em execução em um host envie pacotes para um processo em execução em outro host. No entanto, o UDP não confirma a transmissão bem-sucedida do datagrama.

**Camada de Internet**

Protocolo IP (Internet Protocol)

- **IPv4** - Protocolo da Internet versão 4. Recebe segmentos de mensagem da camada de transporte, empacota mensagens em pacotes e endereça pacotes para entrega de ponta a ponta através de uma rede. O IPv4 usa um endereço de 32 bits.
- **IPv6** - IP versão 6. Semelhante ao IPv4, mas usa um endereço de 128 bits.
- **NAT** - Tradução de endereços de rede. Converte endereços IPv4 de uma rede privada em endereços IPv4 públicos globalmente exclusivos.

Mensagens

- **ICMPv4** - Protocolo de mensagens de controle da Internet para IPv4. Fornece feedback de um host de destino para um host de origem sobre erros na entrega de pacotes.
- **ICMPv6** - ICMP para IPv6. Funcionalidade semelhante ao ICMPv4, mas é usada para pacotes IPv6.
- **ICMPv6 ND** - descoberta de vizinho ICMPv6. Inclui quatro mensagens de protocolo que são usadas para resolução de endereço e detecção de endereço duplicado.

Protocolos de roteamento

- **OSPF** - Abrir o caminho mais curto primeiro. Protocolo de roteamento de estado de link que usa um experimento hierárquico baseado em áreas. OSPF é um protocolo de roteamento interno padrão aberto.
- **EIGRP** - Protocolo de roteamento de gateway interno aprimorado. Um protocolo de roteamento de padrão aberto desenvolvido pela Cisco que usa uma métrica composta com base na largura de banda, atraso, carga e confiabilidade.
- **BGP** - Protocolo de gateway de fronteira. Um protocolo de roteamento de gateway externo padrão aberto usado entre os Internet Service Providers (ISPs). O BGP também é comumente usado entre os ISPs e seus grandes clientes particulares para trocar informações de roteamento.

**Camada de acesso à rede**

Resolução de endereços

- **ARP** - Protocolo de Resolução de Endereço. Fornece mapeamento de endereço dinâmico entre um endereço IPv4 e um endereço de hardware.
    
    **Observação**: Você pode ver outro estado de documentação que o ARP opera na Camada da Internet (Camada OSI 3). No entanto, neste curso, afirmamos que o ARP opera na camada de Acesso à Rede (OSI Camada 2) porque seu objetivo principal é descobrir o endereço MAC do destino. Um endereço MAC é um endereço da camada 2.
    

Protocolos de link de dados

- **Ethernet** - define as regras para os padrões de fiação e sinalização da camada de acesso à rede.
- **WLAN** - Rede local sem fio. Define as regras para sinalização sem fio nas frequências de rádio de 2,4 GHz e 5 GHz.

### Formatação e Encapsulamento de Mensagens

Quando uma mensagem é enviada da origem para o destino, deve usar um formato ou uma estrutura específica. Os formatos da mensagem dependem do tipo de mensagem e do canal usado para entregá-la.

**Rede**

Semelhante ao envio de uma carta, uma mensagem enviada por uma rede de computadores segue regras específicas de formato para que ela seja entregue e processada.

Internet Protocol (IP) é um protocolo com uma função semelhante ao exemplo de envelope. Na figura, os campos do pacote IPv6 (Internet Protocol versão 6) identificam a origem do pacote e seu destino. IP é responsável por enviar uma mensagem da origem da mensagem para o destino através de uma ou mais redes.

**Nota**: Os campos do pacote IPv6 são discutidos em detalhes em outro módulo.
![[Pasted image 20241219205917.png]]

### Tamanho da Mensagem

**Rede**

Do mesmo modo, quando uma mensagem longa é enviada de um host a outro em uma rede, é necessário dividir a mensagem em partes menores. As regras que regem o tamanho das partes, ou quadros, transmitidos pela rede são muito rígidas. Também podem diferir, dependendo do canal usado. Os quadros que são muito longos ou muito curtos não são entregues.

As restrições de tamanho dos quadros exigem que o host origem divida uma mensagem longa em pedaços individuais que atendam aos requisitos de tamanho mínimo e máximo. A mensagem longa será enviada em quadros separados, e cada um contém uma parte da mensagem original. Cada quadro também terá suas próprias informações de endereço. No host destino, as partes individuais da mensagem são reconstruídas na mensagem original.

### Temporização de Mensagem

O tempo de mensagens também é muito importante nas comunicações de rede. A temporização da mensagem inclui o seguinte:

- **Controle de fluxo** - este é o processo de gerenciamento da taxa de transmissão de dados. O controle de fluxo define quanta informação pode ser enviada e a velocidade com que pode ser entregue. Por exemplo, se uma pessoa fala muito rapidamente, pode ser difícil para o receptor ouvir e entender a mensagem. Na comunicação de rede, existem protocolos de rede usados pelos dispositivos de origem e destino para negociar e gerenciar o fluxo de informações.
- **Tempo limite de resposta** - se uma pessoa fizer uma pergunta e não ouvir uma resposta dentro de um período de tempo aceitável, a pessoa presumirá que não haverá resposta e reagirá de acordo. A pessoa pode repetir a pergunta ou prosseguir com a conversa. Os hosts da rede usam protocolos de rede que especificam quanto tempo esperar pelas respostas e que ação executar se ocorrer um tempo limite de resposta.
- **Método de acesso -** determinar quando alguém pode enviar uma mensagem. Clique em Reproduzir na figura para ver uma animação de duas pessoas conversando ao mesmo tempo e, em seguida, ocorre uma "colisão de informações", e é necessário que as duas se afastem e iniciem novamente. Da mesma forma, quando um dispositivo deseja transmitir em uma LAN sem fio, é necessário que a placa de interface de rede (NIC) da WLAN determine se a mídia sem fio está disponível.

### Unicast, broadcast ou multicast

Uma mensagem pode ser entregue de diferentes maneiras. Às vezes, uma pessoa deseja transmitir informações a uma única pessoa. Em outros casos, a pessoa pode precisar enviar informações a um grupo de uma só vez, ou até mesmo para todas as pessoas na mesma área.

Hosts em uma rede usam opções de entrega semelhantes para se comunicar. Esses métodos de comunicação são chamados unicast, multicast e broadcast.

Unicast

Uma opção de entrega um para um é chamada unicast, o que significa que há um único destino para a mensagem.

Multicast

Quando um host precisa enviar mensagens por meio de uma opção de entrega um para muitos, ele utiliza um formato chamado de multicast.

Broadcast

Se todos os hosts na rede precisam receber a mensagem ao mesmo tempo, um broadcast pode ser usado. O broadcast representa uma opção de entrega de mensagem um para todos.

### Os Benefícios de Se Usar um Modelo de Camadas

Você não pode realmente assistir a pacotes reais viajando através de uma rede real da mesma forma que pode assistir os componentes de um carro sendo montados em uma linha de montagem. Então ajuda ter um jeito de pensar em rede para você imaginar o que está acontecendo. Um modelo é útil nessas situações.

Conceitos complexos, como a forma como uma rede opera, podem ser difíceis de explicar e compreender. Por esta razão, um modelo em camadas é usado para modularizar as operações de uma rede em camadas gerenciáveis.

Estes são os benefícios do uso de um modelo em camadas para descrever protocolos e operações de rede:

- Auxiliar no projeto de protocolo porque os protocolos que operam em uma camada específica têm informações definidas sobre as quais eles atuam e uma interface definida para as camadas acima e abaixo.
- Estimular a competição porque os produtos de diferentes fornecedores podem trabalhar em conjunto.
- Impedir que mudanças de tecnologia ou capacidade em uma camada afetem outras camadas acima e abaixo.
- Fornecer um idioma comum para descrever funções e capacidades de rede.

Como mostrado na figura, existem dois modelos em camadas que são usados para descrever operações de rede:

- Modelo de referência OSI (Open System Interconnection)
- Modelo de referência TCP/IP

![[Pasted image 20241219210250.png]]

### O Modelo de Referência OSI

O modelo de referência OSI fornece uma extensa lista de funções e serviços que podem ocorrer em cada camada. Esse tipo de modelo fornece consistência em todos os tipos de protocolos e serviços de rede, descrevendo o que deve ser feito em uma camada específica, mas não prescrevendo como deve ser realizado.

Ele também descreve a interação de cada camada com as camadas diretamente acima e abaixo. Os protocolos TCP/IP discutidos neste curso estão estruturados com base nos modelos OSI e TCP/IP. A tabela mostra detalhes sobre cada camada do modelo OSI. A funcionalidade de cada camada e o relacionamento entre elas ficarão mais evidentes no decorrer deste curso, conforme os protocolos são discutidos com mais detalhes.
![[Pasted image 20241219210345.png]]**Nota**: Enquanto as camadas do modelo TCP / IP são referenciadas apenas pelo nome, as sete camadas do modelo OSI são mais frequentemente referenciadas pelo número do que pelo nome. Por exemplo, a camada física é referida como Camada 1 do modelo OSI, a camada de enlace de dados é a Camada 2 e assim por diante.

### O Modelo de Protocolo TCP/IP

O modelo de protocolo TCP / IP para comunicações entre redes foi criado no início dos anos 70 e às vezes é chamado de modelo da Internet. Esse tipo de modelo corresponde à estrutura de um conjunto de protocolos específico. O modelo TCP/IP é um modelo de protocolo porque descreve as funções que ocorrem em cada camada de protocolos dentro da suíte TCP/IP. O TCP/IP também é usado como um modelo de referência. A tabela mostra detalhes sobre cada camada do modelo OSI.
![[Pasted image 20241219210432.png]]
As definições do padrão e dos protocolos TCP/IP são discutidas em um fórum público e definidas em um conjunto publicamente disponível de documentos de solicitação de comentário (RFC) da IETF. Um RFC é criado por engenheiros de rede e enviado a outros membros do IETF para comentários.

# Encapsulamento de dados

### Segmentando Mensagens

Conhecer o modelo de referência OSI e o modelo de protocolo TCP/IP será útil quando você aprender sobre como os dados são encapsulados à medida que eles se movem através de uma rede. Não é tão simples como uma carta física sendo enviada através do sistema de correio.

Em teoria, uma única comunicação, como um vídeo ou uma mensagem de e-mail com muitos anexos grandes, poderia ser enviada através de uma rede de uma fonte para um destino como um fluxo maciço e ininterrupto de bits. No entanto, isso criaria problemas para outros dispositivos que precisassem usar os mesmos canais de comunicação ou links. Esses grandes fluxos de dados resultariam em atrasos consideráveis. Além disso, se algum link na infra-estrutura de rede interconectada falhasse durante a transmissão, a mensagem completa seria perdida e teria que ser retransmitida na íntegra.

Uma melhor abordagem é dividir os dados em pedaços menores e mais gerenciáveis para o envio pela rede. Segmentação é o processo de dividir um fluxo de dados em unidades menores para transmissões através da rede. A segmentação é necessária porque as redes de dados usam o conjunto de protocolos TCP/IP enviar dados em pacotes IP individuais. Cada pacote é enviado separadamente, semelhante ao envio de uma carta longa como uma série de cartões postais individuais. Pacotes que contêm segmentos para o mesmo destino podem ser enviados por caminhos diferentes.

Isso leva à segmentação de mensagens com dois benefícios principais:

- **Aumenta a velocidade** - como um grande fluxo de dados é segmentado em pacotes, grandes quantidades de dados podem ser enviadas pela rede sem obstruir um link de comunicação. Isso permite que muitas conversas diferentes sejam intercaladas na rede chamada multiplexação.
- **Aumenta a eficiência** - se um único segmento não consegue alcançar seu destino devido a uma falha na rede ou congestionamento da rede, apenas esse segmento precisa ser retransmitido em vez de reenviar todo o fluxo de dados.
### Sequenciamento

O desafio de utilizar segmentação e multiplexação para a transmissão de mensagens por uma rede é o nível de complexidade que é agregado ao processo. Imagine se você tivesse que enviar uma carta de 100 páginas, mas cada envelope poderia conter apenas uma página. Portanto, seriam necessários 100 envelopes e cada envelope precisaria ser endereçado individualmente. É possível que a carta de 100 páginas em 100 envelopes diferentes chegue fora de ordem. Consequentemente, as informações contidas no envelope teriam de incluir um número sequencial para garantir que o destinatário pudesse remontar as páginas na ordem correcta.

Nas comunicações em rede, cada segmento da mensagem deve passar por um processo semelhante para garantir que chegue ao destino correto e possa ser remontado no conteúdo da mensagem original, conforme mostrado na figura. O TCP é responsável por sequenciar os segmentos individuais.

### Unidades de Dados de Protocolo

À medida que os dados da aplicação são passados pela pilha de protocolos em seu caminho para serem transmitidos pelo meio físico de rede, várias informações de protocolos são adicionadas em cada nível. Isso é conhecido como o processo de encapsulamento.

**Nota**: Embora o UDP PDU seja chamado de datagrama, os pacotes IP às vezes também são chamados de datagramas IP.

O formato que uma parte de dados assume em qualquer camada é chamado de unidade de dados de protocolo (PDU). Durante o encapsulamento, cada camada sucessora encapsula a PDU que recebe da camada superior de acordo com o protocolo sendo usado. Em cada etapa do processo, uma PDU possui um nome diferente para refletir suas novas funções. Embora não haja uma convenção de nomenclatura universal para PDUs, neste curso, as PDUs são nomeadas de acordo com os protocolos do conjunto TCP / IP. As PDUs para cada forma de dados são mostradas na figura.
![[Pasted image 20241219210811.png]]
- Dados - o termo genérico para a PDU usada na camada de aplicação;
- Segmento - PDU da camada de transporte;
- Pacote - PDU da camada de rede;
- Quadro - PDU da camada de enlace de dados
- Bits - PDU da camada física usada ao transmitir dados fisicamente pela mídia.

**Nota**: Se o cabeçalho de transporte é TCP, então é um segmento. Se o cabeçalho Transporte é UDP, então é um datagrama.

### Três Endereços

Os protocolos de rede exigem que os endereços sejam usados para comunicação de rede. O endereçamento é usado pelo cliente para enviar solicitações e outros dados para um servidor. O servidor usa o endereço do cliente para retornar os dados solicitados ao cliente que o solicitou.

Todas as camadas de transporte OSI, rede e link de dados usam endereçamento de alguma forma. A camada de transporte usa endereços de protocolo na forma de números de porta para identificar aplicativos de rede que devem manipular dados de cliente e servidor. A camada de rede especifica endereços que identificam as redes às quais os clientes e servidores estão conectados e os próprios clientes e servidores. Finalmente, a camada de link de dados especifica os dispositivos na LAN local que devem lidar com quadros de dados. Todos os três endereços são necessários para a comunicação cliente-servidor, como mostrado na figura.
![[Pasted image 20241219210939.png]]

### Exemplo de Encapsulamento

Quando as mensagens estão sendo enviadas em uma rede, o processo de encapsulamento funciona de cima para baixo. Em cada camada, as informações da camada superior são consideradas dados encapsulados no protocolo. Por exemplo, o segmento TCP é considerado dados dentro do pacote IP.

### Exemplo de desencapsulamento

Esse processo é revertido no host de recebimento e é conhecido como desencapsulamento. O desencapsulamento é o processo usado por um dispositivo receptor para remover um ou mais cabeçalhos de protocolo. Os dados são desencapsulados à medida que se movem na pilha em direção à aplicação do usuário final.