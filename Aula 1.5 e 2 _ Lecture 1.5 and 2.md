Aula 1.5 e 2 | _Lecture 1.5 and 2_
===

###### tags: `Segurança Informática`, `Lei do Cibercrime`, `Introdução à Criptografia`

:::info
- **Local:** _Online_
- **Sumário**  
- **Link:** [Hackmd.io](https://hackmd.io/xKlyAakbRCmZ8cwvWK1pGA?view)
- **Autores:** Pedro R. M. Inácio [(inacio@di.ubi.pt)](mailto:inacio@di.ubi.pt)
- **Edição/Revisão:** xxx.
:::

##  Lei do Cibercrime

Domínios de Guerra:

  * Ciber-espaço - ciber-espionagem, contra informação e ataques cibernéticos (a infrastruturas criticas);
  * Terra;
  * Ar;
  * Água/Mar;
  * Espaço.

Há assuntos com especial destaque na Lei do Cibercrime:
  * Crimes sexuais contra menores;
  * 

Classificação de Documentos ou Informação:
  * _Unclassified_;
  * _Confidential_;
  * _Secret_;
  * _Ultra Secret_.

Um agente que lê os dados também tem de ter uma classificação.
_James Bond_ tem classe _secret_, o que significa que pode:
 * Ler os documentos _Unclassified_, _Confidential_ e _Secret_;
 * Mas **não** pode ler os _Ultra Secret_.

Também significa que:
 * Pode escrever em documentos _Ultra Secret_;
 * Mas **não** pode escrever em documentos _Unclassified_, _Confidential_ e _Secret_.


##  Introdução à Criptografia

A Internet é hoje o _habitat_ natural para a Criptografia, e é extremamente prolífero em necessidades.

### Cripto+grafia (segredo+escrever)

Escrever em segredo de todas as entidades excepto as autorizadas.
Parte que está preocupada em desenvolver técnicas que permitam o objetivo de escrever em segredo.

### Cript+análise (segredo+análise)

Parte que tenta quebrar, através da análise **(inteligência)**, as técnicas da critografia.
Parte que está preocupada em desenvolver técnicas que permitam o objetivo de quebrar as técnicas descritas em cima.

Os ataques de força bruta _(brute force attacks)_ **não** fazem parte da criptanálise.
Se uma cifra só puder ser quebrada com um ataque de _brute force_, então a cifra é boa e fica segura se o número de chaves possível for extremamente grande (no mínimo, $2^{80}= 1208925819614629174706176$ possibilidades).


### Cripto+logia (segredo+ciência)

É a ciência que congrega ambas as anteriores.


### Funcionamento da Criptografia (pode ser aplicado ao desenvolvimento de software seguro)

  1. Especifica-se o sistema (requisitos funcionais e não funcionais, bem como os requisitos de segurança). **Definimos o modelo de ataque;**
  2. Propõe-se uma construção que preencha os requisitos e evite o ataque (baseada num problema matemático que se saiba ser impossível de resolver na prática);
  3. Prova-se que o comprometimento da comunicação corresponde à resolução daquele problema considerado impossível na prática.


### Cenário Histórico

#### Confidencialidade

Alice quer falar com o Bob, mas não quer que a Claire saiba o que ela vai dizer. Contudo, a comunicação é feita por um canal aberto a que a Claire pode ter acesso.

Alice escreve a mensagem.
Alice cifra a mensagem.
Alice envia a mensagem.

Bob recebe a mensagem.
Bob decifra a mensagem.
Bob lã a mensagem.




### Cenários Modernos 

#### Integridade

Alice quer enviar uma mensagem ao Bob, mas não é secreta. A Alice quer ter a certeza que ninguém muda a mensagem até chegar ao Bob. Contudo, a comunicação é feita por um canal aberto a que a Claire pode ter acesso. Neste caso, a Claire pode ler a mensagem, e pode tentar mudar a mensagem antes de chegar ao Bob. 

####  Anonimato

A Alice quer enviar uma informação ao Bob, mas não quer que ninguém saiba que é ela.


###  Definição de Cifras

No contexto da unidade curricular, vamos falar em dois tipos principais de cifras:

####  Cifras de Chave Simétrica

Cifras de chave simétrica são cifras que usam **a mesma chave para cifrar e para decifrar**.

:::info
**Definição Matemática**
Uma cifra de chave simétrica é definida para **três** conjuntos:
  * o conjunto de chaves de cifra $\mathcal{K}$;
  * o conjunto de textos-limpos $\mathcal{M}$;
  * c conjunto de criptogramas $\mathcal{C}$;
por **dois** algoritmos (um para cifrar, outro para decifrar):
  * Algoritmo para cifrar $c=E(k,m): \mathcal{K},\mathcal{M}\rightarrow\mathcal{C}$;
  * Algoritmo para decifrar $m=D(k,c): \mathcal{K},\mathcal{C}\rightarrow\mathcal{M}$.
:::

##### Cifras de Chave Simétrica Contínuas

As Cifras de Chave Simétrica Contínuas permitem cifrar as mensagens à medida que a mensagem é gerada ou de forma sequencial. A mensagem pode ser cifrada à medida que fica disponível.

Exemplos canónicos:
  * RC4;
  * Salsa20;
  * Chacha20;
  * AES-CTR.

##### Cifras de Chave Simétrica por Blocos

Atual por blocos, o que significa que é preciso estar disponível um bloco de cada vez que quero cifrar.

Estas cifras são as mais importantes da atualidade (em termos de cifras de chave simétrica) e, de certas formas, permitem construir cifras de chave simétrica contínuas.

Exemplos canónicos:
  * AES é, por construção, uma cifra por blocos!
      * AES-CBC;
      * AES-ECB; 
  * DES.

#### Cifras de Chave Pública

Cifras de chave pública são cifras que usam **chaves diferentes para cifrar e para decifrar**.

Atuam por blocos.

:::info
**Definição Matemática**
Uma cifra de chave pública é definida para **três** conjuntos:
  * o conjunto de chaves de cifra $\mathcal{K}$;
  * o conjunto de textos-limpos $\mathcal{M}$;
  * c conjunto de criptogramas $\mathcal{C}$;
por **três** algoritmos (um para gerar chaves, um para cifrar, outro para decifrar):
  * Algoritmo para gerar chaves $(p_k,s_k)=G(s)$;
  * Algoritmo para cifrar $c=E(p_k,m): \mathcal{K},\mathcal{M}\rightarrow\mathcal{C}$;
  * Algoritmo para decifrar $m=D(s_k,c): \mathcal{K},\mathcal{C}\rightarrow\mathcal{M}$.
:::


Exemplos canónicos:
   * RSA (vamos dar);
   * ElGamal (vamos dar);
   * ElGamal em curvas elípticas (mestrado).










