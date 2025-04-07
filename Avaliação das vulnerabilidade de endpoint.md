# Perfil de rede e servidor

### Perfil de rede

Para detectar incidentes de segurança graves, é importante compreender, caracterizar e analisar informações sobre o funcionamento normal da rede. Todas as redes, servidores e hosts exibem um comportamento típico para um determinado ponto no tempo. A criação de perfis de rede e dispositivo pode fornecer uma linha de base estatística que serve como ponto de referência. Desvios inexplicáveis em relação à linha de base podem indicar um compromisso.

Deve-se ter cuidado ao capturar dados de linha de base para que todas as operações normais de rede sejam incluídas na linha de base. Além disso, é importante que a linha de base seja atual. Não deve incluir dados de desempenho da rede que não façam mais parte do funcionamento normal. Por exemplo, aumentos na utilização da rede durante operações periódicas de backup do servidor fazem parte do funcionamento normal da rede e devem fazer parte dos dados da linha de base. No entanto, a medição do tráfego que corresponde ao acesso externo a um servidor interno que foi movido para a nuvem não seria. Um meio de capturar apenas o período certo para medição de linha de base é conhecido como detecção de anomalias de janela deslizante. Ele define uma janela que é mais representativa da operação de rede e exclui dados que estão desatualizados. Esse processo continua com medições repetidas da linha de base para garantir que as estatísticas de medição da linha de base retratem a operação da rede com a máxima precisão.

O aumento da utilização de links WAN em momentos incomuns pode indicar uma violação de rede e uma extracção de dados. Os hosts que começam a acessar servidores obscuros da Internet, resolvem domínios obtidos por meio de DNS dinâmico ou usam protocolos ou serviços que não são necessários para o usuário do sistema também podem indicar comprometimento. Desvios no comportamento da rede são difíceis de detectar se o comportamento normal não é conhecido.

Ferramentas como NetFlow e Wireshark podem ser usadas para caracterizar características normais de tráfego de rede. Como as organizações podem fazer demandas diferentes em suas redes dependendo da hora do dia ou do dia do ano, a linha de base da rede deve ser realizada durante um período prolongado. A figura exibe algumas perguntas a serem feitas ao estabelecer uma linha de base de rede.![[Pasted image 20250201153826.png]]

A tabela lista elementos importantes do perfil de rede.
![[Pasted image 20250201153902.png]]
Além disso, um perfil dos tipos de tráfego que normalmente entram e saem da rede é uma ferramenta importante para compreender o comportamento da rede. O malware pode usar portas incomuns que podem não ser vistas normalmente durante a operação normal da rede. O tráfego de host para host é outra métrica importante. A maioria dos clientes de rede se comunica diretamente com servidores, portanto, um aumento do tráfego entre clientes pode indicar que o malware está se espalhando lateralmente pela rede.

Finalmente, alterações no comportamento do usuário, conforme revelado pelo AAA, logs do servidor ou um sistema de criação de perfil do usuário, como o Cisco Identity Services Engine (ISE), é outro indicador valioso. Saber como os usuários individuais normalmente usam a rede leva à detecção de potencial comprometimento das contas de usuário. Um usuário que de repente começa a fazer login na rede em momentos estranhos a partir de um local remoto deve gerar alarmes se esse comportamento for um desvio de uma norma conhecida.
### Perfil de servidor

A definição de perfil do servidor é usada para estabelecer o estado operacional aceito dos servidores. Um perfil de servidor é uma linha de base de segurança para um determinado servidor. Estabelece os parâmetros de rede, usuário e aplicativo que são aceitos para um servidor específico.

Para estabelecer um perfil de servidor, é importante entender a função que um servidor se destina a executar em uma rede. A partir daí, vários parâmetros operacionais e de uso podem ser definidos e documentados.

A tabela lista elementos de um perfil de servidor.![[Pasted image 20250201154024.png]]

