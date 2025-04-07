### Dispositivos Finais

Os dispositivos de rede com os quais as pessoas estão mais familiarizadas são dispositivos finais. Para distinguir um dispositivo final de outro, cada dispositivo final em uma rede tem um endereço. Quando um dispositivo final inicia a comunicação, ele usa o endereço do dispositivo final de destino para especificar onde entregar a mensagem.

### Roteadores

Os roteadores são dispositivos que operam na camada de rede OSI (Camada 3). Conforme mostrado na figura, os roteadores são usados para interconectar sites remotos. Eles usam o processo de roteamento para encaminhar pacotes de dados entre redes. O processo de roteamento usa tabelas de roteamento de rede, protocolos e algoritmos para determinar o caminho mais eficiente para encaminhar um pacote IP. Os roteadores coletam informações de roteamento e atualizam outros roteadores sobre alterações na rede. Os roteadores aumentam a escalabilidade das redes segmentando domínios de transmissão.
![[Pasted image 20250115212245.png]]

Os roteadores têm duas funções principais: determinação de caminho e encaminhamento de pacotes. Para executar a determinação do caminho, cada roteador constrói e mantém uma tabela de roteamento que é um banco de dados de redes conhecidas e como alcançá-las. A tabela de roteamento pode ser criada manualmente e conter rotas estáticas ou pode ser construída usando um protocolo de roteamento dinâmico.

O encaminhamento de pacotes é realizado usando uma função de comutação. A comutação é o processo usado por um roteador para aceitar um pacote em uma interface e encaminhá-lo para outra interface. Uma responsabilidade primária da função de comutação é encapsular os pacotes no tipo de quadro de enlace de dados apropriado para o enlace de dados de saída.

Depois que o roteador determinar a interface de saída utilizando a função de determinação do caminho, ele deverá encapsular o pacote no quadro de enlace de dados da interface de saída.

O que um roteador faz com um pacote recebido de uma rede e destinado a outra rede? O roteador executa as três etapas principais seguintes:

1. Ele desencapsula o cabeçalho e o trailer do quadro da Camada 2 para expor o pacote da Camada 3.

2. Ele examina o endereço IP de destino do pacote IP para encontrar o melhor caminho na tabela de roteamento.

3. Se o roteador encontrar um caminho para o destino, ele encapsula o pacote da Camada 3 em um novo quadro da Camada 2 e encaminha esse quadro pela interface de saída.

Conforme mostrado na figura, os dispositivos têm endereços IPv4 da Camada 3, enquanto as interfaces Ethernet têm endereços de enlace de dados da Camada 2. Os endereços MAC são encurtados para simplificar a ilustração. Por exemplo, o PC1 é configurado com um endereço IPv4 192.168.1.10 e um endereço MAC de exemplo de 0A-10. À medida que um pacote vai do dispositivo origem para o dispositivo destino, os endereços IP de Camada 3 não são alterados. Isso ocorre porque a PDU da Camada 3 não se altera. No entanto, os endereços de enlace de dados da Camada 2 mudam em cada roteador no caminho para o destino, à medida que o pacote é desencapsulado e reencapsulado em um novo quadro da Camada 2.
![[Pasted image 20250115212602.png]]

### Processo de decisão de encaminhamento de pacotes

Agora que o roteador determinou o melhor caminho para um pacote com base na correspondência mais longa, ele deve determinar como encapsular o pacote e encaminhá-lo para a interface de saída correta.

![[Pasted image 20250115212916.png]]

As etapas a seguir descrevem o processo de encaminhamento de pacotes mostrado na figura:

1. O quadro de enlace de dados com um pacote IP encapsulado chega na interface de entrada.
2. O roteador examina o endereço IP de destino no cabeçalho do pacote e consulta sua tabela de roteamento IP.
3. O roteador localiza o prefixo correspondente mais longo na tabela de roteamento.
4. O roteador encapsula o pacote em um quadro de enlace de dados e o encaminha para fora da interface de saída. O destino pode ser um dispositivo conectado à rede ou um roteador de próximo salto.
5. No entanto, se não houver nenhuma entrada de rota correspondente, o pacote será descartado.

