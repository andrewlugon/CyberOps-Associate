# Monitorando protocolos comuns

### Syslog e NTP

Vários protocolos que geralmente aparecem em redes têm recursos que os tornam de especial interesse no monitoramento de segurança. Por exemplo, syslog e Network Time Protocol (NTP) são essenciais para o trabalho do analista de segurança cibernética.

O padrão syslog é usado para registrar mensagens de eventos de dispositivos de rede e endpoints, conforme mostrado na figura. O padrão permite um meio neutro de sistema de transmissão, armazenamento e análise de mensagens. Muitos tipos de dispositivos de vários fornecedores diferentes podem usar syslog para enviar entradas de log para servidores centrais que executam um daemon syslog. Esta centralização da coleta de logs ajuda a tornar o monitoramento de segurança prático. Os servidores que executam syslog normalmente escutam na porta UDP 514.

Como o syslog é tão importante para o monitoramento de segurança, os servidores syslog podem ser um alvo para atores de ameaças. Algumas explorações, como as que envolvem exfiltração de dados, podem levar muito tempo para serem concluídas devido às formas muito lentas em que os dados são secretamente roubados da rede. Alguns atacantes podem tentar ocultar o fato de que a exfiltração está ocorrendo. Eles atacam servidores syslog que contêm as informações que podem levar à detecção da exploração. Os hackers podem tentar bloquear a transferência de dados de clientes syslog para servidores, adulterar ou destruir dados de log ou adulterar o software que cria e transmite mensagens de log. A implementação do syslog de próxima geração (ng), conhecida como syslog-ng, oferece aprimoramentos que podem ajudar a evitar algumas das explorações que visam o syslog.

Pesquise na Internet para obter mais informações sobre syslog-ng.![[Pasted image 20250205210025.png]]
### NTP

As mensagens do Syslog geralmente são carimbadas de data e hora. Isso permite que mensagens de diferentes fontes sejam organizadas pelo tempo para fornecer uma visão dos processos de comunicação de rede. Como as mensagens podem vir de muitos dispositivos, é importante que os dispositivos compartilhem um timeclock consistente. Uma maneira que isso pode ser alcançado é para os dispositivos usarem o Network Time Protocol (NTP). O NTP usa uma hierarquia de fontes de tempo autoritativas para compartilhar informações de tempo entre dispositivos na rede, conforme mostrado na figura. Dessa forma, as mensagens de dispositivo que compartilham informações de tempo consistentes podem ser enviadas para o servidor syslog. O NTP opera na porta UDP 123.

Como os eventos conectados a uma exploração podem deixar rastros em todos os dispositivos de rede em seu caminho para o sistema de destino, os carimbos de data/hora são essenciais para detecção. Os atores de ameaças podem tentar atacar a infraestrutura NTP para corromper as informações de tempo usadas para correlacionar eventos de rede registrados. Isso pode servir para ofuscar vestígios de explorações em curso. Além disso, os atores de ameaças têm sido conhecidos por usar sistemas NTP para direcionar ataques DDoS por meio de vulnerabilidades no software cliente ou servidor. Embora esses ataques não resultem necessariamente em dados de monitoramento de segurança corrompidos, eles podem interromper a disponibilidade da rede.
![[Pasted image 20250205210241.png]]
### DNS

O Serviço de Nome de Domínio (DNS) é usado por milhões de pessoas diariamente. Por isso, muitas organizações têm políticas menos rigorosas para proteger contra ameaças baseadas em DNS do que precisam proteger contra outros tipos de explorações. Os invasores reconheceram isso e geralmente encapsulam diferentes protocolos de rede no DNS para evitar dispositivos de segurança. O DNS agora é usado por muitos tipos de malware. Algumas variedades de malware usam DNS para se comunicar com servidores de comando e controle (CNC) e para exfiltrar dados no tráfego disfarçados como consultas DNS normais. Vários tipos de codificação, como Base64, binário de 8 bits e Hex podem ser usados para camuflar os dados e evitar medidas básicas de prevenção de perda de dados (DLP).

