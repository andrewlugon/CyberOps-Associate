# Integridade e Autenticidade

### Comunicações seguras

As organizações devem fornecer suporte para proteger os dados à medida que eles viajam pelos links. Isso pode incluir tráfego interno, mas é mais importante proteger os dados que viajam para fora da organização para as filiais, locais de trabalho remoto, e parceiros.

Estes são os quatro elementos das comunicações seguras:

- **Integridade dos dados** - Garante que a mensagem não foi alterada. Quaisquer alterações nos dados em trânsito serão detectadas. A integridade é garantida pela implementação de um dos algoritmos Secure Hash (SHA-2 ou SHA-3). O algoritmo de resumo de mensagens MD5 ainda está amplamente em uso, no entanto, é inerentemente inseguro e cria vulnerabilidades em uma rede. O uso de MD5 deve ser evitado.
- **Autenticação da origem** - Garante que a mensagem não é uma falsificação e realmente vem de quem afirma. Muitas redes modernas garantem autenticação com algoritmos como código de autenticação de mensagem baseado em hash (HMAC).
- **Confidencialidade dos dados**- Garante que apenas usuários autorizados possam ler a mensagem. Se a mensagem for interceptada, ela não poderá ser decifrada dentro de um razoável período de tempo. A confidencialidade dos dados é implementada usando algoritmos de criptografia simétrica e assimétrica.
- **Dados não repudiáveis** - Garante que o remetente não possa repudiar ou refutar a validade de uma mensagem enviada. O não repúdio depende do fato de que apenas o remetente possui as características ou a assinatura exclusivas de como essa mensagem é tratada.

A criptografia pode ser usada em praticamente qualquer lugar em que haja comunicação de dados. De fato, a tendência é que toda comunicação seja criptografada.

### Funções criptográficas de hash

Hashes são usados para verificar e garantir a integridade dos dados. O hash é baseado em uma função matemática unilateral que é relativamente fácil de calcular, mas significativamente mais difícil de reverter. A moagem de café é uma boa analogia de função unidirecional. É fácil moer grãos de café, mas é quase impossível unir novamente todos os pedaços para reconstruir os grãos originais. A função de hash criptográfico também pode ser usada para verificar a autenticação.![[Pasted image 20250131203933.png]]

Como mostrado na figura, uma função hash leva um bloco variável de dados binários, chamado de mensagem, e produz uma representação condensada de comprimento fixo, chamado hash. O hash resultante também é às vezes chamado de mensagem digest, digest ou impressão digital.

Com funções hash, é computacionalmente inviável que dois conjuntos diferentes de dados apresentem a mesma saída hash. Cada vez que os dados são modificados ou alterados, o valor de hash também muda. Por isso, muitas vezes os valores criptográficos de hash são chamados de impressões digitais. Eles podem ser usados para detectar arquivos de dados duplicados, alterações de versão de arquivo e aplicativos semelhantes. Esses valores são usados para proteger contra uma alteração acidental ou intencional dos dados ou corrupção acidental dos dados.

A função hash criptográfico é aplicada em muitas situações diferentes para autenticação de entidade, integridade de dados e fins de autenticidade de dados.

### Operação de hash criptográfico

Matematicamente, a equação **_h= H(x)_** é usada para explicar como um algoritmo de hash opera. Como mostrado na figura, uma função hash H leva uma entrada x e retorna um valor hash string de tamanho fixo h.![[Pasted image 20250131204127.png]]

O exemplo na figura resume o processo matemático. Uma função hash criptográfica deve ter as seguintes propriedades:

- A entrada pode ser de qualquer comprimento.
- A saída tem um comprimento fixo.
- H(x) é relativamente fácil de calcular para qualquer x.
- H(x) é um caminho e não reversível.
- H(x) é livre de colisões, o que significa que dois valores de entrada diferentes resultarão em valores de hash diferentes.

