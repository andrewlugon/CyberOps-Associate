### Encapsulamento Ethernet

Ethernet e LAN sem fio (WLANs) são as duas tecnologias LAN mais comumente implantadas. Ao contrário da rede sem fio, a Ethernet usa comunicações com fio, incluindo par trançado, links de fibra óptica e cabos coaxiais.

Ela opera na camada de enlace de dados e na camada física. É uma família de tecnologias de rede definidas nos padrões IEEE 802.2 e 802.3. Ethernet oferece suporte às seguintes larguras de banda de dados:

- 10 Mbps
- 100 Mbps
- 1000 Mbps (1 Gbps)
- 10,000 Mbps (10 Gbps)
- 40,000 Mbps (40 Gbps)
- 100,000 Mbps (100 Gbps)
![[Pasted image 20241226192350.png]]

### Campos de um Quadro Ethernet

O tamanho mínimo de quadro Ethernet é 64 bytes e o máximo é 1518 bytes. Isso inclui todos os bytes do campo de endereço MAC de destino através do campo FCS (Frame Check Sequence). O campo de preâmbulo não é incluído ao descrever o tamanho do quadro.

Qualquer quadro com comprimento menor que 64 bytes é considerado um"fragmento de colisão" ou um "quadro desprezível" e é automaticamente descartado pelas estações receptoras. Quadros com mais de 1.500 bytes de dados são considerados “jumbo” ou “baby giant”.

Se o tamanho de um quadro transmitido for menor que o mínimo ou maior que o máximo, o dispositivo receptor descarta o quadro. É provável que quadros perdidos sejam resultado de colisões ou outros sinais indesejados. Eles são considerados inválidos. No entanto, as interfaces Fast Ethernet e Gigabit Ethernet de alguns switches Cisco Catalyst podem ser configuradas para suportar quadros jumbo maiores.
![[Pasted image 20241226192508.png]]

### Formato do Endereço MAC

Equivalentes decimais e binários de 0 a F Hexadecimal
![[Pasted image 20241226192625.png]]

Um endereço MAC Ethernet é um valor binário de 48 bits expresso como 12 dígitos hexadecimais (4 bits por dígito hexadecimal). Os dígitos hexadecimais usam os números de 0 a 9 e as letras de A a F. A figura mostra os valores decimais e hexadecimais equivalentes para 0000 a 1111 binários. Hexadecimal é comumente usado para representar dados binários. Endereços IPv6 são outro exemplo de endereçamento hexadecimal.

Dependendo do dispositivo e do sistema operacional, você verá várias representações de endereços MAC.

# IPv4

### A camada de Rede

A camada de rede, ou Camada OSI 3, fornece serviços para permitir que dispositivos finais troquem dados entre redes. Como mostrado na figura, IP versão 4 (IPv4) e IP versão 6 (IPv6) são os principais protocolos de comunicação de camada de rede. Outros protocolos de camada de rede incluem protocolos de roteamento, como OSPF (Open Shortest Path First) e protocolos de mensagens, como ICMP (Internet Control Message Protocol).
![[Pasted image 20241226192902.png]]

Para realizar comunicações de ponta a ponta através dos limites da rede, os protocolos de camada de rede executam quatro operações básicas:

- **Endereçamento de dispositivos finais** - Os dispositivos finais devem ser configurados com um endereço IP exclusivo para identificação na rede.
- **Encapsulamento** - A camada de rede encapsula a unidade de dados de protocolo (PDU) da camada de transporte em um pacote. O processo de encapsulamento adiciona informações de cabeçalho IP, como os endereços IP dos hosts origem (emissor) e destino (receptor). O processo de encapsulamento é executado pela origem do pacote IP.
- **Roteamento** - A camada de rede fornece serviços para direcionar os pacotes para um host de destino em outra rede. Para trafegar para outras redes, o pacote deve ser processado por um roteador. A função do roteador é escolher o melhor caminho e direcionar os pacotes para o host de destino em um processo conhecido como roteamento. Um pacote pode atravessar muitos roteadores antes de chegar ao host de destino. Cada roteador que um pacote atravessa para chegar ao host de destino é chamado de salto.
- **Desencapsulamento** - Quando o pacote chega à camada de rede do host de destino, o host verifica o cabeçalho IP do pacote. Se o endereço IP de destino no cabeçalho corresponder ao seu próprio endereço IP, o cabeçalho IP será removido do pacote. Depois que o pacote é desencapsulado pela camada de rede, a PDU resultante da Camada 4 é transferida para o serviço apropriado na camada de transporte. O processo de desencapsulamento é executado pelo host de destino do pacote IP.

