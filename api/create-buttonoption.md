---
icon: subtitles
---

# 创建 ButtonOption

`ButtonOption` 允许你为所有按钮添加元素。要保存 `ButtonOption`，你的插件必须与 zMenu 一起加载。你需要使用事件 `ButtonLoaderRegisterEvent`。

示例：

```java
package fr.maxlego08.example;

// 导入语句
import fr.maxlego08.menu.MenuItemStack;
import fr.maxlego08.menu.api.ButtonManager;
import fr.maxlego08.menu.api.InventoryManager;
import fr.maxlego08.menu.api.button.Button;
import fr.maxlego08.menu.api.button.ButtonOption;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import fr.maxlego08.menu.zcore.utils.loader.Loader;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.plugin.Plugin;

import java.io.File;

/**
 * CustomAction 实现了 ButtonOption 以提供插件 zMenu 内的自定义按钮行为。
 */
public class CustomAction implements ButtonOption {

    // 引用主插件实例以访问其功能和配置。
    private final ExamplePlugin plugin;
    // 一个标志，用于通过配置文件启用或禁用自定义操作。
    private boolean enableCustomAction;

    /**
     * CustomAction 的构造函数。
     * @param plugin 主插件类的实例。
     */
    public CustomAction(ExamplePlugin plugin) {
        this.plugin = plugin;
    }

    /**
     * 返回此自定义操作的唯一名称。
     * @return 此操作的字符串标识符。
     */
    @Override
    public String getName() {
        return "custom_action_example";
    }

    /**
     * 返回与此自定义操作关联的插件实例。
     * @return 插件实例。
     */
    @Override
    public Plugin getPlugin() {
        return this.plugin;
    }

    /**
     * 从配置文件加载按钮设置。
     * 这个方法会自动调用，将配置设置应用到按钮上。
     *
     * @param button 被配置的按钮。
     * @param yamlConfiguration 从文件加载的 YamlConfiguration。
     * @param path 读取配置值的路径前缀。
     * @param inventoryManager 菜单管理器实例。
     * @param buttonManager 按钮管理器实例。
     * @param loader 用于加载物品堆栈的加载器。
     * @param file 配置加载的文件。
     */
    @Override
    public void loadButton(Button button, YamlConfiguration yamlConfiguration, String path, InventoryManager inventoryManager, ButtonManager buttonManager, Loader<MenuItemStack> loader, File file) {
        // 从配置文件中加载 enableCustomAction 值。如果未指定，则默认为 false。
        this.enableCustomAction = yamlConfiguration.getBoolean(path + "enableCustomAction", false);
    }

    /**
     * 处理按钮的点击事件。
     * 当玩家点击分配了此自定义操作的按钮时，将触发此方法。
     *
     * @param button 被点击的按钮。
     * @param player 点击按钮的玩家。
     * @param inventoryClickEvent 与菜单点击相关的事件。
     * @param inventoryDefault 发生点击的菜单。
     * @param slot 点击发生的槽位索引。
     * @param hasPermission 表示玩家是否有权限使用此操作的标志。
     */
    @Override
    public void onClick(Button button, Player player, InventoryClickEvent inventoryClickEvent, InventoryDefault inventoryDefault, int slot, boolean hasPermission) {
        // 如果玩家有权限且自定义操作已启用，则向他们发送自定义消息。
        if (hasPermission && enableCustomAction) {
            player.sendMessage("§a嘿，这是一个自定义操作！");
        }
    }
}
```

你必须以这种方式注册你的 ButtonOption：

```java
    @EventHandler
    public void onButtonLoad(ButtonLoaderRegisterEvent event) {
        InventoryManager inventoryManager = event.getInventoryManager(); // 从事件中初始化菜单管理器
        inventoryManager.registerOption(this.plugin, CustomAction.class);
    }
```
