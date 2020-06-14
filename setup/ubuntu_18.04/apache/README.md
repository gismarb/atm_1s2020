# Apache: Procedimentos de Instalação e Configuração do serviço de acesso Web (Servidor Web)



## Objetivo

Promover o **download**, **instalação** e **configuração** do serviço web, ou em outras palavras do servidor web *(ambiente de hospedagem das páginas, sites, portais, etc)* [Apache](https://httpd.apache.org/). ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***apache2*** *(e suas dependências)*.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de instalação do serviço, podem ser feitos de várias formas, inclusive pelo site oficial da aplicação Apache *([Downlods](https://httpd.apache.org/download.cgi))*. Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Seguido as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do servidor web apache no terminal, digite:

`sudo apt install apache2`

Após esse comando realizado, o servidor web ***Apache2***  já estará disponível para ser utilizado, o que poderá ser verificado, indo até o navegador de Internet *(Chrome, Firefox, etc.)*, com um dos endereços abaixo:

`http://localhost`

`http://127.0.0.1`

#### Configuração:

Como estamos partindo de uma instalação limpa, simples e padrão, e além de tudo fazendo a instalação a partir do gerenciador de pacotes e repositório oficial da distribuição,e mantendo o objetivo de apenas ter um servidor web disponível, não são necessárias demais configurações, com algumas exceções, como por exemplo, habilitar no Firewall as portas de comunicação do protocolo que  o servidor irá utilizar, como ***http e/ou https*** *(o que será demonstrado na seção deste referido serviço)*.

Outras configurações *(pensando na utilização de um servidor web completo)*, poderão ser definidas de acordo com a documentação presente no site oficial do Apache *([Documentação](https://httpd.apache.org/docs/2.4/))* e realizadas no arquivo de configuração do serviço:

 `/etc/apache2/apache2.conf` 

No arquivo acima, poderão ser realizadas várias configurações como ***ServerName***, ***VirtualHosts*** dentre outras.

Para que o serviço esteja ativo, é necessário que o mesmo seja iniciado, e tão logo, seja verificado se está ativo:

`sudo systemctl start apache2.service` 

`sudo systemctl status apache2.service`

## Referências

[Apache](https://httpd.apache.org/)

[Apache HTTP Server Version 2.4 Documentation](https://httpd.apache.org/docs/2.4/)