Se uma função hash é difícil de inverter, ela é considerada um hash unidirecional. Difícil de inverter significa que dado um valor de hash de _h_, é computacionalmente inviável encontrar uma entrada para x tal que _h=h (x)._
### MD5 e SHA

As funções de hash são usadas para garantir a integridade de uma mensagem. Eles garantem que os dados não foram alterados acidentalmente ou intencionalmente. Na figura, o remetente está enviando uma transferência de dinheiro de US $ 100 para Alex. O remetente deseja garantir que a mensagem não seja alterada acidentalmente no caminho para o destinatário. Alterações deliberadas que são feitas por um ator ameaça ainda são possíveis.![[Pasted image 20250131204328.png]]
O algoritmo de hash funciona da seguinte forma:

1. O dispositivo de envio insere a mensagem em um algoritmo de hashing e calcula seu hash de comprimento fixo de **4ehiDx67NMop9**.
2. Esse hash é anexado à mensagem e enviado ao destinatário. A mensagem e o hash estão em texto sem formatação.
3. O dispositivo receptor remove o hash da mensagem e insere a mensagem no mesmo algoritmo de hash. Se o hash calculado for igual ao que está anexado à mensagem, a mensagem não foi alterada durante o trânsito. Se os hashes não forem iguais, conforme mostrado na figura, a integridade da mensagem não será mais confiável.

Existem quatro funções hash bem conhecidas:

- **MD5 com resumo de 128 bits** - Desenvolvido por Ron Rivest e usado em uma variedade de aplicações de internet, MD5 é uma função unidirecional que produz uma mensagem hash de 128 bits. MD5 é considerado um algoritmo legado e deve ser evitado e usado apenas quando não houver alternativas melhores disponíveis. Recomenda- se que SHA-2 ou SHA-3 sejam usados em vez disso.
- **SHA-1** — Desenvolvido pela Agência de Segurança Nacional dos EUA (NSA) em 1995. É muito semelhante às funções hash MD5. Existem várias versões. O SHA-1 cria uma mensagem de 160 bits e é um pouco mais lento que o MD5. O SHA-1 possui falhas conhecidas e é um algoritmo antigo.
- **SHA-2** — Desenvolvido pela NSA. Inclui SHA-224 (224 bits), SHA-256 (256 bits), SHA-384 (384 bits) e SHA-512 (512 bits). Se você estiver usando SHA-2, então os algoritmos SHA-256, SHA-384 e SHA-512 devem ser usados sempre que possível.
- **SHA-3** - SHA-3 é o mais novo algoritmo de hash e foi introduzido pelo NIST como uma alternativa e eventual substituição para a família SHA-2 de algoritmos de hash. SHA-3 inclui SHA3-224 (224 bits), SHA3-256 (256 bits), SHA3-384 (384 bits) e SHA3-512 (512 bits). A família SHA-3 são algoritmos de última geração e devem ser usados sempre que possível.

Embora o hashing possa ser usado para detectar alterações acidentais, ele não pode ser usado para proteger contra alterações deliberadas feitas por um agente de ameaça. Não há informações de identificação única do remetente no procedimento de hash. Isso significa que qualquer pessoa pode processar um hash para quaisquer dados, desde que tenha a função hash correta.

Por exemplo, quando a mensagem atravessa a rede, um invasor em potencial pode interceptar a mensagem, alterá-la, recalcular o hash e anexá-lo à mensagem. O dispositivo receptor só validará contra o hash que estiver anexado.

Portanto, hash é vulnerável a ataques man in the middle e não oferece segurança aos dados transmitidos. Para fornecer autenticação de integridade e origem, é necessário algo mais.

**Observação: Os algoritmos** de hash protegem somente contra alterações acidentais e não protegem os dados contra alterações feitas deliberadamente por um ator de ameaça.
### Autenticação da origem

Para adicionar autenticação de origem e garantia de integridade, use um código de autenticação de mensagem hash com chave (HMAC). HMACs usam uma chave secreta adicional como entrada à função hash.