**Encaminha o pacote para um dispositivo em uma rede conectada diretamente**
Se a entrada de rota indicar que a interface de saída é uma rede conectada diretamente, isso significa que o endereço IP de destino do pacote pertence a um dispositivo na rede diretamente conectada. Portanto, o pacote pode ser encaminhado diretamente para o dispositivo de destino. O dispositivo de destino geralmente é um dispositivo final em uma LAN Ethernet, o que significa que o pacote deve ser encapsulado em um quadro Ethernet.

Para encapsular o pacote no quadro Ethernet, o roteador precisa determinar o endereço MAC de destino associado ao endereço IP de destino do pacote. O processo varia com base em se o pacote é um pacote IPv4 ou IPv6:

- **Pacote IPv4** - O roteador verifica sua tabela ARP para o endereço IPv4 de destino e um endereço MAC Ethernet associado. Se não houver correspondência, o roteador enviará uma Solicitação ARP. O dispositivo de destino retornará uma resposta ARP com seu endereço MAC. O roteador agora pode encaminhar o pacote IPv4 em um quadro Ethernet com o endereço MAC de destino apropriado.
- **Pacote IPv6** - O roteador verifica seu cache vizinho para o endereço IPv6 de destino e um endereço MAC Ethernet associado. Se não houver correspondência, o roteador enviará uma mensagem ICMPv6 Neighbor Solicitation (NS). O dispositivo de destino retornará uma mensagem de anúncio de vizinho (NA) ICMPv6 com seu endereço MAC. O roteador agora pode encaminhar o pacote IPv6 em um quadro Ethernet com o endereço MAC de destino apropriado.

**Encaminha o pacote para um roteador Next-Hop**
Se a entrada de rota indicar que o endereço IP de destino está em uma rede remota, isso significa que o endereço IP de destino do pacote pertence a um dispositivo na rede que não está conectado diretamente. Portanto, o pacote deve ser encaminhado para outro roteador, especificamente um roteador de próximo salto. O endereço do próximo salto é indicado na entrada da rota.

Se o roteador de encaminhamento e o roteador de próximo salto estiverem em uma rede Ethernet, ocorrerá um processo semelhante (ARP e ICMPv6 Neighbor Discovery) para determinar o endereço MAC de destino do pacote, conforme descrito anteriormente. A diferença é que o roteador procurará o endereço IP do roteador próximo salto em sua tabela ARP ou cache vizinho, em vez do endereço IP de destino do pacote.

**Observação:** Este processo irá variar para outros tipos de redes da Camada 2.

**Elimina o pacote - Nenhuma correspondência na tabela de roteamento**

Se não houver correspondência entre o endereço IP de destino e um prefixo na tabela de roteamento, e se não houver rota padrão, o pacote será descartado.

### Informação de Roteamento

A tabela de roteamento de um roteador armazena as seguintes informações:

- **Rotas conectadas diretamente** - essas rotas vêm das interfaces ativas do roteador. Os roteadores adicionam uma rota diretamente conectada quando uma interface está configurada com um endereço IP e está ativada.
- **Rotas remotas** - são redes remotas conectadas a outros roteadores. As rotas para essas redes podem ser configuradas estaticamente ou ser dinamicamente aprendidas através de protocolos de roteamento dinâmico.

Especificamente, uma tabela de roteamento é um arquivo de dados na RAM que é usado para armazenar informações sobre redes diretamente conectadas e remotas. A tabela de roteamento contém a rede ou associações do próximo salto. Essas associações informam ao roteador que um determinado destino pode ser acessado de modo ideal com o envio do pacote a um roteador específico que representa o próximo salto no caminho até o destino final. A associação do próximo salto também pode ser a interface de saída para o próximo destino.

As entradas de rede de destino na tabela de roteamento podem ser adicionadas de várias maneiras:

- **Interfaces de rota local** - Adicionadas quando uma interface está configurada e ativa. Esta entrada só é exibida no IOS 15 ou mais recente para rotas IPv4 e em todas as versões do IOS para rotas IPv6.
- **Interfaces diretamente conectadas** - Adicionadas à tabela de roteamento quando uma interface está configurada e ativa.
- **Rotas estáticas** - Adicionadas quando uma rota é configurada manualmente e a interface de saída está ativa.
- **Protocolo de roteamento dinâmico** - Adicionado quando protocolos de roteamento que aprendem dinamicamente sobre a rede, como EIGRP ou OSPF, são implementados e redes são identificadas.

