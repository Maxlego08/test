---
description: 关于 config.json 文件中值的信息
---

# 🦬 Config.json

```
enableDebug: true/false
```

启用调试，允许你在控制台显示通常会被隐藏的错误信息。



```
enableDebugTime: true/false
```

启用调试时间，允许你显示代码执行时间（以纳秒为单位），适合测试插件的效果。



```
enableLogStorageFile: true/false
```

启用日志存储文件，允许在控制台中保存或加载文件日志。



```
enableInformationMessage: true/false
```

启用信息消息，允许你查看有关菜单的消息或订单成功加载的消息。



```
enableOpenMessage: true/false
```

启用打开消息，默认值用于命令 `/zm open <inventory name> <player> <display message>`。



```
enableMiniMessageFormat: true/false
```

启用 mini 消息格式，允许你激活 mini 消息格式，该功能从 1.17 版本开始提供，更多信息请查看：[https://docs.advntr.dev/minimessage/index.html](https://docs.advntr.dev/minimessage/index.html)



```
enablePlayerCommandInChat: true/false
```

启用聊天中的玩家命令，确保当玩家执行命令时，他们是在聊天中执行而不是在控制台中。如果你有“虚拟”命令，这些命令没有保存在 Spigot 中，你需要启用此选项。



```
secondsSavePlayerData: Int
```

保存玩家数据的秒数：自动备份玩家数据的时间（以秒为单位）。



```
secondsSavePlayerInventories: Int
```

保存玩家菜单的秒数：自动备份菜单数据的时间（以秒为单位）。



```
autoSaveFileInventoryOnUpdate: true/false
```

更新时自动保存菜单文件：允许你在更新时自动保存玩家菜单的文件。



```
mainMenu: "example"
```

默认菜单名称。



```
useSwapItemOffHandKeyToOpenMainMenu: true
```

按下 f 键时打开主菜单。



```
useSwapItemOffHandKeyToOpenMainMenuNeedsShift: true
```

按下交换副手物品的键和蹲下键时打开主菜单。



```
specifyPathMenus: [
  "example",
]
```

加载特定的菜单。



```
generateDefaultFile: true/false
```

生成默认配置文件。