**Observação:** Outros métodos MAC (Message Authentication Code) também são usados. No entanto, o HMAC é usado em muitos sistemas, incluindo SSL, IPsec e SSH.

**Algoritmo de hash HMAC**

Conforme mostrado na figura, um HMAC é calculado usando qualquer algoritmo criptográfico que combina uma função hash criptográfica com uma chave secreta. As funções de hash são a base do mecanismo de proteção dos HMACs.

Somente o remetente e o destinatário têm conhecimento da chave secreta e agora a saída da função hash depende dos dados de entrada e da chave secreta. Apenas as partes que têm acesso a essa chave secreta podem calcular o digest de uma função HMAC. Isso derrota os ataques man-in-the-middle e fornece autenticação da origem dos dados.

Se duas partes compartilharem uma chave secreta e usarem as funções HMAC para autenticação, uma mensagem HMAC adequadamente construída, a parte recebeu indica que a outra parte foi a originadora da mensagem. Isso ocorre porque a outra parte possui a chave secreta.![[Pasted image 20250131205150.png]]

**Criação de valor HMAC**

Conforme mostrado na figura, o dispositivo de envio insere dados (como o pagamento de Terry Smith de US $ 100 e a chave secreta) no algoritmo de hash e calcula o HMAC Digest de comprimento fixo. Esse Digest autenticado é anexado à mensagem e enviado ao destinatário.![[Pasted image 20250131205300.png]]

**Verificação do valor de HMAC**

Na figura, o dispositivo receptor remove o Digest da mensagem e usa a mensagem de texto sem formatação com sua chave secreta como entrada na mesma função de hash. Se o Digest calculado pelo dispositivo receptor for igual ao resumo enviado, a mensagem não foi alterada. Adicionalmente, a origem da mensagem é autenticada porque apenas o remetente possui uma cópia da chave secreta compartilhada. A função HMAC garantiu a autenticidade da mensagem.![[Pasted image 20250131205433.png]]

**Exemplo Cisco Router HMAC**

A figura mostra como os HMACs são usados pelos roteadores Cisco configurados para usar a autenticação de roteamento Open Shortest Path First (OSPF).

R1 está enviando uma atualização de estado do link (LSU) referente a uma rota para a rede 10.2.0.0/16:

1. R1 calcula o valor do hash usando a mensagem LSU e a chave secreta.
2. O valor do hash resultante é enviado com o LSU para o R2.
3. R2 calcula o valor do hash usando o LSU e sua chave secreta. R2 aceita a atualização se os valores de hash corresponderem. Se eles não corresponderem, o R2 descartará a atualização.
![[Pasted image 20250131205622.png]]
# Confidencialidade

### Sigilo dos dados

Existem duas classes de criptografia usadas para fornecer confidencialidade de dados; assimétrico e simétrico. Essas duas classes diferem na maneira como usam as chaves.

Algoritmos de criptografia simétrica, como Data Encryption Standard (DES), 3DES e Advanced Encryption Standard (AES), baseiam-se na premissa de que cada parte que se comunica conhece a chave pré-compartilhada. A confidencialidade dos dados também pode ser garantida usando algoritmos assimétricos, incluindo Rivest, Shamir e Adleman (RSA) e a infraestrutura de chave pública (PKI).

**Nota: O** DES é um algoritmo legado e não deve ser usado. 3DES deve ser evitado, se possível.

A figura destaca algumas diferenças entre criptografia simétrica e assimétrica.![[Pasted image 20250131205954.png]]

### Criptografia Simétrica

Os algoritmos simétricos usam a mesma chave pré-compartilhada para criptografar e descriptografar dados. Uma chave pré-compartilhada, também chamada de chave secreta, é conhecida pelo remetente e pelo receptor antes que qualquer comunicação criptografada possa ocorrer.

Para ajudar a ilustrar como a criptografia simétrica funciona, considere um exemplo em que Alice e Bob moram em locais diferentes e desejam trocar mensagens secretas entre si por meio do sistema de correio. Alice deseja enviar uma mensagem secreta para Bob.

