# Manuseio de evidências e atribuição de ataque

### Perícia Digital

Agora que investigou e identificou alertas válidos, o que faz com as provas? O analista de segurança cibernética irá inevitavelmente descobrir evidências de atividade criminosa. A fim de proteger a organização e prevenir o cibercrime, é necessário identificar os atores da ameaça, denunciá-los às autoridades competentes e fornecer provas para apoiar a acusação. Os analistas de segurança cibernética de nível 1 geralmente são os primeiros a descobrir delitos. Os analistas de segurança cibernética devem saber como lidar adequadamente com evidências e atribuí-la a atores ameaçadores.

A perícia digital é a recuperação e investigação de informações encontradas em dispositivos digitais no que diz respeito a atividades criminosas. Indicadores de comprometimento são a evidência de que ocorreu um incidente de segurança cibernética. Essas informações podem ser dados em dispositivos de armazenamento, na memória volátil do computador ou vestígios de cibercrime que são preservados em dados de rede, como pcaps e logs. É essencial que todos os indicadores de compromisso sejam preservados para análise futura e atribuição de ataques.

A atividade cibernética pode ser amplamente caracterizada como originária de dentro ou fora da organização. Investigações privadas estão preocupadas com indivíduos dentro da organização. Esses indivíduos poderiam simplesmente estar se comportando de maneiras que violam os acordos do usuário ou outras condutas não criminais. Quando indivíduos são suspeitos de envolvimento em atividades criminosas envolvendo roubo ou destruição de propriedade intelectual, uma organização pode optar por envolver autoridades policiais, caso em que a investigação se torna pública. Os usuários internos também poderiam ter usado a rede da organização para realizar outras atividades criminosas que não estão relacionadas à missão organizacional, mas estão em violação de vários estatutos legais. Neste caso, funcionários públicos realizarão a investigação.

Quando um invasor externo explora uma rede e rouba ou alterou dados, as evidências precisam ser coletadas para documentar o escopo da exploração. Vários órgãos reguladores especificam uma série de ações que uma organização deve tomar quando vários tipos de dados foram comprometidos. Os resultados da investigação forense podem ajudar a identificar as ações que precisam ser tomadas.

Por exemplo, de acordo com os regulamentos HIPAA dos EUA, se ocorrer uma violação de dados que envolva informações do paciente, a notificação da violação deve ser feita aos indivíduos afetados. Se a violação envolver mais de 500 pessoas em um estado ou jurisdição, a mídia, bem como os indivíduos afetados, devem ser notificados. A investigação forense digital deve ser usada para determinar quais indivíduos foram afetados e para certificar o número de indivíduos afetados para que a notificação apropriada possa ser feita em conformidade com os regulamentos HIPAA.

É possível que a própria organização possa ser objeto de uma investigação. Os analistas de segurança cibernética podem encontrar-se em contato direto com evidências forenses digitais que detalham a conduta dos membros da organização. Os analistas devem conhecer os requisitos relativos à preservação e tratamento de tais evidências. Se a intenção de destruir provas for estabelecida, poderá resultar em penalidades criminais para a organização e até mesmo para o analista de segurança cibernética.
### O Processo Forense Digital

É importante que uma organização desenvolva processos e procedimentos bem documentados para análise forense digital. A conformidade regulamentar pode exigir esta documentação, e essa documentação pode ser inspecionada pelas autoridades em caso de investigação pública.

Publicação Especial NIST 800-86 _ Guia de integração de técnicas forenses para resposta a incidentes _ é um recurso valioso para organizações que exigem orientação no desenvolvimento de planos digitais forenses. Por exemplo, recomenda que a perícia seja realizada usando o processo de quatro fases.

A seguir, descreve as quatro fases básicas do processo forense de evidências digitais.

![[Pasted image 20250207233856.png]]

**Coleta**
Esta é a identificação de potenciais fontes de dados forenses e aquisição, manuseio e armazenamento desses dados. Este estágio é crítico porque deve-se ter especial cuidado para não danificar, perder ou omitir dados importantes.

**Análise**
Isto implica avaliar e extrair informações relevantes dos dados recolhidos. Isso pode envolver descompactação ou descriptografia dos dados. As informações irrelevantes para a investigação podem ter de ser removidas. Identificar evidências reais em grandes coleções de dados pode ser muito difícil e demorado.

**Análise**
Isto implica tirar conclusões dos dados. Recursos relevantes, como pessoas, lugares, horários, eventos, etc., devem ser documentados. Esta etapa também pode envolver a correlação de dados de várias fontes.

**Relatórios**
Isso implica preparar e apresentar informações resultantes da análise. Os relatórios devem ser imparciais e devem ser apresentadas explicações alternativas, se for caso disso. Limitações da análise e problemas encontrados devem ser incluídos. Devem também ser feitas sugestões para uma investigação mais aprofundada e para os próximos passos.
### Tipos de Evidência

Em processos judiciais, as provas são geralmente classificadas como diretas ou indiretas. Provas diretas são provas que estavam indiscutivelmente na posse do acusado, ou são testemunhas oculares de alguém que observou diretamente o comportamento criminoso.

As provas são ainda classificadas como:

- **Melhor evidência** - Esta é evidência que está em seu estado original. Essas evidências podem ser dispositivos de armazenamento usados por um acusado, ou arquivos de arquivos que podem ser comprovados como inalterados.
- **Evidência corroborante** - Esta é uma evidência que suporta uma afirmação que é desenvolvida a partir da melhor evidência.
- **Evidência indireta** - Esta é evidência que, em combinação com outros fatos, estabelece uma hipótese. Isso também é conhecido como evidência circunstancial. Por exemplo, a evidência de que um indivíduo cometeu crimes semelhantes pode apoiar a afirmação de que a pessoa cometeu o crime de que é acusado.
### Ordem de coleta de evidências

IETF RFC 3227 fornece diretrizes para a coleta de evidências digitais. Descreve uma ordem para a recolha de provas digitais com base na volatilidade dos dados. Os dados armazenados na RAM são os mais voláteis, e serão perdidos quando o dispositivo for desligado. Além disso, dados importantes na memória volátil podem ser substituídos por processos de rotina da máquina. Portanto, a coleta de evidências digitais deve começar com a evidência mais volátil e avançar para a menos volátil, como mostrado na figura.![[Pasted image 20250207234349.png]]

Um exemplo da ordem de coleta de evidências mais volátil a menos volátil é o seguinte:

1. Registros de memória, caches
2. Tabela de roteamento, cache ARP, tabela de processo, estatísticas de kernel, RAM
3. Sistemas de arquivos temporários
4. Meios não voláteis, fixos e removíveis
5. Dados de registro e monitoramento remotos
6. Interconexões físicas e topologias
7. Mídia de arquivamento, fita ou outros backups

Detalhes dos sistemas a partir dos quais as provas foram recolhidas, incluindo quem tem acesso a esses sistemas e a que nível de permissões devem ser registadas. Essas informações devem incluir configurações de hardware e software para os sistemas a partir dos quais os dados foram obtidos.
### Cadeia de Custódia

