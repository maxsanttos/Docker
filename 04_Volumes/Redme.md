# Volumes

## O que são volumes

Uma **forma prática de persistir dados** em aplicações e não depender de containers para isso;

**Todo dado criado por um container é salvo nele**,quando o container é removido perdemos os dados;

Então precisamos dos volumes para gerenciar os dados e também conseguir **fazer backups** de forma mais simples;

## Tipos de volumes

**Anônimos(anonymous):** Diretórios criados pela flag -V, porém com um nome aleatório;

**Nomeados(named):** ão volumes com nomes, podemos nos referir a estes facilmente e saber para que são utilizados no nosso ambiente;

**Bind mounts:** Uma forma de salvar dados na nossa máquina, sem o gerenciamento do Docker, informamos um diretório para este fim;

## Criando o projeto para trabalhar com Volumes

* Se criarmos um container com alguma imagem,**todos os arquivos que gerenciamos dentro dele serão do container**;

* Quando o container for removido, perderemos estes arquivos;

* Por isso precisamos os **volumes**;

* Vamos criar um exemplo prático!

## Problema da persistência de dados

Podemos criar um volume anônimo(**anonymous**) da seguinte maneira:
**sudo run -v /data**

Onde **/data** será o diretório que contém o volume anônimo;

E este container estará atrelado ao volume anônimo

Com o comando **sudo docker volume ls**, podemos ver todos os volumes do nosso ambiente;

## Volumes nomeados

Podemos criar um volume nomeado (**named**) da seguinte maneira: **sudo docker run -v nomedovolume:/data**

Agora o volume tem nome e pode ser facilmente referenciado;

Em **sudo docker volume ls** podemos verificar o container nomeado criado;

Da mesma maneira que o anônimo, este volume tem como função armazenar arquivos;

## Bind mounts

**Bind mount** também é um volume, porém ele fica em um diretório que nós especificamos;

Então não criamos um volume em sim, **apontamos um diretório**;

O comando para criar um bind mount é:**sudo docker run /dir/data:/data**

Desta maneira o diretório **/dir/data** no nosso computador, será o volume deste container;

## O poder extrar do Bind Mount

**Bind mount** não serve apenas para volumes!

Podemos utilizar esta técnica para **atualização em tempo real do projeto**;

Sem ter que refazer o build a cada atulização do mesmo;

Vamos ver na prática!

## Criando volumes manualmente

Podemos criar volumes manualmente também;

Utilizamos o comando: **sudo docker volume create nome**

Desta maneira temos um **named volume** criado, podemos atrelar a algum container na execução do mesmo;

## Listando volume

Com o comando: **sudo docker ls** listamos todos os volumes;

Desta maneira temos acesso aos **anonymous e os named volumes**;

Interessante ara saber quais volumes estão criados no nosso ambiente;

## Inspecionando volumes

Podemos verificar os detalhes de um volume em específico com o comando: **sudo docker volume inspect nome**;

Desta forma temos acesso ao **local em que o volume guarda dados**, nome, escopo e muito mais;

O docker salva os dados dos volumes em algum diretório do nosso computador, desta forma podemos saber qual é;

## Removendo volumes

Podemos também remover um volume existente de forma fácil;

Vamos utilizar o comando: **sudo docker volume rm nome**;

Obeserve que **os dados serão removidados todos também**, tome cuidado com este comando;

## Removendo volumes não utilizados

Podemos **remover todos os volumes que não estão sendo utilizados** com apenas um comando;

O comando é:**sudo docker volume prune**

Semelhante ao prune que remove imagens e containers, visto anteriormente

## Volume apenas de leitura

Podemos criar um volume que tem **apenas permissão de leitura**, isso é útil em algumas aplicações;

Para realizar esta configuração devemos utilizar o comando:**sudo docker run -v volume:/data:ro**

Esta **:ro** é a abreviação de read only;
