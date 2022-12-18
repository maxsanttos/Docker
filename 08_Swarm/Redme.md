# Docker Swarm

## O que é orquestração de containers?

* Orquestração é o ato conseguir **gerenciar e escalar** os containers da nossa aplicação;

* Temos **um serviço que rege sobre outros serviços**, verificando se os mesmos estão funcinando como deveriam;

* Desta forma conseguimos garantir uma aplicação saudável e também que esteja sempre disponível;

* Alguns serviços:**Docker Swarm, Kubernetes e Apache Mesos**;

## O que é Docker Swarm

* Uma ferramenta do Docker para **orquestrar containers**;

* Podendo **escalar horizontalmente** nossos projetos de maneira simples

* O famoso **cluster**!

* A **facilidade do Swarm** para outros orquestradores é que todos os comandos são muitos semelhantes ao do Docker!

* Toda instalação do Docker já vem com o Swarm, **porém desabilitado**;

## Conceitos fundamentais do Swarm

* **Nodes:** é uma instância (máquina) que participa do Swarm;

* **Manager Node:** NOde que gerencia os demais Nodes;

* **Worker Node:** Node que trabalham em função do Manager;

* **Service:** Um conjunto de Tasks que o Manager Node manda o WOrk node executar;

* **Task:** comandos que são executados nos Nodes;

## Maneiras de executar o Swarm

* Para exemplificar corretamente o Swarm vamos precisar de NOdes, ou seja , **mais máquinas**;

* Então temos duas soluções;

* **AWS**, criar a conta e rodar alguns servidores(precisa de cartão de crédito,mais é gratuito);

* **Docker Labs**, gratuito também, roda no navegador, porém expira a cada 4 horas;

## Iniciando o Swarm

* Podemos iniciar o Swarm com o comando: **docker suwarm init**;

* Em alguns casos precisamos declarar o IP do servidor com a flag **--advertise-addr**

* Isso fará com que a instância/máquina vire um **Node**;

* E também transforma o Node em um **Manager**;

## Listando todos os Nodes

* Podemos verificar quais Nodes estão ativos:**docker node ls**

* Desta forma os serviços serão exibidos no terminal;

* Podemos assim **monitorar o que o Swarm está orquestrando**;

* Este comandoserá de grande utilidade a medida que formos adicionando serviços no Swarm;

## Adicionando novos Nodes

* Podemos adicionar um novo serviço com o comando:**docker swarm join --token TOKEN IP:PORTA**

* Desta forma duas máquinas estarão conectadas;

* Esta nova máquina entra na hierarquia com **Worker**;

* Todas as ações (**Tasker**) utilizada na MAnager, serão replicadas em Nodes que foram adcionados com join;

## Subindo serviços no Swarm

* Podemos iniciar um seriço com o comando: **docker service create --name NOME IMAGE**

* Desta forma teremos um container novo sendo adicionado ao nosso Manager;

* E este serviço estará sendo gerenciado pelo Swarm;

* Podemos testar com o nginx. **liberando a porta 80** o container já pode ser acessado;

## Verificando serviços rodando no Swarm

* Podemos listar os serviços que estão rodando com: **docker service ls**

* Desta maneira todos os serviços que iniciamos serão exibidos;

* Algumas informações importante sobre eles estão na tabela: **nome, replicas, imagem,porta**;

## Removendo serviços

* Podemos remover um seriço com: **docker service rm nome**

* Desta maneira o serviço para de rodar;

* Isso pode significar:**parar um container que está rodando** e outras consequências devido a parada do mesmo;

* Checamos a remoção com: docker service ls;

## Aumentando o número de réplicas

* Podemos criar um serviço com um número maior de réplicas:**docker service create --name NOME --replica NUMERO IMAGEM

* Desta maneira uma task será emitida, replicando este serviço nos Workers;

* Podemos checar o status com: docker service ls;

## Testando a orquestração do Swarm

* Vamos remover um container de um **Node worker;**

* Isso fará com que o Swarm reinicie este container novamente;

* Pois o serviço ainda está rodando no **Manager**, e isto é uma de suas atribuições:**garantir que os serviços estejam sempre disponíveis**;

* Obs: precisamos utilizar o force (-f);

## Recuperando o token do Manage

* As vezes vamos precisar checar o token do Swarm, **para dar join em alguma outra instância futuramente**;

* Então temos o comando:**docker swarrm join-token manager**

* Desta forma recebemos o token pelo terminal;

## Checando o Swarm

* Podemos verificar detalhes do Swarm que o Docker está utilizando;

* Utilizamos o comando:**docker info**;

* Desta forma recebemos informações como:**ID do Node, número de nodes, números de managers e muito mais!**

## Deixar o Swarm em um Node

* Podemos parar de executar o Swarm em uma determinada instância também;

* Vamos utilizar o comando:**docker swarm leave**

* A partir deste momento, **a instância não é contada mais como um Node para o Swarm**

## Removendo um Node

* Podemos também remover um NOde do nosso ecossistema do Swarm;

* Vamos utilizar o comando:**docker node rm ID**

* **Desta forma a instância não serpa considerada mais um Node**, saindo do Swarm;

* O container continuará rodando na istância;

* Precisamos utilizar o -f

## Inspecionando serviços

* Podemos ver em mais detalhes o que um serviço possui;

* O comando é:**docker service inspect ID**

* Vamos receer informções como:**nome, data de criação, portas e etc;**

## Verificado containers ativos pelo service

* Podemos ver quais containers um serviço já rodou:

* O comando é:**docker service ps ID**

* Receberemos uma lista de containers que estão rodando e também dos que já receberam baixa;

* este comando é **semelhante ao docker ps -a**

## Rodando compose com swarm

* Para rodar compose com swarm vamos utilizar os comando de stack;

* O comando é:**docker stack deploy -c ARQUIVO.YAML NOME**

* Teremos então o **arquivo compose** sendo executado;

* Porém agora estamos em modo swarm e podemos utilizar os Nodes como réplicas;

## Escalando nossa aplicação

* Podemos criar novas réplicas nos **Worken Nodes**;

* Vamos utilizar o comando:**docker service scale NOME=REPLICAS**

* Desta forma as outras máquinas receberão as Tasks a serem executadas;

## Parar de receber Tasks em um Node

* Podemmos fazer com que serviço **não receba mais 'ordens' do Manager**;

* Para isso vamos utilizar o comando:**docker node update --availability drain ID**

* O status de drian, é o que não recebe tasks;

* Podemos voltar para **active**, e ele volta ao normal;

## Atualizando uma imagem no Swarm

### Atualizar parâmetro

* Podemos atualizar as configurações dos nossos nodes;

* Vamos utilizar o comando:**docker srvice update --image IMAGEM SERVICO**

* Desta forma apenas os nodes que estão com o status **active** receberão atualização;

## Criando redes para serviços do Swarm

* A conexão entre instâncias usa um driver diferente, o **overlay**;

* Podemos criar primeiramente a rede com **docker network create**;

* E depois ao criar um service adicionar a flag **--network REDE** para inserir as instâncias na nossa nova rede;

## Conectando serviço a uma rede já existente

Podemos também concetar serviços que já estão em execução a uma rede;

Vamos utilizar o comando de update:**docker service update --network REDE NOME**

Depois checamos o resultado com **inspect**