Embora possam ter sido recolhidas provas de fontes que apoiam a atribuição a um indivíduo acusado, pode-se argumentar que a evidência poderia ter sido alterada ou fabricada após a coleta. Para contrariar este argumento, deve ser definida e seguida uma rigorosa cadeia de custódia.

A cadeia de custódia envolve a coleta, manuseio e armazenamento seguro de evidências. Devem ser conservados registos pormenorizados dos seguintes elementos:

- Quem descobriu e recolheu as provas?
- Todos os detalhes sobre o tratamento de evidências, incluindo horas, locais e pessoal envolvido.
- Quem tem a principal responsabilidade pelas provas, quando a responsabilidade foi atribuída e quando a custódia mudou?
- Quem tem acesso físico à evidência enquanto foi armazenada? O acesso deve ser limitado apenas ao pessoal mais essencial.
### Integridade e preservação dos dados

Ao coletar dados, é importante que eles sejam preservados em sua condição original. O carimbo de data/hora (timestamp) dos arquivos deve ser preservado. Por esta razão, a prova original deve ser copiada e a análise deve ser realizada apenas em cópias do original. Isto é para evitar perda acidental ou alteração da evidência. Como os carimbos de data/hora podem fazer parte da evidência, abrir arquivos da mídia original deve ser evitado.

O processo utilizado para criar cópias dos elementos de prova utilizados no inquérito deve ser registado. Sempre que possível, as cópias devem ser cópias diretas em nível de bits dos volumes de armazenamento originais. Deve ser possível comparar a imagem do disco arquivado e a imagem do disco investigada para identificar se o conteúdo do disco investigado foi adulterado. Por esta razão, é importante arquivar e proteger o disco original para mantê-lo em sua condição original, sem adulteração.

Memória volátil pode conter evidências forenses, então ferramentas especiais devem ser usadas para preservar essa evidência antes que o dispositivo seja desligado e as evidências sejam perdidas. Os usuários não devem desconectar, desconectar da tomada ou desligar máquinas infectadas, a menos que explicitamente instruído pelo pessoal de segurança.

Seguir estes processos garantirá que qualquer evidência de delito será preservada, e quaisquer indicadores de comprometimento podem ser identificados.
### Atribuição de Ataque

Depois que a extensão do ataque cibernético foi avaliada e as evidências coletadas e preservadas, a resposta ao incidente pode passar para identificar a origem do ataque. Como sabemos, existe uma ampla gama de atores de ameaças, que vão desde indivíduos descontentes, hackers, cibercriminosos e gangues criminosas, ou estados-nação. Alguns criminosos agem de dentro da rede, enquanto outros podem estar do outro lado do mundo. A sofisticação do crime cibernético também varia. Os Estados-nação podem empregar grandes grupos de indivíduos altamente treinados para realizar um ataque e esconder seus rastros, enquanto outros atores ameaçadores podem abertamente se gabar de suas atividades criminosas.

Atribuição de ameaças refere-se ao ato de determinar o indivíduo, a organização ou a nação responsável por um incidente de invasão ou ataque bem-sucedido.

A identificação dos intervenientes responsáveis pela ameaça deve ocorrer através da investigação sistemática e baseada em princípios dos elementos de prova. Embora possa ser útil também especular quanto à identidade dos atores da ameaça, identificando potenciais motivações para um incidente, é importante não deixar que isso vise a investigação. Por exemplo, atribuir um ataque a um concorrente comercial pode levar a investigação longe da possibilidade de uma gangue criminosa ou um Estado-nação ter sido responsável.

Em uma investigação baseada em evidências, a equipe de resposta a incidentes correlaciona Táticas, Técnicas e Procedimentos (TTP) que foram usados no incidente com outras explorações conhecidas. Os cibercriminosos, assim como outros criminosos, têm traços específicos que são comuns à maioria dos seus crimes. Fontes de inteligência de ameaças podem ajudar a mapear o TTP identificado por uma investigação para fontes conhecidas de ataques semelhantes. No entanto, isso destaca um problema com a atribuição de ameaças. Evidência de cibercrime raramente é evidência direta. Identificar semelhanças entre TTP para atores conhecidos e desconhecidos da ameaça é evidência circunstancial.

Alguns aspectos de uma ameaça que podem ajudar na atribuição são a localização de hosts ou domínios de origem, recursos do código usado em malware, as ferramentas usadas e outras técnicas. Por vezes, a nível da segurança nacional, as ameaças não podem ser atribuídas abertamente, porque isso exporia métodos e capacidades que precisam de ser protegidos.

Para ameaças internas, o gerenciamento de ativos desempenha um papel importante. Descobrir os dispositivos a partir dos quais um ataque foi lançado pode levar diretamente ao ator da ameaça. Endereços IP, endereços MAC e logs DHCP podem ajudar a rastrear os endereços usados no ataque de volta para um dispositivo específico. Os logs AAA são muito úteis a esse respeito, pois rastreiam quem acessou quais recursos de rede a que horas.
### A estrutura MITRE ATT&CK

Uma maneira de atribuir um ataque é modelar o comportamento do ator de ameaça. O MITRE Táticas e técnicas adversas & Estrutura de Conhecimento Comum (ATT&CK) permite detectar táticas, técnicas e procedimentos do atacante (TTP) como parte da defesa contra ameaças e atribuição de ataques. Isso é feito mapeando os passos em um ataque para uma matriz de táticas generalizadas e descrevendo as técnicas que são usadas em cada tática. As táticas consistem nos objetivos técnicos que um atacante deve realizar para executar um ataque e as técnicas são o meio pelo qual as táticas são realizadas. Por último, os procedimentos são as acções específicas tomadas pelos intervenientes ameaçadores nas técnicas identificadas. Os procedimentos são o uso documentado de técnicas no mundo real por atores ameaçadores.

O MITRE ATT&CK Framework é uma base de conhecimento global do comportamento do ator de ameaças. Baseia-se na observação e análise de explorações do mundo real com o objetivo de descrever o comportamento do atacante, não o ataque em si. Ele foi projetado para permitir o compartilhamento automatizado de informações, definindo estruturas de dados para o intercâmbio de informações entre sua comunidade de usuários e MITRE.

A figura mostra uma análise de uma exploração de ransomware a partir da excelente sandbox online ANY.RUN. As colunas mostram as táticas de matriz de ataque corporativo, com as técnicas usadas pelo malware organizadas sob as colunas. Clicar na técnica, em seguida, lista detalhes dos procedimentos que são usados pela instância de malware específica com uma definição, explicação e exemplos da técnica.

**Nota**: Faça uma pesquisa na Internet no MITRE ATT&CK para saber mais sobre a ferramenta.![[Pasted image 20250207234710.png]]
# A Cyber Kill Chain

### Etapas da Cyber Kill Chain

A Cyber Kill Chain foi desenvolvida pela Lockheed Martin para identificar e prevenir intrusões cibernéticas. Existem sete etapas para o Cyber Kill Chain. O foco nessas etapas ajuda os analistas a entender as técnicas, as ferramentas e os procedimentos dos atores de ameaças. Ao responder a um incidente de segurança, o objetivo é detectar e parar o ataque o mais cedo possível na progressão da cadeia de eliminação. Quanto mais cedo o ataque for interrompido; menos dano é feito e menos o atacante aprende sobre a rede de destino.

