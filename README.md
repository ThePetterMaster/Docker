# Docker
Este repositório serve para mostrar meu aprendizado com Docker.

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

Executar uma imagem pelo id:
`docker start -a -i CONTAINER ID`

