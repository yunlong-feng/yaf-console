# v1.3.4 - 2018-05-20
 - 修改命名空间, 由 `PHPCasts\Console` 调整为 `PHPCasts\Yaf\Console` 
 - 修改命令文件名

# v1.3.3 - 2017-10-21
 - 修复运行make:controller时, 带 `--resource` 的报错
 - 格式化 `resource.stub` 模板文件
 
# v1.3.2 - 2017-08-21
 - 增加 `php bin/console serve` 命令

# v1.3.1 - 2017-08-21
 - 修改模板目录为Stubs 
 - 修改模板文件后缀为stub

## v1.3.0 - 2017-08-10
 - make:controller支持 `--resource` 参数, 可生成带REST风格的Controller
 
## v1.2.1 - 2017-08-04
 - fixed autoload namespace （'PHPCasts\\Console' -> 'PHPCasts\\Console\\'）
 
## v1.2.0 - 2017-08-04
 - 修改composer.json的autoload （'PHPCasts' -> 'PHPCasts\\Console'）

## v1.1.0 - 2017-08-02
 - 支持生成 module
 - fixed module name and controller name
 
## v1.0.0 - 2017-07-31
 - 支持生成 controller
 - 支持生成 model
 - 支持生成 plugin