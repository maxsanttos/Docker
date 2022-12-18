# Trabalhando com Container

## O que são containers ?

* Um **pacote de código que pode executar uma ação**, por exemplo: rodar uma aplicação de Node.js, PHP,Python e etc;

* Ou seja, os nossos projetos serão executados dentro dos containers que criamos/utilizamos;

* **Containers utilizamos imagens** para poderem ser executados;

* Mútiplos containers podem rodar juntos**, exemplos: um para PHP e outro para MySQL;

## Container X imagem

* **Imagem e Container** são recursos fundamentais do Docker;

* Imagem é o **"projeto"** que será executado pelo container, todas as instruções estarão declaradas nela;

* Container é o **Docker rodando alguma imagem**, consequentemente executando algum código proposto por ela;

* O fluxo é: programamos uma imagem e a executamos por meio de container;

## Onde encontrar imagens ?

Vamos encontrar imagens no repositório do Docker:
<https://hub.docker.com>

Neste site podemos **verificar quais as imagens existem** da tecnologia que estamos procurando, por exemplo:Nodejs;

E também **aprender a como utilizá-las**;

Vamos executar uma imagem e um container com o comando:

```docker
docker run <nome_imagem>
```

* Baixamos a imagem do Ubuntu e rodamos com o comando:

```docker

// Baixa a imagem 
sudo docker pull ubuntu

// apenas roda a imagem ou baixa se não tiver 
sudo docker run ubuntu

// roda a imagem e entra no terminal interativo
sudo docker run -it ubuntu
```

* Para ver se o container está rodando utilizamos o comando

```docker
sudo docker ps

```

## Verificar containers executados

* O comando **docker ps ou docker container ls** exibe quais containers estão sendo executados no momento;

* Utilizamos a **flag -a** temos também todos os containers já executados na máquina;

* Este comando é útil para **entender o que sendo exeutado e acontece** no nosso ambiente;

```docker
sudo docker ps -a
```

## Rodando container no modo interativo

* Podemos rodar um container e deixá-lo **executando no terminal**;

* Vamos utilizar a **flag -it**;

* Desta maneira **podemos executar comandos disponíveis no container** que estamos utilizado o comando run;

* Podemos utilizar a imagem do ubuntu para isso!

```docker
sudo docker run -it node

sudo docker run -it ubuntu
```

## Container X VM (Virtual Machine)

* **Container é uma aplicação que serve para um determinado fim**, não possui sistema operacional, seu tamanho é de alguns mbs;

* VM possui sistema operacional própria, tamanho de gbs, **pode executar diversas funções ao mesmo tempo**;

* Containers acabam gastando menos recursos para serem executados, por causa do seu específico;

* VM gastam mais recursos, porém podem exercer mais funções;

## Executar container em background

* Quando iniciamos um container que persiste, **ele fica ocupando o terminal**;

* Podemos executar um container em backgroud, para não precisar ficar com diversas abas de terminal aberto, utilizamos a **flag -d**(detached);

* Verificamos **containers em background com docker ps** também;

* Podemos utilizar o nginx para este exemplo!

## Expor portas

* Os **containers de docker não tem conexão com nada de fora deles;

* Por isso precisamos expor portas, a **flag é a -p** e podemos fazer assim: *p 80:80;

* Desta maneira **o container estará acessível na porta 80**;

* Podemos testar este exemplo com o nginx!

## Parando containers

* Podemos parar um container com o comando **docker stop <id_ou_nome>**;

* Desta maneira estaremos liberando recurso ue estão sendo gastos pelos mesmo;

* Podemos verificar os containers rodando com o comando **docker ps**;

## Reiniciando containers

* Aprendemos já a parar um container com o stop, para voltar a rodar um container podemos usar o comando **docker start <id_imagem>;

* Lembre-se que **o run sempre cria um novo container**;

* Então caso seja necessário aproveitar um antigo, opte pela start;

## Definindo nome do container

* Podemos definir um nome do container com a flag **--name**;

* Se não colocamos, **recebemos um nome aleatório**, que pode ser um problema para uma aplicação profissional;

* A flag run é inserida junto do **comando run**;

```docker
sudo docker run -d -p 80:80 --name ngixn_app ngixn
```

## Acessando os logs de um container

* Podemos **verificar o que aconteceu em um container** com o comando logs;

* Utilizamos da seguinde maneira: **docker logs id**;

* As últimas ações realizadas no container, serão **exibidas no terminal**;

## Removendo container

* Podemos **remover um container da máquina** que estamos executando o Docker;

* O comando é **sudo docker rm id**;

* Se o container estiver rodando ainda, podemos utilizar a **flag -f**(force);

* O container removido não é mais listado em docker ps -a;
