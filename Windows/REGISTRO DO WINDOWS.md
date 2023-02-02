REGISTRO DO WINDOWS

É um banco de dados hierárquico que armazena as configurações e opções necessárias para executar aplicativos e comandos.

	O registro é na verdade um banco de dados do sistema que armazena todas as configurações dos aplicativos que instalamos. Sempre que trocamos um papel de parede, instalamos um reprodutor de vídeo ou trocamos o nosso navegador padrão de internet, efetuamos modificações nesse banco de dados para que o Windows saiba como queremos que ele funcione.
	
	É uma área restrita do sistema Windows que armazena informações a respeito de todas as configurações do computador, tais como software instalados, parâmetros do sistema, até a parte de hardware. Sendo assim, toda vez que um programa é instalado no sistema, uma nova sub-chave contendo diversas configurações, como localização e versão do programa, etc é adicionada ao Registro do Windows.

As principais chaves do registro ficam salvas no diretório "C:\Windows\System32\config".



Porém, não podemos editar as chaves por esses arquivos. Para fazer isso, precisamos abrir o editor de registro do windows.

Ao abrir o Editor de Registro do Windows (regedit), ele irá exibir as chaves que contêm todas as sub-chaves e os valores do registro.





A estrutura do registro se assemelha a uma árvore de diretórios, tal como o Windows Explorer. 
	
	Existem cinco chaves de registro principais, que contêm uma estrutura de chaves, subchaves e valores.

Fazendo uma analogia ao Windows Explorer:
Chave = Diretório
SubChave = Sub-Diretório
Valor = Arquivos

Cada valor tem a seguinte estrutura:
	- Nome 
	- Tipo
	- Dados



HKEY_LOCAL_MACHINE\Software\RegisteredApplications = sub-chave "RegisteredApplications" da subchave "Software" da chave HKEY_LOCAL_MACHINE. 


CHAVES DO REGISTRO:

 HKEY_CLASSES_ROOT (HKCR): Presente nas versões atuais do Windows apenas para manter a compatibilidade com programas mais antigos.

 HKEY_CURRENT_USER (HKCU): Contém todas as configurações do usuário logado no sistema.

 HKEY_LOCAL_MACHINE (HKLM): Chave mais importante do registro, guarda todas as informações que o sistema operacional precisa para funcionar e de sua interface gráfica. Utiliza o arquivo SYSTEM para armazenar essas configurações.

 HKEY_USERS (HKU): Guarda as configurações de aparência do Windows e as configurações efetuadas pelos usuários, como papel de parede, protetor de tela, temas e outros.

 HKEY_CURRENT_CONFIG (HKCC): Salva os perfis de hardware utilizados pelo usuário. 


QUAL A IMPORTÂNCIA DISSO??

Através do registro do Windows, é possível mudar o comportamento padrão de alguns programas do Sistema Operacional, assim como é possível conseguir algumas informações importantes, como versão de programas, senhas, etc.

	Exemplos:

"In RealVNC the hashed password is located in the following registry key":
	HKLM\SOFTWARE\RealVNC\WinVNC4 /v password

reg query HKLM /f password /t REG_SZ /s: Comando para buscar pela string "password" dentro da chave HKLM.

reg query "HKCU\Software\SimonTatham\PuTTY": Comando para ver detalhes de conexões realizadas com o programa putty.



reg  query  chave\subchave\subchave\subchave: Comando para ver os valores e subchaves contido no caminho especificado. 

reg  add  chave\subchave\subchave: Adicionar um registro

reg  add  chave\subchave\subchave  /v  nome_do_valor  /t tipo  /d  dado: Adicionar determinado valor a um registro.

reg  delete  chave\subchave\subchave: Remover um registro

reg  save  chave\subchave\subchave arquivo_de_saida: Copiar chaves de registro para um arquivo (com extensão .hiv).

Exemplo de uso de registro:

reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f: Ao editar essa chave, o protocolo  fica ativado na maquina.
