## Encryption
Resumindo de maneira simplista, encriptação é a área sa criptografia que se preocupa em tornar um dado legível em ilegível e então torná-lo legível novamente. Perceba que diferente do hash, é uma função de mão dupla.

Texto pleno é.... o texto pleno né.. no caso o dado que você precisa encriptar. 
Texto cifrado é.... o dado que por si só não apresenta sentido ou padrão algum. É a versão encriptada do texto pleno.
Encriptação é.... o processo de transformar um texto pleno em um texto cifrado.
Decriptação é.... o processo reverso da encriptação transformando um texto cifrado em um texto pleno.

Essa ciência é bastante antiga, vamos ver os principais motivos de sua valorização e alguns métodos comuns para encriptação.

Comunicação mais segura entre duas partes = tráfego web com certificados SSL/Telegram.

Dica de projeto open source = https://www.projectcallisto.org/

A criptografia pode se realizar de modo simétrico ou assimétrico.
No modo simétrico, o texto pleno é codificado e decodificado utilizando-se da mesma chave. Isso significa que todo mundo da roda que precisa do dado precisará de acesso a chave, e em caso de perda é problema na certa.
No modo assimétrico, todo mundo da roda possui duas chaves, uma é pública e a outra é privada. Assim o envio do texto cifrado é feito utilizando-se da chave pública do destinatário que poderá decriptografar o conteúdo com sua chave privada. 

Embora a popularidade do método simétrico de encriptação venha diminuindo, algoritmos populares como AES, IDEA, Blowfish usam.

Mas isso não significa que o método assimétrico ou que as chaves públicas são impenetráveis. Mas com toda certeza irá ser mais difícil e inviável. Tecnologias como SSL e o SSH são uma combinação de chaves pública e privada.

Mantenha as chaves atualizadas e armazenadas em um lugar seguro! Mas onde?
