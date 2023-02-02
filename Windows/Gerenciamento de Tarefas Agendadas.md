Gerenciamento de Tarefas Agendadas:

>schtasks ⇒ Lista as tarefas agendadas disponíveis no sistema.

>schtasks /query /v /fo list ⇒ Lista as tarefas agendadas. Filtrar saída com findstr para buscar algo especifico

>schtasks /create /tn "nome_da_tarefa" /tr "path_do_script_ou_exe" /sc "minute" /RU "dominio\usuário" /RP "senha_do_usuário" ⇒ Criar uma tarefa agendada, que será executada pelo usuário especificado, a cada minuto.

>schtasks /create /tn "nome_da_tarefa" /tr "path_do_script_ou_exe" /sc "minute" /RU "system" ⇒ Criar uma tarefa agendada, que será executada pelo usuário system, a cada minuto (Precisar ser usuário system [persistência]).
 	/sc : minute, hourly, daily, weekly, monthly, once, onstart, onlogon 
 
 >schtasks /run /I /TN nome_da_tarefa_agendada ⇒ Executar imediatamente determinada tarefa agendada

>schtasks /delete /tn "nome_da_tarefa" ⇒ Deletar uma tarefa agendada.


OBS:

	* Se encontrarmos uma tarefa agendada executando algum programa que eu tenho permissão para editar, posso tentar modificar o programa que está sendo executado, para tentar executar um programa malicioso (Escalar privilegio).

    * Podemos utilizar o comando de criar uma tarefa agendada para tentar um ataque de força bruta em algum usuário da máquina (Escalar privilegio).

