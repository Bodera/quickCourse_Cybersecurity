# Video 5
Nós cobrimos bastante teoria até aqui e ambientes que exigem atenção dobrada. Então devemos começar a analisar algumas soluções ou abordagens para melhorar a segurança. Perceberá se for astuto, a razão de trabalharmos em cima de aspas simples ao redor das string apresentadas nos exemplos.   

```
Antes quero deixar claro que você deve buscar fazer o uso de medidas, ferramentas, bibliotecas e serviçs que já existam a bastante tempo e, portanto, reconhecidos e geralmente aceitos. 
Pode ser divertido brincar com algoritmos próprios ou técnicas de segurança. Mas essas atitudes, especialmente quando são mantidas em segredo e internamente, são casualmente muito mais vulneráveis do que os padrões atuais da indústria. 
Nosso objetivo é estar o mais seguro e protegido possível. Então por favor atenha-se às ferramentas recomendadas pela indústria, beleza?
```
  
Perfeito, então vamos começar com uma das coisas que praticamente quase todos os sistemas de segurança possuem: __senhas__. 
Precisamos aplicar um hash nessas senhas porque apesar dos nossos melhores avisos, os usuários irão aparecer com 1 senha decente e a usarão site após site, aplicação após aplicação.
E então quando o pontodepescadoaroldo.com for hackeado, logo os invasores porderão direcionar o seu site ou o meu site e esperar por sobreposições de senhas.   

Entretando, nós não queremos fornecer à hackers com seu novo suprimento de senhas e detalhes de contas. Logo aplicamos um hash em todas as senhas que temos armazenadas.  

Outro adendo, a linguagem de programação usada nos exemplos são meramente por razões de ilustração. Tudo que está sendo feito em Python ou JavaScript ou qualquer que seja a linguagem, pode ser feito na sua linguagem favorita ou no framework da sua escolha. Seja criativo e não use exatamente a mesma linguagem e o mesmo código apresentados aqui. VAMOS COMEÇAR!   

