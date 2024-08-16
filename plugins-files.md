---
description: 插件的配置文件
---

# 🗃️ 插件配置

### Config.json

```json
{
  "enableDebug": true,
  "enableDebugTime": false,
  "enableInformationMessage": true,
  "enableLogStorageFile": false,
  "enableOpenMessage": true,
  "enableMiniMessageFormat": true,
  "enablePlayerCommandInChat": false,
  "secondsSavePlayerData": 600,
  "secondsSavePlayerInventories": 600,
  "autoSaveFileInventoryOnUpdate": true,
  "mainMenu": "example",
  "useFKeyToOpenMainMenu": true,
  "useFKeyToOpenMainMenuNeedsShift": true
}
```

### Messages.yml

```yaml
messages:
  prefix:
    message: '§8(§6zMenu§8) '
  time:
    day:
      message: '%02d %day% %02d %hour% %02d %minute% %02d %second%'
    hour:
      message: '%02d %hour% %02d minute(s) %02d %second%'
      simple:
        message: '%02d:%02d:%02d'
    minute:
      message: '%02d %minute% %02d %second%'
    second:
      message: '%02d %second%'
  format:
    second:
      message: second
    seconds:
      message: seconds
    minute:
      message: minute
    minutes:
      message: minutes
    hour:
      message: hour
    hours:
      message: hours
    day:
      message: d
    days:
      message: days
  command:
    syntaxe:
      error:
        message: '§cYou must execute the command like this§7: §a%syntax%'
      help:
        message: §f%syntax% §7» §7%description%
    'no':
      permission:
        message: §cYou do not have permission to run this command.
      console:
        message: §cOnly one player can execute this command.
      arg:
        message: §cImpossible to find the command with its arguments.
  documentation:
    information:
      message: '§7Documentation§8: §fhttps://docs.zmenu.dev/'
  inventory:
    not:
      found:
        message: §cUnable to find the §f%toName% §cinventory in the §f%name%§c inventory.
    error:
      message: §cUnable to find the §f%name%§c inventory.
    open:
      other:
        message: §aYou have just opened the inventory §f%name%§a to the §3%player%§a.
      success:
        message: §aYou have just opened the inventory §f%name%§a.
      error:
        inventory:
          message: §cImpossible to find the inventory §f%name%§c.
        command:
          message: §cImpossible to find the command §f%name%§c.
        player:
          message: §cUnable to find the player, please specify.
        console:
          message: §cOnly one player can open an inventory.
  description:
    open:
      message: Allows you to open an inventory
    reload:
      message: Allows you to reload configuration files
    version:
      message: Show plugin version
    download:
      message: WIP
    login:
      message: WIP
    disconnect:
      message: WIP
    convert:
      message: Convert other configurations to zmenu
    players:
      message: Displays the list of commands for the players' data
      set:
        message: Set new player data. You must set the expiration time in seconds.
          Put 0 to have no expiration
      remove:
        message: Remove player data
      get:
        message: Get player data
      keys:
        message: Returns the list of keys of a player
      clear:
        all:
          message: Clear all player's data
        player:
          message: Clear player's data
  reload:
    message: §aYou have just reloaded the configuration files.
    inventory:
      message: §aYou have just reloaded the inventories files.
      file:
        message: §aVous have just reloaded the inventory §f%name%§a.
    command:
      message: §aYou have just reloaded the commands files.
      file:
        message: §aVous have just reloaded the command §f%name%§a.
      error:
        message: §cIt is not possible to reload the command §f%name%§c.
    files:
      message: §aYou have just reloaded config.json and messages.yml files.
  convert:
    info:
      messages:
      - §fYou can convert the menu from §eDeluxeMenu§f to §azMenu§f.
      - §fYou must install the §3zMenuConvert§f plugin.
      - '§fDownload link§8: §7https://groupez.dev/resources/zmenuconvert.266'
      - §fYou must then issue the command §b/zmenu convert§f.
  players:
    data:
      clear:
        all:
          message: §aYou have just deleted the datas of all the players.
        player:
          message: §aYou have just deleted the player's data §f%player%§a.
      set:
        message: §aYou have just added a data for the §b%player% §a with the §f%key%§a.
      keys:
        success:
          message: '§aPlayer''s Key §f%player%§8: §7%keys%'
        empty:
          message: §cThe §f%player% §chas no key.
      get:
        success:
          messages:
          - '§fKey§8: §7%key%'
          - '§fExpired at (timestamp)§8: §7%expiredAt%'
          - '§fValue§8: §7%value%'
        error:
          message: §cCannot find the key §f%key%§c.
      remove:
        success:
          message: §aYou have just deleted the §f%key% §for the §b%player%§a.
        error:
          message: §cCannot find the key §f%key%§c.
  website:
    login:
      error:
        token:
          message: §cYour token seems invalid, please try again.
        already:
          message: §cYou are already connected to the site.
        info:
          message: §cAn error occurred during your connection, please try again.
      process:
        message: §7Connection in progress, please wait.
      success:
        messages:
        - §aYou have successfully connected to the site.
        - §aYou can now access your purchased resources and the inventory editor.
    disconnect:
      success:
        message: §cYou have just deleted the link to the site.
      error:
        message: §cYou are not connected to the site.
  placeholder:
    never:
      message: never

```

