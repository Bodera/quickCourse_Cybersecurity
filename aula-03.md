# Video 3

2 maneiras populares de obscuring e protecting data. Hashing e Encryption.

Uma forma de que manter os dados armazenados com segurança é fazê-los tornarem-se incompreenssíveis e irreparáveis. (unreadable and unrecoverable)

Hashing é usado em diferentes aplicações: checksums para validação de dados e outros arquivos, compressão de arquivos e autenticação de mensagens, e codificar dados de forma confiável. 

Para a última, utilizamos uma função de hash e usando um ou mais algoritmos transforma os dados em uma hash. 

Todo vez vai ser o mesmo hash se e somente se forem os mesmos dados na mesma função de hash. É uma função de mão única.

Ah essa é uma operação irreversível. Uma vez que se transforma em hash os dados não poderão ser recuperados. E isso é ótimo, não queremos ler os dados apenas queremos verificar a integridade.

Senhas: No ato de cadastro a string passa por uma função de hash onde daí o resultado é armazenado no banco de dados. No ato de login, a mesma senha passa pela função e os valores são comparados (o hash de input e o hash armazenado no banco de dados).

Para evitar confusões como por exemplo, mesma senha e um usuário entra na conta do outro, existe uma característica nos bons algoritmos de hashing, conhecida como salt. 

O salt é um dado único gerado aleatoriamente. Tal qual o Unix timestamp que usamos no log para sabermos quando foi feito o cadastro ou login/logout. E é adicionado na saída da função de hash, então o hash e o salt são armazenados e para validar a senha comparamos o input do usuário adicionado ao salt e checamos com o que possuímos no banco de dados.

Uma colisão é uma brecha de segurança na qual diferentes valores de entrada geram o mesmo hash para uma única função de hash. MD5 é uma função de hash hoje considerado inseguro, o SHA1 também está comprometido. Algoritmos mais seguros são o SHAKE e o Argon2. 
