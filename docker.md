## Docker cheatsheet

[source](https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/)

Listar todas as docker images:

```commandline
docker imges
```

Remover docker image:

```commandline
docker rmi <docker_imge> # --force
```

Listar todos os containers (apenas ativos):

```commandline
docker ps
```
Listar todos os containers, mesmo inativos (sem estar rodando):

```commandline
docker container ls -a
```

Removendo container:

```commandline
docker rm <containerID>
```

removendo `docker volumes`:

```commandline
docker volume rm
```

Removendo `dcoker networds`:

```commandline
docker network rm 
```