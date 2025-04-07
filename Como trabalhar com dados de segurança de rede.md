# Uma plataforma de dados comum

### ELK

Uma rede típica tem uma infinidade de logs diferentes para manter o controle e a maioria desses logs está em formatos diferentes. Com enormes quantidades de dados diferentes, como é possível obter uma visão geral das operações de rede e, ao mesmo tempo, ter uma sensação de anomalias sutis ou alterações na rede?

O Elastic Stack tenta resolver esse problema fornecendo uma única visualização de interface em uma rede heterogênea. O Elastic Stack consiste em Elasticsearch, Logstash e Kibana (ELK). É uma estrutura modular e altamente escalável para ingestão, análise, armazenamento e visualização de dados. O Elasticsearch é uma plataforma de núcleo aberto (código aberto nos componentes principais) para pesquisar e analisar os dados de uma organização em tempo quase real. Ele pode ser usado em muitos contextos diferentes, mas ganhou popularidade na segurança de rede como uma ferramenta SIEM. Security Onion inclui ELK e outros componentes do Elastic, incluindo:

- **Beats** — Esta é uma série de plugins de software que enviam diferentes tipos de dados para os armazenamentos de dados do Elasticsearch.
- **ElastAlert** — Isso fornece consultas e alertas de segurança com base em critérios definidos pelo usuário e outras informações de dados no Elasticsearch. Notificações de alerta podem ser enviadas para um console ou e-mail e outros sistemas de notificação, como a plataforma de resposta a incidentes de segurança do Hive.
- **Curador** — Isso fornece ações para gerenciar índices de dados do Elasticsearch.

O Elasticsearch, que é o componente do mecanismo de pesquisa, usa serviços Web RESTful e APIs, um cluster de computação distribuído com vários nós de servidor e um banco de dados NoSQL distribuído composto de documentos JSON. Funcionalidades adicionais podem ser adicionadas por meio de extensões personalizadas. A empresa Elasticsearch oferece uma extensão comercial chamada X-Pack que adiciona segurança, alerta, monitoramento, relatórios e gráficos. A empresa também oferece um complemento de aprendizado de máquina, bem como seu próprio produto Elastic SIEM.

O Logstash permite a coleta e a normalização de dados de rede em índices de dados que podem ser pesquisados com eficiência pelo Elasticsearch. Os módulos Logstash e Beats são usados para ingerir dados no cluster do Elasticsearch.

Kibana fornece uma interface gráfica para os dados que são compilados pelo Elasticsearch. Ele permite a visualização de dados de rede e fornece ferramentas e atalhos para consultar esses dados, a fim de isolar possíveis violações de segurança.

Os principais componentes de código aberto do Elastic Stack são Logstash, Beats, Elasticsearch e Kibana, conforme mostrado na figura.![[Pasted image 20250207192511.png]]

**Lostash**

Logstash é um sistema de extração, transformação e carga com a capacidade de receber várias fontes de dados de log e transformar ou analisar os dados através de tradução, classificação, agregação, divisão e validação. Depois de transformar os dados, os dados são carregados no banco de dados Elasticsearch no formato de arquivo apropriado. A figura mostra alguns dos campos que estão disponíveis no Logstash, como mostrado na interface Kibana Management.

![[Pasted image 20250207192610.png]]

**Beats**

Os agentes Beats são clientes de software de código aberto usados para enviar dados operacionais diretamente para o Elasticsearch ou através do Logstash. Elastic, bem como a comunidade de código aberto, desenvolvem ativamente agentes Beats, portanto, há uma grande variedade de agentes Beats para enviar dados para o Elasticsearch em tempo quase real. Alguns dos agentes Beats fornecidos pelo Elastic são Auditbeat para dados de auditoria, Metricbeat para dados métricos, Heartbeat para disponibilidade, Packetbeat para tráfego de rede, Journalbeat para diários Systemd e Winlogbeat para logs de eventos do Windows. Algumas Beats de origem comunitária são Amazonbeat, Apachebeat, Dockbeat, Nginxbeat e Mqttbeat, para citar alguns.

**Elasticsearch**

