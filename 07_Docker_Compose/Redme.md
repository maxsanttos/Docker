# Docker Compose

## O que é o Docker Compose?

* O **Docker Compose** é uma ferramenta para rodar múltiplos containers;

* Teremos apenas um arquivo de configuração, que orquestra totalmente esta situação;

* É uma forma de rodar **múltiplos builds e runs** com um comando;

* Em **projetos maiores** é essencial o uso do Compose;

## Instalando o Compose no linux

* **Usuários do Linux** ainda não possuem a ferramenta que utilizaremos nesta seção

* Vamos seguir as instruções de: <https://docs.doker.com/compose/install/>

* O **docker compose** é essencial para atingirmos os nossos objetivos no curso;

## Criando nosso arquivo de Compose

* Primeiramente vamos criar um arquivo chamado **docker-compose.yml** na raiz do projeto;

* Este arquivo vai **coordenar os containers e imagens**, e possui algumas chaves muito utilizadas;

* **Version:** versão do Compose;

* **services:** Containers/serviços que vão rodar nessa aplicação;

* **volumes:** Possível adição de volumes;

## Rodando o Compose

* Para rodar nossa estrutura em Compose vamos utlizar o comando **sudo docker compose up**;

* Isso fará com que as **instruções no arquivo sejam executadas**;

* Da mesma forma que realizamos os builds e também os runs;

* Podemos para o Compose com **ctrl+c** no terminal;

## Compose em background

* O compose também pode ser executado em modo **detached**;

* Para isso vamos utilizar a **flag -d** no comando;

* E então os contianers estarão **rodando em background**;

* Podemos ver sua execução com **docker ps**;

## Parando o Compose

* Podemos parar o Compose que roda em background com:**sudo docker compose down**;

* Desta maneira o serviço para e temos os containers adcionados no **sudo docker ps -a**;

## Variáveis de ambiente no Compose

* Podemos definir variáveis de ambiente para Docker Compose;

* Para isso vamos definir um arquivo base em **en_file**;

* As variáveis podem ser chamadas pela sintaxe: **${VARIAVEL}**

* Esta técnica é útil quando o dado a ser inserido é **sensível/não pode ser compartilhado**, como uma senha;

## Redes no Compose

* O Compose cria uma **rede básica Bridge** entre os containers da aplicação;

* Porém podemos isolar as redes com a chave **networks**;

* Desta maneira podemos concetar apenas os containers que optarmos;

* E podemos **definir drives diferentes** também;

## Criando o Compose do nosso projeto

* Agora vamos inserir o nosso projeto da última seção no Compose;

* Para verificar na prático como fazer uma transferência de **Dockerfiles para Docker Compose!**

## Build de imagens no Compose

* Podemos gerar o **build durante o Compose** também;

* Isso vai **eliminar o processo de gerar o build da imagem** a cada atualização;

* Vamos ver na prática!

## Volume bind mount no Compose

* O volume de **bind mount garante atualização em tempo real dos arquivos do container**;

* Podemos configurar nosso projeto de Compose para utilizar esta fucionalidade também;

* Vamos ver na prática!

## Verificando serviços do Compose

* Podemos fazer a verificação do compose com:**sudo docker-compose ps**

* Receberemos um **resumo dos serviços que sobem** ao rodar o compose;

* Desta maneira podemos avaliar rapidamente o projeto;
