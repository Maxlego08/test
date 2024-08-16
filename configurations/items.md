# 🪁 物品

在开始配置插件的 itemstack 之前，请确保你使用了适合你游戏版本的材料。每个按钮必须附带一个 itemstack（某些特定情况下除外）。

```yaml
item:
  material: <物品材质>
  amount: <数量>
  data: <材质数据, 仅适用于 1.8 到 1.12 版本>
  durability: <耐久值>
  url: <玩家皮肤的 base64>
  name: <显示名称>
  lore: <文本列表>
  potion: <药水效果类型>
  level: <药水等级>
  splash: <药水飞溅 true 或 false>
  extended: <药水扩展 true 或 false>
  glow: <添加发光效果>
  modelID: <自定义模型 ID>
  enchants: <附魔列表>
  flags: <物品属性列表>
  firework: <烟花元数据>
  banner: <旗帜颜色>
  patterns: <旗帜图案>
  color: <皮革护甲颜色>
```

## 材质

```yaml
material: <物品材质>
```

物品的材质。你可以使用占位符来显示材质。

> **支持的材料值：**
>
> * [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) - 示例：`material: STONE`
> * [占位符](https://www.spigotmc.org/resources/placeholderapi.6245/) 值 - 示例：`material: %your_placeholder_material%`
> * 免费 - [zHead](https://www.spigotmc.org/resources/zhead-database.115717/) **推荐** (zhd:\<id>) 示例：`material: zhd:<id>`
> * 付费 - [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (hdb:\<id>) 示例：`material: hdb:<id>`
> * 付费 - [Oraxen](https://www.spigotmc.org/resources/%E2%98%84%EF%B8%8F-oraxen-add-items-blocks-armors-hats-food-furnitures-plants-and-gui-1-18-1-20-1.72448/) (oraxen:\<item name>) 示例：`material: oraxen:<item name>`
> * 付费 - [ItemAdder](https://www.spigotmc.org/resources/%E2%9C%A8itemsadder%E2%AD%90emotes-mobs-items-armors-hud-gui-emojis-blocks-wings-hats-liquids.73355/) (itemsadder:\<item name>) 示例：`material: itemsadder:<item name>`
> * 免费 - [SlimeFun](https://github.com/Slimefun/Slimefun4) (slimefun:\<item name>) 示例：`material: slimefun:<item name>`
> * 免费 - [Nova](https://github.com/xenondevs/Nova) (nova:\<item/block name>) 示例：`material: nova:<item/block name>`
> * Base64 (base64:\<item in base64>) 使用命令 `/zm save <item name> base64` 获取此值
> * [PlayerHead](buttons/#playerhead) (playerHead: \<player name>) 显示玩家的头部。示例：`playerHead: "%player%"` 显示打开菜单的玩家的头部

***

## 数量

```yaml
amount: <amount>
```

物品堆叠的数量。你可以使用占位符来动态设置数量。

***

## 数据

```yaml
data: <data, 仅适用于 1.8 到 1.12 版本>
```

物品的材质数据，仅适用于 1.8 到 1.12 版本。默认值为 0。

***

## 耐久值

```yaml
durability: <耐久值>
```

物品的耐久值，默认值为 0。

***

## URL

```yaml
url: <玩家皮肤的 base64>
```

允许你显示一个 base64 编码的头部。你可以在网站 [minecraft-head.com](https://minecraft-head.com) 上找到头部的值。

你需要获取 "Value" 字段中的内容（在 "Other" 类别下）。

![minecraft-head.com 示例值](../.gitbook/assets/base64.png)

示例

```yaml
url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNjM3YjhhMzk4MzdiYzNkNThmMDljOGM2ZTUzOTYyZDMzZjlmYTBiNjUzOThhNzc5MzUzYWRlMWUxNDcxM2VmZiJ9fX0="
```

***

## 名称

```yaml
name: <显示名称>
```

物品上显示的名称。你可以使用 PlaceholderAPI 来动态设置名称。

{% hint style="info" %}
如果你的服务器有 Kyori Adventure，你可以使用 [mini message 格式](https://docs.adventure.kyori.net/minimessage/format.html)。
{% endhint %}

***

## 说明

```yaml
lore:
  - <line1>
  - <line2>
  - <line3>
  - ...
```

允许你显示物品的说明。你可以使用 PlaceholderAPI 来动态设置说明。

***

## 药水

```yaml
  potion: <药水效果类型>
  level: <药水等级, 1 或 2> # 默认 1
  splash: <药水飞溅 true 或 false>
  extended: <药水扩展 true 或 false>
```

允许你创建药水。详细的药水效果类型请参见 [这里](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionType.html)。

{% hint style="danger" %}
警告：药水不能同时扩展并且有等级 2。
{% endhint %}

{% hint style="info" %}
```yml
# 对于 1.8 到 1.12 的药水，你需要这样配置：
material: POTION
durability: 16454
```
{% endhint %}

***

## 发光

```yaml
glow: <true 或 false>
```

允许物品发光。添加随机附魔和 HIDE\_ENCHANT 物品标志。

***

## 模型 ID

```yaml
modelID: <custom model id>
```

允许你在物品上设置自定义模型 ID。

***

## 附魔

```yaml
enchants:
  - <enchantment name>,<enchantment level>
```

允许你添加附魔。你需要指定附魔名称和附魔等级，格式为：`ENCHANT,ENCHANT_LEVEL`。

可用附魔列表：[https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

***

## 物品属性

```yaml
flags:
  - <flag 1>
  - <flag 2>
  - ...
```

属性列表：[https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)

***

## 颜色

```yaml
type: LEATHER_CHESTPLATE
color: 40,150,40 # RGB 颜色

# 示例带 ARGB
color: 1,40,150,40 # ARGB 颜色，Alpha, RED, GREEN, BLUE
```

为皮革护甲设置 RGB 颜色。格式为：

`<Red>,<Green>,<Blue>`

例如，要设置颜色为 255 红色、100 绿色和 50 蓝色，你可以使用：

`255,100,50`

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;red>,&#x3C;green>,&#x3C;blue>
</strong></code></pre>

你还可以在颜色中添加 alpha 值以获得 ARGB（Alpha, Red, Green, Blue）。格式为：

`<Alpha>,<Red>,<Green>,<Blue>`

例如，要设置颜色为 128 alpha（半透明）、255 红色、100 绿色和 50 蓝色，你可以使用：

`128,255,100,50`

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;alpha>,&#x3C;red>,&#x3C;green>,<blue>
</strong></code></pre>

{% hint style="info" %}
烟花、旗帜和药水的颜色格式也使用 ARGB 格式：

`<Alpha>,<Red>,<Green>,<Blue>`

例如：

* **烟花**：设置颜色为 255 alpha（完全不

透明）、200 红色、150 绿色和 100 蓝色，你可以使用：`255,200,150,100`。
* **旗帜**：设置颜色为 255 alpha、100 红色、200 绿色和 50 蓝色，你可以使用：`255,100,200,50`。
* **药水**：设置颜色为 128 alpha（半透明）、255 红色、50 绿色和 50 蓝色，你可以使用：`128,255,50,50`。

有关更多详细信息，请参见 Color 的 Javadocs [这里](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Color.html#fromARGB\(int,int,int,int\))。
{% endhint %}

***

## 烟花

```yaml
type: FIREWORK
firework:
  star: true
  flicker: true
  trail: true
  type: BALL_LARGE
  colors:
    - 250,10,10 # RGB 和 ARGB
  fadeColors:
    - 250,10,250 # RGB 和 ARGB
```

烟花类型：[https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html)

***

## 旗帜

```yaml
type: BANNER
banner: PINK # 旗帜颜色
patterns: # 旗帜图案：<颜色>:<图案>
  - RED:SQUARE_BOTTOM_LEFT
  - GREEN:STRIPE_LEFT
```

允许你创建一个旗帜。图案列表：[https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html)

## 翻译名称

允许将物品的名称翻译成多种语言

```yaml
items:
  example:
    item:
      material: GRASS_BLOCK
      name: "&a这是一个非常漂亮的草方块"
      lore:
        - "" 
        - "&e我的第一个 zMenu 按钮"
        - "&7恭喜你，你将发现"
        - "&7zMenu 的所有可能性。"

      # 将物品名称翻译成多种语言
      # 你必须定义所用的语言和国家
      # 原版 Minecraft 客户端将使用小写的语言/国家对，用下划线分隔，但自定义资源包可能使用任何格式。
      translatedName:
        - locale: "fr_fr" # 定义为法语
          name: "&aC’est un très beau bloc d’herbe !"
        - locale: "es_es" # 定义为西班牙语
          name: "&a¡Es un hermoso bloque de hierba!"
```

## 翻译说明

允许将物品的说明翻译成多种语言

```yaml
items:
  example:
    item:
      material: GRASS_BLOCK
      name: "&a这是一个非常漂亮的草方块"
      lore:
        - "" 
        - "&e我的第一个 zMenu 按钮"
        - "&7恭喜你，你将发现"
        - "&7zMenu 的所有可能性。"

      # 将物品说明翻译成多种语言
      # 你必须定义所用的语言和国家
      # 原版 Minecraft 客户端将使用小写的语言/国家对，用下划线分隔，但自定义资源包可能使用任何格式。
      translatedLore:
        - locale: "fr_fr" # 定义为法语
          lore:
            - "" # 空行以在名称和说明之间添加空格
            - "&e我的第一个 zMenu 按钮"
            - "&7恭喜你，你将发现"
            - "&7zMenu 的所有可能性。"
        - locale: "es_es" # 定义为西班牙语
          lore:
            - "" # 空行以在名称和说明之间添加空格
            - "&e我的第一个 zMenu 按钮"
            - "&7恭喜你，现在你将发现"
            - "&7zMenu 的所有可能性。"
```
