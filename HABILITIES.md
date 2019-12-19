Muh Switch Keys
So you want to decrypt switch content ? Well, the good news is that all the tools required to do that are written up! The great news is, since this is crypto we're talking about, you'll have to find the keys. Yourself. Like it's easter.

So here you can find a template of the $HOME/.switch/prod.keys file that hactool uses to decrypt content. It contains all the SHA256 and location of the keys and seeds, so you can find them yourselves.

Note that all the seeds (the keys that end with _source) are used along with the master_key_## to derive an actual key. If you have somehow obtained the key without the seed, you can rename xxx_source to xxx_## (where ## is the master key number) and put your key there.

How the heck do I obtain dem keys ?
This section will not work on 7.0.0. If you want to dump the keys, downgrade to 6.2.0. Or find an exploit. Who knows, maybe you're actually really good at Reverse Engineering and you never knew?

A lot changed in the couple last days. We now have the ability to do Fun Stuff. Here's what you need:

A dump of your BOOT0 partition.
Your console's SBK/TSEC key.
If you're on 6.2.0+, the tsec_root_key.
Your decrypted package1 file.
Your package2 file.
All of those are obtainable via hekate.

First, you'll want to find the keyblob_key_source, keyblob_mac_key_source and master_key_source. With those, hactool's keygen option will gain the ability to derive the master_key. On 6.1.0 and under, you'll also get the package1_key, with which you can decrypt the encrypted parts of package1 (RTFM on how to do that). On 6.2.0+, package1 can only be decrypted from a real console, so use hekate to dump it. Then, you'll want to find the package2_key_source. And finally, everything else.

Here's a quick reminder of the versions:

master_key_00: 1.0.0-2.3.0
master_key_01: 3.0.0
master_key_02: 3.0.1-3.0.2
master_key_03: 4.0.0-4.1.0
master_key_04: 5.0.0-5.1.0
master_key_05: 6.0.0-6.1.0
master_key_06: 6.2.0
master_key_07: 7.0.0-7.0.1
Good luck with The Hunt. And remember: We believe in your habilities.

FAQ
Q: The hashes are wrong !

A: You are computing it wrong. Hex is only a representation. Binary is truth. Because I'm such a nice guy, I'll tell you this :

SHA256(00FF00FF) = 7a7bf454c5f3cb1b9d9a20f81417f98d976fe3b3dd52c1b9968f02e89e7e8a2f

Q: Is the order important?

A: Yes, if you don't want to use leaked keys, they are! And you don't want to use leaked keys, do you? Tsktsk.

Here's why the order is important:

keyblob_key_source, keyblob_mac_key_source and master_key_source gives package1_key
package1_key is used to decrypt package1, which contains Secure_Monitor.bin, in which you'll find some key sources and package2_key_source.
package2_key_source and master_key are then used to decrypt package2, which contains everything else.
Q: How do I get my console's SBK/TSEC ?

A: Take a look at fusee-launcher and biskeydump. Those two tools should give you what you want.

Q: How do I get my hands on the package1/package2 ?

A: Those two files are both located in the 0100000000000819.bin archive, which you can easily dump with pegaswitch. Look at the dumpArchive.js script.

If pegaswitch isn't an option for you, you can also get them from a NAND backup. package1 is located at a fixed offset in BOOT0, and package2 is at a fixed offset in BCPKG2-1-Normal-Main. Check the wiki out. You can write a script to extract those files. It's easy, I swear!

Q: RTFM ?

A: Read The Fucking Manual. ./hactool --help will tell you everything else you need.

Q: Can you just cut the chase and give me the keys ?

A: No. I enjoy watching you suffer.

 test.ini
