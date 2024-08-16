---
description: 条件功能允许你基于权限检查执行操作
---

# 🏁 条件

## 条件

### 语法

```yaml
# open_requirement
# click_requirement
view_requirement:

  # 设置需要满足的最低条件数量才能被视为成功。
  # 默认值与条件数量相同。
  minimumRequirement: <number>
  
  # 条件列表，下面是每种类型的所有信息
  requirements:
    - type: permission
      permission: "example.permission"
      deny:
        - type: message
          messages:
            - "&c你没有权限！"
    - type: placeholder
      placeholder: "%player_gamemode%" # 需要PAPI ecloud Player
      value: "CREATIVE"    
      action: equals_string
      # 特定拒绝操作
      deny:
        - type: message
          messages:
            - "&c你必须在创造模式下"      
    - type: regex
      input: "%player_item_in_hand%" # 需要PAPI ecloud Player
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"      
      deny:
        - type: message
          messages:
            - "&c你手中没有物品！"
  
  # 全局成功操作
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
      
  # 全局拒绝操作
  deny:    
    - type: message
      messages:
        - "&c你手中没有物品。"
```

除了全局拒绝和成功操作外，你还可以为每个条件定义特定的拒绝和成功操作。

### 查看条件

定义玩家必须满足的要求才能在菜单中看到一个按钮。

#### 示例：

```yaml
view_requirement:
  deny:
    - type: chat
      messages:
        - "嘿，我的名字是 %player%"
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
  requirements:
    - type: permission
      permission: "admin.use"
    - type: placeholder
      placeholder: "%player_is_flying%"
      value: "yes"
      action: equals_string
```

### 打开条件

定义玩家必须满足的要求才能打开菜单。

#### 示例

```yaml
open_requirement:
  requirements:
    - type: regex
      input: "%player_item_in_hand%"
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"
  deny:
    - type: message
      messages:
        - "&c你手中没有物品。"
```

在下面的示例中，检查玩家手中的物品。如果物品匹配正则表达式模式，玩家可以打开菜单。否则，他们会收到一条消息，菜单不会打开。

### 点击条件

定义多个条件以点击按钮。你需要指定几个条件和相应的点击操作。

你可以使用以下格式直接应用所有点击：

```yaml
clicks:
  - ALL # 或者 ANY
```

你可以将点击类型设置为 `ALL` 或 `ANY` 来将操作应用于所有点击。点击列表可以在 `config.json` 文件中管理。

#### 示例：

```yaml
click_requirement:
  left_click: # 你必须为你的条件指定一个名称，这个名称不会被使用。
    clicks:
      - LEFT
      - SHIFT_LEFT
    requirements:
      - type: placeholder
        placeholder: "%player_gamemode%"
        value: "CREATIVE"
        action: equals_string
    deny:
      - type: sound
        sound: VILLAGER_NO
        pitch: 0.5f
        volume: 1.5f
    success:
      - type: message
        messages:
          - "&a左键点击！"
  right_click: # 你必须为你的条件指定一个名称，这个名称不会被使用。
    clicks:
      - RIGHT
      - SHIFT_RIGHT
    requirements:
      - type: placeholder
        placeholder: "%player_gamemode%"
        value: "CREATIVE"
        action: equals_string
    deny:
      - type: sound
        sound: VILLAGER_NO
        pitch: 1.5f
        volume: 0.5f
    success:
      - type: message
        messages:
          - "&a右键点击！"
```

## 条件类型

<table data-full-width="true"><thead><tr><th width="519">类型</th><th>描述</th></tr></thead><tbody><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: permission
  permission: &#x3C;permission>
</code></pre></td><td>检查玩家是否具有指定的权限。要反转条件，请在权限前面添加感叹号 <code>!</code>，例如：<code>!&#x3C;permission></code>。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: placeholder
  placeholder: &#x3C;placeholder>
  value: &#x3C;placeholder value>
  action: &#x3C;placeholder action>
  target: &#x3C;player / placeholder with player name>
</code></pre></td><td><p>允许使用占位符定义权限。你必须指定占位符、与值进行的操作以及要检查的值。有关更多信息，请点击此处。</p><p>你可以指定玩家；否则，将使用打开菜单的玩家作为默认值。</p></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: regex
  regex: &#x3C;regex>
  input: &#x3C;placeholder>
</code></pre></td><td><p>检查输入是否匹配指定的正则表达式模式。输入可以是一个占位符。</p><p>访问 <a href="https://regexr.com">regexr.com</a> 来创建你的正则表达式模式。</p></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: item
  material: &#x3C;material>
  amount: &#x3C;amount of item>
  modelId: &#x3C;model id> # 默认值为0
</code></pre></td><td>检查玩家的菜单中是否有特定物品。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: job
  job: &#x3C;job name>
</code></pre></td><td>检查玩家是否拥有该职业。与 <a href="https://www.spigotmc.org/resources/jobs-reborn.4216/">JobReborn</a> 插件配合使用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: luckperm
  group: &#x3C;group name>
</code></pre></td><td>检查玩家是否在某个组中。与 <a href="https://www.spigotmc.org/resources/luckperms.28140/">LuckPerms</a> 插件配合使用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: playername
  playerName: &#x3C;placeholder>
</code></pre></td><td>检查占位符返回的文本是否可以是玩家昵称。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: money
  amount: &#x3C;amount>
</code></pre></td><td>检查玩家账户中是否有足够的钱。这仅与 <a href="https://www.spigotmc.org/resources/vault.34315/">Vault</a> 插件配合使用。</td></tr></tbody></table>