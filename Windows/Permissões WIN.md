Permissões WIN

ICACLS: Lista as informações de permissão de determinado arquivo/diretório.
Adicionar permissões:
	>icacls [arq.txt] /grant [user]:F

Negar permissões:
 	>icacls [arq] /deny [user]:F
 


Para Exibir as Permissões dos Arquivos utilize o comando:
cacls "nomedoarquivo" (ou pasta)

Será exibido as permissões dadas a esse arquivo. Sendo:
 R  Ler
 W  Gravar
 C  Alterar (gravar)
 F  Controle total
 
e os parametros:

/E – Edita as permissões
/G – Concede direitos ao usuário especificado utiliza-se: cacls "nomearquivo" /E /G usuario:Permissão(R,W,C,F)
/P – Substitui os  direitos ao usuário especificado utiliza-se: cacls "nomearquivo" /E /P usuario:Permissão(R,W,C,F)
/R – Revoga os direitos do usuário especificado utiliza-se: calcs "nomearquivo" /E /R usuario
/D – Nega Acesso ao usuário especificado utiliza-se: calcs "nomearquivo" /E /D usuario


Para Editar permissões :
cacls "nomedoarquivo"(ou pasta) /E /P (ou G) "nomedousuario:Permissão a ser concedida
ex: cacls pci.txt /E /P User:F  – Nesse caso foi concedida permissão total(F) ao usuario "User" para o Arquivo "pci.txt"

Para Remover permissões
cacls  "nomedoarquivo" /E /D usuario
ou
cacls  "nomedoarquivo" /E /R usuario

O retorno da execução correta do comando é : arquivo processado:"Unidade\Nomearquivo"
