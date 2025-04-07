# Autoridades e o Sistema de Confiança PKI

### Gerenciamento de Chave Pública

O tráfego da Internet consiste no tráfego entre duas partes. Ao estabelecer uma conexão assimétrica entre dois hosts, os hosts trocarão suas informações de chave pública.

Um certificado SSL é um certificado digital que confirma a identidade de um domínio de site. Para implementar SSL em seu site, você compra um certificado SSL para seu domínio de um provedor de Certificado SSL. O terceiro de confiança faz uma investigação aprofundada antes da emissão das credenciais. Após essa investigação aprofundada, o terceiro emite credenciais (ou seja, certificado digital) que são difíceis de falsificar. Desse ponto em diante, todos os indivíduos que confiam no terceiro simplesmente aceitam as credenciais que o terceiro emite. Quando os computadores tentam se conectar a um site via HTTPS, o navegador verifica o certificado de segurança do site e verifica se ele é válido e originado com uma autoridade de certificação confiável. Isso valida que a identificação do site é verdadeira. O certificado é salvo localmente pelo navegador da Web e, em seguida, é usado em transações subsequentes. A chave pública do site está incluída no certificado e é usada para verificar futuras comunicações entre o site e o cliente.

Esses terceiros confiáveis fornecem serviços semelhantes aos escritórios de licenciamento governamentais. A figura ilustra como uma carteira de motorista é análoga a um certificado digital.![[Pasted image 20250131213606.png]]
A Infraestrutura de Chave Pública (PKI) consiste em especificações, sistemas e ferramentas que são usados para criar, gerenciar, distribuir, usar, armazenar e revogar certificados digitais. A autoridade de certificação (CA) é uma organização que cria certificados digitais vinculando uma chave pública a uma identificação confirmada, como um site ou indivíduo. O PKI é um sistema complexo que é projetado para proteger identidades digitais contra hackers até mesmo os atores de ameaças mais sofisticados ou estados-nação.

Alguns exemplos de Autoridades de Certificação são IDentrust, DigiCert, Sectigo, GlobalSign e GoDaddy. Essas CAs cobram por seus serviços. Let's Encrypt é uma CA sem fins lucrativos que oferece certificados gratuitamente.
### A infraestrutura de chave pública

A PKI é necessária para oferecer suporte à distribuição em larga escala e à identificação de chaves de criptografia públicas. A estrutura PKI facilita uma relação de confiança altamente escalável.

Consiste em hardware, software, pessoas, políticas e procedimentos necessários para criar, gerenciar, armazenar, distribuir e revogar certificados digitais.

A figura mostra os principais elementos da PKI.
![[Pasted image 20250131213801.png]]

1. Os certificados PKI contêm a chave pública de uma entidade ou de um indivíduo, a sua finalidade, a autoridade de certificação (AC) que validou e emitiu o certificado, o intervalo de datas durante o qual o certificado é válido e o algoritmo usado para criar a assinatura.
2. O armazenamento de certificados reside em um computador local e armazena certificados emitidos e chaves privadas.
3. O Certificado de Autoridade PKI (CA) é um terceiro confiável que emite certificados PKI para entidades e indivíduos após verificar sua identidade. Ele assina esses certificados usando sua chave privada.
4. O banco de dados de certificados armazena todos os certificados aprovados pela autoridade de certificação.

A figura seguinte mostra como os elementos da PKI interoperam:

- Neste exemplo, Bob recebeu seu certificado digital da CA. Este certificado é usado sempre que Bob se comunica com outras partes.
- Bob se comunica com Alice.
- Quando Alice recebe o certificado digital de Bob, ela se comunica com a autoridade de certificação confiável para validar a identidade de Bob.
![[Pasted image 20250131213854.png]]
1. **Emissões Certificado PKI**. Bob inicialmente solicita um certificado da autoridade de certificação. A autoridade de certificação autentica Bob e armazena o certificado PKI de Bob no banco de dados de certificados.
2. **Trocas Certificado PKI**. Bob se comunica com Alice usando seu certificado PKI.
3. **Verifica o certificado PKI**. Alice se comunica com o C A confiável usando a chave pública da CA. O CA refere-se ao banco de dados de certificados para validar o certificado PKI de Bob.

**Observação**: nem todos os certificados PKI são recebidos diretamente de uma autoridade de certificação. Uma autoridade de registro (RA) é uma autoridade de certificação subordinada e é certificada por uma autoridade de certificação raiz para emitir certificados para usos específicos.
### O Sistema de Autoridades PKI

