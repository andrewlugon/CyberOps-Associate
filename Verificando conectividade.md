As redes nunca param? É claro que elas param. Felizmente, os desenvolvedores dos protocolos IP incluíram um protocolo de teste chamado ICMP. As ferramentas ICMP criam pacotes especiais que testam redes. Os analistas de segurança cibernética devem compreender a rede em que os dados normais viajam para que possam detectar comportamentos anormais. O ICMP pode ajudá-lo a entender o comportamento normal e anormal da rede.

# ICMP

### Mensagens ICMPv4

Embora o IP seja apenas um protocolo de melhor esforço, a suíte TCP/IP prevê o envio de mensagens no caso de certos erros. Essas mensagens são enviadas com os serviços do ICMP. O objetivo dessas mensagens é dar feedback sobre questões relativas ao processamento de pacotes IP sob certas condições, e não tornar o IP confiável. As mensagens ICMP não são necessárias e muitas vezes não são permitidas por questões de segurança.

O ICMP está disponível tanto para IPv4 como para IPv6. ICMPv4 é o protocolo de mensagens para o IPv4. O ICMPv6 fornece os mesmos serviços para o IPv6, mas inclui funcionalidade adicional. Neste curso, o termo ICMP será usado indistintamente quando falarmos de ICMPv4 e ICMPv6.

São muitos os tipos de mensagens ICMP e os motivos pelos quais elas são enviadas. Vamos apresentar algumas das mensagens mais comuns.

Estas são as mensagens ICMP mais comuns para ICMPv4 e ICMPv6:

- Confirmação de host
- Destino ou serviço inalcançável;
- Tempo excedido..
- Redirecionamento de rota

**Confirmação de host**

Uma mensagem de eco ICMP pode ser usada para determinar se um host está operacional. O host local envia uma solicitação de eco ICMP (ICMP Echo Request) para um host. Se o host estiver disponível, o host de destino enviará uma resposta de eco (Echo Reply).

**Destino ou Serviço Inalcançável**

Quando um host ou um gateway recebe um pacote que não pode entregar, ele pode usar uma mensagem ICMP de destino inalcançável para notificar à origem que o destino ou o serviço está inalcançável. A mensagem conterá um código que indica por que não foi possível entregar o pacote.

Estes são alguns dos códigos de destino inacessível para ICMPv4:

- **0** - Net unreachable (Rede Inacessível)
- **1** - Host unreachable (Host Inacessível)
- **2** - Protocol unreachable (Protocolo Inacessível)
- **3** - Port unreachable (Porta Inacessível)

**Nota:** O ICMPv6 possui códigos semelhantes, mas ligeiramente diferentes, para mensagens de Destino Inacessível.

**Tempo Excedido**

Uma mensagem ICMPv4 de tempo excedido é usada por um roteador para indicar que um pacote não pode ser encaminhado porque o campo Vida Útil (TTL) do pacote foi reduzido a 0. Se um roteador recebe um pacote e o campo TTL do pacote IPv4 diminui para zero, ele descarta o pacote e envia uma mensagem de tempo excedido para o host de origem.

O ICMPv6 também enviará uma mensagem de tempo excedido se o roteador não conseguir encaminhar um pacote IPv6 porque o pacote expirou. O IPv6 não tem um campo TTL. Ele usa o campo de limite de salto para determinar se o pacote expirou.

### Mensagens ICMPv6 RS e RA

As mensagens informativas e de erro encontradas no ICMPv6 são muito semelhantes às mensagens de controle e de erros implementadas pelo ICMPv4. No entanto, o ICMPv6 tem funcionalidade aprimorada e novos recursos que não são encontrados no ICMPv4. As mensagens ICMPv6 são encapsuladas no IPv6.

O ICMPv6 inclui quatro novos protocolos como parte do protocolo ND ou NDP (Neighbor Discovery Protocol):

Mensagens entre um roteador IPv6 e um dispositivo IPv6:

- Mensagem de Solicitação de Roteador (RS)
- Mensagem de Anúncio de Roteador (RA)

Mensagens entre dispositivos IPv6:

- Mensagem de solicitação de vizinhos (NS)
- Mensagem de anúncio de vizinhos (NA)