Na figura, Alice e Bob têm chaves idênticas para um único cadeado. A troca de chaves aconteceu antes de enviar quaisquer mensagens secretas. Alice escreve uma mensagem secreta e a coloca em uma pequena caixa trancada com o cadeado. Ela manda a caixa para Bob. A mensagem está segura e trancada dentro da caixa, à medida que a caixa segue seu caminho através do sistema de correios. Quando Bob recebe a caixa, ele usa a chave para destrancar o cadeado e recuperar a mensagem. Bob pode usar a mesma caixa e cadeado para enviar uma resposta secreta para Alice.![[Pasted image 20250131210202.png]]

Hoje, algoritmos de criptografia simétrica são comumente usados com o tráfego VPN. Isso ocorre porque os algoritmos simétricos usam menos recursos da CPU do que os algoritmos de criptografia assimétrica. Isso permite que a criptografia e a descriptografia de dados sejam rápidas ao usar uma VPN. Ao usar algoritmos de criptografia simétrica, como qualquer outro tipo de criptografia, quanto maior a chave, mais tempo levará para alguém descobrir a chave. A maioria das chaves de criptografia tem entre 112 e 256 bits. Para garantir que a criptografia é segura, um comprimento mínimo de chave de 128 bits deve ser usado. Use uma chave mais longa para comunicações mais seguras.

Algoritmos de criptografia simétrica às vezes são classificados como uma cifra de bloco ou uma cifra de fluxo.

**Cifras de bloco**

As cifras de bloco transformam um bloco de texto simples de comprimento fixo em um bloco comum de texto cifrado de 64 ou 128 bits. As cifras de bloco comuns incluem DES com um tamanho de bloco de 64 bits e AES com um tamanho de bloco de 128 bits.
![[Pasted image 20250131210346.png]]

**Cifras de fluxo**

As cifras de fluxo criptografam o texto simples um byte ou um bit de cada vez. As cifras de fluxo são basicamente uma cifra de bloco com um tamanho de bloco de um byte ou bit. As cifras de fluxo geralmente são mais rápidas do que as cifras de bloco porque os dados são criptografados continuamente. Exemplos de cifras de fluxo incluem RC4 e A5, que é usado para criptografar comunicações de telefone celular GSM.![[Pasted image 20250131210459.png]]

Algoritmos de criptografia simétrica mais conhecidos são descritos na tabela.
![[Pasted image 20250131210553.png]]
### Criptografia Assimétrica

Os algoritmos assimétricos, também chamados algoritmos de chave pública, são projetados para que a chave usada para criptografia seja diferente da chave usada para descriptografia, conforme mostrado na figura. A chave de descriptografia não pode, em uma quantidade razoável de tempo, ser calculada a partir da chave de criptografia e vice-versa.![[Pasted image 20250131210636.png]]

Algoritmos assimétricos usam uma chave pública e uma chave privada. Ambas as chaves são capazes do processo de criptografia, mas a chave emparelhada complementar é necessária para descriptografia. O processo também é reversível. Os dados criptografados com a chave pública requerem a chave privada para descriptografar. Algoritmos assimétricos alcançam confidencialidade e autenticidade usando este processo.

Como nenhuma das partes possui um segredo compartilhado, é necessário usar comprimentos de chave muito longos. A criptografia assimétrica pode usar comprimentos de chave entre 512 e 4.096 bits. Comprimentos de chave maiores ou iguais a 2.048 bits podem ser confiáveis, enquanto comprimentos de chave de 1.024 ou menores são considerados insuficientes.

Exemplos de protocolos que usam algoritmos de chave assimétrica incluem:

- **Internet Key Exchange (IKE) -** é um componente fundamental das redes virtuais privadas IPsec (VPNs).
- **Secure Socket Layer (SSL) -**Agora isso é implementado como TLS (Transport Layer Security) padrão da IETF.
- **Secure Shell (SSH) -** Este protocolo fornece uma conexão segura de acesso remoto a dispositivos de rede.
- **Pretty Good Privacy (PGP) -** Este programa de computador fornece privacidade e autenticação criptográficas. É frequentemente usado para aumentar a segurança das comunicações por email.