Muitos fornecedores fornecem servidores da CA como um serviço gerenciado ou como um produto de usuário final. Alguns desses fornecedores incluem Symantec Group (VeriSign), Comodo, Go Daddy Group, GlobalSign e DigiCert, entre outros.

As organizações também podem implementar PKIs privadas usando o Microsoft Server ou Open SSL.

As autoridades de certificação, especialmente aquelas que são terceirizadas, emitem certificados baseados em classes que determinam a confiabilidade de um certificado.

A tabela fornece uma descrição das classes. O número de classe é determinado pelo rigor do procedimento que verificou a identidade do titular quando o certificado foi emitido. Quanto maior o número da classe, mais confiável será o certificado. Portanto, um certificado de classe 5 é confiável muito mais do que um certificado de classe inferior.
![[Pasted image 20250131214046.png]]
Por exemplo, um certificado de classe 1 pode exigir uma resposta por e-mail do titular para confirmar que deseja se inscrever. Este tipo de confirmação é uma autenticação fraca do titular. Para um certificado de classe 3 ou 4, o futuro titular deve provar a identidade e autenticar a chave pública aparecendo pessoalmente com pelo menos dois documentos de identificação oficiais.

Algumas chaves públicas da CA são pré-carregadas, como as listadas em navegadores da Web. A figura exibe vários certificados VeriSign contidos no armazenamento de certificados no host. Quaisquer certificados assinados por qualquer uma das autoridades de certificação na lista serão vistos pelo navegador como legítimos e serão confiáveis automaticamente.![[Pasted image 20250131214147.png]]

### O Sistema de Confiança PKI

PKIs podem formar diferentes topologias de confiança. O mais simples é a topologia PKI de raiz única.

Como mostrado na figura abaixo, uma única autoridade de certificação, chamada de CA raiz, emite todos os certificados para os usuários finais, que geralmente estão dentro da mesma organização. O benefício desta abordagem é a sua simplicidade. No entanto, é difícil dimensionar para um ambiente grande porque requer uma administração estritamente centralizada, o que cria um único ponto de falha.![[Pasted image 20250131214250.png]]

Em redes maiores, as CAs PKI podem ser vinculadas usando duas arquiteturas básicas:

**Topologias de AC certificadas cruzadas** - Conforme mostrado na figura abaixo, este é um modelo ponto a ponto no qual as ACs individuais estabelecem relações de confiança com outras ACs através da certificação cruzada de certificados de AC. Os usuários em ambos os domínios da CA também têm a certeza de que podem confiar uns nos outros. Isso fornece redundância e elimina o ponto único de falha.
![[Pasted image 20250131214341.png]]
**Topologias de CA hierárquicas** - Conforme mostrado na figura abaixo, a CA de nível mais alto é chamada de CA raiz. Ele pode emitir certificados para usuários finais e para uma autoridade de certificação subordinada. As subCAs podem ser criadas para suportar várias unidades de negócios, domínios ou comunidades de confiança. A autoridade de certificação raiz mantém a “comunidade de confiança” estabelecida garantindo que cada entidade na hierarquia esteja em conformidade com um conjunto mínimo de práticas. Os benefícios dessa topologia incluem maior escalabilidade e capacidade de gerenciamento. Esta topologia funciona bem na maioria das grandes organizações. No entanto, pode ser difícil determinar a cadeia do processo de assinatura.

Uma topologia hierárquica e de certificação cruzada pode ser combinada para criar uma infraestrutura híbrida. Um exemplo seria quando duas comunidades hierárquicas querem certificar-se entre si para que os membros de cada comunidade confiem uns nos outros.
### CA hierárquica
![[Pasted image 20250131214443.png]]

### Interoperabilidade de diferentes fornecedores de PKI

A interoperabilidade entre uma PKI e seus serviços de suporte, como o Lightweight Directory Access Protocol (LDAP) e diretórios X.500, é uma preocupação porque muitos fornecedores de CA propuseram e implementaram soluções proprietárias em vez de aguardar o desenvolvimento de padrões.

**Observação**: LDAP e X.500 são protocolos usados para consultar um serviço de diretório, como o Microsoft Active Directory, para verificar um nome de usuário e senha.

Para resolver esse problema de interoperabilidade, o IETF publicou o Internet X.509 Public Key Infrastructure Policy and Certification Practices Framework (RFC 2527). O padrão X.509 versão 3 (X.509 v3) define o formato de um certificado digital.![[Pasted image 20250131214552.png]]
1. **SSL** - Servidores Web seguros Use X.509.v3 para autenticação do site nos protocolos SSL e TLS, enquanto os navegadores da Web usam X.509V3 para implementar certificados de cliente HTTPS. SSL é a autenticação baseada em certificado mais utilizada.
2. **IPsec** - IPsec VPNS usa certificados X.509 quando a autenticação baseada em RSA é usada para a Intercâmbio de chaves da Internet (IKE).
3. **S/MIME** - Os agentes de correio do usuário que suportam proteção de correio com o protocolo Secure / Multipurpose Internet Mail Extensions (S / MIME) usam certificados X.509.
4. **EAP-TLS** - Os switches da Cisco podem usar certificados para autenticar dispositivos finais que se conectam a portas de LAN usando 802.1x entre os dispositivos adjacentes. A autenticação pode ser proxy para um ACS central por meio do Extensible Authentication Protocol with TLS (EAP-TLS).

### Inscrição, autenticação e revogação de certificados

A primeira etapa no procedimento de autenticação da autoridade de certificação é obter com segurança uma cópia da chave pública da autoridade de certificação. Todos os sistemas que utilizam a PKI devem ter a chave pública da autoridade de certificação, que é chamada de certificado autoassinado. A chave pública da autoridade de certificação verifica todos os certificados emitidos pela autoridade de certificação e é vital para o bom funcionamento da PKI.

**Observação**: somente uma autoridade de certificação raiz pode emitir um certificado autoassinado reconhecido ou verificado por outras autoridades de certificação dentro da PKI.

Para muitos sistemas, como navegadores da Web, a distribuição de certificados de CA é processada automaticamente. O navegador da Web vem pré-instalado com um conjunto de certificados raiz de CA públicos. As organizações e seus domínios do site enviam seus certificados públicos para os visitantes do site. As autoridades de certificação e os registradores de domínio de certificado criam e distribuem certificados privados e públicos para clientes que compram certificados.

O processo de registro de certificado é usado por um sistema host para se inscrever com uma PKI. Para fazer isso, os certificados de CA são recuperados em banda através de uma rede e a autenticação é feita fora de banda (OOB) usando o telefone. O registro do sistema com a PKI entra em contato com uma autoridade de certificação para solicitar e obter um certificado de identidade digital para si mesmo e para obter o certificado autoassinado da autoridade de certificação. O estágio final verifica se o certificado da autoridade de certificação foi autêntico e é executado usando um método fora de banda, como o sistema de telefone antigo simples (POTS), para obter a impressão digital do certificado de identidade da autoridade de certificação válido.

A autenticação não requer mais a presença do servidor da autoridade de certificação e cada usuário troca seus certificados contendo chaves públicas.

Os certificados devem, por vezes, ser revogados. Por exemplo, um certificado digital pode ser revogado se a chave for comprometida ou se não for mais necessário.

Aqui estão dois dos métodos mais comuns de revogação:

- **Lista de revogação de certificados (CRL)** - Uma lista de números de série de certificados revogados que foram invalidados porque expiraram. As entidades PKI pesquisam regularmente o repositório CRL para receber a CRL atual.
- **Protocolo de Status de Certificado Online (OCSP)** - Um protocolo de Internet usado para consultar um servidor OCSP para o status de revogação de um certificado digital X.509. As informações de revogação são imediatamente enviadas para um banco de dados on-line.
# Aplicações e impactos da criptografia

### Aplicações PKI

Onde a PKI pode ser usada por uma empresa? O seguinte fornece uma pequena lista de usos comuns de PKIs:

- Autenticação de peer baseada em certificado SSL/TLS
- Proteja o tráfego de rede usando VPNs IPsec
- Tráfego da web HTTPS
- Controle o acesso à rede usando a autenticação 802.1x
- E-mail seguro usando o protocolo S/MIME
- Mensagens instantâneas seguras
- Aprovar e autorizar aplicativos com assinatura de código
- Proteja os dados do usuário com o sistema de arquivos de criptografia (EFS)
- Implementar autenticação de dois fatores com cartões inteligentes
- Protegendo dispositivos de armazenamento USB

### Transações de rede criptográfica

Um analista de segurança deve ser capaz de reconhecer e resolver possíveis problemas relacionados à permissão de soluções relacionadas à PKI na rede corporativa.

Considere como o aumento do tráfego SSL/TLS representa um grande risco de segurança para as empresas porque o tráfego é criptografado e não pode ser interceptado e monitorado por meios normais. Os usuários podem introduzir malware ou vazar informações confidenciais através de uma conexão SSL/TLS.

