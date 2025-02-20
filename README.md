# Jagex Launcher Linux

This repo contains instruction on how to run the Jagex Launcher in Linux as well as how to play through RuneLite

✔️ Tested and working with Jagex Accounts

### Disclaimer

I am not affiliated with Jagex or RuneLite and is not responsible for for the contens of this page

## Bottles
<details closed>
<summary>The easiest way to run the Jagex Launcher is with Bottles</summary>

### Requirements

- [Bottles](https://flathub.org/apps/details/com.usebottles.bottles)<br>
- [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal)
- [Jagex Launcher for Windows](https://www.jagex.com/en-GB/launcher)<br>
- [RuneLite for Linux](https://runelite.net)<br>
- Windows Virtual Machine or Windows computer<br>

### Jagex Launcher
- [ ] Install the Jagex Launcher either in a Windows virtual machine or on a seperate computer
- [ ] Copy the installation folder to the following directory: `$HOME`

### Bottles and FlatSeal
Install Bottles with the link above
- [ ] Install Flatseal with the link above
- [ ] Launch Flatseal and select Bottles. Under Filesystem enable `All user files`
- [ ] Create a new bottle and name it Jagex Launcher. Under enviorment select `Application`
- [ ] Move the installation folder to the following directory:
    ```
    $HOME/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/Program Files (x86)
    ```
- [ ] Select `Run Excecutable` and select the Jagex Launcher executable
- [ ] Close Bottles and run the following commmand:
    ```
    flatpak override com.usebottles.bottles --user --filesystem=xdg-data/applications
    ```
- [ ] Open Bottles and select the Jagex Launcher. Click the three dots to the right and select `Add Desktop Entry`

### RuneLite

- [ ] Install `libfuse2` through your package manager. For example: `sudo apt install libfuse2`
- [ ] Navigate to this directory:
    ```
    $HOME/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/users/$USER/AppData/Local
    ```
- [ ] Create a new folder called `RuneLite` and move `RuneLite.AppImage` to this folder
- [ ] Make the file executable with the following command:
    ```
    sudo chmod +x RuneLite.AppImage
    ```
- [ ] Create a new file called `RuneLite.sh` with the following text:
  ```
  #!/bin/sh
  cd $HOME/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/users/$USER/AppData/Local/RuneLite
  ./RuneLite.AppImage --appimage-extract-and-run
  ```
- [ ] Save the file in the `RuneLite` folder you just created
- [ ] Make `RuneLite.sh` executable with the following command: `sudo chmod +x RuneLite.sh`
- [ ] Create a symbolic link to `RuneLite.sh` with the following command: `ln -s RuneLite.sh RuneLite.exe`

#### Windows Registry

- [ ] Create a new file called `InstallLocation.reg` in your home directory:
```
cat > $HOME/InstallLocation.reg <<EOF
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall\RuneLite Launcher_is1]
"InstallLocation"="C:/users/$USER/AppData/Local/RuneLite"
EOF
```
- [ ] Open Bottles, select Jagex Launcher, then scroll down and select Registry Editor
- [ ] Select registry, Import Registry File.. and import the file you just created
- [ ] Now launch the Jagex Launcher and select RuneLite. `Install` should be replaced with `Play` and launch RuneLite

</details>

## Steam Deck
 
<details closed>
<summary>Run the Jagex Launcher on the Steam Deck</summary> 
 
### Requirements

- [Bottles](https://flathub.org/apps/details/com.usebottles.bottles)
- [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal)
- [Jagex Launcher for Windows](https://www.jagex.com/en-GB/launcher)
- [RuneLite for Linux](https://runelite.net)
- Windows Virtual Machine or Windows computer
  <br>

### Jagex Launcher
Install the Jagex Launcher either in a Windows virtual machine or on a seperate computer<br>
Copy the installation folder to the following directory: `/home/deck`<br>

### Bottles and FlatSeal 
Install Bottles with the link above<br>
Install Flatseal with the link above<br>
Launch Flatseal and select Bottles. Under Filesystem enable `All user files`<br>
Launch Bottles and then create a new Bottle, naming it Jagex Launcher. Under environment select `Application`<br>
Select `Add Shortcuts...` and select the Jagex Launcher executable<br>
Click the three dots to the right of the bottle and select `Add to Steam`<br>
`At this point the Jagex Launcher should launch properly both in Bottles, and in Steam under the Non-Steam Game category.`<br>
Before continuing with installing RuneLite, Right click the Jagex Launcher icon in the notification tray at the bottom right and select 'Exit'

## RuneLite

Enable hidden files, then navigate to this directory: `/home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/users/deck/AppData/Local`<br>
Create a new folder called `RuneLite` and move `RuneLite.AppImage` to this directory<br>
Make the file executable by right clicking the file, selecting permissions, and checking `Is Executable`<br>

Create a new file called `RuneLite.sh` with the following text:
```
#!/bin/sh
cd /home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/users/deck/AppData/Local/RuneLite
./RuneLite.AppImage --appimage-extract-and-run
```
Save the file in the `RuneLite` folder you just created<br>
Make `RuneLite.sh` executable as well<br>
Right click the RuneLite folder and select "Open Terminal Here"<br>
Create a symbolic link to `RuneLite.sh` with the following command: `ln -s RuneLite.sh RuneLite.exe`

#### Windows Registry

Create a new file called `InstallLocation.reg` with the following text:
```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall\RuneLite Launcher_is1]
"InstallLocation"="/home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Jagex-Launcher/drive_c/users/deck/AppData/Local/RuneLite"
```
Save the file in any location, such as `/home/deck/Documents`<br>
Open Bottles, select Jagex Launcher, then scroll down and select Registry Editor<br>
Select registry, Import Registry File.. and import the file you just created<br>
Now launch the Jagex Launcher and select RuneLite. `Install` should be replaced with `Play` and launch RuneLite

</details>

## Steam Deck Proton
<details closed>
<summary>Run the Jagex Launcher on the Steam Deck via Proton, using the original Old School Runescape application</summary>

### Requirements

- [Old School Runescape Steam](https://store.steampowered.com/app/1343370/Old_School_RuneScape/)
- [Wine](https://flathub.org/apps/details/org.winehq.Wine)
- [Jagex Launcher for Windows](https://www.jagex.com/en-GB/launcher)
- [RuneLite for Linux](https://runelite.net)
- Windows Virtual Machine or Windows computer
  <br>

### OSRS Steam
Install Old School Runescape on Steam, and launch it once to create the prefix
  
### Wine
Install Wine from the discover store<br>
Open a new terminal, and type the following command to install .NET 4.8 into the OSRS Proton prefix: `flatpak run --env=WINEPREFIX="/home/deck/.local/share/Steam/steamapps/compatdata/1343370/pfx" --command=winetricks org.winehq.Wine -q dotnet48`<br>
  
### Jagex Launcher
Install the Jagex Launcher either in a Windows virtual machine or on a seperate computer<br>
Enable hidden files, then copy the contents of the installation folder to the following directory: `/home/deck/.local/share/Steam/steamapps/Old School Runescape/bin/win64`<br>
Right click in the win64 folder and select "Open Terminal Here"<br>
Create a symbolic link to `JagexLauncher.exe` with the following command: `ln -s JagexLauncher.exe osclient.exe`

### RuneLite
Download the RuneLite appimage from the link above<br>
Navigate to this directory: `/home/deck/.local/share/Steam/steamapps/Old School Runescape`<br>
Create a new folder called `RuneLite` and move `RuneLite.AppImage` to this directory<br>
Make the file executable by right clicking the file, selecting permissions, and checking `Is Executable`<br>

Create a new file called `RuneLite.sh` with the following text:
```
#!/bin/sh
cd "/home/deck/.local/share/Steam/steamapps/Old School Runescape/RuneLite"
./RuneLite.AppImage --appimage-extract-and-run
```
Save the file in the `RuneLite` folder you just created<br>
Make `RuneLite.sh` executable as well<br>
Right click the RuneLite folder and select "Open Terminal Here"<br>
Create a symbolic link to `RuneLite.sh` with the following command: `ln -s RuneLite.sh RuneLite.exe`

### Windows Registry
Create a new file called `InstallLocation.reg` with the following text:
```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall\RuneLite Launcher_is1]
"InstallLocation"="/home/deck/.local/share/Steam/steamapps/Old School Runescape/RuneLite"
```
Save the file in any location, such as `/home/deck/Documents`<br>
Open a terminal, and run the following command: `flatpak run --env=WINEPREFIX="/home/deck/.local/share/Steam/steamapps/compatdata/1343370/pfx" --command=winetricks org.winehq.Wine regedit`<br>
Select registry, Import Registry File.. and import the file you just created<br>
You can now uninstall Wine through the discover store if you wish<br>
Now launch the Jagex Launcher and select RuneLite. `Install` should be replaced with `Play` and launch RuneLite
  
### Gaming Mode
To improve RuneLite in Gaming mode, a few settings need to be changed<br>
Open RuneLite, and click Configuration to open the plugin settings list. Scroll down to `RuneLite`, and click the cog icon<br>
Set `Game size` to `994x768`<br>
Set `Resize type` to `Keep window size`<br>
Enable `Lock window size`<br>
Set `Contain in screen` to `Always`<br>
Enable `Always on top`<br>
In the main plugin settings list, scroll down to `Stretched Mode` and either make sure `Integer Scaling` is Disabled or disable the plugin entirely

</details>
  
  
  
## Old Method

<details close>
<summary>Run the Jagex Launcher manually using Wine</summary>

### Requirements

- [Wine](https://www.gloriouseggroll.tv/how-to-get-out-of-wine-dependency-hell)
- [WineTricks](https://github.com/Winetricks/winetricks)
- [Jagex Launcher for Windows](https://www.jagex.com/en-GB/launcher)
- [Jagex Launcher icon](https://runescape.wiki/images/Jagex_Launcher_icon.png)
- [RuneLite for Linux](https://runelite.net)
- .NET Framework 4.8
- Windows Virtual Machine or Windows computer

> **Note**<br>
> Replace USERNAME with the name of your Linux user

### Wine

Install Wine with the link above and follow the instructions for your distribution<br>

### WineTricks
Install WineTricks through your package manager. For example: `sudo apt install winetricks`

### .NET Framework

Install .NET Framework with the following command: `winetricks --force -q dotnet48`

### Jagex Launcher
Install the Jagex Launcher either in a Windows virtual machine or on a seperate computer<br>
Copy the installation folder to your home directory on your Linux computer<br>

### Desktop entry
Create a new file called `jagex-launcher.desktop` with the following text:
```
[Desktop Entry]
Type=Application
Name=Jagex Launcher
Terminal=false
Exec=wine /home/USERNAME/Jagex\ Launcher/JagexLauncher.exe
Icon=Jagex_Launcher_icon
```

Save the file in: `/home/USERNAME/.local/share/appliations`<br>
Download the Jagex Launcher icon and save it in `/home/USERNAME/.local/share/icons`<br>
Make sure that the exec path is the same as the path to the Jagex Launcher<br>

### RuneLite

Navigate to this directory: `/home/USERNAME/.wine/drive_c/users/USERNAME/AppData/Local`<br>
Create a new folder called `RuneLite`and move `RuneLite.AppImage` to this directory.<br>
Make the file executable with the following command: `sudo chmod +x RuneLite.AppImage`<br>

Create a new file called `RuneLite.sh` with the following text:
```
#!/bin/sh
cd /home/USERNAME/.wine/drive_c/users/USERNAME/AppData/Local/RuneLite
./RuneLite.AppImage
```
Save the file in the `RuneLite` folder you just created<br>
Make `RuneLite.sh` executable with the following command: `sudo chmod +x RuneLite.sh`<br>
Create a symbolic link to `RuneLite.sh` with the following command: `ln -s RuneLite.sh RuneLite.exe`

#### Windows Registry

Create a new file called `InstallLocation.reg` with the following text:
```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall\RuneLite Launcher_is1]
"InstallLocation"="/home/USERNAME/.wine/drive_c/users/USERNAME/AppData/Local/RuneLite"
```
Save the file in your home directory<br>
Open Windows Registry Editor with the following command: `winetricks regedit`<br>
Select registry, Import Registry File.. and import the file you just created<br>
Now launch the Jagex Launcher and select RuneLite. `Install` should be replaced with `Play` and launch RuneLite

</details>

### References

<sub>[How to use Jagex's New Launcher on Linux by c00k](https://www.youtube.com/watch?v=izLxF_Wwinw)</sub><br>
<sub>[Native Linux RuneLite running with Jagex Launcher Launcher by jolty__](https://www.reddit.com/r/2007scape/comments/uo1ey1/native_linux_runelite_running_with_jagex_launcher)</sub><br>
<sub>[How to Run Jagex Launcher on Steam Deck/Linux Utilizing Bottles by jeremiah1119](https://www.reddit.com/r/2007scape/comments/11q8mly/how_to_run_jagex_launcher_on_steam_decklinux/)</sub>
