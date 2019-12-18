How To Instructions  

# https://switchtools.sshnuke.net  - 
# Pdf Guide -https://switch.homebrew.guide/usingcfw/installnsps
# Troubleshootinghttps://switch.homebrew.guide/troubleshooting.html
# https://wiki.gbatemp.net/wiki/List_of_Switch_homebrew
# https://www.diskgenius.com/
# https://emummc.homebrew.guide/?import=v1-01210000000000000
_____________________________________________________________________________________ 

# Glossary
_____________________________________________________________________________________ 

# Logo
# Search docs
# GETTING STARTED

# Before Starting
# Checking RCM
# Choosing an Exploit
# HACKING YOUR SWITCH

# fusee-gelee
# SD Card Setup (fusee-gelee)
# Safety Precautions (fusee-gelee)
# After Setup (fusee-gelee)
# Launching Atmosphere CFW
# Accessing the Homebrew Menu
# What’s Next?
# Nereba
# Caffeine
# USING CFW
# emuMMC - before hand

# Using and Configuring Hekate
# Install NSPs over USB
# Updating/Downgrading Manually
# Upgrading/Downgrading Manually With a PC
# MISC

# Comparing Custom Firmwares
# Troubleshooting
# Frequently Asked Questions
# Wii U Homebrew Guide
# Credits
# Donate
# OPTIONS

# Switch Theme (Light <–> Dark)
____________________________________________________________________________ 
https://sdsetup.com/console?switch
_____________________________________________________________________________________ 
# SD Card Setup (fusee-gelee)

At this point, you’ve verified that you can exploit fusee-gelee to run CFW. You will now prepare your SD card with the necessary software.

# Step 1: Downloading Software
This guide will walk you through the process of using the website SDSetup to prepare your SD card. This website allows you to easily select which homebrew you want and will automatically prepare a ZIP file with the correct file structure for your SD card.

Go to https://www.sdsetup.com

Select Nintendo Switch

Select the “Kosmos Defaults” package

If you think you know what you are doing, you can choose whatever CFW and options you wish. This guide will assume you at least select Atmosphere, Homebrew Menu, Hekate and Lockpick_RCM.
Select any additional homebrew packages you wish.

On desktop, you can hover over the homebrew names to get a description of what they do.
Select “Download your ZIP”

This can take a while depending on your Internet speed and latency. Be patient.
Save the resulting ZIP if your browser does not do so automatically.
_____________________________________________________________________________________
# Step 2: Preparing Software
_____________________________________________________________________________________
Extract the ZIP file from SDSetup to a folder on your PC.

The ‘sd’ folder contains all of the files that should go on your SD card. Copy all of the contents of this folder to the root of your SD card.
The ‘payloads’ folder contains all of the fusee-gelee payloads which can be launched with TegraRcmGui/Rekado/fusee-launcher/etc that you selected.
The ‘pc’ folder contains all of the PC tools that you selected.
The ‘android’ folder contains all of the Android tools you selected.
The ‘licenses’ folder contains distribution licenses for downloaded applications
The ‘readmes’ folder contains readmes for selected applications, if one was provided.
After copying the SD card files to your SD card, insert it back into your Switch.
_____________________________________________________________________________________
Important

You are technically done! At this point, you can use the Hekate payload provided in your download with your payload sender to launch into Atmosphere.

The next section includes important information about safety precautions you should take.
_____________________________________________________________________________________ 
Payload - Safety Precautions (fusee-gelee) + TegraRcmSmash
_____________________________________________________________________________________
You are now able to run Hekate on your Nintendo Switch to launch the Atmosphere (Kosmos) custom firmware. These next steps will make sure your being as careful as possible in regards to keeping your Switch from bricking and getting banned. These steps are optional but highly recommended
_____________________________________________________________________________________
Backingup and Pre-custome Kosmos or atmos install etc
_____________________________________________________________________________________
Info also Steps below Bold line
_____________________________________________________________________________________
biskeydump - Dumps all your Switch BIS keys for eMMC contents decryption, to be used as a fusee payload (upload via the normal fusee-launcher or my TegraRcmSmash.exe).
_____________________________________________________________________________________
HacDiskMount - use your BIS keys and your RawNand.bin (or the physical eMMC attached via microSD reader or using a mass storage gadget mode in u-boot/linux) to dump, restore or REAL-TIME MOUNT AND EXPLORE/MODIFY partitions from the dump file or attached physical device !
_____________________________________________________________________________________
Binaries available at https://switchtools.sshnuke.net
When appropriate, README.txt file inside the archive points to the source code location