Elasticsearch é um motor de busca empresarial de plataforma cruzada escrito em Java. Os componentes principais são de código aberto com addons comerciais chamados X-packs que dão funcionalidade adicional. O Elasticsearch suporta pesquisa quase em tempo real usando APIs REST simples para criar ou atualizar documentos JSON (JavaScript Object Notation) usando solicitações HTTP. Pesquisas podem ser feitas usando qualquer programa capaz de fazer solicitações HTTP, como um navegador web, Postman, cURL, etc Essas APIs também podem ser acessadas por Python ou outros scripts de linguagem de programação para operações automatizadas.

A estrutura de dados do Elasticsearch é chamada de índice **invertido**, que é projetado para permitir pesquisas de texto completo muito rápidas. Um índice é como um banco de dados, é um namespace para uma coleção de documentos que estão relacionados uns aos outros. Um índice pode ser particionado ou mapeado em diferentes tipos. Se você comparar um índice do Elasticsearch com um banco de dados relacional tradicional, o **índice** será como o banco de dados, os **tipos** serão como as tabelas e os **documentos** serão como as colunas e linhas, conforme mostrado na tabela.![[Pasted image 20250207192751.png]]

O Elasticsearch armazena dados em documentos formatados em JSON. Um documento JSON é organizado em hierarquias de pares chave/valor, com uma **chave** sendo um nome e o **valor** correspondente sendo uma string, número, booleano, data, matriz ou outro tipo de dados.

**Kibana**

Kibana fornece uma interface gráfica de usuário fácil de usar para gerenciar o Elasticsearch. Usando um navegador da Web, um analista pode usar a interface Kibana para pesquisar e visualizar índices. A guia de gerenciamento permite que você crie e gerencie índices e seus tipos e formatos. A guia descoberta é uma maneira rápida e poderosa de visualizar seus dados e pesquisá-los usando as ferramentas de pesquisa. A guia Visualize permite criar visualizações personalizadas, como gráficos de barras, gráficos de linhas, gráficos de pizza, mapas de calor e muito mais. As visualizações criadas podem ser organizadas em painéis personalizados para monitorar e analisar seus dados. Um painel Kibana é mostrado na figura.![[Pasted image 20250207192824.png]]
### Redução de dados

A quantidade de tráfego de rede que é coletada por capturas de pacotes e o número de entradas e alertas de arquivos de log gerados por dispositivos de rede e segurança podem ser enormes. Mesmo com os avanços recentes em Big Data, o processamento, armazenamento, acesso e arquivamento de dados relacionados ao NSM é uma tarefa assustadora. Por esse motivo, é importante identificar os dados de rede que devem ser coletados. Nem todas as entradas de arquivo de log, pacotes e alertas precisam ser coletadas. Ao limitar o volume de dados, ferramentas como Elasticsearch serão muito mais úteis, como mostrado na figura.

Algum tráfego de rede tem pouco valor para o NSM. Dados criptografados, como tráfego IPsec ou SSL, são praticamente ilegíveis. Algum tráfego, como o gerado por protocolos de roteamento ou protocolo de árvore de abrangência, é de rotina e pode ser excluído. Outros protocolos de broadcast e multicast geralmente podem ser eliminados das capturas de pacotes, assim como o tráfego de outros protocolos que geram muito tráfego de rotina.

Além disso, os alertas gerados por um HIDS, como auditoria de segurança do Windows ou OSSEC, devem ser avaliados quanto à relevância. Alguns são informativos ou de baixo impacto potencial na segurança. Essas mensagens podem ser filtradas a partir de dados do NSM. Da mesma forma, o syslog pode armazenar mensagens de severidade muito baixa que poderiam ser ignoradas para diminuir a quantidade de dados NSM a serem tratados.![[Pasted image 20250207192956.png]]
### Normalização de dados

Normalização de dados é o processo de combinar dados de uma série de fontes de dados em um formato comum. O Logstash fornece uma série de transformações que processam dados de segurança e os transformam antes de adicioná-los ao Elasticsearch. Plugins adicionais podem ser criados para atender às necessidades da organização.

Um esquema comum especificará os nomes e formatos para os campos de dados necessários. A formatação dos campos de dados pode variar muito entre as fontes. No entanto, para que a pesquisa seja eficaz, os campos de dados devem ser consistentes. Por exemplo, endereços IPv6, endereços MAC e informações de data e hora podem ser representados em formatos variados. Da mesma forma, máscaras de sub-rede, registros DNS e assim por diante podem variar em formato entre fontes de dados. As transformações Logstash aceitam os dados em seu formato nativo e tornam os elementos dos dados consistentes em todas as fontes. Por exemplo, um único formato será usado para endereços e carimbos de data/hora para dados de todas as fontes.

