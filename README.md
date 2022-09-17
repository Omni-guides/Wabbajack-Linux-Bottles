# Wabbajack-Linux-Bottles
A guide to running Wabbajack on Linux / SteamDeck.

DISCLAIMER - I am not affiliated with the Wabbajack group in any way, just a gamer trying to help other gamers. You may be able to get assistance with this guide from the #unofficial-linux-help channel of the main [Wabbajack Discord](https://discord.gg/wabbajack), but it may be best to @ me (@omni). Due to this being an unofficial guide, assistance from the wabbajack support directly on this is unlikely.

### Introduction

Accreditation to Wabbajack Discord users Chippy and Happy4510 for the groundwork on getting this running. While this guide will get Wabbajack installed and running under Linux, it is far from a straight forward process and even by the end, stability is not the best. For this reason, I would still recommend running Wabbajack in a Windows environment and copying the list over to your Linux/SteamDeck once complete. You can follow my other guide to get a modlist up and running that way - [Skyrim + Wabbajack Modlist + Linux / SteamDeck](https://github.com/Omni-guides/Skyrim-Wabbajack_Modlist-Linux)

However, if you want to go ahead, then following the below steps should allow you to run Wabbajack directly on Linux, stable or not.

The below steps were run on SteamDeck, but they will be the same or similar on other Linux OS distros. I'm using Bottles to create and manage the Wine environment that will be used to run Wabbajack, but there are plenty of other options. I just had most luck with Bottles for avoiding things like black-window and flickering once Wabbajack is running, and also things like the Steam 2FA just never appearing.

---

## Steps

Switch to Desktop Mode on your Steam Deck, and open the Discover store. Search for Bottles, and then click install.

![SteamDeck-Bottles-Discover](https://user-images.githubusercontent.com/110171124/190854078-5678a645-e5df-40fe-b380-9bc48f7e93ce.png)

Create a new Bottle by clicking 'Create a new bottle', or if you already have existing bottles, click the + in the top left corner.

![SteamDeck-Bottles-Start](https://user-images.githubusercontent.com/110171124/190854083-6f6bacd3-a795-47ba-b543-d6244d30de68.png)

Enter a name and select Application then hit Create.

![SteamDeck-Bottles-New](https://user-images.githubusercontent.com/110171124/190854085-de5cd562-1189-449b-af52-e16016bda538.png)

This will start the process of creating a new Bottle environment.

![SteamDeck-Bottles-Creating](https://user-images.githubusercontent.com/110171124/190854086-d2d4bdb9-8aa1-4450-a5b4-296097abf0a1.png)

Once the creation is complete, click anywhere on the new entry.
![SteamDeck-Bottles-created](https://user-images.githubusercontent.com/110171124/190854087-f6c23901-f24e-43ce-8cc2-fea7fe18d474.png)

Click Installers on the left, then scroll down until you see the option for Steam. Click the little download down arrow next to Steam and it will begin the installation. In some other distros, this download icon appears as a floppy disk icon.

![SteamDeck-Bottles-Install-Steam](https://user-images.githubusercontent.com/110171124/190854088-f8aaf768-6f91-451e-9c79-4e1a72aac034.png)

This will install Steam inside our bottle.

![SteamDeck-Bottles-Steam-Installing](https://user-images.githubusercontent.com/110171124/190854089-7a05a51b-24d5-48c8-b113-57aadc7f6e17.png)

Once complete, click Programs on the left, followed by the three dots next to our newly installed Steam application, and then Change Launch Options.

![SteamDeck-Bottles-Steam-LaunchOpts](https://user-images.githubusercontent.com/110171124/190854090-8988b7bb-9623-45c7-957e-7784f0f0b73f.png)

Click the pencil icon next to Command Arguments, and then delete the contents so there are no command arguments.

![SteamDeck-Bottles-Steam-EditLaunchOpts](https://user-images.githubusercontent.com/110171124/190854103-db8ac81f-2c3a-4b87-b863-57b31bff1f46.png)

Next, click Dependencies on the left. Scroll down to find dotnet462, and then click the install icon beside it.

![SteamDeck-Bottles-Steam-dotnet462](https://user-images.githubusercontent.com/110171124/190854141-8c017d8b-aed3-43d5-a115-71a7a19bd4f3.png)

This will start the process of installing dotnet462 inside our bottle. It takes *a long time*, and there will be three rounds of installation while it installs dotnet 4.6, 4.6.1, and finally 4.6.2. Each round will download the dotnet package in the background, and eventually present a screen to install

![SteamDeck-Bottles-dotnetInstall](https://user-images.githubusercontent.com/110171124/190854142-84f5b319-973e-44f1-b470-0740d57fcb9d.png)

Finally, after a long time, and all three rounds, it will finally be installed

![SteamDeck-Bottles-dotnet-complete](https://user-images.githubusercontent.com/110171124/190854143-cb252c03-e8b2-43b8-a4d6-752eae901d1f.png)

Still in the Dependencies tab, find and install vcredist2019. Thankfully this is far quicker to install

![SteamDeck-Bottles-vcredist-install](https://user-images.githubusercontent.com/110171124/190854144-74927f2c-c58a-47d9-a6ab-8657ca831f41.png)

Click the Programs tab, then click Play next to Steam.

![SteamDeck-Bottles-Program](https://user-images.githubusercontent.com/110171124/190854148-3c7be062-b508-43df-a483-c5f64dd03741.png)

This will open Steam and present the familiar Steam Login window. Log in to steam with your credentials. This will finalise the creation of the appropriate Steam folders inside our bottle. Exit steam fully.

Next we are going to link our existing Vanilla Skyrim install from the real Steam environment, to the Steam environment inside our bottle. run the following in a Konsole window:

```
ln -s /home/deck/.local/share/Steam/steamapps/common/Skyrim\ Special\ Edition ~/.var/app/com.usebottles.bottles/data/bottles/bottles/Wabbajack/drive_c/Program\ Files\ \(x86\)/Steam/steamapps/common/Skyrim\ Special\ Edition
```

Next, reopen our Steam Bottle. Another oddity is that Steam is now listed twice in Bottles. Yeah... your guess is as good as mine. I always go for the one with the capital S, but it may not matter.

![SteamDeck-Bottles-Programs-twosteam](https://user-images.githubusercontent.com/110171124/190854146-16d6b92b-f6b9-4282-a817-993a8b034ed7.png)

Once steam is opened, click Skyrim Special Edition, and click install. For reasons I have yet to work out, even though Steam will detect the game and say it is discovering files, it will still ultimately want to redownload the whole game... At least it's not doubling up on space used with this method, but a little annoying. If you work out how to avoid this, let me know ;)

If you want to install the modlist to SDCard on the deck, there's an additional step that will be needed. We need to allow Bottles to access All user files, so that it can access the SDCard location. For this, we will need to install FlatSeal. If you aren't downloading and installing the modlist to SDCard, you can ignore this step.

First, fully close Bottles, if it is still open. Flatseal can be found and installed from the Discover Store

![SteamDeck-Bottles-Flatseal_discover](https://user-images.githubusercontent.com/110171124/190854153-55dc8218-56d4-496f-9da4-869bf96b6a2a.png)

Click the SteamDeck button in the bottom left and start Flatseal

![SteamDeck-Bottles-Launch-Flatseal](https://user-images.githubusercontent.com/110171124/190854154-07c8e860-49bc-4973-9e24-123f0f590b3c.png)

Select Bottles on the left, scroll down to the FIleSystem section, and ensure that 'All user files' is enabled

![SteamDeck-Bottles-FlatSeal-Bottles](https://user-images.githubusercontent.com/110171124/190854156-b406d26d-ba12-486c-acdc-72f7c136336b.png)

Next, we need to download the latest Wabbajack application. You can find the latest release from the releases github page: https://github.com/wabbajack-tools/wabbajack/releases - download the zip file version. Once downloaded, create a new directory, and extract the Wabbajack zip file into a folder with the same name (replace the version number here with whatever the latest Wabbajack version is)

```
mkdir -p /home/deck/Games/Wabbajack/2.5.3.28
```

Or on SDCard
```
mkdir -p /run/media/mmcblk0p1/Games/Wabbajack/2.53.28
```

Then unzip our downloaded Wabbajack zip file

```
unzip /home/deck/Downloads/2.5.3.28.zip -d /home/deck/Games/Wabbajack/2.5.3.28
```

or on SDCard

```
unzip /home/deck/Downloads/2.5.3.28.zip -d /run/media/mmcblk0p1/Games/Wabbajack/2.5.3.28
```

With Skyrim downloaded, and Wabbajack extracted as above, we should be able to launch Wabbajack. In Bottles, go to the Details & Utilities tab, and click Run Executable button in the top right corner. 

![image](https://user-images.githubusercontent.com/110171124/190855572-33f835b4-1e8f-47f8-8de2-5a4e461c0062.png)

This will open a file tree window - navigate to /home/Games/Wabbajack/2.5.3.28 (or wherever you extracted Wabbajack to), find and select Wabbajack.exe, and click Run.

![SteamDeck-Bottles-run-wabbajack](https://user-images.githubusercontent.com/110171124/190854149-1b8b2764-494e-4454-b573-e2ea26868398.png)

At this stage, and with a bit of luck, Wabbajack should act almost as it would on Windows. Performance may be an issue, and sometimes the modlist images take a long time to load, or just never do. Sometimes it takes a couple of attempts to download the modlist file, etc etc - Did I say it's far from perfrect? :)

![SteamDeck-Bottles-Wabbajack-launched](https://user-images.githubusercontent.com/110171124/190854150-15343c9d-42b2-4d56-bdb4-361d8c6738d9.png)

Click the cog in the top-right and add your logins for the Nexus, etc. Now install a modlist as you noramlly would. For the installation location, you may want to create the location in konsole first, something like:

```
mkdir -p /home/deck/Games/Skyrim/Journey
```

or on SDCard, something like

```
mkdir -p /run/media/mmcblk0p1/Games/Skyrim/Journey
```

Then when you are selecting the install location inside Wabbajack, you can browse to that location

![SteamDeck-Bottles-Wabbajack-install-location](https://user-images.githubusercontent.com/110171124/190854151-2b7afc90-62c3-4593-8b1f-b3856a6bf3c5.png)

Do the same for a downloads location, or just accept the default that Wabbajack provides for you.

In my experience, Wabbajack may crash, fairly often, and you'll have to restart the application as above, and select the 'Install from disk' option, to re-start the download and install. I had to babysit the download quite a bit during testing, which is why, even after all of this, I still prefer to run Wabbajack in a Windows VM (or another Windows system) and then copy the list over. That way you can just kick it off and leave it to run.

---

Conclusion

One way, or another, when you get the modlist downloaded, you can move on to actually getting the modlist running so you can play the game. The steps to do so are outlined in my other guide - [Skyrim + Wabbajack Modlist + Linux / SteamDeck](https://github.com/Omni-guides/Skyrim-Wabbajack_Modlist-Linux). As mentioned at the top of the guide, please do drop by the #unofficial-linux-help channel of the main [Wabbajack Discord](https://discord.gg/wabbajack) if you spot an issue with the guide, something doesn't work right for you, you have a suggestion, or even if you just want a chat :)

