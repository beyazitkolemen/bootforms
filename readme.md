
BootForms
===============

## Composer ile Yükleme

Terminal üzerinden aşağıdaki şekilde yükleyebilirsiniz.

```bash
composer require beyazitkolemen/bootforms
```

### Laravel

Eğer laravel kullanıyorsanız aşağıdaki şekilde config/app.php dosyasına Provider ve Aliases ekleyebilirsiniz.


```php
'providers' => [
    //...
    BeyazitKolemen\BootForms\BootFormsServiceProvider::class,
  ],
```


```php
'aliases' => [
    //...
    'BootForm' => BeyazitKolemen\BootForms\Facades\BootForm::class,
  ],
```