**Formatos de Endereço IPv6**

- 2001:db8:acad:1111:2222::33
- 2001:DB8:ACAD:1111:2222::33
- 2001:DB8:ACAD:1111:2222:0:0:33
- 2001:DB8:ACAD:1111:2222:0000:0000:0033

**Formatos MAC**

- A7:03:DB:7C:91:AA
- A7-03-DB-7C-91-AA
- A70.3DB.7C9.1AA

**Formatos de Data**

- Monday, July 24, 2017 7:39:35pm
- Mon, 24 Jul 2017 19:39:35 +0000
- 2017-07-24T19:39:35+00:00
- 1500925254

A normalização dos dados é necessária para simplificar a pesquisa de eventos correlacionados. Se existirem valores formatados de forma diferente nos dados do NSM para endereços IPv6, por exemplo, um termo de consulta separado precisaria ser criado para cada variação para que os eventos correlacionados sejam retornados pela consulta.
### Arquivamento de dados

Todos adorariam a segurança de coletar e salvar tudo, só por precaução. No entanto, reter dados do NSM indefinidamente não é viável devido a problemas de armazenamento e acesso. Note-se que o período de retenção para certos tipos de informações de segurança de rede pode ser especificado por estruturas de conformidade. Por exemplo, o Payment Card Industry Security Standards Council (PCI DSS) exige que uma trilha de auditoria das atividades do usuário relacionadas a informações protegidas seja mantida por um ano.

Security Onion tem diferentes períodos de retenção de dados para diferentes tipos de dados NSM. Para pcaps e logs brutos de Bro, um valor atribuído no **securityonion.conf** arquivo controla a porcentagem de espaço em disco que pode ser usada por arquivos de log. Por padrão, esse valor é definido como 90%. Para o Elasticsearch, a retenção de índices de dados é controlada pelo curador do Elasticsearch. O curador é executado em um contêiner do Docker e executa a cada minuto de acordo com os **cron** trabalhos. O curador registra sua atividade no curator.log. O curador usa como padrão os índices de fechamento com mais de 30 dias. Para modificar isso, altere CURATOR _CLOSE _DAYS em /etc/nsm/securityonion.conf. À medida que um disco atinge a capacidade, o Curator exclui índices antigos para impedir que o disco seja preenchido. Para alterar o limite, modifique LOG _SIZE _LIMIT em /etc/nsm/securityonion.conf.

Os dados de alerta Sguil são mantidos por 30 dias por padrão. Esse valor é definido no **securityonion.conf** arquivo.

Security Onion é conhecido por exigir muito armazenamento e RAM para executar corretamente. Dependendo do tamanho da rede, vários terabytes de armazenamento podem ser necessários. É claro que os dados Security Onion sempre podem ser arquivados em armazenamento externo por um sistema de arquivamento de dados, dependendo das necessidades e capacidades da organização.

**Observação**: Os locais de armazenamento para os diferentes tipos de dados Security Onion variam de acordo com a implementação do Security Onion.

# Investigando dados de rede

### Trabalhando em Sguil

 O principal dever de um analista de segurança cibernética é a verificação de alertas de segurança. Dependendo da organização, as ferramentas usadas para fazer isso variam. Por exemplo, um sistema de emissão de bilhetes pode ser usado para gerenciar a atribuição de tarefas e a documentação. Em Security Onion, o primeiro lugar que um analista de segurança cibernética irá verificar alertas é o Sguil.

O Sguil correlaciona automaticamente alertas semelhantes em uma única linha e fornece uma maneira de exibir eventos correlacionados representados por essa linha. Para ter uma noção do que está acontecendo na rede, pode ser útil classificar na coluna **CNT** para exibir os alertas com a maior frequência.

Clicar com o botão direito do mouse no valor **CNT** e selecionar **Exibir Eventos Correlacionados** abre uma guia que exibe todos os eventos relacionados pelo Sguil. Isso pode ajudar o analista de segurança cibernética a entender o período durante o qual os eventos correlacionados foram recebidos pelo Sguil. Observe que cada evento recebe um ID de evento exclusivo. Somente o primeiro ID de evento na série de eventos correlacionados é exibido na guia Eventos em Tempo Real. A figura mostra os alertas do Sguil classificados no **CNT** com o menu **Exibir eventos** correlacionados aberto.![[Pasted image 20250207230846.png]]
### Consultas Sguil

