# Detalhes de PDU IP

### IPv4 e IPv6

O IP foi projetado como um protocolo sem conexão de Camada 3. Ele fornece as funções necessárias para entregar um pacote de um host de origem a um host de destino por meio de um sistema interconectado de redes. O protocolo não foi projetado para rastrear e gerenciar o fluxo de pacotes. Essas funções, se necessárias, são executadas principalmente pelo TCP na camada 4.

O IP não faz nenhum esforço para validar se o endereço IP de origem contido em um pacote realmente veio dessa origem. Por esse motivo, os agentes de ameaças podem enviar pacotes usando um endereço IP de origem falsificado. Além disso, os agentes da ameaça podem adulterar os outros campos do cabeçalho IP para realizar seus ataques. Portanto, é importante que os analistas de segurança entendam os diferentes campos dos cabeçalhos IPv4 e IPv6.
### O cabeçalho do pacote IPv4
![[Pasted image 20250123224050.png]]
A tabela descreve os campos de cabeçalho IPv4.
![[Pasted image 20250123224530.png]]
![[Pasted image 20250123224543.png]]

### O cabeçalho do pacote IPv6

![[Pasted image 20250123224621.png]]

A tabela descreve os campos de cabeçalho IPv6.
![[Pasted image 20250123224642.png]]
Um pacote IPv6 também pode conter cabeçalhos de extensão (EH) que fornecem informações opcionais da camada de rede. Opcionais, os cabeçalhos de extensão ficam posicionados entre o cabeçalho IPv6 e a carga. EHs são usados para fragmentação, segurança, suporte à mobilidade e muito mais.

Ao contrário de IPv4, os roteadores não fragmentam os pacotes IPv6 roteados.

# Vulnerabilidades de IP

Existem diferentes tipos de ataques que visam IP. A tabela lista alguns dos ataques mais comuns relacionados a IP.
![[Pasted image 20250123224749.png]]

### Ataques ICMP

O ICMP foi desenvolvido para transportar mensagens de diagnóstico e relatar condições de erro quando rotas, hosts e portas não estão disponíveis. Mensagens ICMP são geradas por dispositivos quando ocorre um erro de rede ou uma interrupção. O comando ping é uma mensagem ICMP gerada pelo usuário, chamada de solicitação de eco, usada para verificar a conectividade com um destino.

Os agentes de ameaças usam o ICMP para ataques de reconhecimento e varredura. Isso permite que eles lancem ataques de coleta de informações para mapear uma topologia de rede, descobrir quais hosts estão ativos (acessíveis), identificar o sistema operacional do host (impressão digital do sistema operacional) e determinar o estado de um firewall.

Os atores de ameaças também usam ICMP para ataques DoS e DDoS, conforme mostrado no ataque de inundação ICMP na figura.
![[Pasted image 20250123224902.png]]

**Nota**: O ICMP para IPv4 (ICMPv4) e o ICMP para IPv6 (ICMPv6) são suscetíveis a tipos semelhantes de ataques.

A tabela lista mensagens ICMP comuns de interesse para os atores da ameaça.
![[Pasted image 20250123224920.png]]

As redes devem ter uma filtragem rigorosa da lista de controle de acesso ICMP (ACL) na borda da rede para evitar a sondagem ICMP vindo da Internet. Os analistas de segurança devem ser capazes de detectar ataques relacionados ao ICMP, observando o tráfego capturado e os arquivos de log. No caso de grandes redes, os dispositivos de segurança, como firewalls e sistemas de detecção de intrusão (IDS), devem detectar tais ataques e gerar alertas para os analistas de segurança.

### Ataques de amplificação e reflexão

Os agentes de ameaças geralmente usam técnicas de amplificação e reflexão para criar ataques de negação de serviço (DoS). O exemplo na figura ilustra como uma técnica de amplificação e reflexão chamada ataque Smurf é usada para sobrecarregar um host alvo.![[Pasted image 20250123225131.png]]
**Nota**: Novas formas de ataques de amplificação e reflexão, como ataques de reflexão e amplificação com base no DNS e ataques de amplificação do Network Time Protocol (NTP), agora estão sendo usados.

Os agentes de ameaças também usam ataques de exaustão de recursos. Esses ataques consomem os recursos de um host de destino para travá-lo ou consumir os recursos de uma rede.

### Ataque de Falsificação de Endereços

Os ataques de falsificação de endereço IP ocorrem quando um agente de ameaça cria pacotes com informações falsas de endereço IP de origem para ocultar a identidade do remetente ou para se passar por outro usuário legítimo. O agente de ameaças pode obter acesso a dados inacessíveis ou burlar as configurações de segurança. A falsificação é geralmente incorporada a outro ataque, como um ataque Smurf.

Os ataques de falsificação podem ser cegos ou não cegos:

- **Falsificação não cega** - O agente da ameaça pode ver o tráfego que está sendo enviado entre o host e o destino. O agente de ameaça usa a falsificação não cega para inspecionar o pacote de resposta da vítima alvo. A falsificação não cega determina o estado de um firewall e prever número de sequência. Também pode seqüestrar uma sessão autorizada.
- **Falsificação cega** - O agente da ameaça não pode ver o tráfego que está sendo enviado entre o host e o destino. A falsificação cega é usada em ataques de negação de serviço.

Os ataques de falsificação de endereço MAC são usados quando os atores de ameaças têm acesso à rede interna. Os agentes de ameaças alteram o endereço MAC de seu host para corresponder a outro endereço MAC conhecido de um host de destino, conforme mostrado na figura. O host atacante envia um quadro pela rede com o endereço MAC recém-configurado. Quando o switch recebe o quadro, ele examina o endereço MAC de origem.![[Pasted image 20250123225349.png]]
O switch substitui a entrada atual da tabela CAM e atribui o endereço MAC à nova porta, como mostrado na figura. Em seguida, encaminha os quadros destinados ao host de destino para o host atacante.

![[Pasted image 20250123225419.png]]
A falsificação de aplicativos ou serviços é outro exemplo de falsificação. Um agente de ameaça pode conectar um servidor DHCP não autorizado para criar uma condição MiTM.

# Vulnerabilidades TCP e UDP

### Cabeçalho do segmento TCP

Enquanto alguns ataques têm como alvo o IP, este tópico discute ataques que têm como alvo o TCP e o UDP.

As informações do segmento TCP aparecem imediatamente após o cabeçalho IP. Os campos do segmento TCP e os sinalizadores para o campo bits de controle são exibidos na figura.![[Pasted image 20250123225827.png]]
A seguir, os seis bits de controle do segmento TCP:

- **URG** - Campo de ponteiro urgente significativo.
- **ACK** - Campo de confirmação significativo
- **PSH** - Função Push.
- **RST** - Redefina a conexão
- **SYN** - Sincronizar números de sequência
- **FIN** - Não há mais dados do remetente

### Serviços TCP

O TCP fornece estes serviços:

- **Entrega confiável** - O TCP incorpora reconhecimentos para garantir a entrega, em vez de confiar nos protocolos da camada superior para detectar e resolver erros. Se uma confirmação não for recebida à tempo, o remetente retransmitirá os dados. Exigir reconhecimentos dos dados recebidos pode causar atrasos substanciais. Exemplos de protocolos da camada de aplicação que usam a confiabilidade do TCP incluem HTTP, SSL / TLS, FTP, transferências de zona DNS e outros.
- **Controle de fluxo** - O TCP implementa o controle de fluxo para solucionar esse problema. Em vez de reconhecer um segmento de cada vez, vários segmentos podem ser reconhecidos com um único segmento de reconhecimento.
- **Comunicação com estado** - A comunicação com estado TCP entre duas partes ocorre durante o aperto de mãos triplo TCP. Antes que os dados possam ser transferidos usando o TCP, um aperto de mãos triplo abre a conexão TCP, conforme mostrado na figura. Se ambos os lados concordarem com a conexão TCP, os dados poderão ser enviados e recebidos por ambas as partes usando o TCP.
### Aperto de mão de três vias TCP
![[Pasted image 20250123230024.png]]
Uma conexão TCP é estabelecida em três etapas:

1. O cliente iniciador requisita uma sessão de comunicação cliente-servidor com o servidor.
2. O servidor confirma a sessão de comunicação cliente-servidor e requisita uma sessão de comunicação de servidor-cliente.
3. O cliente iniciador confirma a sessão de comunicação de servidor-cliente.

### Ataques TCP

Aplicações em Rede usam portas TCP ou UDP. Os atores de ameaças realizam varreduras de portas dos dispositivos de destino para descobrir quais serviços eles oferecem.

**Ataque de Inundação de SYN TCP**

O ataque de inundação SYN TCP explora o aperto de mãos triplo do TCP. A figura mostra um agente de ameaça enviando continuamente pacotes de solicitação de sessão TCP SYN com um endereço IP de origem falsificado aleatoriamente para um destino. O dispositivo de destino responde com um pacote TCP SYN-ACK ao endereço IP falsificado e aguarda um pacote TCP ACK. Essas respostas nunca chegam. Eventualmente, o host de destino é sobrecarregado com conexões TCP semi-abertas e os serviços TCP são negados a usuários legítimos.
![[Pasted image 20250123230133.png]]
1. O ator da ameaça envia várias solicitações SYN a um servidor da web.
2. O servidor da web responde com SYN-ACKs para cada solicitação SYN e aguarda a conclusão do aperto de mãos triplo. O agente da ameaça não responde aos SYN-ACKs.
3. Um usuário válido não pode acessar o servidor da Web porque o servidor da Web possui muitas conexões TCP abertas pela metade.

**Ataque de redefinição de TCP**

Um ataque de redefinição de TCP pode ser usado para encerrar as comunicações TCP entre dois hosts. A figura mostra como o TCP usa uma troca de quatro direções para fechar a conexão TCP usando um par de segmentos FIN e ACK de cada extremidade da conexão TCP. Uma conexão TCP termina quando recebe um bit RST. Essa é uma maneira abrupta de interromper a conexão TCP e informar o host de recebimento para parar imediatamente de usar a conexão TCP. Um agente de ameaça pode fazer um ataque de redefinição de TCP e enviar um pacote falsificado contendo um TCP RST para um ou ambos os pontos de extremidade.
![[Pasted image 20250123230234.png]]
O encerramento de uma sessão TCP usa o seguinte processo de troca de quatro vias:

1. Quando o cliente não tem mais dados para enviar no fluxo, ele envia um segmento com um flag FIN ligado.
2. O servidor envia ACK para confirmar o recebimento de FIN para encerrar a sessão do cliente com o servidor.
3. O servidor envia um FIN ao cliente para encerrar a sessão do servidor-para-cliente.
4. O cliente responde com um ACK para reconhecer o FIN do servidor.

**Sequestro de sessão TCP**

Sequestro de sessão TCP é outra vulnerabilidade do TCP. Embora seja difícil de conduzir, um agente de ameaça assume um host já autenticado quando ele se comunica com o alvo. O agente de ameaça deve falsificar o endereço IP de um dos hosts, prever o próximo número de sequência e enviar um ACK para o outro host. Se for bem-sucedido, o agente da ameaça poderá enviar, mas não receber, dados do dispositivo de destino.

### Operação e Cabeçalho do segmento UDP

UDP é comumente usado por DNS, DHCP, TFTP, NFS e SNMP. Também é usado com aplicações em tempo real, como streaming de mídia ou VoIP. UDP é um protocolo de camada de transporte não orientado à conexão. Ele tem uma sobrecarga muito mais baixa que o TCP, porque não é orientado a conexão e não oferece retransmissão, sequenciamento e mecanismos de controle de fluxo sofisticados que fornecem confiabilidade. A estrutura de segmentos UDP, mostrada na figura, é muito menor que a estrutura de segmentos da TCP.

**Nota**: o UDP realmente divide dados em datagramas. No entanto, o termo genérico “segmento” é comumente usado![[Pasted image 20250123230425.png]]
Embora UDP seja normalmente chamado de não confiável, em contraste com a confiabilidade do TCP, isso não significa que os aplicativos que usam UDP são sempre não confiáveis, nem significa que o UDP é um protocolo inferior. Isso simplesmente significa que essas funções não são fornecidas pelo protocolo da camada de transporte e devem ser implementadas em outros locais, se houver necessidade.

A baixa sobrecarga do UDP o torna muito interessante para protocolos que efetuam transações simples de requisição e resposta. Por exemplo, usar TCP para o DHCP geraria tráfego de rede desnecessário. Se nenhuma resposta for recebida, o dispositivo reenvia a solicitação.

### Ataques UDP

O UDP não está protegido por nenhuma criptografia. Você pode adicionar criptografia ao UDP, mas não está disponível por padrão. A falta de criptografia significa que qualquer pessoa pode ver o tráfego, alterá-lo e enviá-lo ao seu destino. Alterar os dados no tráfego alterará o número de checagem de 16 bits, mas o número de checagem é opcional e nem sempre é usado. Quando o número de checagem é usado, o agente de ameaça pode criar um novoo número de checagem com base na nova carga de dados e registrá-lo no cabeçalho como um novo o número de checagem. O dispositivo de destino descobrirá que o número de checagem corresponde aos dados sem saber que os dados foram alterados. Esse tipo de ataque não é amplamente utilizado.

**Ataques de inundação UDP**

É mais provável que você veja um ataque de inundação UDP. Em um ataque de inundação UDP, todos os recursos em uma rede são consumidos. O agente de ameaça deve usar uma ferramenta como UDP Unicorn ou Low Orbit Ion Cannon. Essas ferramentas enviam uma inundação de pacotes UDP, geralmente de um host falsificado, para um servidor na sub-rede. O programa varrerá todas as portas conhecidas tentando encontrar portas fechadas. Isso fará com que o servidor responda com uma mensagem inacessível da porta ICMP. Como existem muitas portas fechadas no servidor, isso cria muito tráfego no segmento, que consome a maior parte da largura de banda. O resultado é muito semelhante a um ataque de negação de serviço (DoS).