Diferentemente da camada de transporte (OSI Layer 4), que gerencia o transporte de dados entre os processos em execução em cada host, os protocolos de comunicação da camada de rede (ou seja, IPv4 e IPv6) especificam a estrutura de pacotes e o processamento usado para transportar os dados de um host para outro hospedeiro. A operação sem levar em consideração os dados contidos em cada pacote permite que a camada de rede transporte pacotes para diversos tipos de comunicações entre vários hosts.

### Encapsulamento IP

O IP encapsula o segmento da camada de transporte (a camada logo acima da camada de rede) ou outros dados adicionando um cabeçalho IP. O cabeçalho IP é usado para entregar o pacote ao host de destino.

O processo de encapsulamento camada por camada possibilita o desenvolvimento e a expansão dos serviços nas diferentes camadas sem afetar outras camadas. Isso significa que os segmentos da camada de transporte podem ser imediatamente empacotados por IPv4 , IPv6 ou qualquer protocolo que venha a ser desenvolvido no futuro.

O cabeçalho IP é examinado por dispositivos de Camada 3 (ou seja, roteadores e switches de Camada 3) à medida que viaja através de uma rede até seu destino. É importante notar que as informações de endereçamento IP permanecem as mesmas desde o momento em que o pacote sai do host de origem até chegar ao host de destino, exceto quando traduzidas pelo dispositivo que executa a Tradução de Endereços de Rede (NAT) para IPv4.

**Observação**: O NAT é discutido em módulos posteriores.

Os roteadores implementam protocolos de roteamento para rotear pacotes entre redes. O roteamento realizado por esses dispositivos intermediários examina o endereçamento da camada de rede no cabeçalho do pacote. Em todos os casos, a parte de dados do pacote, ou seja, a PDU da camada de transporte encapsulada ou outros dados, permanece inalterada durante os processos da camada de rede.

### Características do IP

IP foi desenvolvido como um protocolo com baixa sobrecarga. Ele fornece apenas as funções necessárias para enviar um pacote de uma origem a um destino por um sistema interconectado de redes. O protocolo não foi projetado para rastrear e gerenciar o fluxo de pacotes. Essas funções, se exigido, são realizadas por outros protocolos em outras camadas, principalmente TCP na Camada 4.

Estas são as características básicas da IP:

- **Sem conexão** - Não há conexão com o destino estabelecido antes do envio de pacotes de dados.
- **Melhor esforço** - o IP é inerentemente não confiável, porque a entrega de pacotes não é garantida.
- **Independente da mídia** - A operação é independente do meio (ou seja, cobre, fibra ótica ou sem fio) que carrega os dados.

### Sem Conexão

O IP não tem conexão, o que significa que nenhuma conexão ponta a ponta dedicada é criada pelo IP antes que os dados sejam enviados. A comunicação sem conexão é conceitualmente semelhante a enviar uma carta a alguém sem notificar o destinatário com antecedência. 

### Melhor esforço

O IP também não requer campos adicionais no cabeçalho para manter uma conexão estabelecida. Esse processo reduz bastante a sobrecarga do IP. No entanto, sem conexão de ponta a ponta pré-estabelecida, os remetentes não sabem se os dispositivos de destino estão presentes e funcionais ao enviar pacotes, nem sabem se o destino recebe o pacote ou se o dispositivo de destino pode acessar e ler o pacote.

O protocolo IP não garante que o pacote enviado seja, de fato, recebido.

### Independente de Mídia

Não confiável significa que o IP não tem a capacidade de gerenciar e recuperar pacotes não entregues ou corrompidos. Isso ocorre porque, embora os pacotes IP sejam enviados com informações sobre o local da entrega, eles não contêm informações que podem ser processadas para informar ao remetente se a entrega foi bem-sucedida. Os pacotes podem chegar ao destino corrompidos, fora de sequência ou simplesmente não chegar. O IP não tem capacidade de retransmitir os pacotes em caso de erros.

Se os pacotes forem entregues fora de ordem ou estiver faltando algum pacote, as aplicações que usam os dados, ou serviços de camada superior, deverão resolver esses problemas. Isso permite que o IP funcione de forma bem eficiente. No conjunto de protocolos TCP / IP, a confiabilidade é o papel do protocolo TCP na camada de transporte.

O IP opera independentemente da mídia que transporta os dados nas camadas inferiores da pilha de protocolos.

A camada de enlace de dados OSI é responsável por pegar um pacote IP e prepará-lo para transmissão pelo meio de comunicação. Isso significa que a entrega de pacotes IP não se limita a nenhum meio específico.

