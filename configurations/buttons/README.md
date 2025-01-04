---
description: All information about the buttons
---

# ⏹️ Buttons

## Informations

Buttons allow you to <mark style="color:green;">customize</mark> the actions in your inventory. You need to specify the type of each button and configure the elements specific to that button type. Below, you'll find the buttons that are integrated by default in the plugin; other plugins can also add new types of buttons.

For each button, you must specify an `Item`. To learn how to configure an `Item`, go [here](../items.md).

## Configuration

Here are the configuration elements that are common to all types of buttons. You can use these elements universally across different button types.

```yaml
example: 
  # Select the button type, NONE by default
  type: <button type>
  # Set the slot of the button, 0 by default
  slot: <slot>
  # Put slots for the button, empty by default
  slots: <list of slot>
  # Set the button page, 1 by default
  page: <page>
  # Define whether the button should appear on all pages
  isPermanent: <true of false>
  # Item that will be displayed, please look at the Items documentation
  item: <itemstack>
  # Played a sound when clicking
  sound: <sound from XSound>
  # Sound volume
  volume: <volume of sound>
  # Sound pitch
  pitch: <pitch of sound>
  # Messages sent during clicks
  messages: <list of messages>
  # Displays a link in the message list
  openLink: 
    link: <link>
    message: <message>
    replace: <replace placeholder>
    hover: <list of messages>
  # Close inventory on click
  closeInventory: <true or false>
  # Refresh item name and lore on click
  refreshOnClick: <true or false>  
  # Display player head, need a placeholder or a player name
  playerHead: <placeholder>
  # You can set one or more permissions to display the item
  permission: <permission>  
  # Show another button if not checked (placeholder check, permissions or other)
  else: <else button>
  # Placeholder
  placeholder: <placeholder>
  # Placeholder value
  value: <value for placeholder>
  # Placeholder Action
  action: <action for placeholder>
  # List of placeholders
  placeholders: <list of placeholder>
  # Update button on click (update everything)
  update: <boolean>
  # Command send by the players
  commands: <list of text>
  # Command send by the console on click
  consoleCommands: <list of text>
  # Command send by the console on right click
  consoleRightCommands: <list of text>
  # Command send by the console on left click
  consoleLeftCommands: <list of text>
  consolePermissionCommands: <list of text>
  consolePermission: <permissions>
  # Update item name and lore when the player click on the inventory
  updateOnClick: <boolean>
  # Sets the requirements the player should have to see the button. 
  view_requirement: <requirement>
  # Sets the requirements the player should have to click on the button. 
  click_requirement: <requirement>
```

### TYPE

```yaml
type: <button type>
```

The type of the button. By default, the type will be set to `NONE`. It is important to set the button type if you want to perform specific actions.

***

### SLOT

```yaml
slot: <number between 0 and inventory limit>
```

```yaml
slot: <page>-<slot>
```

Specify the slot where your item will be displayed.

{% hint style="info" %}
* Slots start at 0.
* You can specify the page number directly in the slot. The format should be: `<page>-<slot>`. For example, for a button on page 2 and slot 8, you would use: `2-8`.
* To place multiple items in the same slot, you must use the `else` button.
{% endhint %}

<figure><img src="../../.gitbook/assets/slot.png" alt=""><figcaption><p>Double chest slots</p></figcaption></figure>

To display a button on multiple slots, you can do it like this:

```yaml
slots:
  - 0
  - 1
  - 2
  - 3
  - 4
  ...
```

You can also create slot ranges using this format: `<startslot>-<endslot>`.

```yaml
slots:
  - 0-9 # From slot 0 to slot 9
  - 18
  - 17
  - 26
  - 27
  - 35
  - 36
  - 44-53 # From slot 44 to 53
```

***

### Page

```yaml
page: <page numer>
```

Allows you to specify the page where the button will be displayed. By default, the page will be set to 1.

***

### IsPermanent

```yaml
isPermanent: <true of false>
```