### Detecção de anomalias de rede

O comportamento da rede é descrito por uma grande quantidade de dados diversos, como os recursos do fluxo de pacotes, os recursos dos próprios pacotes e a telemetria de várias fontes. Uma abordagem para a detecção de ataques de rede é a análise desses dados diversos e não estruturados usando técnicas de análise de Big Data. Isso é conhecido como análise de comportamento de rede (NBA).

Isto implica a utilização de técnicas sofisticadas de aprendizagem estatística e de máquina para comparar as linhas de base de desempenho normais com o desempenho da rede num determinado momento. Desvios significativos podem ser indicadores de compromisso. Além disso, o comportamento da rede pode ser analisado quanto a comportamentos de rede conhecidos que indicam comprometimento.

A detecção de anomalias pode reconhecer o tráfego de rede causado pela atividade de worm que exibe o comportamento de varredura. A detecção de anomalias também pode identificar hosts infectados na rede que estão verificando outros hosts vulneráveis.

A figura ilustra uma versão simplificada de um algoritmo projetado para detectar uma condição incomum nos roteadores de fronteira de uma empresa.![[Pasted image 20250201154140.png]]

Por exemplo, o analista de segurança cibernética poderia fornecer os seguintes valores:

- X = 5
- Y = 100
- Z = 30
- N = 500

Agora, o algoritmo pode ser interpretado como: a cada 5 minutos, obter uma amostragem de 1/100 dos fluxos durante o segundo 30. Se o número de fluxos for maior que 500, gere um alarme. Se o número de fluxos for inferior a 500, não faça nada. Este é um exemplo simples de usar um perfil de tráfego para identificar o potencial de perda de dados.

Além de abordagens estatísticas e comportamentais para detecção de anomalias é a detecção de anomalias baseada em regras. A detecção baseada em regras analisa pacotes decodificados para ataques com base em padrões predefinidos.
### Teste de vulnerabilidade de rede

A maioria das organizações conecta-se às redes públicas de alguma forma devido à necessidade de acessar a internet. Essas organizações também devem fornecer serviços voltados para a internet de vários tipos ao público. Devido ao grande número de potenciais vulnerabilidades e ao fato de que novas vulnerabilidades podem ser criadas dentro de uma rede da organização e seus serviços voltados para a Internet, testes periódicos de segurança são essenciais.

A tabela lista vários tipos de testes que podem ser realizados.![[Pasted image 20250201154314.png]]

A tabela lista exemplos de atividades e ferramentas que são usadas em testes de vulnerabilidade.![[Pasted image 20250201154334.png]]

# Sistema de pontuação de vulnerabilidade comum (CVSS)

### Visão geral do CVSS

O Common Vulnerability Scoring System (CVSS) é uma ferramenta de avaliação de risco projetada para transmitir os atributos comuns e a gravidade das vulnerabilidades em sistemas de hardware e software de computador. A terceira revisão, CVSS 3.0, é uma estrutura aberta e neutra do fornecedor, padrão do setor, para ponderar os riscos de uma vulnerabilidade usando uma variedade de métricas. Esses pesos combinam-se para fornecer uma pontuação do risco inerente a uma vulnerabilidade. A pontuação numérica pode ser usada para determinar a urgência da vulnerabilidade e a prioridade de abordá-la. Os benefícios do CVSS podem ser resumidos da seguinte forma:

- Ele fornece pontuações padronizadas de vulnerabilidade que devem ser significativas em todas as organizações.
- Ele fornece uma estrutura aberta com o significado de cada métrica abertamente disponível para todos os usuários.
- Ele ajuda a priorizar o risco de uma forma que seja significativa para organizações individuais.

O Fórum de Equipes de Resposta a Incidentes e Segurança (FIRST) foi designado como guardião do CVSS para promover sua adoção globalmente. O padrão Versão 3 foi desenvolvido com contribuições da Cisco e de outros parceiros do setor. A versão 3.1 foi lançada em junho de 2019.
### Grupos métricos CVSS

