
CRIANDO USUÁRIO NO KALI LINUX


Para criar outro usuário execute:

# useradd -m usuario

O "-m" serve para criar o diretório do usuário.

Crie a senha:

# passwd usuario

Adicione o usuário ao grupo sudo:

# usermod -a -G sudo usuario

Altere o shell do usuário:

# chsh -s /bin/bash usuario

apagar
#userdel -r usuario