A Cyber Kill Chain especifica o que um atacante deve completar para atingir seu objetivo. Os passos na Cyber Kill Chain são mostrados na figura.

Se o atacante for parado em qualquer fase, a cadeia de ataque é quebrada. Quebrar a corrente significa que o defensor frustrou com sucesso a intrusão do ator da ameaça. Os atores da ameaça só serão bem-sucedidos se concluírem a Etapa 7.

**Nota**: Ator ameaça é o termo usado ao longo deste curso para se referir à parte que instigou o ataque. No entanto, Lockheed Martin usa o termo “adversário” em sua descrição da Cyber Kill Chain. Portanto, os termos adversário e ator ameaça são usados de forma intercambiável neste tópico.![[Pasted image 20250208131116.png]]
### Reconhecimento

Reconhecimento é quando o ator ameaça realiza pesquisas, coleta inteligência e seleciona alvos. Isso informará o ator da ameaça se o ataque vale a pena executar. Qualquer informação pública pode ajudar a determinar o que, onde e como o ataque a ser executado. Há muitas informações publicamente disponíveis, especialmente para organizações maiores, incluindo artigos de notícias, sites, procedimentos de conferência e dispositivos de rede voltados para o público. Quantidades crescentes de informações sobre os funcionários estão disponíveis por meio de redes sociais.

O agente da ameaça escolherá alvos que foram negligenciados ou desprotegidos porque terão uma maior probabilidade de serem penetrados e comprometidos. Todas as informações obtidas pelo agente da ameaça são revisadas para determinar sua importância e se revelam possíveis vias adicionais de ataque.

A tabela resume algumas das táticas e defesas usadas durante a etapa de reconhecimento.*![[Pasted image 20250208131217.png]]
### Armamento

O objetivo desta etapa é usar as informações do reconhecimento para desenvolver uma arma contra sistemas específicos ou indivíduos na organização. Para desenvolver essa arma, o designer usará as vulnerabilidades dos ativos que foram descobertos e os construirá em uma ferramenta que pode ser implantada. Depois que a ferramenta foi usada, espera-se que o ator da ameaça tenha alcançado seu objetivo de obter acesso ao sistema ou rede de destino, degradando a integridade de um alvo ou toda a rede. O agente da ameaça examinará ainda mais a segurança da rede e dos ativos para expor fraquezas adicionais, obter controle sobre outros ativos ou implantar ataques adicionais.

Não é difícil escolher uma arma para o ataque. O agente da ameaça precisa analisar quais ataques estão disponíveis para as vulnerabilidades que eles descobriram. Existem muitos ataques que já foram criados e testados em geral. Um problema é que, como esses ataques são tão conhecidos, eles são provavelmente também conhecidos pelos defensores. Muitas vezes, é mais eficaz usar um ataque de dia zero para evitar métodos de detecção. Um ataque de dia zero usa uma arma que é desconhecida para os defensores e sistemas de segurança de rede. O ator ameaça pode querer desenvolver sua própria arma que é especificamente projetada para evitar a detecção, usando as informações sobre a rede e os sistemas que eles aprenderam. Os atacantes aprenderam a criar inúmeras variantes de seus ataques para evitar as defesas da rede.

A tabela resume algumas das táticas e defesas usadas durante a etapa de armamento.![[Pasted image 20250208131328.png]]
### Entrega

Durante esta etapa, a arma é transmitida ao alvo usando um vetor de entrega. Isso pode ser através do uso de um site, mídia USB removível ou um anexo de e-mail. Se a arma não for entregue, o ataque não terá sucesso. O agente da ameaça usará muitos métodos diferentes para aumentar as chances de entregar a carga útil, como criptografar comunicações, fazer com que o código pareça legítimo ou ofuscar o código. Os sensores de segurança são tão avançados que podem detectar o código como malicioso, a menos que ele seja alterado para evitar a detecção. O código pode ser alterado para parecer inocente, mas ainda assim executar as ações necessárias, mesmo que possa demorar mais tempo para ser executado.

A tabela resume algumas das táticas e defesas usadas durante a etapa de entrega.![[Pasted image 20250208131402.png]]
### Exploração

Depois que a arma foi entregue, o ator ameaça a usa para quebrar a vulnerabilidade e ganhar o controle do alvo. Os destinos de exploração mais comuns são aplicativos, vulnerabilidades do sistema operacional e usuários. O atacante deve usar uma exploração que ganhe o efeito que deseja. Isso é muito importante porque se a exploração errada for conduzida, obviamente o ataque não funcionará, mas efeitos colaterais não intencionais, como um DoS ou várias reinicializações de sistema, causarão atenção indevida que poderia facilmente informar os analistas de segurança cibernética sobre o ataque e as intenções do ator da ameaça.

A tabela resume algumas das táticas e defesas usadas durante a etapa de exploração.![[Pasted image 20250208131433.png]]
### Instalação

Esta etapa é onde o ator ameaça estabelece um backdoor para o sistema para permitir o acesso contínuo ao alvo. Para preservar esse backdoor, é importante que o acesso remoto não alerte analistas ou usuários de segurança cibernética. O método de acesso deve sobreviver através de verificações antimalware e reinicialização do computador para ser eficaz. Esse acesso persistente também pode permitir comunicações automatizadas, especialmente eficazes quando vários canais de comunicação são necessários ao comandar uma botnet.

A tabela resume algumas das táticas e defesas usadas durante a etapa de instalação.![[Pasted image 20250208131504.png]]
### Comando e controle

Nesta etapa, o objetivo é estabelecer comando e controle (CNC ou C2) com o sistema de destino. Os hosts comprometidos geralmente se sinalizam da rede para um controlador na Internet. Isso ocorre porque a maioria dos malwares requer interação manual para exfiltrar dados da rede. Os canais CNC são usados pelo ator de ameaças para emitir comandos para o software que eles instalaram no destino. O analista de segurança cibernética deve ser capaz de detectar comunicações CNC para descobrir o host comprometido. Isso pode ser na forma de tráfego não autorizado de Internet Relay Chat (IRC) ou tráfego excessivo para domínios suspeitos.

A tabela resume algumas das táticas e defesas usadas durante a etapa de comando e controle.![[Pasted image 20250208131545.png]]
### Ações sobre os objetivos

O passo final da Cyber Kill Chain descreve o ator ameaçador alcançar seu objetivo original. Isso pode ser roubo de dados, realizar um ataque DDoS ou usar a rede comprometida para criar e enviar spam ou mina Bitcoin. Neste ponto, o ator ameaça está profundamente enraizado nos sistemas da organização, escondendo seus movimentos e cobrindo seus rastros. É extremamente difícil remover o agente de ameaça da rede.

A tabela resume algumas das táticas e defesas usadas durante as ações na etapa objetivos.![[Pasted image 20250208131627.png]]
# O modelo Diamond de análise de intrusão

### Visão geral do modelo Diamond