Solicitação de roteador
1. As mensagens de RA são enviadas por roteadores para fornecer informações de endereçamento aos hosts usando a configuração automática de endereço sem estado (SLAAC). A mensagem RA pode incluir informações de endereçamento para o host, como prefixo, comprimento do prefixo, endereço DNS e nome de domínio. Um roteador enviará uma mensagem de RA periodicamente ou em resposta a uma mensagem de RS. Um host que use SLAAC configurará o gateway padrão como o endereço de link local do roteador que enviou o RA.
2. Quando um host é configurado para obter suas informações de endereçamento automaticamente usando SLAAC, o host enviará uma mensagem RS ao roteador solicitando uma mensagem RA.

Resolução de endereços
1. As mensagens de NA são enviadas quando um dispositivo conhece o endereço IPv6 de um dispositivo, mas não conhece seu endereço MAC. Isso equivale a uma requisição ARP no IPv4.
2. As mensagens NA são enviadas em resposta a uma mensagem NS e correspondem ao endereço IPv6 de destino no NS. A mensagem de NA inclui o endereço MAC Ethernet do dispositivo. Isso é equivalente a uma resposta ARP em IPv4.

Detecção de Endereços Duplicados (DAD)

1. Quando um dispositivo recebe um unicast global ou um endereço unicast de link local, é recomendável executar DAD no endereço para garantir que ele seja único. Para verificar a exclusividade de um endereço, o dispositivo enviará uma mensagem NS com seu próprio endereço IPv6 como o endereço IPv6 de destino, mostrado na figura. Se outro dispositivo na rede tiver esse endereço, ele responderá com uma mensagem de NA. Essa mensagem de NA notificará o dispositivo emissor de que o endereço está em uso. Se uma mensagem de NA correspondente não for devolvida em um determinado período, o endereço unicast será único e aceitável para uso.

**Nota**: O DAD não é necessário, mas o RFC 4861 recomenda que o DAD seja executado em endereços unicast.

# Utilitários Ping e Traceroute

### Ping - Testar conectividade

Neste tópico, você aprenderá sobre as situações em que cada ferramenta é usada e como usá-las. O Ping é um utilitário de teste IPv4 e IPv6 que usa a solicitação de eco ICMP e as mensagens de resposta de eco para testar a conectividade entre hosts.

Para testar a conectividade com outro host em uma rede, uma solicitação de eco é enviada ao endereço do host usando o comando **ping**. Se o host no endereço especificado receber a requisição de eco, ele enviará uma resposta de eco. À medida que cada resposta de eco é recebida, **ping** fornece feedback sobre o tempo entre o envio da solicitação e o recebimento da resposta. Esta pode ser uma medida do desempenho da rede.

O ping tem um valor de tempo limite para a resposta. Se a resposta não é recebida dentro do tempo de espera, o ping mostra uma mensagem informando que a resposta não foi recebida. Isso pode indicar que há um problema, mas também pode indicar que os recursos de segurança que bloqueiam as mensagens de ping foram ativados na rede. É comum o primeiro ping para o tempo limite se a resolução de endereço (ARP ou ND) precisar ser executada antes de enviar a Solicitação de eco ICMP.

Depois que todas as solicitações são enviadas, o **ping** utilitário fornece um resumo que inclui a taxa de sucesso e o tempo médio de ida e volta para o destino.

O tipo de testes de conectividade realizados com **ping** incluem o seguinte:

- Fazendo ping no loopback local
- Fazendo ping no gateway padrão
- Fazendo ping no host remoto

### Fazer ping no loopback

O ping pode ser usado para testar a configuração interna do IPv4 ou IPv6 no host local. Para executar este teste, **ping** o endereço de loopback local 127.0.0.1 para IPv4 (:: 1 para IPv6).

Uma resposta vinda de 127.0.0.1 para IPv4 (ou ::1 para IPv6) indica que o IP está instalado corretamente no host. Essa resposta vem da camada de rede. No entanto, ela não significa que os endereços, as máscaras ou os gateways estão configurados adequadamente, Nem indica o status da camada inferior da pilha de rede. Ela simplesmente testa o IP até a camada de rede do IP. Uma mensagem de erro indica que o TCP/IP não está operacional no host.

### Executar ping no gateway padrão

Você também pode usar **ping** para testar a capacidade de um host de se comunicar na rede local. Isso geralmente é feito através do ping do endereço IP do gateway padrão do host. Um êxito **ping** no gateway padrão indica que o host e a interface do roteador servindo como gateway padrão estão operacionais na rede local.