O Python possui uma ferramenta interna bem útil chamada [hashlib](https://docs.python.org/3/library/hashlib.html). Ela será utilizada para explorarmos alguns algoritmos de hashing. E então iremos observar como aplicar o salt nas nossas hashes e, finalmente, iremos olhar o algoritmo Argon2, ganhador do campeonato de hashing em 2015. Algoritmos de hashing aparecem em diversos formatos e tamanhos aliás, então tenha certeza de que encontrou o que melhor se adequa a sua necessidade.  

Okay, primeiro vamos olhar um algortimo ruim para se usar, o MD5.  

Hashes retornam um monte de bytes, dos quais nós podemos vê-los como bytes retos, ou se preferirmos podemos convertê-los para hexadecimal.   
Hexadecimal é a forma mais provável que você irá utilizar para armazenar o hash em um banco de dados, logo esse será nosso foco. Mas as duas formas serão apresentadas nos primeiros exemplos.  

```python
#First example of hash in python 3.6 environment, using the bad algorithm MD5.
#import the necessary library
import hashlib
#call method which applies md5, and for that we must send bytes for the word Treehouse.
#o método digest() apresenta os bytes de saída do algoritmo.
hashlib.md5(b'Treehouse').digest()
 >>> b'ei-fzW3asz023=xb9\x62\x86\x21\x5B\'
#I've almost hit the keyboard with my face two times. But it's important have an idea about how the MD5 output looks like.
hashlib.md5(b'Treehouse').hexdigest()
 >>> b'29462d66c666cs66de67263uf233suf894v4'
```   

Não tem muito o que dizer, mas se vocÊ testar perceberá que a saída é apresentada com velocidade. Eficiência é outra das coisas pelas quais o MD5 é reconhecido. Vamos mudar de algoritmo agora, vamos tentar o SHA256.  

```python
#First example of hash in python 3.6 environment, using the bad algorithm MD5.
#import the necessary library
import hashlib
#call method which applies sha256, and for that we must send bytes for the word Treehouse.
#o método digest() apresenta os bytes de saída do algoritmo.
hashlib.sha256(b'Treehouse').digest()
 >>> b'0\x1b}\xd8\xba\x80\xd1\x99r\xba\xba\xba\xcci\xbae2\x33\xba<::21\xxx2\xccn\x29\abs\xoa\xpl\xvx\xba\xff\xba\xba\xba\xba\xba\xz?a\xba\xbr5\x21'
#I've almost hit the keyboard with my face four times. But it's important have an idea about how the SHA256 output looks like.
hashlib.sha256(b'Treehouse').hexdigest()
 >>> '33b13d6b444ec9ad0ee9382e5125573995b2cf0eefa15ac23cbb12aef9d168da'
```   
É possível notar a diferença no tamanho da string, a saída do algoritmo é maior. O SHA256 foi por um bom tempo considerado um algoritmo forte, mas atualmente está comprometido devido a colisões que podem ocorrer em um período de tempo razoável. É até onde a segurança vai.   

Vamos então finalmente ver um algoritmo seguro altualmente. Esse aqui também é da família SHA ou s-h-a, e foi desenvolvida na NITH (National Institure of Standarts and Technology). A string de saída desse algoritmo é um pouco diferente apesar de aprensentá-la em uma quantidade variável.
Nós podemos controlar a quantidade de segurança que vai ao criar a hash e a quantidade de dados do hash que sai. Veja como fica nosso código agora:  
```python
import hashlib
#Use o shake-128 usando a mesma palavra-chave em uma string contendo 20 caracteres.
hashlib.shake_128(b'Treehouse').hexdigest(20)
#A string original possui 32 caracteres.
 >>> 'cdaa98b8ba3b48a82791'
```   

Agora, indenpendente da ferramenta de hash que você vai usar, é de extrema importância que você aplique *salt* em suas hashes.  
O resultado? Bom ele traz alguns dados extras aleatórios para o seu trabalho de hash na `COISA` que você escolheu para aplicar o salt. 
Pense qual a maneira de escolher o melhor dado o qual você submeterá ao salt, algumas pessoas usam o time_stamp do momento em que você se cadastrou, outros usam o nome de usuário, ou alguma outra coisinha de dados conhecidos.  

No próximo exemplo, eu decidi usar uma string gerada aleatoriamente da biblioteca (UUID)[https://docs.python.org/3/library/uuid.html] do Python.  

```python
#Não tem como errar, Universally Unique IDentifier, dá um google.
from uuid import uuid4
#vamos criar a variável que armazenará a nossa senha.
password = 'Treehouse'
#criar um uuid e armazená-lo na nossa variável salt.
salt = uuid4.hex()
#e então aplicamos o shake-128 nessas duas variáveis.
#especificamente em uma string de 40 caracteres.
hashlib.shake_128(str.encode(salt+password)).hexdigest(40)
#superei a vontade de acertar o teclado, tá ficando legal.
 >>> 'ab1565f4964dd4abef602853e90eb06a76b52b46'
#essa string é um bom dado para se armazenar. Mas como você sabe o que é a senha e o que é o salt?
#para verificar a validade da hash você precisa saber disso.
#a lógica é anexar o salt ao final do hash.
hashlib.shake_128(str.encode(salt+password)).hexdigest(40) + ":" + salt
 >>> 'ab1565f4964dd4abef602853e90eb06a76b52b46:fe5de92f793b5'
#então para decodificar, fazemos o processo inverso
#e ':' não está incluído na codificação hexadecimal. Deduzimos que ele não pertence ao hash da senha, e nem sequer ao salt.
 '''
 então pegamos o que está depois do ':', somamos à senha que o usuário nos forneceu,
 fazemos o hash em tudo isso com o shake_128, e então comparamos essas duas strings e
 verificamos se as duas conferem.
 '''
```   

Muito legal né? Mas não parece que estamos tornando mais fácil quebrar a hash ao incluí-la em texto pleno ao fim da string?  
Verdade, a utilização de salt impõe um obstáculo muito maior quando lidamos com ataques pré-computados como por exemplo, lists of prehashed words ou também phrases against your hashes.   
Você deve __sempre__ aplicar o salt em suas hashes. Se você se preocupa também com a possibilidade de invasores estarem aptos a ver seu salt, você pode sempre usar outro punhado de dados que são calculáveis como a data de cadastro, onde o email do usuário é o salt original.   

Antes de acabar essa aula, quero dar uma olhada no Argon2, vencedor do último campeonato de hashing de senhas. O que esse algoritmo faz, vários outros algoritmos focados em hashing também são capazes de fazer. Vou fazer aqui, e te mostrar do que se trata.  

```python
#primeiramente vamos importar o módulo PasswordHasher da biblioteca argon2.
from argon2 import PasswordHasher
#uma variável chamada 'ph' vai receber o método.
ph = PasswordHasher()
#e esse método pode chamar outros, o .hash() espera receber uma string, note as aspas duplas.
ph.hash("Treehouse")
 >>> '$argon2i$v=19$m=1024,t=1,p=1$c29tZXNhbHQ$KRgCgTANwEjnGr4D5eiDUTtCEigBjE80DmYo8v+mi3c'
 """
 perceba o encode de saída, note a utilização do algoritmo '$argon2i', 
 e os outros dólares também falam mais sobre como o hash foi gerado, o hash por sinal
 está após o último dólar, após o '$c'.
 """ 
```   
Talvez você pense que essa abordagem não é tão segura, visto que uma tag seria capaz de simular suas configurações de hashing.  
Mas do jeito que as coisas funcionam no Argon2, onde os trabalhos de estresse e preenchimento de memória são os de maior importância, e os valores de '$v' '$m' 't' e 'p' podem ser ajustados por você para determinar o quanto de memória e tempo de processador nossas hash usam.  

Isso traz um benefício maior, porque quando você armazenar a palavra-passe do usuário em seu banco de dados, você saberá COMO identificar os pedaços dela. E você poderá usar isso da próxima vez e fazer uso disso para evoluir suas hashes no futuro, o Argon2 também é bem inteligente.  

Então é isso, lembre-se de usar o mecanismo de hash para proteger the infotax from GP use, usar a quantidade de tempo e memória na geração de hash contra o invasor e evitar colisões. Também é uma boa ideia ter a certeza e ficar acompanhando a reputação do algoritmo que você usa para hashing, daí você pode evoluir as hashes armazenadas como um preço, e então trocar de algoritmo.  

E eu não tô cansado de falar, sistemas como o Argon2 são ótimos para se usar em casos específicos como senhas. Em outras situações em que hashing será necessário, não dificilmente será fácil localizar ferramentas que já existem, próprias e especializadas para a situação em questão. Me refiro a coisas como checar o conteúdo de um arquivo, validar a origem de uma mensagem, ou scanear a biometria de um usuário, ou a impressão digital do dispositivo já possuem soluções existentes que você deveria investigar.  

Pronto, agora nós temos coisas armazenadas com segurança e em um formato ilegível, você tem ideia como você faz para pegá-las de volta?

###### Futher links to automate boring job
(Online hash tools)[https://emn178.github.io/online-tools/]  
(Gerador de senha)[https://dudz.com.br/GeradorSenhas/]  
(Convert case)[https://convertcase.net/pt/]  

##### And the special ones
Google for salt:
https://auth0.com/blog/adding-salt-to-hashing-a-better-way-to-store-passwords/  
https://en.wikipedia.org/wiki/Salt_(cryptography)  
https://www.youtube.com/watch?v=vTz5tk8_BxM  
https://www.youtube.com/watch?v=--tnZMuoK3E  
https://crackstation.net/hashing-security.htm
https://www.schneier.com/blog/archives/2012/10/when_will_we_se.html
ATENÇÂO CUIDADO COM HTTP: http://antelle.net/argon2-browser/

Google for machine fingerprint:
:sheep:
