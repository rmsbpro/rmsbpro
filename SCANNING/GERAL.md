ESCANEAMENTO

# nmap -sTUR -O -v -p 1-65535 -P0 hostname.domain

Bom, agora, explicando:

-sTUR --> este é o scan type. Eu utilizei os 3 protocolos disponíveis (Tcp, Udp e Rpc) Tem a opcão de se usar o -sS somente, para fazer o "Scan Stealth"

-O --> tenta descobrir o sistema operacional

-v -- > verbose mode

-p 1-65535 --> varrer todas as portas

Ai é que está a sacada ! Essa flag diz para o NMAP realizar o scan em TODAS as 65535 portas disponíveis. Bom, isso é que me complicou um pouco ...

Se você rodar o NMAP com essa flag em um sistema que estiver com firewall, pode esperar BASTANTE, porque o scan é bem lento ... eu fechei todas as portas da minha máquina, deixando somente alguns poucos serviços rodando (samba, www, ntp, ).

# nmap -sTUR -O -p 1-65535 -P0 matrix

O tempo total de scan foi de 192'47" !!! Mais de 3 horas !!!

Fora que o /var/log/messages ficou enorme!

Para fazer o scan de uma maneira mais rápida, substituimos o -p pela flag -F (default) Essa flag fará o scan somente nas portas privilegiadas (0-1023) e nas portas mais usadas em servicos conhecidos (1024-49,151). Isso pode ser bem útil ao invés de passar por todas44 as 65.535 portas!

-P0 --> Essa opcão diz ao nmap para não pingar o host de destino. Isso é útil, também, quando se faz um scan em uma máquina que possua firewall. Se o firewall bloqueia pacotes ICMP (o que, pessoalmente, não acho uma boa idéia), o nmap nem vai rodar sobre o host. Fora que o ping gera um pequeno delay.

Agora, a flag mais usual acaba sendo essa:

# nmap -sS -O -P0 -v localhost

============SCANNER MELHORADO, SILENCIOSO===========
#nmap -sS -v -sV -p- -Pn IP_ALVO