Para este teste, o endereço de gateway padrão é usado com mais frequência porque o roteador normalmente está sempre operacional. Se o endereço de gateway padrão não responder, um **ping** poderá ser enviado para o endereço IP de outro host na rede local que se sabe estar operacional.

Se o gateway padrão ou outro host responder, o host local poderá se comunicar com êxito pela rede local. Se o gateway padrão não responder, mas outro host, isso pode indicar um problema com a interface do roteador servindo como gateway padrão.

Uma possibilidade é que o endereço de gateway padrão errado tenha sido configurado no host. Outra possibilidade é que a interface do roteador esteja plenamente operacional, mas tenha segurança aplicada a ela que a impeça de processar ou responder a solicitações ping.

### Efetuar ping em um host remoto

O ping também pode ser usado para testar a capacidade de um host local de se comunicar por uma rede interconectada. O roteador usa sua tabela de roteamento IP para encaminhar os pacotes.

Se esse ping tiver êxito, a operação de uma grande parte da rede interconectada poderá ser verificada. Um êxito **ping** na rede confirma a comunicação na rede local, a operação do roteador que serve como gateway padrão e a operação de todos os outros roteadores que possam estar no caminho entre a rede local e a rede do host remoto.

Além disso, a funcionalidade do host remoto pode ser verificada. Se o host remoto não conseguir se comunicar para fora de sua rede local, ele não responderá.

**Nota**: Muitos administradores de rede limitam ou proíbem a entrada de mensagens ICMP na rede corporativa; portanto, a falta de **ping** resposta pode ser devido a restrições de segurança.

### Traceroute - Teste o caminho

O ping é usado para testar a conectividade entre dois hosts, mas não fornece informações sobre detalhes de dispositivos entre os hosts. Traceroute (**tracert**) é um utilitário que gera uma lista de saltos que foram alcançados com sucesso ao longo do caminho. Essa lista pode dar informações importantes para a verificação e a solução de erros. Se os dados atingirem o destino, o rastreamento listará a interface de cada roteador no caminho entre os hosts. Caso ocorra falha nos dados em algum salto ao longo do caminho, o endereço do último roteador que respondeu ao rastreamento poderá fornecer uma indicação de onde está o problema ou das restrições de segurança que foram encontradas.

**Tempo de Ida e Volta (RTT)**

O uso do traceroute fornece tempo de ida e volta para cada salto ao longo do caminho e indica se um salto falha na resposta. O tempo de ida e volta é o tempo que um pacote leva para alcançar o host remoto e retornar a resposta do host. Um asterisco (*) é usado para indicar um pacote perdido ou não respondido.

Essas informações podem ser usadas para localizar um roteador problemático no caminho ou podem indicar que o roteador está configurado para não responder. Se a tela mostrar tempos de resposta altos ou perdas de dados de um salto específico, isso é uma indicação de que os recursos do roteador ou de suas conexões podem ser usados em excesso.

**TTL no IPv4 e Limite de Saltos no IPv6**

O Traceroute utiliza uma função do campo TTL no IPv4 e do campo Limite de saltos no IPv6 nos cabeçalhos da camada 3, junto com a mensagem ICMP Time Exceded.

### Formato de pacote ICMP

O ICMP é encapsulado diretamente em pacotes IP. Nesse sentido, é quase como um protocolo da camada de transporte, pois é encapsulado em um pacote, porém é considerado um protocolo da Camada 3. O ICMP atua como uma carga útil de dados dentro do pacote IP. Possui um campo de dados de cabeçalho especial, conforme mostrado na figura.

ICMP usa códigos de mensagem para diferenciar entre diferentes tipos de mensagens ICMP. Estes são alguns códigos de mensagem comuns:

- **0** — Echo reply (resposta a um ping)
- **3** - Destination Unreachable (Destino Inalcançável)
- **5** — Redirect (use outra rota para o seu destino)
- **8** — Echo request (para ping)
- **11** — Time Exceeded (TTL tornou-se 0)

Como você verá posteriormente no curso, um analista de segurança cibernética sabe que o campo opcional de carga útil do ICMP pode ser usado em um vetor de ataque para exfiltrar dados.