As consultas podem ser construídas no Sguil usando o Construtor de Consultas. Ele simplifica a construção de consultas até certo ponto, mas o analista de segurança cibernética deve conhecer os nomes de campo e alguns problemas com valores de campo. Por exemplo, o Sguil armazena endereços IP em uma representação de inteiro. Para consultar um endereço IP na notação decimal pontilhada, o valor do endereço IP deve ser colocado dentro da **INET_ATON()** função. Construtor de consultas é aberto a partir do menu **Consulta** Sguil. Selecione **Tabela de Eventos de Consulta** para pesquisar eventos ativos.

A tabela mostra os nomes de alguns dos campos da tabela de eventos que podem ser consultados diretamente. Selecionar **Mostrar Tabelas** de Banco de Dados **no menu** Consulta exibe uma referência aos nomes e tipos de campo para cada uma das tabelas que podem ser consultadas. Ao realizar pesquisas de tabela de eventos, use o padrão **event.fieldName = value**.
![[Pasted image 20250207231037.png]]

A figura mostra um carimbo de data/hora simples e uma consulta de endereço IP feita na janela Construtor de consultas. Observe o uso da **INET_ATON()** função para simplificar a inserção de um endereço IP.![[Pasted image 20250207231141.png]]

No exemplo abaixo, o analista de segurança cibernética está investigando uma porta de origem 40754 associada a um alerta de ameaças emergentes. No final da consulta, a **WHERE event.src_port = ‘40754’** parte foi criada pelo usuário no Query Builder. O restante da consulta é fornecido automaticamente pelo Sguil e diz respeito a como os dados associados aos eventos devem ser recuperados, exibidos e apresentados.![[Pasted image 20250207231230.png]]
### Pivotante a partir de Sguil

A Sguil oferece a capacidade de o analista de segurança cibernética girar para outras fontes de informação e ferramentas. Os arquivos de log estão disponíveis no Elasticsearch. Capturas de pacotes relevantes podem ser exibidas no Wireshark. Transcrições de sessões TCP e informações de detecção Zeek (Bro) também estão disponíveis. O menu mostrado na figura foi aberto clicando com o botão direito do mouse em um ID de alerta. A seleção deste menu abrirá informações sobre o alerta em outras ferramentas, que fornecem informações ricas e contextualizadas ao analista de segurança cibernética.![[Pasted image 20250207231353.png]]

Além disso, o Sguil pode fornecer dinâmicas para informações sobre o Sistema de Detecção de Ativos em Tempo Real Passivo (PRADS) e o Security Analyst Network Connection Profiler (SANCP). Essas ferramentas são acessadas clicando com o botão direito do mouse em um endereço IP de um evento e selecionando os menus Consulta Rápida ou Consulta Avançada.

O PRADS reúne dados de criação de perfil de rede, incluindo informações sobre o comportamento dos ativos na rede. PRADS é uma fonte de eventos, como Snort e OSSEC. Ele também pode ser consultado através do Sguil quando um alerta indica que um host interno pode ter sido comprometido. A execução de uma consulta PRADS fora do Sguil pode fornecer informações sobre os serviços, aplicativos e cargas úteis que podem ser relevantes para o alerta. Além disso, o PRADS detecta quando novos ativos aparecem na rede.

**Nota**: A interface Sguil refere-se a PADS em vez de PRADS. PADS foi o antecessor do PRADS. PRADS é a ferramenta que é realmente usada em Security Onion. O PRADS também é usado para preencher tabelas SANCP. Em Security Onion, as funcionalidades do SANCP foram substituídas pelo PRADS, no entanto, o termo SANCP ainda é usado na interface Sguil. O PRADS coleta os dados e um agente SANCP registra os dados em uma tabela de dados SANCP.

As funcionalidades do SANCP dizem respeito à coleta e registro de informações estatísticas sobre tráfego e comportamento da rede. O SANCP fornece um meio de verificar se as conexões de rede são válidas. Isso é feito através da aplicação de regras que indicam qual tráfego deve ser registrado e as informações com as quais o tráfego deve ser marcado.
### Manipulação de eventos em Sguil