O Modelo Diamond de Análise de Intrusão é composto por quatro partes, como mostrado na figura. O modelo representa um incidente ou evento de segurança. No Modelo Diamond, um evento é uma atividade limitada ao tempo que é restrita a uma etapa específica em que um adversário usa uma capacidade sobre a infraestrutura para atacar uma vítima para alcançar um resultado específico.

Os quatro principais recursos de um evento de intrusão são adversário, capacidade, infraestrutura e vítima:

- **Adversário** - Estas são as partes responsáveis pela intrusão.
- **Capacidade** - Esta é uma ferramenta ou técnica que o adversário usa para atacar a vítima.
- **Infraestrutura** - Este é o caminho ou caminhos de rede que os adversários usam para estabelecer e manter o comando e o controle sobre suas capacidades.
- **Vítima** - Este é o alvo do ataque. No entanto, uma vítima pode ser o alvo inicialmente e, em seguida, usada como parte da infra-estrutura para lançar outros ataques.

O adversário usa recursos sobre infraestrutura para atacar a vítima. O modelo pode ser interpretado como dizendo: “O adversário usa a infraestrutura para se conectar à vítima. O adversário desenvolve capacidade de explorar a vítima.” Por exemplo, um recurso como malware pode ser usado na infraestrutura de e-mail por um adversário para explorar uma vítima.

Os meta-recursos expandem o modelo ligeiramente para incluir os seguintes elementos importantes:

- **Timestamp** - Isso indica a hora de início e parada de um evento e é parte integrante do agrupamento de atividades mal-intencionadas.
- **Fase** - Isso é análogo às etapas da Cyber Kill Chain; atividade maliciosa inclui duas ou mais etapas executadas sucessivamente para alcançar o resultado desejado.
- **Resultado** - Isso delineia o que o adversário ganhou com o evento. Os resultados podem ser documentados como um ou mais dos seguintes: confidencialidade comprometida, integridade comprometida e disponibilidade comprometida.
- **Direção** - Indica a direção do evento em todo o Modelo Diamond. Elas incluem infraestrutura adversária, infraestrutura para vítima, vítima para infraestrutura e infraestrutura para adversário.
- **Metodologia** - Isso é usado para classificar o tipo geral de evento, como varredura de portas, phishing, ataque de entrega de conteúdo, syn flood, etc.
- ***Recursos** - Estes são um ou mais recursos externos usados pelo adversário para o evento de intrusão, como software, conhecimento do adversário, informações (por exemplo, nome de usuário/senhas) e ativos para realizar o ataque (hardware, fundos, instalações, acesso à rede).
### O Modelo Diamond
![[Pasted image 20250208132055.png]]
### Pivotando em todo o modelo Diamond

Como analista de segurança cibernética, você pode ser chamado a usar o Modelo Diamond de Análise de Intrusão para diagramar uma série de eventos de intrusão. O Modelo Diamond é ideal para ilustrar como o adversário giro de um evento para o outro.

Por exemplo, na figura um funcionário relata que seu computador está agindo de forma anormal. Uma verificação de host feita pelo técnico de segurança indica que o computador está infectado com malware. Uma análise do malware revela que o malware contém uma lista de nomes de domínio CNC. Estes nomes de domínio resolvem para uma lista de endereços IP. Esses endereços IP são então usados para identificar o adversário, bem como investigar registros para determinar se outras vítimas na organização estão usando o canal CNC.![[Pasted image 20250208132157.png]]
### O Modelo Diamond e a Cyber Kill Chain

Os adversários não operam em apenas um evento. Em vez disso, os eventos são encadeados em uma cadeia na qual cada evento deve ser concluído com êxito antes do próximo evento. Este segmento de eventos pode ser mapeado para a Cyber Kill Chain discutida anteriormente no capítulo.

O exemplo a seguir, mostrado na figura, ilustra o processo de ponta a ponta de um adversário à medida que eles atravessam verticalmente a Cyber Kill Chain, usam um host comprometido para girar horizontalmente para outra vítima e, em seguida, iniciar outro segmento de atividade:

1. Adversary realiza uma pesquisa na web para a empresa vítima Gadgets, Inc. recebendo como parte dos resultados o nome de domínio gadgets.com.

2. O adversário usa o domínio recém-descoberto gadets.com para uma nova pesquisa “administrador de rede gadget.com” e descobre postagens de fóruns de usuários que afirmam ser administradores de rede do gadget.com. Os perfis de usuário revelam seus endereços de e-mail.

3. O adversário envia e-mails de phishing com um cavalo de Tróia anexado aos administradores de rede do gadget.com.

4. Um administrador de rede (NA1) do gadget.com abre o anexo malicioso. Isso executa a exploração fechada, permitindo a execução de código adicional.

5. O host comprometido do NA1 envia uma mensagem HTTP Post para um endereço IP, registrando-a com um controlador CNC. O host comprometido do NA1 recebe uma resposta HTTP em troca.

6. É revelado pela engenharia reversa que o malware tem endereços IP adicionais configurados que atuam como um backup se o primeiro controlador não responder.

7. Através de uma mensagem de resposta CNC HTTP enviada para o host do NA1, o malware começa a agir como um proxy da web para novas conexões TCP.

8. Através de informações do proxy que está sendo executado no host da NA1, Adversary faz uma pesquisa na web para “pesquisa mais importante de sempre” e encontra Victima 2, Interessante Research Inc.
    
9. Adversary verifica a lista de contatos de e-mail da NA1 para qualquer contato da Interessante Research Inc. e descobre o contato para o Diretor de Pesquisa Interessante da Inc.
    
10. O Diretor de Pesquisa da Interessante Research Inc. recebe um e-mail spear-phish do endereço de e-mail da Gadget Inc. enviado do host da NA1 com a mesma carga útil observada no Evento 3.
    

O adversário agora tem duas vítimas comprometidas, das quais ataques adicionais podem ser lançados. Por exemplo, o adversário poderia explorar os contatos de e-mail do Diretor de Pesquisa para as vítimas potenciais adicionais. O adversário também pode configurar outro proxy para exfiltrar todos os arquivos do Diretor de Pesquisa.

**Nota**: Este exemplo é uma modificação do exemplo do Departamento de Defesa dos EUA na publicação “The Diamond Model of Intrusion Analysis”.
### Exemplos de tópicos de atividades
![[Pasted image 20250208132814.png]]
# Resposta a incidentes

### Estabelecimento de um recurso de resposta

A resposta a incidentes envolve os métodos, políticas e procedimentos usados por uma organização para responder a um ataque cibernético. Os objetivos da resposta a incidentes são limitar o impacto do ataque, avaliar os danos causados e implementar procedimentos de recuperação. Devido à perda potencial de propriedade e receita em larga escala que pode ser causada por ataques cibernéticos, é essencial que as organizações criem e mantenham planos detalhados de resposta a incidentes e designem pessoal responsável pela execução de todos os aspectos desse plano.

As recomendações do NIST (National Institute of Standards and Technology, Instituto Nacional de Padrões e Tecnologia) dos EUA para resposta a incidentes estão detalhadas em sua Publicação Especial 800-61, revisão 2, intitulada “Computer Security Incident Handling Guide”, que mostra a figura.

