WINDOWS POWER SHELL

CMD, também conhecido como command prompt, é o utilitário do Windows. Ele é simples e funciona, mas deixa a desejar para tarefas mais sofisticadas. PowerShell é uma nova ferramenta disponível no Windows e mais recentemente no Linux e MacOS.

Os comandos do PowerShell são chamados de cmdlets. A maneira mais fácil de encontrar esses comandos no PowerShell é executar "Get-Command -Type Cmdlet".

Para criar um script em powershell, basta criar um arquivo com a extensão .ps1.

Podemos executar comandos no powershell abrindo o programa pela interface gráfica ou escrevendo "powershell.exe" no contexto do cmd.

-> Parâmetros uteis:
	> -ExecutionPolicy Bypass: ignorar as políticas de segurança do powershell.
	> -Command "xxx": Executa o comando entre aspas, no contexto do powershell.
	> Invoke-expression (IEX): Executa strings como se fossem comandos do powershell.

Usar ; concatena(ponto-e-virgula)


