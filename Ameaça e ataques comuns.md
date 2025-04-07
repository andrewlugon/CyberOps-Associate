### Tipos de Malware

Malware é a abreviatura de software malicioso ou código malicioso. É um código ou software projetado especificamente para danificar, interromper, roubar ou geralmente infligir alguma outra ação “ruim” ou ilegítima em dados, hosts ou redes. É importante saber sobre malware porque os agentes de ameaças e criminosos online freqüentemente tentam induzir os usuários a instalar malware para ajudar a explorar as lacunas de segurança. Além disso, o malware se transforma tão rapidamente que os incidentes de segurança relacionados ao malware são extremamente comuns porque o software antimalware não pode ser atualizado com rapidez suficiente para impedir as novas ameaças.
### Vírus

Um vírus é um tipo de malware que se espalha inserindo uma cópia de si mesmo em outro programa. Depois que o programa é executado, os vírus se espalham de um computador para outro, infectando os computadores. A maioria dos vírus requer ajuda humana para se espalhar. Por exemplo, quando alguém conecta uma unidade USB infectada ao PC, o vírus entrará no PC. O vírus pode então infectar uma nova unidade USB e se espalhar para novos PCs. Os vírus podem ficar inativos por um período prolongado e, em seguida, ativá-los em uma hora e data específicas.

Um vírus simples pode instalar-se na primeira linha de código em um arquivo executável. Quando ativado, o vírus pode verificar o disco em busca de outros executáveis para que ele possa infectar todos os arquivos que ainda não infectou. Os vírus podem ser inofensivos, como os que exibem uma imagem na tela, ou podem ser destrutivos, como os que modificam ou excluem arquivos do disco rígido. Os vírus também podem ser programados para se modificar e evitar a detecção.

A maioria dos vírus agora se espalha por unidades de memória USB, CDs, DVDs, compartilhamentos de rede e e-mail. Os vírus de e-mail são um tipo comum de vírus.

### Cavalos de Troia

O termo cavalo de Tróia originou-se da mitologia grega. Guerreiros gregos ofereceram ao povo de Tróia (os troianos) um cavalo oco gigante como um presente. Os troianos trouxeram o cavalo gigante para sua cidade murada, sem saber que continha muitos guerreiros gregos. À noite, depois que a maioria dos troianos dormia, os guerreiros saíram do cavalo, abriram os portões da cidade e permitiram que uma força considerável entrasse e tomasse a cidade.

O malware de cavalo de Tróia é um software que parece ser legítimo, mas contém código malicioso que explora os privilégios do usuário que o executa. Muitas vezes, os cavalos de Tróia são encontrados anexados a jogos online.

Os usuários são comumente induzidos a carregar e executar o cavalo de Tróia em seus sistemas. Ao jogar o jogo, o usuário não notará um problema. Em segundo plano, o cavalo de Tróia foi instalado no sistema do usuário. O código malicioso do cavalo de Tróia continua a funcionar mesmo depois que o jogo foi fechado.

O conceito do cavalo de Tróia é flexível. Pode causar danos imediatos, fornecer acesso remoto ao sistema ou acesso através de uma porta traseira. Ele também pode executar ações conforme instruído remotamente, como “me envie o arquivo de senha uma vez por semana.“ Esta tendência de malware para enviar dados de volta para o cibercriminoso destaca a necessidade de monitorar o tráfego de saída em busca de indicadores de ataque.

Cavalos de Tróia escritos sob medida, como aqueles com um alvo específico, são difíceis de detectar.

### Cavalo de Tróia Classificação

Os cavalos de Tróia são geralmente classificados de acordo com o dano que eles causam, ou a maneira pela qual eles violam um sistema, como mostrado na figura.
![[Pasted image 20250122202348.png]]

### Worms

Os worms de computador são semelhantes aos vírus porque se replicam e podem causar o mesmo tipo de dano. Especificamente, os worms se replicam explorando vulnerabilidades nas redes de forma independente. Os worms podem retardar as redes à medida que se espalham de sistema para sistema.

Enquanto um vírus requer um programa host para execução, os worms podem ser executados de modo autônomo. Exceto pela infecção inicial, eles não necessitam mais da participação do usuário. Após infectar um host, um worm pode ser transmitido muito rapidamente pela rede.

Os worms são responsáveis por alguns dos ataques mais devastadores da Internet. Em 2001, o worm Code Red infectou inicialmente 658 servidores. Em 19 horas, o worm infectou mais de 300.000 servidores.