Há, no entanto, uma característica muito importante dos meios físicos que a camada de rede considera: o tamanho máximo da PDU que cada meio consegue transportar. Essa característica é chamada de unidade máxima de transmissão (maximum transmission unit - MTU). Parte das comunicações de controle entre a camada de enlace de dados e a camada de rede é a definição de um tamanho máximo para o pacote. A camada de enlace de dados passa o valor da MTU para a camada de rede. A camada de rede então determina o tamanho que os pacotes podem ter.

Em alguns casos, um dispositivo intermediário, geralmente um roteador, deve dividir um pacote IPv4 ao encaminhá-lo de um meio para outro com uma MTU menor. Esse processo é chamado fragmentação do pacote ou fragmentação. A fragmentação causa latência. Os pacotes IPv6 não podem ser fragmentados pelo roteador.

### Cabeçalho do Pacote IPv4

O IPv4 é um dos principais protocolos de comunicação de camada de rede. O cabeçalho do pacote IPv4 é usado para garantir que esse pacote seja entregue para sua próxima parada no caminho para seu dispositivo final de destino.

O cabeçalho de um pacote IPv4 consiste em campos com informações importantes sobre o pacote. Esses campos contêm números binários que são examinados pelo processo da Camada 3.

### Campos do cabeçalho de pacote IPv4

Os valores binários de cada campo identificam várias configurações do pacote IP. Os diagramas de cabeçalho de protocolo, cuja leitura é feita da esquerda para a direita, de cima para baixo, disponibilizam uma visualização para consultar ao discutir os campos de protocolo. O diagrama de cabeçalho de protocolo IP na figura identifica os campos de um pacote IPv4.
![[Pasted image 20241226193621.png]]

Campos significativos no cabeçalho IPv4 incluem o seguinte:

- **Versão** - Contém um valor binário de 4 bits definido como 0100 que identifica isso como um pacote IPv4.
- **Serviços diferenciados ou DiffServ (DS)** - Anteriormente chamado de campo tipo de serviço (ToS), o campo DS é um campo de 8 bits usado para determinar a prioridade de cada pacote. Os seis bits mais significativos do campo DiffServ são os bits do ponto de código de serviços diferenciados (DSCP) e os dois últimos são os bits de notificação de congestionamento explícita (ECN).
- **Tempo de vida (TTL)** - TTL contém um valor binário de 8 bits usado para limitar a vida útil de um pacote. O dispositivo de origem do pacote IPv4 define o valor TTL inicial. É diminuído em um cada vez que o pacote é processado por um roteador. Se o campo TTL for decrementado até zero, o roteador descartará o pacote e enviará uma mensagem ICMP de tempo excedido para o endereço IP de origem. Como o roteador decrementa o TTL de cada pacote, o roteador também deve recalcular a soma de verificação do cabeçalho.
- **Protocolo** - Este campo é usado para identificar o próximo nível de protocolo. O valor binário de 8 bits indica o tipo de carga de dados que o pacote está carregando, o que permite que a camada de rede transfira os dados para o protocolo apropriado das camadas superiores. Valores comuns incluem ICMP (1), TCP (6) e UDP (17). Checksum de * **cabeçalho —** Isso é usado para detectar corrupção no cabeçalho IPv4.
- **Endereço IPv4 de origem** - Contém um valor binário de 32 bits que representa o endereço IPv4 de origem do pacote. O endereço de origem IPv 4 é sempre um endereço unicast.
- **Endereço IPv4 de destino** - Contém um valor binário de 32 bits que representa o endereço IPv4 de destino do pacote. O endereço IPv4 destino é um endereço unicast, multicast, ou broadcast.

Os dois campos mais referenciados são os endereços IP de origem e destino. Esses campos identificam a procedência do pacote e para onde ele vai. Normalmente, esses endereços não mudam durante a viagem da origem ao destino.

Os campos Tamanho do Cabeçalho de Internet (IHL), Tamanho Total e Soma de Verificação do Cabeçalho servem para identificar e validar o pacote.

Outros campos são usados para reorganizar um pacote fragmentado. O pacote IPv4 usa especificamente os campos Identificação, Flags e Deslocamento do Fragmento para organizar os fragmentos. Um roteador pode precisar fragmentar um pacote IPv4 ao encaminhá-lo de um meio para outro com uma MTU menor.

Os campos Opções e Preenchimento raramente são usados e estão além do escopo deste módulo.

# Noções básicas de endereçamento IP

### Partes de Rede e de Host

Um endereço IPv4 é um endereço hierárquico de 32 bits, composto por uma parte da rede e uma parte do host. Ao determinar a parte da rede versus a parte do host, você deve observar o fluxo de 32 bits, conforme mostrado na figura.
![[Pasted image 20241226193829.png]]

