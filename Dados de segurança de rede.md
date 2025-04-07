# Tipos de dados de segurança

### Dados de Alerta

Os dados de alerta consistem em mensagens geradas por sistemas de prevenção de intrusões (IPSs) ou sistemas de detecção de intrusões (IDSs) em resposta ao tráfego que viola uma regra ou corresponde à assinatura de uma exploração conhecida. Um IDS de rede (NIDS), como o Snort, vem configurado com regras para explorações conhecidas. Os alertas são gerados pelo Snort e são legíveis e pesquisáveis pelos aplicativos Sguil e Squert, que fazem parte do conjunto Security Onion de ferramentas NSM.

Um site de teste que é usado para determinar se o Snort está funcionando é o site tesmyids. Procure por ele na internet. Consiste em uma única página da Web que exibe apenas o seguinte texto **uid=0(root) gid=0(root) groups=0(root)**. Se o Snort estiver funcionando corretamente e um host visitar este site, uma assinatura será correspondida e um alerta será acionado. Esta é uma maneira fácil e inofensiva de verificar se o NIDS está em execução.

A regra Snort que é acionada é:

```
alert ip any any -> any any (msg:"GPL ATTACK_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; fast_pattern:only; classtype:bad-unknown; sid:2100498; rev:8;)
```

Essa regra gera um alerta se **any IP address** na rede receber dados de uma fonte externa que contenha conteúdo com texto correspondente ao padrão de **uid=0(root)**. O alerta contém a mensagem **GPL ATTACK_RESPONSE id check returned root**. O ID da regra Snort que foi acionada é **2100498**.

A linha destacada na figura exibe um alerta Sguil que foi gerado visitando o site testmyids. A regra Snort e os dados do pacote para o conteúdo recebido da página da Web testmyvids são exibidos na área inferior direita da interface Sguil.
![[Pasted image 20250205215255.png]]

### Dados de Sessão e Transação

Os dados de sessão são um registro de uma conversa entre dois pontos de extremidade de rede, que geralmente são um cliente e um servidor. O servidor pode estar dentro da rede corporativa ou em um local acessado pela Internet. Dados de sessão são dados sobre a sessão, não os dados recuperados e usados pelo cliente. Os dados da sessão incluirão informações de identificação, como **as cinco tuplas** de endereços IP de origem e destino, números de porta de origem e destino, e o código IP do protocolo em uso. Os dados sobre a sessão geralmente incluem um ID de sessão, a quantidade de dados transferidos por origem e destino e informações relacionadas à duração da sessão.

Zeek, anteriormente Bro, é uma ferramenta de monitoramento de segurança de rede que você usará em laboratórios mais tarde no curso. A figura mostra uma saída parcial para três sessões HTTP a partir de um log de conexão Zeek. As explicações dos campos são mostradas abaixo da figura.![[Pasted image 20250205215444.png]]

Os dados de transação consistem nas mensagens que são trocadas durante sessões de rede. Essas transações podem ser exibidas em transcrições de captura de pacotes. Os logs de dispositivos mantidos por servidores também contêm informações sobre as transações que ocorrem entre clientes e servidores. Por exemplo, uma sessão pode incluir o download de conteúdo de um servidor web, como mostrado na figura. As transações que representam as solicitações e respostas seriam registradas em um log de acesso no servidor ou por um NIDS como Zeek. A sessão é todo o tráfego envolvido na elaboração da solicitação, a transação é a própria solicitação.![[Pasted image 20250205215529.png]]
### Capturas de pacotes completos

Capturas completas de pacotes são os dados de rede mais detalhados que geralmente são coletados. Devido à quantidade de detalhes, eles também são os tipos de dados mais intensos de armazenamento e recuperação usados no NSM. As capturas completas de pacotes contêm não apenas dados sobre conversas de rede, como dados de sessão. As capturas completas de pacotes também contêm o conteúdo real das conversas. As capturas completas de pacotes contêm o texto das mensagens de email, o HTML nas páginas da Web e os arquivos que entram ou saem da rede. O conteúdo extraído pode ser recuperado de capturas completas de pacotes e analisado quanto a malware ou comportamento do usuário que viola as políticas de negócios e de segurança. A ferramenta familiar Wireshark é muito popular para visualizar capturas de pacotes completos e acessar os dados associados a conversas de rede.
### Dados estatísticos

Como dados de sessão, dados estatísticos são sobre tráfego de rede. Os dados estatísticos são criados através da análise de outras formas de dados de rede. Podem ser feitas conclusões que descrevem ou predizem o comportamento da rede a partir dessas análises. As características estatísticas do comportamento normal da rede podem ser comparadas ao tráfego de rede atual em um esforço para detectar anomalias. As estatísticas podem ser usadas para caracterizar quantidades normais de variação nos padrões de tráfego de rede, a fim de identificar condições de rede que estão significativamente fora desses intervalos. Diferenças estatisticamente significativas devem gerar alarmes e investigação imediata.

A NBA (Network Behavior Analysis) e a Network Behavior Anomaly Detection (NBAD) são abordagens para monitoramento de segurança de rede que usam técnicas analíticas avançadas para analisar dados de telemetria de rede NetFlow ou IPFIX (Internet Protocol Flow Information Export). Técnicas como análise preditiva e inteligência artificial realizam análises avançadas de dados de sessão detalhados para detectar possíveis incidentes de segurança.

**Observação**: IPFIX é a versão padrão IETF do Cisco NetFlow versão 9.

Um exemplo de uma ferramenta NSM que utiliza análise estatística é o Cisco Cognitive Threat Analytics. Ele é capaz de encontrar atividades mal-intencionadas que ignorou os controles de segurança ou entrou na rede por meio de canais não monitorados (incluindo mídia removível) e está operando dentro do ambiente de uma organização. O Cognitive Threat Analytics é um produto baseado em nuvem que usa aprendizado de máquina e modelagem estatística de redes. Ele cria uma linha de base do tráfego em uma rede e identifica anomalias. Ele analisa o comportamento do usuário e do dispositivo e o tráfego da Web para descobrir comunicações de comando e controle, exfiltração de dados e aplicativos potencialmente indesejados que operam na infraestrutura. A figura ilustra uma arquitetura para o Cisco Cognitive Threat Analytics.![[Pasted image 20250205215840.png]]

# Registros de dispositivos finais

### Logs de host

Conforme discutido anteriormente, os sistemas de detecção de intrusão baseados em host (HIDS) são executados em hosts individuais. HIDS não só detecta intrusões, mas na forma de firewalls baseados em host, também pode impedir intrusões. Este software cria logs e os armazena no host. Isso pode dificultar a visão do que está acontecendo em hosts na empresa, pois muitas proteções baseadas em host têm uma maneira de enviar logs para servidores centralizados de gerenciamento de logs. Dessa forma, os logs podem ser pesquisados a partir de um local central usando as ferramentas NSM.

Os sistemas HIDS podem usar agentes para enviar logs para servidores de gerenciamento. O OSSEC, um HIDS de código aberto popular, inclui uma funcionalidade robusta de coleta e análise de logs. Pesquise OSSEC na internet para saber mais. O Microsoft Windows inclui vários métodos para coleta e análise automatizadas de logs de host. Tripwire oferece um HIDS para Linux que inclui funcionalidade semelhante. Todos podem ser dimensionados para grandes empresas.

Os logs de host do Microsoft Windows são visíveis localmente pelo Visualizador de Eventos. O Visualizador de Eventos mantém quatro tipos de logs:

- **Logs de aplicativos** - Eles contêm eventos registrados por vários aplicativos.
- **Registros do sistema** - Isso inclui eventos relacionados à operação de drivers, processos e hardware.
- **Registros de instalação** - Estes registram informações sobre a instalação de software, incluindo atualizações do Windows.
- **Registros de segurança** - Esses eventos registram relacionados à segurança, como tentativas de logon e operações relacionadas ao gerenciamento e acesso de arquivos ou objetos.
- **Logs da linha de comando** - Os invasores que obtiveram acesso a um sistema e alguns tipos de malware executam comandos da interface de linha de comando (CLI) em vez de uma GUI. A execução da linha de comando em log fornecerá visibilidade para esse tipo de incidente.