Protocolos de roteamento dinâmico trocam informações de acessibilidade de rede entre roteadores e se adaptam dinamicamente às alterações de rede. Cada protocolo de roteamento usa algoritmos de roteamento para determinar os melhores caminhos entre diferentes segmentos na rede e atualiza tabelas de roteamento com esses caminhos.

Os protocolos de roteamento dinâmico foram usados em redes desde o final da década de 80. Um dos primeiros protocolos de roteamento foi o RIP. RIPv1 foi lançado em 1988. Como as redes evoluíram e se tornaram mais complexas, surgiram novos protocolos de roteamento. O protocolo RIP foi atualizado para RIPv2 para acomodar o crescimento no ambiente de rede. No entanto, o RIPv2 ainda não é escalável nas implementações de redes maiores atuais. Para atender às necessidades de redes maiores foram desenvolvidos dois protocolos de roteamento avançados: OSPF (Open Shortest Path First) e IS-IS (Intermediate System-to-Intermediate System). A Cisco desenvolveu o IGRP (Interior Gateway Routing Protocol) e EIGRP (enhanced IGRP), que também é escalável nas implementações de redes maiores.

Além disso, há a necessidade de conectar diferentes redes interconectadas e de proporcionar roteamento entre elas. O Border Gateway Protocol (BGP) agora é usado entre provedores de serviços de Internet (ISPs). O BGP também é usado entre ISPs e seus grandes clientes privados para trocar informações de roteamento.

A tabela classifica os protocolos. Os roteadores configurados com esses protocolos enviarão mensagens periodicamente para outros roteadores. Como analista de segurança cibernética, você verá essas mensagens em vários logs e capturas de pacotes.
![[Pasted image 20250115213505.png]]

### Encaminhamento de ponta a ponta

A principal responsabilidade da função de encaminhamento de pacotes é encapsular pacotes no tipo de quadro de vínculo de dados apropriado para a interface de saída. Por exemplo, o formato de quadro de enlace de dados para um link serial pode ser o protocolo PPP (Point-to-Point), o protocolo HDLC (High-Level Data Link Control) ou algum outro protocolo de Camada 2.

### Hubs, Bridges, LAN Switches

Um hub Ethernet atua como um repetidor de várias portas que recebe um sinal elétrico de entrada (dados) em uma porta. Em seguida, encaminha imediatamente um sinal regenerado para todas as outras portas. Os hubs usam processamento de camada física para encaminhar dados. They do not look at the source and destination MAC address of the Ethernet frame. Os hubs conectam a rede a uma topologia em estrela com o hub como ponto de conexão central. Quando dois ou mais dispositivos finais conectados a um hub enviam dados ao mesmo tempo, ocorre uma colisão elétrica, corrompendo os sinais. Todos os dispositivos conectados a um hub pertencem ao mesmo domínio de colisão. Apenas um dispositivo pode transmitir tráfego em um determinado momento em um domínio de colisão. Se ocorrer uma colisão, os dispositivos finais usam a lógica CSMA/CD para evitar a transmissão até que a rede fique sem tráfego. Devido ao baixo custo e à superioridade da comutação Ethernet, os hubs raramente são usados hoje.

As pontes têm duas interfaces e estão conectadas entre hubs para dividir a rede em vários domínios de colisão. Cada domínio de colisão pode ter apenas um remetente de cada vez. As colisões são isoladas pela ponte para um único segmento e não afetam dispositivos em outros segmentos. Assim como um switch, uma ponte toma decisões de encaminhamento com base em endereços MAC Ethernet. As pontes raramente são usadas em redes modernas.

Switches LAN são essencialmente pontes multiportas que conectam dispositivos a uma topologia em estrela. Assim como pontes, os switches segmentam uma LAN em domínios de colisão separados, um para cada porta de switch. Um switch toma decisões de encaminhamento com base em endereços MAC Ethernet.

### Operação de Switch

Os switches usam endereços MAC para direcionar as comunicações de rede através do switch, para a porta apropriada e em direção ao destino. Um switch é composto de circuitos integrados e de um software que controla os caminhos dos dados através do switch. Para que um switch saiba qual porta usar para transmitir um quadro, primeiro ele deve saber quais dispositivos existem nas portas. Conforme o switch aprende a relação das portas com os dispositivos, ele constrói uma tabela chamada tabela de endereços MAC ou tabela de memória endereçável de conteúdo (CAM). A CAM é um tipo especial de memória usado em aplicativos de pesquisa em alta velocidade.

Os switches LAN determinam como lidar com quadros de dados de entrada mantendo a tabela de endereços MAC. Um switch constrói sua tabela de endereços MAC registrando o endereço MAC de cada dispositivo conectado a cada uma de suas portas. O switch usa as informações da tabela de endereços MAC para enviar frames destinados a um dispositivo específico pela porta à qual o dispositivo está conectado.

O processo de duas etapas a seguir é executado em todos os quadros Ethernet que entram em um switch.

**1. Aprendizagem - Exame do Endereço MAC de Origem**

Cada quadro que entra em um switch é verificado para novas informações de endereço MAC que podem precisar ser aprendidas. Ele faz isso examinando o endereço MAC de origem do quadro e o número da porta onde o quadro entrou no switch. Se o endereço MAC de origem não estiver na tabela, ele será adicionado à tabela de endereços MAC junto com o número da porta de entrada, conforme mostrado na figura. Se o endereço MAC de origem não existir na tabela, o switch atualizará o cronômetro de atualização para essa entrada. Por padrão, a maioria dos switches Ethernet mantém uma entrada na tabela por cinco minutos.
![[Pasted image 20250115214126.png]]

**Observação:** se o endereço MAC de origem existe na tabela, mas em outra porta, o switch trata como uma nova entrada. A entrada é substituída usando o mesmo endereço MAC, mas com o número de porta mais atual.

**2. Encaminhamento - Exame do Endereço MAC de Destino**

Se o endereço MAC de destino for um endereço unicast, o switch procurará uma correspondência entre o endereço MAC de destino do quadro e uma entrada em sua tabela de endereços MAC. Se o endereço MAC de destino estiver na tabela, ele encaminhará o quadro pela porta especificada. Se o endereço MAC de destino não estiver na tabela, o switch encaminhará o quadro por todas as portas, exceto a porta de entrada, conforme mostrado na figura. Isso é chamado de unicast desconhecido.
![[Pasted image 20250115214306.png]]

**Observação:** se o endereço MAC de destino for um endereço de broadcast ou multicast, o quadro será enviado por todas as portas, exceto a de entrada.

### VLANs

Dentro de uma rede comutada, as VLANs fornecem segmentação e flexibilidade organizacional. As VLANs oferecem uma maneira de agrupar dispositivos dentro de uma LAN. Um grupo de dispositivos em uma VLAN se comunica como se estivessem conectados ao mesmo segmento de rede. As VLANs são baseadas em conexões lógicas, em vez de conexões físicas.

VLANs permitem que um administrador segmente redes com base em fatores como função, equipe de projeto ou aplicativo, sem levar em conta a localização física do usuário ou dispositivo,
Os dispositivos em uma VLAN atuam como se estivessem em sua própria rede independente, mesmo que compartilhem uma infraestrutura comum com outras VLANs. Qualquer porta do switch pode pertencer a uma VLAN. Pacotes de unicast, broadcast e multicast são encaminhados e inundados apenas para dispositivos finais na VLAN onde os pacotes são fornecidos. Cada VLAN é considerada uma rede lógica separada. Os pacotes destinados aos dispositivos que não pertencem a VLANs devem ser roteados por um dispositivo que permita roteamento.

Uma VLAN é um domínio de broadcast que pode abranger vários segmentos de LAN físicos. As VLANs melhoram o desempenho da rede, separando grandes domínios de transmissão em domínios menores. Se um dispositivo em uma VLAN envia um quadro Ethernet de transmissão, todos os dispositivos na VLAN recebem o quadro, mas os dispositivos em outras VLANs não.

As VLANs também impedem que usuários em VLANs diferentes espiem o tráfego uns dos outros. Por exemplo, mesmo que o RH e as Vendas estejam conectados ao mesmo switch na figura, o switch não encaminhará o tráfego entre as VLANs de RH e de Vendas. Isso permite que um roteador ou outro dispositivo use listas de controle de acesso para permitir ou negar o tráfego. As listas de acesso são discutidas com mais detalhes posteriormente neste capítulo. Por enquanto, lembre-se de que as VLANs podem ajudar a limitar a quantidade de visibilidade de dados em suas LANs.

### STP

Redundância de rede é primordial para a manutenção da confiabilidade da rede. Diversos links físicos entre dispositivos propiciam caminhos redundantes. A rede poderá continuar a operar quando um único link ou porta tiver falhado. Links redundantes também podem compartilhar a carga de tráfego e aumentar a capacidade.