; CONSOLE UNIQUE
; Dumpable using Fusee-Gelee and biskeydump.
; Secure boot key of the console associated with given BOOT0. Useful to
; derive master_key and package1_key.
secure_boot_key                           = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; CONSOLE UNIQUE
; Dumpable using Fusee-Gelee and biskeydump.
; TSEC key of the console associated with given BOOT0. Useful to
; derive master_key and package1_key.
tsec_key                                  = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Can be dumped from hekate on 6.2.0. Requires private exploit to dump on 7.0.0+
; TSEC root key used to derive various keys on 6.2.0+.
; SHA256(tsec_root_key_00)                = 032ADF0A6BE7DD7C11A4FA5CD64A1575E469B9DA5D8BD56A12D0FBC0EB84E8E7 
; SHA256(tsec_root_key_01)                = 44BF5DAA1CDD841F68DBB14E8ADFEB49EB5E5A2089B7CE7276F8011DA42CA517
tsec_root_key_##                          = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in package1. Useful to guarantee that the keyblob_key_sources are correct.
; SHA256(keyblob_mac_key_source)          = B24BD293259DBC7AC5D63F88E60C59792498E6FC5443402C7FFE87EE8B61A3F0
keyblob_mac_key_source                    = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in package1. Used to derive the keyblob_key, which is then used to derive master_key and package1_key.
; Don't forget to replace ## with the appropriate number!
; Does not exist for key 06 onward!
; SHA256(keyblob_key_source_00)           = 8A06FE274AC491436791FDB388BCDD3AB9943BD4DEF8094418CDAC150FD73786
; SHA256(keyblob_key_source_01)           = 2D5CAEB2521FEF70B47E17D6D0F11F8CE2C1E442A979AD8035832C4E9FBCCC4B
; SHA256(keyblob_key_source_02)           = 61C5005E713BAE780641683AF43E5F5C0E03671117F702F401282847D2FC6064
; SHA256(keyblob_key_source_03)           = 8E9795928E1C4428E1B78F0BE724D7294D6934689C11B190943923B9D5B85903
; SHA256(keyblob_key_source_04)           = 95FA33AF95AFF9D9B61D164655B32710ED8D615D46C7D6CC3CC70481B686B402
; SHA256(keyblob_key_source_05)           = 3F5BE7B3C8B1ABD8C10B4B703D44766BA08730562C172A4FE0D6B866B3E2DB3E
keyblob_key_source_##                     = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; 6.2.0+: Found in the SecureMonitor.
; Used to derive master_key.
; The first such key is 06. It's basically the keyblob replacement.
; SHA256(master_kek_source_06)            = 372492E15924F5C59FB05661996F38D5AA6AFABB3D707D366F3111BCF4D7B80F
; SHA256(master_kek_source_07)            = B875AC10B014709FD30DE2C6543ED989E87A9C838AFE8815E22D082AB152757D
master_kek_source_##                      = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; 6.2.0+: Found in the SecureMonitor.
; 6.1.0 and under: Found in package1.
; Used to derive master_key. 
; SHA256(master_key_source)               = 7944862A3A5C31C6720595EFD302245ABD1B54CCDCF33000557681E65C5664A4
master_key_source                         = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Obtainable with Secure Monitor code execution.
; 6.2.0+: Derivable from master_kek_source, tsec_root_key and master_key_source.
; 6.1.0 and under: Derivable from keyblob and master_key_source.
;
; All the other keys are derived with this one.
; Don't forget to replace ## with the appropriate number!
; SHA256(master_key_00)                   = 0EE359BE3C864BB0782E1D70A718A0342C551EED28C369754F9C4F691BECF7CA
; SHA256(master_key_01)                   = 4FE707B7E4ABDAF727C894AAF13B1351BFE2AC90D875F73B2E20FA94B9CC661E
; SHA256(master_key_02)                   = 79277C0237A2252EC3DFAC1F7C359C2B3D121E9DB15BB9AB4C2B4408D2F3AE09
; SHA256(master_key_03)                   = 4F36C565D13325F65EE134073C6A578FFCB0008E02D69400836844EAB7432754
; SHA256(master_key_04)                   = 75FF1D95D26113550EE6FCC20ACB58E97EDEB3A2FF52543ED5AEC63BDCC3DA50
; SHA256(master_key_05)                   = EBE2BCD6704673EC0F88A187BB2AD9F1CC82B718C389425941BDC194DC46B0DD
; SHA256(master_key_06)                   = 9497E6779F5D840F2BBA1DE4E95BA1D6F21EFC94717D5AE5CA37D7EC5BD37A19
; SHA256(master_key_07)                   = 4EC96B8CB01B8DCE382149443430B2B6EBCB2983348AFA04A25E53609DABEDF6
master_key_##                             = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; On 6.1.0 and under: derivable from a keyblob
; On 6.2.0+: unobtainium. Kept deep inside the encrypted TSEC payload.
;
; Allows decrypting package1, which contains the bootloader, warmboot.bin and Secure_Monitor.
; Don't forget to replace ## with the appropriate number!
; SHA256(package1_key_00)                 = 4543CD1B7CAD7EE0466A3DE2086A0EF923805DCEA6C741541CDDB14F54F97B40
; SHA256(package1_key_01)                 = 984F1916834540FF3037D65133F374BD9E715DC3B162AAC77C8387F9B22CF909
; SHA256(package1_key_02)                 = 9E7510E4141AD89D0FB697E817326D3C80F96156DCE7B6903049AC033E95F612
; SHA256(package1_key_03)                 = E65C383CDF526DFFAA77682868EBFA9535EE60D8075C961BBC1EDE5FBF7E3C5F
; SHA256(package1_key_04)                 = 28AE73D6AE8F7206FCA549E27097714E599DF1208E57099416FF429B71370162
; SHA256(package1_key_05)                 = 70AD5C51C9BFFA9DB066BD26AB4B5654235E610BEC8CD76F80FEAF6E29FFF684
package1_key_##                           = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in Secure_Monitor .rodata.
; Allows decrypting package2, which contains the kernel and builtins.
; SHA256(package2_key_source)             = 21E2DF100FC9E094DB51B47B9B1D6E94ED379DB8B547955BEF8FE08D8DD35603
package2_key_source                       = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in Secure_Monitor .rodata.
; SHA256(aes_kek_generation_source)       = FC02B9D37B42D7A1452E71444F1F700311D1132E301A83B16062E72A78175085
aes_kek_generation_source                 = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in spl .rodata.
; SHA256(aes_key_generation_source)       = FBD10056999EDC7ACDB96098E47E2C3606230270D23281E671F0F389FC5BC585
aes_key_generation_source                 = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in Secure_Monitor .rodata.
; SHA256(titlekek_source)                 = C48B619827986C7F4E3081D59DB2B460C84312650E9A8E6B458E53E8CBCA4E87
titlekek_source                           = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in FS .rodata.
; SHA256(key_area_key_application_source) = 04AD66143C726B2A139FB6B21128B46F56C553B2B3887110304298D8D0092D9E
key_area_key_application_source           = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .rodata.
; SHA256(key_area_key_ocean_source)       = FD434000C8FF2B26F8E9A9D2D2C12F6BE5773CBB9DC86300E1BD99F8EA33A417
key_area_key_ocean_source                 = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .rodata.
; SHA256(key_area_key_system_source)      = 1F17B1FD51AD1C2379B58F152CA4912EC2106441E51722F38700D5937A1162F7
key_area_key_system_source                = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .rodata.
; SHA256(header_kek_source)               = 1888CAED5551B3EDE01499E87CE0D86827F80820EFB275921055AA4E2ABDFFC2
header_kek_source                         = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .data.
; SHA256(header_key_source)               = 8F783E46852DF6BE0BA4E19273C4ADBAEE16380043E1B8C418C4089A8BD64AA6
header_key_source                         = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