Vários logs podem ter diferentes tipos de eventos. Os logs de segurança consistem apenas em mensagens de falha ou êxito de auditoria. Em computadores Windows, o log de segurança é realizado pelo Local Security Authority Subsystem Service (LSASS), que também é responsável por impor diretivas de segurança em um host Windows. O LSASS é executado como lsass.exe. Ele é frequentemente falsificado por malware. Ele deve estar sendo executado a partir do diretório System32 do Windows. Se um arquivo com esse nome, ou um nome camuflado, como 1sass.exe, estiver em execução ou em execução a partir de outro diretório, ele pode ser malware.

Os Eventos do Windows são identificados por números de ID e descrições breves. Uma enciclopédia de IDs de eventos de segurança, algumas com detalhes adicionais, está disponível no Ultimate Windows Security na Web.

A tabela explica o significado dos cinco tipos de eventos de log de host do Windows.
![[Pasted image 20250205220658.png]]
### Syslog

O Syslog inclui especificações para formatos de mensagem, uma estrutura de aplicativos cliente-servidor e protocolo de rede. Muitos tipos diferentes de dispositivos de rede podem ser configurados para usar o padrão syslog para registrar eventos em servidores syslog centralizados.

Syslog é um protocolo cliente / servidor. O Syslog foi definido dentro do grupo de trabalho Syslog do IETF (RFC 5424) e é suportado por uma grande variedade de dispositivos e receptores em várias plataformas.

O remetente do Syslog envia uma pequena mensagem de texto (menos de 1 KB) para o receptor do Syslog. O receptor Syslog é comumente chamado de “syslogd”, “Syslog daemon” ou “Syslog server.“ As mensagens do Syslog podem ser enviadas via UDP (porta 514) e/ou TCP (normalmente, porta 5000). Embora existam algumas exceções, como wrappers SSL, esses dados são normalmente enviados em texto simples pela rede.

O formato completo de uma mensagem Syslog que é visto na rede tem três partes distintas, como mostrado na figura.

- PRI (prioridade)
- HEADER
- MSG (texto da mensagem)

O PRI consiste em dois elementos, a Facilidade e a Gravidade da mensagem, que são ambos valores inteiros. O recurso consiste em amplas categorias de fontes que geraram a mensagem, como o sistema, o processo ou a aplicação. O valor Facility pode ser usado por servidores de log para direcionar a mensagem para o arquivo de log apropriado. A gravidade é um valor de 0 a 7 que define a gravidade da mensagem.![[Pasted image 20250205220854.png]]

![[Pasted image 20250205220915.png]]![[Pasted image 20250205220930.png]]![[Pasted image 20250205220942.png]]

A **HEADER** seção da mensagem contém o carimbo de data/hora no **MMM DD HH:MM:SS** formato. Se o carimbo de data/hora for precedido pelos símbolos de ponto (.) ou asterisco ( *), um problema é indicado com NTP. A seção HEADER também inclui o nome do host ou endereço IP do dispositivo que é a origem da mensagem.

A **MSG** parte contém o significado da mensagem syslog. Isso pode variar entre os fabricantes de dispositivos e pode ser personalizado. Portanto, essa parte da mensagem é a mais significativa e útil para o analista de segurança cibernética.
### Logs do servidor

Os logs do servidor são uma fonte essencial de dados para o monitoramento da segurança da rede. Os servidores de aplicativos de rede, como servidores de e-mail e Web, mantêm registros de acesso e erros. Os logs do servidor proxy DNS que documentam todas as consultas DNS e respostas que ocorrem na rede são especialmente importantes. Os logs de proxy DNS são úteis para identificar hosts que possam ter visitado sites perigosos e para identificar a exfiltração de dados DNS e conexões a servidores de comando e controle de malware. Muitos servidores UNIX e Linux usam syslog. Outros podem usar o registro proprietário. O conteúdo dos eventos do arquivo de log depende do tipo de servidor.

Dois arquivos de log importantes para se familiarizar são os logs de acesso do servidor web Apache e os logs de acesso do Microsoft Internet Information Server (IIS). Exemplos de cada um são mostrados abaixo.
![[Pasted image 20250205221231.png]]

### SIEM e coleta de logs

