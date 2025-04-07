# Proteção Antimalware

### Ameaças de endpoint

O termo “endpoint” é definido de várias maneiras. Para fins deste curso, podemos definir endpoints como hosts na rede que podem acessar ou ser acessados por outros hosts na rede. Isso obviamente inclui computadores e servidores, no entanto muitos outros dispositivos também podem acessar a rede. Com o rápido crescimento da Internet das Coisas (IoT), outros tipos de dispositivos são agora endpoints na rede. Isso inclui câmeras de segurança em rede, controladores e até mesmo lâmpadas e aparelhos. Cada ponto de extremidade é potencialmente uma forma de software malicioso obter acesso a uma rede. Além disso, as novas tecnologias, como a nuvem, expandem os limites das redes empresariais para incluir locais na Internet pelos quais as empresas não são responsáveis.

Dispositivos que acessam redes remotamente através de VPNs também são endpoints que precisam ser considerados. Esses endpoints podem injetar malware na rede VPN a partir da rede pública.

Os pontos a seguir resumem algumas das razões pelas quais o malware continua sendo um grande desafio:

- De acordo com pesquisas da Cybersecurity Ventures, até 2021 uma nova organização será vítima de um ataque de ransomware a cada 11 segundos.
- Os ataques de ransomware custarão à economia global US$6 trilhões por ano até 2021.
- Em 2018, 8 milhões de tentativas de roubar recursos do sistema usando malware de criptografia foram observadas.
- De 2016 até o início de 2017, o volume global de spam aumentou drasticamente. De 8 a 10 por cento deste spam pode ser considerado malicioso, como mostrado na figura.
- Em 2020, prevê-se que o número médio de ataques cibernéticos por dispositivo macOS aumentará de 4.8 em 2018 para 14,2 em 2020.
- Vários tipos comuns de malware foram encontrados para alterar significativamente os recursos em menos de 24 horas, a fim de evitar a detecção.

Porcentagem de Spam
![[Pasted image 20250201150456.png]]

### Segurança de endpoints

A mídia de notícias geralmente cobre ataques de rede externa em redes corporativas. Estes são alguns exemplos de tais ataques:

- Ataques DoS na rede de uma organização para degradar ou mesmo interromper o acesso público a ela
- Violação do servidor web de uma organização para desfigurar sua presença na Web
- Violação de servidores de dados e hosts de uma organização para roubar informações confidenciais

Vários dispositivos de segurança de rede são necessários para proteger o perímetro da rede contra acesso externo. Como mostrado na figura, esses dispositivos podem incluir um roteador reforçado que está fornecendo serviços VPN, um firewall de próxima geração (ASA, na figura), um appliance IPS e um servidor de serviços de autenticação, autorização e contabilidade (AAA) (Servidor AAA, na figura).![[Pasted image 20250201150559.png]]
No entanto, muitos ataques se originam de dentro da rede. Portanto, proteger uma LAN interna é quase tão importante quanto proteger o perímetro externo da rede. Sem uma LAN segura, os usuários de uma organização ainda são suscetíveis a ameaças de rede e paralisações que podem afetar diretamente a produtividade e a margem de lucro de uma organização. Depois que um host interno é infiltrado, ele pode se tornar um ponto de partida para um invasor obter acesso a dispositivos críticos do sistema, como servidores e informações confidenciais.

Especificamente, há dois elementos LAN internos para proteger:

- **Endpoints** - Os hosts geralmente consistem em laptops, desktops, impressoras, servidores e telefones IP, todos eles suscetíveis a ataques relacionados a malware.
- **Infraestrutura de rede** - Os dispositivos de infraestrutura LAN interconectam pontos de extremidade e geralmente incluem switches, dispositivos sem fio e dispositivos de telefonia IP. A maioria desses dispositivos é suscetível a ataques relacionados à LAN, incluindo ataques de estouro de tabela de endereços MAC, ataques de falsificação, ataques relacionados a DHCP, ataques de tempestade de LAN, ataques de manipulação de STP e ataques de VLAN.

Este módulo se concentra na proteção de endpoints.

### Proteção contra malware baseada em host

O perímetro da rede está sempre se expandindo. As pessoas acessam recursos de rede corporativa com dispositivos móveis que usam tecnologias de acesso remoto, como VPN. Esses mesmos dispositivos também são usados em redes públicas e domésticas não seguras ou minimamente protegidas. Software antimalware/antivírus baseado em host e firewalls baseados em host são usados para proteger esses dispositivos.

**Software antivírus / antimalware**

Este é um software instalado em um host para detectar e mitigar vírus e malware. Exemplos são o Windows Defender Virus & Threat Protection, Cisco AMP for Endpoints, Norton Security, McAfee, Trend Micro e outros. Programas antimalware podem detectar vírus usando três abordagens diferentes:

- **Baseado em assinaturas** — Essa abordagem reconhece várias características de arquivos de malware conhecidos.
- **Baseado em heurística** — Essa abordagem reconhece recursos gerais compartilhados por vários tipos de malware.
- **Baseado em comportamento** — Essa abordagem emprega análise de comportamento suspeito.

Muitos programas antivírus são capazes de fornecer proteção em tempo real analisando dados conforme eles são usados pelo endpoint. Esses programas também verificam se há malware existente que pode ter entrado no sistema antes de ser reconhecível em tempo real.

A proteção antivírus baseada em host também é conhecida como baseada em agentes. O antivírus baseado em agente é executado em todas as máquinas protegidas. A proteção antivírus sem agente executa verificações em hosts a partir de um sistema centralizado. Os sistemas sem agente tornaram-se populares para ambientes virtualizados nos quais várias instâncias de SO estão sendo executadas em um host simultaneamente. Antivírus baseado em agente executado em cada sistema virtualizado pode ser um sério desperdício de recursos do sistema. O antivírus sem agente para hosts virtuais envolve o uso de um appliance virtual de segurança especial que executa tarefas de varredura otimizadas nos hosts virtuais. Um exemplo disso é o vShield da VMware.

**Firewall de host**

Este software está instalado em um host. Restringe conexões de entrada e saída a conexões iniciadas somente por esse host. Alguns softwares de firewall também podem impedir que um host se infecte e impedir que hosts infectados espalhem malware para outros hosts. Esta função está incluída em alguns sistemas operacionais. Por exemplo, o Windows inclui o Firewall do Windows Defender com Segurança Avançada

Outras soluções são produzidas por outras empresas ou organizações. As ferramentas Linux iptables e TCP Wrappers são exemplos. Os firewalls baseados em host são discutidos com mais detalhes posteriormente neste módulo.

Recomenda-se instalar um conjunto de produtos de segurança baseado em host em redes domésticas e também em redes comerciais. Esses pacotes de segurança baseados em host incluem antivírus, anti-phishing, navegação segura, sistema de prevenção de intrusões baseado em host e recursos de firewall. Essas várias medidas de segurança fornecem uma defesa em camadas que protegerá contra as ameaças mais comuns.

Além da funcionalidade de proteção fornecida pelos produtos de segurança baseados em host é a função de telemetria. A maioria dos softwares de segurança baseados em host inclui funcionalidade de registro robusta que é essencial para operações de segurança cibernética. Alguns programas de segurança baseados em host enviarão logs para um local central para análise.

Há muitos programas e pacotes de segurança baseados em host disponíveis para usuários e empresas. O laboratório de testes independente AV-TEST fornece análises de alta qualidade de proteções baseadas em host, bem como informações sobre muitos outros produtos de segurança.

Pesquise na Internet a organização AVTest para saber mais sobre o AV-TEST.

### Proteção contra malware com base na rede

