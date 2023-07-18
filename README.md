# snirin_microservices
snirin microservices repository

ДЗ 16 docker-2
ERROR:  Error installing bundler:                                                                                                                                                                    
26.53   The last version of bundler (>= 0) to support your Ruby & RubyGems was 2.3.26. Try installing it with `gem install bundler -v 2.3.26`

todo объяснить различия
todo Повторение практики из демо на лекции
todo повторение tehbilly/htop после лекции

Для себя
`docker run = docker create + docker start + docker attach`
Список команд
```
docker version
docker info
docker run hello-world
docker ps
docker ps -a
docker images
docker images -a
docker run -it ubuntu:18.04 /bin/bash
docker run -dt nginx:latest
exit
docker ps -a --format "table {{.ID}}\t{{.Image}}\t{{.CreatedAt}}\t{{.Names}}"
docker start ead70ea1fa33
docker attach ead70ea1fa33
docker exec -it ead70ea1fa33 bash
docker inspect 3fa7e364b9d8
docker ps -q
docker kill $(docker ps -q)
docker system df
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)

docker-machine create <имя>
eval $(docker-machine env <имя>
eval $(docker-machine env --unset)
docker-machine rm <имя>

yc compute instance create \
  --name docker-host \
  --zone ru-central1-a \
  --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4 \
  --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15 \
  --ssh-key ~/.ssh/id_ed25519.pub

docker-machine create \
 --driver generic \
 --generic-ip-address=158.160.103.97 \                    
 --generic-ssh-user yc-user \
 --generic-ssh-key ~/.ssh/id_ed25519 \
 docker-host
 
docker-machine ls

eval $(docker-machine env docker-host)

docker run --rm -ti tehbilly/htop
docker run --rm --pid host -ti tehbilly/htop

docker build -t reddit:latest .
docker run --name reddit -d --network=host reddit:latest

docker login
docker tag reddit:latest snirinnn/otus-reddit:1.0
docker push snirinnn/otus-reddit:1.0
docker run --name reddit -d -p 9292:9292 snirinnn/otus-reddit:1.0

docker logs reddit -f
docker exec -it reddit bash
killall5 1

docker start reddit
docker stop reddit && docker rm reddit
docker run --name reddit --rm -it snirinnn/otus-reddit:1.0 bash

docker inspect snirinnn/otus-reddit:1.0
docker inspect snirinnn/otus-reddit:1.0 -f '{{.ContainerConfig.Cmd}}'

docker exec -it reddit bash
mkdir /test1234
touch /test1234/testfile
rmdir /opt
exit
docker diff reddit
docker stop reddit && docker rm reddit
docker run --name reddit --rm -it /otus-reddit:1.0 bash
ls /

docker-machine rm docker-host
yc compute instance delete docker-host
```
