
# Topologias de rede

### Representações de rede

Arquitetos e administradores de rede devem ser capazes de mostrar como suas redes serão. Eles precisam ser capazes de ver facilmente quais componentes se conectam a outros componentes, onde eles serão localizados e como eles serão conectados. Os diagramas de redes geralmente usam símbolos, como os mostrados na figura, para representar os diferentes dispositivos e conexões que compõem uma rede.

![[Pasted image 20250117204345.png]]Um diagrama fornece uma maneira fácil de entender como os dispositivos se conectam em uma rede grande. Esse tipo de “fotografia” de uma rede é conhecido como um diagrama de topologia. A capacidade de reconhecer as representações lógicas dos componentes físicos de rede é crucial para se permitir visualizar a organização e a operação de uma rede.

Além dessas representações, é utilizada terminologia especializada para descrever como cada um desses dispositivos e mídias se conectam:

- **Placa de interface de rede (NIC)** - Uma NIC conecta fisicamente o dispositivo final à rede.
- **Porta física** - Um conector ou tomada em um dispositivo de rede onde a mídia se conecta a um dispositivo final ou outro dispositivo de rede.
- **Interface** - Portas especializadas em um dispositivo de rede que se conectam a redes individuais. Como os roteadores conectam redes, as portas em um roteador são chamadas de interfaces de rede.

**Observação**: Os termos porta e interface são frequentemente usados alternadamente.

### Diagramas de Topologia

Os diagramas de topologia são documentação obrigatória para qualquer pessoa que trabalhe com uma rede. Eles fornecem um mapa visual de como a rede está conectada. Existem dois tipos de diagramas de topologia: físicos e lógicos.

**Diagramas de topologia física**

Os diagramas de topologia física ilustram a localização física dos dispositivos intermediários e a instalação dos cabos, conforme mostrado na figura. Você pode ver que as salas em que esses dispositivos estão localizados estão rotuladas nesta topologia física.
![[Pasted image 20250117204532.png]]

**Diagramas de topologia lógica**

Diagramas de topologia lógica ilustram dispositivos, portas e o esquema de endereçamento da rede, conforme mostrado na figura. Você pode ver quais dispositivos finais estão conectados a quais dispositivos intermediários e que mídia está sendo usada.
![[Pasted image 20250117204604.png]]

As topologias mostradas nos diagramas físico e lógico são apropriadas para seu nível de entendimento nesse momento do curso. Pesquise na Internet “diagramas de topologia de rede” para ver alguns exemplos mais complexos. Se você adicionar a palavra "cisco" para sua frase de pesquisa, você encontrará muitas topologias usando ícones semelhantes ao que você viu nessas figuras.

### Redes de Vários Tamanhos

Agora que você está familiarizado com os componentes que compõem as redes e suas representações em topologias físicas e lógicas, você está pronto para aprender sobre os muitos tipos diferentes de redes.

Existem redes de vários tamanhos. Eles variam de redes simples compostas por dois computadores a redes que conectam milhões de dispositivos.

As redes domésticas simples permitem que você compartilhe recursos, como impressoras, documentos, imagens e música, entre alguns dispositivos finais locais.

As redes de pequeno escritório e escritório doméstico (SOHO) permitem que as pessoas trabalhem em casa ou em um escritório remoto. Muitos trabalhadores independentes usam esses tipos de redes para anunciar e vender produtos, pedir suprimentos e se comunicar com os clientes.

Empresas e grandes organizações usam redes para fornecer consolidação, armazenamento e acesso a informações em servidores de rede. As redes fornecem e-mail, mensagens instantâneas e colaboração entre funcionários. Muitas organizações usam a conexão de sua rede à Internet para fornecer produtos e serviços aos clientes.

A internet é a maior rede existente. Na verdade, o termo Internet significa uma “rede de redes”. É uma coleção de redes públicas e privadas interconectadas.

Em pequenas empresas e residências, muitos computadores funcionam como servidores e clientes na rede. Esse tipo de rede é chamado de rede ponto a ponto.

### LANs e WANs

As infra-estruturas de rede variam muito em termos de:

- Tamanho da área coberta;
- Número de usuários conectados;
- Número e tipos de serviços disponíveis;
- Área de responsabilidade.

Os dois tipos mais comuns de infraestruturas de rede são as redes locais (LANs) e as redes de longa distância (WANs). Uma LAN é uma infraestrutura de rede que fornece acesso a usuários e dispositivos finais em uma pequena área geográfica. Normalmente, uma LAN é usada em um departamento dentro de uma empresa, uma casa ou uma rede de pequenas empresas. Uma WAN é uma infraestrutura de rede que fornece acesso a outras redes em uma ampla área geográfica, que normalmente pertence e é gerenciada por uma corporação maior ou por um provedor de serviços de telecomunicações. A figura mostra LANs conectadas a uma WAN.
![[Pasted image 20250117204848.png]]

**LANs**

Uma LAN é uma infraestrutura de rede que abrange uma pequena área geográfica. As LANs têm características específicas:

- LANs interconectam dispositivos finais em uma área limitada, como uma casa, uma escola, um edifício de escritórios ou um campus.
- Uma LAN é geralmente administrada por uma única organização ou pessoa. O controle administrativo é imposto no nível da rede e governa as políticas de segurança e controle de acesso.
- As LANs fornecem largura de banda de alta velocidade para dispositivos finais internos e dispositivos intermediários.

**WANs**

A figura mostra uma WAN que interconecta duas LANs. Uma WAN é uma infraestrutura de rede que abrange uma ampla área geográfica. As WANs geralmente são gerenciadas por provedores de serviços (SPs) ou provedores de serviços de Internet (ISPs).

As WANs têm características específicas:

- As WANS interconectam as LANs em grandes áreas geográficas, como entre cidades, estados, províncias, países ou continentes.
- As WANs são geralmente administradas por vários prestadores de serviço.
- As WANs geralmente fornecem links de velocidade mais lenta entre as LANs.
![[Pasted image 20250117205007.png]]

### O modelo de design de rede de três camadas

A LAN com fio do campus usa um modelo de design hierárquico para separar a topologia da rede em grupos ou camadas modulares. Separar o design em camadas permite que cada camada implemente funções específicas, o que simplifica o design da rede. Isso também simplifica a implantação e o gerenciamento da rede.

A LAN com fio do campus permite a comunicação entre dispositivos em um prédio ou grupo de prédios, bem como a interconexão com a WAN e a borda da Internet no núcleo da rede.

Um projeto de LAN hierárquico inclui as camadas de acesso, distribuição e núcleo, conforme mostrado na figura.
![[Pasted image 20250117205141.png]]

Cada camada é projetada para atender a funções específicas.

A camada de acesso oferece endpoints e acesso direto dos usuários à rede. A camada de distribuição agrega camadas de acesso e oferece ⁪conectividade aos serviços. Por fim, a camada de núcleo oferece conectividade entre as camadas de distribuição para os grandes ambientes de LAN. O tráfego do usuário é iniciado na camada de acesso e atravessa as demais camadas se a funcionalidade dessas camadas for necessária.

Embora o modelo hierárquico possua três camadas, algumas redes corporativas menores podem implementar um projeto hierárquico de duas camadas. Em um projeto hierárquico de duas camadas, as camadas de núcleo e distribuição são reduzidas em uma camada, reduzindo o custo e a complexidade, conforme mostrado na figura.
![[Pasted image 20250117205234.png]]

Em arquiteturas de rede simples ou em malha, as mudanças tendem a afetar um grande número de sistemas. O design hierárquico ajuda a restringir as alterações operacionais a um subconjunto da rede, o que facilita o gerenciamento e melhora a resiliência. A estruturação modular da rede em elementos pequenos e fáceis de entender também facilita a resiliência por meio de um melhor isolamento de falhas.

### Arquiteturas de segurança comuns

O design do firewall é principalmente sobre interfaces de dispositivo que permitem ou negam tráfego com base na origem, no destino e no tipo de tráfego. Alguns designs são tão simples quanto designar uma rede externa e uma rede interna, que são determinados por duas interfaces em um firewall.

Aqui estão três designs comuns de firewall.

**Privado e Público**
Como mostrado na figura, a rede pública (ou rede externa) não é confiável e a rede privada (ou rede interna) é confiável.

Normalmente, um firewall com duas interfaces é configurado da seguinte forma:

- O tráfego proveniente da rede privada é permitido e inspecionado à medida que viaja em direção à rede pública. É permitido o tráfego inspecionado que retorna da rede pública e associado ao tráfego originado da rede privada.
- O tráfego originado da rede pública e que viaja para a rede privada geralmente é bloqueado.
![[Pasted image 20250117205441.png]]

**Zona desmilitarizada**

Uma zona desmilitarizada (DMZ) é um projeto de firewall onde normalmente há uma interface interna conectada à rede privada, uma interface externa conectada à rede pública e uma interface DMZ, conforme mostrado na figura.

- O tráfego proveniente da rede privada é inspecionado à medida que ele viaja para a rede pública ou DMZ. Este tráfego é permitido com pouca ou nenhuma restrição. Tráfego inspecionado que retorna da DMZ ou da rede pública para a rede privada é permitido.
- O tráfego originado da rede DMZ e que viaja para a rede privada geralmente é bloqueado.
- O tráfego originado da rede DMZ e viajando para a rede pública é permitido seletivamente com base nos requisitos de serviço.
- O tráfego proveniente da rede pública e que viaja em direção à DMZ é seletivamente permitido e inspecionado. Esse tipo de tráfego normalmente é tráfego de email, DNS, HTTP ou HTTPS. O tráfego de retorno da DMZ para a rede pública é permitido dinamicamente.
- O tráfego originado da rede pública e que viaja para a rede privada está bloqueado.
![[Pasted image 20250117205611.png]]

**Os firewalls de política baseados em zona**

Os firewalls de política baseados em zona (ZPFs) usam o conceito de zonas para fornecer flexibilidade adicional. Uma zona é um grupo de uma ou mais interfaces que têm funções ou recursos semelhantes. As zonas ajudam a especificar onde uma regra ou política de firewall do Cisco IOS deve ser aplicada. Na figura, as políticas de segurança para LAN 1 e LAN 2 são semelhantes e podem ser agrupadas em uma zona para configurações de firewall. Por padrão, o tráfego entre interfaces na mesma zona não está sujeito a nenhuma política e passa livremente. No entanto, todo o tráfego de zona para zona está bloqueado. Para permitir o tráfego entre as zonas, uma política que permite ou inspeciona o tráfego deve ser configurada.

