# Introdução ao monitoramento de rede

### Topologia de segurança de rede

“Todas as redes são alvos” é um ditado comum usado para descrever o cenário atual da segurança de rede. Portanto, para mitigar ameaças, todas as redes devem estar protegidas e protegidas.

Isso requer uma abordagem de defesa em profundidade. Ele requer o uso de métodos comprovados e uma infraestrutura de segurança que consiste em firewalls, sistemas de detecção de intrusões (IDS), sistemas de prevenção de intrusões (IPS) e software de segurança de terminais. Esses métodos e tecnologias são usados para introduzir monitoramento automatizado na rede, criar alertas de segurança ou bloquear automaticamente dispositivos ofensivos quando algo der errado.

No entanto, para grandes redes, uma camada extra de proteção deve ser adicionada. Dispositivos como firewalls e IPS operam com base em regras pré-configuradas. Eles monitoram o tráfego e o comparam com as regras configuradas. Se houver uma correspondência, o tráfego é tratado de acordo com a regra. Isso funciona de forma relativamente perfeita. No entanto, às vezes o tráfego legítimo é confundido com tráfego não autorizado. Chamadas de falsos positivos, essas situações exigem que os olhos humanos os vejam e avaliem antes que possam ser validados.

Uma parte importante do trabalho do analista de segurança cibernética é analisar todos os alertas gerados pelos dispositivos de rede e determinar a validade dos alertas. Esse arquivo que foi baixado pelo usuário X era realmente malware? Esse site que foi visitado pelo usuário Y é realmente malicioso? A impressora no terceiro andar está realmente comprometida porque está tentando se conectar a um servidor que está fora da internet? Estas são perguntas que são normalmente feitas por analistas de segurança diariamente. É seu trabalho determinar as respostas corretas.

### Métodos de monitoramento de rede

A operação diária de uma rede consiste em padrões comuns de fluxo de tráfego, uso de largura de banda e acesso a recursos. Juntos, esses padrões identificam o comportamento normal da rede. Os analistas de segurança devem estar intimamente familiarizados com o comportamento normal da rede porque o comportamento anormal da rede normalmente indica um problema.

Para determinar o comportamento normal da rede, o monitoramento da rede deve ser implementado. Várias ferramentas são usadas para ajudar a descobrir o comportamento normal da rede, incluindo IDS, analisadores de pacotes, SNMP, NetFlow e outros.

Algumas dessas ferramentas exigem dados de rede capturados. Existem dois métodos comuns usados para capturar o tráfego e enviá-lo para dispositivos de monitoramento de rede:

- Torneiras de rede, algumas vezes conhecidas como pontos de acesso de teste (TAPs, test access points)
- Espelhamento de tráfego usando o SPAN (Switch Port Analyzer) ou outro espelhamento de porta.

### Taps de rede

Uma torneira de rede é normalmente um dispositivo de divisão passiva implementado em linha entre um dispositivo de interesse e a rede. Uma torneira encaminha todo o tráfego, incluindo erros de camada física, para um dispositivo de análise, permitindo que o tráfego chegue ao destino pretendido.

A figura exibe uma topologia de amostra exibindo uma torneira instalada entre um firewall de rede e o roteador interno.![[Pasted image 20250122210617.png]]

Observe como a torneira envia simultaneamente o fluxo de dados de transmissão (TX) do roteador interno e o fluxo de dados de recebimento (RX) para o roteador interno em canais separados e dedicados. Isso garante que todos os dados cheguem ao dispositivo de monitoramento em tempo real. Portanto, o desempenho da rede não é afetado ou degradado pelo monitoramento da conexão.

As torneiras também são normalmente à prova de falhas, o que significa que se uma torneira falhar ou perder energia, o tráfego entre o firewall e o roteador interno não é afetado.

Pesquise na Internet para obter informações sobre NetScout Taps para Ethernet UTP de cobre, Ethernet de fibra e links seriais.

### Espelhamento de tráfego e SPAN

Os switches de rede segmentam a rede por projeto. Isso limita a quantidade de tráfego visível para dispositivos de monitoramento de rede. Como a captura de dados para monitoramento de rede requer que todo o tráfego seja capturado, técnicas especiais devem ser empregadas para contornar a segmentação de rede imposta pelos switches de rede. O espelhamento de portas é uma dessas técnicas. Suportado por muitos switches corporativos, o espelhamento de portas permite que o switch copie quadros recebidos em uma ou mais portas para uma porta SPAN (Switch Port Analyzer) conectada a um dispositivo de análise.

A tabela identifica e descreve os termos usados pelo recurso SPAN.![[Pasted image 20250122210743.png]]

A figura mostra um switch que interconecta dois hosts e espelha o tráfego a um IDS (dispositivo de detecção de intrusão) e servidor de gerenciamento de rede.![[Pasted image 20250122210806.png]]
O switch encaminhará o tráfego de entrada em F0/1 e o tráfego de saída em F0/2 para a porta SPAN G0/1 de destino que se conecta a um IDS.