A tecnologia SIEM (Security Information and Event Management, gerenciamento de eventos e informações de segurança) é usada em muitas organizações para fornecer relatórios em tempo real e análise de longo prazo de eventos de segurança, conforme mostrado na figura.
![[Pasted image 20250205221320.png]]
O SIEM combina as funções essenciais de gerenciamento de eventos de segurança (SEM) e ferramentas de gerenciamento de informações de segurança (SIM) para fornecer uma visão abrangente da rede empresarial usando as seguintes funções:

- **Coleta de logs** — Os registros de eventos de origens em toda a organização fornecem informações forenses importantes e ajudam a atender aos requisitos de relatórios de conformidade.
- **Normalização** — Mapeia mensagens de log de diferentes sistemas em um modelo de dados comum, permitindo que a organização se conecte e analise eventos relacionados, mesmo que sejam inicialmente registradas em diferentes formatos de origem.
- **Correlação** — Isso vincula registros e eventos de sistemas ou aplicativos diferentes, acelerando a detecção e reação a ameaças de segurança.
- **Agregação** — Isso reduz o volume de dados de eventos consolidando registros de eventos duplicados.
- **Relatórios** — Apresenta os dados de eventos agregados e correlacionados em monitoramento em tempo real e resumos de longo prazo, incluindo painéis gráficos interativos.
- **Conformidade** — são relatórios para atender aos requisitos de várias regulamentações de conformidade.

Um SIEM popular é o Splunk, que é feito por um parceiro Cisco. Splunk é amplamente utilizado em SOCs. Outra solução SIEM popular é Security Onion com ELK, que consiste nos aplicativos integrados Elasticsearch, Logstash e Kibana. Security Onion inclui outras ferramentas de monitoramento de segurança de rede de código aberto.

Como sabemos, a orquestração, a automação e a resposta de segurança (SOAR) levam o SIEM e vão além para automatizar fluxos de trabalho de resposta de segurança e facilitar a resposta de incidência. Devido à importância da segurança de rede, inúmeras empresas trouxeram excelentes produtos para o mercado de ferramentas de segurança. No entanto, essas ferramentas não têm compatibilidade e exigem monitoramento de vários painéis de produtos independentes para processar os muitos alertas que eles geram. Devido à falta de profissionais de segurança cibernética para monitorar e analisar o grande volume de dados de segurança, é importante que as ferramentas de vários fornecedores possam ser integradas em uma única plataforma. As plataformas de segurança integradas vão além do SIEM e do SOAR para unificar várias tecnologias de segurança, processos e pessoas em uma equipe unificada cujos componentes se baseiam em vez de impedirem uns aos outros. Plataformas de segurança como Cisco SecureX, Fortinet Security Fabric e Paloalto Networks Cortex XDR prometem lidar com a complexidade do monitoramento de segurança de rede integrando várias funções e fontes de dados em uma única plataforma que aumentará consideravelmente a precisão dos alertas, oferecendo defesa robusta.
# Logs de rede

### Tcpdump

A ferramenta de linha de comando tcpdump é um analisador de pacotes muito popular. Ele pode exibir capturas de pacotes em tempo real ou gravar capturas de pacotes em um arquivo. Ele captura dados detalhados de protocolo de pacotes e conteúdo. Wireshark é uma GUI construída sobre a funcionalidade tcpdump.

A estrutura das capturas tcpdump varia dependendo do protocolo capturado e dos campos solicitados.
### NetFlow

NetFlow é um protocolo desenvolvido pela Cisco como uma ferramenta para solução de problemas de rede e contabilidade baseada em sessão. O NetFlow fornece com eficiência um importante conjunto de serviços para aplicativos IP, incluindo contabilidade de tráfego de rede, faturamento de rede com base no uso, planejamento de rede, segurança, recursos de monitoramento de negação de serviço e monitoramento de rede. O NetFlow fornece informações valiosas sobre usuários e aplicativos de rede, tempos de uso de pico e roteamento de tráfego.

O NetFlow não faz uma captura completa de pacote ou captura o conteúdo real no pacote. O NetFlow registra informações sobre o fluxo de pacotes, incluindo metadados. A Cisco desenvolveu o NetFlow e, em seguida, permitiu que ele fosse usado como base para um padrão IETF chamado IPFIX. O IPFIX é baseado no Cisco NetFlow Versão 9.