A única exceção a esta política padrão **deny any** é a zona própria do roteador. A zona auto é o próprio roteador e inclui todos os endereços IP da interface do roteador. As configurações de política que incluem a zona automática aplicar-se-iam ao tráfego destinado e proveniente do roteador. Por padrão, não há nenhuma política para esse tipo de tráfego. O tráfego que deve ser considerado ao projetar uma política para a auto zona inclui o tráfego de plano de gerenciamento e plano de controle, como SSH, SNMP e protocolos de roteamento.
![[Pasted image 20250117205743.png]]

# Dispositivos de segurança

### Firewalls

Um firewall é um sistema ou grupo de sistemas que aplica uma política de controle de acesso entre redes.

**Propriedades comuns do firewall**

Todos os firewalls compartilham algumas propriedades comuns:

- Os firewalls são resistentes a ataques de rede.
- Firewalls são o único ponto de trânsito entre redes corporativas internas e redes externas porque todo o tráfego flui através do firewall.
- Os firewalls aplicam a política de controle de acesso.

**Benefícios do firewall**

Existem vários benefícios do uso de um firewall em uma rede:

- Eles impedem a exposição de hosts, recursos e aplicações sensíveis a usuários não confiáveis.
- Eles sanitizam o fluxo do protocolo, o que impede a exploração de falhas no protocolo.
- Eles bloqueiam dados maliciosos de servidores e clientes.
- Eles reduzem a complexidade do gerenciamento de segurança descarregando a maior parte do controle de acesso à rede para alguns firewalls na rede.

**Limitações do firewall**

Os firewalls também têm algumas limitações:

- Um firewall mal configurado pode ter sérias conseqüências para a rede, como se tornar um único ponto de falha.
- Os dados de muitos aplicações não podem ser transmitidos por firewalls com segurança.
- Os usuários podem procurar proativamente maneiras de contornar o firewall para receber material bloqueado, o que expõe a rede a possíveis ataques.
- O desempenho da rede pode diminuir.
- O tráfego não autorizado pode ser encapsulado ou escondido como tráfego legítimo através do firewall.

### Descrições de tipo de firewall

É importante entender os diferentes tipos de firewalls e suas capacidades específicas para que o firewall correto seja usado para cada situação.

**firewalls de filtragem de pacotes (sem estado)**

Os firewalls de filtragem de pacotes geralmente fazem parte de um firewall de roteador, que permite ou nega tráfego com base nas informações da Camada 3 e da Camada 4. Eles são firewalls sem estado que usam uma simples pesquisa de tabela de políticas que filtra o tráfego com base em critérios específicos.

Por exemplo, os servidores SMTP escutam a porta 25 por padrão. Um administrador pode configurar o firewall de filtragem de pacotes para bloquear a porta 25 de uma estação de trabalho específica para impedir que ele transmita um vírus de e-mail
![[Pasted image 20250121181337.png]]

**Firewall com monitoração de estado**

Firewalls com estado são as tecnologias de firewall mais versáteis e mais comuns em uso. Os firewalls stateful fornecem filtragem de pacotes stateful usando informações de conexão mantidas em uma tabela de estado. Filtragem com estado é uma arquitetura de firewall classificada na camada de rede. Ele também analisa o tráfego na camada 4 da OSI e na camada 5.
![[Pasted image 20250121181533.png]]

**Firewall de gateway de aplicativo**

Um firewall de gateway de aplicação (firewall proxy), conforme mostrado na figura, filtra as informações nas camadas 3, 4, 5 e 7 do modelo de referência OSI. A maior parte do controle e filtragem do firewall é feita em software. Quando um cliente precisa acessar um servidor remoto, ele se conecta a um servidor proxy. O servidor proxy se conecta ao servidor remoto em nome do cliente. Portanto, o servidor só vê uma conexão do servidor proxy.
![[Pasted image 20250121181641.png]]

**Firewall de última geração**

Os firewalls de última geração (NGFW) vão além dos firewalls de estado, fornecendo:

- Prevenção de intrusão integrada
- Reconhecimento e controle de aplicações para ver e bloquear aplicativos arriscados
- Caminhos de atualização para incluir futuros feeds de informações
- Técnicas para lidar com ameaças de segurança em evolução

Outros métodos de implementação de firewalls incluem:

- **Firewall baseado em host (servidor e pessoal)** - Um PC ou servidor com software de firewall em execução nele.
- **Firewall transparente** - Filtra o tráfego IP entre um par de interfaces em ponte.
- **Firewall híbrido** - Uma combinação dos vários tipos de firewall. Por exemplo, um firewall de inspeção de aplicativos combina um firewall com estado com um firewall de gateway de aplicativo.

### Dispositivos de prevenção e detecção de intrusão

