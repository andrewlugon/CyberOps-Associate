
A defesa contra as ameaças atuais requer uma abordagem formalizada, estruturada e disciplinada. Normalmente, as organizações usam os serviços de profissionais em um Centro de Operações de Segurança (SOC). Os SOCs oferecem uma ampla gama de serviços, desde monitoramento e gerenciamento até soluções abrangentes de ameaças e segurança hospedada que podem ser personalizadas para atender às necessidades dos clientes. Os SOCs podem ser totalmente internos, de propriedade e operados por uma empresa, ou elementos de um SOC podem ser contratados a fornecedores de segurança, como os [Managed Security Services] ([http://www.cisco.com/c/en/us/products/security/managed-services.html](http://www.cisco.com/c/en/us/products/security/managed-services.html)) da Cisco.

### Pessoas no SOC

s funções de trabalho em um SOC estão evoluindo rapidamente. Tradicionalmente, os SOCs atribuem funções de trabalho por níveis, de acordo com a experiência e as responsabilidades necessárias para cada um. Os trabalhos de primeiro nível são mais de nível inicial, enquanto os empregos de terceiro nível exigem ampla experiência.

- **Analista de Alerta de Nível 1** - Esses profissionais monitoram alertas recebidos, verificam se um incidente verdadeiro ocorreu e encaminham tickets para o Nível 2, se necessário.
- **Respondente a Incidentes de Nível 2** - Esses profissionais são responsáveis pela investigação aprofundada de incidentes e aconselham a correção ou a ação a serem tomadas.
- **Caçador de Ameaças de Nível 3** - Esses profissionais possuem habilidades de nível especializado em rede, endpoint, inteligência contra ameaças e engenharia reversa de malware. Eles são especialistas em rastrear os processos do malware para determinar seu impacto e como ele pode ser removido. Eles também estão profundamente envolvidos na busca de ameaças potenciais e na implementação de ferramentas de detecção de ameaças. Os caçadores de ameaças buscam ameaças cibernéticas presentes na rede, mas ainda não foram detectadas.
- **Gerente SOC** - Este profissional gerencia todos os recursos do SOC e serve como ponto de contato para a organização ou cliente maior.
![[Pasted image 20241210211305.png]]

### Processo no SOC

O dia de um analista de segurança cibernética geralmente começa com o monitoramento de filas de alertas de segurança. Um sistema de emissão de tíquetes é freqüentemente usado para atribuir alertas a uma fila para que um analista investigue. Como o software que gera alertas pode acionar alarmes falsos, um trabalho do analista de segurança cibernética pode ser verificar se um alerta representa um verdadeiro incidente de segurança. Quando a verificação for estabelecida, o incidente pode ser encaminhado aos investigadores ou a outro pessoal de segurança para ser tratado. Caso contrário, o alerta pode ser descartado como um alarme falso.

Se um tíquete não puder ser resolvido, o Analista de segurança cibernética encaminhará o tíquete para um Respondente de Incidente de Nível 2 para uma investigação e correção mais aprofundadas. Se o Respondente a Incidentes não puder resolver o tíquete, ele será encaminhado para o pessoal do Nível 3 com conhecimento profundo e habilidades de caça a ameaças.

![[Pasted image 20241210211412.png]]

### Tecnologias no SOC - SIEM

um SOC precisa de um SIEM (Security Information and Event Management System, sistema de gerenciamento de eventos e informações de segurança) ou seu equivalente. O SIEM faz sentido de todos os dados gerados por firewalls, dispositivos de rede, sistemas de detecção de intrusões e outros dispositivos.

Os sistemas SIEM são usados para coletar e filtrar dados, detectar e classificar ameaças e analisar e investigar ameaças. Os sistemas SIEM também podem gerenciar recursos para implementar medidas preventivas e lidar com ameaças futuras. As tecnologias SOC incluem um ou mais dos seguintes:

- Coleta, correlação e análise de eventos
- Monitoramento da segurança
- Controle de segurança
- Gerenciamento de logs
- Avaliação de vulnerabilidade
- Controle de vulnerabilidades
- Inteligência de ameaças

### Tecnologias no SOC - SOAR

SIEM e orquestração de segurança, automação e resposta (SOAR) são frequentemente emparelhados, pois possuem recursos que se complementam.

Grandes equipes de operações de segurança (SecOps) usam ambas as tecnologias para otimizar seu SOC. Estima-se que 15% das organizações com uma equipe de segurança de mais de cinco pessoas utilizarão o SOAR até o final de 2020.

As plataformas SOAR são semelhantes às SIEMs na medida em que agregam, correlacionam e analisam alertas. No entanto, a tecnologia SOAR vai um passo além integrando inteligência contra ameaças e automatizando os fluxos de trabalho de investigação e resposta de incidentes com base em manuais desenvolvidos pela equipe de segurança.

![[Pasted image 20241210211545.png]]

Plataformas de segurança SOAR:

- Reunir dados de alarme de cada componente do sistema.
- Fornecer ferramentas que permitam que os casos sejam pesquisados, avaliados e investigados.
- Enfatizar a integração como um meio de automatizar fluxos de trabalho complexos de resposta a incidentes que permitem respostas mais rápidas e estratégias de defesa adaptativas.
- Incluir playbooks predefinidos que permitem a resposta automática a ameaças específicas. Os playbooks podem ser iniciados automaticamente com base em regras predefinidas ou podem ser acionados pelo pessoal de segurança.

SOAR enfatiza ferramentas de integração e automação de fluxos de trabalho SOC. Ele orquestra muitos processos manuais, como a investigação de alertas de segurança, que exigem apenas intervenção humana quando necessário. Isso libera o pessoal de segurança para lidar com questões mais urgentes e investigação de ponta e remediação de ameaças. A futura adoção de plataformas SOAR sofisticadas retornará as operações SOC e as funções de trabalho.

Os sistemas SIEM produzem necessariamente mais alertas do que a maioria das equipes de SECops pode investigar de forma realista, a fim de capturar de forma conservadora o maior número possível de explorações potenciais. A SOAR processará muitos desses alertas automaticamente e permitirá que o pessoal de segurança se concentre em explorações mais complexas e potencialmente prejudiciais.

### Métricas SOC

Um SOC é extremamente importante para a segurança de uma organização. Independentemente de o SOC ser interno a uma organização ou fornecer serviços a várias organizações, é importante entender o quão bem o SOC está funcionando para que possam ser feitas melhorias nas pessoas, processos e tecnologias que compõem o SOC.

Muitas métricas ou indicadores chave de desempenho (KPI) podem ser projetadas para medir diferentes aspectos específicos do desempenho do SOC. No entanto, cinco métricas são comumente usadas como métricas SOC. Observe, no entanto, que as métricas que descrevem o desempenho geral freqüentemente não apresentam uma imagem precisa da operação SOC devido à diversidade de ameaças à segurança cibernética. Várias métricas comuns compiladas pelos gerentes de SOC são:

- **Tempo de permanência** — o período de tempo que os atores da ameaça têm acesso a uma rede antes de serem detectados e seu acesso é interrompido.
- **Tempo médio para detectar (MTTD)** — o tempo médio que o pessoal do SOC leva para identificar incidentes de segurança válidos ocorreu na rede.
- **Tempo médio para responder (MTTR)** — o tempo médio necessário para parar e corrigir um incidente de segurança.
- **Tempo médio para conter (MTTC)** — o tempo necessário para impedir que o incidente cause mais danos aos sistemas ou dados.
- **Tempo de controle** — o tempo necessário para impedir a propagação de malware na rede.

### Segurança corporativa e gerenciada

Para redes de médio e grande porte, a organização se beneficiará com a implementação de um SOC de nível empresarial. O SOC pode ser uma solução interna completa. No entanto, muitas organizações maiores terceirizarão pelo menos parte das operações SOC para um provedor de soluções de segurança.

A Cisco tem uma equipe de especialistas que ajudam a garantir a resolução de incidentes oportuna e precisa. A Cisco oferece uma ampla variedade de recursos de resposta, preparação e gerenciamento a incidentes, incluindo:

- Serviço Cisco Smart Net Total Care para Resolução Rápida de Problemas;
- Equipe de resposta a incidentes de segurança do produto (PSIRT) da Cisco;
- Equipe de resposta a incidentes de segurança de computadores da Cisco (CSIRT);
- Serviços Gerenciados Cisco;
- Operações Táticas Cisco (TacOps);
- Programa de Segurança Física e Segurança da Cisco.

### Segurança versus disponibilidade

A maioria das redes empresariais deve estar em funcionamento o tempo todo. A equipe de segurança entende que, para que a organização cumpra suas prioridades, a disponibilidade da rede deve ser preservada.

Cada empresa ou setor tem uma tolerância limitada para o tempo de inatividade da rede. Essa tolerância é geralmente baseada em uma comparação do custo do tempo de inatividade em relação ao custo de garantia contra o tempo de inatividade. Por exemplo, em uma pequena empresa de varejo com apenas um local, pode ser tolerável ter um roteador como um único ponto de falha. No entanto, se uma grande parte das vendas dessa empresa for de compradores on-line, o proprietário pode decidir fornecer um nível de redundância para garantir que uma conexão esteja sempre disponível.

O tempo de atividade preferencial geralmente é medido no número de minutos de inatividade em um ano, conforme mostrado na tabela. Por exemplo, um tempo de atividade de “cinco noves” significa que a rede está acima de 99,999% do tempo ou inativa por não mais de 5 minutos por ano. “Quatro noves” seria um tempo de inatividade de 53 minutos por ano.

![[Pasted image 20241210211830.png]]

No entanto, a segurança não pode ser tão forte que interfira com as necessidades dos funcionários ou funções empresariais. É sempre um tradeoff entre forte segurança e permitir um funcionamento eficiente dos negócios.