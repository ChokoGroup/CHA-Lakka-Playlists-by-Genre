### CHA - Lakka - Playlists by Genre

##
This pack has two folders:
- CHA_LAKKA (with playlists by genre and thumbnails - still missing "Shooter" and "Sport" games)
- CHA_LAKKA_EMPTY (with a script to create RetroArch Customized Playlists, optionally with thumbnails)

This playlists are designed to work with the (not so) new "Multi OS builds" in https://github.com/ChokoGroup/CHA-Multi-OS-Boot


### Goal
We can run Lakka in our Capcom Home Arcades but without playlists and thumbnails, a very important part of the experience is missing.
The primary goal is to create a set of playlists with thumbnails of games sorted by genre.

A script was made to easily create playlists from a set of ROMs (*.zip format) in several folders and subfolders and also get the thumbnails from the assets previosly downloaded from https://www.progettosnaps.net
They are meant to be used in Lakka, running in Capcom Home Arcade.
They can be loaded from USB or copied to internal memory or SD card, and should work with other ReatroArch installations with little (or even no) changes.


### How to use the existing playlists - Loading from USB
1. Make sure your drive is in a supported format, like FAT32 or EXT4.

2. Make sure the label of your pendrive is "CHOKO_DISK". 
In Windows, you can change the label of your pendrive by right-clicking in the drive letter and select "Rename".

3. Copy the content of the folder CHOKO_DISK to the root of your CHOKO_DISK pendrive.

4. You need to put the ROMs in *.zip format, in folders inside 'CHA_LAKKA/roms'. It isn't easy to put all the right roms in the right place, but there are lists inside the folder "roms".

5. If you don't want the "double view" of snapshot and title screen, go into all subfolders under 'thumbnails' and replace the folders named 'Named_Titles' with those named 'Named_Titles_2'.

6. Now insert the pendrive in the USB EXT port of the CHA and boot into Lakka. Enjoy!


### How to use the existing playlists - Install in SD card
1. Make sure your CHA is running Lakka and connected to your home WiFi.

2. From your PC, navigate directly to Lakka's Samba share by entering "\\lakka\" in the file browser. If you cannot reach the Lakka system by name, it may be possible to reach it by IP.

3. Copy the content of the folder "CHA_LAKKA/assets" to the folder "\\lakka\Assets".

4. Copy the content of the folder "CHA_LAKKA/playlists" to the folder "\\lakka\Playlists".

5. Copy the content of the folder "CHA_LAKKA/roms" to the folder "\\lakka\roms".

6. Copy the content of the folder "CHA_LAKKA/thumbnails" to the folder "\\lakka\thumbnails".

7. If you don't want the "double view" of snapshot and title screen, go into all subfolders under 'thumbnails' and replace the folders named 'Named_Titles' with those named 'Named_Titles_2'.

8. Reboot the CHA and enjoy!


### What is inside CHA_LAKKA_EMPTY?
A script named 'create_RA_playlists.sh', meant to run under linux. It was tested in Ubuntu running under Windows 10.

1. Open that file and change the first lines to match the path where you have the boxart (or flyers), screenshots and titles. Or let any of them be empty to skip creating the correspondig thumbnails, like this:
```
BOXARTS=""
SNAPS=""
TITLES=""
```
If the three options are empty, only the playlists are created, not the thumbnails folders.

2. There is a variable ```BASEPATH="/storage/roms"``` that should not be changed for use in Lakka. It's the path for the parent folder of all ROMs subfolders.

3. DEFAULTCOREPATH and DEFAULTCORENAME are used to set a default core to the playlists. Uncoment or edit the lines to set as you want them.

4. The file 'games_names.txt' is generated by MAME with the command "mame.exe -listfull" and can be updated the same way.

5. Put some ROMS in folders inside the 'roms' folder. They can be organized in subfolders, and a playlist will be created for each (sub) folder.
For example:
```
roms/*.zip     (will be ignored)
roms/Fight/*.zip     (will create a playlist named "Fight")
roms/Fight/Versus/*.zip   (will create a playlist named "Fight - Versus")
```

6. Check if the thumbnails are OK. When an image with the same name as the *.zip is not found, a thumbnail file with zero bytes is still generated, for easy way to track missing images and know the correct name the thumbnail must have.

7. Copy ROMs and playlists (and thumbnails) to the Lakka shared folders.

8. Restart RetroArch and play.