Os bits na parte de rede do endereço devem ser iguais em todos os dispositivos que residem na mesma rede. Os bits na parte de host do endereço devem ser exclusivos para identificar um host específico dentro de uma rede. Se dois hosts tiverem o mesmo padrão de bits na parte de rede especificada do fluxo de 32 bits, esses dois hosts residirão na mesma rede.

Mas como os hosts sabem qual parte dos 32 bits identifica a rede e qual identifica o host? Esse é o papel da máscara de sub-rede.

### A Máscara de Sub-Rede

Conforme mostrado na figura, atribuir um endereço IPv4 a um host requer o seguinte:

- **Endereço IPv4** - este é o endereço IPv4 exclusivo do host.
- **Máscara de sub-rede** - É usada para determinar a parte de rede de um endereço IPv4.
![[Pasted image 20241226193927.png]]

**Observação**: Um endereço IPv4 de gateway padrão é necessário para acessar redes remotas e os endereços IPv4 do servidor DNS são necessários para converter nomes de domínio em endereços IPv4.

A máscara de sub-rede IPv4 é usada para diferenciar a parte da rede da parte do host de um endereço IPv4. Quando um endereço IPv4 é atribuído a um dispositivo, a máscara de sub-rede é usada para determinar o endereço de rede do dispositivo. O endereço de rede representa todos os dispositivos na mesma rede.

##### Máscara de sub-rede
![[Pasted image 20241226194012.png]]
Observe como a máscara de sub-rede é uma sequência consecutiva de 1 bits, seguida por uma sequência consecutiva de 0 bits.

Para identificar as partes da rede e do host de um endereço IPv4, a máscara de sub-rede é comparada com o endereço IPv4 bit por bit, da esquerda para a direita, conforme mostrado na figura.
![[Pasted image 20241226194035.png]]
Observe que, na verdade, a máscara de sub-rede não contém a parte da rede ou host de um endereço IPv4, apenas informa ao computador onde procurar a parte do endereço IPv4 que é a parte da rede e qual parte é a parte do host.

O processo real usado para identificar a parte da rede e a parte de host é chamado de AND.

### Comprimento do Prefixo

Expressar os endereços de rede e os endereços de host com o endereço da máscara de sub-rede em decimal com pontos pode ser complicado. Felizmente, existe um método alternativo para identificar uma máscara de sub-rede, um método chamado comprimento do prefixo.

O comprimento do prefixo é o número de bits definido como 1 na máscara de sub-rede. Está escrito em "notação de barra", que é anotada por uma barra (/) seguida pelo número de bits definido como 1. Portanto, conte o número de bits da máscara de sub-rede e preceda-o com uma barra.

Consulte a tabela para exemplos. A primeira coluna lista várias máscaras de sub-rede que podem ser usadas com um endereço de host. A segunda coluna mostra o endereço binário de 32 bits convertido. A última coluna mostra o comprimento do prefixo resultante.
![[Pasted image 20241226194203.png]]

**Observação** : Um endereço de rede também é conhecido como prefixo ou prefixo de rede. Portanto, o comprimento do prefixo é o número de 1 bits na máscara de sub-rede.

Ao representar um endereço IPv4 usando um comprimento de prefixo, o endereço IPv4 é gravado seguido do comprimento do prefixo sem espaços. Por exemplo, 192.168.10.10 255.255.255.0 seria gravado como 192.168.10.10/24. O uso de vários tipos de comprimentos do prefixo será discutido mais tarde. Por enquanto, o foco estará no prefixo /24 (ou seja, 255.255.255.0)
### Determinando a rede - Lógica AND

Um AND lógico é uma das três operações booleanas usadas na lógica booleana ou digital. As outras duas são OR e NOT. A operação AND é usada para determinar o endereço de rede.

AND lógico é a comparação de dois bits que produz os resultados mostrados abaixo. Observe como somente 1 AND 1 produz um 1. Qualquer outra combinação resulta em um 0.

- 1 E 1 = 1
- 0 E 1 = 0
- 1 E 0 = 0
- 0 E 0 = 0

**Observação** : Na lógica digital, 1 representa Verdadeiro e 0 representa Falso. Ao usar uma operação AND, ambos os valores de entrada devem ser Verdadeiro (1) para que o resultado seja Verdadeiro (1).

Para identificar o endereço de rede de um host IPv4, é feito um AND lógico, bit a bit, entre o endereço IPv4 e a máscara de sub-rede. Quando se usa AND entre o endereço e a máscara de sub-rede, o resultado é o endereço de rede.

Para ilustrar como AND é usado para descobrir um endereço de rede, considere um host com endereço IPv4 192.168.10.10 e máscara de sub-rede 255.255.255.0, conforme mostrado na figura:

- **Endereço de host IPv4 (192.168.10.10)** - O endereço IPv4 do host em formatos decimais pontilhados e binários.
- **Máscara de sub-rede (255.255.255.0)** - A máscara de sub-rede do host nos formatos decimal com pontos e binário.
- **Endereço de rede (192.168.10.0)** - A operação lógica AND entre o endereço IPv4 e a máscara de sub-rede resulta em um endereço de rede IPv4 mostrado nos formatos decimal com pontos e binário.
![[Pasted image 20241226194326.png]]

Usando a primeira sequência de bits como exemplo, observe que a operação E é executada no 1 bit do endereço do host com o 1 bit da máscara de sub-rede. Isso resulta em um bit 1 para o endereço de rede. 1 E 1 = 1.

A operação AND entre um endereço de host IPv4 e uma máscara de sub-rede resulta no endereço de rede IPv4 para este host. Neste exemplo, a operação AND entre o endereço de host 192.168.10.10 e a máscara de sub-rede 255.255.255.0 (/24) resulta no endereço de rede IPv4 192.168.10.0/24. Esta é uma operação IPv4 importante, pois informa ao host a qual rede pertence.

### Sub redes e domínos de Broadcast

A rede 192.168.10.0/24 pode suportar 254 hosts. Redes maiores, como 172.16.0.0/16, podem suportar muitos mais endereços de host (mais de 65.000). No entanto, isso pode potencialmente criar um domínio de Broadcast maior. Um problema desse tipo de domínio é que os hosts podem gerar broadcasts em excesso e afetar a rede de forma negativa.

A solução é reduzir o tamanho da rede para criar domínios de broadcast menores em um processo denominado divisão em sub-redes. Os espaços de rede menores são chamados de sub-redes.

**Observação**: os termos sub-rede e rede costumam ser usados de maneira intercambiável. A maioria das redes são uma sub-rede de um bloco de endereços maior.

A divisão em sub-redes reduz o tráfego total da rede e melhora seu desempenho. Ele também permite que um administrador implemente políticas de segurança que controlam quais sub-redes têm permissão para se comunicar entre si, por exemplo.

Há várias maneiras de usar sub-redes para gerenciar dispositivos de rede. Os administradores de rede podem agrupar dispositivos e serviços em sub-redes que podem ser determinadas por uma variedade de fatores.

# Tipos de endereços IPv4

### Classes de endereços IPv4 e máscaras de sub-rede padrão

Existem vários tipos e classes de endereços IPv4. Embora as classes de endereço estejam se tornando menos importantes na rede, elas ainda são usadas e referenciadas comumente na documentação da rede.

**Classes de endereços**

Em 1981, os endereços IPv4 de Internet eram atribuídos com um endereçamento classful (RFC 790) Os clientes estavam alocados em um endereço de rede em uma das três classes, A, B, ou C. A RFC dividiu os intervalos de unicast em classes específicas chamadas:

- **Classe A** (0.0.0.0/8 a 127.0.0.0/8) - Projetado para suportar redes extremamente grandes com mais de 16 milhões de endereços de host. Usava um prefixo fixo /8 com o primeiro octeto para endereços de rede e os três octetos restantes para endereços de host.
- **Classe B** (128.0.0.0 / 16 - 191.255.0.0 / 16) - Projetada para oferecer suporte às necessidades de redes de tamanho moderado a grande com até aproximadamente 65.000 endereços de host. Usava um prefixo fixo /16 com os dois octetos de mais alta ordem para endereços de rede e os dois octetos restantes para endereços de host.
- **Classe C** (192.0.0.0 / 24 - 223.255.255.0 / 24) - Projetado para oferecer suporte a pequenas redes com no máximo 254 hosts. Usava um prefixo fixo /24 com os primeiros três octetos para endereços de rede e o octeto restante para endereços de host.

**Observação**: Há também um bloco multicast de Classe D consistindo de 224.0.0.0 a 239.0.0.0 e um bloco de endereço experimental de Classe E consistindo de 240.0.0.0 - 255.0.0.0.

Como mostrado na figura, o sistema classful alocava 50% dos endereços IPv4 disponíveis para 128 redes de Classe A, 25% dos endereços para a Classe B, e a Classe C compartilhava os 25% restantes com as Classes D e E. Embora adequado na época, já que a Internet estava em expansão, obviamente esse método era um desperdício de endereços e esgotava o número de endereços de rede IPv4 disponíveis.
![[Pasted image 20241226194844.png]]

O endereçamento classful foi abandonado no fim dos anos de 1990 e substituído por um sistema mais moderno que não usa classe (classless). No entanto, como veremos mais tarde, o endereçamento sem classe era apenas uma solução temporária para o esgotamento de endereços IPv4.

