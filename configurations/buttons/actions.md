# ☢️ 操作

通过需求，您可以定义成功和失败后的操作。以下是可以执行的操作列表。

**示例：** 您需要像这样创建操作列表：

```yaml
success_actions:
  - type: player_command
    commands:
      - "firstcommand"
      - "seconds commands %player%"
  - type: console_command
    commands:
      - "firstcommand"
      - "seconds commands %player%"      
  - type: message
    messages:
      - "firstcommand"
      - "seconds commands %player%"   
```

您可以为列表中的每个项目添加延迟（以 ticks 为单位）。这样做：

```yaml
success_actions:
  - type: player_command
    delay: 10 # 10 ticks
    commands:
      - "firstcommand"
      - "seconds commands %player%"
```

<table data-full-width="true"><thead><tr><th width="544">操作</th><th>描述</th></tr></thead><tbody><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: player_command
  commands:
    - "firstcommand"
    - "seconds commands %player%"
  commandInChat: false # 默认值为 false
</code></pre></td><td>以玩家身份执行指令。您也可以将指令发送到玩家的聊天中。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: console_command
  commands:
    - "firstcommand"
    - "seconds commands %player%"
</code></pre></td><td>以控制台身份执行指令。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: message
  messages:
    - "my message"
    - "my second messages"
  minimessage: true # 默认值为 true
</code></pre></td><td>发送消息给玩家。您可以使用占位符、颜色代码和格式代码。如果您的服务器支持 MiniMessage 格式，默认启用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast
  messages:
    - "my message"
    - "my second message to %player%"
  minimessage: true # 默认值为 true
</code></pre></td><td>向所有在线玩家发送消息。您可以使用占位符、颜色代码和格式代码。如果您的服务器支持 MiniMessage 格式，默认启用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: chat
  messages:
    - "my message"
</code></pre></td><td>代表玩家发送消息。您可以使用占位符、颜色代码和格式代码。如果您的服务器支持 MiniMessage 格式，默认启用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: close
</code></pre></td><td>关闭玩家的菜单。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: inventory
  inventory: &#x3C;inventory name>
  plugin: &#x3C;plugin name>
  page: &#x3C;page>
  arguments: &#x3C;argument list>
</code></pre></td><td>打开 zMenu 的菜单。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: connect
  server: &#x3C;server name>
</code></pre></td><td>允许将玩家发送到另一个服务器，仅在 BungeeCord 和 Velocity 上有效。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 默认值为 1.0f
  volume: &#x3C;sound volume> # 默认值为 1.0f
</code></pre></td><td>向玩家发送声音，您必须使用 <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a> 来处理声音。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast_sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 默认值为 1.0f
  volume: &#x3C;sound volume> # 默认值为 1.0f
</code></pre></td><td>向所有在线玩家发送声音，您必须使用 <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a> 来处理声音。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: data
  action: &#x3C;SET/REMOVE/ADD/SUBTRACT>
  key: &#x3C;data key>
  value: &#x3C;data value>
  seconds: &#x3C;expire seconds> # 默认值为 0
</code></pre></td><td>更新 <a href="../player-data.md">玩家数据</a>。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: refresh  
</code></pre><p></p></td><td>刷新当前按钮。仅在点击需求中有效。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: back
</code></pre></td><td>返回到上一个菜单。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: shopkeeper
  name: &#x3C;shopkeeper name>
</code></pre></td><td>打开一个 <a href="https://www.spigotmc.org/threads/shopkeepers.447969/">Shopkeeper</a> 交易菜单</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: book
  author: "Maxlego08" # 书的作者
  title: "&#x26;cTest" # 书的标题
  lines: # 书的页面
    1: # 第一个页面
      - '     #34ebe8zMenu'
      - ''
      - ''
      - '&#x3C;hover:show_text:"#34eba8Open an url !">&#x3C;click:open_url:"https://minecraft-inventory-builder.com/">#f0af24Open URL&#x3C;reset>'
</code></pre></td><td>为玩家打开一本书。您可以指定书的标题、作者和页面。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: actionbar
  message: "my message"
  minimessage: true # 默认值为 true
</code></pre></td><td>允许您在玩家的动作栏中发送消息。您可以在这里使用占位符和颜色/格式代码。如果您的服务器支持 MiniMessage 格式，默认启用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: withdraw
  amount: &#x3C;amount>
</code></pre></td><td>允许从玩家账户中提取金钱。与 <a href="https://www.spigotmc.org/resources/vault.34315/">Vault</a> 一起使用。</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: deposit
  amount: &#x3C;amount>
</code></pre></td><td>允许将金钱存入玩家账户。与 <a href="https://www.spigotmc.org/resources/vault.34315/">Vault</a> 一起使用。</td></tr></tbody></table>