Por exemplo, malware pode codificar dados roubados como a parte de subdomínio de uma pesquisa DNS para um domínio onde o servidor de nomes está sob controle de um invasor. Uma pesquisa de DNS para 'long string-of-exfiltrated-data.example.com' seria encaminhada para o servidor de nomes de example.com, que gravaria 'long string-of-exfiltrated-data' e responderia de volta ao malware com uma resposta codificada. Este uso do subdomínio DNS é mostrado na figura. Os dados exfiltrados são o texto codificado mostrado na caixa. O ator de ameaças coleta esses dados codificados, decodifica e combina e agora tem acesso a um arquivo de dados inteiro, como um banco de dados de nome de usuário/senha.

É provável que a parte do subdomínio de tais solicitações seria muito mais longa do que as solicitações usuais. Analistas cibernéticos podem usar a distribuição dos comprimentos de subdomínios dentro de solicitações DNS para construir um modelo matemático que descreva a normalidade. Eles podem então usar isso para comparar suas observações e identificar um abuso do processo de consulta DNS. Por exemplo, não seria normal ver um host em sua rede enviando uma consulta para AW4GCGXHy2UGDG8GCHJVDGVJDC.Example.com.

Consultas DNS para nomes de domínio gerados aleatoriamente, ou subdomínios com aparência aleatória extremamente longos, devem ser consideradas suspeitas, especialmente se a ocorrência deles aumentar drasticamente na rede. Os logs de proxy DNS podem ser analisados para detectar essas condições. Como alternativa, serviços como o serviço DNS passivo do Cisco Umbrella podem ser usados para bloquear solicitações para CNC suspeitos e domínios de exploração.
![[Pasted image 20250205210747.png]]
### HTTP e HTTPS

O Hypertext Transfer Protocol (HTTP) é o protocolo de backbone da World Wide Web. No entanto, todas as informações transportadas em HTTP são transmitidas em texto simples do computador de origem para o destino na internet. O HTTP não protege os dados contra alteração ou interceptação por partes mal-intencionadas, o que é uma séria ameaça à privacidade, identidade e segurança das informações. Todas as atividades de navegação devem ser consideradas em risco.

Uma exploração comum de HTTP é chamada de injeção iFrame (quadro inline). A maioria das ameaças baseadas na Web consiste em scripts de malware que foram plantados em servidores web. Esses servidores da Web direcionam os navegadores para servidores infectados carregando iframes. Na injeção iFrame, um ator de ameaça compromete um servidor da Web e planta código malicioso que cria um iFrame invisível em uma página da Web comumente visitada. Quando o iFrame é carregado, o malware é baixado, freqüentemente de um URL diferente da página da Web que contém o código iFrame. Os serviços de segurança de rede, como a filtragem Cisco Web Reputation, podem detectar quando um site tenta enviar conteúdo de um site não confiável para o host, mesmo quando enviado de um IFrame, conforme mostrado na figura.
![[Pasted image 20250205210935.png]]
Para lidar com a alteração ou interceptação de dados confidenciais, muitas organizações comerciais adotaram HTTPS ou implementaram políticas somente HTTPS para proteger os visitantes de seus sites e serviços.

HTTPS adiciona uma camada de criptografia ao protocolo HTTP usando Secure Socket Layer (SSL), como mostrado na figura. Isso torna os dados HTTP ilegíveis, pois deixam o computador de origem até chegar ao servidor. Observe que HTTPS não é um mecanismo para a segurança do servidor Web. Ele só protege o tráfego de protocolo HTTP enquanto está em trânsito.![[Pasted image 20250205211049.png]]

Infelizmente, o tráfego HTTPS criptografado complica o monitoramento de segurança de rede. Alguns dispositivos de segurança incluem descriptografia e inspeção SSL; no entanto, isso pode apresentar problemas de processamento e privacidade. Além disso, o HTTPS adiciona complexidade às capturas de pacotes devido às mensagens adicionais envolvidas no estabelecimento da conexão criptografada. Esse processo é resumido na figura e representa sobrecarga adicional sobre HTTP.![[Pasted image 20250205211205.png]]
### Protocolos de e-mail