(Yes I know these have been out for a few days, but only since today was biskeydump redistributable as a precompiled binary)
_____________________________________________________________________________________
Step 1: Backing up your NAND and BIS keys
_____________________________________________________________________________________
By backing up your NAND (the Switch’s internal memory), you will later be able to restore it in the event that anything goes wrong, essentially rewinding it back to a previous state. BIS keys are also good to backup so you can reinstall any firmware version manually should your NAND backup become corrupted or lost.

Enter RCM but this time send the Hekate payload provided in the SDSetup download to your Switch (refer to Section 1: Accessing RCM if you’ve forgotten how)

In Hekate, select ‘Tools > Backup eMMC > eMMC BOOT0 & BOOT1’

When finished, remove your SD card (you don’t need to shutdown Hekate), insert it into your PC, and copy the ‘backup’ folder to a safe location on your PC. Afterwards, delete the ‘backup’ folder on your SD card.

Insert your SD card back into your Switch

In Hekate, select ‘eMMC RAW GPP’

If your SD card has less than ~32GB free space, Hekate will provide additional instructions every few minutes about pulling files off of your SD card so it can continue.
If you weren’t required to copy files during the backup process, once again copy the ‘backup’ folder off of your SD card and put it in a safe location on your PC. Delete the ‘backup’ folder on your SD card.

Close the Backup menu, go back to the Home tab and tap ‘Reboot > RCM’

