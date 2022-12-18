# Criando imagens e avançado em containers

## O que é uma imagens?

* Imagens **são originadas de arquivos que programamos** para que o Docker crie uma estrutura que execute determinadas ações em containers;

* Elas contém informações como: imagens base, diretório base, comandos a serem executados, porta da aplicação e etc;

* Ao rodar um contianer baseado na imagem, **as instruções serão executadas em camadas**;

## Como escolher uma imagens

* Podemos fazer download das imagens em: <https://hub.docker.com>;

* Porém **qualquer um pode fazer upload de uma imagem**, isso é um problema;

* Devemos então nos atentar as **imagens oficiais**;

* Outro parâmetro interessante é a **quantidade de downloads** e a **quantidade de stars**;

## Criando a nossa primeira imagem

* Para criar uma imagem vamos precisar de um arquivo **Dockerfile** em uma pasta que ficará o projeto;

* Este arquivo vai precisar de algumas instruções para poder ser executado;

---------------------

* **FROM**: imagem base;
* **WORKDIR**: diretório da aplicação;
* **EXPOSE**:porta da aplicação;
* **COPY**: quais arquivos precisam ser copiados;

## Executando uma imagem

* Para executar a imagem primeiramente **vamos precisar fazer o build**;

* O comando é **sudo docker build diretório da imagem**;

* Depois vamos utilizar o **sudo docker run imagem** para executá la;

## Alterado uma imagem

* Sempre que alterarmos o código de uma imagem **vamos precisar fazer o build novamente**;

* Para o Docker é como se fosse **uma imagem completamente nova**;

* Após fazer o build vamos executá-la por o outro id único criada com o docker run;

## Cache de camandas

* As imagens do Docker são divididas em **camadas**(layers);

* Cada instrução no Dockerfile **representauma layer**;

* Quando algo é atualizado **apenas as layers depois da linha atualizada são refeitas**;

* O resto permanece em cache, tornando o **build mais rápido**;

## Download de imagens

* Podemos **fazer o download de alguma imagem do hub e deixá-la disponével em nosso ambiente;

* Vamos utilizar o comando **sudo docker pull imagem**;

* Desta maneira, caso se use em outro container, **a imagem já estará pronta para ser utilizada**;

## Aprender mais sobre os comandos

* Todo comando no docker tem acesso a uma **flag --help**;

* Utilizando desta maneira, **podemos ver as opções disponíveis nos comandos**;

* Para relembrar algo ou executar uma tarefa diferente com o mesmo;

* Ex:**docker run --help**;

```docker
Options:
      --add-host list                  Add a custom host-to-IP mapping (host:ip)
  -a, --attach list                    Attach to STDIN, STDOUT or STDERR
      --blkio-weight uint16            Block IO (relative weight), between 10 and
                                       1000, or 0 to disable (default 0)
      --blkio-weight-device list       Block IO weight (relative device weight)
                                       (default [])
      --cap-add list                   Add Linux capabilities
      --cap-drop list                  Drop Linux capabilities
      --cgroup-parent string           Optional parent cgroup for the container
      --cgroupns string                Cgroup namespace to use (host|private)
                                       'host':    Run the container in the Docker
                                       host's cgroup namespace
                                       'private': Run the container in its own private
                                       cgroup namespace
                                       '':        Use the cgroup namespace as
                                       configured by the
                                                  default-cgroupns-mode option on the
                                       daemon (default)
      --cidfile string                 Write the container ID to the file
      --cpu-period int                 Limit CPU CFS (Completely Fair Scheduler) period
      --cpu-quota int                  Limit CPU CFS (Completely Fair Scheduler) quota
      --cpu-rt-period int              Limit CPU real-time period in microseconds
      --cpu-rt-runtime int             Limit CPU real-time runtime in microseconds
  -c, --cpu-shares int                 CPU shares (relative weight)
      --cpus decimal                   Number of CPUs
      --cpuset-cpus string             CPUs in which to allow execution (0-3, 0,1)
      --cpuset-mems string             MEMs in which to allow execution (0-3, 0,1)
  -d, --detach                         Run container in background and print container ID
      --detach-keys string             Override the key sequence for detaching a container
      --device list                    Add a host device to the container
      --device-cgroup-rule list        Add a rule to the cgroup allowed devices list
      --device-read-bps list           Limit read rate (bytes per second) from a
                                       device (default [])
      --device-read-iops list          Limit read rate (IO per second) from a device
                                       (default [])
      --device-write-bps list          Limit write rate (bytes per second) to a device
                                       (default [])
      --device-write-iops list         Limit write rate (IO per second) to a device
                                       (default [])
      --disable-content-trust          Skip image verification (default true)
      --dns list                       Set custom DNS servers
      --dns-option list                Set DNS options
      --dns-search list                Set custom DNS search domains
      --domainname string              Container NIS domain name
      --entrypoint string              Overwrite the default ENTRYPOINT of the image
  -e, --env list                       Set environment variables
      --env-file list                  Read in a file of environment variables
      --expose list                    Expose a port or a range of ports
      --gpus gpu-request               GPU devices to add to the container ('all' to
                                       pass all GPUs)
      --group-add list                 Add additional groups to join
      --health-cmd string              Command to run to check health
      --health-interval duration       Time between running the check (ms|s|m|h)
                                       (default 0s)
      --health-retries int             Consecutive failures needed to report unhealthy
      --health-start-period duration   Start period for the container to initialize
                                       before starting health-retries countdown
                                       (ms|s|m|h) (default 0s)
      --health-timeout duration        Maximum time to allow one check to run
                                       (ms|s|m|h) (default 0s)
      --help                           Print usage
  -h, --hostname string                Container host name
      --init                           Run an init inside the container that forwards
                                       signals and reaps processes
  -i, --interactive                    Keep STDIN open even if not attached
      --ip string                      IPv4 address (e.g., 172.30.100.104)
      --ip6 string                     IPv6 address (e.g., 2001:db8::33)
      --ipc string                     IPC mode to use
      --isolation string               Container isolation technology
      --kernel-memory bytes            Kernel memory limit
  -l, --label list                     Set meta data on a container
      --label-file list                Read in a line delimited file of labels
      --link list                      Add link to another container
      --link-local-ip list             Container IPv4/IPv6 link-local addresses
      --log-driver string              Logging driver for the container
      --log-opt list                   Log driver options
      --mac-address string             Container MAC address (e.g., 92:d0:c6:0a:29:33)
  -m, --memory bytes                   Memory limit
      --memory-reservation bytes       Memory soft limit
      --memory-swap bytes              Swap limit equal to memory plus swap: '-1' to
                                       enable unlimited swap
      --memory-swappiness int          Tune container memory swappiness (0 to 100)
                                       (default -1)
      --mount mount                    Attach a filesystem mount to the container
      --name string                    Assign a name to the container
      --network network                Connect a container to a network
      --network-alias list             Add network-scoped alias for the container
      --no-healthcheck                 Disable any container-specified HEALTHCHECK
      --oom-kill-disable               Disable OOM Killer
      --oom-score-adj int              Tune host's OOM preferences (-1000 to 1000)
      --pid string                     PID namespace to use
      --pids-limit int                 Tune container pids limit (set -1 for unlimited)
      --platform string                Set platform if server is multi-platform capable
      --privileged                     Give extended privileges to this container
  -p, --publish list                   Publish a container's port(s) to the host
  -P, --publish-all                    Publish all exposed ports to random ports
      --pull string                    Pull image before running
                                       ("always"|"missing"|"never") (default "missing")
      --read-only                      Mount the container's root filesystem as read only
      --restart string                 Restart policy to apply when a container exits
                                       (default "no")
      --rm                             Automatically remove the container when it exits
      --runtime string                 Runtime to use for this container
      --security-opt list              Security Options
      --shm-size bytes                 Size of /dev/shm
      --sig-proxy                      Proxy received signals to the process (default true)
      --stop-signal string             Signal to stop a container (default "SIGTERM")
      --stop-timeout int               Timeout (in seconds) to stop a container
      --storage-opt list               Storage driver options for the container
      --sysctl map                     Sysctl options (default map[])
      --tmpfs list                     Mount a tmpfs directory
  -t, --tty                            Allocate a pseudo-TTY
      --ulimit ulimit                  Ulimit options (default [])
  -u, --user string                    Username or UID (format: <name|uid>[:<group|gid>])
      --userns string                  User namespace to use
      --uts string                     UTS namespace to use
  -v, --volume list                    Bind mount a volume
      --volume-driver string           Optional volume driver for the container
      --volumes-from list              Mount volumes from the specified container(s)
  -w, --workdir string                 Working directory inside the container
```

## Multiplas aplicações do mesmo container

* Podemos inicializar **vários containers com a mesma imagem**;

* As aplicações funcionarão em paralelo;