Antes de realizar uma avaliação do CVSS, é importante conhecer os termos fundamentais utilizados no instrumento de avaliação.

Muitas das métricas abordam o papel do que o CVSS chama de autoridade. Uma autoridade é uma entidade de computador, como um banco de dados, sistema operacional ou caixa de proteção virtual, que concede e gerencia acesso e privilégios aos usuários.![[Pasted image 20250201154643.png]]

**Grupo de métricas base**

Isso representa as características de uma vulnerabilidade que são constantes ao longo do tempo e em contextos. Ele tem duas classes de métricas:

- **Explorabilidade** \ - Esses são recursos da exploração, como vetor, complexidade e interação do usuário exigidas pela exploração.
- **Métricas de impacto** - Os impactos da exploração estão enraizados na tríade de confidencialidade, integridade e disponibilidade da CIA.

**Grupo métrico temporal**

Isso mede as características de uma vulnerabilidade que pode mudar ao longo do tempo, mas não em ambientes de usuário. Ao longo do tempo, a gravidade de uma vulnerabilidade mudará à medida que for detectada e serão desenvolvidas medidas para combatê-la. A gravidade de uma nova vulnerabilidade pode ser alta, mas diminuirá à medida que patches, assinaturas e outras contramedidas forem desenvolvidas.

**Grupo métrio ambiental**

Isso mede os aspectos de uma vulnerabilidade que estão enraizados no ambiente de uma organização específica. Essas métricas ajudam a classificar as consequências dentro de uma organização e permitem o ajuste de métricas menos relevantes para o que uma organização faz.

### Grupo Métrico Base CVSS

A tabela lista os critérios para as métricas de Explorabilidade do Grupo de Métricas Base.
![[Pasted image 20250201154900.png]]

As métricas de Impacto do Grupo Métrico Base aumentam com o grau ou conseqüência da perda devido ao componente afetado. A tabela lista os componentes de métrica de impacto.
![[Pasted image 20250201154934.png]]

### O Processo CVS

O CVSS Base Metrics Group foi projetado como uma forma de avaliar vulnerabilidades de segurança encontradas em sistemas de software e hardware. Ele descreve a gravidade de uma vulnerabilidade com base nas características de uma exploração bem-sucedida da vulnerabilidade. Os outros grupos de métricas modificam a pontuação de gravidade base, contabilizando como a classificação de gravidade base é afetada por fatores de tempo e ambientais.

O processo CVSS usa uma ferramenta chamada Calculadora CVSS v3.1.

A calculadora é como um questionário no qual são feitas escolhas que descrevem a vulnerabilidade para cada grupo de métricas. Depois que todas as escolhas são feitas, uma pontuação é gerada. O texto pop-up que explica cada métrica e valor métrico é exibido passando o mouse sobre cada um. As opções são feitas escolhendo um dos valores para a métrica. Apenas uma escolha pode ser feita por métrica.

A calculadora CVSS pode ser acessada na parte CVSS do site FIRST.

Um guia detalhado do usuário que define critérios métricos, exemplos de avaliações de vulnerabilidades comuns e a relação de valores métricos com a pontuação final está disponível para dar suporte ao processo.

Após a conclusão do grupo Métrica Base, a classificação de gravidade numérica é exibida.

Uma string vetorial também é criada que resume as escolhas feitas. Se outros grupos métricos forem concluídos, esses valores serão anexados à string vetorial. A string consiste na (s) inicial (s) para a métrica e um valor abreviado para o valor métrico selecionado separado por dois-pontos. Os pares de valor métrico são separados por barras. As strings vetoriais permitem que os resultados da avaliação sejam facilmente compartilhados e comparados.

A tabela lista a chave para o grupo Métrica Base.
![[Pasted image 20250201155102.png]]

