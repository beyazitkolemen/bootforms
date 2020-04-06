[BootForms](https://github.com/adamwathan/bootforms "BootForms") Paketine, çoklu dil desteği için kullanılan [Laravel Translateble](https://github.com/Astrotomic/laravel-translatable "Laravel Translateble") paketinin Text ve Textarea için kolay kullanımı dahil edilmiştir.

BootForms
===============

Bootform

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
Bootform Eklentisinden farklı olarak birden fazla dil için kullanımda;
```php
    {!! BootForm::translatetext('Detail', 'detail','tr') !!}
    {!! BootForm::translatetextarea('Detail', 'textareadata','tr') !!}
  ```
şeklinde kullanabilirsiniz.

Laravel Translateble eklentisinde aktif kullandığınız dilleri aşağıdaki şekilde çağırabilirsiniz.
```php
  @foreach(config('translatable.locales') as $count => $langs )
    {{$langs}}
    @endforeach
```

**Örnek Kullanım:
**

     <?php
        $columnSizes = [
          'sm' => [4, 8],
          'lg' => [2, 10],
        ];
        ?>
                {!! BootForm::openHorizontal($columnSizes)->method('POST')->action(route('post')) !!}
                <div class="row">
                    <div class="col-sm-12 col-xs-12">
                        <ul class="nav nav-tabs  bar_tabs" role="tablist">
                            @foreach(config('translatable.locales') as $count => $langs )
                            <li role="presentation" @if($count==0) class="active" @endif style="text-transform: uppercase;"><a href="#{{$langs}}" aria-controls="{{$langs}}" role="tab" data-toggle="tab">{{$langs}}</a></li>
                            @endforeach
                        </ul>
                    </div>
                    <div class="clearfix"></div>
                </div>
                <!-- Tab panes -->
                <div class="tab-content">
                    @foreach(config('translatable.locales') as $count => $langs )
                    <div role="tabpanel" class="tab-pane @if($count == 0) active @endif" id="{{$langs}}">
                        {!! BootForm::translatetext('Title', 'title',$langs) !!}
                        {!! BootForm::translatetextarea('Detail', 'detail',$langs) !!}
                    </div>
                    @endforeach
                </div>
                {!! BootForm::text('No Trans Title', 'no_trans_title') !!}
                {!! BootForm::textarea('No Trans Detail', 'no_trans_detail') !!}
                {!! BootForm::submit('Submit')->class('btn btn-success') !!}
                {!! BootForm::close() !!}
Bind işlemi için (Veri Düzenleme):

    {!! BootForm::bind($data)!!}

gibi eklediğinizde çeviri dilleri otomatik olarak doldurulacaktır.