**Observação**: Embora este capítulo resume grande parte do conteúdo do padrão NIST 800-61r2, você deve estar familiarizado com toda a publicação, pois ela aborda quatro tópicos principais de exame para o exame Noções Básicas de Operações de Segurança Cibernética da Cisco.

O padrão NIST 800-61r2 fornece diretrizes para o tratamento de incidentes, especialmente para analisar dados relacionados a incidentes e determinar a resposta apropriada a cada incidente. As diretrizes podem ser seguidas independentemente de plataformas de hardware, sistemas operacionais, protocolos ou aplicativos específicos.

O primeiro passo para uma organização é estabelecer uma capacidade de resposta a incidentes de segurança de computador (CSIRC). O NIST recomenda a criação de políticas, planos e procedimentos para estabelecer e manter um CSIRC.

**Elementos de Política**

Uma política de resposta a incidentes detalha como os incidentes devem ser tratados com base na missão, tamanho e função da organização. A política deve ser revista regularmente, de modo a ajustá-la de modo a atingir os objetivos do roteiro que foi elaborado. Os elementos de política incluem o seguinte:

- Declaração de compromisso de gestão
- Finalidade e objetivos da política
- Âmbito de aplicação da política
- Definição de incidentes de segurança informática e termos conexos
- Estrutura organizacional e definição de funções, responsabilidades e níveis de autoridade
- Priorização de classificações de gravidade de incidentes
- Medidas de desempenho
- Formulários de comunicação e contato

**Elementos do Plano**

Um bom plano de resposta a incidentes ajuda a minimizar os danos causados por um incidente. Ele também ajuda a melhorar o programa geral de resposta a incidentes, ajustando-o de acordo com as lições aprendidas. Ele garantirá que cada parte envolvida na resposta ao incidente tenha uma compreensão clara não só do que estará fazendo, mas também do que outros estarão fazendo. Os elementos do plano são os seguintes:

- Missão
- Estratégias e objetivos
- Aprovação da alta administração
- Abordagem organizacional para a resposta
- Como a equipe de resposta a incidentes se comunicará com o resto da organização e com outras organizações
- Métricas para medir a capacidade de resposta a incidentes
- Como o programa se encaixa na organização geral

**Elementos de procedimento**

Os procedimentos que são seguidos durante uma resposta a incidentes devem seguir o plano de resposta a incidentes. Os elementos de procedimentos são os seguintes:

- Processos técnicos
- Uso de técnicas
- Preenchimento de formulários,
- Seguindo listas de verificação

Estes são procedimentos operacionais padrão (SOPs) típicos. Esses POPs devem ser detalhados para que a missão e os objetivos da organização estejam em mente quando esses procedimentos forem seguidos. Os SOPs minimizam os erros que podem ser causados por funcionários que estão sob estresse durante a participação no tratamento de incidentes. É importante compartilhar e praticar esses procedimentos, certificando-se de que eles são úteis, precisos e apropriados.
### Partes interessadas da Resposta

Outros grupos e indivíduos dentro da organização também podem estar envolvidos com o tratamento de incidentes. É importante assegurar que cooperarão antes de um incidente estar em curso. Sua experiência e habilidades podem ajudar a equipe de resposta a incidentes de segurança informática (CSIRT) a lidar com o incidente de forma rápida e correta. Estas são algumas das partes interessadas que podem estar envolvidas na entrega de um incidente de segurança:

- **Gestão** - Os gerentes criam as políticas que todos devem seguir. Eles também projetam o orçamento e são responsáveis pela equipe de todos os departamentos. A gerência deve coordenar a resposta ao incidente com outras partes interessadas e minimizar os danos de um incidente.
- **Garantia de informações** - Esse grupo pode precisar ser chamado para alterar coisas como regras de firewall durante alguns estágios de gerenciamento de incidentes, como contenção ou recuperação.
- **Suporte de TI** - Este é o grupo que trabalha com a tecnologia na organização e a entende mais. Como o suporte de TI tem uma compreensão mais profunda, é mais provável que eles executem a ação correta para minimizar a eficácia do ataque ou preservar as evidências adequadamente.
- **Departamento Jurídico** - É uma prática recomendada fazer com que o departamento jurídico revise as políticas, os planos e os procedimentos de incidentes para garantir que eles não violem quaisquer diretrizes locais ou federais. Além disso, se algum incidente tiver implicações legais, um perito jurídico terá de se envolver. Isso pode incluir acusação, coleta de evidências ou ações judiciais.
- **Assuntos Públicos e Relações com a Mídia** - Há momentos em que a mídia e o público podem precisar ser informados de um incidente, como quando suas informações pessoais foram comprometidas durante um incidente.
- **Recursos Humanos** - O departamento de recursos humanos pode precisar executar medidas disciplinares se ocorrer um incidente causado por um funcionário.
- **Planejadores de continuidade de negócios** - incidentes de segurança podem alterar a continuidade de negócios de uma organização. É importante que os responsáveis pelo planejamento de continuidade de negócios estejam cientes dos incidentes de segurança e do impacto que tiveram sobre a organização como um todo. Isto permitir-lhes-á fazer quaisquer alterações nos planos e nas avaliações de risco.
- **Segurança física e gerenciamento de instalações** - Quando um incidente de segurança ocorre devido a um ataque físico, como tailgating ou surf no ombro, essas equipes podem precisar ser informadas e envolvidas. É também da sua responsabilidade garantir instalações que contenham provas de uma investigação.

**A certificação do modelo de maturidade de segurança**

A estrutura de Certificação de Modelo de Maturidade de Segurança Cibernética (CMMC) foi criada para avaliar a capacidade das organizações que desempenham funções para o Departamento de Defesa dos EUA (DoD) para proteger a cadeia de suprimentos militar contra interrupções ou perdas devido a incidentes de segurança cibernética. Violações de segurança relacionadas às informações do DoD indicaram que os padrões do NIST não eram suficientes para atenuar o cenário de ameaças cada vez maior e em evolução, especialmente por parte dos atores do Estado-nação. Para que as empresas recebam contratos do DoD, essas empresas devem ser certificadas. A certificação consiste em cinco níveis, com diferentes níveis exigidos dependendo do grau de segurança exigido pelo projeto.

O CMMC especifica 17 domínios, cada um dos quais tem um número variável de recursos que estão associados a ele. A organização é classificada pelo nível de maturidade que foi alcançado para cada um dos domínios. Um dos domínios diz respeito à resposta a incidentes. Os recursos associados ao domínio de resposta a incidentes são os seguintes:

- Plano de resposta a incidentes
- Detectar e relatar eventos
- Desenvolver e implementar uma resposta a um incidente declarado
- Realizar revisões pós-incidentes
- Teste de resposta a incidentes

O CMMC certifica organizações por nível. Para a maioria dos domínios, há cinco níveis, no entanto, para resposta a incidentes, existem apenas quatro. Quanto maior o nível certificado, mais madura será a capacidade de segurança cibernética da organização. Um resumo dos níveis de maturidade do domínio de resposta à incidência é mostrado abaixo.