As novas arquiteturas de segurança para a rede sem fronteiras enfrentam os desafios de segurança fazendo com que os endpoints usem elementos de varredura de rede. Esses dispositivos fornecem muito mais camadas de varredura do que um único ponto de extremidade possivelmente poderia. Dispositivos de prevenção de malware baseados em rede também são capazes de compartilhar informações entre si para tomar decisões melhor informadas.

A proteção de endpoints em uma rede sem fronteiras pode ser realizada usando técnicas baseadas em rede, bem como baseadas em host. Veja a seguir exemplos de dispositivos e técnicas que implementam proteções de host no nível da rede.

- **Proteção avançada contra malware (AMP)** — Isso fornece proteção de endpoint contra vírus e malware.
- **Email Security Appliance (ESA)** — Isso fornece filtragem de SPAM e e-mails potencialmente mal-intencionados antes que eles cheguem ao endpoint. Um exemplo é o Cisco ESA.
- **Web Security Appliance (WSA)** — Isso fornece filtragem de sites e lista negra para impedir que os hosts cheguem a locais perigosos na Web. O Cisco WSA fornece controle sobre como os usuários acessam a Internet e pode impor políticas de uso aceitáveis, controlar o acesso a sites e serviços específicos e verificar se há malware.
- **Controle de admissão de rede (NAC)** — Isso permite que somente sistemas autorizados e compatíveis se conectem à rede.

Essas tecnologias funcionam em conjunto umas com as outras para dar mais proteção do que as suítes baseadas em host podem fornecer, como mostrado na figura.![[Pasted image 20250201151315.png]]

# Prevenção de intrusão baseada em host

### Firewalls baseados em host

Firewalls pessoais baseados em host são programas de software autônomos que controlam o tráfego que entra ou sai de um computador. Aplicativos de firewall também estão disponíveis para telefones e tablets Android.

Firewalls baseados em host podem usar um conjunto de políticas predefinidas, ou perfis, para controlar pacotes que entram e saem de um computador. Eles também podem ter regras que podem ser diretamente modificadas ou criadas para controlar o acesso com base em endereços, protocolos e portas. Aplicativos de firewall baseados em host também podem ser configurados para emitir alertas aos usuários se um comportamento suspeito for detectado. Eles podem então oferecer ao usuário a capacidade de permitir que um aplicativo ofensivo seja executado ou ser impedido de ser executado no futuro.

O registro varia dependendo do aplicativo de firewall. Normalmente, inclui a data e a hora do evento, se a conexão foi permitida ou negada, informações sobre os endereços IP de origem ou destino dos pacotes e as portas de origem e destino dos segmentos encapsulados. Além disso, atividades comuns, como pesquisas de DNS e outros eventos de rotina, podem aparecer em logs de firewall baseados em host, portanto, filtragem e outras técnicas de análise são úteis para inspecionar grandes quantidades de dados de log.

Uma abordagem para a prevenção de intrusões é o uso de firewalls distribuídos. Os firewalls distribuídos combinam recursos de firewalls baseados em host com gerenciamento centralizado. A função de gerenciamento envia regras para os hosts e também pode aceitar arquivos de log dos hosts.

Independentemente de serem instalados completamente no host ou distribuídos, os firewalls baseados em host são uma camada importante de segurança de rede, juntamente com firewalls baseados em rede. Aqui estão alguns exemplos de firewalls baseados em host:

- **Firewall do Windows Defender** — Primeiro incluído no Windows XP, o Firewall do Windows (agora Firewall do Windows Defender) usa uma abordagem baseada em perfil para a funcionalidade do firewall. O acesso a redes públicas é atribuído ao perfil restritivo do firewall Público. O perfil Privado é para computadores que estão isolados da Internet por outros dispositivos de segurança, como um roteador doméstico com funcionalidade de firewall. O perfil Domínio é o terceiro perfil disponível. Ele é escolhido para conexões com uma rede confiável, como uma rede de negócios que se supõe ter uma infra-estrutura de segurança adequada. O Firewall do Windows tem funcionalidade de registo e pode ser gerido centralmente com políticas de segurança de grupo personalizadas a partir de um servidor de gestão, como o System Center 2012 Configuration Manager.
- **iptables** — Esta é uma aplicação que permite aos administradores de sistema Linux configurar regras de acesso à rede que fazem parte dos módulos Netfilter do kernel Linux.
- **nftables** — O sucessor do iptables, nftables é um aplicativo de firewall do Linux que usa uma máquina virtual simples no kernel do Linux. O código é executado dentro da máquina virtual que inspeciona pacotes de rede e implementa regras de decisão relativas à aceitação e encaminhamento de pacotes.
- **TCP Wrappers** — Este é um sistema de registro e controle de acesso baseado em regras para Linux. A filtragem de pacotes é baseada em endereços IP e serviços de rede.

### Detecção de intrusão baseada em host

A distinção entre detecção de intrusão baseada em host e prevenção de intrusões é desfocada. Na verdade, algumas fontes referem-se a sistemas de detecção e prevenção de intrusões baseados em host (HIPDS). Como a indústria parece favorecer o uso da sigla HIDS, vamos usá-la em nossa discussão aqui.

Um sistema de detecção de intrusões baseado em host (HIDS) foi projetado para proteger hosts contra malware conhecido e desconhecido. Um HIDS pode realizar monitoramento detalhado e relatórios sobre a configuração do sistema e a atividade do aplicativo. Ele pode fornecer análise de log, correlação de eventos, verificação de integridade, aplicação de políticas, detecção de rootkit e alertas. Um HIDS incluirá frequentemente um ponto de extremidade do servidor de gerenciamento, conforme mostrado na figura.

Um HIDS é um aplicativo de segurança abrangente que combina as funcionalidades de aplicativos antimalware com funcionalidade de firewall. Um HIDS não só detecta malware, mas também pode impedi-lo de ser executado se ele deve chegar a um host. Como o software HIDS deve ser executado diretamente no host, ele é considerado um sistema baseado em agentes.![[Pasted image 20250201151851.png]]

### Operação HIDS

Pode-se dizer que os sistemas de segurança baseados em host funcionam como sistemas de detecção e prevenção porque evitam ataques conhecidos e detectam ataques potenciais desconhecidos. Um HIDS usa estratégias proativas e reativas. Um HIDS pode impedir intrusões porque utiliza assinaturas para detectar malware conhecido e impedir que infecte um sistema. No entanto, esta estratégia só é boa contra ameaças conhecidas. As assinaturas não são eficazes contra ameaças novas ou de dia zero. Além disso, algumas famílias de malware exibem polimorfismo. Isso significa que variações de um tipo, ou família, de malware podem ser criadas por invasores que evitarão detecções baseadas em assinaturas alterando aspectos da assinatura de malware apenas o suficiente para que ele não seja detectado. Um conjunto adicional de estratégias é usado para detectar a possibilidade de intrusões bem-sucedidas por malware que evade a detecção de assinaturas:

- **Baseado em anomalia** - O comportamento do sistema host é comparado a um modelo de linha de base aprendido do comportamento normal. Desvios significativos da linha de base são interpretados como resultado de algum tipo de intrusão. Se uma intrusão for detectada, o HIDS poderá registrar detalhes da intrusão, enviar alertas para sistemas de gerenciamento de segurança e tomar medidas para evitar o ataque. A linha de base medida é derivada do comportamento do usuário e do sistema. Como muitas coisas além do malware podem fazer com que o comportamento do sistema mude, a detecção de anomalias pode criar muitos resultados errôneos, o que pode aumentar a carga de trabalho para o pessoal de segurança e também reduzir a credibilidade do sistema.
- **Baseado em políticas** - O comportamento normal do sistema é descrito por regras, ou a violação de regras, que são predefinidas. Violação dessas políticas resultará em ação do HIDS. O HIDS pode tentar encerrar processos de software que violaram as regras e pode registrar esses eventos e alertar o pessoal para violações. A maioria dos softwares HIDS vem com um conjunto de regras predefinidas. Com alguns sistemas, os administradores podem criar políticas personalizadas que podem ser distribuídas aos hosts a partir de um sistema central de gerenciamento de políticas.