As informações do NetFlow podem ser visualizadas com ferramentas como o nfdump. Semelhante ao tcpdump, o nfdump fornece um utilitário de linha de comando para visualizar dados NetFlow a partir do daemon de captura nfcapd ou coletor. Existem ferramentas que adicionam funcionalidade GUI à visualização de fluxos. A figura mostra uma tela da ferramenta FlowViewer de código aberto.![[25.3.2-image-1.png]]

Tradicionalmente, um Fluxo de IP é baseado em um conjunto de 5 a 7 atributos de pacotes IP que fluem em uma única direção. Um fluxo consiste em todos os pacotes transmitidos até que a conversa TCP termine. Os atributos de pacote IP usados pelo NetFlow são:

- Endereço IP origem
- endereço IP de destino
- Porta de origem
- Porta de destino
- Tipo de protocolo da camada 3
- Classe de Serviço
- Interface de roteador ou switch

Todos os pacotes com o mesmo endereço IP de origem/destino, portas de origem/destino, interface de protocolo e classe de serviço são agrupados em um fluxo e, em seguida, pacotes e bytes são contabilizados. Essa metodologia de impressão digital ou determinação de um fluxo é escalável porque uma grande quantidade de informações de rede é condensada em um banco de dados de informações do NetFlow chamado cache do NetFlow.

Todos os registros de fluxo NetFlow conterão os primeiros cinco itens na lista acima e carimbos de data/hora de início e fim do fluxo. As informações adicionais que podem aparecer são altamente variáveis e podem ser configuradas no dispositivo NetFlow Exporter. Os exportadores são dispositivos que podem ser configurados para criar registros de fluxo e transmitir esses registros de fluxo para armazenamento em um dispositivo coletor NetFlow. Um exemplo de um registro básico de fluxo NetFlow, em dois formatos diferentes, é mostrado na figura.![[Pasted image 20250205222154.png]]
Um grande número de atributos para um fluxo está disponível. O registro IANA de entidades IPFIX lista várias centenas, sendo os primeiros 128 os mais comuns.

Embora o NetFlow não tenha sido inicialmente concebido como ferramenta para o monitoramento de segurança de rede, ele é visto como uma ferramenta útil na análise de incidentes de segurança de rede. Ele pode ser usado para construir uma linha do tempo de comprometimento, entender o comportamento individual do host ou para rastrear a movimentação de um invasor ou explorar de host para host dentro de uma rede. A tecnologia Cisco/Lancope Stealthwatch melhora o uso de dados NetFlow para NSM.
### Visibilidade e controle da aplicação

O sistema Cisco Application Visibility and Control (AVC), que é mostrado na figura, combina várias tecnologias para reconhecer, analisar e controlar mais de 1000 aplicativos. Estes incluem voz e vídeo, e-mail, compartilhamento de arquivos, jogos, ponto a ponto (P2P) e aplicativos baseados em nuvem. A AVC usa o reconhecimento de aplicativos baseados em rede de última geração da Cisco versão 2 (NBAR2), também conhecido como NBAR de próxima geração, para descobrir e classificar os aplicativos em uso na rede. O mecanismo de reconhecimento de aplicativos NBAR2 suporta mais de 1000 aplicativos de rede.

Para entender verdadeiramente a importância desta tecnologia, considere a figura. A identificação de aplicativos de rede por porta fornece pouca granularidade e visibilidade do comportamento do usuário. No entanto, a visibilidade do aplicativo através da identificação de assinaturas de aplicativos identifica o que os usuários estão fazendo, seja teleconferência ou download de filmes para seus telefones.![[Pasted image 20250205222339.png]]

Um sistema de gerenciamento e geração de relatórios, como o Cisco Prime, analisa e apresenta os dados de análise de aplicativos em relatórios de painel para uso pelo pessoal de monitoramento de rede. O uso de aplicativos também pode ser controlado por meio de políticas e classificação de qualidade de serviço com base nas informações do AVC.![[Pasted image 20250205222423.png]]

### Logs de filtro de conteúdo

Os dispositivos que fornecem filtragem de conteúdo, como o Cisco Email Security Appliance (ESA) e o Cisco Web Security Appliance (WSA), fornecem uma ampla gama de funcionalidades para monitoramento de segurança. O log está disponível para muitas dessas funcionalidades.

