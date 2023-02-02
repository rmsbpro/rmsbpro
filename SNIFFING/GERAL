É CRIME INTERCEPTAÇÃO DE COMUNICAÇÕES. Pena de 2 a 4 anos.



sniffing só funciona dentro de uma LAN, protocolo ARP,
é preciso entrar nessa LAN.

Dispositivo usado: raspibarry pie, mandando para internet ou wifi proximo.
 

sniffing passivo apenas escuta o trafego
sniffing ativo envolve injeção de pacotes na rede, altera o trafego de rede.
atua na camada 2.
softwares usados: sniffers (tcpdump, wireshark)
hardware usado: raspibarry pie ou big-ip-F5.

===big-ip-F5, realiza SSLinspection, procura me trafegos critografados se há 
algo malicioso.

OBS: SERVIDOR NUNCA INICIA CONEXÃO

loopback - serve para q duas aplicações se comuniquem entre si.

TOR-usa um proxy entre aplicações e cria os saltos, o nó de entrada não
consegue decriptografar, só encaminha, e o nó de saída é reponsável 
pelo trafego.
É recomendado q o nó de saída da rede TOR saia por tunel em um país q aceite
anonimato.

Em linux
rede proxy TOR 127.0.0.1 9150

Em windows tem q usar o navegador.

NUNCA INSTALE UM NÓ DE SAÍDA EM SUA MÁQUINA.

SÓ O HUB PERTMITE SNIFFING PASSIVO, O RESTO TODOS SÃO SNIFFING ATIVOS.

VLANs PARA SE COMUNICAREM ENTRE SI PRECISAM DE ROTEAMENTO ENTRE ELAS, UM SWITCH 
PODE FAZER ISSO, MAS O IDEAL É Q SEJA UM ROTEADOR.
A TABELA "CAM" DO SWITCH É RESPONSÁVEL POR ISSO, NA PRIMEIRA TROCA DE PACOTE
ELE VAI MONTANDO ESSA TABELA.

SWITCH NÃO POSSUI MAC, SÓ CORRELACIONA INTERFACE COM MAC DO HOST

QUANTO MAIS ANTENAS, MAIS CONEXÕES AO MESMO TEMPO PODEM SER FEITAS.


====PROTOCOLO ETHERNET===
CAMADA ENLACE ANALISA OS PREAMBULOS, SEQUENCIAS DE 8BITS Q SEPARAM OS FRAMES
EX:
0806h:ARP
0800h:IPv4
86ddh:IPv6

OBS: WIRESHARK NÃO INTERPRETA CAMADA 1
OBS: A CRIPTOGRAFIA SÓ ENTRA NA CAMADA 6, APRESENTAÇÃO, PROTOCOLO TLS


===CAMADA 3 REDE===
ARP - É SEM AUTENTICAÇÃO, ACEITA RESPOSTAS DE PERGUNTAS Q ELE NÃO FEZ,
PODE SER ALTERADO.

ISSO PODE SER USADO PARA DESVIAR TRAFEGO, POIS AO ENGANAR O SWITCH, O USUÁRIO 
É ENGANADO, POIS NÃO É AUTENTICADO, ISSO É SNIFFING DE REDE.
O SNIFFING FICA ENTRE DUAS PESSOAS E FAZ O ENCAMINHAMENTO ENTRE UM E OUTRO
MANTENDO AS REQUISIÇÕES ENTRE OS DOIS, PARA AS VÍTIMAS A CONEXÃO É DIRETA.

GATEWAY É UM IP Q INTERLIGA REDES, NÃO PRECISA SER O PRIMEIRO ENDEREÇO.
MUDA UM PACOTE DE UMA REDE PARA OUTRA MUDANDO O MAC DE ORIGEM A CADA ROTEADOR 
QUE PASSA.


OBS: SOMENTES ARPs REPLAY ALTERAM A TABELA ARP


=====FORMATAR PEN DRIVE=====
    Para o sistema de arquivos vFAT (FAT32): sudo mkfs.vfat /dev/sdc1
    Para sistema de arquivos NTFS: sudo mkfs.ntfs /dev/sdc1
    Para o sistema de arquivos EXT4: sudo mkfs.ext4 /dev/sdc1

===PARA ACHAR OS HOSTS==== (são boas suloções para redes q não repondem ping)
NMAP- USA CAMCADA DE TRANSPORTE 
NETDISCOVERY - USAR ARP

===criptografia==
a falha não é na criptografia e sim na implementação.
TLS 1.3 é o mais atual, mais seguro

==APLICAÇÃO==
DNS- TRAFEGA DADOS EM CLARO, SÃO AUTENTICADOS POR DNSsec
(PODE SER MANIPULADO)
EU NÃO PRECISO FALSIFICAR TODA A CADEIA, 
APENAS A ÚLTIMA E ENCAMINHAR PARA A VÍTIMA