Uma mudança de paradigma de arquitetura de rede é necessária para se defender contra ataques rápidos e em evolução. Isso deve incluir sistemas de prevenção e detecção de baixo custo, como sistemas de detecção de intrusão (IDS) ou os sistemas de prevenção de intrusão mais escalonáveis (IPS). A arquitetura de rede integra essas soluções nos pontos de entrada e saída da rede.

Ao implementar IDS ou IPS, é importante estar familiarizado com os tipos de sistemas disponíveis, abordagens baseadas em host e em rede, o posicionamento desses sistemas, a função das categorias de assinatura e possíveis ações que um roteador Cisco IOS pode executar quando um ataque é detectado.

A figura mostra como um dispositivo IPS lida com tráfego malicioso.
![[Pasted image 20250121182022.png]]
As tecnologias IDS e IPS são implantadas como sensores. Um sensor IDS ou IPS pode estar na forma de vários dispositivos diferentes:

- Um roteador configurado com o software Cisco IOS IPS
- Um dispositivo projetado especificamente para fornecer serviços IDS ou IPS dedicados
- Um módulo de rede instalado em um dispositivo de segurança adaptável (ASA), switch ou roteador

As tecnologias IDS e IPS usam assinaturas para detectar padrões no tráfego da rede. Uma assinatura é um conjunto de regras que um IDS ou IPS usa para detectar atividades maliciosas. As assinaturas podem ser usadas para detectar violações graves de segurança, para detectar ataques de rede comuns e para coletar informações. As tecnologias IDS e IPS podem detectar padrões de assinatura atômica (pacote único) ou padrões de assinatura composta (pacote múltiplo).

### Vantagens e desvantagens de IDS e IPS
![[Pasted image 20250121182220.png]]

**Vantagens IDS**

Um IDS é implantado no modo off-line e, portanto:

- Os IDs não afetam o desempenho da rede. Especificamente, ele não introduz latência, variação ou outros problemas de fluxo de tráfego.
- Os IDs não afetam a funcionalidade de rede se o sensor falhar. Isso afeta apenas a capacidade do IDS para analisar os dados.

**Desvantagens IDS**

As desvantagens de um IDS incluem:

- Um sensor IDS não pode parar o pacote de disparo e é menos útil na interrupção de vírus de e-mail e ataques automatizados, como worms.
- Ajustar os sensores IDS para atingir os níveis esperados de detecção de intrusão pode ser muito demorado. Os usuários que implantam ações de resposta do sensor IDS devem ter uma política de segurança bem projetada e uma boa compreensão operacional de suas implantações de IDS.
- Uma implementação de IDS é mais vulnerável a técnicas de evasão de segurança de rede porque não está em linha.

**Vantagens IPS**

As vantagens de um IPS incluem:

- Um sensor IPS pode ser configurado para executar uma perda de pacotes para interromper o pacote de gatilho, os pacotes associados a uma conexão ou os pacotes de um endereço IP de origem.
- Como os sensores IPS estão em linha, eles podem usar a normalização de fluxo. Normalização de fluxo é uma técnica usada para reconstruir o fluxo de dados quando o ataque ocorre em vários segmentos de dados.

**Desvantagens IPS**

As desvantagens de um IPS incluem:

- Como ele é implantado em linha, erros, falhas e sobrecarregar o sensor IPS com muito tráfego podem ter um efeito negativo no desempenho da rede.
- Um sensor IPS pode afetar o desempenho da rede introduzindo latência e jitter.
- Um sensor IPS deve ser dimensionado e implementado adequadamente para que aplicativos sensíveis ao tempo, como VoIP, não sejam afetados negativamente.

Você pode implantar um IPS e um IDS. Usar uma dessas tecnologias não anula o uso da outra. Na verdade, as tecnologias IDS e IPS podem se complementar.

Por exemplo, um IDS pode ser implementado para validar a operação de IPS porque o IDS pode ser configurado para inspeção de pacotes mais profunda off-line. Isso permite que o IPS se concentre em menos, mas mais críticos padrões de tráfego em linha.

Decidir qual implementação usar se baseia nos objetivos de segurança da organização, conforme indicado em sua política de segurança de rede.

### Tipos de IPS

Existem dois tipos principais de IPS disponíveis: IPS baseado em host e IPS baseado em rede.

**IPS de host**

O IPS baseado em host (HIPS) é um software instalado em um host para monitorar e analisar atividades suspeitas. Uma vantagem significativa do HIPS é que ele pode monitorar e proteger o sistema operacional e os processos críticos do sistema que são específicos para esse host. Com conhecimento detalhado do sistema operacional, o HIPS pode monitorar atividades anormais e impedir que o host execute comandos que não correspondam ao comportamento típico. Esse comportamento suspeito ou mal-intencionado pode incluir atualizações de registro não autorizadas, alterações no diretório do sistema, execução de programas de instalação e atividades que causam estouros de buffer. O tráfego de rede também pode ser monitorado para impedir que o host participe de um ataque de negação de serviço (DoS) ou faça parte de uma sessão de FTP ilícita.

HIPS pode ser pensado como uma combinação de software antivírus, software antimalware e um firewall. Combinado com um IPS baseado em rede, o HIPS é uma ferramenta eficaz para fornecer proteção adicional para o host.