Finalmente, Sguil não é apenas um console que facilita a investigação de alertas. É também uma ferramenta para endereçar ou classificar alertas. Três tarefas podem ser concluídas no Sguil para gerenciar alertas. Primeiro, os alertas que foram encontrados como falsos positivos podem ser expirados. Isso pode ser feito usando o botão direito do mouse na coluna ST para o evento e usando o menu ou pressionando a tecla F8. Um evento expirado desaparece da fila. Em segundo lugar, se o analista de segurança cibernética não tiver certeza de como lidar com um evento, ele pode ser escalado pressionando a tecla F9. O alerta será movido para a guia Eventos Escalados do Sguil. Finalmente, um evento pode ser categorizado. A categorização é para eventos que foram identificados como verdadeiros positivos.

Sguil inclui sete categorias pré-construídas que podem ser atribuídas usando um menu, que é mostrado na figura, ou pressionando a tecla de função correspondente. Por exemplo, um evento seria categorizado como Cat I pressionando a tecla F1. Além disso, podem ser criados critérios que categorizam automaticamente um evento. Presume-se que eventos categorizados tenham sido tratados pelo analista de segurança cibernética. Quando um evento é categorizado, ele é removido da lista de Eventos em **Tempo Real**. O evento permanece no banco de dados no entanto, e ele pode ser acessado por consultas que são emitidas por categoria.

Este curso abrange Sguil em um nível básico. Existem inúmeros recursos na internet para aprender mais.![[Pasted image 20250207231629.png]]
### Trabalhando no 

Logstash e Beats são usados para ingestão de dados no Elastic Stack. Eles fornecem acesso a um grande número de entradas de arquivo de log. Como o número de logs que podem ser exibidos é tão grande, Kibana, que é a interface visual nos logs, é configurado para mostrar as últimas 24 horas por padrão. Você pode ajustar o intervalo de tempo para exibir intervalos de dados mais amplos ou mais antigos.![[Pasted image 20250207231717.png]]
Para ver registros de arquivos de log por um período diferente, clique na guia Últimas 24 horas no canto superior direito do Kibana. A partir daí, defina o Intervalo de Tempo selecionando a guia Rápido para intervalos de tempo predefinidos. Você também pode inserir as datas e horas manualmente usando a guia Absoluto. A figura mostra um intervalo de tempo absoluto de 17 de maio a 18 de maio de 2020. Os logs são ingeridos no Elasticsearch em índices ou bancos de dados separados com base em um intervalo de tempo configurado.

A melhor maneira de monitorar seus dados no Elasticsearch é criar painéis visuais personalizados que rastreiam os dados que você está interessado em usar. Uma variedade de gráficos visuais, incluindo gráficos de barras, gráficos de pizza, métricas de contagem, mapas de calor, mapas geográficos, listas de números superiores estão disponíveis. No Kibana, visualizações e gráficos podem ser pesquisados e filtrados com métricas específicas e buckets de dados.
### Consultas no ELK

O Elasticsearch é construído sobre o Apache Lucene, uma biblioteca de software de mecanismo de pesquisa de código aberto que possui recursos completos de indexação e pesquisa de texto. O Elasticsearch ingere dados em documentos chamados índices e esses documentos são mapeados para vários tipos de dados usando padrões de índice. Os padrões de índice criam uma estrutura de dados de campos e valores formatados em JSON. Os tipos de dados nos campos podem estar nos seguintes formatos:

- Core Datatypes: Texto (Strings), Numérico, Data, Booleano, Binário e Intervalo
- Complex Datatypes: Objeto (JSON), aninhado (matrizes de objetos JSON)
- Geo Datatypes: Geo-ponto (latitude/longitude), Geo-forma (polígonos)
- Specialized Datatypes: Endereços IP, contagem de tokens, histograma, etc.)

Usando bibliotecas de software Lucene, Elasticsearch tem sua própria linguagem de consulta baseada em JSON chamado Query DSL (Domain Specific Language). Consulta DSL apresenta consultas de folha, consultas compostas e consultas caras. Consultas de folha procuram um valor específico em um campo específico, como consultas de correspondência, termo ou intervalo. Consultas compostas incluem outras consultas de folha ou compostos e são usados para combinar várias consultas de uma forma lógica. Consultas caras são executadas lentamente e incluem correspondência difusa, correspondência regex e correspondência curinga.

**Idioma da consulta**

