---
description: 指令及其权限列表
---

# 📜 指令和权限

## 指令

<table data-full-width="true"><thead><tr><th width="409.9844776750376">指令</th><th width="160.56947162426616">权限</th><th>描述</th></tr></thead><tbody><tr><td>/zm (别名: /zmenu)</td><td>zmenu.use</td><td>显示指令列表。</td></tr><tr><td>/zm open &#x3C;menu> [&#x3C;player>] [&#x3C;display message>] [&#x3C;args>]</td><td>zmenu.open</td><td>打开指定的物品栏。</td></tr><tr><td>/zm reload</td><td>zmenu.reload</td><td>重新加载配置。</td></tr><tr><td>/zm reload config</td><td>zmenu.reload</td><td>重新加载 config.json 和 messages.yml 文件。</td></tr><tr><td>/zm reload inventory [&#x3C;inventory name>]</td><td>zmenu.reload</td><td>重新加载物品栏文件。</td></tr><tr><td>/zm reload command [&#x3C;command name>]</td><td>zmenu.reload</td><td>重新加载指令文件。</td></tr><tr><td>/zm version</td><td></td><td>显示插件版本。</td></tr><tr><td>/zm convert</td><td>zmenu.convert</td><td>将 DeluxeMenu 转换为 zMenu。</td></tr><tr><td>/zm list</td><td>zmenu.list</td><td>物品栏列表。</td></tr><tr><td>/zm create &#x3C;file name> &#x3C;inventory size> &#x3C;inventory name></td><td>zmenu.create</td><td>创建一个新的物品栏文件，之后你只需添加物品即可。</td></tr><tr><td>/zm save &#x3C;item name></td><td>zmenu.save</td><td>将你手中的物品保存为插件配置格式。</td></tr><tr><td>/zm giveopenitem &#x3C;inventory> [&#x3C;player>]</td><td>zmenu.open.item</td><td>允许获取在点击时用于打开物品栏的物品。</td></tr><tr><td>/&#x3C;command></td><td>自定义权限</td><td>打开特定文件。</td></tr></tbody></table>

有关玩家数据系统的指令列表 [请点击这里](player-data.md)。

### 带参数的打开指令

你可以使用 /zm open 指令并带上参数（如 [这里](commands.md#informations)）。

例如，对于默认的物品栏 `example_punish`。你可以定义两个要使用的参数。可以通过两种方式实现。

* 第一种是指定参数的名称，如下所示：`<argument name>:<argument value>`\
  示例：`/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:test`\
  结果：`%zmenu_argument_target%` 和 `%zmenu_argument_reason%`\
  你也可以这样添加更多参数：`/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:"this is a really long reason"`
* 第二种是直接使用值，因此参数名称将是第一个值的 0，第二个值的 1，以此类推。\
  示例：`/zm open zmenu:example_punish Maxlego08 false Maxlego09 test`\
  结果：`%zmenu_argument_0%` 和 `%zmenu_argument_1%`

## 转换

要将 DeluxeMenu 配置转换为 zMenu，你必须使用 **zMenuConvert** 扩展。

下载链接：[https://groupez.dev/resources/zmenuconvert.266](https://groupez.dev/resources/zmenuconvert.266)

安装插件后，你需要运行指令 **/zm convert**。你的菜单和指令将被创建在 `inventories/convert` 和 `commands/convert` 文件夹中。

请注意，转换可能包含错误，你需要检查文件以确保没有问题。&#x20;

GitHub：[https://github.com/Maxlego08/zMenuConvert](https://github.com/Maxlego08/zMenuConvert)
