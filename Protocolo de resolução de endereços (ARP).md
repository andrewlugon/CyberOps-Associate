# MAC e IP

### Destino na Mesma Rede

Há dois endereços principais atribuídos a um dispositivo em uma rede LAN Ethernet:

- **Endereço físico (o endereço MAC)** - Isso é usado para comunicações Ethernet NIC para Ethernet NIC na mesma rede.
- **Endereço lógico (o endereço IP)** - Isso é usado para enviar o pacote da fonte original ao destino final.

Os endereços IP são usados para identificar o endereço do dispositivo de origem original e o dispositivo de destino final. O endereço IP de destino pode estar na mesma rede IP que a origem ou em uma rede remota.

**Nota**: A maioria dos aplicativos usa DNS (Sistema de Nome de Domínio) para determinar o endereço IP quando recebe um nome de domínio como [www.cisco.com](http://www.cisco.com). O DNS é discutido em um módulo posterior.

Os endereços MAC Ethernet têm uma finalidade diferente. Esses endereços servem para entregar o quadro de enlace de dados com o pacote IP encapsulado de uma NIC para outra na mesma rede. Se o endereço IP de destino estiver na mesma rede, o endereço MAC de destino será o do dispositivo de destino.

A figura mostra os endereços MAC Ethernet e endereço IP de PC-A enviando um pacote IP para o servidor de arquivos na mesma rede.

O quadro Ethernet da Camada 2 contém:

- **Endereço MAC de destino** - Este é o endereço MAC da placa de rede Ethernet do servidor de arquivos.
- **Endereço MAC de origem** - Este é o endereço MAC da placa de rede Ethernet do PC-A.

O pacote IP da Camada 3 contém:

- **Endereço IP de origem** - Este é o endereço IP da fonte original, PC-A.
- **Endereço IP de destino** - Este é o endereço IP do destino final, o servidor de arquivos.
![[Pasted image 20250106193258.png]]

### Destino na Rede Remota

Quando o endereço IP de destino estiver em uma rede remota, o endereço MAC de destino será o endereço do gateway padrão do host. O endereço padrão do gateway é o endereço da NIC do roteador, conforme mostrado na figura. Fazendo uma analogia com os correios, seria semelhante a uma pessoa levar uma carta até a agência postal local. Eles só precisam deixar a carta nos correios. Cabe então aos correios encaminhar a carta para o seu destino final.

A figura mostra os endereços de Ethernet MAC e endereços IPv4 para PC-A. Ele está enviando um pacote IP para um servidor de arquivos em uma rede remota. Os roteadores examinam o endereço IPv4 destino para determinar o melhor caminho para encaminhar o pacote IPv4. É um processo semelhante à forma como os correios encaminham correspondência com base no endereço do destinatário.

Quando o roteador recebe o quadro Ethernet, ele desencapsula as informações da Camada 2. Usando o endereço IP de destino, ele determina o dispositivo do próximo salto e encapsula o pacote IP em um novo quadro de enlace de dados para a interface de saída. Em cada link ao longo do caminho, um pacote IP é encapsulado em um quadro específico para a tecnologia de enlace de dados associada a esse link, como a Ethernet. Se o dispositivo do próximo salto for o destino final, o endereço MAC de destino será o da NIC Ethernet do dispositivo.

Como os endereços IPv4 dos pacotes IPv4 em um fluxo de dados são associados aos endereços MAC em cada link ao longo do caminho até o destino? Isso é feito através de um processo chamado protocolo ARP (Address Resolution Protocol).
![[Pasted image 20250106193423.png]]

# ARP

### Visão geral do ARP

Se sua rede estiver usando o protocolo de comunicações IPv4, o Protocolo de Resolução de Endereços ou ARP é o que você precisa para mapear endereços IPv4 para endereços MAC. Este tópico explica como o ARP funciona.

Cada dispositivo IP em uma rede Ethernet tem um endereço MAC Ethernet exclusivo. Quando um dispositivo envia um quadro Ethernet Layer 2, ele contém estes dois endereços:

- **Endereço MAC de destino** - O endereço MAC Ethernet do dispositivo de destino no mesmo segmento de rede local. Se o host de destino estiver em outra rede, o endereço de destino no quadro será o do gateway padrão (ou seja, roteador).
- **Endereço MAC de origem** - O endereço MAC da Ethernet NIC no host de origem.

Para enviar um pacote para outro host na mesma rede IPv4 local, um host deve saber o endereço IPv4 e o endereço MAC do dispositivo de destino. Os endereços IPv4 de destino do dispositivo são conhecidos ou resolvidos pelo nome do dispositivo. No entanto, os endereços MAC devem ser descobertos.

Um dispositivo utiliza o protocolo ARP (Address Resolution Protocol) para determinar o endereço MAC de destino de um dispositivo local quando conhece o endereço IPv4.

O ARP fornece duas funções básicas:

- Resolução de endereços IPv4 em endereços MAC
- Manter uma tabela de mapeamentos de endereços IPv4 para MAC

### Funções do ARP

Quando um pacote é enviado à camada de enlace de dados para ser encapsulado em um quadro Ethernet, o dispositivo consulta uma tabela em sua memória para encontrar o endereço MAC que é mapeado para o endereço IPv4. Esta tabela é armazenada temporariamente na memória RAM e denominada tabela ARP ou cache ARP.

O dispositivo emissor pesquisará em sua tabela ARP um endereço IPv4 destino correspondente a um endereço MAC.

- Se o endereço IPv4 destino do pacote estiver na mesma rede que o endereço IPv4 origem, o dispositivo pesquisará o endereço IPv4 destino na tabela ARP.
- Se o endereço IPv4 destino do pacote estiver em uma rede diferente do endereço IPv4 origem, o dispositivo pesquisará o endereço IPv4 do gateway padrão na tabela ARP.

Nos dois casos, a pesquisa é por um endereço IPv4 e um endereço MAC correspondente para o dispositivo.

Cada entrada (linha) da tabela ARP vincula um endereço IPv4 a um endereço MAC. Chamamos a relação entre os dois valores de um mapa. Isso significa simplesmente que você pode localizar um endereço IPv4 na tabela e descobrir o endereço MAC correspondente. A tabela ARP salva (armazena em cache) temporariamente o mapeamento dos dispositivos da LAN.

Se o dispositivo localizar o endereço IPv4, seu endereço MAC correspondente será usado como endereço MAC de destino no quadro. Se nenhuma entrada for encontrada, o dispositivo enviará uma requisição ARP.

### Operação ARP - Solicitação ARP

Uma solicitação ARP é enviada quando um dispositivo precisa determinar o endereço MAC associado a um endereço IPv4 e não possui uma entrada para o endereço IPv4 em sua tabela ARP.

As mensagens do ARP são encapsuladas diretamente em um quadro Ethernet. Não há cabeçalho IPv4. A requisição ARP é encapsulada em um quadro Ethernet usando as seguintes informações de cabeçalho:

- **Endereço MAC de destino** - Este é um endereço de broadcast FF-FF-FF-FF-FF-FF que requer todos os NICs Ethernet na LAN para aceitar e processar a solicitação ARP.
- **Endereço MAC de origem** - Este é o endereço MAC do remetente da solicitação ARP.
- **Tipo** - As mensagens ARP têm um campo de tipo de 0x806. Ele informa à NIC de recebimento que a parte de dados do quadro precisa ser transferida para o processo ARP.

Como as solicitações de ARP são transmissões, elas são inundadas em todas as portas pelo switch, exceto a porta de recebimento. Todas as NICs Ethernet no processo de LAN transmite e devem entregar a solicitação ARP ao seu sistema operacional para processamento. Cada dispositivo deve processar a requisição ARP para ver se o endereço IPv4 destino corresponde ao seu. Um roteador não encaminhará broadcasts pelas outras interfaces.

Somente um dispositivo na LAN terá um endereço IPv4 correspondente ao endereço IPv4 na requisição ARP. Nenhum outro dispositivo responderá.

### Operação do ARP - Resposta do ARP

Somente o dispositivo com o endereço IPv4 de destino associado à solicitação ARP responderá com uma resposta ARP. A resposta de ARP é encapsulada em um quadro Ethernet com as seguintes informações de cabeçalho:

- **Endereço MAC de destino** - Este é o endereço MAC do remetente da solicitação ARP.
- **Endereço MAC de origem** - Este é o endereço MAC do remetente da resposta ARP.
- **Tipo** - As mensagens ARP têm um campo de tipo de 0x806. Ele informa à NIC de recebimento que a parte de dados do quadro precisa ser transferida para o processo ARP.

Apenas o dispositivo que enviou originalmente uma requisição ARP receberá a resposta ARP unicast. Depois que a resposta do ARP é recebida, o dispositivo adiciona o endereço IPv4 e o endereço MAC correspondente à sua tabela ARP. Agora os pacotes destinados a esse endereço IPv4 podem ser encapsulados em quadros com o endereço MAC correspondente.

Se nenhum dispositivo responder à requisição ARP, o pacote será descartado porque não será possível criar um quadro.

As entradas na tabela ARP têm carimbo de data/hora (timestamp). Se um dispositivo não receber um quadro de um dispositivo específico antes que o carimbo de data / hora expire, a entrada desse dispositivo será removida da tabela ARP.

Além disso, entradas de mapa estáticas podem ser inseridas em uma tabela ARP, mas isso é raro. As entradas estáticas na tabela ARP não expiram com o tempo e devem ser removidas manualmente.

**Nota**: O IPv6 usa um processo semelhante ao ARP para IPv4, conhecido como ICMPv6 Neighbour Discovery (ND). O IPv6 usa mensagens de requisição e de anúncio de vizinho, semelhantes a solicitações ARP e respostas ARP no IPv4.

### Função ARP na Comunicação Remota

Quando o endereço IPv4 destino não está na mesma rede que o endereço IPv4 origem, o dispositivo de origem precisa enviar o quadro para o gateway padrão. Essa é a interface do roteador local. Sempre que um dispositivo de origem tiver um pacote com um endereço IPv4 em outra rede, ele encapsulará esse pacote em um quadro usando o endereço MAC de destino do roteador.

O endereço IPv4 do gateway padrão é armazenado na configuração IPv4 dos hosts. Quando um host cria um pacote para um destino, ele compara o endereço IPv4 destino e seu próprio endereço IPv4 para determinar se os dois endereços IPv4 estão localizados na mesma rede de Camada 3. Se o host de destino não estiver na mesma rede, a origem usará a tabela ARP para obter uma entrada com o endereço IPv4 do gateway padrão. Se não houver uma entrada, ela usará o processo de ARP para determinar um endereço MAC do gateway padrão.

### Remoção de Entradas de uma Tabela ARP

Em cada dispositivo, um temporizador da cache ARP remove entradas ARP que não tenham sido usadas durante um determinado período. Os horários diferem dependendo do sistema operacional do dispositivo. Por exemplo, os sistemas operacionais Windows mais recentes armazenam entradas da tabela ARP entre 15 e 45 segundos.

Os comandos também podem ser usados para remover manualmente algumas ou todas as entradas na tabela ARP. Após a remoção de uma entrada, o processo de envio de uma requisição ARP e de recebimento de uma resposta ARP deve ocorrer novamente para inserir o mapa na tabela ARP.

### Tabelas ARP

Em um roteador Cisco, o comando **show ip arp** é usado para exibir a tabela ARP, conforme mostrado na figura.
![[Pasted image 20250106194218.png]]

Em um PC com Windows 10, o comando **arp -a** é usado para exibir a tabela ARP, conforme mostrado na figura.
![[Pasted image 20250106194231.png]]

# Problemas do ARP

### Transmissões de ARP e falsificação de ARP

Como um quadro broadcast, uma requisição ARP é recebida e processada por todos os dispositivos na rede local. Em uma rede corporativa típica, esses broadcasts provavelmente teriam impacto mínimo no desempenho da rede. No entanto, se um grande número de dispositivos precisasse ser ligado e todos começassem a acessar serviços de rede ao mesmo tempo, poderia haver alguma redução no desempenho por um curto período, como mostra a figura. Depois que os dispositivos enviarem os broadcasts ARP iniciais e tiverem reconhecido os endereços MAC necessários, qualquer impacto na rede será minimizado.
![[Pasted image 20250106194519.png]]

Em alguns casos, o uso do ARP pode levar a um risco potencial à segurança. Um ator de ameaça pode usar falsificação ARP para realizar um ataque de envenenamento por ARP. Esta é uma técnica usada por um ator de ameaça para responder a uma solicitação ARP de um endereço IPv4 que pertence a outro dispositivo, como o gateway padrão, conforme mostrado na figura. O agente da ameaça envia uma resposta ARP com seu próprio endereço MAC. O destinatário da resposta ARP adicionará o endereço MAC errado à sua tabela ARP e enviará esses pacotes ao agente de ameaça.  
Switches de nível corporativo incluem técnicas de mitigação conhecidas como inspeção dinâmica ARP (DAI). A DAI não faz parte do escopo deste curso.



Boa Práticas de Cibersegurança (IBSEC)
fundamento em cibersegurança (IBSEC)
Fundamentos em Redes (IBSEC)
Introduction to Cybersecurity (Cisco)
Endpoint Security (Cisco)
CCNA: Introduction to Networks (Cisco)