---
description: 全局变量预处理文件
---

# Macro.yml

> Macro是预处理全局变量的文件，用于将预载的全局变量提前申明，该文件内的宏会在Lobby加载的时候同时被读取，因此你可以将需要被提前预载的全局变量置于其中。
>
> 除此之外，在2.0.3版本后会有一些系统宏关键字也在这部分进行读取，例如白名单命令的宏（command\_whitelist）以及镜像副本的(world)等。



#### 镜像房间世界宏

> 每个房间在加载的时候都会存在一个world宏变量，如果非镜像房间则默认指向world世界，但是当你的房间属于镜像房间的时候，这个宏则会指向当前镜像所创建的世界。

因此你应该在Macro.yml使用 {world} 宏来传送玩家到正确的房间世界

```yaml
# 加入游戏点 传送到当前房间的世界
joinLocation: "{world};14.5;-60.0;12.5"

# 离开不建议使用{world} 因为离开房间应该返回到一个固定的世界
leaveLocation: "world;14.5;60.0;12.5"
```

#### 特殊宏

*   指令白名单 command\_whitelist

    > 该宏是特殊宏，会在设定值的时候才会有作用，用于设定那些指令是运行在Lobby房间内使用的，默认情况下非OP将会禁止所有指令



    ```yaml
    # 设定可以使用的命令
    command_whitelist:
     - "spawn"
     - "cmi homes"
    ```
