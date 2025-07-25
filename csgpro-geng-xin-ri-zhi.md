---
description: 将会展示每个版本更新的内容
---

# CsgPro更新日志

### CsgPro 2.0.3 Version

> 主要对镜像副本的一些问题的优化

* 修复了高版本 Mohist(1.20.1) 核心无法正确的使用JavaTask的问题
* 修复了玩家能够在短时间创建多次镜像副本导致的一系列问题
* 添加了特殊宏 command\_whitelist 以设定在房间内允许使用的指令
* 添加了镜像房间创建日志并在每次启用插件时检查日志是否存在未删除的世界
* 添加PlaceholderAPI的支持（具体查看对应的文档）
* 添加WorldGuard插件的兼容
* 添加MangoTeam插件的兼容

> 开发者相关

* 默认生成Temp.java类已实现Listener接口

### CsgPro 2.0.4 Version

> 对MangoTeam扩展支持及部分功能增强

#### 内置方法

* **god：**&#x4F7F;目标进入无敌状态
* **Macro：**&#x589E;加了contains特殊符以返回列表是否包含指定值

#### 修复问题

* 修复了PlaceholderAPI兼容失败的消息重复发送的异常
* 修复了Lobby在停服时移除Redis数据的异常错误
* 修复了高低版本移除世界的卸载逻辑不同的问题
* 修复了JavaTask高版本的环境异常问题
* 修复了Lobby管理器并发状态下可能出现的问题

#### 更新内容

* 监听器 onInteract 增加了uuid的返回值
* 添加了扩展解析变量 {striker.group} 以获取玩家当前的队列名称
* 添加了扩展解析变量 {striker.group\_size} 以获取玩家当前队列的玩家人数
* 添加了扩展解析变量{target.uuid} 以获取实体的UUID
* 添加了**WorldGuard**插件存在时卸载世界会同时删除对应世界配置文件
* 优化了Csgtask文件解析器和编译器的代码
* <mark style="color:blue;">**现在Function会以同步的方式运行**</mark>
* <mark style="color:blue;">**新增onPlayerDamaged的内置变量$event**</mark>
* <mark style="color:blue;">**现在if支持else语句**</mark>



API更新

* **GroupAPI：**
  * 新增getGroupTeam() 方法以获取当前队列所创建的队伍

#### 附加更新

* MangoCore需求版本: 1.0.7
