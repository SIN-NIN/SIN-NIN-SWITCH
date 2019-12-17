# SIN-NIN-SWITCH

 # Firmware Info - Collected & Compiled

    Setting up emuMMC on an ipatched unit can be trick and tiring indeed.
    Because for one, you'll have to boot Caffeine through the sysNAND thus leaving traces of CFW
    I'd suggest you to set up emuMMC but don't turn autoRCM on in any given circumstance.
    To make things simple change themes so that your emuMMC and sysNAND won't have the same one, thus making it easier to distinguish between them.

    Set up CFW and then create emuMMC with hekate.

    For anyone else who has the questions or trying to get similar up and running, you can follow these steps. Disclaimer: I'm not responsible if you don't properly read these and skip steps and ultimately brick your Switch. Please read everything 4 times before attempting and please ask if you are ever stuck on any step before attempting anything else. Its always better to be safe than sorry.

    Get a large SD card, I suggest 64gb+, to make your life easy.

    Download Minitool Partition Wizard
    
    Follow this part of this guide 
   # https://nh-server.github.io/switch-guide/user_guide/emummc/partitioning_sd/
    
    Read and then follow this guide 
   # https://switch.homebrew.guide/hacking/caffeine/forewarning
    
    Once you get up to the step "After Setup (Caffeine)", launch back into Hekate and then follow this 
   # https://nh-server.github.io/switch-guide/user_guide/emummc/making_emummc/
   , just the very top part where it says "Making the emuMMC".
    Launch CFW but emuMMC version and set your theme to your preferred color (black or white) and confirm that you are in CFW in the settings under "system", it should say Atm with ver# and "|E" next to it I believe, for emuMMC. Turn off your Switch completely and power back into your sysMMC and set your theme to the opposite, as user NoNAND suggested, so you can easily tell when you're in CFW or not.
    Lastly, download ChoidujourNX and the most recent firmware you would like to use. Set it up as explained here
   # https://switch.homebrew.guide/usingcfw/manualupgrade 
    and make sure you launch your CFW emuMMC before going into ChoudujourNX. Finish following the guide and you should be on the most up to date version on your emuMMC while maintaining 4.x.x on your sysMMC, congrats!
    ________________________________________________________________________________________________________________
    https://pubdev.switch.homebrew.guide/hacking/emummc

   # sysMMC or sysNAND

    sysMMC or sysNAND are synonymous terms which refer to your Switch's real internal storage. This holds your Switch's original firmware, save data, system settings such as WiFi, and games installed to the internal storage.




   # emuMMC or emuNAND

    emuMMC or emuNAND are synonymous terms which refer to a copy of your Switch's internal storage, which is stored on your SD card. This holds a clone of everything needed to run the Switch, including the firmware, save data, system settings, and games installed to the internal storage, as mentioned before.

    Any changes made to an emuMMC, such as WiFi settings, installed games, themes, etc. will have no effect on other emuMMCs or sysMMC.


   # File System Partition

    A partition in the context of file systems refers to a logical section of a storage device. You can think of this as a storage drive on a PC. Each partition is treated as a separate file system with it's own files and format. A storage device can have multiple partitions, allowing completely separate file systems or drives on the same storage device.



   # File-based emuMMC

    File-based emuMMCs are when the internal storage clone is stored as files on an SD card's primary partition, the same partition where you normally put files on your SD card. These emuMMCs are formatted very similarly to NAND backups created by Hekate, and it is trivial to convert Hekate NAND backups to file-based emuMMCs.

    Unfortunately at this time, file-based emuMMCs are very very slow, boot times are often upwards of ten minutes and once you do boot the OS is prohibitively slow. File-based emuMMCs should not be used at this time.


   # Partition-based emuMMC

    A partition-based emuMMC is when the internal storage clone is flashed to it's own partition on an SD card. This allows for higher performance when using emuMMC as the partition can be mounted directly without any performance lost to having to read and write across multiple files.

    Partition-based emuMMCs usually run nearly as fast as internal storage, depending on the speed of the SD card.

   # Nintendo Folder

    The Nintendo folder is the folder on your SD card where games installed to the SD card are stored. This is also where album photos and videos copied to the SD card are stored.

    For sysMMC, this folder is on the root of your SD card ( SD:/Nintendo/ ). emuMMC's use their own unique Nintendo folders to avoid cross-contamination between emuMMCs and sysMMCs. These folders are usually placed in SD:/emummc/[emummc name]/Nintendo/

    Since file-based emuMMCs are considered unusable right now, this guide will instruct you on configuring partition emuMMCs.

    This guide will use a website called emuMMC Instructor, a tool which will generate a guide tailored exactly to the setup best fit for you.

   # WARNING # 
    Your emuMMCs will share the same console-unique data as your sysMMC
    An emuMMC is not magic. It does not allow you to, for example, play pirated games online.

    If you get banned in an emuMMC, your sysMMC and your other emuMMCs will also be banned!
    To safely use an emuMMC for bannable behaviour, make sure 90DNS or PegaScape is correctly configured at all times, or that WiFi/Ethernet is completely disabled!


    If you use fusee-gelee (payloads over USB) to load CFW, jump to For fusee-gelee Users
   # https://pubdev.switch.homebrew.guide/hacking/emummc#for-fusee-gelee-users

    If you use PegaScape (Caffeine/Nereba) to load CFW, jump to For PegaScape (Caffeine/Nereba) Users
   # https://pubdev.switch.homebrew.guide/hacking/emummc#for-pegascape-caffeine-nereba-users


Extra
    You still need to acquire the folders containing firmware content somehow, some of the options are:
    Extract the UPDATE partition from an XCI image of the cartridge that contains the update you want into a folder
    These are common cartridges and firmware versions they contain:
    Puyo Puyo Tetris/ 1-2 Switch (1.0.0) - would never recommend installing this one as no Switch made with 1.0.0 actually runs it (its a slightly different 1.0.0 with exFAT that bricks you)
    Dragon Ball Xenoverse 2/ Mario plus Rabbids Kingdom Battle/Cars 3 Driven to Win (2.1.0)
    Splatoon 2/ Sonic Forces (2.3.0)
    Pokemon Tournament DX (3.0)
    Batman The Telltale Series/ Syberia 2/ The Elder Scrolls V. Skyrim (3.0.1)
    Attack on Titans 2/ Xenoblade Chronicles 2 (3.0.2)
    Bayonetta 2/ Gal Gun 2 (4.0.1)
    Kirby Star Allies (4.1.0)
    Octopath Traveler (5.0.2)
    Taiko no Tatsujin Nintendo Switch Version JPN (5.1.0)​
    Copy the SYSTEM:/Contents/registered folder from another Switch that is running the firmware version you want
    Copy the SYSTEM:/Contents folder from a Switch that has a "System update is pending" notification. This will let you pick either the currently running firmware, or the pending firmware to install.
    *cough* xbins *cough*





    Homebrew / Custom Firmware info 
    Homebrew Launcher
    https://switchbrew.github.io/nx-hbl/
    https://gbatemp.net/threads/hbl-released-for-3-0-0.496967/

    SX OS
    https://sx.xecuter.com/
    https://gbatemp.net/threads/team-xecuter-releases-sx-os-v1-4.512517/

    ReiNX
    https://github.com/Reisyukaku/ReiNX
    https://gbatemp.net/threads/official-reinx-thread.512203/

    Atmosphère
    https://github.com/Atmosphere-NX/
    https://gbatemp.net/threads/atmosphere-nx-custom-firmware-in-development-by-sciresm.496832/
