---
description: API 信息
---

# ℹ️ 信息

zMenu API 允许你创建自己的菜单和按钮。你可以为所有插件使用相同的配置系统。

Javadocs: [https://javadocs.groupez.dev/zmenu/index.html](https://javadocs.groupez.dev/zmenu/index.html)

示例: [https://github.com/Maxlego08/zMenuExample](https://github.com/Maxlego08/zMenuExample)

最新版本在这里: [https://github.com/Maxlego08/zMenu-API/tags](https://github.com/Maxlego08/zMenu-API/tags)

## Maven

```xml
<repositories>
	<repository>
		<id>jitpack.io</id>
		<url>https://jitpack.io</url>
	</repository>
</repositories>

<dependencies>
	<dependency>
		<groupId>com.github.Maxlego08</groupId>
		<artifactId>zMenu-API</artifactId>
		<version>VERSION</version>
	</dependency>
</dependencies>
```

## Gradle

```bash
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}

dependencies {
		implementation 'com.github.Maxlego08:zMenu-API:VERSION'
}
```

## 第一步

第一步是通过 Spigot 服务提供者系统获取 [InventoryManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html) 和 [ButtonManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html) 接口。

```java
@Override
public void onEnable() {
    InventoryManager inventoryManager = getProvider(InventoryManager.class);
    ButtonManager buttonManager = getProvider(ButtonManager.class);
}

private <T> T getProvider(Class<T> classz) {
    RegisteredServiceProvider<T> provider = getServer().getServicesManager().getRegistration(classz);
    return provider == null ? null : provider.getProvider() != null ? (T) provider.getProvider() : null;
}
```
