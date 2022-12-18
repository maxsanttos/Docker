# KUBERNETES

## O que é Kubernetes?

* Uma ferramenta de **orquestração de containers**;

* Permite a criação de **múltiplos containers em diferentes máquinas (nodes)**;

* EScalando projetos, formando um **cluster**;

* Gerencia serviços, garantindo que as aplicações sejam executadas **sempre da mesma forma**;

* Criada pelo **Google**;

## COnceitos Fundamentais

* **Control Plane:** Onde é gerenciado o controle dos processos dos Nodes;

* **Nodes:** Máquinas que são gerenciados pelo Control PLane;

* **Deployment:** A execução de uma imagem/projeto em um Pod;

* **Pod:** um ou mais containers que estão em um Node;

* **Services:** Serviços que expõe os Pods ao mundo externo;

* **kubectl:** Cliente de linha de comando para o Kubernetes;

## Dependências necessárias

* O Kubernetes pode ser executado de uma maneira simples em nossa máquina;

* Vamos precisar do client,**kubectl**, que é maneira de executar o Kubernetes;

* E também o **Minikube, uma espécie de simulador de KUbernetes, para não precisarmos de vários computadores/servidores;

## Instalação Kubernetes no Windows

* Primeiramente vamos instalar o gerenciador de pacotes **chocolatey**;

* Depois seguiremos a documentação de instalação do **client de Kubernetes**;

* Devemos também instalar o **Virtualbox** (não é necessário se você tem o Hyper-V ou o Docker instalado);

* E por fim o **Minikube**;

* Na próxima aula vamos inicializar o Minikube!

## Instalação do Kubernetes no linux

* NO linux vamos instalar primeiramente o **client do Kubernetes**, seguindo a documentação;

* E depois também seguiremos a documentação do **MInikube**;

* Um dos requisitos do Minikube é ter um **gerenciador de VMs/containers** como:DOcker, Virtual box, Hiper-V;

* Na próxima aula vamos incializar o Minikube!

## Iniciando o Minikube

* Para inicializar o MInikube vamos utilizar o comando:**minikube start --driver=DRIVE**

* Onde o drive vai depender de como foi sua instalação das dependências, e por qualquer um deles atingiremos os mesmos resultados!

* Você pode tentar:**virtualbox, hyperv e docker**

* Podemos testar o Minikube com:**minikube status**

## Parando o Minikube

* **Obs:** sempre que o computador for reiniciado, deveremos iniciar o Minikube;

* E podemos pará-lo também com o comando:**minikube stop**

### todas as vezes devemos inicia lo

* Para iniciar novamente, digite:**minikube start --driver=DRIVER**

## Acessando a Dashboard

* O Minikube nos disponibiliza uma **dashboard**;

* Nela podemos ver todo o detalhamento de nosso projeto:**serviços,podes e etc**;

* Vamos acessar com o comando:**minikube dashboard**

* Ou para apenas obter a URL:**minibuke dashboard --url**

## Deployment na teoria

* O **Deployment** é uma parte fundamental do Kubernetes;

* Com ele criiamos nosso serviço que vai rodar nos **Pods**;

* **Definimos uma imagem e um nome**, para posteriormente ser replicado entre os servidores;

* A parte da criação do deployment teremos containers rodando;

* Vamos precisar de uma **imagem no Hub do Docker**, para gerar um Deployment;

## Criando nosso projeto

* Primeiramente vamos criar um pequeno projeto, novamente em **Flask**;

* Buildar a **imagem** do mesmo;

* Enviar a imgem para o **Docker Hub**;

* E testar rodar em um **container**;

* Este projeto será utilizado no **Kubernetes!**

## Criando o Deployment

* Após este mini setup é hora de rodar nosso projeto no **Kubernetes**;

* Para isso vamos precisar de um **Deployment**, que é onde rodamos os containers das aplicações nos **Pods**;

* O comando é:**kubectl create deployment NOME --image=IMAGE**

* Desta maneira o projeto de Flask estará sendo orquestrado pleo Kubernetes;

## Verificando deployments

* Podemos checar se tudo foi criado corretamente, tanto o **Deployment** quanto a recepção do projeto pelo **Pod**;

* Para verificar o Deployment vamos utilizar:**kubectl get deployments**

