GERENCIAMENTO DE REDE

>netsh interface show interface ⇒ Mostra as interfaces de rede da máquina

>netsh interface ip show address ⇒ Mostra os endereços ip dos adaptadores

>netsh interface ip show tcpconnections ⇒ Mostra os estados e as conexões tcp.

>netsh interface ip set address name=[nome_da_interface] static [novo_ip] [nova_máscara] [ip_do_gateway] 1 ⇒ Alterar o ip de uma interface de rede manualmente

>netsh interface ip set address name="[nome_da_interface]" source=dhcp ⇒ Colocar a interface de rede especificada no modo DHCP.

>netsh interface ip set dns name="[nome_da_interface]" static [IP_do_servidor_DNS] ⇒ Setar o
endereço DNS para a interface especificada.

>ipconfig ⇒ Exibe informações sobre as interfaces de rede