Os valores para a cadeia de classificação de gravidade numérica **CVSS:3.1/AV:N/AC:L/PR:H/UI:N/S:U/C:L/I:L/A:N** são listados na tabela.
![[Pasted image 20250201155113.png]]

Para que uma pontuação seja calculada para os grupos de métricas Temporal ou Ambiental, o grupo Métrica Base deve primeiro ser concluído. Em seguida, os valores de métrica Temporal e Ambiental modificam os resultados da Métrica Base para fornecer uma pontuação geral. A interação das pontuações para os grupos métricos é mostrada na figura.
![[Pasted image 20250201155137.png]]

### Relatórios CVSS

Os intervalos de escores e o significado qualitativo correspondente são mostrados na tabela.
![[Pasted image 20250201155204.png]]
Frequentemente, as pontuações do grupo de métricas Base e Temporal serão fornecidas aos clientes pelo aplicativo ou fornecedor de segurança em cujo produto a vulnerabilidade foi descoberta. A organização afetada completa o grupo de métricas ambientais para adaptar a pontuação fornecida pelo fornecedor ao contexto local.

A pontuação resultante serve para orientar a organização afetada na alocação de recursos para resolver a vulnerabilidade. Quanto maior a classificação de gravidade, maior o impacto potencial de uma exploração e maior a urgência em abordar a vulnerabilidade. Embora não sejam tão precisos quanto os escores numéricos do CVSS, os rótulos qualitativos são muito úteis para se comunicar com os stakeholders que não conseguem se relacionar com os escores numéricos.

Em geral, qualquer vulnerabilidade que exceda 3.9 deve ser resolvida. Quanto maior o nível de classificação, maior a urgência para remediação.

### Outras fontes de informações sobre vulnerabilidades

Existem outras fontes importantes de informações sobre vulnerabilidades. Estes trabalham em conjunto com o CVSS para fornecer uma avaliação abrangente da gravidade da vulnerabilidade. Existem dois sistemas que operam nos Estados Unidos:

**Vulnerabilidades e exposições comuns (CVE)**

Este é um dicionário de nomes comuns, na forma de identificadores CVE, para vulnerabilidades conhecidas de segurança cibernética. O identificador CVE fornece uma maneira padrão de pesquisar uma referência a vulnerabilidades. Quando uma vulnerabilidade for identificada, identificadores CVE podem ser usados para acessar correções. Além disso, os serviços de inteligência contra ameaças usam identificadores CVE e aparecem em vários logs do sistema de segurança. O site Detalhes do CVE fornece uma ligação entre as pontuações do CVSS e as informações do CVE. Ele permite a navegação de registros de vulnerabilidade CVE por classificação de gravidade CVSS.

**National Vulnerability Database (NVD)**

Isso utiliza identificadores CVE e fornece informações adicionais sobre vulnerabilidades, como pontuações de ameaças CVSS, detalhes técnicos, entidades afetadas e recursos para investigação adicional. O banco de dados foi criado e é mantido pela agência do National Institute of Standards and Technology (NIST) do governo dos EUA.

# Gerenciamento Seguro de dispositivos
### Gerenciamento de risco

gerenciamento de riscos envolve a seleção e especificação de controles de segurança para uma organização. Faz parte de um programa contínuo de segurança da informação em toda a organização que envolve a gestão do risco para a organização ou para indivíduos associados à operação de um sistema.

A gestão de riscos é um processo contínuo, multi-passo, cíclico.
![[Pasted image 20250201181347.png]]
O risco é determinado como a relação entre ameaça, vulnerabilidade e a natureza da organização. Trata-se, em primeiro lugar, de responder às seguintes questões como parte de uma avaliação de risco:

- Quem são os atores que querem nos atacar?
- Quais vulnerabilidades os atores ameaçadores podem explorar?
- Como seríamos afetados por ataques?
- Qual é a probabilidade de que diferentes ataques ocorram?

