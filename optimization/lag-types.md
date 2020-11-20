---
description: >-
  Source:
  https://www.spigotmc.org/threads/guide-server-optimization%E2%9A%A1.283181/
---

# Lag Types

**TPS - Server Lag** 

TPS stands for **T**icks **P**er **S**econd and is the only lag type a server owner has real control over, short of reducing features \(see "FPS" below\) or moving the server location \(see "Ping" below\). The Performance Guide above is exclusively purposed to improve TPS. 

Server performance is based on 20 ticks each second, which is why a flawless server operates at 20 TPS. Each tick causes the server to calculate tasks like the direction of mobs, crop growth, and updating player interactions with the server. A TPS below 20 means the server is unable to keep up and must skip tasks in order to keep important tasks on time. This task skipping is known as server lag or TPS loss.

`20.0` = Flawless 

`19.9-19.99` = Great, this is not cause for concern, but striving for 19.95+ would be ideal. 

`18.5-19.8` = Okay, players might occasionally complain about minor lag spikes. 

`17.0-18.4` = Poor, complaints of lag will be common. 

`<17.0` = Bad, you need to fix this...starting with the guide above.

\*\*\*\*

**Ping - Internet Lag** 

Ping \(aka latency\) reflects how long \(in milliseconds\) data takes to process and travel between the client and server host. The further a client is geographically separated from the server, the longer this transfer might take. Other common influences on ping are crowded or slow connections for the server or client. For example, streaming HD video on an already weak connection. 

As a server owner, you should host your server in a region where you prefer to have your player base or one that appeases a broader player base.

`1-90` = Great ping for Minecraft! 

`91-179` = Good connection, maybe a slight disadvantage in PvP. 

`180-299` = Poor connection, you might have occasional lag interacting with blocks/players/entities. 

`300-499` = Bad connection, gameplay will be frustrating. 

`500+` = Consider finding a server closer to you and/or testing your bandwidth.

\*\*\*\*

**FPS - Client Lag** 

**Do not** confuse TPS \(above\) with FPS \(**F**rames **P**er **S**econd\). FPS directly reflects a client's ability to process and display the information that the game/server is asking it to render. FPS is 100% client side and has nothing to do with a server's performance. The only thing a server can do to help FPS is diminish server features so weaker devices can keep up, but even that is unlikely to make a dent. 

Do not reduce features to appease PCs from the 1990's. Recommend a popular/free client mod called [Optifine](https://www.optifine.net/) for everyone, especially those with FPS issues.

`61+` = Perfect, anything over 60 FPS is considered overkill for Minecraft. Consider capping your FPS below 100 to avoid unnecessary stress on your machine. 

`41-60` = Great, you will not have any issues. 

`21-40` = Good, the game is playable with minimal graphical issues. 

`11-20` = Poor, you will be frustrated if you like moving or mining... 

`1-10` = Bad, Minecraft is too much, maybe go back to solitaire...

\*\*\*\*

\*\*\*\*[**Timing Reports**](https://youtu.be/T4J0A9l7bfQ) 

Invest time watching this informative video guide on the Timings program, created by the author of Timings. The video breaks down Timings v1\(Spigot\) and v2\(Paper\). The video length is intimidating, but any serious server owner should know how to identity their server's issues. If you prefer reading, the Timings guide is explained at length here [https://www.spigotmc.org/wiki/timings/](https://www.spigotmc.org/wiki/timings/).

