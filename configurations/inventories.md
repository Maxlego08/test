# 👨‍💻 菜单

## 信息

该插件包括一个 `inventories` 文件夹，用于存储所有的菜单。每个菜单由一个单独的文件表示。你可以创建任意数量的菜单，也可以创建子文件夹来组织它们。

在默认配置中，你会看到如下结构：

```
|- inventories
  |- test
    |- test3
      - example3.yml
    - example2.yml
  - example.yml
  - example_shop.yml
  - example_punish.yml
```

***

## 语法

```yaml
name: "<菜单名称>"
size: <菜单大小>
fillItem: <物品堆>
updateInterval: <更新间隔>
clearInventory: <true/false>
items: <按钮>
open_requirement: <要求>
```

***

### 名称

```yaml
name: "<菜单名称>"
```

菜单的显示名称。请注意，根据你的版本，可能会有字符限制。你可以在名称中使用颜色和占位符。

如果你的菜单有多个页面，你可以使用以下占位符显示当前页面和最后页面：

* `%page%` - 当前页面号码
* `%maxPage%` - 最后一页号码

***

### 大小

```yaml
size: <菜单大小>
```

设置菜单的大小。默认值为 54。菜单的大小必须是 9 的倍数，范围从 **9** 到 **54**。有效的值包括：

* 9
* 18
* 27
* 36
* 45
* 54

***

### 填充物品

```yaml
fillItem: <物品堆>
```

允许你用相同的物品堆填充所有槽位。详情请参见 [物品信息](items.md)。

***

### 更新间隔

```yaml
updateInterval: <更新间隔>
```

允许你定义菜单中按钮的刷新间隔（以毫秒为单位）。为了使按钮得到更新，必须启用更新选项。更多信息请参见 [这里](buttons/#update)。

***

### 清空菜单

```yaml
clearInventory: <true/false>
```

允许你在打开时清空玩家的菜单，并在关闭时恢复。这项功能可以让你在菜单中显示图片而不被玩家的物品遮挡。

***

### 布局

YAML 文件中的布局配置允许直观地组织 Minecraft 菜单中的物品，通过提供槽位排列的视觉表示。在示例中，一个名为 `&8Test` 的 54 槽菜单使用字符布局，其中 'A' 代表用钻石填充的槽位，创建了一个带边框的布局。这种方法提高了清晰度和设计效率，因为布局中的每个字符都对应 `items` 部分中定义的一个物品，从而简化了菜单布局的自定义。

使用布局简化了复杂菜单设计的创建，通过可视化映射物品放置位置来实现。

```yaml
name: "&8Test"
size: 54
matrix:
  - "AAAAAAAAA"
  - "A       A"
  - "A       A"
  - "A       A"
  - "A       A"
  - "AAAAAAAAA"
items:
  A:
    item:
      material: DIAMOND
```

***

### 物品

```yaml
items: <按钮>
```

**按钮列表：** 详细信息请参见 [这里](https://zmenu.groupez.dev/configurations/buttons)。

***

### 使用物品打开

通过与物品的互动打开菜单。你必须定义物品的详细信息、要执行的操作（完整列表 [这里](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html)），以及所需的验证类型。

```yaml
# 通过点击特定物品打开此菜单
# 你可以使用 /zm giveopenitem <inventory> <player> 来获取使用的物品
#
openWithItem:
  # 定义将被点击的物品
  item:
    material: compass
    name: "&e打开基础菜单"
    lore:
      - "&7点击我！"
  # 查看 https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html
  actions:
    - RIGHT_CLICK_BLOCK
    - RIGHT_CLICK_AIR
  # 定义验证类型。
  # 根据你的配置和需求，你将定义某种验证类型。以下是所有存在的类型：
  # - full -> 允许完全检查 ItemStack，将使用 ItemStack#isSimilar 方法。
  # - material -> 仅检查材料
  # - name -> 仅检查显示名称
  # - lore -> 仅检查 lore
  # - modelid -> 仅检查自定义模型 ID
  type: full
```

***

### 打开要求

更多信息 [请点击这里](buttons/requirements.md#open-requirement)。

## 翻译名称

允许你翻译玩家菜单的名称。

```yaml
# 菜单名称 (https://docs.zmenu.dev/configurations/inventories#name)
#
# 这是你菜单的标题。你可以在其中放置任何内容。
# 支持颜色代码和占位符。
# 如果你使用的是 Paper、Purpur 或 PufferFish，你可以使用 MiniMessage 的颜色代码 (https://docs.advntr.dev/minimessage/format.html)
#
name: "&7基础菜单"

# 将菜单名称翻译成多种语言
# 你必须定义所用的语言和国家
# 原版 Minecraft 客户端将使用小写语言/国家对，以下划线分隔，但自定义资源包可以使用任何格式。
translatedName:
  - locale: "fr_fr" # 定义为法语
    name: "&aInventaire Basique"
  - locale: "es_es" # 定义为西班牙语
    name: "&aInventario Básico"
```

## 模板

创建了你的 [模板](patterns.md) 后，你可以像这样将它们添加到菜单中：

```yaml
size: 54

name: "&4高级 &c菜单 &7%page%&8/&7%maxPage%"
patterns:
  - "pattern_example"
```

你必须将文件名放在 `patterns` 文件夹中。你可以添加任意数量的模板。

来自 zAuctionHouseV3 的示例：

```yaml
name: '&8ᴀᴜᴄᴛɪᴏɴ &8(&f%page%&8/&f%maxPage%&8)'  # 菜单标题，支持颜色代码和占位符

size: 54  # Minecraft 菜单菜单的大小，必须是 9 的倍数

patterns:  # 菜单中使用的模板标识符列表
  - "zauctionhouse_decoration"  # 装饰元素的模板
  - "zauctionhouse_pagination"  # 菜单分页的模板
  - "zauctionhouse_auction"  # 与拍卖项或功能相关的模板

items:
  displayItems:
    type: ZAUCTIONHOUSE_AUCTION  # 显示的项目类型，特定于拍卖行物品
    isPermanent: true  # 指示这些项目将始终显示，不会动态更新
    slots:  # 指定菜单中物品的槽位
      - 10-16  # 项目占据 10 到 16 槽
      - 19-25  # 项目占据 19 到 25 槽
      - 28-34  # 项目占据 28 到 34 槽
      - 37-43  # 项目占据 37 到 43 槽
    else:
      slots:
        - 22
      item:
        material: BARRIER
        name: '&c&n未找到物品'
```

拍卖菜单将使用三个模板：一个用于装饰，一个用于管理分页，一个用于显示主要按钮（如已购买的物品、过期物品、类别等）。你只需要单独定义列出待售物品的按钮。

使用模板可以减少配置文件的大小，并在多个菜单中重复使用它们。
