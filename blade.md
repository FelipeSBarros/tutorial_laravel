## Blade

`Blade` é uma "engrenagem" *templates* do ambiente Laravel. Diferente de algumas engrenagens de *templates* de PHP, Blade não se restringe ao uso apenas de código PHP. Na verdade todos os *templates* `Blade` são compilados em PHP y `cached` até que sejam modificados, garantindo zero `overhead`. Os templates usam a extensão `.blade.php` e são armazenados na pasta `resources/views directory`.

`Blade` *views* podem ser retornadas de `url` ou `controllers` usnado o "global view helper". 
Dados podem ser passados ao `Blade` usando o segundo ardumento da `view`:

```
Route::get('/', function () {
    return view('greeting', ['name' => 'Finn']);
});
```

Para apresentar os dados, usar `{{}}` (*htmlspecialchars*), que previne ataques XSS.

Pode-se ainda apresentar resultados provenientes de funções PHP:
```shell
The current UNIX timestamp is {{ time() }}.
```

<https://laravel.com/docs/9.x/blade>