A infecção inicial do worm SQL Slammer é conhecida como o worm que comeu a internet. O SQL Slammer foi um ataque de negação de serviço (DoS) que explorava um bug de estouro de buffer no SQL Server da Microsoft. No seu pico, o número de servidores infectados dobrou de tamanho a cada 8,5 segundos. É por isso que ele foi capaz de infectar mais de 250 mil hosts em 30 minutos. Quando foi lançado no fim de semana de 25 de janeiro de 2003, interrompeu a internet, instituições financeiras, caixas eletrônicos e muito mais. Ironicamente, um patch para esta vulnerabilidade tinha sido lançado 6 meses antes. Os servidores infectados não tinham o patch atualizado aplicado. Essa foi uma chamada de ativação para muitas organizações implementarem uma política de segurança exigindo que atualizações e patches fossem aplicados em tempo hábil.

Worms compartilham características semelhantes. Todos eles exploram uma vulnerabilidade habilitadora, têm uma maneira de se propagar e todos contêm uma carga útil.

### Componentes do Worm

Apesar das técnicas de mitigação que surgiram ao longo dos anos, os vermes continuaram a evoluir e representam uma ameaça persistente. Worms tornaram-se mais sofisticados ao longo do tempo, mas eles ainda tendem a ser baseados na exploração de fraquezas em aplicativos de software.

A maioria dos ataques de worm consiste em três componentes.

- **Habilitando vulnerabilidade** - Um worm se instala usando um mecanismo de exploração, como um anexo de e-mail, um arquivo executável ou um cavalo de Tróia, em um sistema vulnerável.
- **Mecanismo de propagação** - Depois de obter acesso a um dispositivo, o worm se replica e localiza novos alvos.
- **Carga útil** - Qualquer código malicioso que resulte em alguma ação é uma carga útil. Na maioria das vezes, isso é usado para criar um backdoor que permite a um ator de ameaça acessar o host infectado ou criar um ataque DoS.

Worms são programas autônomos que atacam um sistema para explorar uma vulnerabilidade conhecida. Após a exploração bem-sucedida, o worm se copia do host atacante para o sistema recém-explorado e o ciclo começa novamente. Seus mecanismos de propagação são comumente implantados de uma forma difícil de detectar.

A técnica de propagação usada pelo worm Code Red é mostrada na figura.
![[Pasted image 20250122202756.png]]
**Nota**: Worms nunca param de se espalhar na internet. Depois de serem liberados, os vermes continuam a se propagar até que todas as fontes possíveis de infecção sejam devidamente corrigidos.

### Ransomware

Os atores de ameaças usaram vírus, worms e cavalos de Tróia para transportar suas cargas úteis e por outros motivos maliciosos. No entanto, o malware continua a evoluir.

Atualmente, o malware mais dominante é o ransomware. Ransomware é um malware que nega acesso ao sistema de computador infectado ou aos seus dados. Os criminosos cibernéticos, em seguida, exigem pagamento para liberar o sistema de computador.

O ransomware evoluiu para se tornar o tipo de malware mais lucrativo da história. Na primeira metade de 2016, as campanhas de ransomware concentradas em usuários corporativos e individuais se tornaram mais amplas e eficientes.

Existem dezenas de variantes de ransomware. Ransomware usa frequentemente um algoritmo de criptografia para criptografar arquivos e dados do sistema. A maioria dos algoritmos de criptografia de ransomware conhecidos não pode ser descriptografada facilmente, deixando as vítimas com poucas opções a não ser pagar o preço pedido. Os pagamentos são normalmente pagos em Bitcoin porque os usuários de bitcoin podem permanecer anônimos. Bitcoin é uma moeda digital de código aberto que ninguém possui ou controla.

Email e publicidade maliciosa, também conhecidos como malvertising, são vetores para campanhas de ransomware. A engenharia social também é usada, como quando os cibercriminosos que se identificam como técnicos de segurança chamam de residências e persuadem os usuários a se conectar a um site que baixa o ransomware para o computador do usuário.

### Outro Malware

Estes são alguns exemplos das variedades de malware moderno:
![[Pasted image 20250122203027.png]]
Esta lista continuará a crescer à medida que a Internet evolui. Novos malwares serão sempre desenvolvidos. Um dos principais objetivos das operações de segurança cibernética é aprender sobre novos malwares e como mitigá-lo prontamente.

### Comportamentos comuns de malware