A publicação especial 800-30 do NIST descreve a avaliação de risco como:

_... o processo de identificação, estimativa e priorização dos riscos de segurança das informações. A avaliação do risco requer uma análise cuidadosa das informações sobre ameaças e vulnerabilidades para determinar a extensão em que circunstâncias ou eventos podem afetar negativamente uma organização e a probabilidade de tais circunstâncias ou eventos ocorrerem._

A publicação completa está disponível para download no NIST.

Uma atividade obrigatória na avaliação de riscos é a identificação de ameaças e vulnerabilidades e a correspondência de ameaças com vulnerabilidades no que geralmente é chamado de emparelhamento de ameaças (T-V). Os pares T-V podem então ser usados como uma linha de base para indicar o risco antes de os controles de segurança serem implementados. Esta linha de base pode, então, ser comparada com avaliações de risco contínuas como meio de avaliar a eficácia da gestão do risco. Esta parte da avaliação de risco é referida como a determinação do perfil de risco inerente de uma organização.

Após a identificação dos riscos, eles podem ser pontuados ou ponderados como forma de priorizar estratégias de redução de risco. Por exemplo, as vulnerabilidades que se verificou terem correspondido a várias ameaças podem receber classificações mais altas. Além disso, os pares T-V que mapeiam para o maior impacto institucional também receberão ponderações mais elevadas.

A tabela lista as quatro formas potenciais de responder aos riscos identificados, com base em suas ponderações ou pontuações.![[Pasted image 20250201181528.png]]

### Gerenciamento de vulnerabilidades

De acordo com o NIST, o gerenciamento de vulnerabilidades é uma prática de segurança projetada para impedir proativamente a exploração de vulnerabilidades de TI existentes em uma organização. O resultado esperado é reduzir o tempo e o dinheiro gasto para lidar com vulnerabilidades e a exploração dessas vulnerabilidades. O gerenciamento proativo de vulnerabilidades de sistemas reduzirá ou eliminará o potencial de exploração e envolverá consideravelmente menos tempo e esforço do que responder após uma exploração ter ocorrido.

O gerenciamento de vulnerabilidades requer um meio robusto de identificar vulnerabilidades com base em boletins de segurança do fornecedor e em outros sistemas de informação, como o CVE. O pessoal de segurança deve ser competente para avaliar o impacto, se houver, das informações de vulnerabilidade recebidas. As soluções devem ser identificadas com meios eficazes de implementar e avaliar as consequências imprevistas das soluções implementadas. Finalmente, a solução deve ser testada para verificar se a vulnerabilidade foi eliminada.
![[Pasted image 20250201181821.png]]

**Descobrir**

Inventário de todos os ativos na rede e identifique os detalhes do host, incluindo sistemas operacionais e serviços abertos, para identificar vulnerabilidades. Desenvolva uma linha de base da rede. Identifique vulnerabilidades de segurança em um agendamento automatizado regular.

**Priorizar ativos**

Categorize os ativos em grupos ou unidades de negócios e atribua um valor comercial a grupos de ativos com base na sua importância às operações de negócios.

**Avaliação**

Determine um perfil de risco básico para eliminar riscos com base na importância, vulnerabilidade, ameaças e classificação de ativos.

**Relatório**

Meça o nível de risco comercial associado aos seus ativos de acordo com suas políticas de segurança. Documente um plano de segurança, monitore atividades suspeitas e descreva vulnerabilidades conhecidas.

**Reparar**

Priorize de acordo com o risco comercial e resolva vulnerabilidades por ordem de risco.

**Verificar**

Verifique se as ameaças foram eliminadas por meio de auditorias de acompanhamento.
### Gerenciamento de ativos