Protocolos de e-mail como SMTP, POP3 e IMAP podem ser usados por atores de ameaças para espalhar malware, exfiltrar dados ou fornecer canais para servidores CNC de malware, como mostrado na figura.

SMTP envia dados de um host para um servidor de email e entre servidores de email. Como DNS e HTTP, é um protocolo comum para ver sair da rede. Como há muito tráfego SMTP, ele nem sempre é monitorado. No entanto, o SMTP foi usado no passado por malware para exfiltrar dados da rede. No 2014 hack da Sony Pictures, uma das explorações usou SMTP para exfiltrar detalhes do usuário de hosts comprometidos para servidores CNC. Essas informações podem ter sido usadas para ajudar a desenvolver explorações de recursos protegidos na rede Sony Pictures. O monitoramento de segurança pode revelar esse tipo de tráfego com base nos recursos da mensagem de email.

IMAP e POP3 são usados para baixar mensagens de email de um servidor de email para o computador host. Por esse motivo, eles são os protocolos de aplicativos que são responsáveis por trazer malware para o host. O monitoramento de segurança pode identificar quando um anexo de malware entrou na rede e qual host ele infectou pela primeira vez. A análise retrospectiva pode então rastrear o comportamento do malware a partir desse ponto em diante. Desta forma, o comportamento do malware pode ser melhor compreendido e a ameaça identificada. As ferramentas de monitoramento de segurança também podem permitir a recuperação de anexos de arquivos infectados para envio a caixas de proteção de malware para análise.![[Pasted image 20250205211412.png]]
### ICMP

ICMP tem muitos usos legítimos, no entanto, a funcionalidade ICMP também tem sido usada para criar vários tipos de explorações. O ICMP pode ser usado para identificar hosts em uma rede, a estrutura de uma rede e determinar os sistemas operacionais em uso na rede. Ele também pode ser usado como um veículo para vários tipos de ataques DoS.

ICMP também pode ser usado para exfiltração de dados. Devido à preocupação de que o ICMP possa ser usado para vigiar ou negar o serviço de fora da rede, o tráfego ICMP de dentro da rede às vezes é ignorado. No entanto, algumas variedades de malware usam pacotes ICMP criados para transferir arquivos de hosts infectados para agentes ameaçadores usando esse método, conhecido como tunelamento ICMP.

Pesquise na internet para uma explicação detalhada da conhecida exploração LOKI.

**Note:** Este site pode estar bloqueado pelo firewall da sua instituição.

Existem várias ferramentas para a criação de túneis. Procure na internet por Ping Tunnel para explorar uma dessas ferramentas.
# Tecnologias de segurança

Muitas tecnologias e protocolos podem ter impacto no monitoramento de segurança. Listas de Controle de Acesso (ACLs) estão entre essas tecnologias. As ACLs podem dar uma falsa sensação de segurança se forem excessivamente confiadas. As ACLs e a filtragem de pacotes em geral são tecnologias que contribuem para um conjunto em evolução de proteções de segurança de rede.

A figura ilustra o uso de ACLs para permitir apenas tipos específicos de tráfego ICMP (Internet Control Message Protocol). O servidor em 192.168.1.10 faz parte da rede interna e tem permissão para enviar solicitações de ping para o host externo em 209.165.201.3. O tráfego ICMP de retorno do host externo é permitido se for uma resposta ICMP, extinção de origem (informa a origem para reduzir o ritmo do tráfego) ou qualquer mensagem ICMP inacessível. Todos os outros tipos de tráfego ICMP são negados. Por exemplo, o host externo não pode iniciar uma solicitação de ping para o host interno. A ACL de saída está permitindo mensagens ICMP que relatam vários problemas. Isso permitirá túneis ICMP e exfiltração de dados.