## 菜单配置

### Basic\_Inventory.yml

```yaml
####################################################
#
# A basic zMenu configuration for beginners
# This configuration includes simple elements to help you take control of the configuration elements of the plugin.
#
# The configuration for the command to open this inventory is in the file commands/basic_command.yml
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#   Documentation: https://docs.zmenu.dev
#   Discord: https://discord.groupez.dev
#   Plugin page: https://groupez.dev/resources/zmenu.253
#   Marketplace: https://minecraft-inventory-builder.com
#   Sponsor: https://serveur-minecraft-vote.fr/
#
####################################################

# Size (https://docs.zmenu.dev/configurations/inventories#size)
#
# Allows to set the size of the inventory.
# The inventory size must be a multiple of 9. So you can put 9, 18, 27, 36, 45 and 54
# If this option is not present in the configuration, then the default will be 54
#
size: 18

# Inventory name (https://docs.zmenu.dev/configurations/inventories#name)
#
# This is the title of your inventory. You can put anything in it.
# Color code and placeholders are supported.
# If you are on Paper, Purpur or PufferFish you have access to the color code of MiniMessage (https://docs.advntr.dev/minimessage/format.html)
#
name: "&7Basics Menu"

# Item section. (https://docs.zmenu.dev/configurations/inventories#items)
#
# This is where you will add all the items that will be present in your inventory.
# With zMenu, each item is a Button. A button will allow you to perform specific actions, such as opening a new inventory, changing pages, going back.
# By default, the button will be of type NONE. All buttons will have the same configuration elements.
# Only buttons with types like INVENTORY, BACK etc... will have specific configuration elements.
# All button information here: https://docs.zmenu.dev/configurations/buttons
#
items:
  # Here you will specify a name for your button. No matter what you put, the name will only be present in the configuration.
  # Attention, the name of your button must be unique. We advise you to choose a name that will describe what the button does.
  myFirstButton:
    # As indicated, each button will have a specific type. To specify the type of button you must put this. (https://docs.zmenu.dev/configurations/buttons#type)
    # By default, the type will be NONE, so you must set this value only if your button is something other than NONE. We will see in more detail the different type of button in another button if below
    type: NONE
    # Slots that you want to put the item. Starts from 0 (https://docs.zmenu.dev/configurations/buttons#slot)
    slot: 4
    # You will now specify the content of your item. The item will include all configuration items that will be displayed in the inventory, name, lore etc.
    # https://docs.zmenu.dev/configurations/items
    item:
      # Let’s start with a block of grass
      # To find the list of materials you must go to the spigot documentation: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html
      # You can also set a material from another plugin, such as ItemAdder for example. All information here: https://docs.zmenu.dev/configurations/items#material
      material: GRASS_BLOCK
      # Here we will name this item (https://docs.zmenu.dev/configurations/items#name)
      # Color code, mini message and placeholders are supported
      name: "&aThis is a very nice grass block"
      # This is the lore. (https://docs.zmenu.dev/configurations/items#lore)
      # You must put several lines to the lore.
      # Color code, mini message and placeholders are supported
      lore:
        - "" # empty line to put space between name and lore
        - "&eMy first button with &fzMenu"
        - "&7Congratulations, you will now discover"
        - "&7all the possibilities of zMenu."

  # Create a second button, but this time let’s show your head. This will also be a NONE button, so we won’t specify it.
  mySecondButton:
    # Slots that you want to put the item. Starts from 0 (https://docs.zmenu.dev/configurations/buttons#slot)
    slot: 9
    # We will add an item with the head of the player who will open the inventory.
    item:
      # This allows you to specify a nickname to display a player head. To display the head of the player who will open the inventory you must use the placeholder %player%
      # You do not need to specify the material and/or data, the plugin will automatically do it.
      playerHead: "%player%"
      # As for the first button you can specify a name and a lore
      name: "&2%player%'s head"
      lore:
        - "&7Here is your head !"
        - ""
        - "&fSo it’s simple, right ?"
        - "&fLet’s continue the discovery of the plugin."

  # Now let’s create a third button, it will be a head with a cake skin and when we click on it a command will be executed by the console.
  myThirdButton:
    # Slots that you want to put the item. Starts from 0 (https://docs.zmenu.dev/configurations/buttons#slot)
    slot: 17
    # We will add an item with the cake head
    item:
      # To put a head with a specific skin, you can directly put the value of the skin. Here we have a cake skin that was picked up here: https://minecraft-heads.com/custom-heads/food%20&%20drinks/65273-cake
      # You do not need to specify the material and/or data, the plugin will automatically do it.
      # More information here: https://docs.zmenu.dev/configurations/items#url
      url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMWJlN2ZmNzkzMTE5OWRjY2U4OGZhNmE4MjdmMjliYjE5MGM5MjUwNGEzNmRmZWY5ODc4NWUxZGQ2MTU2N2NhZCJ9fX0="
      # As for the first button you can specify a name and a lore
      name: "&cThe cake is a lie"
      # Want to make the item shine ? So, just set true to the glow value.
      # This will add an enchantment to the item as well as the HIDE_ENCHANTS flag.
      # https://docs.zmenu.dev/configurations/items#glow
      glow: true
    # We now want the console to execute the command /say %player% is great !
    consoleCommands:
      - "say %player% is great"

#################################################################
#
# Other elements of configurations for the inventory
#
#################################################################

# You want to directly fill your inventory with an item?
# Then with the fillItem is for you. (https://docs.zmenu.dev/configurations/inventories#fill-item)
# In this example, the inventory will be filled with black glass
#
#fillItem:
#  material: BLACK_STAINED_GLASS_PANE
#  name: "&8"

# You have an inventory with a custom texture, and you do not want the player to see his items in are inventory?
# Then the clearInventory is for you
#
# Here players will have their inventory saved, then it sara deleted when opening the inventory.
# When they close the inventory their inventory will be returned to them. Does not remove the armor
#clearInventory: true
```

