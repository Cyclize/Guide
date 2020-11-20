# General

## Use Paper instead

 Paper \(AKA. PaperSpigot or PaperClip\) is **high performance** Spigot fork with many optimizations that aims to fix gameplay, mechanics inconsistencies and **boost server performance**. 

As **Paper is a fork of Spigot**, and **Spigot is based on CraftBukkit** - Paper **supports all** your Bukkit and Spigot plugins! 

We also recommend using Paper if you are running a Vanilla Minecraft server. **Unless** you add any Gameplay changing plugin, it will still be Pure Vanilla, just **more optimized**! 

To install Paper, follow [Java Edition](../version/java-edition.md) tutorial and when you are done, come back here for more optimizations!

## Avoid using 1.13.x version on your server

 Minecraft 1.13.x server uses much more CPU and RAM resources due to the new Aquatic World Generation, compared to 1.12.x. 

If you don't really need new Aquatic World Generation, Items, Blocks, and new Mechanics, Downgrade to 1.12.2 following [Java Edition](../version/java-edition.md) tutorial and install [ViaVersion](https://www.spigotmc.org/resources/viaversion.19254/) plugin that will allow players to join your server with 1.13.x.

## Pre-Generate your World/Map

For open world servers \(i.e. Survival or Factions\), the pre-generation of a map is a huge part of the lag reduction. Take the time to do it before you even touch your server files.

1.  Get the free plugin [WorldBorder](https://www.spigotmc.org/resources/worldborder.60905/)
2.  Set a _reasonable_ border radius with `/wb set <radius>` command. You can always expand later. _\(Recommended radius up to `10 000` for ~100 player server. For small servers, you can start with `2000` and expand more if needed\)_.
3.  Command: `/wb fill`
4. Wait...this may take a number of hours depending on the map size. This will cause lag, so it's best done before a map is live.
5. Leave the border in place so players never generate new chunks \(cause of lag\).

## Plugins that can also help

 **1.** [Hibernate](https://www.spigotmc.org/resources/hibernate.4441/download?version=138511) -  This plugin reduces CPU and Memory usage by temporary disabling unnecessary Server tasks, especially when no players are online. It will not cause any additional lag on your server or change/break anything.