Send the “Lockpick_RCM.bin” payload provided in the SDSetup download to your Switch (if you do not have this payload, you can obtain it from GitHub.

Press the power button to shutdown once finished.

Insert your SD card into your PC.

Copy the /switch/prod.keys file to a safe location.
_____________________________________________________________________________________
Warning

It is highly recommended that you store these backups and keys in multiple locations (ex. cloud storage, external harddrive, etc) as they may be critical to restoring your Switch if anything goes wrong in the future.
_____________________________________________________________________________________
Step 2: (EU Only) Enabling GDPR Protections
_____________________________________________________________________________________
Users with EU Nintendo Network accounts have the option of enabling GDPR protections in their account settings. Doing so has been confirmed to disable lots of telemetry that can get you banned. This setting will not appear if your account is not from the EU.

Go to https://accounts.nintendo.com/setting
Login with your NNID
Under ‘Other settings’, Edit ‘Usage information’ and set it to ‘Don’t share’
Save your changes
Step 3: Blocking Updates & Telemetry with 90DNS
You can configure your WiFi settings to use a custom DNS server that blocks all connections to Nintendo servers (except the internet connection test server).

Doing this will make games unable to be played online, block eShop, game updates and system updates. If you are OK with this, follow these instructions:

Boot your Switch with or without CFW.
Open settings and go to the Internet tab
Configure a WiFi connection if you have not already done so
Select your Wifi network and pick Change Settings
Set DNS Settings to Manual
Set ‘Primary DNS’ to ‘163.172.141.219’
Set ‘Secondary DNS’ to ‘45.248.48.62’
Save and perform the connection test

_____________________________________________________________________________________
Continue to After Setup (fusee-gelee)
_____________________________________________________________________________________
After Setup (fusee-gelee)
_____________________________________________________________________________________
Congratulations! By this point you have:

Learned how to enter RCM
Learned how to launch fusee-gelee payloads through RCM
Learned how to perform NAND backups
Learned how to block as much Nintendo telemetry as possible
_____________________________________________________________________________________
_____________________________________________________________________________________
Android Payload Launcher

NXLoader

My first Android app: Launch Fusée Gelée payloads from stock Android

Heavily based on Fusée Gelée and ShofEL2. fusee.bin is bundled as a default payload

Note: Any proprietary payloads are neither tested nor supported by this software.

Apk:dDownload link https://github.com/DavidBuchanan314/NXLoader/releases
This app is currently in "Alpha" state, it's my first Android app and there is some rather disgusting code (Potentially blocking tasks on the UI thread 🤢). This will be improved soon™.


HOWTO:
Launch the app.
(Optional) go to the Config tab, and select a custom payload file.
Plug in your Switch. (On my Nexus 5, I use a micro USB OTG cable, and an A-to-C cable)
Put it into RCM mode. (Note: your switch will power on by itself when plugged in, be sure to hold VOL+).
Grant permission to the app to access the USB device.
Enjoy!
Note: The app does not need to be running in order to launch the payload. The phone can even be locked!

FAQ:
Why use this over a web-based launcher?: No internet required, and can auto-launch even if your phone is locked. Plug and play!
Can it load Linux?: soon™
Will it brick my phone/switch?: Hopefully not, but I an certainly not responsible if it does!
Does it need root?: Nope!

_____________________________________________________________________________________
1.How to backup/restore your Nintendo Switch's NAND ?
2.Use memloader v3 to mount eMMC on your computer
3.Download and open NxNandManager. Select "File" then "Open drive".
4.Select the mounted drive. You can now perform backup/restore operations.
___________________________________________________________________________________

emuNAND (partition)
Mount the SD card containing emuNAND on your computer
Open NxNandManager then open new drive (CTRL + D).
Select the drive labelled "FULL NAND".

emuNAND (files)
Mount the SD card containing emuNAND on your computer
Open NxNandManager then open new file (CTRL + O).
Open the first split file of your emuNAND (i.e "sdmmc:\emuMMC\SD00\eMMC\00" for emuMMC or "sdmmc:\sxos\emunand\full.00.bin" for SX OS's emuNAND)__
_____________________________________________________________________________________
Hold Volume when plugging Switch into computer to load RCM mode to easy install next step for APX Driver

_____________________________________________________________________________________ 
https://emummc.homebrew.guide/?import=v1-01210000000000000
https://github.com/AtlasNX/Homebrew-Guide/blob/master/hacking/emummc.rst

WARNING
_____________________________________________________________________________________
Your emuMMCs will share the same console-unique data as your sysMMC
An emuMMC is not magic. It does not allow you to, for example, play pirated games online.

If you get banned in an emuMMC, your sysMMC and your other emuMMCs will also be banned!

To safely use an emuMMC for bannable behaviour, make sure 90DNS or PegaScape is correctly configured at all times, or that WiFi/Ethernet is completely disabled!

If you use fusee-gelee (payloads over USB) to load CFW, jump to For fusee-gelee Users

If you use PegaScape (Caffeine/Nereba) to load CFW, jump to For PegaScape (Caffeine/Nereba) Users


_____________________________________________________________________________________


_____________________________________________________________________________________ 
Launching Atmosphere CFW
_____________________________________________________________________________________
To launch Atmosphere:

Enter RCM on your Switch
Push the Hekate payload to your Switch
Tap ‘Launch > CFW’
Hekate will now boot Atmosphere. Note that Atmosphere CFW does not look fundamentaly different to the normal Switch operating system. You can verify you are in Atmosphere by trying to load the Homebrew Menu (see below) or checking if the system version string in System Settings contains (AMS x.x.x).

Accessing the Homebrew Menu
Homebrew installed by placing an NRO file into the /switch folder on your SD card can be launched through the Homebrew Menu.

Access the Homebrew Menu by holding the R button while opening any game, app or the album. Note that for games, you need to hold R after choosing a user (if applicable).

What’s Next?
Check the sidebar for more information about using Custom Firmware.
_____________________________________________________________________________________
USING CFW
_____________________________________________________________________________________
Using and Configuring Hekate
_____________________________________________________________________________________

If something goes wrong or you need help, check troubleshooting.

Launching Atmosphere CFW
Atmosphere is currently the CFW with the largest feature set. It enables game modding, homebrew, backup installs, and more. To launch Atmosphere:
_____________________________________________________________________________________
1.Enter Hekate through RCM or with PegaScape.
_____________________________________________________________________________________
2.Tap ‘Launch > CFW’
Hekate will now boot Atmosphere.
_____________________________________________________________________________________

Chainloading other fusee-gelee payloads within Hekate
_____________________________________________________________________________________
Hekate itself supports chainloading other fusee-payloads so you can, for example, launch ReiNX from Hekate. This is useful for modchips or dongles when you can only configure one payload.
_____________________________________________________________________________________
1.Put any payloads you wish to chainload into the ‘/bootloader/payloads’ folder on your SD card.
2.Enter Hekate through RCM or PegaScape
3.Select ‘Payloads’
4.Select your payload of choice
_____________________________________________________________________________________
Configuring Auto-Boot with Hekate
_____________________________________________________________________________________
By configuring Auto-Boot, each time you run Hekate, instead of seeing the menu, you will be greeted with a splash screen and immediately launch into the configuration of your choice.

1. Enter Hekate through RCM or PegaScape. 
2. step 2 is removed for this process specificly (Hekate will now boot Atmosphere.)
3. Select ‘Options > Auto boot’ 
4. Select your launch configuration of choice

If you need to get back into the menu with autoboot enabled, hold VOL- immediately when the Kosmos bootlogo appears when entering Hekate.
_____________________________________________________________________________________

___________________________________________________
Enabling AutoRCM
_____________________________________________________________________________________
WARNING
_____________________________________________________________________________________
Never enable AutoRCM on an IPATCHED Switch
This section is only intended to be used on consoles with a vulnerable RCM. Enabling AutoRCM on an IPATCHED Switch will literally BRICK your Switch.
_____________________________________________________________________________________
If you cannot run payloads from RCM with fusee-gelee, DO NOT ENABLE AUTORCM.
Failure to heed this warning will result in a bricked Switch.
_____________________________________________________________________________________
AutoRCM is an optional software method of forcing your Switch to go into RCM on every launch, without the need of a jig or hardmod. Essentially, you are purposefully bricking your Switch in a controlled matter that forces it to launch into recovery. This might sound scary but is not actually dangerous, and can be undone at any time.

By doing this, you will need to use a payload sender to boot your Switch after every restart/shutdown.

1.Enter RCM on your Switch
2.Push the Hekate payload to your Switch while holding Vol- to skip autoboot and enter the menu
3.Select ‘Tools > Archive Bit - AutoRCM > Enable AutoRCM’
_____________________________________________________________________________________
You can disable AutoRCM by entering the same menu above and selecting ‘Disable AutoRCM’.

From now on, to boot into stock firmware, select ‘Launch > Stock’ in Hekate.
_____________________________________________________________________________________
Warning

Shutting down the Switch from custom firmwares other than Atmosphere after booting with AutoRCM will not turn off the Switch! You must choose ‘Power Off’ from Hekate to properly shutdown the Switch. Not doing so will leave your Switch in RCM, slowing draining battery.
_____________________________________________________________________________________
Step 1: Backing up your NAND and BIS keys
_____________________________________________________________________________________
By backing up your NAND (the Switch’s internal memory), you will later be able to restore it in the event that anything goes wrong, essentially rewinding it back to a previous state. BIS keys are also good to backup so you can reinstall any firmware version manually should your NAND backup become corrupted or lost.
_____________________________________________________________________________________
1.Enter Hekate through RCM or PegaScape.

2.In Hekate, select ‘Tools > Backup eMMC > eMMC BOOT0 & BOOT1’

3.When finished, remove your SD card (you don’t need to shutdown Hekate), insert it into your PC, and copy the ‘backup’ folder to a safe location on your PC. Afterwards, delete the ‘backup’ folder on your SD card.

4.Insert your SD card back into your Switch

5.In Hekate, select ‘eMMC RAW GPP’

    If your SD card has less than ~32GB free space, Hekate will provide additional instructions every few minutes about pulling files off of your SD card so it can continue.

6.If you weren’t required to copy files during the backup process, once again copy the ‘backup’ folder off of your SD card and put it in a safe location on your PC. Delete the ‘backup’ folder on your SD card.

7.Close the Backup menu, go back to the Home tab and tap ‘Reboot > RCM’

8.Send the “Lockpick_RCM.bin” payload provided in the SDSetup download to your Switch (if you do not have this payload, you can obtain it from GitHub.

9.Press the power button to shutdown once finished.

10.Insert your SD card into your PC.

11.Copy the /switch/prod.keys file to a safe location.
_____________________________________________________________________________________
Warning

It is highly recommended that you store these backups and keys in multiple locations (ex. cloud storage, external harddrive, etc) as they may be critical to restoring your Switch if anything goes wrong in the future.
_____________________________________________________________________________________
_____________________________________________________________________________________