A associação entre as portas de origem e uma porta de destino é chamada de sessão SPAN. Em uma única sessão, uma ou várias portas podem ser monitoradas. Em alguns switches Cisco, o tráfego de sessão pode ser copiado para mais de uma porta de destino. Como alternativa, uma VLAN de origem pode ser especificada na qual todas as portas na VLAN de origem se tornam fontes de tráfego SPAN. Cada sessão SPAN pode ter portas ou VLANs como origens, mas não ambas.

**Observação**: uma variação de SPAN chamada SPAN Remote SPAN (RSPAN) permite que um administrador de rede use a flexibilidade de VLANs para monitorar o tráfego em switches remotos.

# Introdução às ferramentas de monitoramento de rede

### Ferramentas de monitoramento de segurança de rede

As ferramentas comuns que são usadas para monitoramento de segurança de rede incluem:

- Analisadores de protocolo de rede como Wireshark e Tcpdump
- NetFlow
- Sistemas de gerenciamento de eventos e informações de segurança (SIEM)

Também é comum que analistas de segurança confiem em arquivos de log e SNMP (Simple Network Management Protocol) para detecção de comportamento de rede.

Praticamente todos os sistemas geram arquivos de log para gravar e comunicar suas operações. Ao monitorar de perto os arquivos de log, um analista de segurança pode coletar informações extremamente valiosas.

O SNMP permite que os analistas solicitem e recebam informações sobre a operação de dispositivos de rede. É outra boa ferramenta para monitorar o comportamento de uma rede.

Os analistas de segurança devem estar familiarizados com todas essas ferramentas.

##### Ferramentas comuns de monitoramento de segurança de rede![[Pasted image 20250122211703.png]]

### Analisadores de protocolo

Analisadores de protocolo de rede (ou aplicativos de “sniffer de pacotes”) são programas usados para capturar tráfego. Os analisadores de protocolo mostram o que está acontecendo na rede, muitas vezes através de uma interface gráfica do usuário. Os analistas podem usar esses aplicativos para ver as trocas de rede até o nível do pacote. Se um computador foi infectado com malware e atualmente está atacando outros computadores na rede, o analista pode ver isso claramente capturando tráfego de rede em tempo real e analisando os pacotes.

Os analisadores de protocolo de rede não são usados apenas para análise de segurança. Eles também são muito úteis para solução de problemas de rede, desenvolvimento de software, desenvolvimento de protocolo e educação. Por exemplo, na perícia de segurança, um analista de segurança pode tentar reconstruir um incidente a partir de capturas de pacotes relevantes.

Wireshark, mostrado na figura, é uma ferramenta analisadora de protocolo de rede muito popular que é usada em ambientes Windows, Linux e Mac OS. Wireshark é um software livre que pode ser baixado e usado por qualquer pessoa. É uma ferramenta muito útil para aprender sobre comunicações de protocolo de rede. As habilidades do analisador de protocolo de rede são essenciais para analistas de segurança cibernética.

Os quadros capturados pelo Wireshark são salvos em um arquivo PCAP. Os arquivos PCAP contêm as informações de quadro, informações de interface, comprimento do pacote, carimbos de data/hora e até mesmo arquivos binários inteiros que são enviados pela rede.

A execução de uma captura de pacotes de longo prazo produz arquivos PCAP grandes.

O Wireshark também pode abrir arquivos que contêm tráfego capturado de outros softwares, como o utilitário **tcpdump**. Popular entre os sistemas Unix como Linux, **tcpdump** é um utilitário poderoso com inúmeras opções de linha de comando.

**Observação**: **windump** é uma variante do Microsoft Windows do **tcpdump**. **tshark** é uma ferramenta de linha de comando Wireshark semelhante a **tcpdump**.

### NetFlow

NetFlow é uma tecnologia Cisco IOS que fornece estatísticas 24 horas por dia, 7 dias por semana em pacotes que fluem através de um roteador Cisco ou switch multicamada. NetFlow é o padrão para coletar dados operacionais IP em redes IP. O NetFlow agora é compatível com plataformas não Cisco. IP Flow Information Export (IPFIX) é uma versão do NetFlow que é um protocolo padrão IETF.

O NetFlow pode ser usado para monitoramento de rede e segurança, planejamento de rede e análise de tráfego. Ele fornece uma trilha de auditoria completa de informações básicas sobre cada fluxo de IP encaminhado em um dispositivo. Essas informações incluem as informações de IP do dispositivo de origem e destino, a hora da comunicação e a quantidade de dados transferidos. O NetFlow não captura o conteúdo real no fluxo. A funcionalidade NetFlow é frequentemente comparada a uma conta telefônica. A conta identifica o número de destino, a hora e a duração da chamada. No entanto, ele não exibe o conteúdo da conversa telefônica.

Embora o NetFlow armazene informações de fluxo em um cache local no dispositivo, ele deve sempre ser configurado para encaminhar dados para um coletor NetFlow que armazene os dados NetFlow. Há várias ferramentas de terceiros para análise de dados NetFlow.![[Pasted image 20250122212323.png]]

