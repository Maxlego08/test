---
icon: square-terminal
---

# 指令

## 信息

插件包含一个 `commands` 文件夹，用于存放所有命令。你可以创建无限数量的命令。每个命令包括命令名称、别名、权限和要打开的菜单名称。\
你可以在一个文件中放置多个命令，并创建无限数量的文件。

```
|- commands
  |- punish
    - punish.yml
  |- example
    - example.yml    
  - commands.yml
```

## 语法

```yaml
commands:
  basic_command:
    command: basic_command
    inventory: basic_inventory
  advanced_command:
    command: advanced_command
    permission: "admin.use"
    aliases:
      - zai
    inventory: advanced_inventory
  pro_command:
    command: pro_command
    inventory: pro_inventory
  openbook:
    command: openbook
    actions:
      - type: book
        author: "Maxlego08" # 书作者
        title: "&cTest" # 书标题
        lines: # 书页
          1: # 第一页
            - '     #34ebe8zMenu'
            - ''
            - ''
            - '<hover:show_text:"#34eba8打开一个网址！"><click:open_url:"https://minecraft-inventory-builder.com/">#f0af24打开网址<reset>'
  punish:
    command: punish
    permission: "admin.punish"
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - name: target
      - name: reason
        auto-completion:
          - cheat
          - chat
          - skin
          - other
        actions:
          - type: message
            messages:
              - "&7你将对玩家 &f&n%target%&r &7施加惩罚，原因&8: &f%reason%"            
```

***

### 命令

```yaml
command: <command>
```

主命令

***

### 别名

```yaml
aliases:
  - <aliase 1>
  - <aliase 2>
  - ...
```

命令的别名。

***

### 操作

```yaml
actions:
  - ...  
```

你可以使用 [操作](buttons/actions.md) 来执行命令时总是执行的动作。

***

### 权限

```yaml
permission: <permission>
```

玩家必须具备的权限才能打开菜单。

***

### 菜单

```yaml
inventory: <inventory name>
```

要打开的菜单名称。

你也可以通过以下方式指定插件名称：

```yaml
inventory: "<plugin name>:<inventory name>"
```

***

### 参数

```yaml
arguments:
  - <arg1>
  - <arg2>
  - ...
```

允许你向命令添加参数。你可以使用以下占位符来引用参数：`%zmenu_argument_<argument name>%`&#x20;

#### 示例

```yaml
commands:
  punish:
    command: punish
    permission: "admin.punish"
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - name: target
      - name: reason
        auto-completion:
          - cheat
          - chat
          - skin
          - other
        actions:
          - type: message
            messages:
              - "&7你将对玩家 &f&n%target%&r &7施加惩罚，原因&8: &f%reason%"
```

你可以为每个操作定义一个 [操作](buttons/actions.md) 和自动补全列表。

你可以通过 `isRequired` 值来定义参数是否为必需。以下是一个示例。

你不能通过 `performMainAction` 值执行主命令的操作。

你可以运行 **`/punish <target> <reason>`** 命令。例如：`/punish Maxlego08 Cheat (fly)`。

通过占位符，你可以检索参数：

| 占位符                   | 结果        |
| ------------------------ | ----------- |
| `%zmenu_argument_target%` | `Maxlego08` |
| `%zmenu_argument_reason%` | `Cheat (fly)` |

你可以定义参数是否为可选项，以及参数是否具有特定菜单。

#### 示例（无必需参数）:

```yaml
commands:
  warp:
    command: warp
    aliases:
      - warps
    inventory: warp
    arguments:
      - name: warp
        isRequired: false # 设置参数为可选
        performMainAction: false # 不打开菜单
        auto-completion:
          - minapvp
          - cajas
          - dungeon
          - encantamientos
          - jugadores
          - mercado
          - minas
          - rankup
        actions:
          - type: player_command
            commands:
              - "essentials:warp %zmenu_argument_warp% %player%"
```

这个示例打开一个传送点菜单，然后使用参数将玩家传送到所需的传送点，使用了 essentials 的别名。
