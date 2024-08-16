---
icon: drone
---

# 创建材质加载器

你可以创建你自己的 [MaterialLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/MaterialLoader.html)。材质加载器允许你根据配置创建一个 `ItemStack` 对象。

使用 HeadDatabase 的示例：

```java
package fr.maxlego08.menu.loader.materials;

import fr.maxlego08.menu.api.loader.MaterialLoader;
import me.arcaniax.hdb.api.HeadDatabaseAPI;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.inventory.ItemStack;

public class HeadDatabaseLoader implements MaterialLoader {

    @Override
    public String getKey() {
        return "hdb";
    }

    @Override
    public ItemStack load(YamlConfiguration configuration, String path, String materialString) {

        try {

            HeadDatabaseAPI api = new HeadDatabaseAPI();
            return api.getItemHead(materialString);

        } catch (Exception exception) {
            exception.printStackTrace();
        }

        return null;
    }
}
```
