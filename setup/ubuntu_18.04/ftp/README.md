# VSFTPD: Procedimentos de Instalação e Configuração do serviço de transferência de arquivo (FTP)



## Objetivo

Promover o **download**, **instalação** e **configuração** do serviço de FTP (protocolo de transferência de arquivos). Usaremos o [VSFTPD](https://security.appspot.com/vsftpd.html), principal aplicativo de FTP utilizado nos sistemas Linux. ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***vsftpd*** *(e suas dependências)*.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de instalação do serviço, pode ser feito de várias formas, inclusive pelo site oficial da aplicação VSFTPD *([Downlods](https://security.appspot.com/vsftpd.html#download))*. Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Seguido as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do serviço de FTP no terminal, digite:

`sudo apt install vsftpd`

Após esse comando realizado, o referido serviço já estará disponível, mas diferente dos demais, ele requer várias configurações para funcionar *(que serão verificadas mais adiante neste documento)*.

Para acessar o FTP, do lado do cliente, independente do sistema operacional utilizado, será possível, usando algum ***programa de acesso FTP***, como por exemplo o [FileZilla](https://filezilla-project.org/), sendo possível também acessar de um ***navegador de Internet*** *(Chrome, Firefox)*, ou até mesmo do ***gerenciador de arquivos*** *(Explorer do Windows, Nautilus no Linux, etc.)*, realizando as devidas configurações, como também fornecendo as credenciais de acesso *(usuários e senha)*. 

#### Configuração:

Como estamos partindo de uma instalação limpa, simples e padrão, e além de tudo fazendo a instalação a partir do gerenciador de pacotes e repositório oficial da distribuição,e mantendo o objetivo de apenas ter um servidor web disponível, iremos focar apenas na configuração básica de permissões do FTP e criação de usuários de acesso ao FTP.

Para isso primeiramente, iremos editar o arquivo de configuração do serviço, ***mas antes faremos um backup do arquivo de configuração original*** *(por segurança)*:

`sudo cp /etc/vsftpf.conf /etc/vsftpd.conf.bkp`

E agora editamos o mesmo:

`sudo vim /etc/vsftpd.conf`

Dentro do arquivo de configuração, adicionamos as linhas ou retiramos a tag de comentários *(retiramos o "#")* das linhas, conforme me abaixo:

```bash
# Adicionar ou modifcar linhas conforme abaixo ...
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
ftpd_banner=Welcome to ATM1s2020 FTP Service
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
force_dot_files=YES
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000
# ...
```

Depois, é necessário criar os usuários de acesso ao FTP *(os usuários devem ser criados com especificações restritivas quanto ao local de acesso dos mesmos)*. Desta forma, ***para cada usuários que necessitar liberar acesso ao FTP, seguir as instruções abaixo***.

Quando o VSFTPD é instalado, durante a instalação o grupo ***ftp*** é criado. Usaremos este grupo, para gerar as permissões de acesso ao FTP.

Adicionando usuário ao grupo, e criando uma senha para o usuário:

`sudo useradd -g ftp fulano`

`sudo passwd fulano`

Criando pasta de usuário *(dentro da /home)* e fornecendo toda as permissões necessárias de acesso:

`sudo mkdir /home/fulano`

`sudo chown fulano:ftp fulano`

`sudo chmod a-w ftpuser`

E, s***eguindo as regras de segurança***, com o usuário irá fazer acesso a partir de um cliente de FTP, ***forçaremos o acesso via FTP ir para uma pasta específica***, não permitindo que o usuário, via FTP, possa subir o nível de acesso das pastas *(na hierarquia da árvore de diretórios presente)*. Desta forma, simbolicamente, a pasta ***"/home/fulano" será o diretório "/" do usuário***. Seguindo a regra de segurança imposta acima, iremos criar a partir da pasta base do usuário, iremos criar uma pasta ***public***, e nesta liberar direitos de gravação e leitura:

`sudo mkdir /home/fulano/public`
`sudo chown fulano:ftp /home/fulano/public`

E, agora que está tudo configurado e parametrizado, é necessário iniciar e/ou reiniciar o serviço FTP:

`sudo systemctl start vsftpd.service` 

`sudo systemctl restart vsftpd.service`

A partir deste momento, caso esteja tudo correto na parte de infraestrutura e redes, já será possível acessar o servidor FTP, com as credenciais dos usuários criados para este fim. 

## Referências

[VSFTPD.CONF](http://vsftpd.beasts.org/vsftpd_conf.html)

[VSFTPD](https://security.appspot.com/vsftpd.html)

[VSFTPD - Download](https://security.appspot.com/vsftpd.html#download)

[VSFTPD - Documentação](https://security.appspot.com/vsftpd.html#docs)

[FileZilla](https://filezilla-project.org/)

