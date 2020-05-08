# Ubuntu Server 18.04: Procedimentos de Instalação e Configuração do Sistema Operacional

## Visão Geral



## Índice

- [Objetivo](##Objetivo)

- [Como Fazer](##Como-fazer)

- [Teste](Objetivo)

- 

  

## Objetivo

Promover o **download**, **instalação** e **configuração** do sistema operacional **Ubuntu Server 18.04**, de forma que o mesmo esteja disponível na rede, com um **IP estático pré-fixado** na rede onde o servidor estará funcionando.

## Como fazer

- **Download**: baixar a imagem *(ISO)* do sistema operacional no **Portal da Canonical** *([Ubuntu Server 18.04.4](https://ubuntu.com/download/server/thank-you?version=18.04.4&architecture=amd64))* que é mantenedora do projeto Ubuntu. ***Recomendamos sempre realizar os downloads de sites oficiais***;

- **Instalação**: 
  - **Gravar** arquivo **ISO** em um **CD**, **DVD** e/ou **pen drive**, utilizando algum tipo de programa para este fim, e de acordo com a plataforma que está utilizando para gravação. No Linux poderá ser usado `dd if=/local/arquivo.iso  of=/local/pen_drive bs=4M status=progress && sync `, já no Windows poderão usar programas como [ImgBurn](http://ultradownloads.com.br/download/ImgBurn/), [Rufus](https://rufus.ie/) e/ou [balenaEatcher](https://www.balena.io/etcher/);
  - **Instalar** o Sistema Operacional *(instalações em VMs ou máquinas físicas)*:
    - **Reiniciar** o servidor e iniciá-lo em modo Boot;
    - Inserir mídia *(CD, DVD e/ou pen drive bootável com ISO do S.O.)* ou apenas a ISO sobre unidade virtual;
    - **Escolha da língua**: Inglês *(padrão do Ubuntu Server)*;
    - **Configurações de teclado**: Portuguese *(Brazil)*;
    - **Conexões de rede**: utilizar neste momento o que for reconhecido pela Instalação *(posteriormente mudanças poderão ser realizadas neste ponto)*;
    - **Configurações de proxy**: passe a diante por este processo;
    - **Espelhos para repositórios**: padrão do momento da instalação do Ubuntu;
    - **Sistema de arquivo e particionamento**: ext4 / manual.
      - **Criar 5 partições:** *o processo de criação das partições deverá ser implementado apenas em uma máquinas físicas, em VMs, por questões de indisponibilidade de recurso e/ou uso de um ambiente para testes, deixar esta parte no padrão da instalação.*
        - Partição **/** com 40 GB: esta será a partição de sistema;
        - Partição **/home** com 40% do espaço em disco: esta será a partição dedica a área pessoal de cada usuário;
        - Partição ou arquivo **swap** com 4 GB: partição de de memória virtual para sistemas baseados em Unix;
        - Partição **/boot** ou **efi** com 500 MB:  partição onde é gravado o sistema de inicialização do sistema operacional;
        - Partição **/Data** com 40% do espaço em disco: partição onde será mapeada *(via link simbólico)* a pasta ***/var/www/html*** do Servidor Web.
    - **Criação de perfil de acesso**:  cadastrar credenciais de uma usuários *(com direitos administrativos)* e nomeando o servidor *(hostname)*;
    - **Instalação do SSH**: passe a diante por este processo *(faremos a instalação do SSH em outro momento)*;
    - **Pacotes SNAP**: neste momento não existe necessidade, passe a diante por este processo;
    - **Confirme as opções e deixe iniciar a instalação**;
    - **Faça atualizações de segurança**.

- **Configuração**:

  - Após a instalação do sistema estar concluída, o servidor será reiniciado. Tão logo o mesmo reinicie, entre com as credenciais de usuários e continue e realize as configurações iniciais de sistema:
    - **Atualizações de sistema via repositório**: `sudo apt update && sudo apt dist-upgrade -y && sudo apt upgrade -y`; 
  - **Instale um editor de texto**: `sudo apt install vim nano emacs` *(aqui, escolha um dos editores)*;
  - **Instale alguns pacotes necessários**: `sudo apt install htop curl wget neofetch git exuberant-ctags ncurses-term`;
  - **Configurar interfaces de rede *(placa de rede única)***: existem várias forma de fazer a configuração da rede no Ubuntu Server 18.04, mas a ideal é via **netplan** *(um serviço com fim de gerar configurações para interfaces de rede disponíveis)*. Quando o servidor é instalado pela primeira vez, ele por padrão, **está em modo DHCP**, logo é necessário **cadastrar um IP fixo para o mesmo**, como demais configurações necessárias.

