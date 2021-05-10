# **How to install Fallou: New Vegas under Linux in 2021**

## Summary: 
Fallout: New Vegas is fan favorite and considered one of the best role-playing-games of the decade.
Installing New Vegas may not sound like a challenge, but when we talk about stability things change. In this brief guide I will be walking you through the process of installing and modding New Vegas under you Linux machine focusing on stability, so you can finally play for more than 5 minutes. Specifically in this guide I will be using Arch Linux (btw) and Steam, but since you are a Linux user, tweaking it for your distribution shouldn’t be an issue considering that very little things will change (such as package manager, etc...). I also assume that you have basic knowledge about ordinary Linux commands. Are you ready?

## Index:
1. [Getting the Game](#getting-the-game);
1. [Steam tweaks](#steam-tweaks);
1. [Modifications](#modifications):
   1. [4GB Patcher](#4gb-patcher);
   1. [New Vegas Script Extender (NVSE)](#new-vegas-script-extender);
   1. [New Vegas Anti Chrash](#new-vegas-anti-crash);
   1. [New Vegas Stutter Remover](#new-vegas-stutter-remover);
   1. [.ini Files](#ini-files).


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

Now you should have the **FNVpatch.exe** file extracted. Lets move it into our FNV installation directory (note that this isn’t a normal mod, it is a patcher! Therefore don’t put it into your Data folder):

`mv FNVpatch.exe /SteamLibrary/steamapps/common/Fallout\ New\ Vegas/` # Move it to the same place where your launcher is.

Now for the sneaky part: rename your **FalloutNVLauncher.exe** to **FalloutNVLauncher.exe.back**, and rename **FNVpatch.exe** to **FalloutNVLauncher.exe**. Go back to Steam and execute Fallout: New Vegas. Your should see the following prompt pop up:

![Alt text](/images/4gb_patch.png "Patching the game.")

Push any key to continue. Now you game is patched.


## New Vegas Script Extender
What it is and why to use it: http://nvse.silverlock.org/

Download the stable version using the link above. Again, go to the directory that you downloaded the file and extract it with p7zip (if it asks you about replacing any archive, just hit **N**):

`7z e nvse_5_1_beta4.7z` # Extracting the files

Now copy the **.dll** and **.exe** files to your Fallout NV directory.

`find . -name "*.dll" && find . -name "*.exe"` # This are all the files that we must copy

`cp nvse_steam_loader.dll nvse_editor_1_4.dll nvse_1_4.dll nvse_1_4ng.dll nvse_loader.exe /SteamLibrary/steamapps/common/Fallout\ New\ Vegas/` # Copying all the needed files

Go to your FNV directory and rename the file **FalloutNVLauncher.exe** back to **FNVpatch.exe** and **nvse_loader.exe** to **FalloutNVLauncher.exe**. To make sure it has worked, hit play in Steam, go into the game console and type: `GetNVSEVersion`. If you received a reply informing the version of your NVSE, than it worked:

![Alt text](/images/nvse_version.png "NVSE version.")


Now go back to your FNV directory and open de Data folder. Execute the following commands in the order presented:

`mkdir NVSE` # Creating a folder called 'NVSE'

`cd NVSE` # Going within the recently created folder

`touch NVSE_Config.ini && echo "[Memory]" > NVSE_Config.ini && echo "DefaultHeapInitialAllocMB=400" >> NVSE_Config.ini` # Creating the .ini file

## New Vegas Anti Crash
Once again, what it is, why to use it: https://www.nexusmods.com/newvegas/mods/53635/?tab=files

Download the file through the link above an extract it:
`7z e NVAC\ -\ New\ Vegas\ Anti\ Crash-53635-7-5-1-0.zip` # Extracting NVAC

Got to your FNV folder > Data > NVSE and them:
`mkdir Plugins` # Creating the 'Plugins' folder

Finally, drop the extracted **nvac.dll** file into youe recently created folder. You're done with this one.


## New Vegas Stutter Remover
We're almost done, I swear! NVSR: https://www.nexusmods.com/newvegas/mods/34832

You know how it goes, download from the link above and then extract the files:
`7z e NVSR_4-1-36-34832-4-1-36.zip` # Extracting NVSR

Now let's move the **sr_New_Vegas_Stutter_Remover.dll** file into our Plugin's folder:
`mv sr_New_Vegas_Stutter_Remover.dll /SteamLibrary/steamapps/common/Fallout\ New\ Vegas/Data/NVSE/Plugins/`

Done!


## INI Files