Os atores de ameaças podem usar SSL/TLS para introduzir violações de conformidade regulatória, vírus, malware, perda de dados e tentativas de intrusão em uma rede.

Outros problemas relacionados a SSL/TLS podem estar associados à validação do certificado de um servidor Web. Quando isso ocorre, os navegadores da Web exibirão um aviso de segurança. Os problemas relacionados à PKI associados a avisos de segurança incluem:

- **Faixa de datas de validade** - Os certificados X.509v3 especificam datas “não antes” e “não depois”. Se a data atual estiver fora do intervalo, o navegador da Web exibirá uma mensagem. Os certificados expirados podem simplesmente ser o resultado da supervisão do administrador, mas também podem refletir condições mais graves.
- **Erro de validação de assinatura** - Se um navegador não puder validar a assinatura no certificado, não há garantia de que a chave pública no certificado seja autêntica. A validação de assinatura falhará se o certificado raiz da hierarquia da autoridade de certificação não estiver disponível no armazenamento de certificados do navegador.

Alguns desses problemas podem ser evitados devido ao fato de que os protocolos SSL/TLS são extensíveis e modulares. Isto é conhecido como um conjunto de cifras. Os principais componentes do conjunto de cifras são o MAC (Message Authentication Code Algoritmo), o algoritmo de criptografia, o algoritmo de troca de chaves e o algoritmo de autenticação. Estes podem ser alterados sem substituir todo o protocolo. Isso é muito útil porque os diferentes algoritmos continuam a evoluir. À medida que a criptoanálise continua a revelar falhas nesses algoritmos, o conjunto de cifras pode ser atualizado para corrigir essas falhas. Quando as versões de protocolo dentro do conjunto de cifras mudam, o número de versão do SSL/TLS também muda.
### Criptografia e monitoramento de segurança

O monitoramento de rede torna-se mais desafiador quando os pacotes são criptografados. No entanto, os analistas de segurança devem estar cientes desses desafios e enfrentá-los da melhor forma possível. Por exemplo, quando VPNs site a site são usadas, o IPS deve ser posicionado para que ele possa monitorar o tráfego não criptografado.

No entanto, o aumento do uso de HTTPS na rede empresarial introduz novos desafios. Como o HTTPS introduz tráfego HTTP criptografado de ponta a ponta (via TLS/SSL), não é tão fácil espiar o tráfego do usuário.

Os analistas de segurança devem saber como contornar e resolver esses problemas. Aqui está uma lista de algumas das coisas que um analista de segurança pode fazer:

- Configure regras para distinguir entre tráfego SSL e não-SSL, tráfego SSL HTTPS e não-HTTPS.
- Melhore a segurança através da validação de certificados de servidor utilizando CRLs e OCSP.
- Implemente proteção antimalware e filtragem de URL de conteúdo HTTPS.
- Implante um Cisco SSL Appliance para descriptografar o tráfego SSL e enviá-lo para dispositivos IPS (Intrusion Prevention System, sistema de prevenção de intrusões) para identificar riscos normalmente ocultos pelo SSL.

A criptografia é dinâmica e está sempre mudando. Um analista de segurança deve manter um bom entendimento de algoritmos criptográficos e operações para ser capaz de investigar incidentes de segurança relacionados à criptografia.

Há duas maneiras principais em que a criptografia afeta as investigações de segurança. Primeiro, os ataques podem ser direcionados especificamente para os próprios algoritmos de criptografia. Após o algoritmo ter sido rachado e o invasor obter as chaves, todos os dados criptografados que foram capturados podem ser descriptografados pelo invasor e lidos, expondo assim dados privados. Em segundo lugar, a investigação de segurança também é afetada porque os dados podem ser escondidos à vista, encriptando-os. Por exemplo, o tráfego de comando e controle criptografado com TLS/SSL provavelmente não pode ser visto por um firewall. O tráfego de comando e controle entre um servidor de comando e controle e um computador infectado em uma rede segura não pode ser interrompido se não puder ser visto e compreendido. O invasor seria capaz de continuar usando comandos criptografados para infectar mais computadores e, possivelmente, criar uma botnet. Esse tipo de tráfego pode ser detectado descriptografando o tráfego e comparando-o com assinaturas de ataque conhecidas ou detectando tráfego TLS/SSL anômalo. Isso é muito difícil e demorado, ou um processo de acerto ou erro.

