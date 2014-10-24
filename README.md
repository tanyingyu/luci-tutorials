luci_tutorials
==============

<p>该“教程”只为了训练我做了LuCI。在未来的几个月里，我将开始实际工作形成一份谨慎的教程和文档，以便其他人可以利用这个工具包。</p>

<p>LuCI web界面慢慢地转移到一个JSON-RPC结构中，以减少对节点处理的消耗。通过关于如何构建CBI结构挂钩节点，最终允许浏览器插件和网站与启动LUCI的OpenWrt进行远程通信。</p>

TODO: 
 * 整理笔记添加更多的章节
 * 添加JSON-RPC章节和远程站点设计
 * 添加lua基本函数章节{比如：后台调用(shell [sys/util.exec(uci)], C [model.uci], 和 io [io.write(/etc/config/uciFile)])} 展示如何在嵌入式设备中更好的使用lua
