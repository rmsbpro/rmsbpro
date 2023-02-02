Comandos Básico Win:

cls ⇒Limpa a tela

help [comando] ⇒ ajuda [comando] /? ⇒ ajuda
dir  ⇒ listar diretorios
dir /s ⇒ exibe diretorios recursivos
dir /a ⇒ exibe diretorios [ver arq ocultos ou especificos]
dir /b ⇒ exibe dir sem cabeçalhos
dir /s /a /b *pass* == *cred* == *vnc* == *unatt* == *.config*  ⇒ busca por arquivos que contenham o nome especificado a partir do dir atual
   → pass ⇒ senhas
   → cred ⇒ credenciais
   → vnc, unatt ⇒ pode haver senhas nesses formatos
   → .config ⇒ configurações
cd ⇒ mostra o diretorio atual principlamente estando num terminal não interativo ˝terminal cachorro˝
cd .. ⇒ entra numa pasta acima
cd [pasta] ⇒ entra na pasta

TAB para completar (ñ funciona no terminal cachorro[terminal ñ interativo])
CLICK C BOTAO DIR NA TELA DO TERMINAL, JÁ COPIA AUTOMÁTICAMENTE E COLA AO CLICAR NOVAMENTE NA TELA.

mkdir [nome_pasta] ⇒ criar pasta
md [nome_pasta] ⇒ criar pasta
rd [pasta] ⇒ excluir pasta vazia
rd [pasta] /s ⇒ exclui pasta com subpastas, e pede confirmação
rd [pasta] /s /q ⇒ quiet, exclui pasta sem confirmação
del ⇒ deleta arq ou pastas
type ⇒ Exibe o conteúdo, em formato de texto, de um arquivo
ren [nome1] [nome2]⇒ Renomear
xcopy ⇒ faz cópia de arquivos e pastas.
xcopy /e [arq copiado] [destino] ⇒ a opção /e copia tudo da pasta
xcopy /s [arq copiado] [destino] ⇒ a opção /s copia tudo da pasta, exceto os vazios.
move [origem] [destino] ⇒ Move arquivos de uma pasta pra outra.
fc [arq1] [arq2] ⇒ Compara e mostra a diferença entre dois arqvs.
tree [diretorio] ⇒ Lista o diretório atual e todos os seus subdiretorios
tree /f ⇒ Lista o diretório atual e todos os seus subdiretórios e arquivos
sort [arq.txt] ⇒ Exibe o conteúdo do arquivo especificado, na ordem alfabética.
sort /r [arquivo.txt] ⇒ Exibe o conteúdo do arquivo especificado, ordem alfabética reversa 
whoami ⇒ Mostra o nome de usuário e domínio atual.

shutdown ⇒ Desligar/ reiniciar o sistema.
shutdown /s ⇒ Desligar
shutdown /l ⇒ fazer logoff
shutdown /r ⇒ reiniciar
shutdown /f ⇒ executar shutdown sem avisar o usuário
shutdown /c "comentário" ⇒ aparece um aviso para o usuário antes de fazer o desligamento.

˝|˝ Executa um comando de acordo com a saída do comando anterior.
	Ex: type [arquivo.txt] | sort ⇒ O comando sort é executado em cima do resultado do comando type.
˝>˝ ⇒ Direciona a saída de um comando para um arquivo (substituindo o conteúdo do arquivo).
˝>>˝ ⇒ Direciona a saída de um comando para o conteúdo de um arquivo (Adiciona o conteúdo do arquivo) .
˝2>nul": Omite a saída de erros de um comando

IMPORTANTE
runas /user:host\usuario comando ⇒ Executa um comando como um dos usuários do sistema.
Ex: >runas /user:desktop-096icii\usuario2 "cmd.exe /c echo 1 > 1.txt" ⇒ O usuário informado(atacado) executa o cmd ˝echo 1> 1.txt˝

Atribuição das pastas:
attrib ⇒ no resultado qnd apresentar ˝A˝ o sistema sabe q não foi feito o bkp ???
attrib /s ⇒ Exibe os atributos dos arquivos do diretório atual e de seus subdiretórios
attrib /d ⇒ Exibe os atributos dos arquivos e diretórios do diretório atual e de seus subdiretórios.
attrib +s +r +h +a [arq] ⇒ Deixa arq oculto e ñ mostra esse arq, qnd aberto pl interface gráfic, mesmo com a opç de "mostrar arq ocultos" estando ativa. Impede tb q esse arq seja deletado via terminal!
attrib +h pasta => ocultar o diretorio
attrib -h pasta => reexibir o diretório
outras opç do attrib: r(so ler), a(morto), s(sis), h(ocul), o(off), i(s/ conteúd index), x(s/ atrib de arq de remoção), v(integridade), p(fixado), u(desafixado), b(blob SMR).
     

Buscar arquivos:
findstr [nome*] [arq.txt] ⇒ localizar arq (grep bem cachorro), Exibe apenas as linhas do arq.txt q tem a string especificada.
findstr /i [nome*] ⇒ localizar arq com ignore case
findstr /spin /c:˝password˝ *.* 2>nul ⇒ Procura, em todos os arq a partir do dir atual, por arq q contem a string especific.
