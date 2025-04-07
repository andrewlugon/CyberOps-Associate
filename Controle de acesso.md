# Conceitos de controle de acesso

### Segurança das comunicações - CIA

A segurança da informação trata da proteção da informação e dos sistemas de informação contra acesso não autorizado, uso, divulgação, interrupção, modificação ou destruição.![[Pasted image 20250128180753.png]]

Como mostrado na figura, a tríade da CIA consiste em três componentes da segurança da informação:

- **Confidencialidade** - Somente indivíduos, entidades ou processos autorizados podem acessar informações confidenciais.
- **Integridade** - refere-se à proteção de dados contra alterações não autorizadas.
- **Disponibilidade** - os usuários autorizados devem ter acesso ininterrupto aos recursos e dados da rede de que necessitam.

Os dados de rede podem ser criptografados (tornados ilegíveis para usuários não autorizados) usando vários aplicativos de criptografia. A conversa entre dois usuários de telefone IP pode ser criptografada. Os arquivos em um computador também podem ser criptografados. Estes são apenas alguns exemplos. A criptografia pode ser usada em praticamente qualquer lugar em que haja comunicação de dados. De fato, a tendência é que toda comunicação seja criptografada.
### Segurança Zero Trust

Zero Trust é uma abordagem abrangente para proteger todo o acesso em redes, aplicações e ambientes. Essa abordagem ajuda a proteger o acesso de usuários, dispositivos de usuário final, APIs, IoT, microsserviços, contêineres e muito mais. Ele protege a força de trabalho, as cargas de trabalho e o local de trabalho de uma organização. O princípio de uma abordagem de confiança zero é: “Nunca confie, sempre verifique”. Assumir confiança zero sempre que alguém ou algo solicitar acesso a ativos. Uma estrutura de segurança de confiança zero ajuda a impedir acesso não autorizado, conter violações e reduzir o risco de movimento lateral de um invasor através de uma rede.

Tradicionalmente, o perímetro da rede, ou borda, era o limite entre dentro e fora, ou confiável e não confiável. Em uma abordagem de confiança Zero, qualquer lugar em que uma decisão de controle de acesso seja necessária deve ser considerado um perímetro. Isso significa que, embora um usuário ou outra entidade possa ter passado com êxito o controle de acesso anteriormente, eles não são confiáveis para acessar outra área ou recurso até que sejam autenticados. Em alguns casos, os usuários podem ser obrigados a autenticar várias vezes e de maneiras diferentes, para obter acesso a diferentes camadas da rede.

Os três pilares da confiança zero são força de trabalho, cargas de trabalho e local de trabalho.

**Confiança zero para a força de trabalho**

Este pilar consiste em pessoas (por exemplo, funcionários, prestadores de serviços, parceiros e fornecedores) que acessam aplicativos de trabalho usando seus dispositivos pessoais ou gerenciados por empresas. Esse pilar garante que apenas os usuários certos e dispositivos seguros possam acessar aplicativos, independentemente da localização.

**Confiança zero para cargas de trabalho**

Esse pilar está preocupado com aplicativos que estão sendo executados na nuvem, em data centers e outros ambientes virtualizados que interagem uns com os outros. Ele se concentra no acesso seguro quando uma API, um microsserviço ou um contêiner está acessando um banco de dados dentro de um aplicativo.

**Confiança zero para o local de trabalho**

Este pilar se concentra no acesso seguro para qualquer e todos os dispositivos, inclusive na Internet das Coisas (IoT), que se conectam a redes empresariais, como terminais de usuário, servidores físicos e virtuais, impressoras, câmeras, sistemas de AVAC, quiosques, bombas de infusão, sistemas de controle industrial e muito mais.

### Modelos de controle de acesso

Uma organização deve implementar controles de acesso adequados para proteger seus recursos de rede, recursos do sistema de informações e informações.

Um analista de segurança deve entender os diferentes modelos básicos de controle de acesso para ter uma melhor compreensão de como os invasores podem quebrar os controles de acesso.

A tabela lista vários tipos de métodos de controle de acesso.![[Pasted image 20250128181259.png]]

Outro modelo de controle de acesso é o princípio do privilégio mínimo, que especifica uma abordagem limitada, conforme necessário, para conceder direitos de acesso ao usuário e ao processo a informações e ferramentas específicas. O princípio do privilégio mínimo afirma que os usuários devem receber a quantidade mínima de acesso necessária para desempenhar sua função de trabalho.

Uma exploração comum é conhecida como escalação de privilégios. Nesta exploração, vulnerabilidades em servidores ou sistemas de controle de acesso são exploradas para conceder a um usuário não autorizado, ou processo de software, níveis de privilégio mais altos do que deveriam ter. Depois que o privilégio é concedido, o agente de ameaça pode acessar informações confidenciais ou assumir o controle de um sistema.
# Uso e operação AAA

### Operação AAA

Uma rede deve ser projetada para controlar quem tem permissão para se conectar a ela e o que eles têm permissão para fazer quando estão conectados. Estes requisitos de design são identificados na política de segurança de rede. A política especifica como administradores de rede, usuários corporativos, usuários remotos, parceiros de negócios e clientes acessam recursos de rede. A política de segurança de rede também pode exigir a implementação de um sistema de contabilidade que rastreia quem iniciou sessão e quando e o que fizeram durante a sessão iniciada. Alguns regulamentos de conformidade podem especificar que o acesso deve ser registrado e os logs mantidos por um determinado período de tempo.

O protocolo AAA (Authentication, Authorization and Accounting) fornece a estrutura necessária para habilitar a segurança de acesso escalável.

A tabela lista as três funções de segurança independentes fornecidas pela estrutura arquitetônica AAA.![[Pasted image 20250128181709.png]]

Esse conceito é semelhante ao uso de um cartão de crédito. O cartão de crédito identifica quem pode utilizá-lo, estipula um limite de uso e mantém o controle dos itens comprados pelo usuário.

### autenticação AAA

A autenticação AAA pode ser usada para autenticar usuários para o acesso administrativo ou pode ser usada para autenticar usuários para o acesso à rede remota.

A Cisco fornece dois métodos comuns de implementação de serviços AAA.

**Autenticação de AAA local**

Esse método às vezes é conhecido como autenticação autônoma porque autentica usuários contra nomes de usuário e senhas armazenados localmente, como mostrado na figura. A AAA local é ideal para redes pequenas.

**Autenticação de AAA com base em servidor**

Esse método se autentica em um servidor AAA central que contém os nomes de usuário e senhas para todos os usuários. A autenticação AAA baseada em servidor é apropriada para redes de médio a grande porte.

O AAA centralizado é mais escalável e gerenciável do que a autenticação AAA local e, portanto, é a implementação AAA preferida.

Um sistema AAA centralizado pode manter bancos de dados independentemente para autenticação, autorização e contabilidade. Ele pode aproveitar o Active Directory ou o Lightweight Directory Access Protocol (LDAP) para autenticação de usuário e associação de grupo, mantendo seus próprios bancos de dados de autorização e contabilidade.

Os dispositivos se comunicam com o servidor AAA centralizado usando os protocolos RADIUS (Remote Authentication Dial-In User Service) ou Terminal Access Controller Access Control System (TACACS +).

A tabela lista as diferenças entre os dois protocolos.![[Pasted image 20250128182055.png]]

### Registros de Contabilidade AAA

O AAA centralizado também permite o uso do método de contabilidade. Os registros contábeis de todos os dispositivos são enviados para repositórios centralizados, o que simplifica a auditoria das ações do usuário.

AAA Accounting coleta e relata dados de uso em registros AAA. Esses logs são úteis para auditoria de segurança. Os dados coletados podem incluir os horários de conexão inicial e final, comandos executados, número de pacotes e número de bytes.

Um uso amplamente difundido da contabilidade é combiná-lo com a autenticação AAA. Isso ajuda a gerenciar o acesso a dispositivos de interrede pela equipe administrativa da rede. Contabilidade fornece mais segurança do que apenas autenticação. Os servidores AAA mantêm um registro detalhado de exatamente o que o usuário autenticado faz no dispositivo, conforme mostrado na figura. Isso inclui todos os comandos EXEC e de configuração emitidos pelo usuário. O log contém vários campos de dados, incluindo o nome de usuário, a data e a hora, e o comando real que foi inserido pelo usuário. Esta informação é útil na solução de problemas de dispositivos. Ele também fornece evidências contra indivíduos que realizam ações maliciosas.![[Pasted image 20250128182150.png]]

A tabela exibe os vários tipos de informações contábeis que podem ser coletadas.![[Pasted image 20250128182211.png]]