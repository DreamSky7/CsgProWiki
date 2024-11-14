---
description: 部分变量可使用扩展的变量解析以获取更详细的数据
---

# 🍾 扩展解析变量

### 实体变量（包含实体和玩家）

> 请注意这里的target是一个举例子的变量，请结合实际情况使用

* **{target.uuid}** 返回实体的UUID
* **{target.health}** 返回实体的当前生命值
* **{target.max\_health}** 返回实体的最大生命值
* **{target.name}** 返回实体的名称
* **{target.location}** 返回实体的坐标

### 玩家变量（仅支持玩家使用）

* **{striker.group}** 返回玩家当前所在队列的名称 _`仅2.0.4+支持`_
* **{striker.group\_size}** 返回玩家当前所在队列的玩家人数 _`仅2.0.4+支持`_
* **{striker.level}** 返回玩家当前的等级
* **{striker.food}** 返回玩家当前的饥饿值
* **{striker.display}** 返回玩家当前的显示名称
* **{striker.item\_hand}** 返回玩家当前手中的物品名称

### 坐标变量（仅支持坐标使用）

> 请注意这里的location是一个举例子的变量，请结合实际情况使用

* **{location.x}** 返回坐标x值
* **{location.y}** 返回坐标y值
* **{location.z}** 返回坐标z值
* **{location.world}** 返回坐标的世界名称



### 数组变量（仅支持数据和列表）

> 请注意这里的testlist是一个举例子的变量，请结合实际情况使用

* **{testlist.random}** 返回数据中随机的一条数据
* **{testlist.x}** 返回数据中指定索引的数据，例如获取第二条数据 `{testlist.1}`
