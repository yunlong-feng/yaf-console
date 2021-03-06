# yaf-console

## 简介

快速生成对应的module、controller、model、plugin。

## 依赖

 - Yaf
 - Composer
 - Console文件

## 安装

```shell
composer require "phpcasts/yaf-console" -vvv 
```

## 配置

yaf配置开启:
 ```
 yaf.use_namespace = true
 yaf.use_spl_autoload = 1 
 ```

## 创建Console文件

```shell
cd /path/to/app_root    //cd到项目根目录
mkdir bin
vim bin/console
```

加入以下内容：
```php
#!/usr/bin/env php
<?php

define('APP_ROOT', dirname(__DIR__));
define('APP_PATH', APP_ROOT . '/application');
require APP_ROOT . '/vendor/autoload.php';

use Symfony\Component\Console\Application;

use PHPCasts\Yaf\Console\ModuleMakeCommand;
use PHPCasts\Yaf\Console\ControllerMakeCommand;
use PHPCasts\Yaf\Console\ModelMakeCommand;
use PHPCasts\Yaf\Console\PluginMakeCommand;
use PHPCasts\Yaf\Console\CheckCommand;
use PHPCasts\Yaf\Console\ServeCommand;

$application = new Application();

// ... register commands
$application->add(new ModuleMakeCommand());
$application->add(new ControllerMakeCommand());
$application->add(new ModelMakeCommand());
$application->add(new PluginMakeCommand());
$application->add(new CheckCommand());
$application->add(new ServeCommand());

$application->run();
```

## 创建 Server.php

在项目根目录，创建如下文件
vim server.php
```php
<?php

$uri = urldecode(
	parse_url($_SERVER['REQUEST_URI'], PHP_URL_PATH)
);

// This file allows us to emulate Apache's "mod_rewrite" functionality from the
// built-in PHP web server. This provides a convenient way to test a Laravel
// application without having installed a "real" web server software here.
if ($uri !== '/' && file_exists(__DIR__.'/public'.$uri))
{
	return false;
}

require_once __DIR__.'/public/index.php';
```

## 使用

```shell
php bin/console  // 查看可用命令
php bin/console make:module Web                         // 创建Web模块
php bin/console make:controller User                    // 创建控制器
php bin/console make:controller User --resource         // 创建含有增删改查的控制器
php bin/console make:controller Web/User                // 在Web模块下创建控制器
php bin/console make:controller Web/User  --resource    // 在Web模块下创建控制器
php bin/console make:model User                         // 创建模型
php bin/console make:plugin Test                        // 创建插件
// todo more

php bin/console serve                                   // 运行本应用
```

## 修改日志

详见 [Changelog](./CHANGELOG.md)
