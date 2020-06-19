# Cardinal-Anticheat 1.8-1.12

<img src="http://cac.dodo1213.de/img/banner.png">

<div align="center">
    <a href="https://link.lukasl.dev/cacdiscord">
        <img
            height="30" src="https://img.shields.io/discord/647922123192533022.svg?logo=discord&style=for-the-badge"
        />
    </a>
</div>

## Disclaimer

Cardinal-Anticheat is a **free** [**Spigot**](https://github.com/SpigotMC) anticheat which blocks most of the known cheats out there. Keep in mind, that Cardinal-Anticheat is still in beta, false postives may occurre... 

Cardinal-Anticheat also contains a custom build-in replay system which is quite usable to check whether a player was cheating or not. The output-file is a .zip file ~ 5MB depending on the amount of worlds used and their size.

[**Download**](#download)

## Commands

```
cac flag    - Shows the flags/alerts
cac ban     - Bans a player permanently
cac unban   - Unbans a player
cac info    - Tells you whether a player is banned or not
cac iptable - Adds the ip-address of a player to the firewall rule and prevents any further communication
cac replay  - Watch a replay which has been recorded before
cac report  - A custom report system only for stuffs in which each flag will be a 'report' which will be stored
cac reset   - Resets the violations of a player
cac reboot  - Restarts the plugin
cac reload  - Reloads configurations
cac export  - Export the current settings into a single file
cac import  - Import a setting from a file
```

## Permission

```
CAC.command       - Allows you to use most of the commands
CAC.tabcomplete   - Allows you to use tab-completion
CAC.flag          - Allows you to toggle /cac flag
CAC.manage.ban    - Allows you to ban players
CAC.manage.unban  - Allows you to unban players
CAC.manage.report - Allows you to edit reports
CAC.addon         - Allows you to manage addons
CAC.proxy         - Allows you to you even though your ip might be a proxy
CAC.config.import - Allows you to import settings
CAC.config.export - Allows you to export settings
CAC.replay.watch  - Allows you to watch a replay
CAC.replay.gui    - Allows you to see a list of all replays ingame
```

## Important

If you're using multiversion to allow players of any versions to join false positives will occurre...
In case your server is on 1.8 and players with versions higher than that are able to you disable following detections:
+ yMotion
+ Speed Type A

After testing different legit clients, I came to the conclusion that PvPLounge is not considered as legit and will be detected for:
+ Blockhit
+ NoSlowdown

These violations aren't the fault of Cardinal-Anticheat because no other modification was detected for Blockhit or NoSlowdown. **The only legit thing out there is still vanilla!**
However, in case you want PvPLounge users allow to playing on your server, there's an addon available on my discord (see below) in #addons

<div id="download"
## Installation

First navigate to the [**release**](https://github.com/Clientastisch/Cardinal-Anticheat/releases) tab and download the newest version available. After the download move the `CAC.jar` into the `plugins` folder. The `CACApi.jar` **is only for development purpose** and should not be moved inside the `plugins` folder too.
 />

## Addons ([**documentation**](http://cac.dodo1213.de/doc/allclasses-noframe.html))

1. First things first, download the `CACApi.jar` of the newest [**release**](https://github.com/Clientastisch/Cardinal-Anticheat/releases)
2. Add `CACApi.jar` as you dependency. It's **only** a placeholder, nothing you should move inside your `plugins` folder
3. Instead of `extends JavaPlugin` you have to `implement Addon` which requires two methods:

```java
import me.clientastisch.extension.Extension;
import me.clientastisch.extension.impl.Addon;

public class Core implements Addon {

    @Override
    public void onEnable() throws Exception {
    
    }

    @Override
    public void onDisable() throws Exception {

    }
}
```

4. Unlike spigot, a file called `addon.json` must be created like following:

```json
{
  "name": "MyAwesomeAddon",
  "author": "Me",
  "main": "my.path.to.core",
  "version": "v1.0"
}
```

5. Export your addon to `plugins//CAC//addons`
6. Reload your server or use `/cac addon load <addon>` and you're done!

## Power of addons

Addons are supported for every [**Spigot**](https://github.com/SpigotMC) version on which Cardinal-Anticheat is supported too. This gives you the ability to create multiversion extensions. Futhermore, you get access to a [**bunch of events**](http://cac.dodo1213.de/doc/allclasses-noframe.html) which are either packet or spigot based and access to some player-data collected by the anticheat which gives you some additional information which spigot doesn't provide on its own.

### Bugs & False positives

If any bugs or false positives occurre **report** them [**here**](https://github.com/Clientastisch/Cardinal-Anticheat/issues/new/choose). <br>
Otherwise I'll probably never notice them