Junto com JSON, consultas Elasticsearch fazer uso dos seguintes elementos: operadores booleanos, Campos, Intervalos, Curingas, Regex, Pesquisa difusa, Pesquisa de texto.

- **Operadores booleanos** - operadores AND, OR e NOT:
    
    - “ php” OU “zip” OU “exe” OU “jar” OU “run”
    - “ RST” E “ACK”
- **Campos** - Em pares chave:valor separados por dois pontos, você especifica o campo de chave, dois pontos, um espaço e o valor:
    
    - dst.ip: “192.168.1.5”
    - dst.port: 80
- **Intervalos** - Você pode pesquisar campos dentro de um intervalo específico usando colchetes (inclusive) ou intervalo de chaves (exclusivo):
    
    - host: [1 TO 255] — Retorna eventos com idade entre 1 e 255
    - TTL: {100 TO 400} — Retorna eventos com preços entre 101 e 399
    - name: [Admin TO User] — Retorna nomes entre e incluindo Admin e Usuário
- **Curingas** - O* caractere é para vários caracteres curingas e o? caractere para curingas de caractere único:
    
    - P?ssw?rd — Vai combinar Password, e P@ssw0rd
    - Pas* — Vai combinar Pass, Passwd, e Password
- **Regex** — Estes são colocados entre barras (/):
    
    - /d [ao] n/ — Combina com dan e don
    - /<.+>/ — Corresponderá a um texto semelhante a uma marca HTML
- **Pesquisa difusa** - A pesquisa difusa usa a distância de Damerau-Levenshtein para corresponder aos termos que são semelhantes na ortografia. Isso é ótimo quando seu conjunto de dados tem palavras ortografadas incorretamente. Use o til (~) para encontrar termos semelhantes:
    
    - index.php~ - Isso pode retornar resultados como “index.html”, “home.php” e “info.php”.
    - Use o til (~) junto com um número para especificar o tamanho da distância entre as palavras:
    - term~2 - Isso vai combinar, entre outras coisas: "team", "terms", "trem" e "torn"
- **Pesquisa de texto** - Digite o termo ou valor que deseja localizar. Isso pode ser um campo, ou uma string dentro de um campo, etc.

**Execução da Consulta**

O Elasticsearch foi projetado para fazer interface com usuários usando clientes baseados na Web que seguem a estrutura HTTP REST. As consultas podem ser executadas usando os seguintes métodos:

- **URI** - Elasticsearch can execute queries using URI searches:
    - http://localhost:9200/_search?q=query:ns.example.com
- **cURL** - Elasticsearch can execute queries using cURL from the command line:
    - curl “localhost: 9200/ _search?q=query:ns.example.com”
- **JSON** — O Elasticsearch pode executar consultas com uma pesquisa de corpo de solicitação usando um documento JSON que começa com um elemento de consulta e uma consulta formatada usando a linguagem específica de domínio de consulta.
- **Ferramentas de desenvolvimento** — O Elasticsearch pode executar consultas usando o console Dev Tools no Kibana e uma consulta formatada usando o Query Domain Specific Language.

**Observação**: As consultas avançadas do Elasticsearch estão além do escopo deste curso. Nos laboratórios, você receberá as instruções de consulta complexas, se necessário.
### Investigando chamadas de processo ou API

Os aplicativos interagem com um sistema operacional (SO) por meio de chamadas do sistema para a interface de programação de aplicativos (API) do sistema operacional, como mostrado na figura. Essas chamadas de sistema permitem o acesso a muitos aspectos da operação do sistema, tais como:

- Controle de processos de software
- Gerenciamento de Arquivos
- Gerenciamento de dispositivos
- Gerenciamento de informações
- Comunicação

O malware também pode fazer chamadas ao sistema. Se o malware pode enganar um kernel do sistema operacional para permitir que ele faça chamadas de sistema, muitas explorações são possíveis.

O software HIDS rastreia a operação de um sistema operacional host. As regras OSSEC detectam alterações nos parâmetros baseados em host, como a execução de processos de software, alterações nos privilégios do usuário e modificações no registro, entre muitos outros. As regras da OSSEC dispararão um alerta em Sguil. Ao girar para o Kibana no endereço IP do host, você pode escolher o tipo de alerta com base no programa que o criou. A filtragem de índices OSSEC resulta em uma exibição dos eventos OSSEC que ocorreram no host, incluindo indicadores de que o malware pode ter interagido com o kernel do sistema operacional.![[Pasted image 20250207232101.png]]
### Investigando Detalhes do Arquivo

