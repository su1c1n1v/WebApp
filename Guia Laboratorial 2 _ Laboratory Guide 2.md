Guia Laboratorial 2 | _Laboratory Guide 2_
===

###### tags: `Segurança Informática`, `Guia 2`

:::info
- **Local:** _Online_
- **Sumário**  
- **Link:** [Hackmd.io](https://hackmd.io/zN0xqlipTPSuA964-VLdYA?view)
- **Autores:** Pedro R. M. Inácio [(inacio@di.ubi.pt)](mailto:inacio@di.ubi.pt)
- **Edição/Revisão:** xxx.
:::

O _OpenSSL_ é a implementação em linguagem `C`, gratuita e código aberto, dos algoritmos criptográficos usados nos protocolos _Transport Layer Security_ (TLS) e _Secure Sockets Connection_ (SSL).

O _OpenSSL_ tinha um mega _bug_ que ía acabando com a Internet chamado _Heartbleed_!

**Q3.:** `man openssl`

**Q4.:** 
  * _OpenSSL_ é a implementação em C dos algoritmos ... (uma biblioteca de código, portanto)
  * `openssl` é uma ferramenta da linha de comandos, que pode vir com a instalação da biblioteca, e que nos deixa usar as funções na biblioteca logo na linha de comandos.

```
 1  0  1  1  1  0
32 16  8  4  2  1 = 46 

          2           E
 0  0  1  0  1  1  1  1 
      32 16  8  4  2  1 = 47
 
 1  1  0  0  0  0
32 16  8  4  2  1 = 48

 1  0  1  1  1  1
32 16  8  4  2  1 = 47

101110 = 46

            3           0
   0  0  1  1  0  0  0  0
128  64 32 16  8  4  2  1 = 48

   1 2 0 1
  27 9 3 1 = 27 + 2*9 + 1 = 46

   1 2 1 0 
  27 9 3 1 = 27*1 + 9*2 + 3*1 = 48
```

Rivest Cipher 4 (RC4)