O ESA, por exemplo, tem mais de 30 logs que podem ser usados para monitorar a maioria dos aspectos da entrega de e-mail, funcionamento do sistema, antivírus, operações antispam e decisões de lista negra e lista branca. A maioria dos logs são armazenados em arquivos de texto e podem ser coletados em servidores syslog, ou podem ser enviados para servidores FTP ou SCP. Além disso, os alertas sobre o funcionamento do próprio equipamento e seus subsistemas podem ser monitorados por e-mail para administradores responsáveis pelo monitoramento e operação do dispositivo.

Os dispositivos WSA oferecem uma profundidade de funcionamento semelhante. O WSA atua efetivamente como um proxy da Web, o que significa que ele registra todas as informações de transação de entrada e saída para tráfego HTTP. Esses logs podem ser bastante detalhados e são personalizáveis. Eles podem ser configurados em um formato de compatibilidade W3C. O WSA pode ser configurado para enviar os logs para um servidor de várias maneiras, incluindo syslog, FTP e SCP.

Outros logs disponíveis para o WSA incluem logs de decisão da ACL, logs de varredura de malware e logs de filtragem de reputação da Web.

A figura ilustra os painéis de “detalhamento” disponíveis nos dispositivos de filtragem de conteúdo da Cisco. Ao clicar em componentes dos relatórios Visão geral, detalhes mais relevantes são exibidos. As buscas de destino fornecem as informações mais focadas.![[Pasted image 20250205223105.png]]

### Registro de Dispositivos Cisco

Os dispositivos de segurança Cisco podem ser configurados para enviar eventos e alertas para plataformas de gerenciamento de segurança usando SNMP ou syslog. A figura ilustra uma mensagem syslog gerada por um dispositivo Cisco ASA e uma mensagem syslog gerada por um dispositivo Cisco IOS.![[Pasted image 20250205223148.png]]
Observe que há dois significados usados para o recurso termo nas mensagens do syslog da Cisco. O primeiro é o conjunto padrão de valores de Facilidade que foram estabelecidos pelos padrões syslog. Esses valores são usados na parte da mensagem PRI do pacote syslog para calcular a prioridade da mensagem. A Cisco usa alguns dos valores entre 15 e 23 para identificar as Instalações de log da Cisco, dependendo da plataforma. Por exemplo, os dispositivos Cisco ASA usam syslog Facility 20 por padrão, o que corresponde a local4. O outro valor Facility é atribuído pela Cisco e ocorre na parte MSG da mensagem syslog.

Os dispositivos Cisco podem usar formatos de mensagem syslog ligeiramente diferentes e podem usar mnemônicos em vez de IDs de mensagem, conforme mostrado na figura. Um dicionário de mensagens de syslog do Cisco ASA está disponível no site da Cisco.
### Logs de proxy

Os servidores proxy, como os usados para solicitações Web e DNS, contêm logs valiosos que são uma fonte primária de dados para monitoramento de segurança de rede.

Servidores proxy são dispositivos que atuam como intermediários para clientes de rede. Por exemplo, uma empresa pode configurar um proxy da Web para lidar com solicitações da Web em nome de clientes. Em vez de solicitações de recursos da Web serem enviadas diretamente para o servidor do cliente, a solicitação é enviada primeiro para um servidor proxy. O servidor proxy solicita os recursos e os retorna ao cliente. O servidor proxy gera logs de todas as solicitações e respostas. Esses logs podem ser analisados para determinar quais hosts estão fazendo as solicitações, se os destinos são seguros ou potencialmente maliciosos, e também para obter insights sobre o tipo de recursos que foram baixados.

Proxies da Web fornecem dados que ajudam a determinar se as respostas da Web foram geradas em resposta a solicitações legítimas ou foram manipuladas para parecer respostas, mas são, de fato, explorações. Também é possível usar proxies da web para inspecionar o tráfego de saída como meio de prevenção de perda de dados (DLP). O DLP envolve a varredura do tráfego de saída para detectar se os dados que estão saindo da Web contêm informações confidenciais, confidenciais ou secretas. Exemplos de proxies populares da Web são Squid, CCProxy, Apache Traffic Server e WinGate.

Um exemplo de um log de proxy da web do Squid na forma nativa do Squid aparece abaixo. Explicações dos valores de campo aparecem na tabela abaixo da entrada de log.![[Pasted image 20250205224122.png]]

