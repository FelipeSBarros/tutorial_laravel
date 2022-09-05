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

## Executando docker

```shell
docker up -d
```
`-d` libera o terminal.

```shell
docker-compose ps
```

Os `docker-composes` identificados como "restarting", são aqueles que dependem de dependencias do projeto. Para instalá-los, basta acessar o bash do container da app e executar o `composer install`, que irá ler o arquivo `composer.json` com as dependencias e os instalarão.

```shell
docker-compose exec app bash
# carlos@e8d842490502:/var/www$

carlos@e8d842490502:/var/www$ composer install
```


### [Composer install](https://getcomposer.org/doc/01-basic-usage.md#installing-dependencies) 

> It resolves all dependencies listed in your composer.json file and writes all of the packages and their exact versions to the composer.lock file, locking the project to those specific versions.