Os algoritmos assimétricos são substancialmente mais lentos que os algoritmos simétricos. Seu design é baseado em problemas computacionais, como fatorar números extremamente grandes ou calcular logaritmos discretos de números extremamente grandes.

Por serem lentos, algoritmos assimétricos geralmente são usados em mecanismos criptográficos de baixo volume, como assinaturas digitais e troca de chaves. No entanto, o gerenciamento de chaves de algoritmos assimétricos tende a ser mais simples que os algoritmos simétricos, porque geralmente uma das duas chaves de criptografia ou descriptografia pode ser tornada pública.

Exemplos comuns de algoritmos de criptografia assimétrica são descritos na tabela.![[Pasted image 20250131210916.png]]

### Criptografia Assimétrica - Confidencialidade

Algoritmos assimétricos são usados para fornecer confidencialidade sem pré-compartilhar uma senha. O objetivo de confidencialidade dos algoritmos assimétricos é iniciado quando o processo de criptografia é iniciado com a chave pública.

O processo pode ser resumido usando a fórmula:

**Chave pública (criptografar) + chave privada (descriptografar) = confidencialidade**

Quando a chave pública é usada para criptografar os dados, a chave privada deve ser usada para descriptografar os dados. Apenas um host tem a chave privada; portanto, a confidencialidade é alcançada.

Se a chave privada estiver comprometida, outro par de chaves deve ser gerado para substituir a chave comprometida.

### Criptografia assimétrica - Autenticação

O objetivo de autenticação de algoritmos assimétricos é iniciado quando o processo de criptografia é iniciado com a chave privada.

O processo pode ser resumido usando a fórmula:

**Chave privada (criptografar) + chave pública (descriptografar) = autenticação**

Quando a chave privada é usada para criptografar os dados, a chave pública correspondente deve ser usada para descriptografar os dados. Como apenas um host tem a chave privada, somente esse host poderia ter criptografado a mensagem, fornecendo autenticação do remetente. Normalmente, nenhuma tentativa é feita para preservar o sigilo da chave pública, portanto, qualquer número de hosts pode descriptografar a mensagem. Quando um host descriptografa uma mensagem com êxito usando uma chave pública, é confiável que a chave privada criptografou a mensagem, o que verifica quem é o remetente. Esta é uma forma de autenticação.

### Criptografia assimétrica - Integridade

Combinar os dois processos de criptografia assimétrica fornece confidencialidade, autenticação e integridade da mensagem.
![[Pasted image 20250131211527.png]]

### Diffie-Hellman

Diffie-Hellman (DH) é um algoritmo matemático assimétrico que permite que dois computadores gerem um segredo compartilhado idêntico sem terem se comunicado antes. A nova chave compartilhada nunca é realmente trocada entre o remetente e o destinatário. No entanto, como as duas partes o conhecem, a chave pode ser usada por um algoritmo de criptografia para criptografar o tráfego entre os dois sistemas.

Aqui estão dois exemplos de casos em que DH é comumente usado:

- Os dados são trocados usando uma VPN IPsec
- Dados SSH são trocados

Para ajudar a ilustrar como o DH opera, consulte a figura.
![[Pasted image 20250131211714.png]]

As cores na figura serão usadas em vez de números longos complexos para simplificar o processo de contrato de chave DH. A troca de chaves DH começa com Alice e Bob concordando com uma cor comum arbitrária que não precisa ser mantida em segredo. A cor combinada em nosso exemplo é amarelo.

Em seguida, Alice e Bob selecionarão uma cor secreta. Alice escolheu vermelho enquanto Bob escolheu azul. Essas cores secretas nunca serão compartilhadas com ninguém. A cor secreta representa a chave privada secreta escolhida de cada parte.

