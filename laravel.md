## Laravel

Estrutura de arquivos:

[`webpackmix`][webpackmix]: Sistema de controle `js` e `css`;
[`phpunit.xml`][phpunit.xml]: Sistema de testes (unitários e de integração);
[`packages.json`][packages.json]: Controle de dependências do projeto;
[`artisan`][artisan]: `CLI` do laravel com muitos recursos;

Pastas:
`vendor` - Pacotes de terceiros instalados pelo `composer.json` (incluindo o laravel em sí);  
`tests` - Suite de testes;  
`storage` - Arquivos criados e armazenados no `runtime` a app;  
`routes` - Rotas do projeto;  
`resources` - One ficam toos os arquivos de front-end (view blade). Podendo ser usado no `webpack`;  
`public` - `Document host` da aplicação. Ponto de partida;  
`lang` - internacionalização da app;  
`database` - Onde ficam as migrações;  
`config` - Arquivos de configuração individual;  
`configbootstrap` - Inicializador do bootstrap;  
`app`: onde trabalhamos  
    1. `controllers`  
    1. `middlewares`  
    1. `models`  
  
[webpackmix]:https://laravel.com/docs/9.x/mix  
[phpunit.xml]:https://phpunit.de/  
[packages.json]:https://laracasts.com/discuss/channels/laravel/understanding-packagejson  
[artisan]:https://laravel.com/docs/9.x/artisan  