### Produtos HIDS

Há uma série de produtos HIDS no mercado hoje. A maioria deles utiliza software no host e algum tipo de funcionalidade centralizada de gerenciamento de segurança que permite a integração com serviços de monitoramento de segurança de rede e inteligência contra ameaças. Exemplos são Cisco AMP, AlienVault USM, Tripwire e Segurança HIDS de código aberto (OSSEC).

O OSSEC usa um servidor de gerenciador central e agentes instalados em hosts individuais. Atualmente, os agentes estão disponíveis para plataformas Mac, Windows, Linux e Solaris. O servidor OSSEC, ou Manager, também pode receber e analisar alertas de uma variedade de dispositivos de rede e firewalls através de syslog. O OSSEC monitora os logs do sistema nos hosts e também realiza a verificação da integridade do arquivo. O OSSEC pode detectar rootkits e outros malwares e também pode ser configurado para executar scripts ou aplicativos em hosts em resposta a gatilhos de eventos.

Pesquise OSSEC na internet para saber mais.

# Segurança de aplicações

### Superfície de ataque

Lembre-se de que uma vulnerabilidade é uma fraqueza em um sistema ou em seu design que pode ser explorada por uma ameaça. Uma superfície de ataque é a soma total das vulnerabilidades em um determinado sistema que é acessível a um invasor. A superfície de ataque pode consistir em portas abertas em servidores ou hosts, software executado em servidores voltados para a Internet, protocolos de rede sem fio e até mesmo usuários.

A superfície de ataque continua a se expandir, como mostrado na figura. Mais dispositivos estão se conectando a redes através da Internet das Coisas (IoT) e BYOD (Traga seu próprio dispositivo). Grande parte do tráfego de rede agora flui entre dispositivos e algum local na nuvem. O uso de dispositivos móveis continua a aumentar. Todas essas tendências contribuem para uma previsão de que o tráfego IP global aumentará três vezes nos próximos cinco anos.

O Instituto SANS descreve três componentes da superfície de ataque:

- **Superfície de ataque de rede** - O ataque explora vulnerabilidades em redes. Isso pode incluir protocolos convencionais de rede com e sem fio, bem como outros protocolos sem fio usados por smartphones ou dispositivos IoT. Os ataques de rede também exploram vulnerabilidades nas camadas de rede e transporte.
- **Superfície de ataque de software** - O ataque é entregue através da exploração de vulnerabilidades em aplicativos de software baseados na Web, na nuvem ou em host.
- **Superfície de ataque humano** - O ataque explora fraquezas no comportamento do usuário. Tais ataques incluem engenharia social, comportamento malicioso por parte de dentro de confiança e erro do usuário.
![[Pasted image 20250201152513.png]]

### Lista negra e lista branca de aplicativos

Uma maneira de diminuir a superfície de ataque é limitar o acesso a ameaças potenciais criando listas de aplicativos proibidos. Isso é conhecido como lista negra.

As listas negras de aplicativos podem ditar quais aplicativos de usuário não têm permissão para serem executados em um computador. Da mesma forma, as listas brancas podem especificar quais programas podem ser executados, conforme mostrado na figura. Dessa forma, aplicativos vulneráveis conhecidos podem ser impedidos de criar vulnerabilidades em hosts de rede.

As listas brancas são criadas de acordo com uma linha de base de segurança estabelecida por uma organização. A base de referência estabelece uma quantidade de risco aceite e as componentes ambientais que contribuem para esse nível de risco. Software não incluído na lista branca pode violar a linha de base de segurança estabelecida aumentando o risco.