Alice e Bob agora misturam a cor comum compartilhada (amarelo) com suas respectivas cores secretas para produzir uma cor pública. Portanto, Alice vai misturar o amarelo com sua cor vermelha para produzir uma cor pública de laranja. Bob irá misturar o amarelo e o azul para produzir uma cor pública de verde.

Alice envia sua cor pública (laranja) para Bob e Bob envia sua cor pública (verde) para Alice.

Alice e Bob misturam a cor que receberam com a sua própria cor secreta original (vermelho para Alice e azul para Bob). O resultado é uma mistura final de cor marrom que é idêntica à mistura de cor final do parceiro. A cor marrom representa a chave secreta compartilhada resultante entre Bob e Alice.

A segurança do DH se baseia-se no fato de que ele usa números muito grandes em seus cálculos. Por exemplo, um número DH 1024 bits é aproximadamente igual a um número decimal de 309 dígitos. Considerando que um bilhão é 10 dígitos decimais (1.000.000.000), pode-se facilmente imaginar a complexidade de trabalhar não com um, mas com vários números decimais de 309 dígitos.

Diffie-Hellman usa diferentes grupos DH para determinar a força da chave que é usada no processo de acordo de chave. Os números de grupo mais altos são mais seguros, mas exigem tempo adicional para calcular a chave. O seguinte identifica os grupos DH suportados pelo Cisco IOS Software e seu valor de número primo associado:

- DH Group 1: 768 bits
- DH Group 2: 1024 bits
- DH Group 5: 1536 bits
- DH Group 14: 2048 bits
- DH Group 15: 3072 bits
- DH Group 16: 4096 bits

**Nota**: Um acordo de chave DH também pode ser baseado em criptografia de curva elíptica. Os grupos DH 19, 20 e 24, que são baseados em criptografia de curva elíptica, também são suportados pelo Cisco IOS Software.

Infelizmente, os sistemas de chave assimétrica são extremamente lentos para qualquer tipo de criptografia em massa. É por isso que é comum criptografar a maior parte do tráfego usando um algoritmo simétrico, como 3DES ou AES, e usar o algoritmo DH para criar chaves que serão usadas pelo algoritmo de criptografia.
# Criptografia de chave pública

As assinaturas digitais são uma técnica matemática usada para fornecer autenticidade, integridade e não repúdio. As assinaturas digitais têm propriedades específicas que permitem autenticação de entidade e integridade de dados. Além disso, as assinaturas digitais fornecem não repúdio da transação. Em outras palavras, a assinatura digital serve como prova legal de que o intercâmbio de dados ocorreu. As assinaturas digitais usam criptografia assimétrica.
![[Pasted image 20250131212644.png]]
As assinaturas digitais são comumente usadas nas duas situações a seguir:

1. **Assinatura de código** — Isso é usado para fins de autenticação e integridade de dados. A assinatura de código é usada para verificar a integridade dos arquivos executáveis baixados do site de um fornecedor. Ele também usa certificados digitais assinados para autenticar e verificar a identidade do site que é a origem dos arquivos.
2. **Certificados digitais** - são semelhantes a um cartão de identificação virtual e usados para autenticar a identidade do sistema com o site de um fornecedor e estabelecer uma conexão criptografada para trocar dados confidenciais.

Existem três algoritmos DSS (Digital Signature Standard) que são usados para gerar e verificar assinaturas digitais:

- **Algoritmo de Assinatura Digital (DSA)** - DSA é o padrão original para gerar pares de chaves públicas e privadas e para gerar e verificar assinaturas digitais.
- **Rivest-Shamir Adelman Algoritmo (RSA)** - RSA é um algoritmo assimétrico que é comumente usado para gerar e verificar assinaturas digitais.
- **Elliptic Curve Digital Signature Algoritmo (ECDSA)** - O ECDSA é uma variante mais recente do DSA e fornece autenticação de assinatura digital e não repúdio com os benefícios adicionais da eficiência computacional, tamanhos de assinatura pequenos e largura de banda mínima.

