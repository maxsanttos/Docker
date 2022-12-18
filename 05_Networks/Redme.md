# Networks

## Erro ao instalar python-pip

fala galera!

alguns alunos relatam o erro:

**E:Package 'python-pip' has no installation candidate

caso tenham o mesmo problema:basta trocar o python-pip para pyhton3-pip

## O que são networks

**Uma forma de gerenciar a conexão do Docker** com outras plataformas ou até mesmo entre containers;

As redes ou networks são **criadas separadas do containes**. como os volumes;

Além disso existem alguns **drive de rede**, que veremos em seguinda;

Uma rede deica muito simples a comunicação entre contianers;

## Tipos de conexão

Os containers ter três principais tipos de comunicação:

**Externa:** conexão com uma API de um seridor remoto;

**Com o host:** comunicação com a máquina que está executando o Docker;

**Entre containers:** comunicação que utiliza o driver bridge e permite a comunicação entre dois ou mais containers;

## Tipos de Driver

**Bridge:** o mais comum e default do Docker, utilizado quando contianers precisam se conectar (na maioria das vezes optamos por este driver);

**host:** permite a conexão entre um contianer a máquina que está hosteando o Docker;

**macvlan:** permite a conexão a um contianer por um MAC address;

**none:** remove todas conexões de rede de um container(ou null);

**plugins:** permite extensões de terceiros para criar outras redes;

## Listando networks

Podemos verificar todas as redes do nosso ambiente com: **sudo docker network ls**;

**Algumas redes já estão criadas**, estas fazem parte da configuração inicial do docker;

## Criando redes

Para criar uma ede vamos utilizar o comando docker **sudo docker network create nome**;

Esta rede será do tipo **bridge**, que é o mais utilizado

## Removendo redes

Podemos remover redes de forma simples também:**sudo docker network rm nome**;

Assim **a rede não estará mais disponível** para utilizarmos;

Devemos tomar cuidado com contianers já conectados;

## Removendo redes em massa

Podemos remover redes de forma simples também:**sudo docker network prune**;

Assim **todas as redes não utilizadas** no momento serão removidas;

Receberemos uma mensagem de confirmação do Docker antes da ação ser executada;

## Instalando o Postman

Vamos criar uma **API** para testar a conexão entre containers;

Para isso vamos utilizar o software **Postman**, que é o mais utilizado do mercado para desenvolvimento de APIs;

Lik:**<https://www.postman.com/>**

## Conexão externa

Os containers **podemos se conectar livremente ao mundo externo**;

Um caso seria: uma API de código aberto;

Podemos acessá-la livremente e utilizar seus dados;

vamos testar!

## Conexão com o host

Podemos também **conectar um contianer com o host do Docker**;

**Host** é a máquina que está executando o Docker;

Como ip de host utilizamos:**host.docker.internal**

No caso pode ser a nossa mesmo! =)

## Conexão entre containers

Podemos também estabelecer uma **conexão entre containers**;

Duas imagens distintas rodando em **containers separados que precisam se conectar para inserir um dado no banco**, por exemplo;

Vamos precisar de uma rede **bridge**, para fazer esta conexão;

Agora nosso container de flask vai inserir dados em um MYSQL que roda pelo Docker também;

## Conctando um container a uma rede

Podemos conectar um container a uma rede;

Vamos utilizar o comando **sudo docker network connect rede id_container**

Após o comando o contianer estará dentre da rede!

## Desconectando um contianer

Podemos desconectar um container a uma rede também;

Vamos utilizar o comando **sudo docker network disconnect rede id_container**

Após o comando o contianer estará fora da rede!

## Inspecionando redes

Podemos analisar os detalhes de uma rede com o comando: **sudo docker network inspect nome**

Vamos receber informações como: data de criação, driver, nome e muito mais!