Vários caminhos precisam ser gerenciados de modo que os loops de Camada 2 não sejam criados. Os melhores caminhos são selecionados e um caminho alternativo fica prontamente disponível se o caminho principal falhar. O Spanning Tree Protocol é usado para manter um caminho livre de loop na rede da Camada 2, a qualquer momento.

A redundância aumenta a disponibilidade da topologia de rede, protegendo-a de um único ponto de falha, como um cabo ou um switch com falha na rede. Quando a redundância física é introduzida em um projeto, ocorrem loops e quadros duplicados. Os loops e quadros duplicados têm consequências graves para uma rede comutada. O STP foi desenvolvido para resolver esses problemas.

O STP garante que há apenas um caminho lógico entre todos os destinos da rede, bloqueando intencionalmente os caminhos redundantes que podem causar um loop. Uma porta é considerada bloqueada quando os dados do usuário são impedidos de entrar ou de sair daquela porta. Isso não inclui os quadros da unidade de dados de protocolo de bridge (BPDU) que são usados pelo STP para evitar loops. Bloquear os caminhos redundantes é fundamental para evitar loops na rede. Os caminhos físicos ainda existirão para fornecer redundância, mas esses caminhos ficarão desativados para evitar que ocorram loops. Se o caminho for necessário em algum momento para compensar uma falha no cabo ou switch de rede, o STP recalculará os caminhos e desbloqueará as portas necessárias para permitir que o caminho redundante torne-se ativo.

### Comutação Multilayer

Switches multicamadas (também conhecidos como switches de Camada 3) não apenas executam switching de Camada 2, mas também quadros de encaminhamento baseados em informações de Camadas 3 e 4. Todos os switches multicamadas Cisco Catalyst suportam os seguintes tipos de interfaces da Camada 3:

- **Porta roteada** - Uma interface pura de Camada 3 semelhante a uma interface física em um roteador Cisco IOS.
- **Interface virtual do switch (SVI)** - Uma interface de VLAN virtual para o roteamento entre VLANs. Em outras palavras SVIs são as interfaces de VLAN roteadas virtuais.

**Portas roteadas**

Uma porta roteada é uma porta física que atua de forma semelhante a uma interface em um roteador, conforme mostrado na figura. Diferentemente de uma porta de acesso, uma porta roteada não está associada a uma VLAN. Uma porta roteada se comporta como uma interface de roteador regular. Além disso, como a funcionalidade de Camada 2 foi removida, os protocolos de Camada 2, como o STP, não funcionam em uma interface roteada. Entretanto, alguns protocolos, como LACP e EtherChannel, funcionam na Camada 3. Diferentemente dos roteadores Cisco IOS, as portas roteadas em um switch Cisco IOS não suportam subinterfaces.
![[Pasted image 20250115214945.png]]

**Interfaces virtuais do switch**

Uma SVI é uma interface virtual configurada em um switch multicamada, como mostrado na figura. Ao contrário dos switches básicos de Camada 2 discutidos acima, um switch multicamada pode ter vários SVIs. Uma SVI pode ser criada para qualquer VLAN que exista no switch. Uma SVI é considerada virtual porque não há uma porta física dedicada à interface. Ela pode executar as mesmas funções para a VLAN que uma interface de roteador e pode ser configurada de forma similar a uma interface do roteador (isto é, endereço IP, ACLs de entrada/saída etc,). A SVI para a VLAN fornece o processamento de Camada 3 para pacotes para ou de todas as portas de switch associadas a essa VLAN.
![[Pasted image 20250115215033.png]]

# Comunicações sem fio

### LANs sem fio versus com fio

As WLANs usam Freqüências de Rádio (RF) em vez de cabos na camada física e na subcamada MAC da camada de enlace de dados. As WLANs compartilham uma origem semelhante com as LANs Ethernet. O IEEE adotou o portfólio 802 LAN/MAN de padrões de arquitetura de rede de computadores. Os dois grupos de trabalho dominantes 802 são 802.3 Ethernet, que definiu Ethernet para LANs com fio, e 802.11 que definiu Ethernet para WLANs. Existem diferenças importantes entre os dois.

As WLANs também diferem das LANs com fio da seguinte forma:

- As WLANs conectam clientes à rede por meio de um ponto de acesso sem fio (AP) ou roteador sem fio, em vez de um switch Ethernet.
- As WLANs conectam dispositivos móveis que geralmente são alimentados por bateria, em vez de dispositivos LAN conectados. As placas de rede sem fio tendem a reduzir a duração da bateria de um dispositivo móvel.
- WLANs suportam hosts que disputam acesso na mídia de RF (bandas de frequência). O 802.11 prescreve a prevenção de colisões (CSMA/CA) em vez de detecção de colisões (CSMA/CD) para acesso à mídia para evitar colisões proativamente dentro da mídia.
- As WLANs usam um formato de quadro diferente das LANs Ethernet com fio. As WLANs exigem informações adicionais no cabeçalho da Camada 2 do quadro.
- As WLANs levantam mais problemas de privacidade porque as frequências de rádio podem chegar fora das instalações.

A tabela resume as diferenças entre LANs sem fio e com fio.

![[Pasted image 20250117202150.png]]

### Estutura do quadro 802.11

Lembre-se de que todos os quadros da camada 2 consistem em uma seção de cabeçalho, carga útil e sequência de verificação de quadro (FCS - Frame Check Sequence). O formato de quadro 802.11 é semelhante ao formato de quadro Ethernet, exceto pelo fato de conter mais campos, conforme mostrado na figura.
![[Pasted image 20250117202230.png]]

Todos os quadros sem fio 802.11 contêm os seguintes campos:

- **Controle do quadro** - Isso identifica o tipo de quadro sem fio e contém subcampos para versão do protocolo, tipo de quadro, tipo de endereço, gerenciamento de energia e configurações de segurança.
- **Duração** - Isso é normalmente usado para indicar a duração restante necessária para receber a próxima transmissão de quadro.
- **Endereço1** - Geralmente, contém o endereço MAC do dispositivo sem fio ou AP de recebimento.
- **Endereço2** - Geralmente, contém o endereço MAC do dispositivo sem fio transmissor ou ponto de acesso
- **Endereço3** - Às vezes, isso contém o endereço MAC do destino, como a interface do roteador (gateway padrão) à qual o ponto de acesso está conectado.
- **Controle de sequencia** - Ele contém informações para controlar o seqüenciamento e os quadros fragmentados.
- **Endereço4** - Isso geralmente está ausente porque é usado apenas no modo ad hoc.
- **Payload** - Este contém os dados para transmissão.
- **FCS** - Isso é usado para controle de erro da camada 2.

### CSMA/CA

As WLANs são configurações de mídia compartilhada half-duplex. Half-duplex significa que apenas um cliente pode transmitir ou receber a qualquer momento. Mídia compartilhada significa que todos os clientes sem fio podem transmitir e receber no mesmo canal de rádio. Isso cria um problema porque um cliente sem fio não pode ouvir enquanto está enviando, o que torna impossível detectar uma colisão.

Para resolver esse problema, as WLANs usam o acesso múltiplo com detecção de operadora com prevenção de colisão (CSMA / CA) como o método para determinar como e quando enviar dados na rede. Um cliente sem fio faz o seguinte:

1. Ouve o canal para ver se ele está ocioso, o que significa que nenhum outro tráfego está atualmente no canal. O canal também é chamado de portadora.
2. Envia uma mensagem pronta para enviar (RTS) para o ponto de acesso para solicitar acesso dedicado à rede.
3. Recebe uma mensagem clara para enviar (CTS) do ponto de acesso que concede acesso ao envio.
4. Se o cliente sem fio não receber uma mensagem CTS, ele aguardará um período aleatório antes de reiniciar o processo.
5. Depois de receber o CTS, ele transmite os dados.
6. Todas as transmissões são confirmadas. Se um cliente sem fio não receber uma confirmação, ele assume uma colisão e reinicia o processo.

### Associação de cliente sem fio e ponto de acesso

Para que os dispositivos sem fio se comuniquem através de uma rede, eles devem primeiro se associar a um Ponto de acesso ou roteador sem fio. Uma parte importante do processo 802.11 é descobrir uma WLAN e subsequentemente conectar-se a ela. Os dispositivos sem fio concluem o seguinte processo de três estágios, conforme mostrado na figura:

- Descobrir um ponto de acesso sem fio
- Autenticar-se no ponto de acesso
- Associar-se ao ponto de acesso
![[Pasted image 20250117202511.png]]

