# SAMBA : Procedimentos de Instalação e Configuração do serviço de compartilhamento de arquivos do servidor (SAMBA)

## Objetivo

Promover o **download**, **instalação** e **configuração** do serviço de compartilhamento de arquivos ***SAMBA*** *(principal programa de compartilhamento de arquivos entre Linux e Windows, nativo para ambientes Linux)*. ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***samba*** *(e suas dependências)*.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de instalação do ambiente de desenvolvimento, podem ser feitos de várias formas, inclusive pelo site oficial do SAMBA *([Download](https://www.samba.org/samba/download/))*. Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Seguido as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do serviço de compartilhamento de arquivos do SAMBA, no terminal, digite:

`sudo apt install samba`

Com o comando acima, todos os componentes serão instalados para que esteja disponível para criar os compartilhamentos de arquivos *(assim como compartlilhamento de recursos, como Impressora e outros)*.

#### Configuração:

Existem "n" configurações possíveis, que podem ser verificadas na seção de documentação do portal oficial do SAMBA *([Documentação](https://www.samba.org/samba/docs/))*. 

Para nosso uso, teremos apenas que fazer a configuração básica do compartilhamento de arquivo, e registrar os acessos dos usuários (credenciais de acesso). Para isso, será necessário seguir os passos abaixo.

Fazer backup do arquivo de configuração do SAMBA:

`sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bkp`

Editar o arquivo de configuração:

`sudo vim /etc/samba/smb.conf`

No arquivo de configuração, apagar todas as linhas presentes, e usar a configuração abaixo *(de acordo com sua necessidade, poderá realizar outra configurações diferentes)*:

```bash
[global]
workgroup = WORKGROUP
netbios name = ubuntu_server
security = user
server string = Linux
os level = 33
log file = /var/log/samba/log.%m
log level = 1
max log size = 100
debug level = 2

[DADOS]
comment = Compartilhamento do Samba
path = /usr/local/DADOS
public = yes
browseable = yes
writable = yes
read only = no
create mask = 0777
directory mask = 0777
force create mode = 0777
force directory mode = 0777
```

Após a configurações acima, iremos criar a pasta para compartilhamento, e assim, dar as permissões necessárias.

Crie a pasta de compartilhamento, que em nosso caso será criado em ***"/usr/local"*** a pasta ***"DADOS"*** *(o local do compartilhamento será de acordo com a necessidade)*:

`sudo mkdir -p /usr/local/DADOS` 

Forneças as permissões necessárias *(em nosso caso leitura e gravação e execução)*:

`sudo chmod 777 /usr/local/DADOS`

Crie os acessos ao  compartilhamento via SAMBA *(neste caso, poderá ser ou não o usuário de existente no servidor Linux)*:

`sudo smbpasswd -a fulano`

Após isso, reinicie o  serviço do SAMBA, para consolidar as modificações:

`sudo systemctl restart smbd.service`

Neste momento, basta acessar o compartilhamento *(repassando usuário e senha, previamente cadastrados)*, por meio de um ***gerenciador de arquivos*** *(Explorer do Windows, Nautilus do Linux, etc)* e, caso tudo esteja *"OK"*, o acesso será liberado para gravar, ler e excluir documentos, assim como executar programas diretamente do compartilhamento.

## Referências

[SAMBA](https://www.samba.org/)

[SAMBA - Downloads](https://www.samba.org/samba/download/)

[SAMBA - Documentação](https://www.samba.org/samba/docs/)