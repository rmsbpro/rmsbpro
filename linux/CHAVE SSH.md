===ssh===
Ex: Se usuário iniciou uma sessão SSH a partir de um host
comprometido, onde havia um keylogger funcionando, a
senha será comprometida.


===ssh-keygen=== 
obs: dê tudo enter, vc cria ela básica, mas vc pode atribuir um nome para ela
e colocar uma frase senha.


====VERIFICANDO EXIXTÊNCIA DE CHAVES:
Primeiro verifique se você não possui nenhuma chave gerada, para isso de uma olhada na pasta ".ssh" 
que fica dentro do diretório "/home/seuusuário", você também pode usar o comando "#ls ~/.ssh". 
Caso não exista nenhum arquivo chamado "id_rsa" e "id_rsa.pub" significa que não existem chaves geradas para o seu usuário.

====GERANDO CHAVES=====

#ssh-keygen -t rsa -b 2048

Onde ssh-keygen é o comando de geração de chaves de fato e -t especifica o tipo de chave que estamos gerando, 
nesse caso o tipo é RSA, -b é força dessa chave em bits, aqui pode-se estipular um valor de até 4096 bits.

>>>PASSO 1 – O diretório/arquivo que deseja salvar a chave | Deixe o padrão "/home/seunome/.ssh/id_rsa", basta apertar enter

>>>PASSO 2- O passphrase | Seria como se fosse uma senha para a chave, se você  usar um passphrase deverá digitá-lo toda vez que for se conectar. 
Existem formas de deixar esse passphrase salvo mas você pode deixar em  branco que já será mais seguro que usar apenas a sua senha. 
Apenas  aperte enter para deixar em branco

>>>PASSO 3- Repetir o passphase | se deixou em branco apenas apenas aperte enter novamente.



===COPIANDO CHAVE PUBLICA PARA OUTRA MÁQUINA===
OBS: Dentro da pasta pessoal de cada usuário existe a pasta oculta com as chaves SSH
aluno@alunomac:~/.ssh$ ssh-copy-id -i id_rsa.pub msfadmin@192.168.122.43
obs: ela irá pra dentro do arquivo authorized_keys dá 
máquina destino da cópia

OBS: só irá pedir a senha no próximo login, depois irá sem senha, 
caso ainda estaja pedindo a senha apague as pastas .ssh dos dois usuários, 
crie a chave novamente e faça a transferência.