### Advanced\_inventory.yml

```yaml
####################################################
#
# An advanced zMenu configuration for beginners
# This configuration of the elements to better exploit the capabilities of the plugin.
# This configuration will contain two pages, so we will show you how to navigate between several pages
#
# The configuration for the command to open this inventory is in the file commands/basic_command.yml
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#   Documentation: https://docs.zmenu.dev
#   Discord: https://discord.groupez.dev
#   Plugin page: https://groupez.dev/resources/zmenu.253
#   Marketplace: https://minecraft-inventory-builder.com
#   Sponsor: https://serveur-minecraft-vote.fr/
#
####################################################

# Size (https://docs.zmenu.dev/configurations/inventories#size)
#
# Allows to set the size of the inventory.
# The inventory size must be a multiple of 9. So you can put 9, 18, 27, 36, 45 and 54
# If this option is not present in the configuration, then the default will be 54
#
size: 54

# Inventory name (https://docs.zmenu.dev/configurations/inventories#name)
#
# This is the title of your inventory. You can put anything in it.
# Color code and placeholders are supported.
# If you are on Paper, Purpur or PufferFish you have access to the color code of MiniMessage (https://docs.advntr.dev/minimessage/format.html)
#
# If your inventory has multiple pages, you can view the current page and the last page with the following placeholders:
# %page% - Current max
# %maxPage% - Last page
#
name: "&4Advanced &cInventory &7%page%&8/&7%maxPage%"

# Patterns (https://docs.zmenu.dev/configurations/patterns)
#
# The fathers allow you to have to create buttons that can be used in several inventories.
# Thus, you do not need to repeat your configuration but only to specify the name of the father.
# The patterns are in the patterns folder.
#
# To add a father you only need to specify the name you put in the father’s file.
#
patterns:
  - "pattern_example"

# Item section. (https://docs.zmenu.dev/configurations/inventories#items)
#
# This is where you will add all the items that will be present in your inventory.
# With zMenu, each item is a Button. A button will allow you to perform specific actions, such as opening a new inventory, changing pages, going back.
# By default, the button will be of type NONE. All buttons will have the same configuration elements.
# Only buttons with types like INVENTORY, BACK etc... will have specific configuration elements.
# All button information here: https://docs.zmenu.dev/configurations/buttons
#
items:

  # Button with multiple slots (https://docs.zmenu.dev/configurations/buttons#slot)
  #
  # You can define a button that will be displayed on multiple slots.
  # To put several slots, you must put as in the example if below. You must write "slots" and not "slot"
  # You’re going to have to put a slot list, but instead of putting each slot in sequence you can make slot range like this:
  # <start slot>-<end slot>, in the example below we have 2-6, which represents slots 2, 3, 4, 5, and 6
  #
  # So we have red glass that will be displayed on all pages of slot 2 to 6
  decorations:
    # Specifies whether the button should appear on all pages (https://docs.zmenu.dev/configurations/buttons#ispermanent)
    isPermanent: true
    item:
      material: RED_STAINED_GLASS_PANE
      name: "&e"
    slots:
      - 2-6 # From slot 2 to slot 6

  # Page 1 (https://docs.zmenu.dev/configurations/buttons#page)
  #
  # Vous pouvez spécifier la page d'un bouton de deux manières différente.
  # The first one will be as in the example below. If your button is on a single slot, you can do this:
  # <page>-<slot>, in the example below we have 1-22, witch represent page 1 and slot 22
  # By default if you do not specify anything, then the page will always be page number 1
  #
  itemInFirstPage:
    slot: 1-22
    item:
      material: BOOK
      name: "&fA book"
      lore:
        - "&7Just a book at first page"

  # Page 2 (https://docs.zmenu.dev/configurations/buttons#page)
  #
  # Now let’s see how to specify the page in another way. In the example if below we have the page value directly.
  # So in this example, the button will be on page 2 and slot 22. This way of writing is easier to understand but also longer.
  # You choose the method you prefer to indicate the page of a button.
  #
  # Attention, if your button has several slots, you must indicate the page this way.
  #
  # The button also has the INVENTORY type (https://docs.zmenu.dev/configurations/buttons#inventory)
  # This button type allows you to navigate between different inventory. You will need to specify the name of the inventory, as well as the plugin from where the inventory was created.
  # It is important to specify the name of the plugin, let’s imagine that inventory several inventories use the same name, its would be impossible to find the right one.
  # By specifying the plugin name you will not have a problem. By default, the plugin used will be zMenu
  #
  # In this example, the button will open the inventory "basic_inventory" of the plugin "zMenu"
  #
  itemInSecondPage:
    type: INVENTORY
    slot: 22
    page: 2
    inventory: "basic_inventory"
    plugin: "zMenu"
    item:
      material: COMPASS
      name: "&fOpen basic inventory"
      lore:
        - "&7Click here for open"
        - "&7the &fbasic inventory"

  # PREVIOUS (https://docs.zmenu.dev/configurations/buttons#previous)
  #
  # The PREVIOUS button returns to the previous page.
  # With zMenu there is the value "else" which allows to specify an else button. When a check is performed, and it is not completed, then the else button will be used.
  # if (verification)
  #   display button
  # else
  #   display another button
  # With this principle, it is possible to display another button if there is no need for a previous page. In the example if below we will change the name, lore and url of the item.
  # If you do not want to display an item if there is no previous page, just do not put anything
  #
  previous:
    # By default, the PREVIOUS and NEXT type buttons will be displayed on all pages, but if you need, you can disable it.
    item:
      url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNjllYTFkODYyNDdmNGFmMzUxZWQxODY2YmNhNmEzMDQwYTA2YzY4MTc3Yzc4ZTQyMzE2YTEwOThlNjBmYjdkMyJ9fX0="
      name: "#18f54c⬅ &fᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
      lore:
        - ""
        - "&f➥ &7Click to access the #18f54cprevious page"
    type: PREVIOUS
    slot: 48
    # This is where you should put the else button. It is quite possible to ambush the else buttons in succession.
    # How you are in an else button, you don’t need to specify the slot, slots, page or isPermanent. The values will be the same if you do not specify them.
    else:
      item:
        url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjc1NDgzNjJhMjRjMGZhODQ1M2U0ZDkzZTY4YzU5NjlkZGJkZTU3YmY2NjY2YzAzMTljMWVkMWU4NGQ4OTA2NSJ9fX0="
        name: "#cf1717✘ &fᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
        lore:
          - ""
          - "&f➥ &7Click to access the #cf1717previous page"

  # NEXT (https://docs.zmenu.dev/configurations/buttons#next)
  #
  # The NEXT Button allows you to go to the next page
  # Same principle as for the PREVIOUS button, you have the same operation here.
  next:
    item:
      url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODI3MWE0NzEwNDQ5NWUzNTdjM2U4ZTgwZjUxMWE5ZjEwMmIwNzAwY2E5Yjg4ZTg4Yjc5NWQzM2ZmMjAxMDVlYiJ9fX0="
      name: "#18f54c➡ &fɴᴇxᴛ ᴘᴀɢᴇ"
      lore:
        - ""
        - "&f➥ &7Click to access the #18f54cnext page"
    type: NEXT
    slot: 50
    else:
      item:
        url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjc1NDgzNjJhMjRjMGZhODQ1M2U0ZDkzZTY4YzU5NjlkZGJkZTU3YmY2NjY2YzAzMTljMWVkMWU4NGQ4OTA2NSJ9fX0="
        name: "#cf1717✘ &fɴᴇxᴛ ᴘᴀɢᴇ"
        lore:
          - ""
          - "&f➥ &7Click to access the #cf1717next page"

```

