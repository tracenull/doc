# 服务管理脚本
执行完框架安装后，可以在你的项目根目录下，看多一个easyswoole的文件。
执行以下命令：
```
php easyswoole
```
可见：
```
 ______                          _____                              _
 |  ____|                        / ____|                            | |
 | |__      __ _   ___   _   _  | (___   __      __   ___     ___   | |   ___
 |  __|    / _` | / __| | | | |  \___ \  \ \ /\ / /  / _ \   / _ \  | |  / _ \
 | |____  | (_| | \__ \ | |_| |  ____) |  \ V  V /  | (_) | | (_) | | | |  __/
 |______|  \__,_| |___/  \__, | |_____/    \_/\_/    \___/   \___/  |_|  \___|
                          __/ |
                         |___/

欢迎使用为API而生的 easySwoole 框架 当前版本: 3.x

使用:
  easyswoole [操作] [选项]

操作:
  install       安装easySwoole
  start         启动easySwoole
  stop          停止easySwoole
  reload        重启easySwoole
  help          查看命令的帮助信息

有关某个操作的详细信息 请使用 help 命令查看 
如查看 start 操作的详细信息 请输入 easyswoole help -start
```

## 服务启动
开发模式： 
```
php easyswoole start
```
## 守护模式启动
```
php easyswoole start d
```
## 生产环境(默认配置加载dev.php,使用该命令加载produce.php  3.1.2之前是dev.env,produce.env)
```
php easyswoole start produce
```
## 服务停止
```
php easyswoole stop
```
> 注意，守护模式下才需要stop，不然control+c或者是终端断开就退出进程了

## 重启服务
```
php easyswoole reload 只重启task进程
php easyswoole reload all  重启task + worker进程
```
> 注意，守护模式下才需要reload，不然control+c或者是终端断开就退出进程了，此处为热重启，可以用于更新worker start后才加载的文件（业务逻辑），主进程（如配置文件）不会被重启。

## 文件热加载

由于 `swoole` 常驻内存的特性，修改文件后需要重启worker进程才能将被修改的文件重新载入内存中，我们可以自定义Process的方式实现文件变动自动进行服务重载

相关示例请查看

- [热重载DEMO](https://github.com/easy-swoole/demo/blob/3.x/App/Process/HotReload.php)
- [热重载实现原理](https://www.easyswoole.com/Manual/3.x/Cn/_book/Othe/HotReload.html)