; Found in FS .rodata. 1.0.0 FS didn't have this, as it didn't support sd cards.
; SHA256(sd_card_kek_source)              = 6B2ED877C2C52334AC51E59ABFA7EC457F4A7D01E46291E9F2EAA45F011D24B7
sd_card_kek_source                        = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .rodata. 1.0.0 FS didn't have this, as it didn't support sd cards.
; SHA256(sd_card_save_key_source)         = D482743563D3EA5DCDC3B74E97C9AC8A342164FA041A1DC80F17F6D31E4BC01C
sd_card_save_key_source                   = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
; Found in FS .rodata. 1.0.0 FS didn't have this, as it didn't support sd cards.
; SHA256(sd_card_nca_key_source)          = 2E751CECF7D93A2B957BD5FFCB082FD038CC2853219DD3092C6DAB9838F5A7CC
sd_card_nca_key_source                    = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
@pplatoon
pplatoon commented on Mar 23, 2018
Oh my God ! A treasure hidden in the grave ... are there traps? or is it just to see how we play to be smart? haha you are very naughty ...

@geek85
geek85 commented on Apr 5, 2018
SHA256(master_key_03) = 4f36c565d13325f65ee134073c6a578ffcb0008e02d69400836844eab7432754

@rajkosto
rajkosto commented on Apr 26, 2018 • 
You mention that the secure_boot_key is dumpable using github.com/ktemkin/Atmosphere/tree/poc_nvidia however as of now (commit a18c962d699c98c6d41d98f343e4efe2f78bcc52), the SBK it prints out on the display is byte-reversed in u32 units compared to the one you need to give to hactool (hactool expects bytes, not 4 little endian u32s, so if you feed it the dump directly as output on the screen by poc_nvidia fusee.bin it will just complain about the MAC not being correct, and not generate any keys).

tl;dr if you used the default fusee.bin to dump SBK, split the hex dump into 4 uint32s, byte-reverse each one, and then put that into your keys file, or just use github.com/rajkosto/biskeydump to dump both SBK and tsec (which it prints in the format hactool expects)

@ghost
ghost commented on May 1, 2018
How about the eticket_rsa_kek_source?
That's necessary for getting your personalized titlekeys.

@Whovian9369
Whovian9369 commented on May 2, 2018
SHA256(eticket_rsa_kek_source) = b71db271dc338df380aa2c4335ef8873b1afd408e80b3582d8719fc81c5e511c
SHA256(eticket_rsa_kekek_source) = e8965a187d30e57869f562d04383c996de487bba5761363d2d4d32391866a85c
SHA256(rsa_oaep_kek_generation_source) = e1ddaf657ab14b63e8a92e5899b84ef8c045bbb085f96099af9aee90823bfd9a
