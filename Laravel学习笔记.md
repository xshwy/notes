# 文档
1. [极客学院出品的文档][1]
2. [Laravel中文站出品的文档][2]

# 前期准备

## Homestead 配置

1. 安装[VirtualBox][3]
2. 安装[Vagrant][4]
3. 安装 Homestead Vagrant Box
    0. `vagrant box add laravel/homestead`,因各种原因有时下载会中断，所以提前自己下载下来，执行完命令后可以看到下载链接
    1. 将离线下载的`虚拟机文件`添加到vagrant box里 `vagrant box add laravel/homestead ./virtualbox.box`
4. 配置Laravel/Homestead
    0. `cd ~`
    1. `git clone https://github.com/laravel/homestead.git Homestead`
    2. `bash init` 执行后会创建 `~/.homestead`目录
5. 配置Homestead
    0. `vi ~/.homestead/Homestead.yaml`
    1. 修改`provider:virtualbox`
    2. 修改`folders: -map: xxx/xxx/xx` 为项目路径
    3. 修改`sites: -to: /home/vagrant/Code/Public`
6. 操作Homestead
    0. `cd ~/Homestead`
    1. 启动`vagrant up`
    2. 关闭`vagrant halt`
    3. 访问SSH `vagrant ssh`
    4. 连接数据库
        0. 地址 `127.0.0.1`
        1. 用户名`homestead`
        2. 密码`secret`
    3. 如果出现错误提示，可以用`vagrant provision`就一命试试看

## 准备工作
0. 准备VPN翻出围墙
1. 需要先安装Composer `curl -sS https://getcomposer.org/installer | php`

## 通过Composer安装Laravel
`composer global require "laravel/installer=~1.1"`

## 全局使用composer
`sudo mv composer.phar /usr/local/bin/composer`


<!--more-->


## 通过Composer创建新项目
`composer create-project laravel/laravel project-name`

## 配置phpStorm
1. 安装插件搜索 Laravel并安装
2. 配置Laravel插件`Other Settings`->`Laravel Plugin`->`Enable plugin for this project`
3. 在当前项目下的`composer.json`的`"require":{}`增加一行`"barryvdh/laravel-ide-helper":"dev-master"`
4. 在当前项目文件夹执行 `composer update`
5. 添加service provider，打开项目`config/app.php` 于`providers`添加如下一行：`'Barryvdh\LaravelIdeHelper\IdeHelperServiceProvider',`
6. 执行`php artisan ide-helper:generate`
7. 再当前项目下的`composer.json`的`"post-update-cmd": [`增加一行`"php artisan ide-helper:generate"`


## 启动项目
`php artisan serve`

# 开始工作

## 工作流程
1. 访问路由
2. 通过路由跳转到控制器
3. 控制器打开视图

## 创建路由

编辑app/Http/routes.php
`Routes::get('/about','siteController@about');`

```
Routes::get('/show',function(){
    view('show');
});
```

## 创建控制器
`php artison make:controller controll-nameController`
可选参数 `--palin` 可以创建空白控制器 `--resource` 可以创建带有`RESTful`风格的函数

## 使用中间件
1. 创建 `php artison make:middleware TestMiddleware` 再`/app/Http/Middleware`目录
2. 配置 添加到`\App\Http\Middleware\TestMiddleware::class` 到 `\App\Http\Kernel`下的`$routeMiddleware`
3. 使用 `['middleware'=>['Test']]`

## 操作视图

1. 创建视图
    `创建resources/views/view-name.blade.php文件`

2. 视图显示参数

    1. 转义输出`{{$var-name}}`
    2. 不转义输出`{{!$var-name!}}`

3. 显示视图

    1. 直接显示视图 `return view('view-name')`
    2. 传递参数到视图 `return view('view-name',compact('var-name'))`

## 操作模板

1. 创建模板
    `创建resources/views/app.blade.php文件`
2. 模板占位符
    `@yield('content')`
3. 在视图里使用模板
```
@extends('app') //引用模板文件
@section('content') //填充占位符
    这里可以写内容
@stop
```

# 数据库操作

## 配置数据库
`修改.env文件即可`

## 执行数据库更改
`php artisan migrate`

## 撤销
`php artisan migrate:rollback`

## 创建数据表
0. 文件位置
`database/migrations/create-table-code.php`

1. 创建文件命令
`php artisan make:migration create_table-name_table --create=table-name`

## 追加字段
```
// 增加一个文件
php artisan make:migration add_intro_column_to_articles --table=table-name`

// 编辑 up()、down()

// 在down()里面需要添加删除字段的步骤$table->dropColumn('colum-name');

// dropColumn 依赖dbal包
composer require dectrine/dbal

```

## 创建model
`php artisan make:model model-name`


## 命令行操作数据库

1. 进入tinker`php artisan tinker`
2. 实例化model `$first = App\Model-name`
3. 赋值 `$fisrt->colmun-name='value';`
4. 提交 `$first->save();`
5. 查找 `$first=App\model-name::find();`
6. where `$first=App\model-name::where('','=','')->get();`

7. 直接创建数据 `$first=App\model-name:;create(['title'=>'mytitle']);`

    · 因为保护原因，无法直接创建数据，需要在model里面设置保护字段`protected $fillable=['title']`

8. 查询全部 `$first = App\Model-name::all();`



##撤销/回滚

# 表单操作

## 需要先安装 illuminate/html
`composer require illuminate/html`

## 配置illuminate/html
1. 将`Illuminate\Html\HtmlServiceProvider::class`添加到`config/app.php` 里的 `providers`数组里
2. 设置别名，将`'Form'      => Illuminate\Html\FormFacade::class,` 添加到`aliases`数组里

## 使用表单

```
{!! Form::open(['url'=>'articles']) !!} // 表示以post方式提交到/articles页面

    {!! Form::label('title','标题:') !!}
    {!! Form::text('title',null,['class'=>'form-control']) !!}


    {!! Form::label('content','正文:') !!}
    {!! Form::textarea('content',null,['class'=>'form-control']) !!}

    {!! Form::submit('发表文章',['class'=>'btn btn-success form-control']) !!}

{!! Form::close() !!}
```

### 获取表单内容

articles/store函数的``$request->all()``就可以获取全部的提交信息
``$request->get('label-name')`` 可以获取相应的表单数据



# 语法
1. if判断
```
@if(true)
    ……
@endif
```

2. 循环迭代
```
@foreach($array in obj)
    ……
@endforeach
```


  [1]: http://wiki.jikexueyuan.com/project/laravel-5.1
  [2]: http://laravel-china.org/docs/5.1
  [3]: https://www.virtualbox.org/wiki/Downloads
  [4]: http://www.vagrantup.com/downloads.html