**Observação**: Proxies da Web abertos, que são proxies que estão disponíveis para qualquer usuário da Internet, podem ser usados para ofuscar endereços IP de atores de ameaças. Endereços de proxy abertos podem ser usados na lista negra do tráfego da Internet.

**Cisco Umbrella**

O Cisco Umbrella, anteriormente OpenDNS, oferece um serviço DNS hospedado que amplia a capacidade do DNS para incluir aprimoramentos de segurança. Em vez de organizações que hospedam e mantêm listas negras, proteção contra phishing e outras seguranças relacionadas a DNS, o Cisco Umbrella fornece essas proteções em seu próprio serviço DNS. O Cisco Umbrella é capaz de aplicar muito mais recursos ao gerenciamento de DNS do que a maioria das organizações pode pagar. O Cisco Umbrella funciona em parte como um super proxy DNS nesse sentido. O pacote Cisco Umbrella de produtos de segurança aplica inteligência contra ameaças em tempo real para gerenciar o acesso DNS e a segurança dos registros DNS. Os logs de acesso DNS estão disponíveis no Cisco Umbrella para a empresa assinada. Em vez de usar servidores DNS locais ou ISP, uma organização pode optar por assinar o Cisco Umbrella para DNS e outros serviços de segurança. Um exemplo de um log de proxy DNS aparece abaixo. A tabela explica o significado dos campos na entrada de log.![[Pasted image 20250205224245.png]]

### Cisco Firepower estão disponíveis

Os dispositivos de firewall da próxima geração ou NextGen estendem a segurança da rede além dos endereços IP e dos números de porta da Camada 4 para a camada do aplicativo e além. Os Firewalls NexGen são dispositivos avançados que forneceram muito mais funcionalidades do que as gerações anteriores de dispositivos de segurança de rede. Uma dessas funcionalidades é relatar painéis com recursos interativos que permitem relatórios rápidos de apontar e clicar sobre informações muito específicas sem a necessidade de SIEM ou outros correladores de eventos.

A linha de dispositivos NextGen Firewall (NGFW) da Cisco usa o Firepower Services para consolidar várias camadas de segurança em uma única plataforma. Isso ajuda a conter custos e simplificar o gerenciamento. Os serviços da potência de fogo incluem visibilidade e controle de aplicativos, IPS de última geração da potência de fogo (NGIPS), filtragem de URL baseada em categoria e reputação e proteção avançada contra malware (AMP). Dispositivos Firepower permitem monitorar a segurança da rede por meio de uma GUI habilitada para Web chamada Visualizador de Eventos.

Eventos comuns do NGFW incluem:

- **Evento de Conexão** - Os logs de conexão contêm dados sobre sessões que são detectadas diretamente pelo NGIPS. Os eventos de conexão incluem propriedades básicas de conexão, como carimbos de data/hora, endereços IP de origem e destino, e metadados sobre por que a conexão foi registrada, como qual regra de controle de acesso registrou o evento.
- **Evento de intrusão** - O sistema examina os pacotes que atravessam a rede em busca de atividades mal-intencionadas que possam afetar a disponibilidade, integridade e confidencialidade de um host e seus dados. Quando o sistema identifica uma possível intrusão, ele gera um evento de intrusão, que é um registro da data, hora, tipo de exploração e informações contextuais sobre a origem do ataque e seu destino.
- **Host ou evento de ponto final** - Quando um host aparece na rede, ele pode ser detectado pelo sistema e os detalhes do hardware do dispositivo, endereçamento IP e a última presença conhecida na rede podem ser registrados.
- **Evento de descoberta de rede** - eventos de descoberta de rede representam alterações que foram detectadas na rede monitorada. Essas alterações são registradas em resposta às diretivas de descoberta de rede que especificam os tipos de dados a serem coletados, os segmentos de rede a serem monitorados e as interfaces de hardware do dispositivo que devem ser usadas para coleta de eventos.
- **Evento de fluxo de** rede - A descoberta de rede pode usar vários mecanismos, um dos quais é usar registros de fluxo NetFlow exportados para gerar novos eventos para hosts e servidores.
 ![[Pasted image 20250205224349.png]]

