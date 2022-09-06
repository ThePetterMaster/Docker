# Docker
![](/homepage-docker-logo.png)

Este repositório serve para mostrar meu aprendizado com Docker.

## O que é um container?
<blockquote>Container Docker, é o componente do software de código aberto que automatiza a implementação de aplicativos em Containers LINUX, o famoso Docker.</blockquote>

 ![](/Container.png)
 
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

Abrir terminal do ubuntu:
`docker run -it ubuntu`

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

Acessar a rota no comando acima( 0.0.0.0:49154->80/tcp):
`http://localhost:49154/`

Executando/Baixando sem travar o terminal(-d) e gerando porta fixa (-p):

`docker run -d -p 12345:80 dockersamples/static-site`

Dando nome a um container:

`docker run -d -P --name meu-site dockersamples/static-site`

Executando/Baixando um container colocando uma variável de ambiente:

`docker run -d -P -e AUTHOR="Pedro Neto" dockersamples/static-site`
