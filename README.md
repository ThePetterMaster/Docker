# Docker
![](/homepage-docker-logo.png)

Este repositório serve para mostrar meu aprendizado com Docker.

## O que é um container?
<blockquote>Container Docker, é o componente do software de código aberto que automatiza a implementação de aplicativos em Containers LINUX, o famoso Docker.</blockquote>

 ![](/Container.png)
 
 ## Arquitetura do Docker:
 
  ![](/docker-arquitetura.webp)
 
 ## Docker Daemon:
 
Possui um processo chamado dockerd, escuta as requisições da API do Docker e gerencia os objetos:

## Docker Client:

Utilizado para interagir com o docker, o docker client envia os comandos ao dockerd que os executa.

## Docker Registry:

O docker registry é responsável por armazenar e distribui as imagens docker.

## O que são imagens?

Podemos dizer que uma imagem é a aplicação que queremos executar.

## O que são containers Docker?

Um container é uma instancia de uma imagem sendo executada de forma isolada no host. Na prática é uma imagem com uma camada de read write.


## Camadas de um container e seu compartilhamento

Em um container existem camadas que são compartilhadas por outros containers e essas não podem ser alteradas. Somente as camadas de read write podem ser alteradas.

 ![](/Camadas.jpg)


## Primeiros passos com Docker

Verificar se o Docker foi instalado:
` docker version`

Baixar primeira imagem no Docker:
` docker pull hello-world`

Executar primeira imagem no Docker(Irá baixar caso não esteja):
` docker run hello-world`

Executar imagem ubuntu:
`docker run ubuntu`

Executar o echo do ubuntu:
`docker run ubuntu echo "Olá mundo"`

Abrir terminal do ubuntu(modo iterativo):
`docker run -it ubuntu`

Executar um comando em um container que já está em execução:
`docker exec -it CONTEINER ID bash`

Listar imagens ativas:
`docker ps`

Listar imagens ativas ou não:
`docker ps -a`

Listar id das imagens ativas:
`docker ps -q`

Executar um container pelo id:
`docker start -a -i CONTAINER ID`

Parar um container em execução(termina por padrão em 10 segundos):
`docker stop CONTAINER ID`

Parar um container em execução(em 0 segundos):
`docker stop -t 0 CONTAINER ID`

Parar todos containers em que `docker ps -q` retorna :
`docker stop -t 0 $(docker ps -q)`

Remover um container pelo id:
`docker rm CONTAINER ID`

Remover todos containers inativos:
`docker container prune`

Visualizar imagens:
`docker images`

Removendo imagem:
`docker rmi hello-world`

Executando/Baixando um container de uma fonte não oficial(usuario=dockersamples container=static-site):


`docker run dockersamples/static-site`

Executando/Baixando sem travar o terminal(-d) e gerando porta aleatória (-P):

`docker run -d -P dockersamples/static-site`

-p (ou --publish): Permite especificar manualmente a correspondência de portas entre o host e o container. O formato é -p [porta_host]:[porta_container]. Por exemplo, -p 8080:80 mapeia a porta 8080 do host para a porta 80 do container. Isso oferece controle preciso sobre quais portas são expostas e como são mapeadas.

-P (ou --publish-all): Mapeia automaticamente todas as portas expostas no Dockerfile ou na imagem para portas aleatórias no host. Isso é útil quando você não se importa com quais portas específicas são usadas no host, mas quer garantir que todas as portas expostas no container estejam acessíveis.

No contexto do comando docker run, a flag -d significa “modo destacado” (do inglês, “detached mode”). Quando você usa -d, o Docker executa o container em segundo plano, permitindo que você continue a usar o terminal para outras tarefas.

Por exemplo, ao executar docker run -d dockersamples/static-site, o container será iniciado e rodará em segundo plano, sem ocupar o terminal.

Acessar a rota no comando acima( 0.0.0.0:49154->80/tcp):
`http://localhost:49154/`
 
 ![](/hellodocker.png)

`docker port CONTAINER ID`

Executando/Baixando sem travar o terminal(-d) e gerando porta fixa (-p):

`docker run -d -p 12345:80 dockersamples/static-site`

Dando nome a um container:

`docker run -d -P --name meu-site dockersamples/static-site`

Executando/Baixando um container colocando uma variável de ambiente:

`docker run -d -P -e AUTHOR="Pedro Neto" dockersamples/static-site`

Verificar quais são as camadas de uma imagem:

`docker history CONTAINER ID`

Detalhes de uma imagem:

`docker inspect CONTAINER ID`

 ![](/autorpedroneto.png)
 
## Etapas do run

Procura a imagem localmente -> Baixa a imagem caso não encontre localmente -> Valida o hash da imagem -> Executa o container.

## Docker File

Arquivo para criação de imagens.
 ![](/DockerFile.png)

 
## Volumes no docker

Através dos volumes é que é possivel persistir dados de um container após ele ser parado

Executar em uma pasta:
`docker run -d -p  8080:3000 -v "$(pwd):/var/www" -w "/var/www" node npm start`

$(pwd) retorna o diretório atual da pasta

`:/var/www` indica em qual pasta do docker host deve esta o volume

`-w "/var/www" node npm start` indica que ao executar o container, o terminal irá executar o comando `npm start` na pasta /var/www do docker host usando o node

## Docker File

É um arquivo que serve para configurar volumes 
`
FROM  node:latest 
ENV PORT=3000
COPY . /var/www
WORKDIR /var/www
RUN npm install
ENTRYPOINT npm start
EXPOSE $PORT 
`
Comando para gerar a imagem no arquivo Dockerfile:
`docker build -f Dockerfile -t neto/node .`

Executando o container:
`docker run -d -p 8080:3000 neto/node`

## Comunicação entre containers 

![](/ConectandoContainers.png)

## Redes no Docker

O docker cria um ip para cada container executado no docker host

![](/RedesDocker.png)

Por padrão eles são criados em uma rede chamada "bridge". Para verificar isso:`docker inspect CONTAINER ID`

![](/CriandoRede.png)

Comando para criar uma rede: `docker network create --driver bridge minha-rede`

Pegando banco de dados do alura:`docker pull douglasq/alura-books:cap05`

Rodando o banco de dados(primeiro) dentro da rede minha-rede:`docker run -d --name meu-mongo --network minha-rede mongo`

Rodando a aplicação dentro da rede minha-rede:`docker run --network minha-rede -d -p 8080:3000 douglasq/alura-books:cap05`









