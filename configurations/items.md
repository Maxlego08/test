# 🪁 Items

Before you start configuring the plugin itemstack, make sure you are using the correct material for your version of the game. Each button must be accompanied by an itemstack (except in certain specific cases).

## Material

```yaml
material: <material>
```

The material of the item. You can use a placeholder to display a material.

> **Supported material values:**
>
> * [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) - Example: `material: STONE`
> * [Placeholder](https://www.spigotmc.org/resources/placeholderapi.6245/) value - Example: `material: %your_placeholder_material%`
> * FREE - [zHead](https://www.spigotmc.org/resources/zhead-database.115717/) **RECOMMENDED** (zhd:\<id>) Example: `material: "zhd:<id>"`
> * PAID - zItems (ztems:\<item name>) Example: `material: "zitems:<id>"`
> * PAID - [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (hdb:\<id>) Example: `material: "hdb:<id>"`
> * PAID - [Oraxen](https://www.spigotmc.org/resources/%E2%98%84%EF%B8%8F-oraxen-add-items-blocks-armors-hats-food-furnitures-plants-and-gui-1-18-1-20-1.72448/) (oraxen:\<item name>) Example: `material: "oraxen:<item name>"`
> * PAID - [ItemAdder](https://www.spigotmc.org/resources/%E2%9C%A8itemsadder%E2%AD%90emotes-mobs-items-armors-hud-gui-emojis-blocks-wings-hats-liquids.73355/) (itemsadder:\<item name>) Example: `material: "itemsadder:<item name>"`
> * FREE - [SlimeFun](https://github.com/Slimefun/Slimefun4) (slimefun:\<item name>) Example: `material: "slimefun:<item name>"`
> * FREE - [Nova](https://github.com/xenondevs/Nova) (nova:\<item/block name>) Example: `material: "nova:<item/block name>"`
> * Base64 (base64:\<item in base64) Retrieve this value in base64 with the command `/zm save <item name> base64`
> * [PlayerHead ](buttons/#playerhead)(playerHead: \<player name>) Displays the head of a player. Example: `playerHead: "%player%"` Displays the head of the player who opens the inventory

***

## Amount

```yaml
amount: <amount>
```

The amount of the itemstack. You can use a placeholder to have a dynamic amount.

***

## Data

```yaml
data: <data, only avaible between 1.8 and 1.12>
```

The material data, only available for versions between 1.8 and 1.12. By default, it's 0.

***

## Durability

```yaml
durability: <durability>
```

The durability of the item, by default, is 0.

***

## Url

```yaml
url: <player skin in base64>
```

Allows you to display a head with a URL in base64. You can find the values of the heads on the site [minecraft-head.com](https://minecraft-head.com).

You must take the content in the "Value" field under the "Other" category.

![minecraft-head.com example of value](../.gitbook/assets/base64.png)

Example

```yaml
url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNjM3YjhhMzk4MzdiYzNkNThmMDljOGM2ZTUzOTYyZDMzZjlmYTBiNjUzOThhNzc5MzUzYWRlMWUxNDcxM2VmZiJ9fX0="
```

***

## Name

```yaml
name: <display name>
```

The name that will be displayed on the item. You can use PlaceholderAPI to make the name dynamic.

{% hint style="info" %}
If your server has Kyori Adventure, you can use the [mini message format](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

***

## Lore

```yaml
lore:
  - <line1>
  - <line2>
  - <line3>
  - ...
```

Allows you to display the lore of the item. You can use PlaceholderAPI to make the lore dynamic.

***

## Potion

```yaml
  potion: <potion effect type>
  level: <potion level, 1 or 2> # 1 by default
  splash: <potion splash true or false>
  extended: <potion extended true of flase>
```

Allows you to create a potion. Check potion effect types [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionType.html) for more details.

{% hint style="danger" %}
Warning: A potion cannot be extended and have a level 2 at the same time.
{% endhint %}

{% hint style="info" %}
```yml
# For potions in 1.8 up to 1.12 you have to do like this:
material: POTION
durability: 16454
```
{% endhint %}

***

## Glow

```yaml
glow: <true of false>
```

Allows the item to shine. Add random enchant and HIDE\_ENCHANT itemflag.

***

## ModelID

```yaml
modelID: <custom model id>
```

Allows you to put a custom model id on the item.

***

## Enchantments

```yaml
enchants:
  - <enchantment name>,<enchantment level>
```

Allows you to add enchantments. You need to specify the name of the enchantment followed by the level of the enchantment, in the format: `ENCHANT,ENCHANT_LEVEL`.

### List of enchantments

<table><thead><tr><th width="237">Enchantment</th><th>Aliases</th></tr></thead><tbody><tr><td>damage_all</td><td>alldamage, alldmg, sharpness, sharp, dal</td></tr><tr><td>damage_arthropods</td><td>ardmg, baneofarthropods, baneofarthropod, arthropod, dar</td></tr><tr><td>damage_undead</td><td>undeaddamage, smite, du</td></tr><tr><td>dig_speed</td><td>digspeed, efficiency, minespeed, cutspeed, ds, eff</td></tr><tr><td>durability</td><td>durability, dura, unbreaking, d</td></tr><tr><td>thorns</td><td>thorns, highcrit, thorn, highercrit, t</td></tr><tr><td>fire_aspect</td><td>fireaspect, fire, meleefire, meleeflame, fa</td></tr><tr><td>knockback</td><td>knockback, kback, kb, k</td></tr><tr><td>loot_bonus_blocks</td><td>blockslootbonus, fortune, fort, lbb</td></tr><tr><td>loot_bonus_mobs</td><td>mobslootbonus, mobloot, looting, lbm</td></tr><tr><td>oxygen</td><td>oxygen, respiration, breathing, breath, o</td></tr><tr><td>protection_environmental</td><td>protection, prot, protect, p</td></tr><tr><td>protection_explosions</td><td>explosionsprotection, explosionprotection, expprot, blastprotection, bprotection, bprotect, blastprotect, pe</td></tr><tr><td>protection_fall</td><td>fallprotection, fallprot, featherfall, featherfalling, pfa</td></tr><tr><td>protection_fire</td><td>fireprotection, flameprotection, fireprotect, flameprotect, fireprot, flameprot, pf</td></tr><tr><td>protection_projectile</td><td>projectileprotection, projprot, pp</td></tr><tr><td>silk_touch</td><td>silktouch, softtouch, st</td></tr><tr><td>water_worker</td><td>waterworker, aquaaffinity, watermine, ww</td></tr><tr><td>arrow_fire</td><td>firearrow, flame, flamearrow, af</td></tr><tr><td>arrow_damage</td><td>arrowdamage, power, arrowpower, ad</td></tr><tr><td>arrow_knockback</td><td>arrowknockback, arrowkb, punch, arrowpunch, ak</td></tr><tr><td>arrow_infinite</td><td>infinitearrows, infarrows, infinity, infinite, unlimited, unlimitedarrows, ai</td></tr><tr><td>luck</td><td>luck, luckofsea, luckofseas, rodluck</td></tr><tr><td>lure</td><td>lure, rodlure</td></tr><tr><td>depth_strider</td><td>depthstrider, depth, strider</td></tr><tr><td>frost_walker</td><td>frostwalker, frost, walker</td></tr><tr><td>mending</td><td>mending</td></tr><tr><td>binding_curse</td><td>bindingcurse, bindcurse, binding, bind</td></tr><tr><td>vanishing_curse</td><td>vanishingcurse, vanishcurse, vanishing, vanish</td></tr><tr><td>sweeping_edge</td><td>sweepingedge, sweepedge, sweeping</td></tr><tr><td>loyalty</td><td>loyalty, loyal, return</td></tr><tr><td>impaling</td><td>impaling, impale, oceandamage, oceandmg</td></tr><tr><td>riptide</td><td>riptide, rip, tide, launch</td></tr><tr><td>channeling</td><td>channelling, chanelling, channeling, chaneling, channel</td></tr><tr><td>multishot</td><td>multishot, tripleshot</td></tr><tr><td>quick_charge</td><td>quickcharge, quickdraw, fastcharge, fastdraw</td></tr><tr><td>piercing</td><td>piercing</td></tr><tr><td>soul_speed</td><td>soulspeed, soilspeed, sandspeed</td></tr><tr><td>swift_sneak</td><td>swiftsneak</td></tr><tr><td>breach</td><td>breach</td></tr><tr><td>density</td><td>density</td></tr><tr><td>wind_burst</td><td>windburst, wind, burst</td></tr></tbody></table>

***

## Flags

```yaml
flags:
  - <flag 1>
  - <flag 2>
  - ...
```

List of flags: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)

***

## Color

```yaml
type: LEATHER_CHESTPLATE
color: 40,150,40 # RGB color

# Example with ARGB
color: 1,40,150,40 # ARGB color, Alpha, RED, GREEN, BLUE
```

Set the RGB color (Red, Green, Blue) for leather armor. The format is as follows:

`<Red>,<Green>,<Blue>`

For example, to set a color with 255 red, 100 green, and 50 blue, you would use:

`255,100,50`

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;red>,&#x3C;green>,&#x3C;blue>
</strong></code></pre>

You can also add an alpha value in the color to have ARGB (Alpha, Red, Green, Blue). The format is as follows:

`<Alpha>,<Red>,<Green>,<Blue>`

For example, to set a color with 128 alpha (semi-transparent), 255 red, 100 green, and 50 blue, you would use:

`128,255,100,50`

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;alpha>,&#x3C;red>,&#x3C;green>,blue>
</strong></code></pre>

{% hint style="info" %}
The color format for fireworks, banners, and potions follows the same ARGB format:

`<Alpha>,<Red>,<Green>,<Blue>`

For example:

* **Fireworks**: To set a color with 255 alpha (fully opaque), 200 red, 150 green, and 100 blue, you would use: `255,200,150,100`.
* **Banners**: To set a color with 255 alpha, 100 red, 200 green, and 50 blue, you would use: `255,100,200,50`.
* **Potions**: To set a color with 128 alpha (semi-transparent), 255 red, 50 green, and 50 blue, you would use: `128,255,50,50`.

For further details, check the Javadocs for Color [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Color.html#fromARGB\(int,int,int,int\)).
{% endhint %}

***

## Firework

```yaml
type: FIREWORK
firework:
  star: true
  flicker: true
  trail: true
  type: BALL_LARGE
  colors:
    - 250,10,10 # RGB and ARGB
  fadeColors:
    - 250,10,250 # RGB and ARGB
```

Firework type: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html)

***

## Banner

```yaml
type: BANNER
banner: PINK # Banner color
patterns: # Banner pattern: <color>:<pattern>
  - RED:SQUARE_BOTTOM_LEFT
  - GREEN:STRIPE_LEFT
```

Allows you to create a banner. Pattern list: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html)

## Translated Name

Allows to translate the name of the item in several languages

```yaml
items:
  example:
    item:
      material: GRASS_BLOCK
      name: "&aThis is a very nice grass block"
      lore:
        - "" 
        - "&eMy first button with &fzMenu"
        - "&7Congratulations, you will now discover"
        - "&7all the possibilities of zMenu."

      # Translate the item name into multiple languages
      # You must define the language and the country used
      # The vanilla Minecraft client will use lowercase language / country pairs separated by an underscore, but custom resource packs may use any format they wish.
      translatedName:
        - locale: "fr_fr" # Allows to define the language in French
          name: "&aC’est un très beau bloc d’herbe !"
        - locale: "es_es" # Allows to define the language in Spanish
          name: "&a¡Es un hermoso bloque de hierba!"
```

## Translated Lore

Allows to translate the lore of the item in several languages

```yaml
items:
  example:
    item:
      material: GRASS_BLOCK
      name: "&aThis is a very nice grass block"
      lore:
        - "" 
        - "&eMy first button with &fzMenu"
        - "&7Congratulations, you will now discover"
        - "&7all the possibilities of zMenu."

      # Translate the item lore into multiple languages
      # You must define the language and the country used
      # The vanilla Minecraft client will use lowercase language / country pairs separated by an underscore, but custom resource packs may use any format they wish.
      translatedLore:
        - locale: "fr_fr" # Allows to define the language in French
          lore:
            - "" # empty line to put space between name and lore
            - "&eMon premier bouton avec &fzMenu"
            - "&7Félicitations, vous allez maintenant découvrir"
            - "&7toutes les possibilités de zMenu."
        - locale: "es_es" # Allows to define the language in Spanish
          lore:
            - "" # empty line to put space between name and lore
            - "&eMi primer botón con &fzMenu"
            - "&7Felicidades, ahora vas a descubrir"
            - "&7todas las posibilidades de zMenu."
```

## Max Stack Size

```yaml
max-stack-size: 2
```

Overrides the default maximum stack size of this item. Choose a number between 1 and 99. max-stack-size must be 1 if max-damage is set.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Max Damage

```yaml
max-damage: 2567
```

Controls the maximum amount of damage an item can take. If not present, the item cannot be damaged. For this to work, you need to make this item a tool if it is not already and then set it's initial damage (usually 0). max-stack-size must be 1 if max-damage is set.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Damage

```yaml
damage: 20
```

The absolute amount of damage or use this item has taken.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Repair Cost

```yaml
repair-cost: 10
```

Number of enchantment levels to add to the base level cost when repairing, combining, or renaming this item with an Anvil.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Unbreakable

```yaml
unbreakable: false
```

Tools, armor and weapons set with this won't lose durability when used.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Unbreakable Show In Tooltip

```yaml
unbreakable-show-in-tooltip: false
```

If false, an 'Unbreakable' line will not be included in the tooltip. Default is True.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Fire Resistant

```yaml
fire-resistant: false
```

If true, this item will not burn in fire

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Item Rarity

```yaml
item-rarity: COMMON
```

Determines the default color of its name. This enum is ordered from least rare to most rare.

* `COMMON` - White item name.
* `EPIC` - Light purple item name.
* `RARE` - Aqua item name.
* `UNCOMMON` - Yellow item name.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Hide Tooltip

```yaml
hide-tooltip: false
```

If present, it will completely hide whole item tooltip (that includes item name). The tooltip will be still visible and searchable in creative mode.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Hide additional tooltip

```yaml
hide-additional-tooltip: false
```

If true, disables 'additional' tooltip part which comes from the item type.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Enchantment Glint

```yaml
enchantment-glint: false
```

If true, the item will glint, even without enchantments; if false, the item will not glint, even with enchantments. If null, the override will be cleared.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Enchantment Show In Tooltip

```yaml
enchantment-show-in-tooltip: true
```

If false, no enchantments will be shown in the item tooltip. Default is true.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Attribute Show In Tooltip

```yaml
attribute-show-in-tooltip: true
```

If false. The attributes will not show on the item tooltip. Default is true.

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}

## Trim

```yaml
# Only work for armors!
trim:
  enable: false
  # QUARTZ, IRON, NETHERITE, REDSTONE, COPPER; GOLD; EMERALD, DIAMOND, LAPIS, AMETHYST
  material: QUARTZ
  # SENTRY, DUNE, COAST, WILD, WARD, EYE, VEX, TIDE, SNOUT, RIB, SPIRE, WAYFINDER, SHAPER, SILENCE, RAISER, HOST
  pattern: DUNE
```

Allows to define an armor trim, only usable on armor

{% hint style="danger" %}
Only available for 1.21 and below
{% endhint %}
