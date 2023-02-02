
						



@@@@@@@@@@@@@ AULA 1 @@@@@@@@@@@@@

WINDOWS

buscar na ávore por arquivos q contanham as expressões

dir /s /a /b *pass*==*cred*==*vnc*==*unatt*==*.config*
lista até os ocultos

criar / deletar pasta

md    cria

rd 	deleta

rd /s /q apaga as subpastas e não pede permissão

xcopy /e copia todos os arquivos e diretórios
xcopy /s copia todos os arquivos e diretorios exceto os vazios
xcopy "aula 1 windowns.txt" Documents\
xcopy /F "aula 1 windowns.txt" aula.txt



type ====lista o conteudo do arquivo

ren ==== renoemeia o arquivo

move

fc ==== compara e mostra diferença entre dois arquivos
fc "aula 1 windowns.txt" aula.txt

whoami   mostra o nome do usuario e dominio atual

tree /f === lista a arvore de diretorios com os arquivos

runas /user:desktop-096icii\ruan "cmd.exe /c echo 1 > 1.txt"
executa um comando como outro usuário, porém precisa de confirmação de senha, 
pois não passa por parâmetro, se executar de um terimal sem interatividade, irá perder o terminal. 

===LENDO ARQUIVOS
type "aula 1 windowns.txt" | sort > aula.txt
lê o conteudo, ordena e sobrescreve a saída no arquivo escolhido
type "aula 1 windowns.txt" | sort >> aula.txt
lê o conteudo, ordena e acrescenta a saída no arquivo escolhido

OBS: attrib +R +S +H +A e outros, atribuir o +S deixa o arquivo oculto e como de sistema, 
que não pode ser deletado de forma fácil

senha=1234
password=4321

=====buscar expressão em arquivos
findstr /spin /c:"password" /c:"senha" *.* 2>null

systeminfo, permite ver quais hotfix estão instalados e caso um mais atual estaja faltando 
já pode ser fonte de um exploit 

taskkill - mata processo, muito usado para matar processo q está travando porta que estava sendo explorada
e o terminal foi perdido,  /o descobre qual a porta está sendo usada

powercat.ps1 === usado para shell reverso

schstack === agendador de tarefas do windows, pode agendar execução de scripts maliciosos durante a inicialização ou
de tempos em tempos usado para cria persistencia, shell reverso, terminal sempre será executado em background, já um bat
 pode aparecer a execução para o usuário, pode ser um .bat q chama o terminal e já executa alguns comandos nesse terminal
, ocorrerá em background

vc pode criar uma tarefa que execute um bat que vai baixar da máquina atacante ou mandar o shell acada minuto
pode criar uma tarefa para manter percistência como "system" é o maior previlégio do windows, uma maneira de 
fazer isso é chamar o powercat.ps1 da máquina atacante para a alvo


@@@@@@@@@@@@@@@@@ AULA 2 @@@@@@@@@@@@@@@@@

executar alguma tarefa com o "runas" usanso algum usuario q nunca logou na máquina 
o arquivo "profile" vai estar vazio, logo as execuções ocorreram em background

====ESCALAR PRIVILÉGIOS====

Se encontrarmos uma tarefa agendada executando algum programa que eu tenho permissão
para editar, posso tentar modificar o programa que está sendo executado, para tentar executar um
programa malicioso (Escalar privilegio).
* Podemos utilizar o comando de criar uma tarefa agendada para tentar um ataque de força
bruta em algum usuário da máquina (Escalar privilegio).

para desabilitar em antivirus
tentar renomear os arquivos (de .exe para .rar, por exemplo) do antivírus na pasta em
"Arquivos de programas".
======================

verificar programas rodando "sc query", "sc qc NOME_DO_SERVIÇO" e variantes:
o objetivo é verifiar onde estão localizados os executáveis dos serviços, 
quem executa "ex: SYSTEM" e quando executa "ex: AUTO_START", são possibilidades 
para estabelecer persistência, podendo substituir algum ou criando uma nova tarefa 
com "sc create".
EXEMPLO:
sc create "nome_do_serviço" binPath= "caminho_do_executável" DisplayName=
"descrição_do_serviço" obj= "usuário_que_executará" password= "senha_do_usuário": Criar
um novo serviço.

obj=.\LocalSystem , usado para escalar previlégio e persistir algum backdoor 

• Se encontrarmos um serviço com permissão de edição, podemos modificar o caminho
do executável que o serviço executa, forçando ele a executar um programa malicioso
(Escalar privilégio)

• Se encontrarmos um programa que está sendo executado por um serviço e que meu
usuário tenha permissão para substituir esse programa, posso colocar um programa
malicioso nesse path. (Escalar privilegio).

BIZU: no windows o arquivo profile dos usuárioa armazenam muitas senhas.

==============REUSO DE SENHA:
OBTER SENHA DE ALGUM WIFI
"netsh wlan show profiles"
netsh wlan show profiles name="nome_da_rede" key=clear
pode ser que esse usuário reutilize essa senha em outros sistemas, é uma opção

==========LOCAIS DO WINDOWS Q ARMAZENAM SENHAS:
As principais chaves do registro ficam salvas no diretório "C:\Windows\System32\config".
DEFAUT
SAM
SECURITY
SOFTWARE
SYSTEM
é interessante navegar até os ultimos diretorios para achar o valor, esses arquivos
só consegue ser lidos pelo editor de registro do windows
BIZU: Através do registro do Windows, é possível mudar o comportamento padrão de
alguns programas do Sistema Operacional, assim como é possível conseguir algumas
informações importantes, como versão de programas, senhas, etc.

======= UTILIDADES DO REGISTRO========
+++EXEMPLO 1++++
reg query HKLM /f password /t REG_SZ /s: Comando para buscar pela string "password" dentro
da chave HKLM.

+++EXEMPLO 2+++
CASO NA MÁQUINA ALVO POSSUA O PUTTY INSTALADO ACHO OS IPS ACESSADOS, POTENCIAIS ALVOS:
reg query "HKCU\Software\SimonTatham\PuTTY: Comando para ver detalhes de conexões
realizadas com o programa putty.
+++EXEMPLO 3+++
CAUSAR FALHA EM UM SOFTWARE, DESABILITAR DEFENDER VIA REGISTRO
reg add "HKLM\software\policies\microsoft\windows defender" /v Disableantispyware /t
reg_DWORD /D 1 /F: Comando para desabilitar o Windows defender, utilizando chaves
de registro.

+++EXEMPLO 4+++
CASO QUEIRA COPIAR OS REGISTROS PARA ANALISE POSTERIOR
reg save chave\subchave\subchave arquivo_de_saida: Copiar chaves de registro para um
arquivo (com extensão .hiv).

+++EXEMPLO 5+++
=======HABILITAR  via registro
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server"
/v fDenyTSConnections /t REG_DWORD /d 0 /f