O gerenciamento de ativos envolve a implementação de sistemas que controlam a localização e a configuração de dispositivos e software em rede em uma empresa. Como parte de qualquer plano de gerenciamento de segurança, as organizações devem saber quais equipamentos acessam a rede, onde esse equipamento está dentro da empresa e logicamente na rede, e que software e dados esses sistemas armazenam ou podem acessar. O gerenciamento de ativos não apenas rastreia ativos corporativos e outros dispositivos autorizados, mas também pode ser usado para identificar dispositivos que não estão autorizados na rede.

O NIST especifica na publicação NISTIR 8011 Volume 2, os registros detalhados que devem ser mantidos para cada dispositivo relevante. O NIST descreve técnicas e ferramentas potenciais para operacionalizar um processo de gerenciamento de ativos:

- Detecção automatizada e inventário do estado real dos dispositivos
- Articulação do estado desejado para esses dispositivos usando políticas, planos e procedimentos no plano de segurança das informações da organização
- Identificação de ativos autorizados não conformes
- Remediação ou aceitação do estado do dispositivo, possível iteração da definição de estado desejado
- Repita o processo em intervalos regulares ou em curso

A figura fornece uma visão geral desse processo.
![[Pasted image 20250201182127.png]]

### Gerenciamento de dispositivos móveis (MDM)

O gerenciamento de dispositivos móveis (MDM), especialmente na era do BYOD, apresenta desafios especiais para a gestão de ativos. Os dispositivos móveis não podem ser controlados fisicamente nas instalações de uma organização. Elas podem ser perdidas, roubadas ou adulteradas, colocando em risco o acesso a dados e à rede. Parte de um plano MDM é agir quando os dispositivos deixam a custódia da parte responsável. As medidas que podem ser tomadas incluem desativar o dispositivo perdido, criptografar os dados no dispositivo e aprimorar o acesso ao dispositivo com medidas de autenticação mais robustas.

Devido à diversidade de dispositivos móveis, é possível que alguns dispositivos que serão usados na rede sejam inerentemente menos seguros do que outros. Os administradores de rede devem assumir que todos os dispositivos móveis não são confiáveis até que tenham sido adequadamente protegidos pela organização.

Os sistemas MDM, como o Cisco Meraki Systems Manager, permitem que o pessoal de segurança configure, monitore e atualize um conjunto muito diversificado de clientes móveis a partir da nuvem.
### Gerenciamento de configurações

O gerenciamento de configuração aborda o inventário e o controle das configurações de hardware e software dos sistemas. Configurações seguras de dispositivos reduzem o risco de segurança. Por exemplo, uma organização fornece muitos computadores e laptops para seus funcionários. Isso amplia a superfície de ataque para a organização, porque cada sistema pode ser vulnerável a explorações. Para gerenciar isso, a organização pode criar imagens de software de linha de base e configurações de hardware para cada tipo de máquina. Essas imagens podem incluir um pacote básico de software necessário, software de segurança de ponto de extremidade e políticas de segurança personalizadas que controlam o acesso do usuário a aspectos da configuração do sistema que poderiam ser tornados vulneráveis. As configurações de hardware podem especificar os tipos permitidos de interfaces de rede e os tipos permitidos de armazenamento externo.

O gerenciamento de configuração se estende à configuração de software e hardware de dispositivos de rede e servidores também. Conforme definido pelo NIST, gerenciamento de configuração:

_Compreende uma coleção de atividades focadas no estabelecimento e manutenção da integridade de produtos e sistemas, através do controle dos processos de inicialização, alteração e monitoramento das configurações desses produtos e sistemas._

A publicação especial NIST 800-128 sobre gerenciamento de configuração para segurança de rede está disponível para download no NIST.

Para dispositivos de interrede, estão disponíveis ferramentas de software que farão backup de configurações, detectam alterações nos arquivos de configuração e habilitam a alteração em massa de configurações em vários dispositivos.

Com o advento dos data centers em nuvem e da virtualização, o gerenciamento de vários servidores apresenta desafios especiais. Ferramentas como Puppet, Chef, Ansible e SaltStack permitem o gerenciamento eficiente de servidores usados na computação baseada em nuvem.
### Gerenciamento Corporativo de Patchs