Allows you to specify if the button should be displayed on all pages of the inventory. If your inventory has only one page, you don’t need to use this option.

***

### useCache

```yaml
useCache: <true of false>
```

Allows you to enable or disable caching on the item. By default, caching will always be used if the button item does not contain a placeholder.

***

### Item

```yaml
item: <itemstack>
```

Allows you to specify the item that will be displayed. For more information, click [here](https://zmenu.groupez.dev/configurations/items).

***

### Sound

```yaml
sound: ENTITY_COW_HURT
pitch: 1.5
volume: 0.5
```

Allows you to play a sound for the player when they click. You must use the sounds available in [XSound.](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java) You can also adjust the pitch and volume of the sound.

***

### Messages

```yaml
messages:
  - <line 1>
  - <line 2>
  ...
```

Allows you to send a list of messages to the player upon clicking. You can use the [MiniMessage](https://docs.advntr.dev/minimessage/format.html) format to send messages with click or hover actions.

***

### Openlink

```yaml
link: <link>
message: <message>
replace: <replace string>
hover:
  - <line 1>
  - <line 2>
  ...
```

Allows you to send a clickable message to the player. You need to include in your message list a text that will be replaced by the clickable link. An example is provided below.

{% hint style="warning" %}
Please use this only if your server is running an older version of Minecraft. Otherwise, use the [MiniMessage](https://docs.advntr.dev/minimessage/format.html) format, which is much easier to work with.
{% endhint %}

> Example:

```yaml
messages:
  - "&8(&6zMenu&8) &fAdd your server to the site &3Serveur Minecraft Vote"
  - "&8(&6zMenu&8) %link% &d!"
openLink:
  link: "https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU"
  message: "&b&lClick here"
  replace: "%link%"
  hover:
    - "&bClick here !"
```

***

### CloseInventory

```yaml
closeInventory: <true of false>
```

Allows you to close the inventory after clicking.

***

### RefreshOnClick

```yaml
refreshOnClick: <true or false>
```

Allows the button to refresh after a click. You can use this feature to create a shop, for example. An example is provided in the default configuration.

***

### PlayerHead

```yaml
playerHead: <placeholder>
```

Allows you to display a player's head based on a placeholder. You can use the placeholder `%player%` to display the head of the player who opens the inventory.

A caching system ensures the direct display of the skin for the heads.

***

### Permission

```yaml
permission: <permission>
```

Allows you to define a permission that the player must have to display the item. You can reverse the permission by adding `!` in front of the permission, which will cause the plugin to check that the player does **not** have the permission.

You can also define a list of permissions the player must have:

```yaml
permission:
  - "first.permission"
  - "!second.permission"
```

***

### Or Permission

Allows you to define a list of permissions, where the player only needs to have one of them.

```yaml
orPermission:
  - "first.permission"
  - "!second.permission"
```

***

### Else

```yaml
else: <else button>
```

Allows you to display an `else` button if the player doesn't have the required permission. You can place multiple `else` buttons in a row without any issues. An example of this usage can be found in the default configuration.

Example:

```yaml
items:
  |mybutton:
  |  <item configuration>
  |--|else:
  |  |  <first else configuration>
  |  |--|else:
  |  |--|  <second else configuration>
```

***

### Placeholder

```yaml
  placeHolder: <placeholder>
  value: <value for placeholder>
  action: <action for placeholder>
```

Allows you to define a permission using a placeholder. You must specify the placeholder, the action to be performed with the value, and the value that will be checked.

**Actions:**

* **`BOOLEAN`** (alias: `b=`): Checks if a value is true or false.
* **`EQUALS_STRING`** (alias: `s=`): Checks if the text is strictly equal to the value.
* **`EQUALSIGNORECASE_STRING`** (alias: `s==`): Checks if the text is equal to the value, ignoring case.
* **`CONTAINS_STRING`** (alias: `sc`): Checks if the text is contained within the value.
* **`DIFFERENT_STRING`** (alias: `s!=`): Checks if the text is different from the value.
* **`SUPERIOR`** (alias: `>`): Checks if a number is strictly greater than the value.
* **`LOWER`** (alias: `<`): Checks if a number is strictly less than the value.
* **`SUPERIOR_OR_EQUAL`** (alias: `>=`): Checks if a number is greater than or equal to the value.
* **`LOWER_OR_EQUAL`** (alias: `<=`): Checks if a number is less than or equal to the value.
* **`EQUAL_TO`** (alias: `==`): Verifies that two numbers are identical.

You can check multiple placeholders like this:

```yml
placeholders:
  - placeholder: <your placeholder>
    value: <your value>
    action: <your action>
  - placeholder: <your placeholder>
    value: <your value>
    action: <your action>
```

***

### Update

```yaml
update: <true or false>
```

Enables the automatic update of the item's name and lore. To configure the update interval, please refer to [this section](../inventories.md#update-interval).

***

### UpdateMasterButton

```yaml
updateMasterButton: <true or false>
```

Allows you to completely update the button. You need to enable the update option for this feature to be activated. Instead of just updating the name and lore, this option refreshes the entire button. This includes rechecking permissions, requirements, and the `else` button.

***

### UpdateOnClick

```yaml
updateOnClick: <true of false>
```

Allows your button to be updated whenever a player clicks anywhere in the inventory, regardless of the slot.

***

### Commands

```yaml
commands: 
  - "<your command>"
```

Allows the player to execute a list of commands. You can use the placeholder `%player%` to retrieve the username of the player executing the commands.

***

### Console Commands

```yaml
consoleCommands: # Commands to be executed by the console no matter the click
  - "<your command>"
consoleRightCommands: # Commands to be executed by the console when right-click
  - "<your command>"
consoleLeftCommands: # Commands to be executed by the console when left-click
  - "<your command>"
consolePermissionCommands: # Commands to be executed by the console if the player has permission
  - "<your command>"
consolePermission: "<permission>
```

You can execute commands from the console based on the player's click, as well as commands that require specific player permissions. You can use the placeholder `%player%` to retrieve the username of the player executing the commands.

***

### View Requirement

```yaml
view_requirement:
  requirements: # In this example the player must have a balance greater than or equal to 5000
    - type: placeholder
      placeholder: "%vault_eco_balance%"
      value: "5000"
      action: "SUPERIOR_OR_EQUAL"
```

Sets the conditions the player must meet to see the button. This can include permissions, placeholders, and other criteria. For more information, refer to [this section](requirements.md#view-requirement).

***

### Click Requirement

Defines the conditions the player must meet to click on the button. These requirements are checked when the player clicks, and actions can be executed based on the success or failure of these conditions. For more information, refer to [this section](requirements.md#click-requirement).

***

### Actions

You can define a list of actions to perform when clicking. These actions can include sending messages, executing commands, opening a book, and more. For more information, refer to [this section](actions.md).

```yaml
actions:
  - type: message
    messages:
      - "example"
```

***

### Error item ([zMenu+](https://minecraft-inventory-builder.com/resources/zmenu.4))

**Example of Inventory with Fail Item:**

In this example, if the player is not in creative mode, a barrier with the name "Error" will be displayed for 10 ticks.

```yaml
name: "&8Test"
size: 54
items:
  example:
    item:
      material: DIAMOND
    slot: 22
    error_item:
      duration: 10 # Duration of item display
      item: # Item to display
        material: BARRIER
        name: "&cError"
    click_requirement:
      left_click:
        clicks:
          - ALL
        requirements:
          - type: placeholder
            placeholder: "%player_gamemode%"
            value: "CREATIVE"
            action: equals_string
```

<figure><img src="../../.gitbook/assets/error_item.gif" alt=""><figcaption></figcaption></figure>

***

## NONE

The `NONE` type is the default type; it simply displays a button. You don't need to specify it, as it will be automatically selected if the plugin doesn't detect a different type.

## INVENTORY

The `INVENTORY` type allows the player to open a new inventory.

```yaml
inventory: <inventory file name>
plugin: <plugin name>
toPage: <page>
arguments:
  - <argument 1>
  - <argument 2>
```

* **`inventory`**: The name of the inventory you want to open. This should match the name of the inventory file.
* **`plugin`**: The name of the plugin from which the inventory originates. It's advisable to specify the plugin name to avoid opening a different inventory with the same name.
* **`toPage`**: The page number you want to open. The default is page 1.
* **`arguments`**: A list of arguments you can add. Each argument can include a name in the following format: `<name>:<value>`.

You must specify the inventory's name, which corresponds to the file name where the inventory is stored. Additionally, it's recommended to specify the plugin name to avoid confusion if two inventories share the same name.

## BACK

The `BACK` type allows you to return to the previous inventory.

## HOME

The `HOME` type allows you to return to the main inventory, which is the first one that was opened.

## NEXT

The `NEXT` type allows you to go to the next page, if it exists. You can use the `else` element to display another button if there is no next page.

Example:

```yaml
next:
  type: NEXT
  isPermanent: true
  slot: 50
  item:
    material: ARROW
    name: "&fNext"
  else: #Displays another button if there is no next page.
    item:
      material: BLACK_STAINED_GLASS_PANE
```

## PREVIOUS

The `PREVIOUS` type allows you to go to the previous page, if it exists. You can use the `else` element to display another button if there is no previous page.

```yaml
previous:
  type: PREVIOUS
  isPermanent: true
  slot: 48
  item:
    material: ARROW
    name: "&fPrevious"
  else: #Displays another button if there is no next page.
    item:
      material: BLACK_STAINED_GLASS_PANE
```

## MAINMENU

The `MAINMENU` type allows you to return to the main inventory specified in the `config.json`.

## JUMP

The `JUMP` type allows you to change to a predefined page.

```yaml
jumpButton:
  type: JUMP
  toPage: 5
```

## PAGINATION ([zMenu+](https://minecraft-inventory-builder.com/resources/zmenu.4))

**Example of Inventory with Pagination Button:**

In this example, the items will be displayed in slots 21, 22, and 23 across multiple pages.

The list of items includes the material and the name. You can put anything you want in the list. To use the values, you must reference them with the placeholder keys. In this example, the keys will be `%material%` and `%name%`.

You can also modify the values like this:

* `%lower_<key>%` - Displays the value in lowercase.
* `%upper_<key>%` - Displays the value in uppercase.
* `%capitalize_<key>%` - Displays the value with the first letter capitalized.

You can use placeholders everywhere, including in your requirements, commands, and other placeholders.

```yaml
name: "&8&lPagination &r&7%page%&8/&7%maxPage%"
size: 54
items:
  example:
    type: PAGINATION
    elements:
      - material: DIAMOND
        name: "diaMond"
      - material: IRON_INGOT
        name: "iron_INGOT"
      - material: EMERALD
        name: "emeRald"
      - material: COAL
        name: "cOAl"
      - material: GOLD_INGOT
        name: "gold_INGOT"
    slots:
      - 21-23
    item:
      material: "%material%"
      name: "&e%index% &7- &b%current%"
      lore:
        - "&8&m-----------------------"
        - ""
        - "&f%name% &8- &7Normal"
        - "&f%upper_name% &8- &fUpper case"
        - "&f%lower_name% &8- &7lower case"
        - "&f%capitalize_name% &8- &7Capitalized"
        - ""
        - "&8&m-----------------------"
  next:
    type: NEXT
    isPermanent: true
    slot: 50
    item:
      material: ARROW
      name: "&fNext"
  previous:
    type: PREVIOUS
    isPermanent: true
    slot: 48
    item:
      material: ARROW
      name: "&fPrevious"
```

<figure><img src="../../.gitbook/assets/pagination.gif" alt=""><figcaption></figcaption></figure>

## DYNAMIC PAGINATION ([zMenu+](https://minecraft-inventory-builder.com/resources/zmenu.4))

This feature allows you to create a dynamic inventory using placeholders, offering limitless possibilities such as creating a ranking system. The only limit is your imagination.

In the example below, placeholders are generated by zMenu+ as an example:

* `%zmenu+_pagination_size%` - Returns the size of your list. This value will change when the plugin is loaded.
* `%zmenu+_pagination_name_<index>%` - Returns text based on the index. The text is generated automatically when the plugin is loaded.

You must specify the start and end of the pagination using `start` and `end`, which work with PlaceholderAPI.

Additionally, you have three internal placeholders to help you identify the button number that is displayed:

* `%index%` - Returns the index of the button, starting at 0.
* `%current%` - Returns the index of the button plus 1, starting at 1.
* `%value%` - Returns the value of the button.

If your pagination does not start with 0, you must use this placeholder to retrieve the correct index of the button.

```yaml
name: "&8Dynamic Pagination &7%page%/%maxPage%"
size: 54
items:
  pagination:
    type: DYNAMIC_PAGINATION
    start: 10 # You need to specify the beginning, here 10. But the easiest way is to start at 0
    end: "%zmenu+_pagination_size%" # The number or pagination must stop
    slots:
      - 20-24
      - 29-33
    item:
      material: IRON_INGOT
      name: "&fHey its &e%zmenu+_pagination_name_%value%% &8- &f%index%"
      lore:
        - "&7Index&8: &f%index%"
        - "&7Current&8: &f%current%"
        - "&7Value&8: &f%value%"

  next:
    type: NEXT
    isPermanent: true
    slot: 50
    item:
      material: ARROW
      name: "&fNext"

  previous:
    type: PREVIOUS
    isPermanent: true
    slot: 48
    item:
      material: ARROW
      name: "&fPrevious"
```

<figure><img src="../../.gitbook/assets/dynamic_pagination.gif" alt=""><figcaption></figcaption></figure>

## INPUT ([zMenu+](https://minecraft-inventory-builder.com/resources/zmenu.4))

This feature allows the player to input a message in the chat and triggers actions based on success or error.

**Input Types:**

* **NUMBER** - Checks a number; you can set a minimum and maximum value.
* **TEXT** - Checks a text input; you can set a regex pattern for validation.
* **ONLINE\_PLAYER** - Checks if the input matches the nickname of an online player.

You can add conditions based on the input type:

* For **NUMBER**, you can specify a minimum and maximum value.
* For **TEXT**, you can use a regex pattern for validation.

**Example:** In this example, the button checks if the chosen number is between 0 and 100.

```yaml
name: "&8Input Inventory"
size: 27
items:
  chooseAmount:
    slot: 13
    type: INPUT
    item:
      material: DIAMOND_SWORD
      name: '&fChoose a number'
      lore:
        - ''
        - '&7Please choose a number between &b0&f and &a100'
    # Type of input to check
    # NUMBER - Allows to check a number, you can set a minimum and maximum
    # TEXT - Allows to check a text, you can set regex
    # ONLINE_PLAYER - Allows to check the nickname of a player online
    inputType: NUMBER
    # Conditions has checked, works with PlaceholderAPI
    conditions:
      min: 0
      max: 100
      # regex: "^[a-zA-Z0-9]+$"
    # Action performed in case of successful conditions
    success_actions:
      - type: console_command
        commands:
          - "bc %player% has just chosen the number %input% !" # or placeholder: %zmenu_input%
    # Action performed in case conditions failed
    error_actions:
      - type: message
        messages:
          - "&cYou must choose a number between 0 and 100."
    # Action performed when clicking, by default the inventory will not close, you must close it, then send a message or perform other action at the same time
    actions:
      - type: message
        messages:
          - "&7Please choose a number between &b0&f and &a100&8:"
      - type: close
```

<figure><img src="../../.gitbook/assets/input.gif" alt=""><figcaption></figcaption></figure>