### Endereços privados reservados

Os endereços IPv4 públicos são endereços roteados globalmente entre os roteadores ISP. No entanto, nem todos os endereços IPv4 disponíveis podem ser usados na Internet . Existem blocos de endereços (conhecidos como endereços privados) que são usados pela maioria das organizações para atribuir endereços IPv4 a hosts internos.

Em meados da década de 1990, os endereços IPv4 privados foram introduzidos devido ao esgotamento do espaço de endereços IPv4. Os endereços IPv4 privados são reservados e podem ser usados por uma rede interna.

Os blocos de endereços privados

- 10.0.0.0 /8 ou 10.0.0.0 para 10.255.255.255
- 172.16.0.0 /12 ou 172.16.0.0 a 172.31.255.255
- 192.168.0.0 /16 ou 192.168.0.0 a 192.168.255.255

É importante saber que os endereços desses blocos não são permitidos na Internet e devem ser filtrados (descartados) pelos roteadores de Internet. Por exemplo, na figura, os usuários das redes 1, 2 ou 3 estão enviando pacotes para destinos remotos. Os roteadores do ISP constatam que os endereços IPv4 origem nos pacotes são endereços privados e descartam os pacotes.
##### Endereços privados não podem ser roteados pela Internet]

A maioria das organizações usa endereços IPv4 privados para seus hosts internos. No entanto, esses endereços da RFC 1918 não podem ser roteados na Internet e devem ser convertidos em um endereço IPv4 público. A NAT (conversão de endereços de rede) é usada para converter endereços IPv4 privados em endereços IPv4 públicos. Normalmente isso é feito no roteador que conecta a rede interna à rede do ISP.

Roteadores domésticos têm a mesma capacidade. Por exemplo, a maioria dos roteadores atribui endereços IPv4 a seus hosts com e sem fio com base no endereço privado 192.168.1.0 /24. A interface do roteador doméstico que se conecta à rede do provedor de serviços de Internet (ISP) geralmente recebe um endereço IPv4 público para usar na Internet.

# O gateway padrão

### Decisão de Encaminhamento do Host

Com IPv4 e IPv6, os pacotes são sempre criados no host de origem. O host de origem deve ser capaz de direcionar o pacote para o host de destino. Para fazer isso, os dispositivos finais do host criam sua própria tabela de roteamento. Este tópico discute como os dispositivos finais usam tabelas de roteamento.

Outra função da camada de rede é direcionar pacotes entre hosts. Um host pode enviar um pacote para o seguinte:

- **Próprio** - Um host pode executar ping em si mesmo enviando um pacote para um endereço IPv4 especial de 127.0.0.1 ou um endereço IPv6 :: / 1, conhecido como interface de loopback. O ping na interface de loopback testa a pilha de protocolos do TCP/IP no host.
- **Host local** - este é um host de destino que está na mesma rede local que o host de envio. Os hosts de origem e destino compartilham o mesmo endereço de rede.
- **Host remoto** - este é um host de destino em uma rede remota. Os hosts de origem e destino não compartilham o mesmo endereço de rede.

Se um pacote é destinado a um host local ou a um host remoto é determinado pelo dispositivo final de origem. O dispositivo final de origem determina se o endereço IP de destino está na mesma rede em que o próprio dispositivo de origem está. O método de determinação varia de acordo com a versão IP:

- **Em IPv4** - o dispositivo de origem usa sua própria máscara de sub-rede junto com seu próprio endereço IPv4 e o endereço IPv4 de destino para fazer essa determinação.
- **Em IPv6** - o roteador local anuncia o endereço da rede local (prefixo) para todos os dispositivos da rede.

Em uma rede doméstica ou comercial, você pode ter vários dispositivos com e sem fio interconectados usando um dispositivo intermediário, como um switch LAN ou um ponto de acesso sem fio (WAP). Este dispositivo intermediário fornece interconexões entre hosts locais na rede local. Os hosts locais podem interagir entre si e compartilhar informações sem a necessidade de dispositivos adicionais. Se um host estiver enviando um pacote para um dispositivo configurado com a mesma rede IP que o dispositivo host, o pacote será simplesmente encaminhado para fora da interface do host, através do dispositivo intermediário e diretamente ao dispositivo de destino.

Obviamente, na maioria das situações, queremos que nossos dispositivos possam se conectar além do segmento de rede local, como em outras residências, empresas e na Internet. Os dispositivos que estão além do segmento de rede local são conhecidos como hosts remotos. Quando um dispositivo de origem envia um pacote a um dispositivo de destino remoto, é necessária a ajuda de roteadores e do roteamento. O roteamento é o processo de identificação do melhor caminho até um destino. O roteador conectado ao segmento de rede local é conhecido como gateway padrão (default gateway).