### Pro\_invnetory.yml

```yaml
####################################################
#
# A pro zMenu configuration for professional
# This configuration includes more complex items, the requirements
#
# The configuration for the command to open this inventory is in the file commands/basic_command.yml
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#   Documentation: https://docs.zmenu.dev
#   Discord: https://discord.groupez.dev
#   Plugin page: https://groupez.dev/resources/zmenu.253
#   Marketplace: https://minecraft-inventory-builder.com
#   Sponsor: https://serveur-minecraft-vote.fr/
#
####################################################

# Size (https://docs.zmenu.dev/configurations/inventories#size)
#
# Allows to set the size of the inventory.
# The inventory size must be a multiple of 9. So you can put 9, 18, 27, 36, 45 and 54
# If this option is not present in the configuration, then the default will be 54
#
size: 45

# Inventory name (https://docs.zmenu.dev/configurations/inventories#name)
#
# This is the title of your inventory. You can put anything in it.
# Color code and placeholders are supported.
# If you are on Paper, Purpur or PufferFish you have access to the color code of MiniMessage (https://docs.advntr.dev/minimessage/format.html)
#
name: "#454545sʜᴏᴘ"

# View Requirement (https://docs.zmenu.dev/configurations/requirements#view-requirement)
#
# Allows verification of different permissions when opening inventory. You can specify a list of requirements, details of requirements available on the plugin documentation.
# You will then be able to define actions to be performed on success or deny.
#
# In the example if below, if the player to the permission "zmenu.shop.show" then the inventory will open, otherwise a message will be sent
#
open_requirement:
  requirements:
    - type: permission
      permission: "zmenu.shop.show"
  deny:
    - type: message
      messages:
        - "&cYou do not have permission to access the shop."

# Item section. (https://docs.zmenu.dev/configurations/inventories#items)
#
# This is where you will add all the items that will be present in your inventory.
# With zMenu, each item is a Button. A button will allow you to perform specific actions, such as opening a new inventory, changing pages, going back.
# By default, the button will be of type NONE. All buttons will have the same configuration elements.
# Only buttons with types like INVENTORY, BACK etc... will have specific configuration elements.
# All button information here: https://docs.zmenu.dev/configurations/buttons
#
items:

  # Button with multiple slots (https://docs.zmenu.dev/configurations/buttons#slot)
  #
  # You can define a button that will be displayed on multiple slots.
  # To put several slots, you must put as in the example if below. You must write "slots" and not "slot"
  # You’re going to have to put a slot list, but instead of putting each slot in sequence you can make slot range like this:
  # <start slot>-<end slot>, in the example below we have 2-6, which represents slots 2, 3, 4, 5, and 6
  #
  # So we have red glass that will be displayed on all pages of slot 2 to 6
  slots:
    # Specifies whether the button should appear on all pages (https://docs.zmenu.dev/configurations/buttons#ispermanent)
    isPermanent: true
    item:
      material: GRAY_STAINED_GLASS_PANE
      name: "&e"
    slots:
      - 0-9 # slot 0 to 9
      - 18
      - 17
      - 26
      - 27
      - 35-44 # slot 35 to 44

  #
  # The item if below will use the click_requirement and view_requirement.
  # You will have the same configuration items as for the open_requirement.
  # Attention, for the click_requirement you will have to define several requirements according to your need.
  # You also need to specify clicks. So you can create multiple requirements for each click.
  #
  # In the example if below, if the player has enough money, and he has the zmenu.shop.use permission then the item will be displayed, otherwise another item will be displayed.
  # And when clicking we will check again the money and the permission of the player before giving him the diamonds.
  #
  # You want to make a shop with zMenu ? Use zShop https://www.spigotmc.org/resources/zshop-1-8-1-20-advanced-inventory-plugin.74073/
  shop1:
    slot: 22
    view_requirement:
      requirements:
        - type: placeholder
          placeholder: "%vault_eco_balance%"
          value: 500
          action: SUPERIOR_OR_EQUAL
        - type: permission
          permission: "zmenu.shop.use"
    click_requirement:
      purchase:
        clicks:
          - ANY # or ALL for all clicks type
        requirements:
          - type: placeholder
            placeholder: "%vault_eco_balance%"
            value: 500
            action: SUPERIOR_OR_EQUAL
          - type: permission
            permission: "zmenu.shop.use"
        deny:
          - type: sound
            sound: VILLAGER_NO
            pitch: 1.5f
            volume: 0.5f
        success:
          - type: sound
            sound: ENTITY_COW_HURT
            pitch: 1.5f
            volume: 0.5f
          - type: console_command
            commands:
              - "eco take %player% 500"
              - "give %player% diamond 64"
    # Allows to refresh the entire button when clicking, the button is dynamic
    refreshOnClick: true
    item:
      material: DIAMOND
      name: "&aClick to buy !"
      lore:
        - "&fYou have enough money to buy this."
    else:
      # Use classic configuration for click, send message and sound
      sound: VILLAGER_NO
      pitch: 1.5f
      volume: 0.5f
      messages:
        - "&cYou dont have enough money to buy this."
      item:
        material: BARRIER
        name: "&cYou can't do that :'("
        lore:
          - "&cYou dont have enough money to buy this."

# Open this menu by clicking a specific item
# You can use /zm giveopenitem <inventory> <player> to retrieve the item to use
#
#openWithItem:
#  # Define the item that will be clicked
#  item:
#    material: compass
#    name: "&eOpen Basic Inventory"
#    lore:
#      - "&7Click on me !"
#  # Look at https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html
#  actions:
#    - LEFT_CLICK_BLOCK
#    - LEFT_CLICK_AIR
#  # Define the type of verification.
#  # Depending on your configuration and need you will define a certain type of verification. Here are all the types that exist:
#  # - full -> Allows to check the itemStack in full, will use the ItemStack#isSimilar method.
#  # - material -> Allows to check only the material
#  # - name -> Allows to check only the display name
#  # - lore -> Allows to check only the lore
#  # - modelid -> Allows to check only the Custom Model Id
#  type: full
```