Para ter uma associação bem-sucedida, um cliente sem fio e um ponto de acesso devem concordar com parâmetros específicos. Os parâmetros devem ser configurados no ponto de acesso e subseqüentemente no cliente para permitir a negociação de uma associação bem-sucedida.

- **SSID** - O nome SSID aparece na lista de redes sem fio disponíveis em um cliente. Em organizações maiores que usam várias VLANs para segmentar o tráfego, cada SSID é mapeado para uma VLAN. Dependendo da configuração da rede, vários pontos de acesso em uma rede podem compartilhar um SSID comum.
- **Senha** - Isso é necessário no cliente sem fio para se autenticar no ponto de acesso.
- **Modo de rede** - refere-se aos padrões de WLAN 802.11a/b/g/n/ac/ad. Os pontos de acesso e roteadores sem fio podem operar no modo misto, o que significa que eles podem oferecer suporte simultâneo a clientes que se conectam por vários padrões.
- **Modo de segurança** - Isso se refere às configurações de parâmetros de segurança, como WEP, WPA ou WPA2. Sempre habilite o nível de segurança mais alto suportado.
- **Configurações do canal** - Refere-se às bandas de frequência usadas para transmitir dados sem fio. Os roteadores sem fio e os APs podem verificar os canais de frequência de rádio e selecionar automaticamente uma configuração de canal apropriada. O canal também pode ser configurado manualmente se houver interferência com outro ponto de acesso ou dispositivo sem fio.

### Modo de descoberta passiva e ativa

Os dispositivos sem fio devem descobrir e conectar-se a um ponto de acesso ou roteador sem fio. Os clientes sem fio se conectam ao ponto de acesso usando um processo de verificação (verificação). Este processo pode ser passivo ou ativo.

**Modo passivo**

No modo passivo, o ponto de acesso anuncia abertamente seu serviço enviando periodicamente quadros de beacon de transmissão contendo o SSID, padrões suportados e configurações de segurança. O objetivo principal do beacon é permitir que os clientes sem fio aprendam quais redes e pontos de acesso estão disponíveis em uma determinada área. Isso permite que os clientes sem fio escolham qual rede e ponto de acesso usar.
![[Pasted image 20250117202746.png]]

**Modo ativo**

No modo ativo, os clientes sem fio devem saber o nome do SSID. O cliente sem fio inicia o processo transmitindo um quadro de solicitação de análise em vários canais. A solicitação de análise inclui o nome SSID e os padrões suportados. Os pontos de acesso configurados com o SSID enviarão uma resposta do probe que inclui o SSID, os padrões suportados e as configurações de segurança. O modo ativo pode ser necessário se um ponto de acesso ou roteador sem fio estiver configurado para não transmitir quadros de beacon.

Um cliente sem fio também pode enviar uma solicitação de análise sem um nome SSID para descobrir redes WLAN próximas. Os pontos de acesso configurados para transmitir quadros de beacon responderiam ao cliente sem fio com uma resposta do probe e forneceriam o nome SSID. Os pontos de acesso com o recurso SSID de transmissão desativado não respondem.
![[Pasted image 20250117202854.png]]

### Dispositivos sem fio - AP, LWAP e WLC

Uma implementação comum de dados sem fio permite que dispositivos se conectem sem fio por meio de uma LAN. Em geral, uma LAN sem fio requer pontos de acesso sem fio e clientes que tenham NICs sem fio. Os roteadores sem fio domésticos e de pequenas empresas integram as funções de um roteador, comutador e ponto de acesso em um dispositivo. Observe que em redes pequenas, o roteador sem fio pode ser o único AP porque apenas uma área pequena requer cobertura sem fio. Em redes maiores, pode haver muitos APs.

Todas as funções de controle e gerenciamento dos APs em uma rede podem ser centralizadas em um Wireless LAN Controller (WLC). Ao usar uma WLC, os APs não atuam mais de forma autônoma, mas atuam como APs leves (LWAPs). Os LWAPs apenas encaminham dados entre a LAN sem fio e a WLC. Todas as funções de gerenciamento, como definição de SSIDs e autenticação, são conduzidas na WLC centralizada, em vez de em cada AP individual. Um grande benefício da centralização das funções de gerenciamento de AP na WLC é a configuração simplificada e o monitoramento de vários pontos de acesso, entre muitos outros benefícios.

