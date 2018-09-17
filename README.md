

adb定义：

adb(Android Debug Bridge) 安卓调试桥，包含adb client、adb server和adbd三部分。

adb client：运行在PC上，即DDMS或者在Windows dos下启动的adb shell

adb server：运行在PC上，作为adb client的server端，也作为adbd服务进程的客户端

adbd 服务进程：运行在Android系统上，以服务进程运行

三者的关系图：




   
   
```
bogon:~ wenweichen$ adb
Android Debug Bridge version 1.0.40
Version 4986621
Installed as /Users/wenweichen/Library/Android/sdk/platform-tools/adb

global options:
 -a         listen on all network interfaces, not just localhost
 -d         use USB device (error if multiple devices connected)
 -e         use TCP/IP device (error if multiple TCP/IP devices available)
 -s SERIAL  use device with given serial (overrides $ANDROID_SERIAL)
 -t ID      use device with given transport id
 -H         name of adb server host [default=localhost]
 -P         port of adb server [default=5037]
 -L SOCKET  listen on given socket for adb server [default=tcp:localhost:5037]
```


下面是 adb devices 命令和其执行结果：

$ adb devices
List of devices attached 
emulator-5554  device
emulator-5556  device
emulator-5558  device
如果没有模拟器或手机在运行，运行 adb devices 命令的执行结果如下：

$ adb devces
List of devices attached
操作指定模拟器或手机
如果有多个模拟器或手机正在运行，当使用 adb 命令的时候就需要指定目标设备，这可以通过使用 -s 选项参数实现，用法如下：

adb -s <serialNumber> <command>
你可以使用 adb 命令指定序列号在特定的设备上执行命令，这里可以先使用前面提到的 adb devices 命令查询设备的序列号信息。

例如：

adb -s emulator-5556 install helloWorld.apk


```
adb install [-lrtsdg] <path_to_apk>
(-l: 锁定该程序)
(-r: 重新安装该程序，保留应用数据)
(-t: allow test packages)
(-s: 将应用安装到 SD卡，不过现在手机好像都没有 SD卡 了吧)
(-d: 允许降版本号安装，当然只有 debug 包才能使用)
(-g: 安装完默认授予所有运行时权限，这个应该对 Android 6.0 及之后的版本才有效吧)
```



```
//<package> 表示要卸载应用的包名
adb uninstall [-k] <package>
(-k:不删除程序运行所产生的数据和缓存目录)
```