Lista de bloqueio de aplicativos e lista de permissões
![[Pasted image 20250201152643.png]]

Os sites também podem ser incluídos na lista branca e na lista negra. Essas listas negras podem ser criadas manualmente ou podem ser obtidas de vários serviços de segurança. As listas negras podem ser continuamente atualizadas pelos serviços de segurança e distribuídas para firewalls e outros sistemas de segurança que as utilizam. O sistema de gerenciamento de segurança Firepower da Cisco é um exemplo de um sistema que pode acessar o serviço de inteligência de segurança Cisco Talos para obter listas negras. Essas listas negras podem então ser distribuídas para dispositivos de segurança dentro de uma rede corporativa.

Pesquise na internet The Spamhaus Project, que é um exemplo de um serviço gratuito de lista negra.

### Sandboxing baseado em sistema

Sandboxing é uma técnica que permite que arquivos suspeitos sejam executados e analisados em um ambiente seguro. As sandboxes de análise automatizada de malware oferecem ferramentas que analisam o comportamento do malware. Essas ferramentas observam os efeitos da execução de malware desconhecido para que os recursos do comportamento de malware possam ser determinados e usados para criar defesas contra ele.

Como mencionado anteriormente, o malware polimórfico muda com freqüência e o novo malware aparece regularmente. O malware entrará na rede apesar dos sistemas de segurança baseados em host e perímetro mais robustos. HIDS e outros sistemas de detecção podem criar alertas sobre suspeita de malware que pode ter entrado na rede e executado em um host. Sistemas como o Cisco AMP podem rastrear a trajetória de um arquivo através da rede e podem “reverter” eventos de rede para obter uma cópia do arquivo baixado. Esse arquivo pode ser executado em uma área restrita, como o Cisco Threat Grid Glivebox, e as atividades do arquivo documentado pelo sistema. Essas informações podem então ser usadas para criar assinaturas para impedir que o arquivo entre na rede novamente. As informações também podem ser usadas para criar regras de detecção e reproduções automatizadas que identificam outros sistemas que foram infectados.

Cuckoo Sandbox é um sandbox popular sistema de análise de malware livre. Ele pode ser executado localmente e ter amostras de malware enviadas a ele para análise. Existem várias outras sandboxes públicas online. Esses serviços permitem que amostras de malware sejam carregadas para análise. Alguns desses serviços são VirusTotal, Joe Sandbox e CrowdStrike Falcon Sandbox.

Uma ferramenta online interessante é ANY.RUN, que é mostrado na figura. Ele oferece a capacidade de carregar uma amostra de malware para análise como qualquer sandbox online. No entanto, ele oferece uma funcionalidade de relatórios interativos muito rica que está cheia de detalhes sobre o exemplo de malware. ANY.RUN executa o malware e captura uma série de capturas de tela do malware se ele tiver elementos interativos que são exibidos na tela do computador sandbox. Você pode exibir amostras públicas que foram enviadas por usuários ANY.RUN para investigar informações sobre malware recém-descoberto ou malware que está circulando atualmente na Internet. Os relatórios incluem a atividade de rede e internet do malware, incluindo solicitações HTTP e consultas DNS. Os arquivos que são executados como parte do processo de malware são mostrados e classificados como ameaça. Os detalhes estão disponíveis para os arquivos, incluindo vários valores de hash, exibições hexadecimais e ASCII do conteúdo do arquivo e as alterações do sistema feitas pelos arquivos. Além disso, identificar indicadores de comprometimento, como hashes de arquivo de malware, solicitações DNS e as conexões IP feitas pelo malware também são mostrados. Finalmente, as táticas adotadas pelo malware são mapeadas para a Matriz MITRE ATT&CK com cada tática vinculada aos detalhes no site MITRE.