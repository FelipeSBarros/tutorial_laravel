## Laravel docker

Passo-a-passo de instalação do laravel e demais dependencias usando `dcoker`. Origem do tutorial: curso [especializeTI][especializeTI].   
[Repositório original][repo_especializeTI]

[Algumas coisas sobre docker](./docker.md)

### Instalação

A pasta onde o mesmo está sendo instalado é './curso-laravel9'

```shell
git clone https://github.com/especializati/setup-docker-laravel.git curso-laravel9
cd curso-laravel9/
git checkout laravel-9-com-php-8
rm -rf .git/
```

Vamos criar uma pasta para nosso projeto interna a pasta atual que contem o `laravel`.

```shell
cp .env.example .env
```
Há que abrir o `.env` e alterar a porta do container `nginx` conforme especificado no `docker-compose.yml`): 8989:80

```shell
# .env
APP_URL=http://localhost:8989
DB_HOST=mysql
DB_DATABASE=curso_laravel_9
DB_PASSWORD=root
CACHE_DRIVER=redis
SESSION_DRIVER=redis
REDIS_HOST=redis
```

:warning: confirmar que os serviços usados (banco de dados, nigx, etc não estejam direcionado a portas já em uso!)

Tendo alterado essas configurações, basta rodar o [`docker-compose up](https://docs.docker.com/engine/reference/commandline/compose_up/#:~:text=The%20docker%20compose%20up%20command,background%20and%20leaves%20them%20running.):

> Builds, (re)creates, starts, and attaches to containers for a service.


```shell
docker-compose up -d
```


```shell
docker-compose ps
         Name                        Command                 State                       Ports                  
----------------------------------------------------------------------------------------------------------------
especializati-laravel-9   docker-php-entrypoint php-fpm    Up           9000/tcp                                
especializati-mysql       docker-entrypoint.sh mysqld      Up           0.0.0.0:3388->3306/tcp,:::3388->3306/tcp
especializati-nginx       /docker-entrypoint.sh ngin ...   Up           0.0.0.0:8989->80/tcp,:::8989->80/tcp    
especializati-queue       docker-php-entrypoint php  ...   Restarting                                           
especializati-redis       docker-entrypoint.sh redis ...   Up           6379/tcp 
```

O `especializati-queue` está como *restarting* pois não fizemos a instalação das dependencias do projeto. Podemos fazer isso diretamente **no container de nodda aplicação**. As dependencias geralmente ficam num `composer.json`, com todas as informações básicas e necessários definidas.

Para fazer essa instalação, basta executar o bash internamente ao container de nossa aplicação.
```shell
docker-compose exec app bash
# carlos@e8d842490502:/var/www$

carlos@e8d842490502:/var/www$ composer install
```

Agora a app precisa ter uma `key` gerada. Ao executar:
`php artisan Key:generate` a `key` é gerada e adicionada no `.env`, automagicamente.

Criando pasta de
```shell
mkdir example-project
cd example-project/
```

[especializeTi]: https://academy.especializati.com.br/aula/instalando-o-laravel-9
[repo_especializeTI]: https://github.com/especializati/setup-docker-laravel/blob/laravel-9-com-php-8/docker-compose.yml
