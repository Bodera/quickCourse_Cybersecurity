## Sensitive data
Então, nós possuímos toneladas de opções quando se trata de aplicar hashing em nossos dados. Desde hashes rápidos e que são fáceis de quebrar até as hashes que sobrecarregam processadores e as restrições de memória.  

Mas, às vezes, precisamos ser capazes de recuperar os dados de seu estado codificado de forma segura. Então, vamos repassar brevemente a criptografia de chave privada e de chave pública novamente.  

## Criptografia de chaves privada e pública
Nas criptografias de chave privada ou simétricas, a codificação e decodificação da mensagem é feita utilizando a mesma chave.  

Se a chave for violada, todas as comunicações estarão agora disponíveis para olhos não autorizados.  

Apesar disso ela ainda tem seus usos, desde que você esteja bloqueando algo apenas para si mesmo.  
___

Para criptografias de chave pública ou assimétricas, a codificação e decodificação da mensagem é feita utilizandos duas chaves separadamente.

A codificação é feita usando a chave pública e a decodificação por sua vez é feita utilizando a chave privada.

Isso permite que você dê a outras pessoas sua chave pública.

Elas podem codificar as mensagens que irão lhe enviar usando sua chave pública, e então você, e somente você, pode decoficar o conteúdo usando sua chave privada.

Atualmente nós combinamos as duas técnicas in tecnologias como oa protocolos de Segurança na Camada de Transporte e Camada de Soquete Seguro. Ou como você deve estar mais familiarizado com eles, TLS e SSL.  
Nessa configuração, o seu cliente, geralmente um navegador web, gera em um servidor um segredo compartilhado, o que chamamos de autenticação mútua, que eles usão para codificar e decodificar todo o tráfego entre eles. Confira mais nos hyperlinks que seguem...  
* [Mutual authentication](https://www.youtube.com/watch?v=VZj4CZkrkcc)
* [Shared secrety](https://www.youtube.com/watch?v=Abi8f9SaijM)

Além disso, o servidor também fornece uma chave pública que é usada para autenticar sua identidade para o cliente e para verificar onde cada conjunto de dados foi originado.

TLS e SSL são usados para fornecer a segurança em conexões HTTPS.

Verifique o URL acima e você deverá ver algum tipo de cadeado ou indicador de que você estpa usando uma conexão HTTPS segura.

Vamos agora explorar um exemplo prático de utilização de chave pública com a ferramente open source gnuPG ou GPG.

## Aplicação
Eu já tenho a ferramenta instalada na minha máquina, mas se você estiver curioso sobre o `gpg`, segue o link com o manual e notas de instalação para sistemas Linux baseados no S.O. Debian para você explorar:  
* [MiniHowTo](https://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html)

```bash
$ sudo apt update  
$ sudo apt-get install gnupg
$ gpg --full-gen-key
```  
Então você pode estudar as diferentes opções na hora de encriptar um arquivo binário usando o GnuPG. Um ilustração do comando para encriptar um documento a seguir.  

```bash
$ gpg --armor --sign --encrypt [Data]
```
Um exemplo do novo texto cifrado que nós geramos deve ser caracterizado com o formato de arquivo *_asc_* se parece com o seguinte:  
```
-----BEGIN PGP MESSAGE-----

hQGMA/O0YvUKloa5AQv9Fm6E/tuh6Y82k0s9gKcZvnOiwxYSEf8refiuYNj1cUI5
PbQwPulnfw7c0h0GaoEP+4KO7MKIW9esUq049zWruux
KuFzy0IRiEzv3/SccFisP+ifXqEMDiYiDPpIo1j+uJPzVLnujHJkCf/l2LQhyZ74
0GCMUGfpTOg3GmK6A2y8VKbRuaydV+Ge88d8+ciRhRtBopDiBySQ2m2bVxEBWsYR
zUcRp9lyTEIR1zSfwe44PRIeyfOO2gEto6KC3sssy4ARZ5bcXNfEhivX0+td3TdV
Fj6E1py/USl/UbmR0htHSQ5vlcPfdzYwWaDWe/dryRYUP7YeZkuA5lYfVJE8CGgb
s2+ZovDX1POj9u+X2Um8FMCrYzlXYtBDQMkWbWu7FDRfFeWBEi8doNaJhPqM7Paw
A3N7OqdYvUT72wqygtrb4OCPre7xsxUKmrUJQBaGQIK2uCi6TSyE/7QF9EE31cVl
c1PlwrGNh0rv8Bs39AtGTd2MqTn5iapIX5VIx8lDFSy9LB/NVHiB/ZkHHTNsfnln
54VADVxbJR/UXz9xzoyeMN4I8pnL8XzKhQyXIssiC7q9szyy/EEJFMsN3Xv0oVKz
7sv2mSwejtkh6s9gKenpm/lS+qfGkP2loyKTpe65ow==
=g6Uo
-----END PGP MESSAGE-----
```  

Você irá notar que a saída é bem maior que isso, mas o intuito aqui é ser ilustrativo para que você quebre a inércia e descubra as aplicações da segurança de dados no mercado de trabalho.

Tá. Mas e como você faz para ler o arquivo em texto pleno?

Abra o terminal e na mesma pasta que contém o arquivo encriptado execute o comando:  
```bash
$ gpg [Data]
```

Você será instruído a fornecer a palavra-passe para a sua assinatura. A propósito usando o mesmo comando que vimos anteriormente substituindo o `gpg` por `gpg2` funciona perfeitamente. Descubra o por quê.

A saída do terminal lhe diz seu nome de usuário, o algoritmo mais o ID da sua chave privada e o seu endereço de e-mail. Uma assinatura foi criada aqui.

Poderíamos ter recebido essa mensagem por um cabo coaxial ou pela internet. E podemos fazer tudo o que for necessário com esses dados agora, tanto a versão encriptada quanto a descriptografada.

Podemos subir essas informações em um banco de dados hospedado na nuvem, ou em algum outro servidor. Ou ainda transferi-lo para algum outro serviço ou enviá-lo para outra pessoa.

Muito provavelmente, eu receberia isso como um e-mail, que é onde o GPG realmente se destaca. Confira mais sobre clicando [aqui](https://www.dewinter.com/gnupg_howto/english/GPGMiniHowto-6.html#ss6.2) e depois [aqui](https://www.openpgp.org/software/).  

Há obviamente muito mais envolvida na criptografia.

Especialmente no que tange [o sigilo mundial](https://en.wikipedia.org/wiki/Forward_secrecy) que garante que o acesso a uma chave não implica no acesso às mensagens anteriores.

Configurar seu servidor Apache ou NGINX para usar o SSL também está fora do escopo deste curso.

## Finalização

Você agora está armado com conhecimento sobre hashing e criptografia de dados, mas será que precisa fazer tudo isso por conta própria?

Vamos dar uma olhada em lugares onde é mais inteligente descarregar esse trabalho para terceiros.