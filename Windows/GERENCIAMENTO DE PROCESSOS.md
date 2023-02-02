GERENCIAMENTO DE PROCESSOS

Processo corresponde a uma instância de uma aplicação que está sendo executada no sistema operacional.

>tasklist ⇒  Lista os processos ativos, nomes, PID... ,semelhante ao ps aux no Lnx
	>tasklist /M ⇒  lista as DLL que cada processo usa
	>tasklist /SVC ⇒ lista os serviços relacionados com esse processo
	>tasklist /V ⇒  Mostra qual usuário está utilizando determinado processo

>taskkill /pid xxxx ⇒ Mata determinado processo ativo (Ex: taskkill /pid 3395).
	>taskkill /fi "xxx" ⇒  mata todos os processos que satisfazem determinada condição
	Ex: >taskkill /fi "pid ge 1000"

CTR-C não é interessante executar na máquina que está invadindo, pq pode manter o processo ativo, e vai impedir de acessar novamente aquela máquina , deve então executar o  -ano (ver quais portas estão sendo usada e matar aquela porta do shellreverso e acessar novamente)

systeminfo (Hotfix o que tá instalado importante)

drverquery (usado p verificar vulnerabilidades divulgadas)
