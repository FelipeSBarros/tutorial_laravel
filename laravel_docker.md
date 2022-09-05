## Laravel docker

Passo-a-passo de instalação do laravel e demais dependencias usando `dcoker`. Origem do tutorial: curso [especializeTI][especializeTI].   
[Repositório original][repo_especializeTI]

[Algumas coisas sobre docker](./docker.md)

### Instalação

A pasta onde o mesmo está sendo instalado é './laravel9'

```
git clone https://github.com/especializati/setup-docker-laravel.git laravel9
cd laravel9/
git checkout laravel-9-com-php-8
rm -rf .git/
```

Vamos criar uma pasta para nosso projeto interna a pasta atual que contem o `laravel`.

```commandline
cp .env.example .env
mkdir example-project
cd example-project/
```

[especializeTi]: https://academy.especializati.com.br/aula/instalando-o-laravel-9
[repo_especializeTI]: https://github.com/especializati/setup-docker-laravel/blob/laravel-9-com-php-8/docker-compose.yml