- **Nível 2 -** Estabeleça um plano de resposta a incidentes que siga o processo do NIST. Detectar, relatar e priorizar eventos. Responda a eventos seguindo procedimentos predefinidos. Analise a causa dos incidentes para mitigar problemas futuros.
- **Nível 3** - Documentar e relatar incidentes às partes interessadas que foram identificados no plano de resposta a incidentes. Teste a capacidade de resposta a incidentes da organização.
- **Nível 4 -** Use o conhecimento de táticas, técnicas e procedimentos do atacante (TPT) para refinar o planejamento e a execução da resposta a incidentes. Estabeleça um centro de operações de segurança (SOC) que facilite um recurso de resposta 24/7.
- **Nível 5 -** Utilize técnicas de coleta de dados forenses informáticas aceitas e sistemáticas, incluindo o manuseio e armazenamento seguros de dados forenses. Desenvolva e utilize respostas manuais e automatizadas em tempo real para possíveis incidentes que seguem padrões conhecidos.
### Ciclo de vida de resposta a incidentes do NIST

O NIST define quatro etapas no ciclo de vida do processo de resposta a incidentes, conforme mostrado na figura.

- **Preparação** - Os membros do CSIRT são treinados para responder a um incidente. Os membros do CSIRT devem desenvolver continuamente o conhecimento das ameaças emergentes.
- **Detecção e análise** - Através do monitoramento contínuo, o CSIRT identifica, analisa e valida rapidamente um incidente.
- **Contenção, Erradicação e Recuperação** - O CSIRT implementa procedimentos para conter a ameaça, erradicar o impacto nos ativos organizacionais e usar backups para restaurar dados e software. Esta fase pode voltar à detecção e análise para reunir mais informações, ou para expandir o escopo da investigação.
- **Atividades pós-incidente** - O CSIRT então documenta como o incidente foi tratado, recomenda alterações para resposta futura e especifica como evitar uma repetição.

O ciclo de vida de resposta a incidentes destina-se a ser um processo de aprendizagem auto-reforçado, pelo qual cada incidente informa o processo para lidar com incidentes futuros. Cada uma dessas fases é discutida com mais detalhes neste tópico.
![[Pasted image 20250208133834.png]]
### Preparação

A fase de preparação é quando o CSIRT é criado e treinado. Essa fase também é quando as ferramentas e ativos que serão necessários pela equipe para investigar incidentes são adquiridos e implantados. A lista a seguir contém exemplos de ações que também ocorrem durante a fase de preparação:

- Os processos organizacionais são criados para abordar a comunicação entre as pessoas na equipe de resposta. Isso inclui informações de contato para partes interessadas, outros CSIRTs e aplicação da lei, um sistema de rastreamento de problemas, smartphones, software de criptografia, etc.
- São criadas instalações para hospedar a equipe de resposta e o SOC.
- Hardware e software necessários para análise e mitigação de incidentes são adquiridos. Isso pode incluir software forense, computadores sobressalentes, servidores e dispositivos de rede, dispositivos de backup, sniffers de pacotes e analisadores de protocolo.
- As avaliações de risco são usadas para implementar controles que limitarão o número de incidentes.
- A validação da implantação de hardware e software de segurança é realizada em dispositivos de usuário final, servidores e dispositivos de rede.
- Materiais de treinamento de conscientização sobre segurança do usuário são desenvolvidos

Recursos adicionais de análise de incidentes podem ser necessários. Exemplos desses recursos são uma lista de ativos críticos, diagramas de rede, listas de portas, hashes de arquivos críticos e leituras de linha de base da atividade do sistema e da rede. O software de mitigação também é um item importante quando se prepara para lidar com um incidente de segurança. Uma imagem de um sistema operacional limpo e arquivos de instalação de aplicativos pode ser necessária para recuperar um computador de um incidente.

Muitas vezes, o CSIRT pode ter um kit de salto preparado. Esta é uma caixa portátil com muitos dos itens listados acima para ajudar a estabelecer uma resposta rápida. Alguns desses itens podem ser um laptop com software apropriado instalado, mídia de backup e qualquer outro hardware, software ou informações para ajudar na investigação. É importante inspecionar regularmente o kit de salto para instalar atualizações e certificar-se de que todos os elementos necessários estão disponíveis e prontos para uso. É útil praticar a implantação do jump kit com o CSIRT para garantir que os membros da equipe saibam usar seu conteúdo corretamente.![[Pasted image 20250208133956.png]]
### Detecção e análise
![[Pasted image 20250208134022.png]]

Como há tantas maneiras diferentes em que um incidente de segurança pode ocorrer, é impossível criar instruções que cobrem completamente cada etapa a seguir para lidar com eles. Diferentes tipos de incidentes exigirão respostas diferentes.

**Vetores de Ataque**
Uma organização deve estar preparada para lidar com qualquer incidente, mas deve se concentrar nos tipos mais comuns de incidentes para que eles possam ser tratados rapidamente. Estes são alguns dos tipos mais comuns de vetores de ataque:

- **Web** - Qualquer ataque iniciado a partir de um site ou aplicativo hospedado por um site.
- **E-mail** - Qualquer ataque iniciado a partir de um email ou anexo de email.
- **Perda ou Roubo** - Qualquer equipamento usado pela organização, como um laptop, desktop ou smartphone, pode fornecer as informações necessárias para que alguém inicie um ataque.
- **Personificação** - Quando algo ou alguém é substituído com o propósito de intenção maliciosa.
- **Atrição** - Qualquer ataque que use força bruta para atacar dispositivos, redes ou serviços.
- **Mídia** - Qualquer ataque iniciado a partir de armazenamento externo ou mídia removível.

**Detecção**
Alguns incidentes são fáceis de detectar, enquanto outros podem passar despercebidos por meses. A detecção de incidentes de segurança pode ser a fase mais difícil no processo de resposta a incidentes. Os incidentes são detectados de muitas maneiras diferentes e nem todas essas formas são muito detalhadas ou fornecem clareza detalhada. Existem formas automatizadas de detecção, como software antivírus ou IDS. Há também detecções manuais por meio de relatórios de usuários.

É importante determinar com precisão o tipo de incidente e a extensão dos efeitos. Existem duas categorias para os sinais de um incidente:

- **Precursor** - Este é um sinal de que um incidente pode ocorrer no futuro. Quando precursores são detectados, um ataque pode ser evitado alterando medidas de segurança para abordar especificamente o tipo de ataque detectado. Exemplos de precursores são entradas de log que mostram uma resposta a uma varredura de porta ou uma vulnerabilidade recém-descoberta para o servidor Web de uma organização.
- **Indicador** - Este é um sinal de que um incidente já pode ter ocorrido ou está ocorrendo no momento. Alguns exemplos de indicadores são um host infectado com malware, vários logins com falha de uma fonte desconhecida ou um alerta IDS.

**Análise**
A análise de incidentes é difícil porque nem todos os indicadores são precisos. Em um mundo perfeito, cada indicador deve ser analisado para descobrir se é preciso. Isso é quase impossível devido ao número e variedade de incidentes registrados e relatados. O uso de algoritmos complexos e aprendizado de máquina muitas vezes ajudam a determinar a validade de incidentes de segurança. Isso é mais prevalente em grandes organizações que têm milhares ou mesmo milhões de incidentes diariamente. Um método que pode ser usado é a criação de perfis de rede e sistema. A criação de perfis é medir as características da atividade esperada em dispositivos e sistemas de rede para que as alterações nele possam ser mais facilmente identificadas.

