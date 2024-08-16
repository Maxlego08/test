---
description: 配置插件所需的所有信息
---

# ℹ️ 信息

### 链接

在开始配置插件之前，请确保你使用的材料名称与你所使用的版本相匹配。

👉 我们建议你通过以下链接检查材料名称：

* [1.8.8](https://helpch.at/docs/1.8.8/org/bukkit/Material.html)
* [1.12.2](https://helpch.at/docs/1.12.2/org/bukkit/Material.html)
* [1.13.2](https://helpch.at/docs/1.13.2/org/bukkit/Material.html)
* [1.14.4](https://helpch.at/docs/1.14.4/org/bukkit/Material.html)
* [最新](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) (1.21)

\-> 对于声音的配置，你必须使用 [XSound](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java) 的值。

\-> [附魔](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

\-> [药水效果](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html)

\-> [物品标志](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html)

\-> [Minecraft-heads](https://minecraft-heads.com/) (Minecraft 头颅可以帮助你获取用于显示头颅的 base64 值)

\-> 对于颜色，你可以使用 Minecraft 颜色代码 `&<code>`。对于高于 1.16 的版本，你可以使用十六进制颜色，如 `#<color>`（例如，`#ff55ff`）。

{% hint style="info" %}
如果你的服务器使用了 Kyori Adventure（如 Paper 或其任何 Paper 分支），你可以使用 [Mini message 格式](https://docs.adventure.kyori.net/minimessage/format.html)。
{% endhint %}

### 信息

该插件的运作方式不同于其他菜单插件。我们有一个 `Button` 系统，可以让你执行各种操作。这个系统还允许其他开发者轻松地向插件的配置中添加功能。

我们将探讨不同类型的默认按钮及其配置元素。但首先，让我们来看看一个菜单文件的结构。