Os invasores podem determinar quais endereços IP, protocolos e portas são permitidos pelas ACLs. Isso pode ser feito por varredura de portas, testes de penetração ou através de outras formas de reconhecimento. Os atacantes podem criar pacotes que usam endereços IP de origem falsificados. Os aplicativos podem estabelecer conexões em portas arbitrárias. Outros recursos do tráfego de protocolo também podem ser manipulados, como o sinalizador estabelecido em segmentos TCP. As regras não podem ser antecipadas e configuradas para todas as técnicas de manipulação de pacotes emergentes.

Para detectar e reagir à manipulação de pacotes, comportamentos mais sofisticados e medidas baseadas em contexto precisam ser tomadas. Os firewalls de próxima geração da Cisco, o AMP (Advanced Malware Protection) e os appliances de conteúdo de e-mail e Web são capazes de resolver as deficiências das medidas de segurança baseadas em regras.
![[Pasted image 20250205212841.png]]
### NAT e PAT

Conversão de Endereços de Rede (NAT) e Tradução de Endereço de Porta (PAT) podem complicar o monitoramento de segurança. Vários endereços IP são mapeados para um ou mais endereços públicos visíveis na Internet, ocultando os endereços IP individuais que estão dentro da rede (endereços internos).

A figura ilustra a relação entre endereços internos e externos que são usados como endereços de origem (SA) e endereços de destino (DA). Esses endereços internos e externos estão em uma rede que está usando NAT para se comunicar com um destino na Internet. Se o PAT estiver em vigor e todos os endereços IP que saem da rede usarem o endereço global 209.165.200.226 interno para tráfego na Internet, pode ser difícil registrar o dispositivo interno específico que está solicitando e recebendo o tráfego quando ele entra na rede.

Esse problema pode ser especialmente relevante com dados NetFlow. Os fluxos de NetFlow são unidirecionais e são definidos pelos endereços e portas que eles compartilham. O NAT basicamente quebrará um fluxo que passa por um gateway NAT, tornando as informações de fluxo além desse ponto indisponíveis. A Cisco oferece produtos de segurança que irão “costurar” fluir juntos mesmo que os endereços IP tenham sido substituídos pelo NAT.

O NetFlow é discutido com mais detalhes posteriormente no módulo.![[Pasted image 20250205213036.png]]
### Criptografia, encapsulamento e encapsulamento

Como mencionado com HTTPS, a criptografia pode apresentar desafios para o monitoramento de segurança tornando os detalhes do pacote ilegíveis. A criptografia faz parte das tecnologias VPN. Nas VPNs, um protocolo comum, como IP, é usado para transportar tráfego criptografado. O tráfego criptografado essencialmente estabelece uma conexão virtual ponto a ponto entre redes através de instalações públicas. A criptografia torna o tráfego ilegível para outros dispositivos, exceto os endpoints VPN.

Uma tecnologia semelhante pode ser usada para criar uma conexão virtual ponto a ponto entre um host interno e dispositivos de atores de ameaças. O malware pode estabelecer um túnel criptografado que usa um protocolo comum e confiável e usá-lo para extrair dados da rede. Um método semelhante de exfiltração de dados foi discutido anteriormente para DNS.
### Rede ponto a ponto e Tor

Na rede ponto a ponto (P2P), mostrada na figura, os hosts podem operar em funções de cliente e servidor. Existem três tipos de aplicativos P2P: compartilhamento de arquivos, compartilhamento de processadores e mensagens instantâneas. No compartilhamento de arquivos P2P, os arquivos em uma máquina participante são compartilhados com membros da rede P2P. Exemplos disso são os outrora populares Napster e Gnutella. Bitcoin é uma operação P2P que envolve o compartilhamento de um banco de dados distribuído, ou razão, que registra saldos e transações Bitcoin. BitTorrent é uma rede de compartilhamento de arquivos P2P.

