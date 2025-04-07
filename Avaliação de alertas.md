# Fontes de alertas

### Security Onion

O Security Onion é um pacote de código aberto de ferramentas de Monitoramento de Segurança de Rede (NSM) que é executado em uma distribuição Ubuntu Linux. As ferramentas Security Onion fornecem três funções principais para o analista de segurança cibernética: captura completa de pacotes e tipos de dados, sistemas de detecção de intrusão baseados em rede e em host e ferramentas de analistas de alerta. Security Onion pode ser instalado como uma instalação autônoma ou como um sensor e plataforma de servidor. Alguns componentes do Security Onion são de propriedade e mantidos por corporações, como Cisco e Riverbend Technologies, mas são disponibilizados como código aberto.

Para obter mais informações e para obter o Security Onion, pesquise na internet o site Security Onion.

**Observação**: em alguns recursos, você pode ver Security Onion abreviado como SO. Neste curso, usaremos Security Onion.
### Ferramentas de detecção para coleta de dados de alerta

Security Onion contém muitos componentes. É um ambiente integrado projetado para simplificar a implantação de uma solução NSM abrangente. A figura ilustra uma visão simplificada da maneira como alguns dos componentes do Security Onion trabalham juntos.![[Pasted image 20250206231550.png]]

**CapMe**
Esta é uma aplicação web que permite a visualização de transcrições pcap renderizadas com as ferramentas tcpflow ou Zeek. O CapMe pode ser acessado a partir da ferramenta ELSA (Enterprise Log Search and Archive). O CapMe oferece ao analista de segurança cibernética um meio fácil de ler para visualizar uma sessão inteira da Camada 4. O CapMe atua como um plugin para o ELSA e fornece acesso a arquivos pcap relevantes que podem ser abertos no Wireshark.

**Snort**
Este é um Sistema de Detecção de Intrusão de Rede (NIDS). É uma importante fonte de dados de alerta indexados na ferramenta de análise Sguil. O Snort usa regras e assinaturas para gerar alertas. O Snort pode baixar automaticamente novas regras usando o componente PulledPork do Security Onion. Snort e PulledPork são ferramentas de código aberto que são patrocinadas pela Cisco.

**O Zeek**
Anteriormente conhecido como Bro. Este é um NIDS que usa mais uma abordagem baseada em comportamento para detecção de intrusões. Em vez de usar assinaturas ou regras, o Zeek usa políticas, na forma de scripts que determinam quais dados registrar e quando emitir notificações de alerta. O Zeek também pode enviar anexos de arquivos para análise de malware, bloquear o acesso a locais mal-intencionados e desligar um computador que parece estar violando políticas de segurança.

**Observação:** Algumas interfaces dentro do Security Onion ainda não foram atualizadas com a alteração de nome de Bro para Zeek.

**OSSEC**
Este é um sistema de detecção de intrusão baseado em host (HIDS) integrado ao Security Onion. Ele monitora ativamente as operações do sistema host, incluindo a realização de monitoramento de integridade de arquivos, monitoramento de log local, monitoramento de processos do sistema e detecção de rootkit. Alertas OSSEC e dados de log estão disponíveis para Sguil e Kibana. O OSSEC requer que um agente seja executado nos computadores Windows da empresa.

**WAZUH**
Wazuh é um HIDS que substituirá OSSEC em Security Onion. É uma solução completa que fornece um amplo espectro de mecanismos de proteção de terminais, incluindo análise de arquivos de log do host, monitoramento de integridade de arquivos, detecção de vulnerabilidades, avaliação de configuração e resposta a incidentes. Assim como o OSSEC, ele exige que os agentes estejam sendo executados em hosts de rede.

**Suricata**
Este é um NIDS que usa uma abordagem baseada em assinaturas. Ele também pode ser usado para prevenção de intrusões em linha. É semelhante ao Zeek; no entanto, o Suricata usa multithreading nativo, que permite a distribuição do processamento de fluxo de pacotes em vários núcleos de processadores. Ele também inclui alguns recursos adicionais, como bloqueio baseado em reputação e suporte para multithreading de unidade de processamento gráfico (GPU) para melhorar o desempenho.
### Ferramentas de Análise

