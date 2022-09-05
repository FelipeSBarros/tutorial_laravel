## Laravel

### Estrutura

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

## Criando rotas

A rota é definida pelo método, seguido pela string da rola, o controlador a ser usado e a `action` (ou método do controlador) a ser usada (ambos podem estar em um array). A mesmo é então nomeada para facilitar a sua manutenção.  

```
# routes/web.php
Route::get('/users', [UserController::class, 'index'])->name('users.index');
```

Para que o `Controler` seja criado, é necesário acessar a app pelo terminal (contrainer da app), usando o artisan:  
```
php artisan make:controller UserController
#   INFO  Controller created successfully. 
```

Com isso o controle será criado na pasta `app>Http>Controllers`. E no arquivo criado devemos implementar o método a ser usado pela `route`.

```shell
class UserController extends Controller
{
    public function index()
    {
        dd('UserController@index');
    }
}
```

O `dd()` é uma forma de debug, comum no processod e desenvolvimento. Para confirmar se está funcionando, é importante importar a classe em `routes/web.pho`:

```shell
use App\Http\Controllers\{
    UserController
};
```


Para uma rota retornar uma `view`, basta indicar o diretório.view:

`return view('users.index');`

### Criando uma `view`

Em `resources>views`, deve-se criar o subdiretório e o nome da view adicionando`.blade.php`:

`index.blade.php`

Ele irá automaticamente identificar a view nomeada na rota e irá usar o blade para renderizar a view. 
:warning: Não esquecer de adicionar o sufixo `.blade.php`;  

Mais de um método pode ser criado em um mesmo `controller`.

Quando for necessário passar um parâmetro pela `url` a ser usada na renderização da view pela , indica-se a mesma pelo uso de "{}":

`Route::get('/users/{id}', [UserController::class, 'show'])->name('users.show');`

Já no controlador, usa-se a mesmo como variável, por isso o uso do "$":

```shell
public function show($id)
    {
        dd('users@how', $id);
    }
```
