# Docker

### Iniciando com Docker (baixando imagem nginx)
-     Baixar imagem: **docker run nginx**
-     Visualiza container rodando: **docker ps**
-     Visualiza todos os container criados: **docker ps -a**
-     Parando um container: **docker stop <`container_id`>**
-     Remove um container que esta parado: **docker rm <`container_id`>** 
-     Remove um container forçando a parada: **docker rm <`container_id`> -f**
-     Rondando uma imagem docker em background em uma porta especifica: **docker run -d --name nginx_porta -p 8080:80 nginx:alpine**
-     Rodando o container em outra porta local: **docker run -d --name nginx_porta2 -p 80:80 nginx:alpine**
-     Rodando comandos no container: **docker exec my_nginx uname -a **
-     Acessando o bash do container: **docker exec -it my_nginx bash**

### Iniciando com volumes no Docker
-     Criando volume do container: **docker run -d --name my_nginx -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx**
-     Listar volumes: **docker volume ls**
-     Criar volume: **docker volume create vol_test**
-     Help do volume: **docker volume --help **
-     Inspecionar volume: **docker volume inspect vol_test**
-     Criando volume com algumas options: **docker volume create --driver local --opt type=none --opt device=$(pwd) --opt o=bind volume_local**
-     Colocando uma imagem ao volume criado: **docker run -d --name=nginx2 -p 8081:80 -v volume_local:/usr/share/nginx/html nginx**
-     Matar todos os volumes: **docker volume prune**

### Docker Networks
-     Listar as Networks: **docker network ls**
-     Inspecionar a network bridge: **docker network inspect bridge**
-     Criando uma network: **docker network create -d bridge my_network ** *(Você so pode resolver os ip para nome quando cria sua propria rede docker, pois a rede padrão do docker não faz isso)*
-     Criando um container para minha network: **docker run -d --name nginx3 --net=my_network nginx**

