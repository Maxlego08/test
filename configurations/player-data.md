---
description: 玩家数据系统
---

# 🛝 玩家数据

使用 zMenu，你可以为玩家存储数据并通过占位符使用这些数据。这样，你可以创建计数器、冷却时间等等！

每个数据包含一个键、一个值和一个到期日期。如果你设置为 **0**，那么数据将永不过期。到期日期是一个时间戳。

## 命令

使用这些命令的权限为：`zmenu.players`

<table><thead><tr><th width="410">命令</th><th>描述</th></tr></thead><tbody><tr><td>/zm players</td><td>显示玩家数据的命令列表。</td></tr><tr><td>/zm players set &#x3C;player> &#x3C;key> &#x3C;expiration> &#x3C;value></td><td>设置新的玩家数据。你必须设置到期时间（以秒为单位）。设置为 0 表示没有到期时间。</td></tr><tr><td>/zm players remove &#x3C;player> &#x3C;key></td><td>移除玩家数据。</td></tr><tr><td>/zm players get &#x3C;player> &#x3C;key></td><td>获取玩家数据。</td></tr><tr><td>/zm players keys &#x3C;player></td><td>返回玩家的键列表。</td></tr><tr><td>/zm players clear &#x3C;player></td><td>清除玩家数据。</td></tr><tr><td>/zm players clearall</td><td>清除所有玩家的数据。</td></tr><tr><td>/zm players add &#x3C;player> &#x3C;key> &#x3C;value></td><td>将一个数值添加到某个值，仅适用于数字。</td></tr><tr><td>/zm players subtract &#x3C;player> &#x3C;key> &#x3C;value></td><td>从某个值中减去一个数值，仅适用于数字。</td></tr></tbody></table>

## 占位符

占位符可以用于物品栏中，用于显示物品或权限。你可以使用占位符阻止对按钮的访问。你可以在[这里](../plugins-files.md)查看示例。

<table><thead><tr><th width="426.56591923371104">占位符</th><th>描述</th></tr></thead><tbody><tr><td><code>%zmenu_player_value_&#x3C;key>%</code></td><td>返回键中包含的值。</td></tr><tr><td><code>%zmenu_player_expire_format_&#x3C;key>%</code></td><td>根据键返回格式化的到期时间。</td></tr><tr><td><code>%zmenu_player_expire_&#x3C;key>%</code></td><td>根据键返回到期时间。</td></tr><tr><td><code>%zmenu_player_key_exist_&#x3C;key>%</code></td><td>返回 true 或 false，判断某个键是否存在。</td></tr></tbody></table>
