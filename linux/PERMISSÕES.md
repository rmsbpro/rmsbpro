

Níveis de acesso
As permissões dos arquivos no Linux são definidas por quatro dígitos que representam:
1. permissões especiais;
2. permissões da pessoa que criou o arquivo ou o diretório (dono ou user);
3. permissões dos usuários membros do mesmo grupo do dono do arquivo ou do diretório (grupo ou group);
4. permissões do resto dos usuários do sistema (outros ou others).



Permissões comuns
As permissões comuns para o dono, o grupo e os outros são de 3 tipos:
1. leitura (r) – permite ler o conteúdo de um arquivo/diretório.
2. escrita (w) – permite alterar um arquivo/diretório.
3. execução (x) – permite executar um arquivo ou acessar um diretório e executar comandos.




EXEMPLO:
suponha que a resposta ao comando "ls -l teste" seja a seguinte:
-rw-rw-r−− 1 aluno curso 1024 Fev 13 10:55 teste
10 caracteres onde:
"-"(tipo objeto) = arquivo comum
"rw-"(dono)= leitura e escrita
"rw-"(grupo)= leitura e escrita
"r--"(outros)= leitura



• O primeiro caractere diz qual é o tipo do objeto:◇
•  – para arquivo comum;
◇ b para dispositivos de bloco (oferecem grandes quantidades de dados de cada vez).
◇ c para dispositivo de caracteres (oferecem dados de um caractere de cada vez);
◇ d para diretório;
◇ l para link simbólico;
◇ p para FIFO ou Named Pipe;
◇ s para socket mapeado em arquivo;


Permissões especiais
Para executar um processo, o Linux usa as permissões do usuário que o iniciou. Isso significa que os privilégios do usuário se aplicam a todas as ações do processo. O problema é que somente o root pode fazer tudo no sistema e um usuário pode, por exemplo, não ter permissão para usar um navegador da Internet.

• SUID – com esta permissão, o usuário executa o arquivo como se fosse o dono (não funciona em diretório). Isto significa que será usado o UID do dono do arquivo ao invés do UID do usuário que executa o programa.
• SGID – com esta permissão, o usuário executa o arquivo ou acessa o diretório como membro do grupo ao qual pertence o arquivo/diretório. Isto significa que o usuário assume o GID do grupo (ele é membro desse grupo, mas é outro o seu grupo padrão).
• sticky bit – o usuário pode criar/alterar/deletar (apenas) os seus próprios arquivos no diretório que possui esta permissão, mesmo que não seja o dono do diretório e nem membro do grupo ao qual o diretório pertence. Quando o sticky bit é usado em um arquivo, significa que este arquivo é compartilhado por vários usuários.



EXEMPLO:
suponha que a resposta ao comando "ls -l teste" seja a seguinte:
-rwSrwSr−− 1 aluno curso 1024 Fev 13 10:55 teste


A string "-rwSrwSr−−" indica que:
• é um arquivo comum (primeiro "-");
• "rwS" define permissão de leitura, escrita e SUID (quem executar o programa usará a UID(PERMISSÃO) do aluno);
• "rwS" define permissão de leitura, escrita e SGID (quem executar o programa usará a GID do curso);
• "r−−" define permissão de leitura para os outros.

UID é pemissão pra proprietário se ganha alguma especial vira SUID  equivale a 4
GID é permissão pra grupo se ganha alguma especial nele vira SGID equivale a 2
logo 4 +2 = 6 permissão especial, corresponde ao primeiro número, o restante é proprietário, grupo e outros
Para esse exemplo, é possível dizer que o arquivo teste tem permissão 6664.

SIGNIFICADO DAS LETRAS



ONDE ESTÃO  AS PERMISSÕES ESPECIAIS

São exemplos do uso das permissões especiais no Linux:
• O comando ping precisa de permissões de root (um soquete de rede precisa ser aberto para a transmissão de pacotes ICMP). Neste caso, é usada a permissão SUID e o comando tem permissões 4755.

-rwsr-xr-x 1 root root 44168 Mai 7 2014 /bin/ping
◇ A ferramenta crontab usa SGID para permitir que os usuários agendem tarefas. As permissões usadas são 2755.

-rwxr-sr-x 1 root crontab 35984 Fev 9 2013 /usr/bin/crontab
◇ O diretório /tmp tem permissão sticky bit (todos os usuário do sistema podem criar, ler, alterar e deletar arquivos desde que sejam os donos).

drwxrwxrwt 8 root root 4096 Fev 13 11:40 tmp
De acordo com o que já foi discutido, as permissões do diretório /tmp são 1777.