### Example\_punish.yml

```yaml
#########################################################################################################################################
#
#
#   Sponsor: https://serveur-minecraft-vote.fr/
#   5€ gift code on Minecraft Vote Server : ZMENU (https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU)
#
#   This is a default configuration of the plugin. This configuration shows you the different possibilities of the plugin.
#   Before starting the configuration of the plugin, we invite you to read the documentation.
#
#   Documentation: https://docs.zmenu.dev/
#   Discord: https://discord.groupez.dev/
#   Plugin page: https://groupez.dev/resources/zmenu.253
#
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#
#   Commands and permissions:
#   - /zm » Display the list of commands (aliases: /zmenu) - zmenu.use
#   - /zm open <menu> [<player>] [<display message>] » Opens the specified inventory - menu.open
#   - /zm reload » Reload configurations - menu.reload
#   - /zm reload config » Reload config.json and messages.yml files - zmenu.reload
#   - /zm reload inventory [<inventory name>] » Reload inventories files - zmenu.reload
#   - /zm reload command [<command name>] » Reload commands files - zmenu.reload
#   - /zm version » Show plugin version
#   - /zm convert » Convert other plugin to zMenu - zmenu.convert
#   - /<command> » Open specific file - Custom permission
#
#
#########################################################################################################################################

name: "#03fc98Select ban duration"
size: 27
items:
  '0':
    item:
      material: BLACK_STAINED_GLASS_PANE
      name: '&f'
    slots:
    - 0-0
    - 8-9
    - 17-18
    - 26-26
  '1':
    item:
      material: GRAY_STAINED_GLASS_PANE
      name: '&f'
    slots:
    - 1-7
    - 19-25
  '10':
    slot: 10
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 1d %zmenu_argument_reason%"
    item:
      material: CLOCK
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 1 day'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '11':
    slot: 11
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 3d %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 3
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 3 days'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '12':
    slot: 12
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 1w %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 7
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 1 week'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '13':
    slot: 13
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 1mo %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 30
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 1 month'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '14':
    slot: 14
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 3mo %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 3
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 3 months'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '15':
    slot: 15
    closeInventory: true
    commands:
    - "tempban %zmenu_argument_target% 365d %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 12
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• 1 year'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '16':
    slot: 16
    closeInventory: true
    commands:
    - "ban %zmenu_argument_target% %zmenu_argument_reason%"
    item:
      material: CLOCK
      amount: 64
      name: '#db3214Ban &f&n%zmenu_argument_target%'
      lore:
      - ''
      - '#148bdbReason'
      - ' &f• %zmenu_argument_reason%'
      - ''
      - '#148bdbDuration'
      - ' &f• Permanent'
      - ''
      - '&f» &a&nClick&f to confirm ban'
  '22':
    slot: 22
    closeInventory: true
    item:
      material: BARRIER
      name: '&f» &c&nClick&f to cancel'

```