Uma desvantagem do HIPS é que ele opera apenas a nível local. Ele não tem uma visão completa da rede ou eventos coordenados que possam estar acontecendo em toda a rede. Para ser eficaz em uma rede, o HIPS deve ser instalado em cada host e ter suporte para cada sistema operacional. A tabela lista as vantagens e desvantagens do HIPS.![[Pasted image 20250121182705.png]]

**IPS baseado em rede**

Um IPS baseado em rede pode ser implementado usando um dispositivo IPS dedicado ou não dedicado. As implementações de IPS baseadas em rede são um componente crítico da prevenção de intrusões. Existem soluções IDS/IPS baseadas em host, mas elas devem ser integradas a uma implementação IPS baseada em rede para garantir uma arquitetura de segurança robusta.

Os sensores detectam atividades maliciosas e não autorizadas em tempo real e podem agir quando necessário. Como mostrado na figura, os sensores são implantados em pontos de rede designados. Isso permite que os gerentes de segurança monitorem a atividade da rede enquanto ela estiver ocorrendo, independentemente do local do alvo de ataque.
![[Pasted image 20250121182823.png]]

### Dispositivos de segurança especializados

Há uma variedade de dispositivos de segurança especializados disponíveis. Aqui estão alguns exemplos.

**AMP**
Cisco Advanced Malware Protection (AMP) é uma solução de proteção e análise de malware avançada de classe empresarial. Ele fornece proteção abrangente contra malware para organizações antes, durante e depois de um ataque:

- Antes de um ataque, a AMP fortalece as defesas e protege contra ameaças conhecidas e emergentes.
- Durante um ataque, o AMP identifica e impede que tipos de arquivos violadores de políticas, tentativas de exploração e arquivos mal-intencionados se infiltrem na rede.
- Após um ataque ou após a inspeção inicial de um arquivo, o AMP vai além dos recursos de detecção pontual e monitora e analisa continuamente todas as atividades e tráfego de arquivos, independentemente da disposição, procurando por quaisquer indicações de comportamento malicioso. Se um arquivo com uma disposição desconhecida ou previamente considerada "boa" começar a se comportar mal, o AMP o detectará e alertará instantaneamente as equipes de segurança com uma indicação de comprometimento. Em seguida, ele proporciona visibilidade em relação à origem do malware, aos sistemas afetados e às ações dessa ameaça.

A AMP acessa a inteligência de segurança coletiva do Cisco Talos Security Intelligence and Research Group. O Talos detecta e correlaciona ameaças em tempo real usando a maior rede de detecção de ameaças do mundo.

**WSA**
Um Cisco Web Security Appliance (WSA) é um gateway da Web seguro que combina proteções líderes para ajudar as organizações a enfrentar os desafios crescentes de proteção e controle do tráfego da Web. O WSA protege a rede bloqueando automaticamente sites arriscados e testando sites desconhecidos antes de permitir que os usuários os acessem. O WSA fornece proteção contra malware, visibilidade e controle de aplicativos, controles de política de uso aceitável, relatórios criteriosos e mobilidade segura.

Embora o WSA proteja a rede contra intrusões de malware, ele não fornece proteção para usuários que desejam se conectar à Internet diretamente fora da rede protegida, como em um serviço Wi-Fi público. Neste caso, o PC do usuário pode ser infectado com malware que pode então se espalhar para outras redes e dispositivos. Para ajudar a proteger os PCs dos usuários contra esses tipos de infecções de malware, há o Cisco Cloud Web Security (CWS).

O CWS, juntamente com o WSA, fornece proteção abrangente contra malware e os impactos associados. A solução Cisco CWS impõe a comunicação segura de e para a Internet e fornece aos funcionários remotos o mesmo nível de segurança que os funcionários no local ao usar um laptop emitido pelo empregador. O Cisco CWS incorpora duas funções principais, filtragem da Web e segurança da Web, e ambas são acompanhadas por relatórios extensos e centralizados.

**ESA**
Um Cisco Email Security Appliance (ESA) /Cisco Cloud Email Security ajuda a mitigar ameaças baseadas em e-mail. O Cisco ESA defende sistemas de e-mail de missão crítica.

O Cisco ESA é constantemente atualizado por feeds em tempo real do Cisco Talos, que detecta e correlaciona ameaças usando um sistema mundial de monitoramento de banco de dados.

Estas são algumas das principais características da ESA:

- **Inteligência global contra ameaças** - O Cisco Talos oferece uma visão 24 horas da atividade de tráfego global. Ele analisa anomalias, descobre novas ameaças e monitora as tendências do tráfego.
- **Bloqueio de spam** - Uma defesa em várias camadas combina uma camada externa de filtragem com base na reputação do remetente e uma camada interna de filtragem que realiza uma análise profunda da mensagem.
- **Proteção avançada contra malware** - Inclui AMP que tira proveito da vasta rede de inteligência de segurança na nuvem do Sourcefire. Ele oferece proteção em todo o continuum do ataque antes, durante e depois de um ataque.
- **Controle de mensagens de saída** - Controla mensagens de saída para ajudar a garantir que mensagens importantes estejam em conformidade com os padrões do setor e estejam protegidas em trânsito.

# Serviços de segurança

### Controle de tráfego com ACLs

