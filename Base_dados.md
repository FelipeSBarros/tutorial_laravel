## Base de dados 

O Docker compose recebe as informações sobre banco de dados direto do `.env` e cria o banco de dados conforme especificado.

```shell
    # db mysql
    mysql:
        container_name: especializati-mysql
        image: mysql:5.7.22
        restart: unless-stopped
        environment: 
            MYSQL_DATABASE: ${DB_DATABASE}
            MYSQL_ROOT_PASSWORD: ${DB_PASSWORD}
            MYSQL_PASSWORD: ${DB_PASSWORD}
            MYSQL_USER: ${DB_USERNAME}
        volumes: 
            - ./.docker/mysql/dbdata:/var/lib/mysql
        ports: 
            - "3388:3306"
        networks: 
            - laravel-9

```

### Migrações

As migrações ficam na pasta `databse>migrations`. Algumas tabelas são criadas automaticamente, como usuários e senha.

No méodo `up()` a tabela é criada;
No méodo `Down()` a tabela é criada;


* `php artisan migrate`
Cria as tabelas;

* `php artisan migrate:refresh`
Identifica as modificações e deleta recriando as que foram alteradas;

* `php artisan migrate:fresh`
Deleta TODAS as tabelas e as cria de novo;

Ao executar as migrações, uma tabela chamada `migrations` é criada para confirmar quais migrações já foram executadas. Dessa forma, uma mesma migrção não é executada duas vezes.

As tabelas serão criaadas conforme a ordem do timestamp de sua migração.
