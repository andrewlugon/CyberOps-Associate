### Ativos, vulnerabilidades, ameaças

Analistas de segurança cibernética devem se preparar para qualquer tipo de ataque. É seu trabalho proteger os ativos da rede da organização. Para fazer isso, os analistas de segurança cibernética devem primeiro identificar:

- **Ativos** - qualquer coisa de valor para uma organização que deve ser protegida, incluindo servidores, dispositivos de infraestrutura, dispositivos finais e o maior ativo, dados.
- **Vulnerabilidades** - Uma fraqueza em um sistema ou em seu design que pode ser explorada por um agente de ameaça.
- **Ameaças** - Qualquer perigo potencial para um ativo.

### Identificar ativos

medida que uma organização cresce, seus ativos também crescem. Considere o número de ativos que uma grande organização teria de proteger. Pode igualmente adquirir outros ativos através de fusões com outras empresas. O resultado é que muitas organizações só têm uma ideia geral dos ativos que precisam ser protegidos.

A coleta de todos os dispositivos e informações de propriedade ou gerenciadas pela organização são ativos. Os ativos constituem a superfície de ataque que os atores da ameaça podem atingir. Estes ativos devem ser inventariados e avaliados quanto ao nível de proteção necessário para impedir potenciais ataques.

O gerenciamento de ativos consiste em inventários de todos os ativos e, em seguida, desenvolver e implementar políticas e procedimentos para protegê-los. Essa tarefa pode ser assustadora, considerando que muitas organizações precisam proteger usuários e recursos internos, trabalhadores móveis e serviços virtuais e baseados em nuvem.

Além disso, as organizações precisam identificar onde os ativos de informações essenciais estão armazenados e como o acesso é obtido a essas informações. Os ativos de informação variam, assim como as ameaças contra eles. Por exemplo, uma empresa de varejo pode armazenar informações de cartão de crédito do cliente. Uma empresa de engenharia armazenará projetos e softwares sensíveis à concorrência. Um banco armazenará dados de clientes, informações de conta e outras informações financeiras confidenciais. Cada um desses ativos pode atrair diferentes atores de ameaças que têm diferentes níveis de habilidade e motivações.

### Identificar vulnerabilidades

A identificação de ameaças fornece a uma organização uma lista de prováveis ameaças para um ambiente específico. Ao identificar ameaças, é importante fazer várias perguntas:

- Quais são as possíveis vulnerabilidades de um sistema?
- Quem pode querer explorar essas vulnerabilidades para acessar ativos de informações específicos?
- Quais são as consequências se as vulnerabilidades do sistema forem exploradas e os ativos forem perdidos?

Por exemplo, consulte a figura.![[Pasted image 20250127205858.png]]

A identificação da ameaça para um sistema de banca electrónica incluiria:

- **Compromisso interno do sistema** - O atacante usa os servidores de e-banking expostos para invadir um sistema bancário interno.
- **Dados roubados do cliente** - Um atacante rouba os dados pessoais e financeiros dos clientes bancários do banco de dados do cliente.
- **Transações falsas de um servidor externo** - Um invasor altera o código do aplicativo de e-banking e faz transações personificando um usuário legítimo.
- **Transações falsas usando um PIN de cliente roubado ou cartão inteligente** - Um invasor rouba a identidade de um cliente e conclui transações mal-intencionadas da conta comprometida.
- **Ataque insider no sistema** - Um funcionário do banco encontra uma falha no sistema a partir do qual montar um ataque.
- **Erros de entrada de dados** - Um usuário insere dados incorretos ou faz solicitações de transação incorretas.
- **Destruição do data center** - Um evento cataclísmico danifica gravemente ou destrói o data center.

Identificar vulnerabilidades em uma rede requer uma compreensão dos aplicativos importantes que são usados, bem como das diferentes vulnerabilidades desse aplicativo e hardware. Isso pode exigir uma quantidade significativa de pesquisa por parte do administrador de rede.

### Identificar ameaças

As organizações devem usar uma abordagem de defesa profunda para identificar ameaças e proteger ativos vulneráveis. Essa abordagem usa várias camadas de segurança na borda da rede, na rede e nos pontos de extremidade da rede.

Para obter um exemplo, consulte a figura.![[Pasted image 20250127205947.png]]

figura exibe uma topologia simples de uma abordagem de defesa em profundidade:

- **Roteador de borda** - A primeira linha de defesa é conhecida como um roteador de borda (R1 na figura). O roteador de borda tem um conjunto de regras especificando qual tráfego ele permite ou nega. Ele passa todas as conexões que se destinam à LAN interna para o firewall.
- **Firewall** - A segunda linha de defesa é o firewall. O firewall é um dispositivo de ponto de verificação que executa filtragem adicional e rastreia o estado das conexões. Ele nega o início de conexões de redes externas (não confiáveis) para a rede interna (confiável), enquanto permite que usuários internos estabeleçam conexões bidirecionais com as redes não confiáveis. Ele também pode executar autenticação de usuário (proxy de autenticação) para conceder aos usuários remotos externos acesso a recursos de rede interna.
- **Roteador interno** - Outra linha de defesa é o roteador interno (R2 na figura). Ele pode aplicar regras de filtragem finais no tráfego antes de ser encaminhado para seu destino.

Os roteadores e firewalls não são os únicos dispositivos que são usados em uma abordagem de defesa profunda. Outros dispositivos de segurança incluem IPS (Intrusion Prevention Systems), Proteção Avançada contra Malware (AMP), sistemas de segurança de conteúdo da Web e de e-mail, serviços de identidade, controles de acesso à rede e muito mais.

Na abordagem de segurança em camadas de defesa profunda, as diferentes camadas trabalham juntas para criar uma arquitetura de segurança na qual a falha de uma salvaguarda não afeta a eficácia das outras salvaguardas.

### A cebola de segurança e a alcachofra de segurança

Uma analogia comum usada para descrever uma abordagem de defesa em profundidade é chamada de “cebola de segurança”. Como ilustrado na figura, um ator de ameaça teria que descascar as defesas de uma rede camada por camada de uma maneira semelhante a descascar uma cebola. Somente depois de penetrar cada camada, o ator da ameaça alcançaria os dados ou o sistema de destino.

**Observação:** A cebola de segurança descrita nesta página é uma forma de visualizar a defesa em profundidade. Isso não deve ser confundido com o conjunto Security Onion de ferramentas de segurança de rede.![[Pasted image 20250127210121.png]]

O cenário em mudança da rede, como a evolução das redes sem fronteiras, mudou essa analogia para a “alcachofra de segurança”, que beneficia o ator de ameaça.

Conforme ilustrado na figura, os atores da ameaça não precisam mais descascar cada camada. Eles só precisam remover certas “folhas de alcachofra”. O bônus é que cada “folha” da rede pode revelar dados confidenciais que não estão bem protegidos.

Por exemplo, é mais fácil para um agente de ameaça comprometer um dispositivo móvel do que comprometer um computador ou servidor interno protegido por camadas de defesa. Cada dispositivo móvel é uma folha. E folha após folha, tudo leva o hacker a mais dados. O coração da alcachofra é onde os dados mais confidenciais são encontrados. Cada folha fornece uma camada de proteção enquanto fornece simultaneamente um caminho para o ataque.

Nem todas as folhas precisam ser removidas para chegar ao coração da alcachofra. O hacker arranca a armadura de segurança ao longo do perímetro para chegar ao “coração” da empresa.

Enquanto os sistemas voltados para a Internet são geralmente muito bem protegidos e as proteções de limites são tipicamente sólidos, hackers persistentes, auxiliados por uma mistura de habilidade e sorte, eventualmente encontram uma lacuna nesse exterior hard-core através do qual eles podem entrar e ir onde quiserem.![[Pasted image 20250127210218.png]]

# Políticas, regulamentos e padrões de segurança

### Políticas de Negócios

Políticas de negócios são as diretrizes que são desenvolvidas por uma organização para governar suas ações. As políticas definem padrões de comportamento correto para a empresa e seus funcionários. Na rede, as políticas definem as atividades permitidas na rede. Isso define uma linha de base de uso aceitável. Se um comportamento que viola a política de negócios for detectado na rede, é possível que tenha ocorrido uma violação de segurança.

Uma organização pode ter várias diretivas orientadoras, conforme listado na tabela.![[Pasted image 20250127213325.png]]

### Política de Segurança

Uma política de segurança abrangente tem uma série de benefícios, incluindo os seguintes:

- Demonstra o compromisso de uma organização com a segurança
- Define as regras para o comportamento esperado
- Garante a consistência nas operações do sistema, aquisição e uso de software e hardware e manutenção
- Define as consequências legais das violações
- Dá ao pessoal de segurança o apoio da gestão

As políticas de segurança são usadas para informar os usuários, funcionários e gerentes sobre os requisitos de uma organização para proteger os ativos de tecnologia e informação. Uma política de segurança também especifica os mecanismos necessários para atender aos requisitos de segurança e fornece uma linha de base a partir da qual adquirir, configurar e auditar sistemas e redes de computadores para conformidade.

A tabela lista as diretivas que podem ser incluídas em uma diretiva de segurança.![[Pasted image 20250127213524.png]]

Um dos componentes de política de segurança mais comuns é um AUP. Isso também pode ser referido como uma política de uso apropriada. Este componente define o que os usuários têm ou não permissão para fazer nos vários componentes do sistema. Isso inclui o tipo de tráfego permitido na rede. A AUP deve ser o mais explícita possível, para evitar mal-entendidos.

Por exemplo, um AUP pode listar sites específicos, grupos de notícias ou aplicativos de uso intensivo de largura de banda que são proibidos de serem acessados por computadores da empresa ou da rede da empresa. Cada funcionário deve ser obrigado a assinar uma AUP, e as AUPs assinadas devem ser mantidas durante a duração do emprego.
### Políticas BYOD

Muitas organizações agora também devem oferecer suporte ao BYOD (Traga seu próprio dispositivo). Isso permite que os funcionários usem seus próprios dispositivos móveis para acessar sistemas, software, redes ou informações da empresa. O BYOD oferece vários benefícios importantes para as empresas, incluindo aumento da produtividade, redução dos custos operacionais e de TI, melhor mobilidade para os funcionários e maior atração quando se trata de contratar e reter funcionários.

No entanto, esses benefícios também trazem um maior risco de segurança das informações, pois o BYOD pode levar a violações de dados e maior responsabilidade para a organização.

Uma política de segurança BYOD deve ser desenvolvida para realizar o seguinte:

- Especifique os objetivos do programa BYOD.
- Identifique quais funcionários podem trazer seus próprios dispositivos.
- Identifique quais dispositivos serão suportados.
- Identificar o nível de acesso que os funcionários são concedidos ao usar dispositivos pessoais.
- Descrever os direitos de acesso e as atividades permitidas ao pessoal de segurança no dispositivo.
- Identifique quais regulamentos devem ser cumpridos ao usar dispositivos de funcionários.
- Identifique as salvaguardas a serem implementadas se um dispositivo for comprometido.

A tabela lista as práticas recomendadas de segurança BYOD para ajudar a mitigar vulnerabilidades BYOD.![[Pasted image 20250127213814.png]]

### Conformidade com regulamentações e padrões

Há também regulamentos externos em relação à segurança da rede. Os profissionais de segurança de rede devem estar familiarizados com as leis e códigos de ética que são vinculativos para os profissionais de Segurança de Sistemas de Informação (INFOSEC).

Muitas organizações são obrigadas a desenvolver e implementar políticas de segurança. Os regulamentos de conformidade definem o que as organizações são responsáveis pelo fornecimento e a responsabilidade caso não cumpram. Os regulamentos de conformidade que uma organização é obrigada a seguir dependem do tipo de organização e dos dados que a organização manipula. Regulamentos específicos de conformidade serão discutidos mais tarde no curso.