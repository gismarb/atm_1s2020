# PHP : Procedimentos de Instalação e Configuração do ambiente de desenvolvimento web (Stack de desenvolvimento PHP)



## Objetivo

Promover o **download**, **instalação** e **configuração** do serviço do ambiente de ***PHP*** *(stack de desenvolvimento web)*. ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***php7.4*** *(e suas dependências, que em nosso caso são obrigatórias)*.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de instalação do ambiente de desenvolvimento, podem ser feitos de várias formas, inclusive pelo site oficial do PHP *([Download](https://www.php.net/downloads))*. Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Seguido as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do ambiente de desenvolvimento PHP no terminal, digite:

`sudo apt install php7.4 libapache2-mod-php7.4 php7.4-mysql php7.4-curl php7.4-common`

Os pacotes acima *(assim como módulos)*, são os pacotes básicos para utilização do PHP em conjunto com o Apache e o MySQL Server. Todavia, será possível instalar outros módulos do PHP, de acordo com as necessidades de cada projeto. ***Os módulos do PHP disponíveis podem ser verificados da seguinte forma***:

`sudo apt-cache search php- | less`

#### Configuração:

Existem "n" configurações possíveis, que podem ser verificadas na seção de documentação do portal oficial do PHP *([Documentação](https://www.php.net/docs.php))*. 

Para nosso uso, apenas precisamos reiniciar o servidor web:

`sudo systemctl start apache2.service`

`sudo systemctl status apache2.service`

Agora, para conferir se a integração entre Apache e PHP estão em pleno funcionamento, vamos realizar um teste básico *(verificar se o servidor interpreta a uma arquivo .php)*, vamos criar um arquivo teste.php:

`sudo vim /var/www/html/teste.php`

Depois digitamos o conteúdo:

```php
<?php
	phpinfo();
?>
```

Logo após, salvamos e fechamos o arquivo (conforme seu edito preferido, em nosso caso usamos o VIM), e reiniciamos o servidor web novamente:

`sudo systemctl restart apache2.service`

Agora, vamos ao navegador de Internet, e acessamos um dos dois links abaixo:

`http://localhost/teste.php`

`http://127.0.0.1/teste.php`

Desta forma, o resultado esperado é o que se segue logo abaixo:

![](../../../images/2_acesso_phpinfo.gif)

## Referências

[PHP](https://www.php.net/)

[PHP - Downloads](https://www.php.net/downloads)

[PHP - Documentação](https://www.php.net/docs.php)