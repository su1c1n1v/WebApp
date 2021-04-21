Guia Laboratorial 1 | _Laboratory Guide 1_
===

###### tags: `Segurança Informática`, `Guia 1`

:::info
- **Local:** _Online_
- **Sumário**  
- **Link:** [Hackmd.io](https://hackmd.io/i1__5ByBQBa16oebHBTjrQ?view)
- **Autores:** Pedro R. M. Inácio [(inacio@di.ubi.pt)](mailto:inacio@di.ubi.pt)
- **Edição/Revisão:** xxx.
:::

##  Cifras Clássicas

### Cifras Monoalfabéticas

A mesma "letra" e transformada sempre da mesma maneira, indepentemente do local onde está na mensagem (isto é mau).

#### Cifra de César

Segundo o imperador Romano César, cifrar consistia em andar três letras para a esquerda; decifrar consistia em andar três letras para a direita. 

$M$ é a letra a cifrar e $C$ é o criptograma.

O algoritmo de cifra   $C = E(k,M) = M + k \mod 26$.
O algoritmo de decifra $M = D(k,M) = C - k \mod 26$.

Na verdade, para a cifra de César, 
$C = E(k,M) = M + 23 \mod 26$;
$M = D(k,M) = C - 23 \mod 26$;
é equivalente a
$C = E(k,M) = M - 3 \mod 26$;
$M = D(k,M) = C + 3 \mod 26$.

---

**Tarefa 1 (1 minuto)**

$C=E(23,\text{OLA}) = \text{LIX}$

```
Ajuda:
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
0 1 2 3 4 5 6 7 8 9 1 1 1 1 1 1 1 1 1 1 2 2 
                    0 1 2 3 4 5 6 7 8 9 0 1
```

---

**Tarefa 2 (2 minutos)**

$D(10,\text{LOXPSMKOYWKSYB}) = \text{BENFICA E O MAIOR}$

---

**Tarefa 3 (12 minutos)**

J HVM NVGBVYJ, LPVIOJ YJ OZP NVG
NVJ GVBMDHVN YZ KJMOPBVG!

```
J ||||| 
H ||
V ||||||||| A (a chave é 21 M-21 mod 26)
M |||
N ||||
G ||||
B |||
Y |||
L |
P |||
I |
O |||
Z ||
D |
K |
```

O MAR SALGADO, QUANTO DO TEU SAL
SAO LAGRIMAS DE PORTUGAL!


-21 é igual a +5 mod 26

--- 

K = 0 x
K = 1 
K = 2
K = 3
...
K = 25
K = 26 x 

---

**Tarefa 4 (2 minutos)**

```
  TIOMANELTINHAUMAQUINTA
+ AULAAULAAULAAULAAULAAU
------------------------
  
```

TIO MANEL TINHA UMA QUINTA

#### Cifra de Sustituição 

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
S Q T U H J I B Y K A V L C W E Z N R M X G F P D O

PEDRO
EHUNW
```

**Q8.:**

```
A  B  C  D E F G H I J K L M N O P Q R S T U V W X Y Z
26 25 24

1 chave que não é boa!
```

O número de chaves é $26\times 25\times 24 \times 23 ... \times 1-1 = 26!-1$



### Cifras Polialfabéticas

A mesma "letra" pode ser transformada de maneiras diferentes em partes diferentes do processamento.

#### Cifra de Vigenere

**Tarefa 4 (10 minutos)**

```
  TIO MANEL TINHA UMA QUINTA
+ AUL AAULA AULAA ULA AULAAU
----------------------------
  TCZ MAHPL TCYHA OXA QOTNTU
```

8+20 mod 26 = 28 mod 26 = 2 (A=0, B=1, C=2)

---

**Q5.:**

 $26\times 26\times 26 \times 26  - 1 = 26^4 - 1$
 
 AAAA Não dá! :-1: 
 AAAB
 AAAC
 ...
 AAAZ
 BBBA
 BBBB
 BBBC
 ...
 BBBZ
 C 
 D
 E
 F
 
---

**Q5.:**


---

**Tarefa 5 (10 minutos)**

```
  JUWP G IBELM
 -BCDB C DBCDB
 --------------
  ISTO E FACIL 
```


#### Enigma

A chave de cifra da Enigma era constituida por:
  * As ligações no _switchboard_;
  * Era preciso escolher três rotores de um total de cinco;
  * Era preciso dizer em que posição cada rotor começava (26 posições possíveis);
  * Era preciso dizer qual a posição do primeiro para o segundo rotor, e do segundo para o terceiro rotor em que esses rotores rodavam;
 
O número total de chaves era dado por:
  * $A^5_3$ (para escolher rotores);
  * $26^3$ posições para os rotores;
  * $26^2$ possibilibilidades de iteração do primeiro para o segundo e do segundo para o terceiro rotor;
  * perfazendo 712882560 de combinações (sem o _switchboard_).


#### _One Time Pad_

A _one time pad_ é a cifra perfeita (em termos de secretismo).

```
E.g., 
0101110101001010
```

Quantos 0s:  8 zeros     (esperávamos 8)
Quantos 1s:  8 uns       (esperávamos 8)
Quantos 00s: 1 zero-zero (esperávamos 4)
Quantos 01s: 6 zero-um   (esperávamos 4)
Quantos 10s: 6 um-zero   (esperávamos 4)
Quantos 11s: 2 um-um     (esperávamos 4)


16 x 0.5 = 8 caras e 8 coroas
           16 caras e 0 coroas
           
00 0.5 x 0.5 = 0.25 x 16 = 4 
01 0.5 x 0.5 = 0.25 x 16 = 4
10
11


A probabilidade de sair 1 ou 0, mandando a moeda ao ar é 0.5, independentemente da iteração em que estamos.
Neste caso, nós não sabemos nada do futuro.

```
    0000000100000001  mensagem a transmitir
xOR 0101110101001010  chave de cifra  (16 bits) gerada com 
    0101110001001011  criptograma     (16 bits)
```
**Texto-limpo:**
Quantos 0s: 14 zeros não parece ter aleatoriedade
Quantos 1s: 2  uns
Quantos 00s: 12 00s 
Quantos 01s: 2 01s
...

**Criptograma:**
Quantos 0s: 8 zeros (esperávamos 8) parece ter aleatoriedade!
Quantos 1s: 8 uns (esperávamos 8)
Quantos 00s: 3 00s (esperávamos 4)
Quantos 01s: 5 01s (esperávamos 4)
...



```
    0000000100000001 texto-limpo     (16 bits)
xOR 1001110101101010 chave de cifra  (16 bits) gerada com uma moeda
    1001110001101011 criptograma     (16 bits)
```
**Texto-limpo:**
Quantos 0s: 14 zeros não parece ter aleatoriedade
Quantos 1s: 2  uns
Quantos 00s: 12 00s 
Quantos 01s: 2 01s
...

**Criptograma:**
Quantos 0s: 7 zeros (esperávamos 8) parece ter aleatoriedade!
Quantos 1s: 9 uns (esperávamos 8)
Quantos 00s: 3 00s (esperávamos 4)
Quantos 01s: 4 01s (esperávamos 4)
...


```
    ttttttttt0tttttt
xOR 0010xxxxx0xxxxxx 
    1010001100011100 => 
```


```
1001110001101011
1001110101101010 chave de cifra
0000000100000001

```

Quando fazemos xOR de algo que não é aleatório com algo que é aleatório, o resultado dá aleatório!


Imaginem agora que queriam enviar o CoD inteiro a um(a) colega. Queriam cifrar o ficheiro antes de o enviar com a _One time pad_. 400GB
Quantas vezes teriam de mandar uma moeda ao ar? Quantos 0s e 1s aleatórios teriam de gerar?

  1. Teriam de gerar 400GB de 0s e 1s;
  2. Teriam de enviar o jogo cifrado e depois tinham de ir entregar a chave ao(à) colega.


A _One Time Pad_ tem secretismo perfeito, mas não pode ser usada na prática. As cifras de chave simétrica continuas são a imitação desta cifra, mas com chaves usáveis...



```
    0101110001001011  criptograma     (16 bits)
xOR 0101110101001010
    0000000100000001
```