### Gateway Padrão

O gateway padrão é o dispositivo de rede (ou seja, roteador ou switch da Camada 3) que pode rotear o tráfego para outras redes. Comparando a rede com uma sala, o gateway padrão é a porta. Se você quiser ir para outra sala (rede), vai precisar encontrar essa porta.

Em uma rede, um gateway padrão geralmente é um roteador com esses recursos:

- Ele possui um endereço IP local no mesmo intervalo de endereços que outros hosts na rede local.
- Ele pode aceitar dados na rede local e encaminhar dados para fora da rede local.
- Ele direciona o tráfego para outras redes.

Um gateway padrão é necessário para enviar tráfego fora da rede local. O tráfego não pode ser encaminhado para fora da rede local se não houver gateway padrão, o endereço de gateway padrão não estiver configurado ou o gateway padrão estiver inativo.

### Um host direciona para o gateway padrão

Uma tabela de roteamento de host normalmente inclui um gateway padrão. No IPv4, o host recebe o endereço IPv4 do gateway padrão dinamicamente do DHCP (Dynamic Host Configuration Protocol) ou configurado manualmente. No IPv6, o roteador anuncia o endereço de gateway padrão ou o host pode ser configurado manualmente.

A configuração do gateway padrão cria uma rota padrão na tabela de roteamento do computador. Uma rota padrão é a rota ou o caminho que o computador usa quando tenta entrar em contato com uma rede remota.

### Tabelas de Roteamento dos Hosts

Em um host do Windows, o comando **route print** ou **netstat -r** pode ser usado para exibir a tabela de roteamento do host. Ambos os comandos geram a mesma saída. O resultado pode parecer confuso no começo, mas é bastante simples de entender.

A figura exibe uma topologia de exemplo e a saída gerada pelo **netstat -r** comando.
![[Pasted image 20241226195434.png]]
**Observação**: a saída exibe apenas a tabela de rotas IPv4.

A inserção do comando **netstat -r** ou o comando equivalente **route print** exibe três seções relacionadas às conexões de rede TCP / IP atuais:

- **Lista de interface** - lista o endereço de controle de acesso à mídia (MAC) e o número de interface atribuído de cada interface com capacidade de rede no host, incluindo adaptadores Ethernet, Wi-Fi e Bluetooth.
- **Tabela de rotas IPv4** - lista todas as rotas IPv4 conhecidas, incluindo conexões diretas, rede local e rotas padrão locais.
- **Tabela de rotas IPv6** - lista todas as rotas IPv6 conhecidas, incluindo conexões diretas, rede local e rotas padrão locais.,

# IPv6

O IPv4 tem um máximo teórico de 4,3 bilhões de endereços. Combinados à NAT (tradução de endereços de rede), os endereços privados foram imprescindíveis para retardar a redução do espaço de endereços IPv4. No entanto, o NAT é problemático para muitos aplicativos, cria latência e possui limitações que impedem severamente as comunicações ponto a ponto.

Com o número cada vez maior de dispositivos móveis, os provedores móveis têm liderado o caminho com a transição para o IPv6. Os dois principais provedores de telefonia móvel nos Estados Unidos relatam que mais de 90% de seu tráfego usa IPv6.

A maioria dos principais ISPs e provedores de conteúdo, como YouTube, Facebook e NetFlix, também fizeram a transição. Muitas empresas como Microsoft, Facebook e LinkedIn estão fazendo transição para IPv6 somente internamente. Em 2018, a ISP Comcast de banda larga relatou uma implantação de mais de 65% e a British Sky Broadcasting mais de 86%.

**⁪Internet das Coisas**

A internet de hoje é significativamente diferente da internet das últimas décadas. A internet de hoje é mais do que e-mail, páginas da web e transferências de arquivos entre computadores. A Internet em evolução está se tornando uma Internet das Coisas (IoT). Os únicos dispositivos que acessam a Internet não serão mais computadores, tablets e smartphones. Os dispositivos equipados com sensor e prontos para a Internet de amanhã incluirão tudo, desde automóveis e dispositivos biomédicos, até eletrodomésticos e ecossistemas naturais.

Com uma população cada vez maior na Internet, espaço de endereços IPv4 limitado, problemas com NAT e uma Internet das Coisas, chegou o momento de iniciar a transição para o IPv6.

### Formatos de Endereço IPv6

O primeiro passo para aprender sobre IPv6 em redes é entender a forma como um endereço IPv6 é escrito e formatado. Os endereços IPv6 são muito maiores do que os endereços IPv4, razão pela qual é improvável que fiquemos sem eles.

