---
description: 如何创建一个按钮
icon: hexagon-check
---

# 创建按钮

本示例的代码可以在这里找到：[https://github.com/Maxlego08/zMenuExample/tree/master](https://github.com/Maxlego08/zMenuExample/tree/master)

如果你需要更具体的示例，可以查看 zShop 源代码：[https://github.com/Maxlego08/zShop/tree/master](https://github.com/Maxlego08/zShop/tree/master)

## 按钮

本文件指导你如何为插件创建一个 `SpecialButton`，利用 `SpecialButton.java` 类来实现自定义点击动作。这个示例展示了一个非常简单的按钮的典型用法。

### 概述

`SpecialButton` 继承自 `fr.maxlego08.menu` API 的 `ZButton`，用于自定义按钮在点击事件中的行为。它设计用来关闭玩家的菜单界面，发送自定义消息，并为玩家的速度应用“跳跃”或“提升”效果。

### 前提条件

确保你的项目中包含 `fr.maxlego08.menu` API，以使用 `ZButton` 和其他所需的类。

### 实现步骤

#### 第一步：定义 SpecialButton 类

创建一个名为 `SpecialButton` 的类，继承自 `ZButton`。该类将重写 `onClick` 方法以定义按钮的行为。

```java
public class SpecialButton extends ZButton {
    // 方法实现
}
```

#### 第二步：重写 onClick 方法

在 `SpecialButton` 类中，重写 `onClick` 方法以指定按钮被点击时发生的动作。这包括关闭玩家的菜单，发送自定义消息，并修改玩家的速度以模拟跳跃。

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
    // 自定义动作
}
```

第3步：实现自定义动作

在 `onClick` 方法中，添加自定义动作的逻辑：

1. **关闭菜单界面：** 使用 `player.closeInventory()` 关闭菜单界面。
2. **发送自定义消息给玩家：** 使用 `player.sendMessage("§fWhoosshh")` 发送自定义消息。
3. **修改玩家的速度：**
   * 获取当前速度：`Vector vector = player.getVelocity()`。
   * 修改速度以添加向上运动：`vector.add(new Vector(0, 2, 0))`。
   * 应用新的速度：`player.setVelocity(vector)`。

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
    player.closeInventory(); // 关闭玩家当前的菜单
    player.sendMessage("§fWhoosshh"); // 发送自定义消息给玩家

    Vector vector = player.getVelocity(); // 获取玩家当前的速度
    vector.add(new Vector(0, 2, 0)); // 修改 Y 轴以使玩家“跳跃”
    player.setVelocity(vector); // 应用新的速度给玩家
}
```

#### 第四步：注册 SpecialButton

要在插件中注册 `SpecialButton`，实例化它并将其添加到所需的菜单布局中。确保你使用的菜单系统支持自定义按钮动作。

```java
public class MyPlugin extends JavaPlugin {
    @Override
    public void onEnable() {
        // 插件启动逻辑
        // 假设 buttonManager 是你管理按钮的类实例
        buttonManager.register(new NoneLoader(this, SpecialButton.class, "zmenuexample_special"));
    }
}
```

这种方法可以非常快速地保存一个按钮，而不需要创建新的加载器。你必须指定插件来源、按钮类和名称。建议为按钮名称加上插件名称的前缀。

### 结果

```java
package fr.maxlego08.example;

import fr.maxlego08.menu.api.utils.Placeholders;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.util.Vector;

import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.util.Vector;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;

/**
 * SpecialButton 继承 ZButton 实现了自定义点击动作。
 */
public class SpecialButton extends ZButton {

    /**
     * 处理该特殊按钮上的点击事件。
     *
     * @param player 点击按钮的玩家。
     * @param event 菜单点击事件详情。
     * @param inventory 点击发生的菜单。
     * @param slot 点击发生的槽位。
     * @param placeholders 动态文本替换的占位符，此方法未使用。
     */
    @Override
    public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
        // 关闭玩家的菜单界面。
        player.closeInventory();

        // 发送消息给玩家。
        player.sendMessage("§fWhoosshh");

        // 获取玩家当前的速度。
        Vector vector = player.getVelocity();

        // 向玩家的当前速度添加向上的运动。
        // 这里 'new Vector(0, 2, 0)' 在 X 和 Z 轴上没有运动，但在 Y 轴上添加向上的运动。
        vector.add(new Vector(0, 2, 0));

        // 将新的速度应用给玩家，产生“跳跃”或“提升”效果。
        player.setVelocity(vector);

        // 如果需要，调用超类方法。 如果超类不实现进一步的操作，这个调用可能是多余的。
        super.onClick(player, event, inventory, slot, placeholders);
    }
}
```

## 分页按钮

本文件说明如何实现 `ExamplePaginateButton` 以在插件中创建分页菜单界面，使用提供的 `ExamplePaginateButton.java` 类作为基础。

### 概述

`ExamplePaginateButton` 利用 `fr.maxlego08.menu.api` 中的 `PaginateButton` 接口提供分页功能，允许项目显示在多个菜单页面中。

### 前提条件

* 在项目中包含 `fr.maxlego08.menu` API。
* 了解 Bukkit/Spigot 插件中的菜单操作基本概念。

### 实现步骤

#### 第一步：扩展 ZButton 并实现 PaginateButton

你的 `ExamplePaginateButton` 应该扩展 `ZButton` 并实现 `PaginateButton`，启用特殊渲染行为和分页：

```java
public class ExamplePaginateButton extends ZButton implements PaginateButton {
    private final ExamplePlugin plugin;
    
    public ExamplePaginateButton(Plugin plugin) {
        this.plugin = (ExamplePlugin) plugin;
    }
}
```

我们使用 `Plugin` 而不是 `ExamplePlugin`，因为负责按钮注册的 `NoneLoader` 类需要一个插件参数的构造函数。由于 `NoneLoader` 设计为与 Spigot 的通用 `Plugin` 接口一起使用，因此确保与任何 Spigot 插件的兼容性。然后，执行特定 `ExamplePlugin` 类的转换，以访问其独特功能。这种方法保持了灵活性，并遵守 Spigot 的插件架构。

#### 第二步：重写 hasSpecialRender

指示你的按钮使用自定义渲染逻辑进行分页：

```java
@Override
public boolean hasSpecialRender() {
    return true;
}
```

#### 第三步：实现自定义渲染逻辑

重写 `onRender` 方法以定义基于当前页面的项目显示方式：

```java
@Override
public void onRender(Player player, InventoryDefault inventory) {
    Pagination<ItemStack> pagination = new Pagination<>();
    List<ItemStack> itemStacks = pagination.paginate(this.plugin.getItemStacks(), this.slots.size(), inventory.getPage());
    // 循环并将项目添加到菜单
}
```

#### 第四步：定义分页大小

实现 `getPaginationSize` 以指定分页的总项目数。这直接影响菜单中的页面数量，允许动态列表管理。列表大小的变化将自动调整分页，使该方法在处理可变数量的数据时成为关键组件。

```java
@Override
public int getPaginationSize(Player player) {
    return this.plugin.getItemStacks().size();
}
```

#### 第五步：注册 ExamplePaginateButton

要在插件中注册 `ExamplePaginateButton`，实例化它并将其添加到所需的菜单布局中。确保你使用的菜单系统支持自定义按钮动作。

```java
public class MyPlugin extends JavaPlugin {
    @Override
    public void onEnable() {
        // 插件启动逻辑
        // 假设 buttonManager 是你管理按钮的类实例
        buttonManager.register(new NoneLoader(plugin, ExamplePaginateButton.class, "zmenuexample_pagination"));
    }
}
```

这种方法可以非常快速地保存一个按钮，而不需要创建新的加载器。你必须指定插件来源、按钮类和名称。建议为按钮名称加上插件名称的前缀。

### 结果

```java
package fr.maxlego08.example;

import fr.maxlego08.menu.api.button.PaginateButton;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;


import fr.maxlego08.menu.zcore.utils.inventory.Pagination;
import org.bukkit.entity.Player;
import org.bukkit.inventory.ItemStack;
import org.bukkit.plugin.Plugin;

import java.util.List;

/**
 * ExamplePaginateButton 继承自 ZButton 并实现 PaginateButton，提供分页功能。
 */
public class ExamplePaginateButton extends ZButton implements PaginateButton {

    // 参考主插件实例以访问其功能。
    private final ExamplePlugin plugin;

    /**
     * 构造函数将通用 Plugin 类型转换为特定的 ExamplePlugin 类型。
     * @param plugin 插件实例，作为通用 Plugin 类型传递。
     */
    public ExamplePaginateButton(Plugin plugin) {
        this.plugin = (ExamplePlugin) plugin;
    }

    /**
     * 指示此按钮具有特殊渲染行为，启用分页。
     * @return true 以表示使用了自定义渲染逻辑。
     */
    @Override
    public boolean hasSpecialRender() {
        return true;
    }

    /**
     * 自定义渲染方法，用于分页项目。它根据当前页面和可用槽位填充菜单。
     * @param player 查看菜单的玩家。
     * @param inventory 渲染的菜单。
     */
    @Override
    public void onRender(Player player, InventoryDefault inventory) {
        // 使用 Pagination 工具将 itemStacks 拆分为页面。
        Pagination<ItemStack> pagination = new Pagination<>();

        // 获取当前页面的分页 ItemStacks 列表。
        List<ItemStack> itemStacks = pagination.paginate(this.plugin.getItemStacks(), this.slots.size(), inventory.getPage());

        // 遍历分页项目并将其添加到菜单。
        for (int i = 0; i != Math.min(itemStacks.size(), this.slots.size()); i++) {
            int slot = slots.get(i); // 获取槽位编号。
            ItemStack itemStack = itemStacks.get(i); // 获取 ItemStack。
            // 将项目添加到菜单指定的槽位，并设置点击监听器。
            inventory.addItem(slot, itemStack).setClick(event -> player.sendMessage("§fClick !"));
        }
    }

    /**
     * 根据总项目数确定分页大小。
     * @param player 计算分页大小的玩家。
     * @return 用于分页的总项目数。
     */
    @Override
    public int getPaginationSize(Player player) {
        // 返回 itemStacks 的总大小，以确定需要多少页。
        return this.plugin.getItemStacks().size();
    }
}
```

## 自定义按钮加载器

如果你的按钮需要更多设置，你可以创建自己的按钮加载器。只需创建一个实现 `ButtonLoader` 的类。以下是 zShop 的示例：

```java
package fr.maxlego08.zshop.loader;

import fr.maxlego08.menu.api.button.Button;
import fr.maxlego08.menu.api.button.DefaultButtonValue;
import fr.maxlego08.menu.api.loader.ButtonLoader;
import fr.maxlego08.zshop.ShopPlugin;
import fr.maxlego08.zshop.api.buttons.AddButton;
import fr.maxlego08.zshop.buttons.ZAddButton;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.plugin.Plugin;

public class AddButtonLoader implements ButtonLoader {

    private final ShopPlugin plugin;

    public AddButtonLoader(ShopPlugin plugin) {
        this.plugin = plugin;
    }

    @Override
    public Class<? extends Button> getButton() {
        return AddButton.class;
    }

    @Override
    public String getName() {
        return "zshop_add";
    }

    @Override
    public Plugin getPlugin() {
        return this.plugin;
    }

    @Override
    public Button load(YamlConfiguration configuration, String path, DefaultButtonValue defaultButtonValue) {

        String amount = configuration.getString(path + "amount", "1");

        return new ZAddButton(this.plugin, amount);
    }
}
```
