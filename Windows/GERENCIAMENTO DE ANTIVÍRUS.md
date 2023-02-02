GERENCIAMENTO DE ANTIVÍRUS

Sequencia de comandos para tentar desabilitar o Windows defender, utilizando o powershell. Não é necessário reiniciar a máquina. Mudar para $false caso queira reativar:

       netsh advfirewall set allprofile state off 
	> powershell.exe Set-MpPreference -DisableIOAVProtection $true
	> powershell.exe Set-MpPreference -DisableRealTimeMonitoring $true
netsh advfirewall set allprofile state off 
No Windows a partir da build 18305, a proteção contra violações do Windows defender deve estar desativada. Para verificar se a proteção contra violações está ativa, use o comando:

	>	powershell.exe Get-MpComputerStatus
	
Na saída do comando acima, procurar por "IsTamperProtected". Caso esteja como true, não será possível desabilitar o Windows defender com esse método.		

-------------------------------------------------------------------------------------------------

Sequencia de comandos para tentar desabilitar o Windows defender, utilizando chaves de registro. É necessário reiniciar a maquina para fazer efeito. Para ativar novamente, mudar o valor dos registros para 0

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware  /t reg_DWORD /D 1 /F

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableBehaviorMonitoring /t reg_DWORD /D 1 /F

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableOnAccessProtection /t reg_DWORD /D 1 /F

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableScanOnRealtimeEnable /t reg_DWORD /D 1 /F


-------------------------------------------------------------------------------------------------

> wmic product get name,version, installlocation: Lista os programas instalados no Sistema, assim como sua versão e local onde estão instalados (Se ficar muito grande para o terminal, tirar algum parâmetro).

> wmic product where name="nome do programa"  call uninstall  /nointeractive : Após verificar o nome do antivírus, tentar deletar ele do sistema.

net start: Listar os serviços ativos.
net stop "nome_do_antivirus": Tentar pausar o serviço do antivírus.

OBS: Tentar renomear os arquivos (de .exe para .rar, por exemplo) do antivírus na pasta em "Arquivos de programas".
