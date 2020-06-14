# MySQL Server : Procedimentos de Instalação e Configuração do Sistema Gerenciador de Banco de Dados (SGBD)



## Objetivo

Promover o **download**, **instalação** e **configuração** do serviço de banco de dados ***MySQL*** que será utilizado em conjunto com o PHP e Apache, para criar o ambiente de servidor web *(assim, como stack para programação Web)*. ***Aqui, será demonstrada a forma básica de realizar o procedimento e configuração***.

O pacote que utilizaremos será o ***mysql-server*** *(e suas dependências)*.

> ***Observação:*** *todos os procedimentos demonstrados e comentados aqui, serão baseados na distribuição Ubuntu Server 18.04.4 (demais versões de Ubuntu Server, anteriores ou posteriores, poderão ter procedimentos diferentes para a instalação destes serviços).*
>
> ***Para outras distribuições, pesquisar a documentação para específica para cada distribuição.***

## Como fazer

#### **Download**: 

O download do arquivos de instalação do serviço, podem ser feitos de várias formas, inclusive pelo site oficial do MySQL *([Download](https://www.mysql.com/downloads/))*. Nós aqui, indicamos que o mesmo seja ***baixado do repositório oficial do Ubuntu Server, via apt***.

#### Instalação: 

Seguido as recomendações prévias *(utilizando os repositórios oficiais da distribuição via apt)*,  para instalação do servidor de banco de dados MySQL no terminal, digite:

`sudo apt install mysql-server`

Após o procedimento da instalação, será possível *(fica a critério de cada aplicação)*, realizar ou não a instalação das regras e políticas de segurança do ***MySQL Server***:

`sudo mysql_secure_installation`

Basicamente, quando optamos pela opção acima, teremos que configurar o grau de segurança da senha, se iremos remover o banco de testes *(que acompanhar a instalação)*, remover o anúncio de usuários anónimo, dentre outras opções. Recomendamos, para maiores detalhes *([Documentação](https://dev.mysql.com/doc/refman/8.0/en/installing.html))*.

#### Configuração:

Diferentemente dos demais serviços, o MySQL requer várias configurações para que possa ser utilizado. Inicialmente, é indicado alterar o modo de de autenticação do usuário ***root*** ***(por questões de segurança)***, do modo ***auth_socket*** para ***mysql_native_password***, seguido os passos abaixo:

1. No terminal:

   `sudo mysql`

2. Após acessar ao banco de dados, poderá verificar *(SELECT)* quais usuários e métodos de autenticação *(opcional)*:

   `SELECT user,authentication_string,plugin,host FROM mysql.user;`

3. Alterar modo de autenticação do usuários root:

   `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'alguma_senha_forte_aqui';`

4. Atualizar mudanças na tabela de usuários do MySQL:

   `FLUSH PRIVILEGES;`

5. Por fim, poderá realizar novamente a consulta da tabela de usuários do MySQL *(presente no passo 2)*, e encerrar o acesso ao banco de dados.

A partir deste momento será necessário inicializar o serviços do MySQL Server, para que possa usar o banco de dados, e tão logo, verificar se este serviço está ativo: 

`sudo systemctl start mysql.service` 

`sudo systemctl status mysql.service`

E a partir deste momento, o ***MySQL Server*** estará pronto para o uso, onde os bancos de dados e acessos (usuários), poderão ser criados para sua utilização.

## Referências

[MySQL](https://www.mysql.com/)

[MySQL - Documentação (Instalação Geral)](https://dev.mysql.com/doc/refman/8.0/en/installing.html)

[MySQL - Documentação (Instalação via APT)](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/)