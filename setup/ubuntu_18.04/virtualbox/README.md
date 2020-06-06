# VirtualBox 6.1: Procedimentos de Instalação e Configuração do Sistema de Virtualização



## Objetivo

Promover o **download**, **instalação** e **configuração** do sistema virtualização **VirtualBox 6.1**, e, desta forma, disponibilizando um ambiente virtual para emular uma máquina física.

## Como fazer

#### **Download**: 

- **Microsoft Windows:**  baixar o VirtualBox diretamente no **Portal da Oracle** *([VirtualBox 6.1](https://www.virtualbox.org/))* a versão sugerida para  este estudo *(e/ou uma versão mais atual)*.  Como recurso opcional, também poderá ser baixado o os pacotes de extensão da da ferramenta *([Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.6/Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack))*.

- **Linux:** em  uma **distro Linux** *(no nosso caso, o Pop!_OS 20.04 LTS)*, faremos a instalação pelo repositório da distribuição via **apt** *(o Pop!_OS é uma distro derivada do Ubuntu, e assim como o mesmo, utiliza o gerenciador de pacotes apt para realizar a instalação de programas presentes no repositório oficial da distribuição)*.

#### Instalação: 

- **Microsoft Windows:**  o processo de instalação compreende-se, basicamente, **no processo padrão de instalação de programas no Windows**. Apenas execute o arquivo *(dependendo da versão do Windows e/ou configuração, usar a opção "Executar como Administrador")* de instalação (*que foi baixado do site oficial do VirtualBox)*, que deverá ser uma arquivo com nome:

   `VirtualBox-6.1.8-137981-Win.exe`

  Sendo que **esta descrição poderá mudar de acordo com a versão do VirtualBox que foi utilizada na instalação** *(em nosso caso, é a versão 6 e suas builds)*.

  Por fim, também deverá ser instalado o pacote de extensões de funções do VirtualBox *(criam uma interação melhorada entre a virtualização e o sistema operacional hospedeiro)*, no mesmo processo padrão, anterior, executando o arquivo:

  `Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack`

- **Linux:** como já repassado, anteriormente, estamos utilizando, como base para este estudo, o **Pop!_OS 20.04 LTS** *(como máquina host para a virtualização)*. Neste ponto,  o processo de instalação (tanto do VirtualBox, quanto do pacote de extensões), ocorre da seguinte forma: 

  `sudo apt install virtualbox -y`

  `sudo apt install virtualbox-ext-pack`
  
  Para instalar o VirtualBox em outras distros Linux, por favor, consultem os repositórios oficiais de cada distribuição, ou acessem a área de downloads para Linux, no site oficial do VirtualBox *(https://www.virtualbox.org/wiki/Linux_Downloads)*, para verificar a forma de instalação para sua referida distribuição.

#### Configuração:

Neste ponto, não existem diferenças *(exceto em casos específicos que não se aplicam ao estudo corrente)* para utilização do VirtualBox na criação do ambiente virtual. Desta forma, todos os passos demonstrados daqui para frente, poderão ser executado em ambos os sistemas operacionais *(Linux e Windows)*.

Basicamente, o **processo consiste em criar um máquina virtual** *(VM)* parte da construção de um computador *(porém virtual)*, onde iremos definir processador, disco, memória, etc, tudo que é necessário em um computador *(conforme demonstrado abaixo)*. 

![1](../atm_1s2020/images/1_criando_vm.gif)



**Detalhes da VM *(configurações mínimas)*:**

- 1 GB de memória RAM;
- 10 GB de armazenamento *(HDD)*;
- De preferência, prefira a opção de alocação dinâmica para o disco;
- Escolha o local onde o arquivo de disco será criado *(representação do HDD, que em nosso caso é um arquivo)*;
- Para o formato do disco, escolha o padrão VDI;
- Reserve ao menos um *(1)* núcleo do processador físico para utilização da VM;
- Informe, nas configurações da VM, o local onde está o arquivo ISO, para instalação do Sistema Operacional;

Após a criação da VM, já será possível realizar o início da mesma *(clicando em Start)* e realizando a instalação do Sistema Operacional **Ubuntu Server 18.04.4** *(que será nosso sistema operacional para criação do Servidor Web)*.

## Referências

[VirtualBox](https://www.virtualbox.org/)

[VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.10/VirtualBoxSDK-6.1.10-138449.zip)

[Download VirtualBox for Linux Hosts](https://www.virtualbox.org/wiki/Linux_Downloads)

