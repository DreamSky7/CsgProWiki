---
description: 脚本的准备部分工作
---

# 预处理部分

直接上图，不多哔哔

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>一个示例的CsgTask文件</p></figcaption></figure>

从示例的CsgTask文件中我们可以看到CsgTask有两部分内容由###（至少3个） 进行分割，上方的部分则是预处理的部分，下方的部分则是写监听逻辑和方法逻辑的地方。

我们来逐一说说预处理部分的含义和支持的用法。

#### macro

macro在预处理部分的作用是有着查缺补漏的效果，即定义此文件需要存在当前宏的定义才能正常运行，如果没有则提示缺少宏定义，具体的写法如下：

```
macro [宏名称] [默认值]
```

如示例中的宏如果不存在于宏定义文件Macro中，则会在Macro中创建一个宏，并提示管理员需要设置默认值才能正常使用这个CsgTask脚本。

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>脚本中设置了Macro需要存在名为version的宏，右边Macro定义文件中不存在这个宏</p></figcaption></figure>

这时候重载插件会发现Macro会自动创建缺失的预处理，如果存在默认值还会补齐默认值

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>重载后的Macro文件中自动创建了预处理需要的宏</p></figcaption></figure>

#### depend

depend主要用于规定脚本的使用需要存在于哪些插件，例如上面例图中的depend Vault则是需要服务器中安装depend插件才可正常运行脚本。

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>缺失依赖将使CsgTask无法运行</p></figcaption></figure>

_**有一个很关键的点，depend和macro更多是为模块的开发者准备的，当你的模块需要考虑分享给他人使用的时候你就可以使用来避免他人缺失内容导致的加载失败。当然也可以是对自己的约束。**_



#### restrict

restrict的主要重要就是控制脚本的作用域，例如当前文件中的Listener监听和function仅对指定队列中的玩家生效，可防止不同队列的同等监听同时触发的问题。\


<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>两个不同的CsgTask触发器分别对应不同的作用域</p></figcaption></figure>

示例中两个文件分别有着不同的restrict控制，其中restrict Main则是对于Main队列中的玩家有效，也就是说Main队列击杀玩家会被提示“大厅禁止杀戮” ，另外一边则是需要在Red队列中才会触发