Uma lista de controle de acesso (ACL) é uma série de comandos que controlam se um dispositivo encaminha ou descarta pacotes com base nas informações encontradas no cabeçalho do pacote. Quando configuradas, as ACLs executam as seguintes tarefas:

- Eles limitam o tráfego da rede para aumentar o desempenho da rede. Por exemplo, se a política corporativa não permite tráfego de vídeo na rede, as ACLs que bloqueiam tráfego de vídeo podem ser configuradas e aplicadas. Isso reduziria significativamente a carga da rede e aumentaria o desempenho da rede.
- Eles fornecem controle de fluxo de tráfego. As ACLs podem restringir o fornecimento de atualizações de roteamento para garantir que as atualizações sejam de uma fonte conhecida.
- Elas fornecem um nível básico de segurança para acesso à rede. As ACLs podem permitir que um host acesse uma parte da rede e impedir que outro host acesse a mesma área. Por exemplo, o acesso à rede de Recursos Humanos poderá ser restrito a usuários autorizados.
- Elas filtram o tráfego com base no tipo de tráfego. Por exemplo, uma ACL pode permitir tráfego de correio eletrônico, mas bloquear todo o tráfego de Telnet.
- Elas examinam hosts para permitir ou negar acesso aos serviços de rede. As ACLs podem permitir ou negar a um usuário o acesso a tipos de arquivo, como FTP ou HTTP.

Além da permissão ou negação de tráfego, as ACLs podem ser usadas selecionando tipos de tráfego que serão analisados, enviados ou processados de outras formas. Por exemplo, as ACLs podem ser usadas para classificar o tráfego para ativar o processamento de prioridade. Esse recurso é semelhante a ter um ingresso VIP em um show ou em evento esportivo. O ingresso VIP fornece aos convidados selecionados os privilégios não oferecidos aos portadores de bilhetes de admissão geral, como a entrada prioritária ou possibilidade de entrar em uma área restrita.

A figura mostra uma topologia de amostra com ACLs aplicadas aos roteadores R1, R2 e R3.![[Pasted image 20250121184848.png]]

### ACLs - Recursos importantes

Dois tipos de ACLs Cisco IPv4 são padrão e estendidos. As ACLs padrão podem ser usadas para permitir ou negar tráfego somente dos endereços IPv4 origem. O destino do pacote e as portas envolvidas não são avaliados.

As ACLs estendidas filtram pacotes IPv4 com base em vários atributos que incluem:

- Tipo de protocolo
- Endereço IPv4 origem
- Endereço IPv4 destino
- Portas TCP ou UDP origem
- Portas TCP ou UDP destino
- Informações opcionais do tipo de protocolo para o melhor controle

As ACLs padrão e estendidas podem ser criadas usando-se um número ou um nome para identificar a ACL e sua lista de instruções.

Usar ACLs numeradas é um método eficaz para determinar o tipo de ACL em redes pequenas com tráfego definido de forma mais homogênea. No entanto, um número não fornece informações sobre o propósito da ACL. Portanto, um nome pode ser usado para identificar uma ACL da Cisco.

Ao configurar o registro de ACL, uma mensagem ACL pode ser gerada e registrada quando o tráfego atende aos critérios de permissão ou negação definidos na ACL.

As ACLs Cisco também podem ser configuradas para permitir apenas tráfego TCP que tenha um conjunto de bits ACK ou RST, de modo que apenas o tráfego de uma sessão TCP estabelecida seja permitido. Isso pode ser usado para negar qualquer tráfego TCP de fora da rede que está tentando estabelecer uma nova sessão TCP.

### SNMP

O protocolo SNMP (Simple Network Management Protocol) permite que os administradores gerenciem dispositivos finais como servidores, estações de trabalho, roteadores, switches e dispositivos de segurança em uma rede IP. Permite que os administradores de rede monitorem o desempenho da rede, encontrem e resolvam os problemas da rede e planejem o crescimento da rede.

O SNMP é um protocolo da camada de aplicação que fornece um formato de mensagem para a comunicação entre gerenciadores e agentes.

Como mostrado na figura, o sistema SNMP consiste em dois elementos.

- Gerenciador SNMP que executa o software de gerenciamento SNMP.
- Agentes SNMP que são os nós que estão sendo monitorados e gerenciados.

O Management Information Base (MIB) é um banco de dados dos agentes que armazena dados e estatísticas operacionais sobre o dispositivo.

Para configurar o SNMP em um dispositivo de rede, primeiramente é necessário definir a relação entre o gerenciador e o agente.

O gerenciador de SNMP faz parte de um sistema de gerenciamento de rede (NMS). O gerenciador de SNMP executa o software de gerenciamento de SNMP. Conforme mostrado na figura, o gerente SNMP pode coletar informações de um agente SNMP usando a ação "get" e pode alterar as configurações em um agente usando a ação "set". Além disso, os agentes SNMP podem encaminhar informações diretamente para um gerenciador de rede usando “traps”.![[Pasted image 20250121191039.png]]

### NetFlow

