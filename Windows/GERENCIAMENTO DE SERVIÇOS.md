GERENCIAMENTO DE SERVIÇOS

	Um serviço é um aplicativo quase como qualquer outro. A diferença é que eles são executados em segundo plano e não possuem uma interface de usuário na qual seja possível clicar ou tocar. Eles fornecem recursos do sistema operacional, como serviços de rede, verificação de atualização, escaneamento do sistema (antivírus), etc...

> sc query: lista os serviços ativos.
	> sc query state= all: Lista todos os serviços

sc query | findstr "NOME_DO_SERVIÇO": Lista apenas os nomes dos serviços (Para Windows em português)

sc qc nome_do_serviço: Mostra configurações e informações de um serviço.

sc start nome_do_serviço : Inicia um serviço

sc stop nome_do_serviço : Para um serviço

sc create "nome_do_serviço" binPath= "caminho_do_executável" DisplayName= "descrição_do_serviço" start= "auto" obj= "dominio\usuário_que_executará" password= "senha_do_usuário": Criar um novo serviço passando usuário e senha de algum usuário. (adicionar quando iniciar o serviço) 

sc delete "nome_do_serviço": Exclui um serviço

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------


(Atenção para o espaço após os sinais de "=" ).
sc create "nome_do_serviço" binPath= "caminho_do_executável" DisplayName= "descrição_do_serviço" start= "auto" obj= ".\LocalSystem": Criar um novo serviço , que será executado pelo usuário system.
sc config nome_do_serviço binPath= novo_caminho_do_executável: Exemplo de comando para mudar o caminho do executável que o serviço executa. 
sc config nome_do_serviço obj= ".\LocalSystem": Comando para mudar o usuário que executa o serviço (Nesse caso, executar como usuário system).

OBS:
Se encontrarmos um serviço que tenhamos permissão de edição, podemos modificar o caminho do executável que o serviço executa, forçando ele a executar um programa malicioso (Escalar privilégio).

Se encontrarmos um programa que está sendo executado por um serviço e que meu usuário tenha permissão para substituir esse programa, posso colocar um programa malicioso nesse path. (Escalar privilegio). 
