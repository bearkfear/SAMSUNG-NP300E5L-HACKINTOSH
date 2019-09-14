# Samsung Hackintosh

Model: NP300E5L

summary:

Almost the entire system is fully operational.

Items that could not be configured:

- Wireless Qualcomm Atheros QCA9377

I used the olarilla ISO
You can download the ISO: http://bit.ly/2lLZomm

### SCREEN **BOOT**

clover options: 

	configs:
	
		config.plist // Desktops
		config2.plist // Notebooks

		Mac OS Expandido (Journaling)
		Mapa de Partição GUID



### POST INSTALLATION

Open ** Files ** folder and run:
	
- Master.disable
- Install clover

Options to tag in Clover:

- Install clover on ESP
- Bootloader / Does not update MBR sectors
- CloverEFI/CloverEFI 64-bits SATA
- Install Clover Preferences Panel

Open Olarila from Files folder


Você quis dizer: Na aba Olarila Folders selecionar Notebooks SkyLake
52/5000
In the Olarila Folders tab select SkyLake+ Notebooks

### AUDIO: 

**Layout IDs:** 5, 11, 13, 14, 21, 22, 28, 56, 57

Layout 11 was what worked best for me. I got the microphone to work with great quality!

To make the audio work you need to try the layout IDs that are arranged and install Kext AppleALC

You can also download it from the Github link:
http://bit.ly/2kzsl4L

After that go to the config.plist which is in the EFI / Clover folder and in ACPI apply the patch. **change HDAS to HDEF**. 	

Restart Hackintosh and it will probably be working. If it does not work change to another Layout ID and restart again.


### VIDEO:

To make sure your video is working correctly, apply the following changes:

For intel HD Graphics 520 perform the following procedures.
Open your config.plist and select the left side tab that says Graphics, and inside it check the box **IntectIntel**

Now go to the field **ig-plataform-id** and select **0x19160000** (will be on Skylake mobile)

Finally put **3** on field **Video Ports**


### TRACKPAD

To fix trackpad, run the following steps

Using the kext
ApplePS2SmartTouchPad.kext
Copy the kext to the folder EFI/Clover/Kext/other/....
Copy Trackpad.prefPane to /System/Biblioteca/PreferencesPanes.


### INTEGRATED SCREEN

Using over time realizes that the image quality that came to my integrated screen was not exactly what I expected, even with the graphics card working. I later got a Dell Full HD monitor that I tried to use HDMI and was successful, however the graphics acceleration was a bit confusing and weird. I was able to solve this problem by applying an EDID patch.

Follow the steps to fix: 

Copy the folder DisplayVendorID-X and the file Icons.plist to: `/System/Library/Displays/Contents/Resources/Overrides`

Now, run CloverConfigurator and your config.plist. Select on the ACPI tab the following

Now run cloverConfigurator and open your config.plist. From there select the ACPI tab and apply the following DSDT patch.

| 		Comment				 | Find* [HEX] | Replace [HEX] |  
|---------|---------- |----------|
| Rename H_EC to EC__ | 485F4543   | 45435F5F | 

## BATERRY

To make baterry indicator works you just need to copy my DSDT (already patched) to Clover Folder (EFI/Clover/ACPI/patched)
It's make system better too.
