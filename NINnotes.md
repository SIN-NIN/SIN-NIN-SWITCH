https://github.com/Atmosphere-NX/Atmosphere
https://switchtools.sshnuke.net
https://gbatemp.net/threads/biskeydump-and-hacdiskmount-switch-emmc-decryption-real-time-mounting-tools.502434/
Folllowing his latest tweet :

https://twitter.com/sciresm/status/874660344408440832
_________________________________________________________________________________
It seems that @SciresM has seriously started working on a CFW implementation.
https://github.com/SciresM/Atmosphere-NX

A custom sysmodule for Atmosphere that allows writing to PRODINFO
 emuMMC.
 
 How To Install:

1. Move the downloaded ams_mitm.kip into the "atmosphere/kips" folder. If the folder "kips" doesn't exist, create it.
2. Create a new folder in "atmosphere" called "flags".
3. Create an empty file called "hbl_cal_read.flag" in this folder and plug your SD card back into your Switch.
4. Boot fusee_primary.bin and not the [CFW] option by Kosmos!

You're done! All homebrew applications including Incognito should now have access to PRODINFO.


Warning: Please delete this sysmodule after modifying PRODINFO for security reasons.

Source: https://github.com/benfah/Atmosphere

________________________________________________________________________________
if you are using Kosmos, after you put everything in SD and put it back, follow this step :
1.Go to Kosmos Toolbox
2.Reboot to Hekate
3.Payloads---fusee-primary.bin
4.Incognito
5.Power off
6.Boot to Hekate
7.Launch---CFW(EMUNAND)
8.Go check serial number and make sure you don't miss anything
It works on my 8.1.0 emuMMC with Kosmos 13.0.1
_________________________________________________________________________________
https://gbatemp.net/threads/l4t-ubuntu-a-fully-featured-linux-on-your-switch.537301/
LINUX
_________________________________________________________________________________
https://gbatemp.net/threads/kefir-updater.539086/
___________________________________________________
https://gbatemp.net/threads/what-to-do-in-emummc-regarding-profiles.554251/_______________________________
What is it?
Kefir Updater is a homebrew for Nintendo switch, which can update Kefir or add linked Nintendo account by one-click!​

Instruction for automatic update
1. Download KefirUpdater.nro
2. Put it into sdmc://switch/kefirupdater
3. Run Kefir Updater from hbmenu
4. Press Check updates in menu
5. Follow the prompts that appear on the screen.
​
Instruction for add linked account
1. Run Kefir Updater from hbmenu
2. Click "Add linked Account"
3. Follow the prompts that appear on the screen.​

_________________________________________________________________________________________
1. Use emunand
2. For games, use HBG
3. Use incognito RCM to play legit games online
4. Use atmosphere or Reinx (Both free options)
_________________________________________________________________________________________Hekate - CTCaer mod v4.10.1

* Hekate is a Bootloader with fw patching, recovery tools and many more features. *

* hekate or Εκάτη (in Greek) is a goddess in ancient greek religion and mythology. *
* She was one of the main deities worshiped in Athenian households as a protective goddess and one who bestowed prosperity and daily blessings on the family. *
* Here, it blesses your Nintendo Switch. *

* CFW Launching for ALL current updates (1.0.0 - 8.0.0)
* Supports booting of all current CFWs, Linux chainloading, payload tools
* Auto boot
* Modules/Plug-ins support
* Full Atmosphère support w/Exosphère booting
* Automatic RAW eMMC partial dumping
* Restore eMMC
* Working Sleep Mode on ALL firmware and downgraded ones with higher fuse count.
* And many more



[​IMG]



Before you continue:
Hekate - ipl, is a custom bootloader with extra features.
It must not be confused with CFW, hbmenu and anything else that is on the Horizon OS (Switch's OS) side.
E.g., hekate supports exFAT formatted sd cards, but if you never downloaded the exFAT update, it will not work on horizon os or any homebrew.
So, please don't report problems that happen after leaving hekate - ipl (hbmenu can't see apps, etc).



Summary:
CTCaer mod is based on naehrwert's hekate - ipl. hekate is basically a custom Nintendo Switch bootloader with many advanced features.
It supports all sd cards (except SDSC) and automatically chooses if it will dump in parts or not, based on your free space and sd card filesystem.
Supports CFW launching in the following Switch updates (all current):
1.0.0
2.X.X (all)
3.X.X (all)
4.X.X (all)
5.X.X (all)
6.X.X (all)
7.0.X (all)
8.0.0
Comes with many additional features. For example you can see your SoC's fuses, eMMC info, SD card info, etc.
_________________________________________________________________________________________________________________

collection of everything that can be used on Fusee Gelee / RCM exploits

Links
https://wiki.gbatemp.net/wiki/List_of_Switch_exploits
https://wiki.gbatemp.net/wiki/List_of_Switch_payloads

Notes

fusée gelée payload list

This page lists all the related programs and payload using the Fusée Gelée exploit.

Please, help maintaining a list of all existing Payload senders, dongles and payloads.


Payload senders (or payload injectors, or code loaders), are programs or devices used to transfer a small binary file (the payload) to the Nintendo Switch while being in Recovery mode (RCM), which allows early custom program's execution at console boot before the Switch official Operating System (Horizon OS) is loaded.
__________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________v