Os cibercriminosos modificam continuamente o código de malware para alterar a forma como ele se espalha e infecta computadores. No entanto, a maioria produz sintomas semelhantes que podem ser detectados através do monitoramento de log de rede e dispositivo.

Os computadores infectados com malware geralmente apresentam um ou mais dos seguintes sintomas:

- Aparência de arquivos, programas ou ícones da área de trabalho estranhos
- Programas antivírus e de firewall estão desativando ou reconfigurando configurações
- A tela do computador está congelando ou o sistema está travando
- E-mails são enviados espontaneamente sem o seu conhecimento para a sua lista de contatos
- Os arquivos foram modificados ou excluídos
- Maior uso da CPU e/ou da memória
- Problemas de conexão a redes
- Velocidade lenta do computador ou do navegador da Web
- Processos ou serviços desconhecidos em execução
- Portas TCP ou UDP desconhecidas abertas
- Conexões são feitas para hosts na Internet sem ação do usuário
- Comportamento estranho do

**Observação**: o comportamento de malware não se limita à lista acima.

# Ataques de rede comuns - reconhecimento, acesso e engenharia social

### Tipos de ataques de rede

Malware é um meio de obter uma carga útil entregue. Quando é entregue e instalada, a carga útil pode ser usada para causar uma variedade de ataques internos à rede. Os atores de ameaças também podem atacar a rede de fora.

Por que os atores ameaçadores atacam redes? Há muitos motivos, incluindo dinheiro, ganância, vingança ou crenças políticas, religiosas ou sociológicas. Os profissionais de segurança de rede devem compreender os tipos de ataques usados para combater essas ameaças para garantir a segurança da LAN.

Para atenuar os ataques, é útil primeiro categorizar os vários tipos de ataques. Ao categorizar ataques de rede, é possível abordar tipos de ataques em vez de ataques individuais.

Embora não haja uma maneira padronizada de categorizar os ataques de rede, o método utilizado neste curso classifica os ataques em três categorias principais.

- Ataques de Reconhecimento
- Ataques de Acesso
- Ataques de DoS

### Ataques de Reconhecimento

Reconhecimento é coleta de informações. É análogo a um ladrão que inspeciona um bairro indo de porta em porta fingindo vender alguma coisa. O que o ladrão está realmente fazendo é procurando casas vulneráveis, como residências desocupadas, residências com portas ou janelas fáceis de abrir e residências sem sistemas de segurança ou câmeras de segurança.

Os atores de ameaças usam ataques de reconhecimento (ou recon) para fazer descobertas e mapeamentos não autorizados de sistemas, serviços ou vulnerabilidades. Os ataques Recon precedem ataques de acesso ou ataques DoS.

Algumas das técnicas usadas pelos atores de ameaças mal-intencionadas para realizar ataques de reconhecimento estão descritas na tabela.![[Pasted image 20250122203444.png]]

### Ataques de Acesso

Os ataques de acesso exploram vulnerabilidades conhecidas em serviços de autenticação, serviços de FTP e serviços da Web. O objetivo desse tipo de ataque é obter acesso a contas da web, bancos de dados confidenciais e outras informações confidenciais.

Os atores de ameaças usam ataques de acesso a dispositivos de rede e computadores para recuperar dados, obter acesso ou escalar privilégios de acesso ao status de administrador.

**Ataques de senha**

Em um ataque de senha, o agente de ameaça tenta descobrir senhas críticas do sistema usando vários métodos. Os ataques de senha são muito comuns e podem ser iniciados usando uma variedade de ferramentas de quebra de senha.

**Ataques de falsificação (spoofing)**

Nos ataques de falsificação, o dispositivo do agente de ameaças tenta se passar por outro dispositivo falsificando os dados. Ataques comuns incluem falsificação IP (IP spoofing), falsificação MAC (MAC spoofing), e falsificação DHCP (DHCP spoofing). Esses ataques de falsificação serão discutidos em mais detalhes posteriormente neste módulo

Outros ataques de acesso incluem:

- Exploração de confiança
- Redirecionamento de porta
- ataque man in the middle
- ⁪ataque de saturação do buffer

Em um ataque de exploração de confiança, um agente de ameaça usa privilégios não autorizados para obter acesso a um sistema, possivelmente comprometendo o alvo.

Em um ataque de redirecionamento de porta, um agente de ameaça usa um sistema comprometido como base para ataques contra outros alvos.

Em um ataque man-in-the-middle, o agente de ameaça é posicionado entre duas entidades legítimas para ler ou modificar os dados que passam entre as duas partes