Sempre que os usuários desconhecidos recebem acesso aos recursos de rede, a segurança é uma preocupação. Aplicativos P2P de compartilhamento de arquivos não devem ser permitidos em redes corporativas. A atividade da rede P2P pode contornar as proteções de firewall e é um vetor comum para a propagação de malware. P2P é inerentemente dinâmico. Ele pode operar conectando-se a vários endereços IP de destino e também pode usar numeração dinâmica de portas. Arquivos compartilhados são frequentemente infectados com malware, e os atores de ameaças podem posicionar seu malware em clientes P2P para distribuição a outros usuários.

As redes P2P de compartilhamento de processadores doam ciclos de processador para tarefas computacionais distribuídas. Pesquisa de câncer, pesquisa de extraterrestres, e pesquisa científica usam ciclos de processador doados para distribuir tarefas computacionais.

Mensagens instantâneas (IM) também é considerado um aplicativo P2P. IM tem valor legítimo dentro de organizações que têm equipes de projeto distribuídas geograficamente. Nesse caso, aplicativos de IM especializados estão disponíveis, como a plataforma Webex Teams, que são mais seguras do que as mensagens instantâneas que usam servidores públicos.
![[Pasted image 20250205213459.png]]

Tor é uma plataforma de software e rede de hosts P2P que funcionam como roteadores de internet na rede Tor. A rede Tor permite que os usuários naveguem na internet anonimamente. Os usuários acessam a rede Tor usando um navegador especial. Quando uma sessão de navegação é iniciada, o navegador constrói um caminho de ponta a ponta em camadas na rede do servidor Tor que é criptografado, como mostrado na figura. Cada camada criptografada é “removida” como as camadas de uma cebola (portanto, “roteamento de cebola”) à medida que o tráfego atravessa um retransmissor do Tor. As camadas contêm informações criptografadas do próximo salto que só podem ser lidas pelo roteador que precisa ler as informações. Dessa forma, nenhum dispositivo único conhece todo o caminho para o destino e as informações de roteamento só podem ser lidas pelo dispositivo que as requer. Finalmente, no final do caminho do Tor, o tráfego atinge seu destino na internet. Quando o tráfego é retornado à origem, um caminho criptografado em camadas é construído novamente.

Tor apresenta uma série de desafios aos analistas de segurança cibernética. Primeiro, o Tor é amplamente utilizado por organizações criminosas na “Dark Net”. Além disso, Tor tem sido usado como um canal de comunicação para malware CNC. Como o endereço IP de destino do tráfego Tor é ofuscado pela criptografia, com apenas o nó Tor de próximo salto conhecido, o tráfego Tor evita listas negras configuradas em dispositivos de segurança.
![[Pasted image 20250205213701.png]]

### Balanceamento de carga

O balanceamento de carga envolve a distribuição do tráfego entre dispositivos ou caminhos de rede para evitar recursos de rede sobrecarregados com muito tráfego. Se existirem recursos redundantes, um algoritmo ou dispositivo de balanceamento de carga funcionará para distribuir o tráfego entre esses recursos, conforme mostrado na figura.

Uma maneira de fazer isso na internet é através de várias técnicas que usam DNS para enviar tráfego para recursos que têm o mesmo nome de domínio, mas vários endereços IP. Em alguns casos, a distribuição pode ser para servidores que são distribuídos geograficamente. Isso pode resultar em uma única transação de Internet sendo representada por vários endereços IP nos pacotes de entrada. Isso pode fazer com que recursos suspeitos apareçam em capturas de pacotes. Além disso, alguns dispositivos do gerenciador de balanceamento de carga (LBM) usam testes para testar o desempenho de diferentes caminhos e a integridade de diferentes dispositivos. Por exemplo, um LBM pode enviar testes para os diferentes servidores para os quais ele está balanceando o tráfego de carga, a fim de detectar que os servidores estão operando. Isso é feito para evitar o envio de tráfego para um recurso que não está disponível. Esses testes podem parecer tráfego suspeito se o analista de segurança cibernética não estiver ciente de que esse tráfego faz parte da operação do LBM.![[Pasted image 20250205213943.png]]




