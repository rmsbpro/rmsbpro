>>scan evasivo:
	ping scan para saber se up ou down
	nc tbé usado


	Decoy (gera ips falsos)
	-f fragmenta os pacotes 
	nmap -sS -f <alvo>
	nmap -sS -D 92.68.10.2,173.23.54.67,<IP_atacante>,8.2.3.2 <IP_alvo>
	nmap -sS -D RND:[quantidade_IPs_Falsos] [alvo]

	O PACOTE NÃO É MODIFICADO:
	nmap -sS -T[0-5]

 	--souce-port ou -g (mudar a porta q faz a requisição)
	exemplo:
	UDP port 53 – confunde-se com resposta DNS
	TCP port 53 – confunde-se com transferência de zona
	TCP por 80 – confunde-se com reposta de servidores web
	TCP port 443 – confunde-se com respostas HTTPS

#nmap -sS -g 53 -Pn -v --open --scan-delay 1 --max-retries 1 --max-rtt-timeout 1 --top-ports 100 192.168.88.122 -D 192.168.80.133,192.168.70.30,192.168.88.5	
							