Em um ataque de estouro de buffer, o agente de ameaça explora a memória do buffer e a sobrecarrega com valores inesperados. Isso geralmente torna o sistema inoperante, criando um ataque de DoS.

### Ataques de engenharia social

Engenharia social é um ataque de acesso que tenta manipular indivíduos para realizar ações ou divulgar informações confidenciais. Algumas técnicas de engenharia social são realizadas pessoalmente, enquanto outras podem usar o telefone ou a Internet.

Os engenheiros sociais frequentemente dependem da boa vontade das pessoas para ajuda. Eles também atacam as fraquezas das pessoas. Por exemplo, um agente de ameaças pode chamar um funcionário autorizado com um problema urgente, que requer acesso imediato à rede. O agente de ameaças pode recorrer à vaidade do funcionário, valer-se de autoridade usando técnicas que citam nomes ou apelar para a ganância do funcionário.

Informações sobre técnicas de engenharia social são mostradas na tabela.
![[Pasted image 20250122203846.png]]

O Social Engineer Toolkit (SET) foi projetado para ajudar hackers whitehat e outros profissionais de segurança de rede a criar ataques de engenharia social para testar suas próprias redes. É um conjunto de ferramentas baseadas em menu que ajudam a lançar ataques de engenharia social. O SET é apenas para fins educacionais. Está disponível gratuitamente na Internet.

As empresas devem educar seus usuários sobre os riscos da engenharia social e desenvolver estratégias para validar identidades por telefone, via email ou pessoalmente.

A figura mostra práticas recomendadas que devem ser seguidas por todos os usuários.

### Fortalecimento do elo mais fraco

A cibersegurança é tão forte quanto seu elo mais fraco. Como computadores e outros dispositivos conectados à Internet se tornaram uma parte essencial de nossas vidas, eles não parecem mais novos ou diferentes. As pessoas se tornaram muito casuais em seu uso desses dispositivos e raramente pensam em segurança de rede. O elo mais fraco na segurança cibernética pode ser o pessoal dentro de uma organização, e a engenharia social é uma grande ameaça à segurança. Por isso, uma das medidas de segurança mais eficazes que uma organização pode tomar é treinar seu pessoal e criar uma “cultura consciente da segurança”.

# Ataques de rede - negação de serviço, estouros de buffer e evasão

### Ataques de DoS

Um ataque de negação de serviço (DoS) cria algum tipo de interrupção dos serviços de rede para usuários, dispositivos ou aplicativos. Existem dois tipos principais de ataque de negação de serviço (DoS):

- **Grande quantidade de tráfego** - O agente de ameaças envia uma enorme quantidade de dados a uma taxa que a rede, host ou aplicativo não pode manipular. Isso faz com que os tempos de transmissão e resposta diminuam. Também pode travar um dispositivo ou serviço.
- **Pacotes maliciosamente formatados** - O invasor envia um pacote formatado maliciosamente para um host ou aplicativo e o receptor não consegue manipulá-lo. Isso causa lentidão ou falha na execução do dispositivo receptor.

Os ataques de DoS são um grande risco, porque interrompem a comunicação e causam perda significativa de tempo e dinheiro. Esses ataques são relativamente simples de conduzir, mesmo por um invasor não capacitado.

Um ataque de negação de serviço distribuída (DDoS) é semelhante a um ataque de negação de serviço (DoS), porém é originado por várias fontes coordenadas. Por exemplo, um agente de ameaça cria uma rede de hosts infectados, conhecidos como zumbis. O agente de ameaças usa um sistema de comando e controle (CnC) para enviar mensagens de controle aos zumbis. Os zumbis constantemente examinam e infectam mais hosts com malware bot. O malware bot é projetado para infectar um host, tornando-o um zumbi que pode se comunicar com o sistema CnC. Um grupo de zumbis é chamada de botnet. Quando pronto, o agente de ameaça instrui o sistema CnC a fazer com que o botnet de zumbis execute um ataque DDoS.

### Componentes de ataques DDoS

Se os atores da ameaça podem comprometer muitos hosts, eles podem executar um ataque DoS distribuído (DDoS). Os ataques DDoS são semelhantes em intenção aos ataques DoS, exceto que um ataque DDoS aumenta em magnitude porque ele se origina de várias fontes coordenadas, como mostrado na figura. Um ataque DDoS pode usar centenas ou milhares de fontes, como em ataques DDoS baseados em IoT.

Os termos a seguir são usados para descrever componentes de um ataque DDoS:
![[Pasted image 20250122204318.png]]