O Security Onion integra esses vários tipos de dados e logs do Sistema de Detecção de Intrusões (IDS) em uma única plataforma através das seguintes ferramentas:

- **Sguil** - Isso fornece um console de alto nível para investigar alertas de segurança de uma ampla variedade de fontes. Sguil serve como ponto de partida na investigação de alertas de segurança. Uma grande variedade de fontes de dados está disponível para o analista de segurança cibernética, girando diretamente do Sguil para outras ferramentas.
- **Kibana** - Kibana é uma interface de painel interativo para dados do Elasticsearch. Ele permite a consulta de dados do NSM e fornece visualizações flexíveis desses dados. Ele fornece recursos de análise de dados de exploração de dados e aprendizado de máquina. É possível girar do Sguil diretamente para o Kibana para ver exibições contextualizadas com base nos endereços IP de origem e destino associados a um alerta. Pesquise na internet e visite o site [elastic.co](http://elastic.co) para saber mais sobre os muitos recursos do Kibana.
- **Wireshark** - Este é um aplicativo de captura de pacotes integrado ao conjunto Security Onion. Ele pode ser aberto diretamente de outras ferramentas e exibirá capturas completas de pacotes relevantes para uma análise.
- **Zeek** - Este é um analisador de tráfego de rede que serve como um monitor de segurança. O Zeek inspeciona todo o tráfego em um segmento de rede e permite uma análise aprofundada desses dados. A rotação do Sguil para o Zeek fornece acesso a logs de transações muito precisos, conteúdo de arquivos e saída personalizada.

**Nota**: Outras ferramentas Security Onion que não são mostradas na figura estão além do escopo deste curso. Uma descrição completa do Security Onion e seus componentes pode ser encontrada no site Security Onion.
### Geração de alertas

Alertas de segurança são mensagens de notificação geradas por ferramentas, sistemas e dispositivos de segurança do NSM. Os alertas podem vir em várias formas, dependendo da fonte. Por exemplo, o syslog fornece suporte para classificações de gravidade que podem ser usadas para alertar analistas de segurança cibernética sobre eventos que exigem atenção.

No Security Onion, o Sguil fornece um console que integra alertas de várias fontes em uma fila com carimbo de data/hora. Um analista de segurança cibernética pode trabalhar na fila de segurança investigando, classificando, escalonando ou retirando alertas. Em vez de usar um sistema de gerenciamento de fluxo de trabalho dedicado, como o RTIR (Request Tracker for Incident Response), um analista de segurança cibernética usaria a saída de um aplicativo como o Sguil para orquestrar uma investigação do NSM.

Os alertas geralmente incluem informações de cinco tuplas quando disponíveis, bem como carimbos de data/hora e informações que identificam qual dispositivo ou sistema gerou o alerta. Lembre-se de que as cinco tuplas incluem as seguintes informações para rastrear uma conversa entre um aplicativo de origem e destino:

- **SrcIP** - o endereço IP de origem para o evento.
- **SPort** - a porta de Camada 4 de origem (local) para o evento.
- **DstIP** - o IP de destino para o evento.
- **DPort** - a porta de Camada 4 de destino para o evento.
- **Pr** - o número do protocolo IP para o evento.

Informações adicionais podem ser se uma decisão de permissão ou negação foi aplicada ao tráfego, alguns dados capturados da carga útil do pacote ou um valor de hash para um arquivo baixado ou qualquer um dos vários dados.

A figura mostra a janela do aplicativo Sguil com a fila de alertas que estão aguardando para serem investigados na parte superior da interface.![[Pasted image 20250206232219.png]]

Os campos disponíveis para os eventos em tempo real são os seguintes:

- **ST** - This is the status of the event. RT means real time. The event is color-coded by priority. The priorities are based on the category of the alert. There are four priority levels: muito baixo, baixo, médio e alto. As cores variam de amarelo claro a vermelho à medida que a prioridade aumenta.
- **CNT** - Esta é a contagem do número de vezes que este evento foi detectado para o mesmo endereço IP de origem e destino. O sistema determinou que este conjunto de eventos está correlacionado. Em vez de relatar cada um em uma série potencialmente longa de eventos correlacionados nesta janela, o evento é listado uma vez com o número de vezes que foi detectado nesta coluna. Números altos aqui podem representar um problema de segurança ou a necessidade de ajuste das assinaturas de eventos para limitar o número de eventos potencialmente falsos que estão sendo relatados.
- **Sensor** - Este é o agente que relata o evento. Os sensores disponíveis e seus números de identificação podem ser encontrados na guia Status do agente do painel, que aparece abaixo da janela de eventos à esquerda. Esses números também são usados na coluna ID de alerta. No painel Status do Agente, podemos ver que os sensores OSSEC, pcap e Snort estão reportando ao Sguil. Além disso, podemos ver os nomes de host padrão para esses sensores, que inclui a interface de monitoramento. Observe que cada interface de monitoramento tem dados pcap e Snort associados a ele.
- **ID de alerta** - Este número de duas partes representa o sensor que relatou o problema e o número de evento desse sensor. Podemos ver a partir da figura que o maior número de eventos que são exibidos são do sensor OSSEC (1). O sensor OSSEC relatou oito conjuntos de eventos correlacionados. Destes eventos, 232 foram relatados com ID de evento 1.24.
- **Data/Hora** - Este é o carimbo de data/hora do evento. No caso de eventos correlacionados, é o carimbo de data/hora do primeiro evento.
- **Mensagem de Evento** - Este é o texto de identificação para o evento. Isso é configurado na regra que disparou o alerta. A regra associada pode ser visualizada no painel direito, logo acima dos dados do pacote. Para exibir a regra, a caixa de seleção **Mostrar regra** deve ser marcada.

Dependendo da tecnologia de segurança, os alertas podem ser gerados com base em regras, assinaturas, anomalias ou comportamentos. Não importa como eles são gerados, as condições que acionam um alerta devem ser predefinidas de alguma maneira.
### Regras e Alertas

Os alertas podem vir de várias fontes:

- **NIDS** - Snort, Zeek e Suricata
- **HIDS** - OSSEC, Wazuh
- **Gerenciamento e monitoramento de ativos** - Sistema de detecção de ativos passivos (PADS)
- **Transações HTTP, DNS e TCP** - Registradas pelo Zeek e pcaps
- **Mensagens do Syslog*** - Várias fontes

As informações encontradas nos alertas que são exibidos no Sguil serão diferentes no formato de mensagem porque elas vêm de fontes diferentes.

O alerta Sguil na figura foi acionado por uma regra que foi configurada no Snort. É importante que o analista de segurança cibernética seja capaz de interpretar o que acionou o alerta para que o alerta possa ser investigado. Por esse motivo, o analista de segurança cibernética deve entender os componentes das regras do Snort, que são uma das principais fontes de alertas em Security Onion.![[Pasted image 20250206232453.png]]

### Estrutura de Regra Snort

As regras de Snort consistem em duas seções, como mostrado na figura: o cabeçalho da regra e as opções da regra. O cabeçalho da regra contém a ação, o protocolo, os endereços IP de origem e destino e as máscaras de rede e as informações da porta de origem e destino. A seção Opções de regra contém mensagens de alerta e informações sobre quais partes do pacote devem ser inspecionadas para determinar se a ação da regra deve ser executada. A localização da regra às vezes é adicionada pelo Sguil. Local da Regra é o caminho para o arquivo que contém a regra e o número da linha em que a regra aparece para que ela possa ser encontrada e modificada, ou eliminada, se necessário.
### Estrutura da regra Snort e informações fornecidas pelo SGUI
![[Pasted image 20250206232717.png]]

**O cabeçalho da regra**

O cabeçalho da regra contém a ação, o protocolo, o endereçamento e as informações da porta, conforme mostrado na figura. Além disso, a direção do fluxo que acionou o alerta é indicada. A estrutura da parte do cabeçalho é consistente entre as regras de alerta Snort.

O Snort pode ser configurado para usar variáveis para representar endereços IP internos e externos. Essas variáveis, **$HOME_NET** e **$EXTERNAL_NET**, aparecem nas regras Snort. Eles simplificam a criação de regras, eliminando a necessidade de especificar endereços e máscaras específicos para cada regra. Os valores dessas variáveis são configurados no **snort.conf** arquivo. O Snort também permite que endereços IP individuais, blocos de endereços ou listas de ambos sejam especificados em regras. Os intervalos de portas podem ser especificados separando os valores superior e inferior do intervalo com dois pontos. Outros operadores também estão disponíveis.
### Estrutura do cabeçalho da regra Snort
![[Pasted image 20250206232942.png]]

**As Opções de Regra**

A estrutura da seção de opções da regra é variável. É a parte da regra que está entre parênteses, como mostrado na figura. Ele contém a mensagem de texto que identifica o alerta. Ele também contém metadados sobre o alerta, como um URL que fornece informações de referência para o alerta. Outras informações podem ser incluídas, como o tipo de regra e um identificador numérico exclusivo para a regra e a revisão da regra. Além disso, os recursos da carga do pacote podem ser especificados nas opções. O manual de usuários do Snort, que pode ser encontrado na internet, fornece detalhes sobre regras e como criá-las.

Mensagens de regra de snifar podem incluir a origem da regra. Três fontes comuns para as regras do Snort são:

- **GPL** - Regras mais antigas do Snort que foram criadas pelo Sourcefire e distribuídas sob uma GPLv2. O conjunto de regras GPL não é certificado pelo Cisco Talos. Inclui Snort SIDs 3464 e abaixo. O conjunto de regras GPL pode ser baixado do site do Snort e está incluído no Security Onion.
- **ET** - Regras Snort de ameaças emergentes. Emerging Threats é um ponto de coleta para regras Snort de várias fontes. As regras ET são de código aberto sob uma licença BSD. O conjunto de regras ET contém regras de várias categorias. Um conjunto de regras ET está incluído com Security Onion. Emerging Threats é uma divisão da Proofpoint, Inc.
- **VRT** - Essas regras estão imediatamente disponíveis para assinantes e são liberadas para usuários registrados 30 dias após sua criação, com algumas limitações. Eles agora são criados e mantidos pelo Cisco Talos.

As regras podem ser baixadas automaticamente do [Snort.org](http://Snort.org) usando o utilitário de gerenciamento de regras PulledPork que está incluído com o Security Onion.

Alertas que não são gerados pelas regras do Snort são identificados pelas tags OSSEC ou PADS, entre outras. Além disso, regras locais personalizadas podem ser criadas.
### Estrutura de Opções de Regras Snort
![[Pasted image 20250206233118.png]]
# Visão geral da avaliação de alerta

### A necessidade de avaliação de alerta

O cenário de ameaças está mudando constantemente à medida que novas vulnerabilidades são descobertas e novas ameaças evoluem. À medida que as necessidades do usuário e organizacional mudam, a superfície do ataque também. Os atores de ameaças aprenderam a variar rapidamente os recursos de suas explorações para evitar a detecção.

É impossível projetar medidas para evitar todas as façanhas. As explorações irão inevitavelmente fugir às medidas de protecção, por mais sofisticadas que sejam. Às vezes, o melhor que pode ser feito é detectar exploits durante ou depois de terem ocorrido. As regras de detecção devem ser excessivamente conservadoras. Em outras palavras, é melhor ter alertas que às vezes são gerados por tráfego inocente, do que ter regras que perdem tráfego malicioso. Por esse motivo, é necessário que analistas qualificados de segurança cibernética investiguem alertas para determinar se uma exploração realmente ocorreu.

Os analistas de segurança cibernética de nível 1 costumam trabalhar em filas de alertas em uma ferramenta como Sguil, girando para ferramentas como Zeek, Wireshark e Kibana para verificar se um alerta representa uma exploração real.
### Ferramentas primárias para o analista de segurança cibernética de nível 1
![[Pasted image 20250206235601.png]]
### Avaliação de alertas

Os incidentes de segurança são classificados usando um esquema emprestado de diagnósticos médicos. Este esquema de classificação é usado para orientar ações e avaliar procedimentos de diagnóstico. Por exemplo, quando um paciente visita um médico para um exame de rotina, uma das tarefas do médico é determinar se o paciente está doente. Um dos resultados pode ser uma determinação correta de que a doença está presente e o paciente está doente. Outro resultado pode ser que não há doença e o paciente é saudável.

A preocupação é que o diagnóstico pode ser preciso, ou verdadeiro, ou impreciso, ou falso. Por exemplo, o médico pode perder os sinais de doença e fazer a determinação incorreta de que o paciente está bem quando está de fato doente. Outro erro possível é decidir que um paciente está doente quando esse paciente é de fato saudável. Os falsos diagnósticos são caros ou perigosos.

Na análise de segurança de rede, o analista de segurança cibernética é apresentado com um alerta. Isso é semelhante a um paciente indo ao médico e dizendo: “Estou doente”. O analista de segurança cibernética, como o médico, precisa determinar se esse diagnóstico é verdadeiro. O analista de segurança cibernética pergunta: “O sistema diz que ocorreu uma exploração. Isso é verdade?”

Os alertas podem ser classificados da seguinte forma:

- **Verdadeiro Positivo**: O alerta foi verificado como sendo um incidente de segurança real.
- **Falso Positivo**: O alerta não indica um incidente de segurança real. A atividade benigna que resulta em um falso positivo é às vezes referida como um gatilho benigno.

Uma situação alternativa é que um alerta não foi gerado. A ausência de um alerta pode ser classificada como:

- **Verdadeiro Negativo**: Nenhum incidente de segurança ocorreu. A atividade é benigna.
- **Falso Negativo**: Ocorreu um incidente não detectado.
![[Pasted image 20250206235740.png]]

**Verdadeiros positivos** são o tipo de alerta desejado. Eles significam que as regras que geram alertas funcionaram corretamente.

**Falsos positivos não** são desejáveis. Embora eles não indiquem que ocorreu uma exploração não detectada, eles são caros porque os analistas de segurança cibernética devem investigar alarmes falsos; portanto, o tempo é retirado da investigação de alertas que indicam verdadeiras explorações.

**Verdadeiros negativos** são desejáveis. Eles indicam que o tráfego normal benigno é corretamente ignorado e alertas errôneos não estão sendo emitidos.

**Falsos negativos** são perigosos. Eles indicam que as explorações não estão sendo detectadas pelos sistemas de segurança que estão em vigor. Esses incidentes podem passar despercebidos por um longo período de tempo, e a perda e danos contínuos de dados podem resultar.

Eventos benignos são aqueles que não devem acionar alertas. Os eventos benignos em excesso indicam que algumas regras ou outros detectores precisam ser melhorados ou eliminados.

Quando os verdadeiros positivos são suspeitos, um analista de segurança cibernética às vezes é obrigado a escalar o alerta para um nível mais alto para investigação. O investigador avançará com a investigação, a fim de confirmar o incidente e identificar qualquer dano potencial que possa ter sido causado. Essas informações serão usadas por mais funcionários de segurança sênior que trabalharão para isolar os danos, solucionar vulnerabilidades, mitigar a ameaça e lidar com os requisitos de relatórios.

Um analista de segurança cibernética também pode ser responsável por informar o pessoal de segurança de que falsos positivos estão ocorrendo na medida em que o tempo do analista de segurança cibernética é seriamente afetado. Esta situação indica que os sistemas de monitoramento de segurança precisam ser ajustados para se tornarem mais eficientes. Alterações legítimas na configuração da rede ou nas regras de detecção recém-baixadas podem resultar em um pico repentino de falsos positivos também.

Falsos negativos podem ser descobertos bem depois de uma exploração ter ocorrido. Isso pode acontecer por meio da análise de segurança retrospectiva (RSA). A RSA pode ocorrer quando regras recém-obtidas ou outras informações sobre ameaças são aplicadas a dados de segurança de rede arquivados. Por esse motivo, é importante monitorar as informações sobre ameaças para conhecer novas vulnerabilidades e explorações e avaliar a probabilidade de que a rede estava vulnerável a elas em algum momento no passado. Além disso, a exploração deve ser avaliada em relação aos danos potenciais que a empresa pode sofrer. Pode determinar-se que a adição de novas técnicas de atenuação é suficiente ou que deve ser realizada uma análise mais pormenorizada.
### Análise Determinística e Análise Probabilística

Técnicas estatísticas podem ser usadas para avaliar o risco de que as explorações serão bem-sucedidas em uma determinada rede. Esse tipo de análise pode ajudar os tomadores de decisão a avaliar melhor o custo de mitigar uma ameaça com os danos que uma exploração poderia causar.

Duas abordagens gerais utilizadas para isso são a análise determinística e probabilística. A análise determinística avalia o risco com base no que é conhecido sobre uma vulnerabilidade. Ele pressupõe que, para que uma exploração seja bem-sucedida, todas as etapas anteriores do processo de exploração também devem ser bem-sucedidas. Este tipo de análise de risco só pode descrever o pior caso. No entanto, muitos atores ameaçadores, embora conscientes do processo para realizar uma exploração, podem não ter conhecimento ou experiência para concluir com sucesso cada passo no caminho para uma exploração bem-sucedida. Isso pode dar ao analista de segurança cibernética a oportunidade de detectar a exploração e impedi-la antes que ela prossiga.

A análise probabilística estima o sucesso potencial de uma exploração, estimando a probabilidade de que, se uma etapa de uma exploração tiver sido concluída com sucesso, a próxima etapa também será bem-sucedida. A análise probabilística é especialmente útil na análise de segurança de rede em tempo real em que inúmeras variáveis estão em jogo e um determinado ator de ameaça pode tomar decisões desconhecidas à medida que uma exploração é perseguida.

A análise probabilística baseia-se em técnicas estatísticas que são projetadas para estimar a probabilidade de que um evento ocorrerá com base na probabilidade de ocorrerem eventos anteriores. Usando esse tipo de análise, os caminhos mais prováveis que uma exploração tomará podem ser estimados e a atenção do pessoal de segurança pode ser focada em prevenir ou detectar a exploração mais provável.

Em uma análise determinística, toda a informação para realizar uma exploração é assumida como sendo conhecida. As características da exploração, como o uso de números de porta específicos, são conhecidas de outras instâncias da exploração ou porque portas padronizadas estão em uso. Na análise probabilística, presume-se que os números de porta que serão utilizados só podem ser previstos com algum grau de confiança. Nessa situação, uma exploração que usa números de porta dinâmicos, por exemplo, não pode ser analisada deterministicamente. Tais explorações foram otimizadas para evitar a detecção por firewalls que usam regras estáticas.

As duas abordagens são resumidas a seguir.

- **Análise Determinística** - Para que uma exploração seja bem-sucedida, todas as etapas anteriores da exploração também devem ser bem-sucedidas. O analista de segurança cibernética conhece as etapas para uma exploração bem-sucedida.
- **Análise Probabilística** - Técnicas estatísticas são usadas para determinar a probabilidade de que uma exploração bem-sucedida ocorrerá com base na probabilidade de que cada etapa da exploração seja bem-sucedida.