O gerenciamento de patches está relacionado ao gerenciamento de vulnerabilidades. Vulnerabilidades aparecem frequentemente em sistemas operacionais e firmware críticos de cliente, servidor e dispositivo de rede. Software de aplicativos, especialmente aplicativos de Internet e estruturas como Acrobat, Flash e Java, também são freqüentemente descobertos como tendo vulnerabilidades. O gerenciamento de patches envolve todos os aspectos da aplicação de patches de software, incluindo a identificação de patches necessários, aquisição, distribuição, instalação e verificação de que o patch está instalado em todos os sistemas necessários. A instalação de patches é frequentemente a maneira mais eficaz de mitigar vulnerabilidades de software. Às vezes, eles são a única maneira de fazê-lo.

O gerenciamento de patches é exigido por algumas regulamentações de conformidade, como Sarbanes Oxley (SOX) e a Lei de Portabilidade e Responsabilidade de Seguros de Saúde (HIPAA). A falha na implementação de patches de forma sistemática e oportuna pode resultar em falhas de auditoria e penalidades por não conformidade. O gerenciamento de patches depende dos dados de gerenciamento de ativos para identificar sistemas que executam software que exigem patches. O software de gerenciamento de patches está disponível em empresas como SolarWinds e LANDesk. O Microsoft System Center Configuration Manager (SCCM) é uma ferramenta de nível empresarial para distribuição automatizada de patches para um grande número de estações de trabalho e servidores Microsoft Windows.
### técnicas de gerenciamento de patches

**Baseado em agente**

Isso requer que um agente de software esteja sendo executado em cada host a ser corrigido. O agente informa se o software vulnerável está instalado no host. O agente se comunica com o servidor de gerenciamento de patches, determina se existem patches que exigem instalação e instala os patches. O agente é executado com privilégios suficientes para permitir que ele instale os patches. As abordagens baseadas em agentes são os meios preferidos para a aplicação de patches em dispositivos móveis.
![[Pasted image 20250201182649.png]]

**Varredura sem agente**

Os servidores de gerenciamento de patches verificam a rede em busca de dispositivos que exigem patches. O servidor determina quais patches são necessários e instala esses patches nos clientes. Somente os dispositivos que estão em segmentos de rede digitalizados podem ser corrigidos dessa maneira. Isso pode ser um problema para dispositivos móveis.
![[Pasted image 20250201182724.png]]

**Monitoramento de rede passiva**

Os dispositivos que requerem aplicação de patches são identificados através do monitoramento do tráfego na rede. Essa abordagem só é eficaz para software que inclui informações de versão em seu tráfego de rede.![[Pasted image 20250201182758.png]]

# Sistemas de Gestão de Segurança da Informação

### Sistemas de gerenciamento de segurança

Um Sistema de Gerenciamento de Segurança da Informação (ISMS) consiste em uma estrutura de gerenciamento por meio da qual uma organização identifica, analisa e aborda os riscos de segurança da informação. Os ISMSS não são baseados em servidores ou dispositivos de segurança. Em vez disso, um ISM consiste em um conjunto de práticas que são sistematicamente aplicadas por uma organização para garantir a melhoria contínua da segurança da informação. Os ISMSS fornecem modelos conceituais que orientam as organizações no planejamento, implementação, controle e avaliação de programas de segurança da informação.

Os ISMSS são uma extensão natural do uso de modelos de negócios populares, como o Gerenciamento de Qualidade Total (TQM) e os Objetivos de Controle para a Informação e Tecnologias Relacionadas (COBIT), para o domínio da segurança cibernética.

Um ISMS é uma abordagem sistemática e multicamada para a segurança cibernética. A abordagem inclui pessoas, processos, tecnologias e as culturas em que interagem em um processo de gestão de riscos.

Um ISMS muitas vezes incorpora o framework “plan-do-check-act”, conhecido como o ciclo Deming, da TQM. É visto como uma elaboração sobre o componente processual do modelo de capacidade organizacional Povo-Process-Tecnologia-Cultura, como mostra a figura.![[Pasted image 20250201183301.png]]

### ISO-27001

ISO é a Organização Internacional de Padronização. Os padrões voluntários da ISO são internacionalmente aceitos e facilitam os negócios realizados entre as nações.

A ISO fez parceria com a Comissão Eletrotécnica Internacional (IEC) para desenvolver a série ISO/IEC 27000 de especificações para ISMSS, conforme mostrado na tabela.
![[Pasted image 20250201183338.png]]

A certificação ISO 27001 é uma especificação global de todo o setor para um ISM. A figura ilustra a relação das ações estipuladas pelo padrão com o ciclo plano-do-check-act.![[Pasted image 20250201183419.png]]

**Planejar**

- Entender os objetivos de negócios relevantes
- Definir escopo das atividades
- Acesse e gerencie o suporte
- Avaliar e definir o risco
- Realizar gerenciamento de ativos e avaliação de vulnerabilidades

**Certo**

- Criar e implementar um plano de gestão de riscos
- Estabelecer e aplicar políticas e procedimentos de gestão de riscos
- Treinar pessoal, alocar recursos

**Verificar**

- Monitorar a implementação
- Compilar relatórios
- Suporte a auditoria externa de certificação

**Aja**

- Auditoria contínua de processos
- Melhorar continuamente os processos
- Tomar medidas corretivas
- Tomar medidas preventivas

A certificação ISO-27001 significa que as políticas e procedimentos de segurança de uma organização foram verificados de forma independente para fornecer uma abordagem sistemática e proativa para gerenciar eficazmente os riscos de segurança para informações confidenciais do cliente.
### NIST Cybersecurity Framework

O NIST é muito eficaz na área de segurança cibernética, como vimos neste módulo. Mais padrões do NIST serão discutidos mais tarde no curso.

O NIST também desenvolveu a estrutura de segurança cibernética, que é semelhante às normas ISO/IEC 27000. A estrutura do NIST é um conjunto de padrões projetados para integrar padrões, diretrizes e práticas existentes para ajudar a gerenciar e reduzir melhor o risco de segurança cibernética. O quadro foi emitido pela primeira vez em fevereiro de 2014 e continua a ser desenvolvido.

O núcleo da estrutura consiste em um conjunto de atividades sugeridas para alcançar resultados específicos de segurança cibernética e referências exemplos de orientação para alcançar esses resultados. As funções principais, que são definidas na tabela, são divididas em categorias e subcategorias principais.
![[Pasted image 20250201183621.png]]

As principais categorias fornecem uma compreensão dos tipos de atividades e resultados relacionados a cada função, conforme mostrado na tabela seguinte.![[Pasted image 20250201183638.png]]

Organizações de muitos tipos estão usando o Framework de várias maneiras. Muitos acharam útil para aumentar a conscientização e se comunicar com as partes interessadas dentro de sua organização, incluindo a liderança executiva. O Framework também está melhorando as comunicações entre as organizações, permitindo que as expectativas de segurança cibernética sejam compartilhadas com parceiros de negócios, fornecedores e entre setores. Ao mapear o Framework para as abordagens atuais de gerenciamento de segurança cibernética, as organizações estão aprendendo e mostrando como elas correspondem aos padrões, diretrizes e práticas recomendadas do Framework. Algumas partes estão a utilizar o Quadro para conciliar a política interna com a legislação, a regulamentação e as melhores práticas da indústria. O Quadro também está sendo usado como uma ferramenta de planejamento estratégico para avaliar os riscos e as práticas atuais.

Pesquise na Internet para saber mais sobre o NIST Cybersecurity Framework.