# Atividades Multidisciplinares 1º Semestre 2020 - (ATM1s2020)
Desenvolvendo um Workflow para um Servidor Web, com Apache, MySQL, PHP, SSH, FTP, SAMBA.

------



### Resumo

O processo de desenvolvimento de um ambiente Web é complexo e trabalhoso. Partimos do projeto, estudo do ambiente, criação do ambiente *(S.O.)*, depois criamos a base para o funcionamento do ambiente Web *(que é caracteriza-se por um serviço web, stack e/ou linguagem web e sistema de banco de dados)*, e para gerar uma camada de infraestrutura de suporte para o ambiente, implementamos serviços básicos de infraestrutura *(sistema de FTP, compartilhamento de arquivos, acesso remoto e regras de firewall)*

### Sumário
[Resumo](#resumo)

[Introdução](#introdução)

[Desenvolvimento](#desenvolvimento)

[Conclusão](#conclusão)

[Referências](#referências)

### Introdução

Este projeto visa demonstrar todos os principais processos existentes na produção e desenvolvimento de um ambiente web, do ponto de vista de criação de ambiente e suas especificidades.

### Desenvolvimento

Um servidor Web, ou uma ***Stack completa de produção Web*** deve ser separada por áreas específicas. Desta forma, cada área específica deverá ser trabalhada e desenvolvida de forma paralela, para que no final se tenha um ambiente disponível, confiável e produtivo.

Desta forma, devemos separar o desenvolvimento em:

- ***Servidor web:*** Será o ambiente onde o site ou sistema Web será interpretado, e da onde serão respondidas as chamadas ***http e/ou https***.

  [Apache](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/apache/README.md)

- ***Stack de desenvolvimento web:*** Quando falamos na Stack de Desenvolvimento, nos referimos a uma ou mais ***linguagens de back-end*** que serão interpretadas e/ou pré-compiladas no servidor web.

  [PHP](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/php/README.md)

- ***SGDB web:*** Para completar o processo de produção, assim como viabilizar sistemas completos, faz-se necessário a utilização de um ***sistema gerenciador de banco de dados específico com suporte para uso sobre um servidor web***.

  [MySQL Server](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/mysql/README.md)

- ***Servidor de compartilhamento de arquivos:*** Para facilitar o compartilhamento de arquivos *(principalmente na fase de desenvolvimento)* entre servidor e cliente de acesso, é usual implantar e implementar serviços de compartilhamento de arquivo *(multiplataforma)*.

  [Samba](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/samba/README.md)

- ***Servidor de Transferência de Arquivos:*** Como já feito desde os primórdios da Web, ***todo servidor web deve ter um sistema de FTP***.

  [VSFTPD (FTP)](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/ftp/README.md)

- ***Acesso remoto seguro:*** Assim como sistema de FTP, a utilização de um ***serviço de SSH também é obrigatória***.

  [SSH](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/ssh/README.md)

- ***Regras de firewall:*** Ao menos no ambiente do servidor web, é ***extremamente importante, criar e gerenciar as regras de firewall***.

  [UFW](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/firewall/README.md)

- ***Sistema Operacional:*** O Sistema operacional, em sua maioria, seguirá uma ***vertente de derivados de sistemas Unix***, como nosso caso, o Ubuntu Server 18.04.4 *(Linux)*.

  [Ubuntu Server 18.04.4](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/ubuntu_server/README.md)

- ***Sistema de Virtualização (Opcional):*** O sistema de virtualização, apesar de não serem obrigatório *(ainda que os principais sistemas web atualmente, esteja rodando sobre cloud, logo em ambiente virtual)*, ***podem ser usados em ambiente de testes*** (como por exemplo com auxílio de ferramentas específicas como [Docker](https://www.docker.com/) e/ou [Vagrant](https://www.vagrantup.com/))

  [VirtualBox 6.1](https://github.com/gismarb/atm_1s2020/blob/master/setup/ubuntu_18.04/virtualbox/README.md)

### Conclusão

O processo de ***desenvolvimento de um Workflow de um Servidor Web*** é demasiadamente complexo e heterogêneo, tendo em vista que muitas são as nuances que devem ser trabalhadas de forma sinérgica, para que se tenha sucesso ao final do trabalho. Devemos nos atentar, que em um ambiente corporativo, procedimentos automatizados poderão ser utilizados para optimizar os processos de desenvolvimento assim como utilização em produção. Mas, sobretudo, visando a criação de um ambiente, para que seja feito debug e/ou deploy de aplicações e soluções Web, é interessante construir o ambiente, visando todos os aspectos possíveis que serão colocados em produção, com os que já foram listados anteriormente *([Desenvolvimento](#desenvolvimento))*, simulando de fato o que se pode esperar em um grande provedor web. Desta forma, ***percebemos, que independente da plataforma, se é um ambiente de produção ou teste, se é um sistema e/ou aplicação web de pequeno ou grande porte, a linha base de projeto será sempre a mesma***.

### Referências

[VirtualBox](https://www.virtualbox.org/)

[VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.10/VirtualBoxSDK-6.1.10-138449.zip)

[Download VirtualBox for Linux Hosts](https://www.virtualbox.org/wiki/Linux_Downloads)

[Download Ubuntu Server 18.04.4](https://ubuntu.com/download/server/thank-you?version=18.04.4&architecture=amd64)

[Download ImgBurn](http://ultradownloads.com.br/download/ImgBurn/)

[Donwload Rufus](https://rufus.ie/)

[Download balenaEatcher](https://www.balena.io/etcher/)

[Como configurar endereço IP estático no Linux Ubuntu 18.04 com netplan](http://www.bosontreinamentos.com.br/linux/como-configurar-endereco-ip-estatico-no-linux-ubuntu-18-04-com-netplan/)

[OpenSSH](https://www.openssh.com/)

[Putty](https://www.putty.org/)

[Secure Shell](https://pt.wikipedia.org/wiki/Secure_Shell)

[SAMBA](https://www.samba.org/)

[SAMBA - Downloads](https://www.samba.org/samba/download/)

[SAMBA - Documentação](https://www.samba.org/samba/docs/)

[PHP](https://www.php.net/)

[PHP - Downloads](https://www.php.net/downloads)

[PHP - Documentação](https://www.php.net/docs.php)

[MySQL](https://www.mysql.com/)

[MySQL - Documentação (Instalação Geral)](https://dev.mysql.com/doc/refman/8.0/en/installing.html)

[MySQL - Documentação (Instalação via APT)](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/)

[VSFTPD.CONF](http://vsftpd.beasts.org/vsftpd_conf.html)

[VSFTPD](https://security.appspot.com/vsftpd.html)

[VSFTPD - Download](https://security.appspot.com/vsftpd.html#download)

[VSFTPD - Documentação](https://security.appspot.com/vsftpd.html#docs)

[FileZilla](https://filezilla-project.org/)

[Ubuntu - UFW](http://wiki.ubuntu-br.org/UFW)

[Ubuntu - Firewall](http://wiki.ubuntu-br.org/Firewall)

[UFW - Downloads](https://pkgs.org/download/ufw)

[Ubuntu - Repositórios UFW](https://ubuntu.pkgs.org/)

[Apache](https://httpd.apache.org/)

[Apache HTTP Server Version 2.4 Documentation](https://httpd.apache.org/docs/2.4/)

