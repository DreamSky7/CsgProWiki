---
description: 了解Lobby房间与Group的工作关系
---

# ⚡ Lobby 房间

### 文件结构

> 在认识Lobby之前我们需要知道CsgPro的文件结构，这将有助于我们知道房间的文件结构是怎么样的。首先你需要在Plugins文件夹中确认已经生成了CsgPro的文件夹确保插件正常运行

CsgPro （根目录）

* Lobby —— 文件夹
  * 房间1文件夹 —— 文件夹
    * xxxx.csgtask —— csgtask语法文件
    * xxxx.javatask —— javatask语法文件
    * Macro.yml —— 宏变量文件
  * 房间2文件夹 —— 文件夹
    * Macro.yml —— 宏变量文件
* Option.yml —— 配置文件

***

### 创建房间

> 可以看到Lobby文件夹是Lobby房间的创建位置，Lobby文件夹内的每个文件夹对应每个游戏房间Lobby，就上面的结构来看可以得到存在 “房间1” 和 “房间2” 两个游戏房间。
>
> 而房间里的CsgTask和JavaTask就是这个房间内的玩法的实现了。

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>一个示例的结构</p></figcaption></figure>

例图中可以看出存在3个游戏房间，除此之外你还可以使用 `/csg showlist` 来查看哪些房间已经被加载。然后就可以使用 `/csg join 房间名称`

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>/Csg ShowList 指令效果</p></figcaption></figure>

<mark style="color:red;">PS：从更长远的角度上将，尽量避免使用中文来命名文件夹（房间）的名称。</mark>
