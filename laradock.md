## [`Laradock`](https://laradock.io/)

Tutorial específico sobre o uso do `laradock`, do specializeTI:

* [video1: 06 - Ambiente Completo PHP 7 com Docker (Laradock)
](https://www.youtube.com/watch?v=6XfZLqoywz4)
* [video2: 07 - Múltiplos Projetos com Docker (Laradock)](https://www.youtube.com/watch?v=lKhlG4xHKGM)

O laradock provê uma serie de recursos prontos e pré-configurados para facilitar a criação dos containers para densenvolvimento de projetos com PHP e `laravel`.

Na [documentação](https://laradock.io/getting-started/#installation), apresenta-se diferentes formas de usar o `laradock`;
1. Para um único projeto;
2. Para múltiplos projetos PHP ([apresentado também, neste video](https://www.youtube.com/watch?v=lKhlG4xHKGM));

### `docker-compose.yml`

É um arquivo com toda a configuração dos diferentes containers;

### `.env`

Arquivo onde ficarão as informações sensíveis do projeto, como senha, portas e etc. Veja em [docker](./docker.md#env-e-docker-compose.yml) que o `docker-compose.yml` recebe variáveis definidas no arquivo `.env`.

### nginx

Após o clone do laravel e antes de rodar os containers, é importante configurar em `nginx>sites>default.conf`.

No caso de estarmos trabalhando com mais um um projeto, seria o caso de criar um arquivo `.conf` que tenha o mesmo nome da pasta ao qual o projeto se encontra. Exemplo: `imibio.conf`.

:warning: Caso os dockers já estiverem em execução, sera necessário reiniciá-los:

```commandline
docker-compose restart
```

É necessário também, acessar o arquivo de hosts para adicionar ao localhost o endereço criado:
```
sudo nano /etc/hosts
#127.0.0.1 imibio.dev
```

### Acessando workspace

```
docker-compose exec workspace bash
cd imibio
compose install
```

#### Migrações

antes de realizar as migrações confirmar que o `.env` está da seguinte forma:

```commandline
APP_NAME=Laravel
APP_ENV=local
APP_KEY=base64:E9BLSGkJEe6UDpDdLVz19VPXDDkthIgWjhCfezc6Q9A=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=imibio
DB_USERNAME=root
DB_PASSWORD=root
```

O banco de dados deverá ser criado antes de realizar as migrações.

```commandline
php artisan migrate
```
