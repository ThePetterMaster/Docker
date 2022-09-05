# Docker
![](/homepage-docker-logo.png)

Este repositório serve para mostrar meu aprendizado com Docker.

## O que é um container?
<blockquote>Container Docker, é o componente do software de código aberto que automatiza a implementação de aplicativos em Containers LINUX, o famoso Docker.</blockquote>

 ![](/Container.png)
 
## Camadas de um container e seu compartilhamento

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

Executar um container pelo id:
`docker start -a -i CONTAINER ID`

Parar um container em execução:
`docker stop CONTAINER ID`

Remover um container pelo id:
`docker rm CONTAINER ID`

Remover todos containers inativos:
`docker container prune`

Visualizar imagens:
`docker images`

Removendo imagem:
`docker rmi hello-world`

