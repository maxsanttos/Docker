# O que é Docker ?

O **Docker** é um software que **reduz a complexidade de setup** de aplicações;
Onde **configuramos containers**, que são como servidores para rodar nossas aplicações;
Com facilidade,podemos criar **ambiente independentes** e que funcionam em diversos SO's;
E aindaa deixa os projetos **performáticos**;

## Por quê Docker ?

* O **Docker** proporciona mais velocidade na configuração do ambiente de um dev;

* **Pouco tempo gasto em manutenção**, containers são executados como configurados;

* **Performance** para executar aplicação, mais performático que uma VM ;

* Nos livra da **Matrix from Hell**;

## Qual é a versão utilizar?

* O **Docker** é dividido em duas versões: **CE X EE**

* CE é a **Community Edition**, edição gratuita, que nos possibilita utilizar o Docker nomalmente, é a que vamos optar;

* EE é a **Enterpris Edition**, edição paga, há uma garantia maior das ersões que disponibiliza e você tem suporte do time do Docker;

## Instalação Windows

Para WIndows vamos instalar um software chamado **Docker Descktop**;

Com ele virá a possibilidade também de rodar **Docker no terminal**, que é onde aplicaremos a maioria dos comandos durante o curso;

Docker Descktop é uma **interface** para trabalhar com o Docker;

Obs: Há duas versões, a que você vai instalar **depende da versão do seu Windows**;

## Instalação Docker Mac

Para Mac vamos instalar um software chamado **Docker Descktop**;

Com ele virá a possibilidade também de rodar **Docker no terminal**, que é onde aplicaremos a maioria dos comandos durante o curso;

Docker Descktop é uma **interface** para trabalhar com o Docker;

Este software é o mesmo que utilizamos no WIndows;

## Instalação Docker linux

Para **Linux** vamos precisar escolher a versão baseada em nossa distribuição;

Vamos precisar **executar comando no ternimal**, seguindo a documentação;

Desta maneira teremos o Docker disponível;

### Uninstall old versions

```docker
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### Installation methods

``` docker

sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Add Docker’s official GPG key:

``` docker
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Use the following command to set up the repository:

```docker
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine

Update the apt package index, and install the latest version of Docker Engine, containerd, and Docker Compose, or go to the next step to install a specific version:

```docker
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

To install a specific version of Docker Engine, list the available versions in the repo, then select and install:

a. List the versions available in your repo:

```docker
apt-cache madison docker-ce
```

Install a specific version using the version string from the second column, for example, 5:20.10.16~3-0~ubuntu-jammy.

```docker
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```

Verify that Docker Engine is installed correctly by running the hello-world image

```docker
sudo service docker start
sudo docker version
```

This command downloads a test image and runs it in a container. When the container runs, it prints a message and exits.

## Problemas de Instalação

Caso você não conseguiu instalar, por algum erro ou incompatibilidade visite o site: <https://docs.docker.com/get-docker/>

Nele há um guia para **cada sistema operacional** e também por distribuição de Linux;

Infelizmente ainda não há uma maneira global e única de instalar o docker;

## Editor de código do curso

* Neste curso vamos utilizar o **VS Code**;

* Ele possui um **terminal integrado**, o que ajuda muito a trabalhar com o Docker;

* Além de ser, provavelmente, o **mais utilizado** em empresas atualmente;

* OBS: é opcional;

## Extensão Docker do VS Code

* A **extensão de Docker** na VS Code vai ajudar a criar código para arqivos de Docker no editor;

* Esta extensão **sugere código (auto complete)** e também trás um **highlight** que ajuda a programar aquivos Docker;

* Vamos **Escrever nossas imagens** com ajuda dela e do VS Code;

## Terminal no Windows

* Caso você opte **por não utilizar o VS Code**, vai precisar de uma  forma de rodar comandos no terminal;

* A opção mais interessante é o **Cmder**;

* Este software simula um terminal de Linux, aceitando todos os comandos compatíveis com o Docker também.

## Rodando um container no Docker

* Vamos testar o Docker utilizando uma **imagem real**;

* Para rodar containers utilizamos o comando **docker run**;

* Neste comando **podemos passar diversos parâmentros**;

* Neste exemplo vamos passar apenas o nome da imagem que é **docker/whalesay**

* Um comando chamado cowsay e uma mensagem;
