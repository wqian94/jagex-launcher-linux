# Jagex launcher for Linux

This repo contains instruction on how to install the Jagex Launcher on linux through Wine as well as how to play through RuneLite.

## Why i created this repo

Unfortunatly the Jagex launcher does not work natively on Linux, and it's not as straight forward to play through RuneLite. Since Jagex havne't provided any documentation on how to run the Jagex Launcher on Linux i created this repo. Hopefully this won't be needed in the future, but until then this repo will provide the nessesary information.

## Instructions

**This repo does _NOT_ contain links to the Jagex Launcher or RuneLite. Please make sure you download everything from the correct websites**
 
<details>
<summary>

## Manual install
##

</summary>

### Requirements
- Wine with dependencies
- WineTricks
- .NET Framework 4.8
- Windows VM or Windows computer
- Jagex Launcher for Windows
- RuneLite AppImage (optional)

### Installing Wine

To install Wine with the necessary dependencies head over to [GloriousEggroll website](https://www.gloriouseggroll.tv/how-to-get-out-of-wine-dependency-hell) and follow the steps for your distribution. <br> 
Make sure you also install WineTricks as it's needed for the next step.


### Installing .NET Framework
To install .NET Framework open a terminal and type following command `winetricks --force -q dotnet48`

## Running the Jagex Launcher
Unfortunatly to run the Jagex Launcher you need all of the files from an already installed Jagex launcher in Windows. These files can be obtained either by installing the Jagex launcher in Windows on a virtual machine, or on a seperate computer. Once you have obtained the files place them in a folder, preferably in your home directory and open a terminal. Navigate to the folder you created and start the Jagex Launcher by running the following command `wine JagexLauncher.exe`

### Desktop entry
Unless you want to open a terminal every time you want to run the Jagex Launcher you should create a desktop entry. To create a desktop entry simply open a text editor and create a new text file. Inside the file type the following.
```
[Desktop Entry]
Type=Application
Name=Jagex Launcher
Terminal=false
Exec=wine /home/USER/JagexLauncher/JagexLauncher.exe
Icon=/home/USER/JagexLauncher/icon.png
```

Save the file as "jagex-launcher.desktop" in `/home/USER/.local/share/appliations` where "USER" is the name of your user in Linux and make sure that the exec path and icon path is the same as the folder you created earlier. Lastly download an icon and place it in the same folder. The Jagex Launcher icon can be found both on the OldSchool Wiki and the Runescape Wiki on the Jagex Launcher page.


If you only want to use the default runescape clients you can simply download it straight from the Jagex Launcher and run it, but if you also want to use RuneLite keep reading. 

### RuneLite

To set up RuneLite navigate into the following directory `/home/USER/.wine/drive_c/users/USER/AppData/Local` Create a new directory and call it RuneLite. Copy RuneLite.AppImage to this folder and make sure that it is executable by opening a terminal and typing `sudo chmod +x RuneLite.AppImage` Open a text editor and create a new file called RuneLite.sh Inside the file type the following where USER is the name of your Linux user.
```
#!/bin/sh
cd /home/USER/.wine/drive_c/users/USER/AppData/Local/RuneLite
./RuneLite.AppImage
```
After creating the file make sure that it is also executable by typing `sudo chmod +x RuneLite.sh` Next create a symbolic link by typing `ln -s RuneLite.sh RuneLite.exe`


Finally you need to add a registry key to Wine so the Jagex Launcher thinks RuneLite is installed.<br>

Create a new file called `InstallLocation.reg` with the following text and save it in your home directory.

```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall\RuneLite Launcher_is1]
"InstallLocation"="/home/USER/.wine/drive_c/users/USER/AppData/Local/RuneLite"
```

Open a terminal and type with following command `winetricks regedit`
Select registry, "Import Registry File.." and import the file you just created.

<details>
  <summary>Once you are done it should look like this</summary>
<img src="/assets/images/regedit.png">
</details>

You are finally finnished, and should be able to open the Jagex launcher with your new desktop entry and if everything is done correctly it should say Play when selecting RuneLite from the client drop down menu.

</details>

# Credits

Big thanks to these people for making the information available to create this repo.

"How to use Jagex's New Launcher on Linux" by c00k on Youtube
<br>
"Native Linux RuneLite running with Jagex Launcher" by jolty__ on Reddit

