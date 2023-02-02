===============idle scan===============
Ocorre no scan com todas as portas escaneadas, que estiveram abaertas.
ele usa o ip de outra maquina da rede para receber a resposta
do ping, ao chegar a resposta nessa outra máquina, ele entende q não 
fez a requisição, fecha a conexão e incrementa o IPID e, mais um ao ver 
a diferença no IPID ele entende a porta como aberta.


Descoberta de zombie para ser usado no processo (idle):
#nmap -O -v -n <range>
#hping3 -S -r < range > (r) permite ver o IPID

Execução
#nmap -sI <IP_IDLE> <IP_ALVO>

USO SCAN
DÁ PRA VER AS RESPOSTAS DO DNS no wireshark

-iL para indicar um arquivo com uma lista de IPs

-oN faz saída em um arquivo
-oX faz saída em xml

