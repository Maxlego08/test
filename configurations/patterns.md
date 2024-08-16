# 🔋 模板

## 菜单

**模板** 允许您创建可重用的按钮配置，可以应用于多个菜单。这种方法有助于有效地管理菜单的装饰，避免重复配置相同的内容。

#### 如何使用模板

1. **创建模板**：将您的模板文件放入 `patterns` 文件夹中。您可以创建任意数量的模板，以管理不同的装饰元素或布局。
2. **定义模板**：每个模板文件将定义一组按钮及其配置。使用这些模板来标准化和简化菜单的设计。
3. **应用模板**：在您的菜单配置文件中，您可以引用这些模板来应用它们。这使您能够保持一致性，并轻松更新或修改多个菜单中的设计元素。

#### 示例

例如，如果您有一个用于分页按钮或装饰边框的模板，您可以在模板文件中定义它，然后在各种菜单配置中包含该模板。这样，对模板的任何更改将自动反映在所有使用它的菜单中。

#### 优势

* **效率**：避免重复按钮配置。
* **一致性**：在不同菜单中保持统一的外观。
* **易于管理**：在一个地方更新设计元素，并在所有地方应用更改。

通过利用模板，您可以有效管理和自定义菜单的外观，而无需重复配置工作。

[示例](../plugins-files.md#pattern1):

```yaml
name: "pattern1"
size: 54
# Displays the pattern on multiple pages, false by default
enableMultiPage: <true/false>
items:
    ...
```

一个模板必须包含一个 `name`，它的名称将在菜单中用来识别该模板。

然后是 `size`，即菜单的大小，您必须将大小相同的模板与菜单匹配。例如，大小为 18 的模板不能与大小为 27 的菜单一起使用。

接下来是一个项目列表，与 [菜单](inventories.md#items) 中的项目类似。

## 按钮

您可以为按钮创建模板，以避免重复设置相同的内容。这将节省您大量的配置时间。

### 如何创建模板？

您必须在模板文件夹中创建一个 yml 文件，文件名很重要。它将用于您的菜单文件中。在文件中，您必须指定名称、类型和按钮。默认文件看起来如下：

```yaml
name: "<your name>"
type: BUTTON
button:
```

然后，您可以像在菜单中一样配置您的按钮。不同的是，您可以定义来自菜单文件的变量，这些变量将在这里使用。您可以定义无限数量的变量，这完全取决于您的需要。

以下是一个示例模板，其中名称和插槽将发生变化：

```yaml
name: 'Example'
type: BUTTON
button:
  slot: '%slot%'
  item:
    material: PAPER
    name: "&c%name%"
```

变量可以有前缀，以改变它们的用法。

<table data-full-width="true"><thead><tr><th>前缀</th><th>定义</th></tr></thead><tbody><tr><td>%upper_&#x3C;key>%</td><td>以大写字母显示文本</td></tr><tr><td>%lower_&#x3C;key>%</td><td>以小写字母显示文本</td></tr><tr><td>%capitalize_&#x3C;key>%</td><td>以首字母大写显示文本</td></tr><tr><td>%add_one_&#x3C;key>%</td><td>将值加一，请注意值必须是数字。</td></tr><tr><td>%remove_one_&#x3C;key>%</td><td>将值减一，请注意值必须是数字。</td></tr></tbody></table>

### 如何使用模板

使用模板非常简单。只需在您的按钮配置中显示模板配置，设置文件名并放置您的占位符。例如，如上所示，我们将会有：

```yaml
name: 'Example'
size: 54
items:
  example1:
    pattern:
      fileName: "<your file name>"
      slot: 10
      name: 'Example 1'
  example2:
    pattern:
      fileName: "<your file name>"
      slot: 12
      name: 'Example 1'
```

模板可以在菜单中无限使用。这允许创建非常优化的配置，而无需多次重复相同的内容。只有重要的项目会出现在您的菜单文件中。

### 示例

这个示例来自资源 [Vote Menu](https://builtbybit.com/resources/vote-menu-zmenu-configurations.41468/).

#### 菜单商店

```yaml
name: '&l#8fa3e8ᴠᴏᴛᴇ sʜᴏᴘ'
size: 54
items:

  shop1:
    pattern:
      fileName: "vote_shop" # 
      slot: 20
      point: 10
      material: DIAMOND_BLOCK
      name: ' #3f3f3f▷ #6ff8edDiamond Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Diamond Blocks'
      commands:
        - 'give %player% diamond_block 16'

  shop2:
    pattern:
      fileName: "vote_shop"
      slot: 21
      point: 20
      material: EMERALD_BLOCK
      name: ' #3f3f3f▷ #40f082Emerald Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Emerald Blocks'
      commands:
        - 'give %player% emerald_block 16'

  shop3:
    pattern:
      fileName: "vote_shop"
      slot: 22
      point: 6
      material: IRON_BLOCK
      name: ' #3f3f3f▷ #e3e3e3Iron Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Iron Blocks'
      commands:
        - 'give %player% iron_block 16'
```

#### 模板

```yaml
name: 'Vote Reward'
type: BUTTON
button:
  slot: '%slot%'
  view_requirement:
    requirements:
      - type: placeholder
        placeholder: "%zmenu_player_value_vote_points%"
        value: '%point%'
        action: LOWER
  updateOnClick: true
  actions:
    - type: sound
      sound: ENTITY_VILLAGER_NO
  item:
    material: '%material%'
    name: '%name%'
    lore:
      - ''
      - '#ffd353⛃ ᴅᴇsᴄʀɪᴘᴛɪᴏɴ#3f3f3f:'
      - '%description%'
      - ''
      - '#ffd353🌟 ᴘʀɪᴄᴇ#3f3f3f: #8fa3e8%point% points'
      - ''
      - '#ff0000✘ ʏᴏᴜ ᴅᴏɴ’ᴛ ʜᴀᴠᴇ ᴇɴᴏᴜɢʜ ᴠᴏᴛᴇ ᴘᴏɪɴᴛs'
  else:

    updateOnClick: true
    refreshOnClick: true
    click_requirement:
      right_click:
        clicks:
          - ALL
        requirements:
          - type: placeholder
            placeholder: "%zmenu_player_value_vote_points%"
            value: '%point%'
            action: SUPERIOR_OR_EQUAL
        deny:
          - type: sound
            sound: VILLAGER_NO
          - type: message
            messages:
              - "#3f3f3f[#ff0000✘#3f3f3f] #ff0000发生错误，请重新打开菜单。"
          - type: close
        success:
          - type: data
            action: SUBTRACT
            key: 'vote_points'
            value: '%point%'
          - type: console_command
            commands:
              - '%commands%'
          - type: sound
            sound: ENTITY_PLAYER_LEVELUP

    item:
      material: '%material%'
      name: '%name%'
      lore:
        - ''
        - '#ffd353⛃ ᴅᴇsᴄʀɪᴘᴛɪᴏɴ#3f3f3f:'
        - '%description%'
        - ''
        - '#ffd353🌟 ᴘʀɪᴄᴇ#3f3f3f: #8fa3e8%point% points'
        - ''
        - '#ffd353➥ ᴄʟɪᴄᴋ ᴛᴏ ᴘᴜʀᴄʜᴀsᴇ'
```
