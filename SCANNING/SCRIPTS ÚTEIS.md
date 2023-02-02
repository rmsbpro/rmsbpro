							

========== VERIFICAR ATIVOS DA REDE==========
#fping -c1 -g 172.16.26.0 172.16.26.255 | grep ms | awk '{print $1}' > LOGping.txt

#nmap -sP 172.16.26.0/24 | grep for | awk '{print $5}' > LOGpingNmap.txt

========== VERIFICA ATIVOS COM DNS REVERSO===========

#nmap -sL 177.8.88.0/20 | grep eb.mil.br | awk '{print $6}'  LOGip4.txt 

#sed -i "s/(//g" LOGips4.txt | sed -i "s/)//g" LOGips4.txt 

==========VERIFICA PORTAS ABERTAS DE UM HOST======
#nmap -p- IP_ALVO

===SCANNER COM NETCAT====
outra possibilidade de scanear é usar o netcat
ex: porta 80

#nc -nv 192.168.122.43 80

scaneando mais portas ((checar))
#for port in {1..1024}; do nc -nz 192.168.122.43 "$port" && echo "$port" open; done

#nc -nvz 192.168.122.43 1-1024 2>&1 | grep "succeeded!" (trás somente as portas abertas, não resolve nomes)
saída: Connection to 192.168.122.43 512 port [tcp/*] succeeded!


#nc -vz 192.168.122.43 1-1024 2>&1 | grep "succeeded!" (resolve nomes)
saída: Connection to 192.168.122.43 445 port [tcp/microsoft-ds] succeeded!

===Banergrap é par a descobrir o q está rodando na porta===
#echo scnatemp | nc -nv 192.168.122.43 80 (escreve o q está rodando no terminal na tela)

#echo 'HEAD' | nc -nv 192.168.122.43 80 (escreve o q está rodando no terminal na tela e tras a versão do servidor web)


=============VERIICA NAS PORTASA AGUNS TESTES DE EXPLOITS CONHECIDOS==========
#nmap -p 21,22,23,25,53,80,111,139,445,512,513,514,1099,1524,2049,2121,3306,3632,5432,5900,6000,6667,6697,8009
,8180,8787,44198,44957,58125,60811 --script vuln 192.168.122.43

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
========NMAP MELHORADO=====
Para escapar de IDS/IPS firewal
==========scanner inicial(completão)===============
nmap -sS -v --scan-delay 1 --max-retries 1 --max-rtt-timeout 1 --top-ports 100 <IP_ALVO> -D 192.168.80.133,192.168.70.30,192.168.26.6

-sS = não fecha conexão TCP
--scan-delay 1 = espera 1 segunda entre cada onda de varredura
--max-retries 1 = só faz 1 tentativa por porta
--max-rtt-timeout 1 = só espra a porta responder por 1 seg
--top-ports 100 = scan nas 100 principais portas
-D = são os IPs q a máquina atacante irá assumir para enganar as detecções

=============ENCONTRAR AS VULNERABILIDADES=============================
nmap -p <porta1,porta2,porta3,...> --scan-delay 1  --script vuln <IP_ALVO> -D 192.168.80.133,192.168.70.30,192.168.26.6
OBS: é bom trocar os IPs do -D
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


====RESUIDO MAN DO NMAP====

O scan SYN é a opção de scan padrão e mais popular por boas razões. 
Pode ser executada rapidamente, escaneando milhares de portas por
segundo em uma rede rápida, não bloqueada por firewalls intrusivos.
Ele também permite uma diferenciação limpa e confiável
 entre os estados aberto (open), fechado (closed), e filtrado (filtered).

nmap -sS -v -n --scan-delay 2 --max-retries 1 --max-rtt-timeout 1 <IP_AlVO> -D 192.168.80.133,192.168.70.30,192.168.26.6

OBS: Outro uso do --scan-delay é para evitar os sistemas de prevenção e
 detecção de intrusão (IDS/IPS) baseados em limites

OBS: --max-retries <númerodetentativas>
 (Especifica o número máximo de retransmissões de sondagens de scan de portas)


OBS:scan UDP, o DNS, o SNMP, e o DHCP (registrados nas portas 53, 161/162, e 67/68) 
nmap -sU -t 1 IP

OBS: O principal efeito de -T0 é serializar o scan de forma que apenas uma 
porta é escaneada por vez, e então, aguardar cinco minutos entre o envio de 
cada sondagem (FAZ TCP)


OBS:Se for scanear uma rede interira uma boa opção para agilizar o processo é
o --host-timeout (script do nmap q pula hosts lentos de scanear), pois 65mil 
portas de cada host pode levar a 18h de scan

OBS: -D Disfarça um scan usando chamarizes
-D 192.168.80.133 192.168.70.30 192.168.26.6

OBS: --top-ports 100 ou --top-ports 1000


==========scanner inicial(completão)===============
nmap -sS -v -g 53 --scan-delay 1 --max-retries 1 --max-rtt-timeout 1 --top-ports 100 192.168.88.122 -D 192.168.80.133,192.168.70.30,192.168.26.6
====================================================


OPÇÕES DE MARCAÇÃO DOS PACOTES DO NMAP:
scan Null (-sN)

    Não marca nenhum bit (o cabeçalho de flag do tcp é 0)
scan FIN (-sF)

    Marca apenas o bit FIN do TCP.
scan Xmas(-sX)

    Marca as flags FIN, PSH e URG, iluminando o pacote como uma árvore de Natal

-sI <hostzumbi[:portadesondagem]> (scan Idle)


DETECTAR FIREWALL
nmap -p80,443 --script http-waf-detect --script-args="http-waf-detect.aggro,http-waf-detect.detectBodyChanges" targetWebsite.com

DETCTAR FIREWALL COM MAIS RUÍDO
nmap -p80,443 --script http-waf-fingerprint --script-args http-waf-fingerprint.intensive=1 targetWebsite