**Nota**: Existe uma economia subterrânea onde os botnets podem ser comprados (e vendidos) por uma taxa nominal. Isso pode fornecer aos atores de ameaça botnets de hosts infectados prontos para lançar um ataque DDoS contra o alvo escolhido.

### Mirai Botnet

Mirai é malware que direcionou dispositivos IoT configurados com informações de login padrão. Câmeras de televisão de circuito fechado (CCTV) constituíam a maioria dos alvos de Mirai. Usando um ataque de dicionário de força bruta, Mirai correu através de uma lista de nomes de usuário padrão e senhas que eram amplamente conhecidos na internet.

- root/default
- root/1111
- root/54321
- admin/admin1234
- admin1/password
- guest/12345
- tech/tech
- support/support

Depois de obter acesso bem-sucedido, Mirai direcionou os utilitários BusyBox baseados em Linux que são executados nesses dispositivos. Esses utilitários foram usados para transformar os dispositivos em bots que poderiam ser controlados remotamente como parte de uma botnet. O botnet foi então usado como parte de um ataque distribuído de negação de serviço (DDoS). Em setembro de 2016, uma botnet Mirai com mais de 152.000 CCTVs e gravadores de vídeo digitais (DVRs) foi responsável pelo maior ataque DDoS conhecido até então. Com o pico de tráfego de mais de 1 TB/s, ele derrubou os serviços de hospedagem de uma empresa de hospedagem na web com sede na França.

Em outubro de 2016, os serviços da Dyn, um provedor de serviços de nomes de domínio (DNS), foram atacados, causando interrupções na internet para milhões de usuários nos Estados Unidos e na Europa.

Reproduza o vídeo para ver uma demonstração de como um ataque DDoS baseado em botnet torna os serviços indisponíveis.

Nota: Em dezembro de 2017, três atores americanos de ameaças declararam-se culpados por conspirar para “conduzir ataques DDoS contra sites e empresas de hospedagem na web localizadas nos Estados Unidos e no exterior”. Os três criminosos enfrentam até 10 anos de prisão e 250 mil dólares em multas.

### Ataques de Buffer Overflow

O objetivo de um ator de ameaça ao usar um ataque DoS de estouro de buffer é encontrar uma falha relacionada à memória do sistema em um servidor e explorá-la. Explorar a memória do buffer sobrecarregando-a com valores inesperados geralmente torna o sistema inoperável, criando um ataque DoS.

Por exemplo, um ator de ameaça insere entrada maior do que o esperado pelo aplicativo em execução em um servidor. O aplicativo aceita a grande quantidade de entrada e armazena na memória. O resultado é que ele pode consumir o buffer de memória associado e potencialmente substituir a memória adjacente, eventualmente corrompendo o sistema e fazendo com que ele falhe.

Um exemplo inicial do uso de pacotes mal formados foi o **Ping of Death**. Nesse ataque herdado, o ator de ameaça enviou um ping de morte, que era uma solicitação de eco em um pacote IP maior que o tamanho máximo de pacote de 65.535 bytes. O host receptor não seria capaz de lidar com um pacote desse tamanho e ele iria falhar.

Os ataques de estouro de buffer estão evoluindo continuamente. Por exemplo, uma vulnerabilidade de ataque remoto de negação de serviço foi descoberta recentemente no Microsoft Windows 10. Especificamente, um ator de ameaça criou código malicioso para acessar memória fora do escopo. Quando esse código é acessado pelo processo AHCACHE.SYS do Windows, ele tenta acionar uma falha do sistema, negando serviço ao usuário. Pesquise na Internet no “blog TALOS-2016-0191” para acessar o site de inteligência de ameaças Cisco Talos e ler uma descrição de tal ataque.

**Observação**: Estima-se que um terço dos ataques mal-intencionados sejam o resultado de estouros de buffer.

### Métodos de Evasão

Atores de ameaça aprenderam há muito tempo que “esconder é prosperar”. Isso significa que seus métodos de malware e ataque são mais eficazes quando não são detectados. Por esta razão, muitos ataques usam técnicas de evasão furtiva para disfarçar uma carga útil de ataque. Seu objetivo é evitar a detecção, evitando defesas de rede e host.

Alguns dos métodos de evasão usados por atores ameaçadores incluem:![[Pasted image 20250122205639.png]]
Novos métodos de ataque estão constantemente sendo desenvolvidos. O pessoal de segurança da rede deve estar ciente dos métodos de ataque mais recentes para detectá-los.