Quando um indicador é considerado preciso, isso não significa necessariamente que ocorreu um incidente de segurança. Alguns indicadores acontecem por outras razões além da segurança. Um servidor que falha continuamente, por exemplo, pode ter RAM ruim em vez de um ataque de estouro de buffer ocorrer. Para ser seguro, até mesmo sintomas ambíguos ou contraditórios devem ser analisados para determinar se ocorreu um incidente de segurança legítimo. O CSIRT deve reagir rapidamente para validar e analisar incidentes. Isso é realizado seguindo um processo predefinido e documentando cada etapa.

**Escopo**
Quando o CSIRT acredita que um incidente ocorreu, ele deve executar imediatamente uma análise inicial para determinar o escopo do incidente, como quais redes, sistemas ou aplicativos são afetados, quem ou o que originou o incidente e como o incidente está ocorrendo. Essa atividade de escopo deve fornecer informações suficientes para que a equipe priorize atividades subsequentes, como contenção do incidente e análise mais profunda dos efeitos do incidente.

**Notificação de incidentes**
Quando um incidente é analisado e priorizado, a equipe de resposta a incidentes precisa notificar as partes interessadas e externas apropriadas para que todos os que precisam estar envolvidos desempenhem suas funções. Exemplos de partes que são normalmente notificadas incluem:

- Diretor executivo de informações (CIO)
- Chefe de segurança da informação
- Oficial de segurança da informação local
- Outras equipes de resposta a incidentes dentro da organização
- Equipas externas de resposta a incidentes (se apropriado)
- Proprietário do sistema
- Recursos humanos (para casos envolvendo funcionários, como assédio por e-mail)
- Assuntos públicos (para incidentes que possam gerar publicidade)
- Departamento jurídico (para incidentes com potenciais ramificações legais)
- US-CERT (necessário para agências federais e sistemas operados em nome do governo federal)
- Aplicação da lei (se for caso disso)
### Contenção, erradicação e recuperação
![[Pasted image 20250208134419.png]]

Depois que um incidente de segurança foi detectado e uma análise suficiente foi realizada para determinar se o incidente é válido, ele deve ser contido para determinar o que fazer sobre ele. Estratégias e procedimentos para contenção de incidentes precisam estar em vigor antes que um incidente ocorra e implementado antes que haja danos generalizados.

**Estratégia de contenção**
Para cada tipo de incidente, uma estratégia de contenção deve ser criada e aplicada. Estas são algumas condições para determinar o tipo de estratégia a ser criada para cada tipo de incidente:

- Quanto tempo levará para implementar e concluir uma solução?
- Quanto tempo e quantos recursos serão necessários para implementar a estratégia?
- Qual é o processo para preservar evidências?
- Um invasor pode ser redirecionado para uma área restrita para que o CSIRT possa documentar com segurança a metodologia do invasor?
- Qual será o impacto na disponibilidade de serviços?
- Qual é a extensão dos danos aos recursos ou ativos?
- Quão eficaz é a estratégia?

Durante a contenção, podem ocorrer danos adicionais. Por exemplo, nem sempre é aconselhável desconectar o host comprometido da rede. O processo malicioso pode notar essa desconexão para o controlador CNC e acionar um apagamento de dados ou criptografia no destino. É aqui que a experiência e a experiência podem ajudar a conter um incidente além do escopo da estratégia de contenção.

**Evidência**
Durante um incidente, as provas devem ser recolhidas para resolvê-lo. Os elementos de prova também são importantes para a investigação posterior por parte das autoridades. Documentação clara e concisa sobre a preservação de evidências é fundamental. Para que as provas sejam admissíveis em tribunal, a recolha de provas deve estar em conformidade com regulamentos específicos. Após a coleta de evidências, ela deve ser devidamente contabilizada. Isso é conhecido como cadeia de custódia. Estes são alguns dos itens mais importantes para registrar ao documentar evidências usadas na cadeia de custódia:

- Localização da recuperação e armazenamento de todos os elementos de prova
- Quaisquer critérios de identificação para todas as evidências, como número de série, endereço MAC, nome de host ou endereço IP
- Informações de identificação para todas as pessoas que participaram da coleta ou manuseamento das evidências
- Hora e data em que a evidência foi coletada e em cada instância foi tratada

É vital educar qualquer pessoa envolvida no tratamento de evidências sobre como preservar as evidências adequadamente.

**Identificação do atacante**
A identificação de invasores é secundária à contenção, erradicação e recuperação de hosts e serviços. No entanto, a identificação de invasores minimizará o impacto em ativos e serviços comerciais críticos. Estas são algumas das ações mais importantes a serem executadas para tentar identificar um host atacante durante um incidente de segurança:

- Use bancos de dados de incidentes para pesquisar atividades relacionadas. Esse banco de dados pode ser interno ou localizado em organizações que coletam dados de outras organizações e os consolidam em bancos de dados incidentes, como o banco de dados da comunidade VERIS.
- Valide o endereço IP do invasor para determinar se ele é viável. O host pode ou não responder a um pedido de conectividade. Isso pode ser porque ele foi configurado para ignorar as solicitações ou o endereço já foi reatribuído a outro host.
- Use um mecanismo de busca na internet para obter informações adicionais sobre o ataque. Pode ter havido outra organização ou indivíduo que tenha liberado informações sobre um ataque a partir do endereço IP de origem identificado.
- Monitore os canais de comunicação que alguns atacantes usam, como o IRC. Como os usuários podem ser disfarçados ou anonimizados em canais de IRC, eles podem falar sobre suas façanhas nesses canais. Freqüentemente, as informações coletadas a partir desse tipo de monitoramento são enganosas e devem ser tratadas como pistas e não como fatos.

**Erradicação, recuperação e remediação**
Após a contenção, o primeiro passo para a erradicação é identificar todos os hospedeiros que precisam de correção. Todos os efeitos do incidente de segurança devem ser eliminados. Isso inclui infecções de malware e contas de usuário que foram comprometidas. Todas as vulnerabilidades que foram exploradas pelo invasor também devem ser corrigidas ou corrigidas para que o incidente não ocorra novamente.

Para recuperar hosts, use backups limpos e recentes ou reconstrua-os com mídia de instalação se não houver backups disponíveis ou se eles tiverem sido comprometidos. Além disso, atualize e corrija totalmente os sistemas operacionais e o software instalado de todos os hosts. Altere todas as senhas de host e senhas para sistemas críticos de acordo com a política de segurança de senhas. Esse pode ser um bom momento para validar e atualizar a segurança da rede, as estratégias de backup e as políticas de segurança. Os atacantes freqüentemente atacam os sistemas novamente, ou usam um ataque semelhante para direcionar recursos adicionais, então não se esqueça de evitar isso da melhor forma possível. Concentre-se no que pode ser corrigido rapidamente enquanto prioriza sistemas e operações críticos.
### Atividades pós-incidente
![[Pasted image 20250208134637.png]]

