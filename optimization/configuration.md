---
description: >-
  Source:
  https://www.spigotmc.org/threads/guide-server-optimization%E2%9A%A1.283181/
---

# Configuration

{% hint style="warning" %}
Please be careful when modifying configuration on your own! Going too low or too high can break certain things on your server! I also suggest following the link above since it's more regularly updated. Also, the downloadable files may not be to your liking and was only tested on version 1.8.
{% endhint %}

Bukkit and Spigot \(and Paper\) have a number of settings that boost efficiency, reduce TPS usage, and let you avoid harsh plugins \(i.e. ClearLag\). This tutorial lists recommended settings and the pros/cons for applying them.

If you cannot find a referenced value in your file, you are on an older version and can safely skip it. If you need help identifying lag or reading timing reports, read [Lag Types](lag-types.md) tutorial too.

## BUKKIT.YML

{% file src="../.gitbook/assets/bukkit.yml" caption="Download Instead :D" %}

**spawn-limits**

Default: `monsters:70, animals:15, water-animals:15, ambient:15`

Optimized: `monsters:55, animals:12, water-animals:5, ambient:3`

Performance Impact: `Medium`

➫ Lower values result in less spawning. Be cautious setting spawns much lower or mob shortages will be noticeable. Settings later in this guide will make the reduction of spawns less of an impact to gameplay.

Note: Servers with &lt;15 players average should leave these near default to avoid mob shortages.

Note: 1.13+ servers should leave water-animals near default for fish, dolphins, etc.

**chunk-gc**

Default: `period-in-ticks:600, load-threshold:0`

Optimized: `period-in-ticks:400, load-threshold:300`

Performance Impact: `Minor-Medium`

➫ This unloads vacant chunks faster than vanilla rates. Faster unloading of chunks stops TPS consumption inside them.

**ticks-per.monster-spawns**

Default: `1`

Optimized: `2`

Performance Impact: `Medium`

➫ This dictates how often \(in ticks\) the server will attempt to spawn a monster in a legal location. Doubling the time between attempts helps TPS without impacting spawn rates.

Note: Only go 3-5 if you have severe TPS loss from the mobSpawn event.

**autosave**

Default: `6000 (usually)`

Optimized: `6000`

Performance Impact: `Situational`

➫ This enables Bukkit's world saving function and how often it runs \(in ticks\). It should be 6000 \(5 minutes\) by default, just double check it is not 0 \(disabled\). This is a gradual/queued task and is very efficient, even more so in Paper if you use that.

## SPIGOT.YML

{% file src="../.gitbook/assets/spigot.yml" caption="Download Instead :D" %}

**save-user-cache-on-stop-only**

Default: `false`

Optimized: `true`

Performance Impact: `Situational`

➫ This toggles whether the server continuously saves new user cache data \(false\) or if it delays that task until a stop/restart \(true\). This is a huge TPS savings on Spigot, only minor on Paper as it handles that task efficiently.

Note: Take regular backups to avoid data loss in the rare event of a fatal crash. Whether you set this true or false.

**max-tick-time**

Default: `tile:50, entity:50`

Optimized: `tile:1000, entity:1000`

Performance Impact: `N/A`

