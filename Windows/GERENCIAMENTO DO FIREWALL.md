GERENCIAMENTO DO FIREWALL

>netsh advfirewall show allprofiles ⇒ Mostra o status do firewall (Ativo ou Inativo)

>netsh advfirewall set allprofile state off ⇒ Desabilita o firewall do Windows.

>netsh advfirewall set allprofile state on ⇒ Habilita o firewall do Windows.

>netsh advfirewall firewall add rule name="nome_da_regra" dir=in action=allow protocol=tcp program="C:\caminho\programa.exe" enable=yes ⇒ Permitir que um programa especifico no firewall.

>netsh advfirewall firewall add rule name="nome_da_regra" dir=in action=allow protocol=tcp localport=4444: Abrir uma porta especificada no firewall:

	• dir = in | out
	• action = allow|block
	• protocol = TCP | UDP |any
	
OBS:

*Obs: As portas 80 e 443 costumam estar abertas para conexões de saída. Interessante tentar utilizar essas portas para obter um shell reverso