NetFlow é uma tecnologia CISCO IOS que fornece estatísticas em pacotes que passam por meio de um switch multicamadas ou de um roteador da Cisco. Enquanto o SNMP tenta fornecer uma ampla gama de recursos e opções de gerenciamento de rede, o NetFlow está focado em fornecer estatísticas sobre pacotes IP que fluem através de dispositivos de rede.

O NetFlow fornece dados para permitir monitoramento de rede e segurança, planejamento de rede, análise de tráfego para incluir identificação de gargalos de rede e contabilidade IP para fins de faturamento. Por exemplo, na figura, o PC 1 se conecta ao PC 2 usando um aplicativo como HTTPS.
![[Pasted image 20250121191433.png]]

O NetFlow pode monitorar essa conexão de aplicativo, rastreando contagens de bytes e pacotes para esse fluxo de aplicativo individual. Em seguida, envia as estatísticas para um servidor externo chamado coletor NetFlow.

A tecnologia NetFlow tem visto várias gerações que oferecem mais sofisticação na definição de fluxos de tráfego, mas fluxos “NetFlow original” diferenciados usando uma combinação de sete campos. Caso um desses campos varie em valor de outro pacote, os pacotes podem ser determinados com segurança como sendo de fluxos diferentes:

- Endereço IP de origem
- Endereço IP de destino
- Número da porta de origem
- Número da porta de destino
- Tipo de protocolo da camada 3
- Marcação de tipo de serviço (ToS)
- Interface lógica de entrada

Os quatro primeiros campos que o NetFlow usa para identificar um fluxo devem ser familiares. Os endereços IP de origem e destino, além das portas de origem e destino, identificam a conexão entre o aplicativo de origem e de destino. O tipo de protocolo da Camada 3 identifica o tipo de cabeçalho que segue o cabeçalho IP (geralmente TCP ou UDP, mas outras opções incluem ICMP). O byte ToS no cabeçalho IPv4 contém informações sobre como os dispositivos devem aplicar regras de qualidade de serviço (QoS) aos pacotes nesse fluxo.

### Espelhamento de portas

Um analisador de pacotes (também conhecido como sniffer de pacotes ou sniffer de tráfego) é normalmente um software que captura pacotes que entram e saem da placa de interface de rede (NIC). Nem sempre é possível ou desejável ter o analisador de pacotes no dispositivo que está sendo monitorado. Às vezes, é melhor em uma estação separada designada para capturar os pacotes.

Como os switches de rede podem isolar o tráfego, os sniffers de tráfego ou outros monitores de rede, como IDS, não podem acessar todo o tráfego em um segmento de rede. O espelhamento de portas é um recurso que permite que um switch faça cópias duplicadas do tráfego que passa por um switch e, em seguida, enviá-lo para fora uma porta com um monitor de rede conectado. O tráfego original é encaminhado da maneira usual. Um exemplo de espelhamento de porta é ilustrado na figura.
![[Pasted image 20250121191838.png]]

### Servidores Syslog

Quando determinados eventos ocorrem em uma rede, os dispositivos de rede têm mecanismos confiáveis para notificar o administrador com mensagens de sistema detalhadas. Essas mensagens podem não ser críticas ou podem ser significativas. Os administradores de rede têm uma variedade de opções de armazenamento, interpretação, exibição dessas mensagens e para serem alertados sobre as mensagens que podem ter maior impacto na infraestrutura de rede.

O método mais comum de acessar mensagens do sistema é usar um protocolo chamado syslog.

Muitos dispositivos de rede são compatíveis com syslog, incluindo: roteadores, switches, servidores de aplicativos, firewalls e outros dispositivos de rede. O protocolo syslog permite que os dispositivos de rede enviem suas mensagens de sistema pela rede para os servidores syslog, conforme mostrado na figura.![[Pasted image 20250121191913.png]]

O serviço de logging de syslog oferece três funções principais:

- A capacidade de coletar informações de registro para monitorar e solucionar problemas
- A capacidade de selecionar o tipo de informações de registro que são capturadas
- A capacidade de especificar o destino das mensagens syslog capturadas

### NTP

É importante sincronizar a hora em todos os dispositivos da rede porque todos os aspectos de gerenciamento, proteção, solução de problemas e planejamento de redes exigem um registro de data e hora preciso e consistente. Quando a hora não está sincronizada entre os dispositivos, será impossível determinar a ordem dos eventos que ocorreram em diferentes partes da rede.

Normalmente, as configurações de data e hora em um dispositivo de rede podem ser definidas usando um destes dois métodos:

- Configuração manual de data e hora
- Configurando o Network Time Protocol (NTP)

Conforme a rede cresce, torna-se cada vez mais difícil garantir que todos os dispositivos da infraestrutura operem com horário sincronizado. Mesmo em um ambiente de rede menor, o método manual não é o ideal. Se um dispositivo for reinicializado, como ele obterá uma data e um carimbo de hora precisos?

A melhor solução é configurar o NTP na rede. Esse protocolo permite que os roteadores na rede sincronizem as configurações de hora com um servidor NTP. Um grupo de clientes NTP que obtém informações de data e hora de uma única fonte tem configurações de hora mais consistentes. Quando o NTP é implementado na rede, ele pode ser configurado para sincronizar com um relógio mestre privado ou pode ser sincronizado com um servidor NTP disponível publicamente na Internet.

As redes NTP usam um sistema hierárquico de fontes de horário. Cada nível desse sistema hierárquico é denominado stratum. O nível do stratum é definido como o número de contagens de saltos da fonte oficial. O horário sincronizado é distribuído através da rede usando o NTP. A figura exibe uma amostra de uma rede NTP.![[Pasted image 20250121192011.png]]
Os servidores NTP são organizados em três níveis conhecidos como estratos:

- **Estrato 0** - uma rede NTP obtém a hora de fontes de hora oficiais. Essas fontes, também conhecidas como dispositivos de stratum 0, são dispositivos de pontualidade de alta precisão, com pouco ou nenhum atraso associado a eles.
- **Estrato 1** - Os dispositivos do estrato 1 estão diretamente conectados às fontes de tempo autorizadas. Eles atuam como o principal padrão de horário da rede.
- **Estrato 2** e estratos inferiores - Os servidores estrato 2 são conectados aos dispositivos estrato 1 por meio de conexões de rede. Os dispositivos do stratum 2, como os clientes NTP, sincronizam a hora usando os pacotes NTP dos servidores do stratum 1. Eles também podem atuar como servidores dos dispositivos do stratum 3.

Números menores de stratum indicam que o servidor está mais próximo da fonte de horário autorizada, se comparados aos números de strati maiores. Quanto maior o número do stratum, mais baixo seu nível. A valor máximo da contagem de saltos é 15. O Stratum 16, o nível mais baixo de stratum, indica que um dispositivo não está sincronizado. Servidores de horário no mesmo nível de stratum podem ser configurados para agir como pares com outros servidores de horário no mesmo nível de stratum, para finalidades de backup ou verificação da hora.

### Servidores AAA

A tabela lista as três funções de segurança independentes fornecidas pela estrutura arquitetônica AAA.![[Pasted image 20250121192158.png]]

Terminal Access Controller Access-Control System Plus (TACACS) e Remote Authentication Dial-In User Service (RADIUS) são protocolos de autenticação usados para se comunicar com servidores AAA. A seleção do TACACS+ ou RADIUS depende das necessidades da empresa.

Embora ambos os protocolos possam ser usados para comunicação entre um roteador e os servidores de AAA, o TACACS+ é considerado o protocolo mais seguro. Isto é porque todas as trocas de protocolo TACACS+ são criptografadas, enquanto o RADIUS criptografa apenas a senha do usuário. O RADIUS não criptografa nomes de usuário, informações de contabilidade ou qualquer outra informação transportada na mensagem RADIUS.

A tabela lista as diferenças entre os dois protocolos.![[Pasted image 20250121192310.png]]

### VPN

Uma VPN é uma rede privada criada em uma rede pública, geralmente a Internet, conforme mostrado na figura.![[Pasted image 20250121192410.png]]

Em vez de usar uma conexão física dedicada, uma VPN usa conexões virtuais que são roteadas pela Internet da organização para o site remoto. As primeiras VPNs eram túneis IP restritos que não incluíam autenticação ou criptografia dos dados. Por exemplo, Generic Routing Encapsulation (GRE) é um protocolo de encapsulamento desenvolvido pela Cisco que pode encapsular uma ampla variedade de tipos de pacote de protocolo de camada de rede dentro de túneis IP. Isso cria um link ponto-a-ponto virtual com roteadores Cisco em pontos remotos sobre uma rede interconectada IP.

Uma VPN é virtual, pois carrega informações dentro de uma rede privada, mas essas informações são realmente transportadas por uma rede pública. Uma VPN é privada, pois o tráfego é criptografado para manter os dados confidenciais enquanto são transportados pela rede pública.

A VPN é um ambiente de comunicações no qual o acesso é controlado rigorosamente para permitir conexões de mesmo nível em uma comunidade com interesses definidos. A confidencialidade é alcançada criptografando o tráfego dentro da VPN. Hoje, uma implementação segura de VPN com criptografia é o que geralmente é equiparado ao conceito de rede virtual privada.

No sentido mais simples, uma VPN conecta dois endpoints, como um escritório remoto a um escritório central, através de uma rede pública, para formar uma conexão lógica. As conexões lógicas podem ser feitas na Camada 2 ou na Camada 3. Exemplos comuns de VPNs de Camada 3 são GRE, MPLS (Multiprotocol Label Switching) e IPsec. As VPNs de camada 3 podem ser conexões de site ponto a ponto, como GRE e IPsec, ou podem estabelecer qualquer conectividade para muitos sites usando MPLS.

O IPsec é um conjunto de protocolos desenvolvido com o apoio do IETF para obter serviços seguros em redes IP comutadas por pacotes.

Os serviços de IPsec permitem a autenticação, integridade, controle de acesso e confidencialidade. Com o IPsec, as informações trocadas entre sites remotos podem ser criptografadas e verificadas. As VPNs são normalmente implantadas em uma topologia site a site para conectar sites centrais com locais remotos com segurança. Eles também são implantados em uma topologia de acesso remoto para fornecer acesso remoto seguro a usuários externos que viajam ou trabalham de casa. As VPNs de acesso remoto e site-to-site podem ser implantadas usando IPsec.

