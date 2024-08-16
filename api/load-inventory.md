---
icon: loader
---

# 加载菜单

要加载菜单，你可以使用 `InventoryManager` 接口中的多种方法。但我建议你使用 `loadInventoryOrSaveResource` 方法。它允许你从插件的资源中检索文件并保存它。

```java
try {
    // 尝试从 YAML 文件加载或保存自定义菜单配置
    this.inventoryManager.loadInventoryOrSaveResource(this.plugin, "inventories/paginate_inventory.yml");
} catch (InventoryException exception) {
    // 记录加载菜单过程中发生的任何异常
    exception.printStackTrace();
}
```
