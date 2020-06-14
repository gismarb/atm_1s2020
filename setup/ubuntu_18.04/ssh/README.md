# Secure Socket Shell (SSH): Procedimentos de Instalação e Configuração do acesso remoto ao servidor Web



## Objetivo

Promover o **download**, **instalação** e **configuração** do sistema de acesso remoto *(serviços de acesso remoto)*, que em nosso caso é o **SSH** *(acesso remoto via linha de comando)*. ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***openssh-server***.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de insalação do serviço, podem ser feitos de várias formas, inclusive pelo site oficial do [OpenSSH](https://www.openssh.com/). Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Serguindos as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do serviço *(servidor SSH)* no terminal, digite:

`sudo apt install openssh-server`

Após esse comando realizado, o serviço do SSH já estará disponível para ser utilizado.

No lado do ***cliente*** *(de quem vai acessar e/ou usar o acesso SSH)*, ***sendo Linux***, poderá fazer a insalação conforme sua distro *(caso ela não já tenha pré-instalado o pacote)*. No caso das distros derivadas do ***Debian e/ou Ubuntu***, poderão fazer como abaixo:

`sudo apt install openssh-client`

Para quem usa ***Windows***, a referência é  usar o [putty](https://www.putty.org/), baixando do site oficial da aplicação. Este programa não necessita ser instalado, sendo necessário, únicamente, de forma geral, executá-lo, passar o IP do servidor SSH e a porta *(padrão porta 22 TCP)* , para que possa ser estabelecida a conexão.

#### Configuração:

Existem "n" opções de configuração em relação ao uso do serviço de SSH no Linux, mas aqui vamos apenas nos reservar em utilizar o padrão já dísponível logo após a instalação. O Ubuntu Server 18.04.4, por padrão, já vem com acesso SSH desativado, então, a única alteração a realizar, é habilitar a comunicação da  porta 22, no firewall, o que será demonstrado na seção deste referido serviço. 

É importante realçar que SSH, conforme pode checar no portal da  *[Wikipédia](https://pt.wikipedia.org/wiki/Secure_Shell):*

> *"Secure Shell (SSH) é um protocolo de rede criptográfico para operação de serviços de rede de forma segura sobre uma rede insegura"*.

Desta forma, para que não haja confusão, ***SSH é o protocolo de acesso remoto***, e ***openssh-server, é o serviço e/ou programa que utiliza o referido protocolo para realizar o que o mesmo propõe*** *(acesso remoto seguro, via linha de comando - CLI)*. 

## Referências

[OpenSSH](https://www.openssh.com/)

[Putty](https://www.putty.org/)

[Secure Shell](https://pt.wikipedia.org/wiki/Secure_Shell)