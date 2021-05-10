# **How to install Fallou: New Vegas under Linux in 2021**

## Summary: 
Fallout: New Vegas is fan favorite and considered one of the best role-playing-games of the decade.
Installing New Vegas may not sound like a challenge, but when we talk about stability things change. In this brief guide I will be walking you through the process of installing and modding New Vegas under you Linux machine focusing on stability, so you can finally play for more than 5 minutes. Specifically in this guide I will be using Arch Linux (btw) and Steam, but since you are a Linux user, tweaking it for your distribution shouldn’t be an issue considering that very little things will change (such as package manager, etc...). I also assume that you have basic knowledge about ordinary Linux commands. Are you ready?

## Steps:
1. [Getting the Game](#getting-the-game);
1. [Steam tweaks](#steam-tweaks);
1. [Modifications](#modifications):
   1. [4GB Patcher](#4gb-patcher);
   1. [New Vegas Stended Script](#);
   1. ...
1.[Extra Tips];


## Getting the Game
Currently there are two ways to acquire Fallout: New Vegas, they are: buying directly from Bethesda or buying  it on Steam (this last one is the recommended). I’ll continue this tutorial assuming that you bought it through Steam. If you did it directly from Bethesda or from a third party store, you will have to use **wine** in order to do some of the following procedures. As I said before, I recommend you buying it through Steam, once that wine can be a little hard to work with if you are not used to. Now, assuming that you now have a official copy of the game, it is time to download it. Wait, what do you mean you can’t? 

Hopefully Valve has been changing the game for Linux users, and now playing Window’s games is more possible than ever. In order to download the game you first must **toggle the Steam Play** function. After confirming the alteration, Steam will restart:


**First:**

![Alt text](/images/steam_play1.png "Steam Play 1")



**Then:**

![Alt text](/images/steam_play2.png "Steam Play 2")


## Steam Tweaks
Now New Vegas (and plenty of other games) can be installed. I won’t go over the basics on how to set a SteamLibrary file, verify your download and etc… it can be easily found in [Steam’s documentation](https://support.steampowered.com/kb.php), if you happen to have any doubt.


While your download gets finished, let’s talk about Proton. More specifically, about its versions. Chances are that you will use Proton to play other Steam games, so it is worth mentioning **ProtonDB**. In order to know which Proton version will better support your game, and if there will be any bug/fix needed, I strongly recommend you accessing [ProtonDB](https://www.protondb.com/). There you will find all Steam games and their rank base on how well they run.
For me the version the better suited the game was 4.11-13. If your Proton version happen to not suit New Vegas well, you can simply do it by: **right-clicking on the game > properties > compatibility > Force the use of a specific Steam Play compatibility tool:**


**Right-clicking on the game:**

![Alt text](/images/proton_version1.png "Changing the Proton version for a specific game")



**Compatibility tab:**

![Alt text](/images/proton_version2.png "Choosing a Proton version")


Now you should open the launcher for the first time. The game will automatically detect your hardware and adjust the settings accordingly. Make sure you have all Steam dependencies (and make sure you have all of your GPU’s dependencies as well). Configure all that you want to now! I would encourage you to check the resolution configuration, old game old parameters, is probably going to be wrong. Hit play, get back.


## Modifications
From now on this tutorial will be based on the following video: https://www.youtube.com/watch?v=Cypqage_Pdk

Most guides will probably tell you to follow by using wine. We won’t be using it, there’s a sneaky way around. If you know a thing or two about Steam, you are aware that it only cares about the name of the .exe file, regardless of what it is. You probably know where I’m going now… Instead of executing the patches using wine, we’ll do it by using Steam. That’s the trick.
However, if you insist in going on with Wine, I would recommend controlling it within a container or with a specific user. 

Vanilla wine should seal the deal:
`sudo pacman -S wine`

**Disclaimer:** some operations when executed by wine may display errors. If that’s the case, just re-execute it and you should be fine. If even by re-doing the operation the goals weren’t reached, then you’ll have to customize you wine installation.

## 4GB Patcher
What it is and why to use it: https://www.nexusmods.com/newvegas/mods/62552?tab=description

Download the file (the version that does not require the VC++ redist) from the link above (you will need a nexus account). Please, note that the file extension is in .7z. With that being said, you will need a software to extract it. I personally use **p7zip**.


`sudo pacman -S p7zip` # Installing the extraction software

Navigate to the directory that you’ve just downloaded the file and execute:

`7z e 4GB\ Patcher-62552-1-5-1618787921.7z` # Extracting the patcher

Now you should have the **FNVpatch.exe** file extracted. Lets move it into our FNV installation directory (note that this isn’t a normal mod, it is a patcher! Therefore don’t put it into your DATA folder):

`mv FNVpatch.exe /SteamLibrary/steamapps/common/Fallout\ New\ Vegas/` # Move it to the same place where your launcher is.

Now for the sneaky part: rename your **FalloutNVLauncher.exe** to **FalloutNVLauncher.exe.back**, and rename **FNVpatch.exe** to **FalloutNVLauncher.exe**. Go back to Steam and execute Fallout: New Vegas. Your should see the following prompt pop up:

