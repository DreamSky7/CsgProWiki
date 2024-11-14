---
description: 基础模块仅提供于加入房间的玩家的常规处理
---

# 示例：基础模块

<pre><code>restrict Main

###

# 监听玩家加入大厅
listener onPlayerJoinLobby()
    if({lobby_player_amount} > {max_player})
        leave() @p
        end()
    
    # 触发下方的对应的方法
    onJoinSuccess() @p

    if({lobby_player_amount}=={min_player})
        # 触发下方对应的监听
        onPlayerEnough()
    
    if({lobby_player_amount}=={max_player})
        # 触发下方对应的监听
        onPlayerFull()
        
listener onPlayerLeaveLobby()
    notice({module_prefix} &#x26;7玩家 &#x26;f{striker} &#x26;7离开了游戏！)
    
<strong>listener onPlayerEnough()
</strong>    title(&#x26;a即将开始！,&#x26;7游戏将于 &#x26;b{wait_time} &#x26;7秒后开始,10,15,10) @e
    setscore(temp_timecount,{wait_time})
    actionbar(&#x26;7本场游戏将于 &#x26;b&#x26;o{wait_time}s &#x26;7开始) @e
    while({temp_timecount} > 0)
        delay(20)
        if ({lobby_player_amount} &#x3C;{min_player})
            onPlayerEnoughCancel()
            end()
        setscore(temp_timecount,~-1)
        
        if({isFull} == 1 )
            if({temp_timecount} > {full_time})
                setscore (temp_timecount,{full_time})
        actionbar(&#x26;7本场游戏将于 &#x26;b&#x26;o{temp_timecount}s &#x26;7开始) @e
        onLobbyTimeCount({temp_timecount})
    onLobbyStart()

listener onPlayerEnoughCancel()
    notice({module_prefix} &#x26;c由于人数不足，游戏倒计时已取消。)

# 自定义方法
function onLobbyTimeCount(tc)
    #参数tc是时间
    if({tc}&#x3C;6)
        title(&#x26;b&#x26;l{tc}s,&#x26;7即将开始,10,15,10) @e

listener onPlayerFull()
    notice({module_prefix} &#x26;a&#x26;n玩家已满计时加速，游戏马上开始！) @p
    macro(isFull,1)
    # 关闭房间的加入
    close()

function onJoinSuccess()
    teleport({joinLocation}) @p
    
    # 可以在加入成功给玩家设定血量和清空玩家背包等操作
    setproperty(maxhealth,{maxhealth}) @p
    setproperty(health,{maxhealth}) @p
    # 清空玩家背包物品
    clear() @p

    if ({lobby_player_amount} >= {min_player})
        notice({module_prefix} &#x26;7玩家 &#x26;f{striker} &#x26;7加入了游戏 [&#x26;a{lobby_player_amount}&#x26;8/&#x26;a{max_player}&#x26;7])
        # 结束当前语句，这里的 end() 代表下面的不会继续执行了
        end()
    notice({module_prefix} &#x26;7玩家 &#x26;f{striker} &#x26;7加入了游戏 [&#x26;a{lobby_player_amount}&#x26;8/&#x26;a{max_player}&#x26;7])
    notice({module_prefix} &#x26;7玩家人数达到 &#x26;a{min_player} &#x26;7后方可开始游戏)
</code></pre>

我们额外说明一下 **onPlayerJoinLobby()** 部分，可以注意到在判断中出现了两个变量

* **max\_player：**max\_player是Marco.yml文件中预处理的宏
* **lobby\_player\_amount：**CsgPro在房间存在阶段会刷新的内置宏，这个宏是一直存在的，并会一直更新，其对应的就是大厅的玩家数量