* E para receber mais detalhes deles:**kubectl describe deployments**

* Desta forma conseguimos **saber se o projeto está de fato rodando** e também **o que está rodando nele**;

## Checando pods

* Os **Pods** são componentes muito importantes também, onde os containers realmente são executados;

* Para verificar os Pods utilizamos:**kubectl get pods**

* E para saber mais detalhes deles:**kubectl describe pods**

* Recebemos **o status dos Pods** que estão ligados e também **informações impotantes sobre eles**;

## Configurações Kubernetes

* Podemos também verificar **como o kubernetes está configurado**;

* O comando é:**kubectl config view**

* No nosso caso: vamos receber informações importantes baseadas no **Minikube**, que é por onde o kubernetes está sendo executado;

## Services na teoria

* As aplicações do Kubernetes **não tem conexão com o mundo externo**;

* Por isso precisamos criar um **Service**, que é o que possibilita expor os Pods;

* Isso acontece pois os **Pods são criados para serem destruidos** e perderem tudo, ou seja, os dados gerados nele também são apagados;

* Então o **Service é uma entidade separada dos Pods**, que expõe eles a uma rede;

## Criando um Service

* Para criar um serviço e expor nosso Pods devemos utilizar o comando:
**kubectli expose deployment NOME --type=TIPO --port=PORTA**

* Colocaremos o nome do **Deployment** já criado;

* O **tipo de service**, há vários para utilizarmos, porém o **LoadBalancer** é o mais comum, onde todos os POds são expostos;

* E uma **porta** para o serviço ser consumido;

## Gerando um IP para o Service

* Podemos acessar o nosso serviço com o comando:**minikube service NOME**

* Desta forma o **IP aparece no nosso terminal**;

* E também **uma aba no navegador é aberta** com o projeto;

* E pronto! Temos um projeto rodando pelo **Kubernetes**!

## Verificando os nosso serviços

* Podemos também obter detalhes dos **Services já criados**;

* O comando para verifica todos é:**kubectl get services**

* E podemos obter informações de um serviço em específico com:**Kubectl describe services/NOME**

```docker
─max@pop-os ~  
╰─➤  kubectl get services   

NAME          TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
flaskdeploy   LoadBalancer   10.105.85.31   <pending>     5000:31214/TCP   7m44s
kubernetes    ClusterIP      10.96.0.1      <none>        443/TCP          16h

╭─max@pop-os ~  
╰─➤  kubectl describe service/flaskdeploy

Name:                     flaskdeploy
Namespace:                default
Labels:                   app=flaskdeploy
Annotations:              <none>
Selector:                 app=flaskdeploy
Type:                     LoadBalancer
IP Family Policy:         SingleStack
IP Families:              IPv4
IP:                       10.105.85.31
IPs:                      10.105.85.31
Port:                     <unset>  5000/TCP
TargetPort:               5000/TCP
NodePort:                 <unset>  31214/TCP
Endpoints:                172.17.0.5:5000
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>

```

## Escalando aplicação

* Vamos aprender agora a como utilizar outros Pods,**replicando assim a nossa aplicação**;

* O comando é:**kubectl scale deployment/NOME --replicas=NUMERO**

* Podemos agora verificar no **Dashboard** o aumento de Pods

* E também com o comando de:**kubectl get pods**

## Verificando número de réplicas

* Além do get pods e da Dashboard, temos mais um comando para **checar réplicas**

* Que é o:**kubectl get rs**

* Desta maneira temos os **status das réplicas** dos projetos;

## Diminuir número de réplicas

* Podemos facilmente também **reduzir o número de Pods**;

* Esta técnica é chamada de **scale down**;

* O comando é o mesmo, porém colocamos menos réplicas e o kubernetes faz o resto;

* Comando:**kubectl scale deployment/NOME --replicas=NUMERO_MENOR**

## Atualizando a imagem do projeto

* Para atualizar a imagem vamos precisar do **nome do container**, isso é dado na Dashboard dentro do Pod;

* E também a nova imagem deve ser uma outra versão da atual, **precisamos subir uma nova tag no Hub**;

* Depois o comando:**kubectl set imagem deployment/NOME NOME_CONTAINER=nova_imagem**

##