* Para testar isso, podemos determinar uma **porta diferente** para cada uma, e rodar no **modo detached;**

```docker
sudo docker run -d ...
```

## Alterando o nome da imagem e tag

* Podemos **nomear a imagem** que criamos;

* Vamos utilizar o comando **sudo docker tag imagem** para isso;

* Também podemos **modificar a tag**, que seria como a versão da imagem, semelhante ao git;

* Para inserir a tag utilizamos: **sudo docker tag nome:tag**;

```docker
sudo docker tag minhaimagem:latest  minhaimagem:minhatag
```

## Iniciando imagem com o nome

* Podeos **nomear a imagem já na sua criação**;

* Vamos utilizar a **flag -t**;

* é possivel inserir o nome e a tag, na sintaxe: **nome:tag**;

* Isso torna o proceso de nomeação mais simples;

```docker
sudo docker build -t meunode_diferente .
```

## Comando start interativo

* A **flag -it** pode ser utilizada com o comando start também;

* Ou seja, não precisamos criar um novo container para utilizá-lo no terminal;

* O comando é: **sudo docker start -i container**;

## Removendo imagens

* Assim como nos containers, **podemos remover imagens com um comando**;

* Ele é o: **sudo docker rmi imagem**;

* Imagens que estão sendo utilizadas por um container, apresentarão um erro no terminal;

* Podemos utilizar a **flag -f** para forçar a remoção;

## Remoção de imagens e containers não utilizados

* Com o comando **docker system prune**;

* Podemos **remover imagens, containers e networks** não utilizados;

* O sistema irá exigir uma confirmação para realizar a remoção;

## Removendo container após utilização

* Um container pode ser automaticamente deletado após sua utilização;

* Para isso vamos utilizar a **flag --rm**;

* O comando seria:**sudo docker --rm container**;

* Desta maneira **economizamos espaço no computador** e deixamos o ambiente ais organizado;

## Copiado arquivos entre containers

* Para cópia de arquivos entre containers utilizamos o comando: **sudo docker cp**

* Pode ser utilizado para copiar um arquivo de um diretório para um container;

* Ou de um container para um diretório determinado;

passos:

```docker
sudo docker run -d -p 3000:3000 --name node_diferente2 meunode_diferente

sudo docker cp meunode_diferente2:/app/app.js ./copia/
```

## Verificar informações de processamento

* Para verificar dados de execução de um container utlizamos:**sudo docker top container**;

* Desta maneira temos acesso a quando ele foi iniciado, id do processo, descriação do comando CMD

## Inspecinando container

* Para verificar diversas informações como:**id,data de criação,imagem e muito mais**;

* Utilizamos o comando **docker inspect container**;

* Desta maneira conseguimos entender como o container está configurado;

comando

```docker

sudo docker inspect myql
detalhado
sudo docker inspect mysql | grep IPAddress
```

## Verificando processamento do Docker

* Para verificar os processos que estão sendo executados em um container,utilizamos o comando: **sudo docker stats**

* Desta maneira temos acesso ao andamento do processamento e memória gasta pelo mesmo;

## Autenticação no terminal

* Para concluir esta aula vamos precisar criar uma conta no:<https://hub.docker.com>

* Para autenticar-se pelo terminal vamos utilizar o comando **sudo docker login**;

* E então inserir usuário e senha;

* Agora podemos **enviar nossas próprias imagens** para o HUB! =)

## Encerrando autenticação

* Para remover a conexão entre nossa máquina e o Docker Hub, vamos utilizar o comando **sudo doker logout**;

* Agora não podemos mais enviar imagens, pois não estamos autenticados;

## Enviando imagem para o Docker Hub

* Para enviar uma imagem nossa ao Docker Hub utilizamos o comando **sudo docker push imagem**;

* Porém antes vaoms precisar **criar o repositório** para a mesma no site do Hub;

* Também será necessário **esar autenticado**;

## Atualizando imagens no Hub

* Para enviar uma atualização **vamos primeiramente fazer o build**;

* **Trocando a tag da imagem** para a versão atualizada;

* **Depois vamos fazer um push** novamente para o repositorio;

* Assim odas as versões estarão disponíveis para serem utilizadas;

## BAixando e utilizando a imagem

* Para baixar a imagem podemos utilizar o comando **sudo docker pull imagem**;

* E depois criar um novo container com **sudo docker run imagem**

* E pronto! Estaremos utilizando a nossa imagem com um container;
