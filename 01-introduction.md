
Basic LuCI development Info
===========================

Model-View-Controller (MVC)
---------------------
MVC是一种将响应数据分离于用户界面的技术。这种技术架构在LuCI系统中被用到

LuCI使用已存在的UCI配置文件作为数据模型。使用一种叫做CBI的语言将UCI文件转化为可视化的HTML表单。控制器是由一些在LuCI目录中的lua脚本完成。

LuCI目录结构
---------------------

LuCI目录所在位置：

    /usr/lib/lua/luci/

一般路由器的缺省资源文件目录：

RESOURCES: LuCI资源文件夹 (images, js, css, and html assets) ，它不含theme相关的内容。

    /www/luci-static/resources/

MEDIA: LuCI当前theme的资源文件

    /www/luci-static/commotion/

	
LuCI配置文件
--------------------

'core' 'main': 这里都是一些诸如缺省路径，开启网络接口和语言设置之类的基本设置。

'extern' 'flash_keep': 需要在sysupgrade时候保存的配置。详见：https://forum.openwrt.org/viewtopic.php?id=23194 for more info on customization

'internal' 'languages': LuCI支持的语种缩写。

'internal' 'sauth': 指定sessions的存放位置及admin用户有效登陆时长。

'internal' 'ccache':  LuCI模块缓存. See: 06-debugging module of this repo for an in depth overview.

'internal' 'themes': LuCI当前支持的themes。

CBI
---

CBI模型
CBI模型是一些LUA程序文件，用于分析UCI配置文件和生成HTML表单的CBI解析器。

CBI解析器入口在以下目录所示的文件中

    /usr/lib/lua/luci/cbi.lua

CBI还使用了一组数据原型。这些数据原型实质上是一些Lua函数，它使用JavaScript在客户端动态验证用户输入。

    /usr/lib/lua/luci/cbi/datatypes.lua

我将会在04-model-cbi中详细讨论该模型。

LuCI应用程序接口
-------------

虽然只需简单使用CBI接口就可以使用OpenWRT程序的UCI，但要实现更复杂的功能或在UCI不兼容的程序中使用，会要求你写你自己的Lua脚本。LUCI拥有强大的Lua函数集与OpenWRT进行交互。

API文档 - http://luci.subsignal.org/api/luci/

Nixio
-----
Nixio is the "Networking and I/O library for Lua." Nixio is the low level Lua code that powers the LuCI API. IF you are looking for Lua hooks for specific networking and I/O tasks that too far abstracted by the LuCI libraries, here is where you need to look.

API Documentation - http://luci.subsignal.org/api/nixio/
Source - http://luci.subsignal.org/trac/browser/luci/trunk/libs/nixio


The LuCI development Environment
-----------------------------

To use the LuCI development environment you can simply run 'make luci' from the luci_tutorials folder to use the simple makefile I have written to automate the process. It will echo out the command to run once it is finished gathering the needed files.

If you are missing dependencies you can go to the online guide to get requirements:

    http://luci.subsignal.org/trac/wiki/Documentation/DevelopmentEnvironmentHowTo


Executing a LuCI command from the Linux shell
--------------------------------------------

Note:
-l     Used to load the module
-e    Executes some lua script

root@OpenWrt:~# lua -lluci.sys -e 'print(luci.sys.sysinfo())'


Config file for init-scripts and dependences
--------------------------------------------
/etc/config/unitrack