O NetFlow pode monitorar essa conexão de aplicativo rastreando contagens de bytes e pacotes para esse fluxo de aplicativo individual. Em seguida, envia as estatísticas para um servidor externo chamado coletor NetFlow.

Por exemplo, o Cisco Stealthwatch coleta estatísticas do NetFlow para executar funções avançadas, incluindo:

- **Costura de fluxo -** Ele agrupa entradas individuais em fluxos.
- **Desduplicação de fluxo** - Filtra entradas duplicadas de vários clientes NetFlow.
- **Costura NAT** - Simplifica os fluxos com entradas NAT.

Há um canal Cisco Stealthwatch no YouTube que fornece muitos detalhes sobre o Stealthwatch e seus usos.

### SIEM e SOAR

Os analistas de segurança de rede devem avaliar com rapidez e precisão o significado de qualquer evento de segurança e responder às seguintes perguntas críticas:

- Quem está associado a este evento?
- O usuário tem acesso a outros recursos confidenciais?
- Esse evento representa um problema de conformidade em potencial?
- O usuário tem acesso a propriedade intelectual ou informações confidenciais?
- O usuário está autorizado a acessar esse recurso?

Para ajudar a responder a essas perguntas, os analistas de segurança usam:

- Gerenciamento de eventos de informações de segurança (SIEM, Security Information Event Management)
- Orquestração, automação e resposta de segurança (SOAR, Security orchestration, automation and response,)

**SIEM**

O SIEM (Security Information Event Management) é uma tecnologia usada em organizações empresariais para fornecer relatórios em tempo real e análise de longo prazo de eventos de segurança.

Dispositivos de rede, incluindo firewall, IPSs, ESAs, WSAs, roteadores, switches, servidores e hosts, são configurados para enviar eventos de log para o software SIEM. O software SIEM correlaciona milhões de eventos usando aprendizado de máquina e software de análise especial para identificar o tráfego que deve ser investigado.

Os sistemas SIEM incluem as seguintes funções essenciais:

- **Análise forense** — A capacidade de pesquisar logs e registros de eventos de fontes em toda a organização. Ele fornece informações mais completas para análise forense.
- **Correlação** — examina logs e eventos de diferentes sistemas ou aplicativos, acelerando a detecção e reação a ameaças de segurança.
- **Agregação** - A agregação reduz o volume de dados de eventos consolidando registros de eventos duplicados.
- **Reporting** - Reporting apresenta os dados de eventos correlacionados e agregados em monitoramento em tempo real e resumos de longo prazo.

O SIEM fornece detalhes sobre a origem da atividade suspeita:

- Informações do usuário, como nome de usuário, status de autenticação, localização.
- Informações do dispositivo, como fabricante, modelo, versão do sistema operacional, endereço MAC, método de conexão de rede e localização.
- Informações de postura, como se o dispositivo é compatível com a política de segurança, tem arquivos antivírus atualizados e é atualizado com os patches de SO mais recentes.

**SOAR**

A orquestração, automação e resposta de segurança (SOAR) aprimora o SIEM. Ele ajuda as equipes de segurança a investigar incidentes de segurança e adiciona coleta de dados aprimorada e várias funcionalidades que ajudam na resposta a incidentes de segurança.

Soluções SOAR:

- Fornece ferramentas de gerenciamento de casos que permitem que o pessoal de segurança cibernética pesquise e investigue incidentes, frequentemente integrando inteligência contra ameaças à plataforma de segurança de rede.
- Use inteligência artificial para detectar incidentes e auxiliar na análise e resposta a incidentes.
- Automatize procedimentos complexos de resposta a incidentes e investigações, que são tarefas potencialmente intensas de mão-de-obra executadas pela equipe do centro de operações de segurança (SOC) executando livros de execução. Esses são playbooks que executam ações como acessar e analisar dados relevantes, tomar medidas para isolar sistemas comprometidos e pesquisar ameaças para validar alertas e executar uma resposta a incidentes.
- Oferece painéis e relatórios para documentar a resposta a incidentes para melhorar os principais indicadores de desempenho do SOC e pode melhorar consideravelmente a segurança da rede para as organizações.

O SIEM ajuda a soar o alarme para atividades mal-intencionadas. Os analistas terão que agir sobre a ameaça. A SOAR ajuda os analistas a responder à ameaça.

### Sistemas SIEM

Existem vários sistemas SIEM. O SolarWinds Security Event Manager e o Splunk Enterprise Security são dois dos sistemas SIEM proprietários mais populares usados pelos SoCs. Pesquise na internet para saber mais sobre esses produtos.

Neste curso, usaremos um produto de código aberto chamado Security Onion que inclui o pacote ELK para a funcionalidade SIEM. ELK é um acrônimo para três produtos da Elastic:

- **Elasticsearch** - Mecanismo de pesquisa de texto completo orientado para documentos
- **Logstash** - Sistema de processamento de pipeline que conecta “entradas” a “saídas” com “filtros” opcionais entre
- **Kibana** - Análise baseada em navegador e painel de pesquisa para Elasticsearch

Pesquise na internet para saber mais sobre Elastic.co e seu conjunto de produtos.