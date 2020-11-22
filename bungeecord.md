# Bungeecord

{% hint style="info" %}
**DISCLAIMER 1:** Bungeecord server is **not** a Lobby/Hub server! Bungeecord only allows you to teleport between multiple Spigot \(Paper\) Minecraft servers \(Lobby/Hub, Gamemode 1, Gamemode 2, ... Gamemode n\).

**DISCLAIMER 2:** This tutorial only works with on Minecraft: Java Edition servers using Spigot \(Paper, and it's forks\)!

**DISCLAIMER 3:** After you are done with this tutorial use Bungeecord server's IP address to connect to your server network. Other servers IP's won't work!

**DISCLAIMER 4:** If you already got \#custom-ip, don't forget to edit SRV Record Details to match your Bungeecord server's IP. To make the change, go to the [https://dash.cloudflare.com/](https://dash.cloudflare.com/) &gt; Click on your domain &gt; Go to the `DNS` Page &gt; Click on the `SRV 0 Port IP` &gt; Follow step **19\)** from \#custom-ip.
{% endhint %}

## What is Bungeecord and why do I need it?

Bungeecord or Waterfall \(Optimized Bungeecord\) is Minecraft: Java Edition proxy server software that allows you to teleport between multiple Minecraft servers.

You can use commands like /server &lt;server name&gt; or just /&lt;server name&gt; command to teleport from one server to another.

If you have Lobby/Hub server, you are also able to switch server with use of Compass or Nether Portals!

Well then, let's get right into it!

## Prerequisites

To create a Bungeecord server network, you will need:

**`*`** Patience.

**`*`** 3 or more servers

_`(Optional)`_

**`*`** Change your Server names for better organization.

To get around better, we recommend changing server names. Keep it simple and name server by what their content is.

For example, if you are running Factions server, simply name it "Factions". If it's Bungeecord/Waterfall server - "Bungeecord", "Bungee", "Proxy", "Waterfall", ...

If you don't know how to change the name of your server, Open up your host's Panel &gt; Click on the Server name &gt; Scroll down the Sidebar \(Where Console, File Manager, ... are located\) &gt; Click on the _`Configuration`_ button &gt; Server name

## Setting up Spigot server

**`1.`** Go to the your host's panel and open up your Spigot server

**`2.`** Go into the _`File Manager`_

**`3.`** Go into _`server.properties`_

1. Find `online-mode=true`
2. Change it to `online-mode=false`
3. Save

**`4.`** Go into _`spigot.yml`_

1. Find `bungeecord=false`
2. Change it to `bungeecord=true`
3. Save

## Setting up Bungeecord server

**`1.`** Go to the your host's panel and open up your Bungeecord/Waterfall/Proxy server.[![](https://media.discordapp.net/attachments/471284424273821696/560152624364650499/firefox_2AQesbXgMk.png?width=400&height=225)](https://cdn.discordapp.com/attachments/471284424273821696/560152624364650499/firefox_2AQesbXgMk.png)

**`2.`** _If you have some files on your server already, make sure to backup them!_

1. Go into the _`File Manager`_ 
2. Select all Files and Folder 
3. Click on the _`Mass Actions`_ Button 
4. _`Delete files`_

_\`\`_[![](https://media.discordapp.net/attachments/471284424273821696/560152712797487115/ksxuf8dw68.png?width=400&height=212)](https://cdn.discordapp.com/attachments/471284424273821696/560152712797487115/ksxuf8dw68.png)

**`3.`** Download [waterfall](https://papermc.io/ci/job/waterfall/lastSuccessfulBuild/artifact/Waterfall-Proxy/bootstrap/target/Waterfall.jar), If downloaded file is flagged as Dangerous, Click on the `Keep` Button. The file is not dangerous! Chrome and Chrome-based browsers flag all JAR files as dangerous, even if they are not.

**`4.`** Upload downloaded `Waterfall.jar` file to your Bungeecord server.

Drag & Drop the file from downloads to the File Manager window.

**OR**

Click on the _`Upload`_ button, select downloaded `Waterfall.jar` file and click _`Open`_.

[![](https://media.discordapp.net/attachments/471284424273821696/560152835451256842/lPWVYD0dA9.png?width=400&height=110)](https://cdn.discordapp.com/attachments/471284424273821696/560152835451256842/lPWVYD0dA9.png)

**`5.`** Wait for Blue line to turn Green. _If blue line freezes when uploading, reload the page, delete partially uploaded file and try again._

\_\_[![](https://media.discordapp.net/attachments/471284424273821696/560152924030894120/firefox_GfM3gMXyI1.png?width=400&height=157)](https://cdn.discordapp.com/attachments/471284424273821696/560152924030894120/firefox_GfM3gMXyI1.png)

**`6.`** Click on the _`Refresh`_ button.

**OR**

Reload/Refresh the page.

[![](https://media.discordapp.net/attachments/471284424273821696/560153110367043587/firefox_wWN0PRg9My.png?width=400&height=81)](https://cdn.discordapp.com/attachments/471284424273821696/560153110367043587/firefox_wWN0PRg9My.png)

**`7.`** Right click on `Waterfall.jar` **OR** Click on the `...` button, Select _`Rename`_.

[![](https://media.discordapp.net/attachments/471284424273821696/560153236695154713/firefox_bHNb4uol2k.png?width=400&height=96)](https://cdn.discordapp.com/attachments/471284424273821696/560153236695154713/firefox_bHNb4uol2k.png)

**`8.`** If you only defined one server in **priorities**, find `force_default_server: false` and change `false` to `true`.

**`9.`** Find:

```text
groups:
  md_5:
  - admin
```

And replace `md_5` with your Minecraft name.

**`10.`** Find `network_compression_threshold: 256` and change it's value to `512`.

Then click on the _`Save File`_ Button!

When you see Green pop-up saying `File was successfully saved.`, click on the _`Return to File Manager`_ Button.[![](https://media.discordapp.net/attachments/471284424273821696/560155950862827521/firefox_e69pgeKav6.png?width=400&height=215)](https://cdn.discordapp.com/attachments/471284424273821696/560155950862827521/firefox_e69pgeKav6.png)**\`\`**

**`11.`** Navigate to the `plugins` folder.[![](https://media.discordapp.net/attachments/471284424273821696/560156135294894080/firefox_cqo5Hf5W0I.png?width=400&height=146)](https://cdn.discordapp.com/attachments/471284424273821696/560156135294894080/firefox_cqo5Hf5W0I.png)

**`12.`** Download the following plugins: [SlashServer](https://www.spigotmc.org/resources/slashserver.75/%20) and [BungeeGuard](https://ci.lucko.me/job/BungeeGuard/lastSuccessfulBuild/artifact/bungeeguard-proxy/target/bungeeguard-proxy.jar)

And also the following for offline mode \(Cracked\) Bungeecord server network: [AuthMe Bungee](https://www.spigotmc.org/resources/authmebungee.50219/%20), [Skins Restorer](https://www.spigotmc.org/resources/skinsrestorer.2124/%20), and [AntiBot Attack](https://www.spigotmc.org/resources/anti-bot-attack.18540/)

**`13.`** Upload downloaded plugins to your Bungeecord server.

Drag & Drop the plugin/s from downloads to the File Manager window.

**OR**

Click on the _`Upload`_ button, select downloaded plugin and click _`Open`_.

[![](https://media.discordapp.net/attachments/471284424273821696/560156795318829057/firefox_bYZMNXwNuf.png?width=400&height=96)](https://cdn.discordapp.com/attachments/471284424273821696/560156795318829057/firefox_bYZMNXwNuf.png)

**`14.`** Wait for Blue lines to get Green. _Again, if blue line freezes, reload the page and try uploading plugins again._

**`15.`** Go back to the _`Console`_.

_`Kill`_ \(Force stop\) your server then _`Start`_ it back up.

[![](https://media.discordapp.net/attachments/471284424273821696/560156935446593548/unknown.png?width=400&height=210)](https://cdn.discordapp.com/attachments/471284424273821696/560156935446593548/unknown.png)