Na década de 1990, a RSE Security Inc. começou a publicar padrões de criptografia de chave pública (PKCS). Havia 15 PKCS, embora 1 tenha sido retirado a partir do momento em que esta escrita foi escrita. A RSE publicou estes padrões porque possuíam as patentes aos padrões e desejavam promovê-los. Os PKCS não são padrões do setor, mas são bem reconhecidos no setor de segurança e recentemente começaram a se tornar relevantes para organizações de padrões como o grupo de trabalho IETF e PKIX.

### Assinaturas digitais para assinatura de código

As assinaturas digitais são comumente usadas para garantir a autenticidade e integridade do código de software. Os arquivos executáveis são empacotados em um envelope assinado digitalmente, o que permite ao usuário final verificar a assinatura antes de instalar o software.

Assinar digitalmente o código fornece várias garantias sobre o código:

- O código é autêntico e é realmente originado pela editora.
- O código não foi modificado desde que saiu do editor do software.
- A editora publicou inegavelmente o código. Isso fornece não repúdio do ato de publicação.

A Publicação 140-3 do FIPS (Federal Information Processing Standard) do Governo dos EUA especifica que o software disponível para download na internet deve ser assinado e verificado digitalmente. O objetivo do software assinado digitalmente é garantir que o software não foi adulterado e que ele foi originado da fonte confiável, conforme reivindicado. As assinaturas digitais servem como verificação de que o código não foi adulterado por agentes da ameaça e o código malicioso não foi inserido no arquivo por terceiros.

### Assinaturas digitais para certificados digitais

Um certificado digital é equivalente a um passaporte eletrônico. Ele permite que usuários, hosts e organizações troquem informações com segurança pela Internet. Especificamente, um certificado digital é usado para autenticar e verificar se um usuário que está enviando uma mensagem é quem afirma ser. Os certificados digitais também podem ser usados para fornecer confidencialidade ao receptor com os meios de criptografar uma resposta.

Os certificados digitais são semelhantes aos certificados físicos. Por exemplo, o certificado Cisco Certified Network Associate Security (CCNA-S) em papel na figura identifica para quem o certificado foi emitido, quem autorizou o certificado e por quanto tempo o certificado é válido. Os certificados digitais também fornecem informações semelhantes.![[Pasted image 20250131213055.png]]O certificado digital verifica de forma independente uma identidade. Assinaturas digitais são usadas para verificar se um artefato, como um arquivo ou mensagem, é enviado pelo indivíduo verificado. Em outras palavras, um certificado verifica a identidade, uma assinatura verifica se algo vem dessa identidade.

Esse cenário ajudará você a entender como uma assinatura digital é usada. Bob está confirmando um pedido com Alice. Alice está encomendando do site do Bob. Alice se conectou com o site de Bob, e depois que o certificado foi verificado, o certificado de Bob é armazenado no site de Alice. O certificado contém a chave pública de Bob. A chave pública é usada para verificar a assinatura digital do Bob.

Consulte a figura para ver como a assinatura digital é usada.![[Pasted image 20250131213150.png]]
Bob confirma a ordem e seu computador cria um hash da confirmação. O computador criptografa o hash com a chave privada do Bob. O hash criptografado, que é a assinatura digital, é anexado ao documento. A confirmação do pedido é então enviada para Alice através da internet.

Quando Alice recebe a assinatura digital, ocorre o seguinte processo.
![[Pasted image 20250131213221.png]]1. O dispositivo receptor de Alice aceita a confirmação do pedido com a assinatura digital e obtém a chave pública de Bob.
1. O computador de Alice descodifica a assinatura usando a chave pública de Bob. Esta etapa revela o valor de hash assumido do dispositivo de envio.
2. O computador de Alice cria um hash do documento recebido, sem sua assinatura, e compara esse hash com o hash de assinatura descriptografado. Se os hashes corresponderem, o documento é autêntico. Isso significa que a confirmação foi enviada por Bob e que ela não mudou desde que foi assinada.


