---
icon: gauge-max
---

# 快速事件

在默认配置中，FastEvents 是默认启用的。你可以使用名为 `FastEvent` 的接口，其中包含每个插件事件的方法，而不是使用 Bukkit API 的事件。或者，你可以在 `config.json` 中禁用此选项，并正常使用 Bukkit 事件。

## 注册 FastEvent

```java
inventoryManager.registerFastEvent(plugin, yourFastEventClass)
```

示例：

```java
import fr.maxlego08.menu.api.InventoryManager;
import fr.maxlego08.menu.api.event.FastEvent;
import fr.maxlego08.menu.api.event.events.ButtonLoadEvent;
import fr.maxlego08.menu.api.event.events.InventoryLoadEvent;
import fr.maxlego08.menu.api.event.events.PlayerOpenInventoryEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class ExampleEvent extends FastEvent {

    @Override
    public void onButtonLoad(ButtonLoadEvent event) {

    }

    @Override
    public void onInventoryLoad(InventoryLoadEvent event) {

    }

    @Override
    public void onPlayerOpenInventory(PlayerOpenInventoryEvent event) {

    }
}
```

```java
import fr.maxlego08.menu.api.InventoryManager;
import org.bukkit.plugin.java.JavaPlugin;

public class ExamplePlugin extends JavaPlugin {

    @Override
    public void onEnable() {
        InventoryManager inventoryManager = getServer().getServicesManager().getRegistration(InventoryManager.class).getProvider();
        inventoryManager.registerFastEvent(this, new ExampleEvent());
    }
}
```