➫ The optimized setting disables this unstable feature. The minor TPS savings is not worth the potential damage. [Why disable max-tick-time?](https://aikar.co/2015/10/08/spigot-tick-limiter-dont-use-max-tick-time/)

**mob-spawn-range**

Default: `8`

Optimized: `6-7`

Performance Impact: `Minor`

➫ This sets the max spawning distance \(in chunks\) from a player. After limiting spawns in Bukkit, this will condense the spawning around your players to mimic the appearance of normal spawn rates. If you did not change those, leave this at default.

**entity-activation-range**

Default: `animals:32, monsters:32, misc:16`

Optimized: `animals:24, monsters:24, misc:12`

Performance Impact: `Minor`

➫ This reduces entity ticking as entities outside these ranges will be ticked less often. Lower settings _might_ create the occasional "lazy" mob. Consider leaving these closer to default unless you have issues with active entity ticking.

**merge-radius**

Default: `item:2.5, exp:3.0`

Optimized: `item:4.0, exp:6.0`

Performance Impact: `Medium-Heavy`

➫ Merging items has a huge impact on tick consumption for ground items. Higher values allow more items to be swept into piles and allow you to avoid plugins like ClearLag. Note: Merging items will lead to the occasional illusion of items disappearing as they merge together a few blocks away. A minor annoyance.

**view-distance**

Default: `10`

Optimized: `4-6`

Performance Impact: `Heavy`

➫ This is the most impactful performance setting, but noticeably impacts gameplay. This caps the chunk render distance for players. Open world servers \(like Survival\) should use 5-6, but others with low specs, huge player counts, or custom terrain might consider 4 if chunk gen causes lag. Note: Paper's async chunk loading \(and other Paper options\) might allow you to keep this in the 7-8 range. It is _that_ efficient.

\*\*\*\*

**nerf-spawner-mobs**

Default: `false`

Optimized: `true`

Performance Impact: `Medium-Heavy`

➫ When enabled, mobs from spawners will not have AI \(will not swim, attack, move\). While this is big TPS savings on servers where mob farms are popular, it also has a significant gameplay impact \(breaks many push-based farms\). A merging or farm limiter plugin might be a better solution. Note: Paper has an option to force these nerfed mobs to jump/swim nonstop. This re-allows water push farms and keeps the TPS savings. They will still not attack/chase players \(main cause of lag\).

\*\*\*\*

**item-despawn-rate**

Default: `6000 (5 minutes)`

Optimized: `less?`

Performance Impact: `Minor-Medium`

➫ The time \(in ticks\) before a ground item is removed. While the TPS savings can be significant if reduced, it also impacts gameplay on servers where returning to dropped items \(i.e. Survival\) is critical. Increasing the item merge radius \(above\) might be enough to avoid this setting change.

\*\*\*\*

**arrow-despawn-rate**

Default: `1200`

Optimized: `300`

Performance Impact: `Minor`

➫ Similar to item-despawn-rate, but for fired arrows. While some servers may want to keep arrows on the ground longer, most will have minimal complaints from faster removal. Note: Paper has settings to reduce the gameplay impact of faster removal, but keeps the TPS savings. Leave this near default if you use Paper's arrow despawn options.

## PAPER.YML

**Note:** Spigot dropped async chunk loading in 1.13. Paper brought it back and improved it! If you have chunk loading lag, maybe try Paper?

{% file src="../.gitbook/assets/paper.yml" caption="Download Instead :D" %}

**optimize-explosions**

Default: `false`

Optimized: `true`

Performance Impact: `Minor`

➫ Paper applies a custom and _far_ more efficient algorithm for explosions. It basically removes dead/pointless entities inside explosions.

\*\*\*\*

**mob-spawner-tick-rate**

Default: `1`

Optimized: `2`

Performance Impact: `Minor`

➫ This is the delay \(in ticks\) before an activated spawner attempts to spawn mobs. Doubling the rate to 2 should have no impact on spawn rates. Only go higher if you have severe load from ticking spawners. Keep below 10.

\*\*\*\*

**disable-chest-cat-detection**

Default: `false`

Optimized: `true`

Performance Impact: `Minor`

➫ By default, chests scan for a cat/ocelot on top of it when opened. While setting true eliminates a vanilla mechanic \(cats block chest opening\), do you really need this silly mechanic?

\*\*\*\*

**container-update-tick-rate**

Default: `1`

Optimized: `2-3`

Performance Impact: `Minor`

➫ This changes how often your containers/inventories are refreshed while open. Do not go higher than 3.

\*\*\*\*

**fire-physics-event-for-redstone**

Default: `true`

Optimized: `false`

Performance Impact: `Minor-Medium`

➫ This stops active redstone from firing BlockPhysicsEvent and can salvage some TPS from a cosmetic task.

**grass-spread-tick-rate**

Default: `1`

Optimized: `2-3`

Performance Impact: `Medium`

➫ The time \(in ticks\) before the server attempts to spread grass in loaded chunks. This will have minimal gameplay impact on most game types.

\*\*\*\*

**despawn-ranges**

Default: `soft: 32, hard: 128`

Optimized: `soft: 28, hard: 96`

Performance Impact: `Medium`

Soft = The distance \(in blocks\) from a player where mobs will be randomly removed. Hard = Distance where mobs will be removed instantly.

➫ Lower ranges clear unneeded mobs and allow more mobs to be spawned in areas with player traffic. This helps performance and further reduces the gameplay impact of reduced spawning \(bukkit.yml\). Note: This may _slightly_ increase the disappearance of mobs a player can see. Worth it!

\*\*\*\*

**hopper.disable-move-event**

Default: `false`

Optimized: `true`

Performance Impact: `Heavy (situational)`

➫ This will significantly reduce hopper lag by preventing InventoryMoveItemEvent being called for EVERY slot in a container. **Warning:** If you have a plugin that listens to InventoryMoveItemEvent, do not set true.

\*\*\*\*

**non-player-arrow-despawn-rate**

Default: `-1 (uses Spigot arrow-despawn-rate)`

Optimized: `60 (3 seconds)`

Performance Impact: `Minor`

➫ Similar to arrow-despawn-rate in Spigot, but targets skeleton arrows. Since players cannot pickup mob-fired arrows, this setting is only a cosmetic change.

\*\*\*\*

**creative-arrow-despawn-rate**

Default: `-1 (uses Spigot arrow-despawn-rate)`

Optimized: `60 (3 seconds)`

Performance Impact: `Minor`

➫ Like the setting above, but for player-fired arrows that cannot be picked up \(infinity bows + potion tipped arrows\).

\*\*\*\*

**keep-spawn-loaded**

Default: `false`

Optimized: `true`

Performance Impact: `Medium (situational)`

➫ This keeps your highest traffic area \(spawn\) loaded when no players are around and prevents the server from having to constantly load spawn when players /spawn or login. This is a large task for servers with custom, lavish spawn areas. Note: Be sure to set keep-spawn-loaded-range to a chunk range that makes sense for your spawn. Your spigot.yml view-distance will be used if not set.

\*\*\*\*

**prevent-moving-into-unloaded-chunks**

Default: `false`

Optimized: `true`

Performance Impact: `Medium-Heavy`

➫ Prevents players from entering an unloaded chunk \(due to lag\), which causes more TPS loss. The true setting will rubber band them back into a "safe" area. Note: If you did not pregenerate your world \(what's wrong with you?!\), this setting might be a godsend.

\*\*\*\*

**use-faster-eigencraft-redstone**

Default: `false`

Optimized: `true`

Performance Impact: `Heavy`

➫ This setting eliminates redundant redstone block updates by as much as 95% without breaking vanilla mechanics/devices \(pretty sure\). Empirical testing shows a speedup by as much as 10x! Note: If you use \(or used\) the plugin Pandawire, you might consider this option instead as Pandawire knowingly breaks a handful of vanilla redstone machines. Paper's setting does not and will attempt to fix issues if found.

\*\*\*\*

**anti-xray.enabled**

Default: `false`

Optimized: `true`

Performance Impact: `N/A`

➫ While this setting will actually cost TPS and the config options are limited, it is the most efficient anti-xray in existence! Pretty clean too. Note: Paper users with versions older than 1.12.2 should consider [Orebfuscator plugin](https://www.spigotmc.org/resources/orebfuscator.22818/) as an alternative.

## SERVER.PROPERTIES

{% file src="../.gitbook/assets/server.properties" caption="Download Instead :D" %}

**network-compression-threshold**

Default: `256`

Optimized: `Standalone(512) BungeeCord(-1)`

Impact: `Minor`

➫ This option caps the size of a packet before the server attempts to compress it. Setting it higher can save some resources at the cost of more bandwidth, setting it to -1 disables it. Note: If your server is in a Bungeecord server network on the same node as the Bungeecord server, disabling this \(-1\) will be beneficial.

{% hint style="info" %}
**BONUS:** If you own a Nukkit \(Bedrock Edition\) server, [here](https://cdn.discordapp.com/attachments/556447500848988303/579472642789212170/Optimized_Nukkit_Config.zip) is a configuration kindly provided by [MCPEHubYT](https://discord.gg/YZUtcwP). You just need to upload, click on the 3 dots beside it, then click Decompress.
{% endhint %}