No Sguil, se o analista de segurança cibernética suspeitar de um arquivo, o valor de hash pode ser enviado para um site online, como VirusTotal, para determinar se o arquivo é conhecido como malware. O valor de hash pode ser enviado a partir da guia Pesquisar na página VirusTotal.

No Kibana, Zeek Hunting pode ser usado para exibir informações sobre os arquivos que entraram na rede. A partir dos tipos MIME, ou mídia, que estão presentes, os filtros podem ser definidos para exibir informações sobre tipos específicos de arquivos, como **application/xml** ou **application/zip**. A partir daí, detalhes para os arquivos individuais podem ser exibidos, como mostrado na figura. Note que no Kibana, o tipo de evento é mostrado como **bro_files**, mesmo que o novo nome para Bro seja Zeek.![[Pasted image 20250207232149.png]]
Numerosos detalhes estão disponíveis para os arquivos. Neste exemplo, os hashes MD5 e SHA-1 são mostrados, assim como outros detalhes. As entradas azuis fornecem tabelas dinâmicas para visualizar detalhes das informações fornecidas na tabela no CapMe! ou outras ferramentas.
# Aprimorando o trabalho do analista de segurança cibernética

### Painéis e visualizações

Os painéis fornecem uma combinação de dados e visualizações que são projetados para melhorar o acesso e a interpretação de grandes quantidades de informações. Painéis geralmente são interativos. Eles permitem que os analistas de segurança cibernética se concentrem em detalhes e informações específicas clicando em elementos do painel. Por exemplo, clicar em uma barra em um gráfico de barras poderia fornecer um detalhamento das informações para os dados representados por essa barra. Kibana inclui a capacidade de projetar painéis personalizados. Além disso, outras ferramentas incluídas no Security Onion, como o Squert, fornecem uma interface visual para os dados do NSM.

A interface Kibana para selecionar as visualizações que irão compor um painel personalizado são mostradas na figura.![[Pasted image 20250207232554.png]]
### Gerenciamento do fluxo de trabalho

Devido à natureza crítica do monitoramento de segurança de rede, é essencial que os fluxos de trabalho sejam gerenciados. Os fluxos de trabalho são a sequência de processos e procedimentos através dos quais as tarefas de trabalho são concluídas. O gerenciamento de fluxos de trabalho SOC aumenta a eficiência da equipe de operações cibernéticas, aumenta a responsabilidade da equipe e garante que todos os alertas potenciais sejam tratados adequadamente. Em grandes organizações de segurança, é concebível que milhares de alertas sejam recebidos diariamente. Cada alerta deve ser sistematicamente atribuído, processado e documentado pela equipe de operações cibernéticas.

A automação de runbook, ou sistemas de gerenciamento de fluxo de trabalho, fornecem as ferramentas necessárias para agilizar e controlar processos em um centro de operações de segurança cibernética. O Sguil fornece gerenciamento básico de fluxo de trabalho. No entanto, não é uma boa escolha para grandes operações com muitos funcionários. Em vez disso, estão disponíveis sistemas de gerenciamento de fluxo de trabalho de terceiros que podem ser personalizados para atender às necessidades das operações de segurança cibernética.

Além disso, consultas automatizadas são úteis para adicionar eficiência ao fluxo de trabalho de operações cibernéticas. Essas consultas, às vezes conhecidas como playbooks ou playbooks, buscam automaticamente incidentes de segurança complexos que podem fugir a outras ferramentas. No Kibana, as pesquisas filtradas podem ser transformadas em visualizações, que podem ser atualizadas e monitoradas dinamicamente para rastrear eventos. A pilha ELK pode adicionar funcionalidade de alerta instalando a extensão X-Pack no Elastic. O X-Pack é uma extensão comercial do Elasticsearch e inclui recursos de segurança, alerta, monitoramento, emissão de relatórios e gráficos. O Elasticsearch fornece várias formas de notificação de alerta e pode notificar analistas de segurança cibernética por e-mail ou outros meios. Além do X-Pack, a [Elastic.co](http://Elastic.co) também oferece seu próprio produto Elastic SIEM comercial com recursos avançados de monitoramento, alerta e orquestração.