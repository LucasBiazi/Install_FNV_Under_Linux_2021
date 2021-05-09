# **How to install Fallou: New Vegas under Linux in 2021**

## Summary: 
Fallout: New Vegas is fan favorite and considered one of the best role-playing-games of the decade.
Installing New Vegas may not sound like a challenge, but when we talk about stability things change. In this brief guide I will be walking you through the process of installing and modding New Vegas under you Linux machine focusing on stability, so you can finally play for more than 5 minutes. Specifically in this guide I will be using Arch Linux (btw) and Steam, but since you are a Linux user, tweaking it for your distribution shouldn’t be an issue considering that very little things will change (such as package manager, etc...). I also assume that you have basic knowledge about ordinary Linux commands. Are you ready?

## Steps:
1. [Getting the Game](#getting-the-game);
1. [Steam tweaks];
1. [Modifications]:
   1. [4GB Patcher];
   1. [New Vegas Stended Script];
   1. ...
1.[Extra Tips];


## Getting the Game
Currently there are two ways to acquire Fallout: New Vegas, they are: buying directly from Bethesda or buying  it on Steam (this last one is the recommended). I’ll continue this tutorial assuming that you bought it through Steam. If you did it directly from Bethesda or from a third party store, you will have to use **wine** in order to do some of the following procedures. As I said before, I recommend you buying it through Steam, once that wine can be a little hard to work with if you are not used to. Now, assuming that you now have a official copy of the game, it is time to download it. Wait, what do you mean you can’t? 

Hopefully Valve has been changing the game for Linux users, and now playing Window’s games is more possible than ever. In order to download the game you first must **toggle the Steam Play** function. After confirming the alteration, Steam will restart:


**First:**

![Alt text](/images/steam_play1.png "Steam Play 1")



**Then:**

![Alt text](/images/steam_play2.png "Steam Play 2")

Now New Vegas (and plenty of other games) can be installed. I won’t go over the basics on how to set a SteamLibrary file, verify your download and etc… it can be easily found in [Steam’s documentation](https://support.steampowered.com/kb.php), if you happen to have any doubt.


While your download gets finished, let’s talk about Proton. More specifically, about its versions. Chances are that you will use Proton to play other Steam games, so it is worth mentioning **ProtonDB**. In order to know which Proton version will better support your game, and if there will be any bug/fix needed, I strongly recommend you accessing [ProtonDB](https://www.protondb.com/). There you will find all Steam games and their rank base on how well they run.
For me the version the better suited the game was 4.11-13. If your Proton version happen to not suit New Vegas well, you can simply change it:
