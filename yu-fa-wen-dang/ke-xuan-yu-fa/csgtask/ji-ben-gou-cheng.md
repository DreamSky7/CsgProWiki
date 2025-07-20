---
description: 简单的CsgPro结构
---

# 基本构成

### 代码结构

```
restrict Main

###

listener onPlayerJoinLobby()
    tell({module_prefix} 玩家加入了房间) @p
```

* \###: 这里的作用只起到分割的效果，该分隔符以上的部分为是预处理部分，下面的部分就是写房间逻辑的部分，房间逻辑主要是由各式各样的监听组成的，使用起来只需要格式写对即可，例如上面的简单例子中的格式。

这其中还包含了一个变量，在CsgPro中变量的形式都是以 **{内容}** 的格式出现的，并且需要使用方法来定义对应的变量名和值，而例子中并没有关于变量的注册，这是因为其变量的注册是由Macro.yml提前定义的。

详细使用说明详见 [yu-chu-li-bu-fen.md](yu-chu-li-bu-fen.md "mention")和 [macro.yml.md](macro.yml.md "mention")两个篇章对于其功能的讲解



### 监听使用

> 基于不同的监听器会有不同的效果，有些可能是对实体行为的监听，如：玩家移动，玩家下蹲，玩家击杀生物等。有些是对于房间变化的监听，例如当房间加入玩家和房间离开玩家。

```
listener [监听器](变量映射)
    方法逻辑 @触发者
```

* **方法：**&#x53EF;以是CsgPro内置的方法也可以是由其他JavaTask提供的扩展方法等等。
* **监听器：**&#x53EF;以是CsgPro内置的监听也可以是自定义的监听器，自定义监听的效果是需要自己去实现的，或者主动触发。
* **变量映射：**&#x90E8;分监听器会有一定的回参，这里可以选择传入一个名称作为回参变量。
* **触发者：**&#x4EE3;表这个方法的目标是谁，例如使用 `tell(消息) @e` 来给所有玩家发送指定消息

```
listener onKillPlayer(target)
    tell(&7玩家 &f{striker} &7击杀了玩家 &f{target}) @a
```

上面的示例中展示的是一个玩家击杀玩家的监听器，当玩家击杀另一名后便会触发该监听器并执行监听器内的方法部分，这里tell则是起到一个发送消息的功能，发送的目标是由 **@a** 来决定，即对当前队列的所有玩家发送，其中的 {target} 是该方法的回参，我们使用其来接收后并在想用的位置进行输出

其&#x4E2D;**{striker}**&#x662F;一个固有变量，当监听器被某个玩家触发后，**{striker}** 代表的就是那个玩家

查看所有可用的方法可参考下面的链接

* [listener-nei-zhi-jian-ting.md](../../../kuo-zhan-wen-dang/listener-nei-zhi-jian-ting.md "mention")
* [function-nei-zhi-fang-fa.md](../../../kuo-zhan-wen-dang/function-nei-zhi-fang-fa.md "mention")
