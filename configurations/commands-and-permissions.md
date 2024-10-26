# 📜 Commands and Permissions

## Commands

| Command | Permission | Description |
|---------|------------|-------------|
| `/zm` (aliases: `/zmenu`) | `zmenu.use` | Display the list of commands. |
| `/zm open <menu> [<player>] [<display message>] [<args>]` | `zmenu.open` | Opens the specified inventory. |
| `/zm reload` | `zmenu.reload` | Reload configurations. |
| `/zm reload config` | `zmenu.reload` | Reload `config.json` and `messages.yml` files. |
| `/zm reload inventory [<inventory name>]` | `zmenu.reload` | Reload inventory files. |
| `/zm reload command [<command name>]` | `zmenu.reload` | Reload command files. |
| `/zm version` | - | Show plugin version. |
| `/zm convert` | `zmenu.convert` | Convert DeluxeMenu to zMenu. |
| `/zm list` | `zmenu.list` | Display the list of inventories. |
| `/zm create <file name> <inventory size> <inventory name>` | `zmenu.create` | Create a new inventory file. You can add items afterward. |
| `/zm save <item name>` | `zmenu.save` | Save the item you have in hand in the plugin configuration format. |
| `/zm giveopenitem <inventory> [<player>]` | `zmenu.open.item` | Retrieve the item used to open the inventory during a click. |
| `/<command>` | Custom permission | Open a specific file. |

List of commands for the player data system can be found [here](player-data.md).

### Open Command with Arguments

You can use the `/zm open` command with arguments (more details [here](commands.md#informations)).

For example, with the default inventory `example_punish`, you can define two arguments to be used. You can do this in two ways:

- **Specify Argument Names**: Use `<argument name>:<argument value>` format.
  - Example: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:test`
  - Result: `%zmenu_argument_target%` and `%zmenu_argument_reason%`
  - You can also add more arguments: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:"this is a really long reason"`

- **Use Values Directly**: The argument names will be indexed as 0, 1, etc.
  - Example: `/zm open zmenu:example_punish Maxlego08 false Maxlego09 test`
  - Result: `%zmenu_argument_0%` and `%zmenu_argument_1%`