Depois que as atividades de resposta a incidentes erradicaram as ameaças e a organização começou a se recuperar dos efeitos do ataque, é importante dar um passo atrás e periodicamente se reunir com todas as partes envolvidas para discutir os eventos que ocorreram e as ações de todos os indivíduos, enquanto Lidando com o incidente. Isso fornecerá uma plataforma para aprender o que foi feito corretamente, o que foi feito errado, o que poderia ser alterado e o que deve ser melhorado.

**Endurecimento baseado em lições**

Após um incidente importante ter sido tratado, a organização deve realizar uma reunião de “lições aprendidas” para analisar a eficácia do processo de manipulação de incidentes e identificar o fortalecimento necessário para controles e práticas de segurança existentes. Exemplos de boas perguntas a serem respondidas durante a reunião incluem o seguinte:

- Exatamente o que aconteceu, e quando?
- Quão bem a equipe e a gerência se comportaram ao lidar com o incidente?
- Os procedimentos documentados foram seguidos? Eram adequados?
- Quais informações foram necessárias antes?
- Foram tomadas quaisquer medidas ou medidas que possam ter inibido a recuperação?
- O que a equipe e a gerência fariam de forma diferente na próxima vez que ocorrer um incidente semelhante?
- Como o compartilhamento de informações com outras organizações pode ser aprimorado?
- Que medidas corretivas podem evitar incidentes semelhantes no futuro?
- Quais precursores ou indicadores devem ser observados no futuro para detectar incidentes semelhantes?
- Quais ferramentas ou recursos adicionais são necessários para detectar, analisar e mitigar incidentes futuros?
### Coleta e retenção de dados de incidentes

Ao realizar reuniões de “lições aprendidas”, os dados coletados podem ser usados para determinar o custo de um incidente por razões de orçamento, bem como para determinar a eficácia do CSIRT e identificar possíveis deficiências de segurança em todo o sistema. Os dados coletados precisam ser acionáveis. Colete apenas dados que possam ser usados para definir e refinar o processo de manipulação de incidentes.

Um maior número de incidentes tratados pode mostrar que algo na metodologia de resposta à incidência não está funcionando corretamente e precisa ser refinado. Poderia também mostrar incompetência no CSIRT. Um número menor de incidentes pode mostrar que a segurança da rede e do host foi melhorada. Também pode mostrar uma falta de detecção de incidentes. Contagens de incidentes separadas para cada tipo de incidente podem ser mais eficazes para mostrar pontos fortes e fracos do CSIRT e medidas de segurança implementadas. Essas subcategorias podem ajudar a direcionar onde reside uma fraqueza, em vez de se haver alguma fraqueza.

O tempo de cada incidente fornece informações sobre a quantidade total de mão-de-obra usada e o tempo total de cada fase do processo de resposta a incidentes. O tempo até a primeira resposta também é importante, bem como quanto tempo levou para relatar o incidente e encaminhá-lo para além da organização, se necessário.

É importante realizar uma avaliação objetiva de cada Incidente. A resposta a um incidente que foi resolvido pode ser analisada para determinar a sua eficácia. A Publicação Especial 800-61 do NIST fornece os seguintes exemplos de ativações realizadas durante uma avaliação objetiva de um incidente:

- Analisando logs, formulários, relatórios e outras documentações de incidentes para a adesão a políticas e procedimentos de resposta a incidentes estabelecidos.
- Identificando quais precursores e indicadores do incidente foram registrados para determinar com que eficácia o incidente foi registrado e identificado.
- Determinando se o incidente causou danos antes de ser detectado.
- Determinar se a causa real do incidente foi identificada e identificar o vetor de ataque, as vulnerabilidades exploradas e as características dos sistemas, redes e aplicativos alvo ou vitimizados.
- Determinando se o incidente é uma recorrência de um incidente anterior.
- Cálculo do dano monetário estimado do incidente (por exemplo, informações e processos comerciais críticos afetados negativamente pelo incidente).
- Medir a diferença entre a avaliação de impacto inicial e a avaliação de impacto final.
- Identificar quais medidas, se houver, poderiam ter evitado o incidente.
- A avaliação subjetiva de cada incidente exige que os membros da equipe de resposta a incidentes avaliem seu próprio desempenho, bem como o de outros membros da equipe e de toda a equipe. Outra fonte valiosa de entrada é o proprietário de um recurso que foi atacado, a fim de determinar se o proprietário acha que o incidente foi tratado de forma eficiente e se o resultado foi satisfatório.

Deve haver uma política em vigor em cada organização que descreva quanto tempo a evidência de um incidente é mantida. Muitas vezes, as provas são retidas durante muitos meses ou muitos anos após um incidente ter ocorrido. Em alguns casos, os regulamentos de conformidade podem exigir o período de retenção. Estes são alguns dos fatores determinantes para a retenção de evidências:

- **Promotoria** - Quando um atacante será processado por causa de um incidente de segurança, as provas devem ser mantidas até que todas as ações legais tenham sido concluídas. Isso pode ser vários meses ou muitos anos. Em ações judiciais, nenhuma evidência deve ser ignorada ou considerada insignificante. A política de uma organização pode declarar que qualquer evidência que envolva um incidente que tenha sido envolvido em ações legais nunca deve ser excluída ou destruída.
- **Tipo de Dados** - Uma organização pode especificar que tipos específicos de dados devem ser mantidos por um período de tempo específico. Itens como e-mail ou texto podem precisar ser mantidos apenas por 90 dias. Dados mais importantes, como os usados em uma resposta a incidentes (que não teve ação legal), podem precisar ser mantidos por três anos ou mais.
- **Custo** - Se houver muita mídia de hardware e armazenamento que precisa ser armazenada por um longo período de tempo, ela pode se tornar dispendiosa. Lembre-se também de que, à medida que a tecnologia muda, os dispositivos funcionais que podem usar hardware desatualizado e mídia de armazenamento também devem ser armazenados.
### Requisitos de relatórios e compartilhamento de informações

Os regulamentos governamentais devem ser consultados pela equipe jurídica para determinar com precisão a responsabilidade da organização em relatar o incidente. Além disso, o gerenciamento precisará determinar qual comunicação adicional é necessária com outras partes interessadas, como clientes, fornecedores, parceiros, etc.

Além dos requisitos legais e das considerações das partes interessadas, o NIST recomenda que uma organização coordene com as organizações para compartilhar detalhes sobre o incidente. Por exemplo, a organização poderia registrar o incidente no banco de dados da comunidade VERIS.

As recomendações críticas do NIST para o compartilhamento de informações são as seguintes:

- Planeje a coordenação de incidentes com partes externas antes que ocorram incidentes.
- Consulte o departamento jurídico antes de iniciar qualquer esforço de coordenação.
- Realizar compartilhamento de informações sobre incidentes durante todo o ciclo de vida de resposta a incidentes
- Tente automatizar o máximo possível do processo de compartilhamento de informações.
- Equilibre os benefícios do compartilhamento de informações com as desvantagens do compartilhamento de informações confidenciais.

Compartilhe o máximo possível de informações apropriadas sobre incidentes com outras organizações.