Os endereços IPv6 têm 128 bits e são escritos como uma sequência de valores hexadecimais. Cada 4 bits são representados por um único dígito hexadecimal, totalizando 32 valores hexadecimais, como mostra a Figura 1. Os endereços IPv6 não diferenciam maiúsculas e minúsculas e podem ser escritos tanto em minúsculas como em maiúsculas.
![[Pasted image 20241226195805.png]]

**Formato Preferencial**

Como mostrado na Figura 1, o formato preferencial para escrever um endereço IPv6 é x: x: x: x: x: x: x: x, com cada “x” consistindo de quatro valores hexadecimais. O termo octeto refere-se aos oito bits de um endereço IPv4. No IPv6, um hexteto é o termo não oficial usado para se referir a um segmento de 16 bits ou quatro valores hexadecimais. Cada “x” equivale a um único hexteto, 16 bits ou quatro dígitos hexadecimais.

Formato preferencial significa que o endereço IPv6 é gravado usando todos os 32 dígitos hexadecimais. Isso não significa necessariamente que é o método ideal para representar o endereço IPv6. Existem duas regras que ajudam a reduzir o número de dígitos necessários para representar um endereço IPv6.
### Regra 1 - Omitir zeros à esquerda

A primeira regra para ajudar a reduzir a notação de endereços IPv6 é omitir os 0s (zeros) à esquerda de qualquer seção de 16 bits ou hexteto. Aqui estão quatro exemplos de maneiras de omitir zeros à esquerda:

- 01AB pode ser representado como 1AB
- 09f0 pode ser representado como 9f0
- 0a00 pode ser representado como a00
- 00ab pode ser representado como ab

Essa regra se aplica somente aos 0s à esquerda, e NÃO aos 0s à direita. Caso contrário, o endereço ficaria ambíguo.

### Regra 2 - Dois pontos duplos

A segunda regra para ajudar a reduzir a notação de endereços IPv6 é que o uso de dois-pontos duplo (::) pode substituir uma única sequência contígua de um ou mais segmentos de 16 bits (hextetos) compostos exclusivamente por 0s. Por exemplo, 2001:db8:cafe: 1:0:0:0:1 (0s iniciais omitidos) poderia ser representado como 2001:db8:cafe:1::1. O dois-pontos duplos (::) é usado no lugar dos três hextets all-0 (0:0:0).

Os dois-pontos em dobro (::) só podem ser usados uma vez em um endereço; caso contrário, haveria mais de um endereço resultante possível. Quando associada à técnica de omissão dos 0s à esquerda, a notação de endereço IPv6 pode ser bastante reduzida. É o chamado formato compactado.

Aqui está um exemplo do uso incorreto de dois pontos: 2001:db8::abcd::1234.

O dois-pontos duplo é usado duas vezes no exemplo acima. Aqui estão as possíveis expansões deste endereço de formato compactado incorreto:

- 2001:db8::abcd:0000:0000:1234
- 2001:db8::abcd:0000:0000:0000:1234
- 2001:db8:0000:abcd::1234
- 2001:db8:0000:0000:abcd::1234

Se um endereço tiver mais de uma cadeia contígua de todos os hextets 0, a prática recomendada é usar dois pontos duplos (::) na cadeia mais longa. Se as strings forem iguais, a primeira string deve usar dois pontos duplos (::).

### Comprimento do Prefixo IPv6

Lembre-se de que o prefixo (a parte de rede) de um endereço IPv4 pode ser identificado pelo comprimento do prefixo (notação em barra) ou por uma máscara de sub-rede decimal com pontos. Por exemplo, o endereço IPv4 192.168.1.10 com máscara de sub-rede decimal com pontos 255.255.255.0 é equivalente a 192.168.1.10/24.

No IPv4 o /24 é chamado de prefixo. No IPv6 é chamado de comprimento do prefixo. O IPv6 não usa a notação decimal com pontos da máscara de sub-rede. Como o IPv4, o comprimento do prefixo é representado na notação de barra e é usado para indicar a parte da rede de um endereço IPv6.

O comprimento do prefixo pode variar de 0 a 128. O comprimento do prefixo IPv6 recomendado para LANs e a maioria dos outros tipos de redes é /64, conforme mostrado na figura.
![[Pasted image 20241226200126.png]]
Isso significa que o prefixo ou a parte de rede do endereço é de 64 bits, restando outros 64 bits para a ID da interface (parte de host) do endereço.

É altamente recomendável usar um ID de interface de 64 bits para a maioria das redes. Isso ocorre porque a configuração automática de endereço sem estado (SLAAC) usa 64 bits para o ID de interface. Também facilita a criação e o gerenciamento de sub-redes.