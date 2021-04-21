Aula 3 | _Lecture 3_
===

###### tags: `Segurança Informática`, `Cifras de Chave Simétrica por Blocos`

:::info
- **Local:** _Online_
- **Sumário**  
- **Link:** [Hackmd.io](https://hackmd.io/G1d5P00rQPyTh-51YJMdtg?view)
- **Autores:** Pedro R. M. Inácio [(inacio@di.ubi.pt)](mailto:inacio@di.ubi.pt)
- **Edição/Revisão:** xxx.
:::


## Cifras de Chave Simétrica Contínuas

As _stream ciphers:_
  * permitem cifrar texto-limpo bit-a-bit;
  * são baseadas na geração de bits pseudo-aletórios por um gerador seguro (RC4, salsa20, chacha20, AES-CTR) e no XOR bit a bit desses bits com o texto-limpo;
  * nestas cifras, o algoritmo para cifrar é o mesmo que para decifrar;


## Cifras de Chave Simétrica por Blocos

As cifras de chave simétrica continuas permitem **cifrar bit-a-bit**, enquanto que as cifras de chave simétrica por blocos cifram sempre **bloco-a-bloco**. Estas cifras aceitam um bloco de texto-limpo, aceitam uma chave e debitam um bloco de criptograma de cada vez:
  * cifram bloco-a-bloco;
  * decifram bloco-a-bloco;
  * o tamanho do bloco de entrada é normalmente igual ao tamanho do bloco de saída;
  * o algoritmo para decifrar é inverso ao algoritmo para cifrar;

```
               +-------------+
bloco de  ---> | máquina     |
entrada        | de lavar com| -----> bloco de
               | trituradora |        criptograma
chave de --->  | misturar    |
cifra          +-------------+
```
:::success
Se a cifra for boa, então a máquina deve misturar tudo de uma forma muito eficiente e difícil de prever:
  1. Difusão (propriedades estatisticas no bloco de entrada devem ficar completamente difusas no bloco de criptograma);
  2. Confusão (as relações entre o bloco de entrada, o bloco criptograma e a chave de cifra não devem ser notáveis).
:::

Exemplos canónicos de cifras de chave simétrica por blocos:
  * _Data Encryption Standard_ (DES), chaves de 7 bytes (56 bits) e foi quebrado com um _rack_ de _playstations_ (quase _brute force_ ao conjunto de chaves). 56 bits são $2^{56}=72057594037927936$ combinações:
  ```python
  2**56
  ```
  o tamanho do bloco é de 8 bytes;
  * _Triple DES_ (3DES) . E(k3, D(k2,E(k1,m))), o tamanho da chave era 21 bytes, 168 bits;
  o tamanho do bloco é de 8 bytes;
  * _Advanced Encryption Standar_ (AES), chaves de 128 (16 bytes), 192 (24 bytes) ou 256 bits (32 bytes), e o tamanho do bloco é de 16 bytes.
 
  
**Q.:** No minimo, quantas rondas são necessárias para uma Rede de _Feistel_ ser segura?
  - [ ] zero rondas;
  - [ ] uma ronda;
  - [ ] duas rondas;
  - [x] três rondas;
  - [ ] muitas rondas.
  
**Q.:** Qual o nome do teorema que provou, em 1985, que eram precisas três rondas para que uma PRP fosse considerada segura?
  - [ ] Horst Feistel;
  - [x] Luby–Rackoff.
  
  
**Q.:** Das seguintes, em que cifras de chave simétrica por blocos é que as redes de Feistel foram usadas?
  - [x] DES 
  - [x] 3DES
  - [ ] AES
  - [ ] RSA

**Q.:** Das seguintes, em que cifras de chave simétrica por blocos é que as redes de Feistel **não** foram usadas?
  - [ ] DES 
  - [ ] 3DES
  - [x] AES
  - [ ] RSA
  
A AES usa funções de permutação e de substituição para conseguir as propriedades da difusão e da confusão.

:::info
As cifras de chave simétrica por blocos são muito importantes na atualidade e consideradas **cavalos de trabalho** para quase tudo o que é criptografia de chave simétrica. Usam-se estas cifras para:
  * cifrar por blocos;
  * construir outras cifras de chaves simétrica, mas **contínuas**!
  * criar funções de *hash*;
  * gerar números pseudo-aleatórios seguros.
:::

As cifras de chave simétrica por blocos podem ser usadas de várias formas para cifrar. A essas formas chamamos modos de cifra:
  * _Electronic Code Book_ (ECB);
      * Este modo não deve ser utilizado, a não ser para cifrar algo aleatório (e.g., uma chave de cifra) ou algo mais pequeno que o tamanho de um bloco...
  * _Cipher Block Chaining_ (CBC);
  * _CounTeR Mode_ deterministico (CTR-d);
      * este modo transforma a cifra por blocos numa cifra de chave simétrica contínua!
  * _CounTeR Mode_ aleatório (CTR);
     * este modo transforma a cifra por blocos numa cifra de chave simétrica contínua!


### _Electronic Code Book_ (ECB)

  * Este modo de cifra leva _padding_ (preenchimento) no último bloco a cifrar;
``` 
          +----------------------------------------+
          v                                        v
  | olá pedro. 11111 | olá pedro. 11112 | olá pedro. 11111 |
         | ECB(k, m1)       | ECB(k, m2)        | ECB(k, m3)   
         v                  v                   v
  | lkdjfalkdjflalkj | iluerqwoijorjnj | lkdjfalkdjflalkj |
  
```
```
olá pedro. 11111  lkdjfalkdjflalkj det chave
```

``` 
          +----------------------------------------+
          v                                        v
  | olá pedro. 11111 | olá pedro. 11112 | olá pedro. 11111 |
         | ECB(k, m1)       | ECB(k, m2)        | ECB(k, m3)   
         v                  v                   v
  | lkdjfalkdjflalkj | iluerqwjorjnjlk | djfalkdjflalkj | lkdjfalkdjflalkj |
  
```

### _Cipher Block Chaining_ (CBC)

Em Português, _Cipher Block Chaining_ (CBC) significa "encadeamento de blocos de cifra"!

  * O CBC é muito utilizado para cifrar ficheiros no disco.


**Q.:** De quantos blocos de criptograma é que eu preciso para decifrar qualquer bloco cifrado no modo CBC?
  - [ ] um bloco;
  - [x] dois blocos;
  - [ ] três blocos.


**Q.:** De quantos blocos de criptograma é que eu preciso para decifrar qualquer bloco cifrado no modo ECB?
  - [x] um bloco;
  - [ ] dois blocos;
  - [ ] três blocos.

**Q.:** É possível decifrar qualquer parte do texto-limpo independemente de tudo o resto?
  - [x] É possível, mas precisamos sempre de dois blocos adjacentes.

**Q.:** É possível **cifrar** usando processamento paralelo no modo CBC?
  - [ ] Pois tá claro que sim.
  - [x] Não, nem pensar.

**Q.:** É possível **decifrar** usando processamento paralelo no modo CBC?
  - [x] Pois tá claro que sim.
  - [ ] Não, nem pensar.
  
**Q.:** É possível cifrar usando processamento paralelo no modo ECB?
  - [x] Pois tá claro que sim.
  - [ ] Não, nem pensar.

**Q.:** É possível decifrar usando processamento paralelo no modo ECB?
  - [x] Pois tá claro que sim.
  - [ ] Não, nem pensar.

**Q.:** É possível cifrar usando processamento paralelo no modo CTR?
  - [x] Pois tá claro que sim.
  - [ ] Não, nem pensar.

**Q.:** É possível decifrar usando processamento paralelo no modo CTR?
  - [x] Pois tá claro que sim.
  - [ ] Não, nem pensar.

**Q.:** Que modos precisam de _padding_?
  - [x] CBC
  - [ ] CTR (o modo CTR transforma a cifra numa _stream cipher_, que não levam _padding!_, porque o texto-limpo é cifrado bit-a-bit)!
  - [x] ECB


**Q.:** Que modos precisam de vetor de inicialização?
  - [x] CBC
  - [x] CTR aleatoriezado
  - [ ] CTR deterministico
  - [ ] ECB

### Vetor de Inicilização

:::info
Um vetor de inicialização é um **valor aleatório**, que deve ser único para cada mensagem e que só serve para que **duas mensagems cifradas com a mesma chave, mesmo que esses mensagens sejam iguais, os criptogramas são diferentes.
:::

:::danger
O vetor de inicialização não é secreto. Secreta é a chave de cifra!
:::



### PKCS1.5 _Padding_

  Considerar que o tamanho do bloco devia ser 16 bytes
  Antes de ser cifrado, um bloco tem de ser preenchido:
```
  | xxxxxxxxxx |        --> | xxxxxxxxxx666666 |
  | xxxxxxxxxxxx |      --> | xxxxxxxxxxxx4444 |
  | xxxxxxxxxxxxxxx |   --> | xxxxxxxxxxxxxxx1 |
  | xxxxxxxxxxxxxxx1 |  --> | xxxxxxxxxxxxxxx1 |  
  | xxxxxxxxxxxxxxx1 |  --> | xxxxxxxxxxxxxxx1 | 1111111111111111 |
                                                 6666666666666666
  
```  
  Depois de ser decifrado, o preenchimento tem de ser retirado:

```
  | xxxxxxxxxx666666 | --> | xxxxxxxxxx | 
  | xxxxxxxxxxxx4444 | --> | xxxxxxxxxxxx |
  | xxxxxxxxxxxxxxx1 | --> | xxxxxxxxxxxxxxx |
  | xxxxxxxxxxxxxxx1 | --> | xxxxxxxxxxxxxxx |  
  | xxxxxxxxxxxxxxxx | 1111111111111111 |
                       6666666666666666
                       --->                        
  | xxxxxxxxxxxxxxx1 |
```  
Quando aplicamos este padding, asssume-se sempre que é colocado algum preenchimento, mesmo quando o bloco está cheio. Ao assumir isto temos a certeza que quando vamos tirar o preenchimento estão protegidos os casos em que as últimas letras são parecidas às do preenchimento...
  ...
  
  
  
  
  
  
  
  
  
  
  
  