=====CAPTURANDO UM ARQUIVO VIA SCP===
#scp msfadmin@192.168.122.43:/home/msfadmin/.ssh/authorized_keys /home/aluno

Ex: Também é possível copiar do host A para o host B diretamente, ou utilizando seu host
como intermediário
#scp -3 msfadmin@192.168.122.43:/etc/passwd aluno@192.168.80.43:/etc/passwd
