# 🎨 Listener 内置监听

{% hint style="info" %}
监听器可以自定义，具体如何自定义可以在 可选语法 - CsgTask - 监听器介绍中了解如何使用
{% endhint %}

## 房间控制类

### onLobbyLoaded()

> 当游戏房间加载的时候触发。

### onLobbyUnloaded()

> 当游戏房间卸载的时候触发。

### onGroupLoaded(name)

> 当队列加载的时候触发。
>
> 参数：
>
> * name 队列名称

### onGroupUnloaded()

> 当队列卸载的时候触发。

### onPlayerJoinLobby() @p

> 玩家加入游戏房间后触发

### onPlayerLeaveLobby() @p

> 玩家离开游戏房间后触发

### onPlayerJoinGroup(name) @p

> 玩家加入队列触发
>
> 参数：
>
> * name 队列名称

```
// 示例
listener onPlayerJoinGroup(name)
    tell(玩家 {player} 加入了队列 {name}) @p

```

### onPlayerLeaveGroup() @p

> 玩家离开队列触发

### onPlayerRest(amount)

> 游戏房间内人数变化触发，_**请注意镜像房间如果玩家清零会直接卸载镜像房间**_
>
> 参数：
>
> * amount 剩余的玩家数量

```
// 示例
listener onPlayerRest(amount)
    if({amount}== 1)
        tell(你的对手已经退出，即将结束比赛) @a
```

### onEverySecond()

> 游戏房间加载完成后每秒都会触发，可用来做计时



## 实体监听类

### onPlayerChat(message) @p

> 当玩家发送聊天消息时触发
>
> 参数:
>
> * message 发送的消息

```
// 示例
listener onPlayerChat(message)
    if({message} == 我同意)
      tell(你同意什么?) @p
    if({message} == 我拒绝)
      tell(你不能拒绝!) @p
```

### onKillPlayer(target) @p

> 当玩家击杀另一名玩家时触发
>
> 参数:
>
> * target 被击杀的玩家

```
// 示例
listener onKillPlayer(target)
    tell({striker} 爆干了玩家 {target}) @p
```

### onKillEntity(entity) @p

> 当玩家击杀某个生物触发
>
> 参数:
>
> * entity 被击杀生物的

```
// 示例
listener onKillEntity(entity)
    if({entity} == 霸王龙)
        tell(什么？这你都能赢？！) @p
```

### onPlayerDeath() @p

> 当玩家死亡时触发

### onPlayerDamaged(dmg, damager) @p

> 当玩家受到伤害的时候触发
>
> 参数:
>
> * dmg 伤害
> * damager 造成伤害的玩家

```
// 示例
listener onPlayerDamaged(dmg, damager)
    tell(玩家 {damager} 对你造成了 {dmg} 真实伤害！快跑！！！)@p
```

### onPlayerRespawn @p

> 当玩家重生后触发，**某些情况下可能出现异常，可以加个Delay(5)保证正常触发**

```
// 示例
listener onKillPlayer()
    delay(5)
    tell(你重生了！) @p
```

### onPlayerBreakBlock(block, location) @p

> 当玩家破坏了某个方块后触发
>
> 参数:
>
> * block 被破坏的方块名称
> * location 被破坏的方块位置

### onInteractBlock(block, location) @p

> 当玩家点击了某个方块后触发
>
> 参数:
>
> * block 被破坏的方块名称
> * location 被破坏的方块位置

### onInteract(striked, uuid) @p

> 玩家右键某个生物触发
>
> 参数:
>
> * striked 被交互的生物名称
> * uuid 被交互的的生物UUID  ✅ CsgPro 2.0.4+

### onSendCommand(args) @p

> 玩家执行指令时触发
>
> 参数:
>
> * args 执行的指令

### onPlayerSneck() @p

> 玩家半蹲时触发（SHIFT）

### onPlayerWalk(block) @p

> 玩家移动时触发，**实际上不移动也触发**
>
> 参数:
>
> * block 踩着的方块

```
// 示例
listener onPlayerWalk(block)
    if({block} == DIAMOND_BLOCK)
        tell(你踩在钻石上获得了神龙之力) @p
```