## 指令配置

### Commands.yml

```yaml
#########################################################################################################################################
#
#
#   Sponsor: https://serveur-minecraft-vote.fr/
#   5€ gift code on Minecraft Vote Server : ZMENU (https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU)
#
#   This is a default configuration of the plugin. This configuration shows you the different possibilities of the plugin.
#   Before starting the configuration of the plugin, we invite you to read the documentation.
#
#   Documentation: https://docs.zmenu.dev/
#   Discord: https://discord.groupez.dev/
#   Plugin page: https://groupez.dev/resources/zmenu.253
#
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#
#   Commands and permissions:
#   - /zm » Display the list of commands (aliases: /zmenu) - zmenu.use
#   - /zm open <menu> [<player>] [<display message>] » Opens the specified inventory - menu.open
#   - /zm reload » Reload configurations - menu.reload
#   - /zm reload config » Reload config.json and messages.yml files - zmenu.reload
#   - /zm reload inventory [<inventory name>] » Reload inventories files - zmenu.reload
#   - /zm reload command [<command name>] » Reload commands files - zmenu.reload
#   - /zm version » Show plugin version
#   - /zm convert » Convert other plugin to zMenu - zmenu.convert
#   - /<command> » Open specific file - Custom permission
#
#
#########################################################################################################################################

commands:
  basic_command:
    command: basic_command
    inventory: basic_inventory
  advanced_command:
    command: advanced_command
    permission: "admin.use"
    aliases:
      - zai
    inventory: advanced_inventory
  pro_command:
    command: pro_command
    inventory: pro_inventory
  openbook:
    command: openbook
    actions:
      - type: book
        author: "Maxlego08" # Book author
        title: "&cTest" # Book title
        lines: # Book pages
          1: # First page
            - '     #34ebe8zMenu'
            - ''
            - ''
            - '<hover:show_text:"#34eba8Open an url !"><click:open_url:"https://minecraft-inventory-builder.com/">#f0af24Open URL<reset>'

```

### Punish.yml

```yaml
#########################################################################################################################################
#
#
#   Sponsor: https://serveur-minecraft-vote.fr/
#   5€ gift code on Minecraft Vote Server : ZMENU (https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU)
#
#   This is a default configuration of the plugin. This configuration shows you the different possibilities of the plugin.
#   Before starting the configuration of the plugin, we invite you to read the documentation.
#
#   Documentation: https://docs.zmenu.dev/
#   Discord: https://discord.groupez.dev/
#   Plugin page: https://groupez.dev/resources/zmenu.253
#
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#
#   Commands and permissions:
#   - /zm » Display the list of commands (aliases: /zmenu) - zmenu.use
#   - /zm open <menu> [<player>] [<display message>] » Opens the specified inventory - menu.open
#   - /zm reload » Reload configurations - menu.reload
#   - /zm reload config » Reload config.json and messages.yml files - zmenu.reload
#   - /zm reload inventory [<inventory name>] » Reload inventories files - zmenu.reload
#   - /zm reload command [<command name>] » Reload commands files - zmenu.reload
#   - /zm version » Show plugin version
#   - /zm convert » Convert other plugin to zMenu - zmenu.convert
#   - /<command> » Open specific file - Custom permission
#
#
#########################################################################################################################################

commands:
  punish:
    command: punish
    permission: "admin.punish"
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - name: target
      - name: reason
        auto-completion:
          - cheat
          - chat
          - skin
          - other
        actions:
          - type: message
            messages:
              - "&7You will put a punishment to the player &f&n%target%&r &7with the reason&8: &f%reason%"
```

## 模板配置

### Pattern\_example

```yaml
#########################################################################################################################################
#
#
#   Sponsor: https://serveur-minecraft-vote.fr/
#   5€ gift code on Minecraft Vote Server : ZMENU (https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU)
#
#   This is a default configuration of the plugin. This configuration shows you the different possibilities of the plugin.
#   Before starting the configuration of the plugin, we invite you to read the documentation.
#
#   Documentation: https://docs.zmenu.dev/
#   Discord: https://discord.groupez.dev/
#   Plugin page: https://groupez.dev/resources/zmenu.253
#   Marketplace: https://minecraft-inventory-builder.com/
#
#
#  ███████╗███╗░░░███╗███████╗███╗░░██╗██╗░░░██╗
#  ╚════██║████╗░████║██╔════╝████╗░██║██║░░░██║
#  ░░███╔═╝██╔████╔██║█████╗░░██╔██╗██║██║░░░██║
#  ██╔══╝░░██║╚██╔╝██║██╔══╝░░██║╚████║██║░░░██║
#  ███████╗██║░╚═╝░██║███████╗██║░╚███║╚██████╔╝
#  ╚══════╝╚═╝░░░░░╚═╝╚══════╝╚═╝░░╚══╝░╚═════╝░
#
#
#   Commands and permissions:
#   - /zm » Display the list of commands (aliases: /zmenu) - zmenu.use
#   - /zm open <menu> [<player>] [<display message>] » Opens the specified inventory - menu.open
#   - /zm reload » Reload configurations - menu.reload
#   - /zm reload config » Reload config.json and messages.yml files - zmenu.reload
#   - /zm reload inventory [<inventory name>] » Reload inventories files - zmenu.reload
#   - /zm reload command [<command name>] » Reload commands files - zmenu.reload
#   - /zm version » Show plugin version
#   - /zm convert » Convert other plugin to zMenu - zmenu.convert
#   - /<command> » Open specific file - Custom permission
#
#
#########################################################################################################################################

name: "pattern_example"
size: 54
items:
  example1:
    isPermanent: true
    item:
      material: IRON_INGOT
      name: "&fExample of pattern"
    slots:
      - 0
      - 8
      - 45
      - 53

```
