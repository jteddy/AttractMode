# Creating a custom list of ROMs for AttractMode / GroovyArcade / MAME

## MAME INI Files

Ensure these extras are included in AttractMode *import_extras*. This adds additional information needed to for when we need to filter/sort. I've place them in the directory `/home/arcade/shared/configs/mame/ini/`

- catver.ini - https://www.progettosnaps.net/catver/
- nplayers.ini - https://nplayers.arcadebelgium.be/

## AttractMode - Emulator Configuration

Add the import_extras line to `/home/arcade/shared/frontends/attract/emulators/MAME.cfg`

```
# Generated by groovymame-config
#
executable           /opt/galauncher/galauncher.sh
args                 groovymame arcade [name]
workdir              $HOME/shared/configs/mame
rompath              $HOME/shared/roms/mame/
romext               .zip;.7z
system               Arcade
info_source          listxml
import_extras        $HOME/shared/configs/mame/ini/nplayers.ini;$HOME/shared/configs/mame/ini/catver.ini
artwork    flyer
artwork    marquee         $HOME/shared/frontends/attract/menu-art/marquee
artwork    snap            $HOME/shared/frontends/attract/menu-art/snap
artwork    wheel

```

## AttractMode - Generate the Game List 
This will generate the full romlist based on the version of GroovyMAME installed.
```
attract --build-romlist MAME --full
```

## Generating A Custom ROM Lists

I don't want to copy the full MAME merged set to my drive (37,978 at this time of writing). There are numerous ROMs I will never play on my machine such as mechanical, gambling etc.

AttractMode Column Name & Descriptions

- Name - name of the rom Ex. pacman.zip
- Title - The name you want to show in the list Ex. Pac-Man
- Emulator - The emulator that this games it used with
- CloneOf - Used to show a clone of a game (mame) [pacman is a clone of puckman. puckman is the parent rom]
- Year - The year the game was made
- Manufacturer - The manufacturer name
- Category - The category of the game (genre) [shooter fighting role playing ect.]
- Players - the number of players
- Rotation - Is it a vertical or a horizontal screen (mame)
- Control - Joystick spinner trackball ect.
- Status - The working status of the game [Good, working but not perfect not working] (mame)
- DisplayCount - How many screens it uses (mame)
- DisplayType - Is it a vector or a Raster monitor (mame)
- AltRomname - if there is one (pacman.zip..instead of puckman.zip)
- AltTitle - if there is one (Pac-Man..instead of Puckman.zip)
- Extra - any extra info

**Datutil**

Create the MAME dat file for groovymame.

- [datutil](http://www.logiqx.com/Tools/DatUtil/) - Instructions can be found [here](https://www.romcenter.com/forum/viewtopic.php?t=3373).

```
/usr/local/bin/groovymame -lx > groovymame.dat
```

```
datutil.exe -f rc2 -o groovyMAME0.229_RomCenter2.dat "groovymame_229.dat"
```

datutil kept crashing on Win10 and onto plan B.

**Excel**

I found the best approach was to create a list of all the ROMs that I wanted deleted. This will save about 50GB of disk space and get rid of a lot of waste.

**Remove**

- Extras
  - Mechanical
- DisplayCount
  - 3,4
- Status
  - preliminary
- Category
  - casino, medal, rhythm, slot machine, utilities, whac-a-mole, pachinko
- Players
  - non-arcade, Pinball,

### Deleting the uneeded ROMs over

I captured the filenames of the list of ROMs I need. Use this list to copy the ROMs to my chosen directory.

As I just had the filenames I needed to add the .zip extension to the list. I did this in notepad++ with a find/replace

**Find What:** (^.*)

**Replace with**: $1.zip

To copy the files I just used the command prompt

```
for /f %n in (copy_files.txt) do cp "%n" "E:\arcade\ROMVault_V3.2.5\RomRoot"
```

```
for /f %i in (delete_files.txt) do del %i
```

### Create the MAME DAT File

ui.ini has a categorypath. I copied the files from pS_CatVer_232.zip/UI_files into the /home/arcade/shared/configs/mame/folders directory

```
#
# UI SEARCH PATH OPTIONS
#
categorypath              folders

```

My /home/arcade/shared/configs/mame/ini folder has catver.ini and nplayers.ini in it.

Create my MAME XML file

```
/usr/local/bin/groovymame -lx > groovymame.dat
```

### Verify your ROM set

As if this writing GroovyMAME is using v229 and I have v232 ROMs. I'll verify the ROM set to ensure everything is working.

I'm a fan of [RomVault](https://www.romvault.com/). The first step

- Drop the DAT file into /romvault/DatRoot/
- Create a copy of my v232 rom set. 
- Set the directory and "Scan ROMs"
- Copy the files from /romvault/ROMRoot/ into /home/arcade/shared/roms/mame/


# AttractMode
## Filters

The individual ROM lists maybe a bad idea. The goal now is to use filters.



#### Common Filters



### Street Fighter

## AttractMode/romlists

### Street Fighter.txt
All Street Fighter, Marvel vs, Capcom vs, SNK vs Games. (MAME v0.229)
**Key Words**

- Street Fighter
- Marvel vs
- SNK vs
- Marvel Super Heroes
- Gem Fighter
- Tatsunoko
- Super Puzzle Fighter

### Mortal Kombat.txt

All Mortal Kombat ROMs. (MAME v0.229)

**Key Words**

- Mortal Kombat

### King of Fighters.txt

**Key Words**

- King of Fighters

## AttractMode.cfg Filters

To achieve the same as the above.

## Regular Expressions for editing romlists in notepad++

Open the main romlist file like mame.txt do a find for the roms you are after e.g. "street fighter". Use notepad to find all in the document and use the below regex to delete the "Line 12345: " text.
    
    .*Line.\d+:.

## AttractMode Commands

Generate a ROM list. I received errors when mame had admin privileges and attract-console didn't.

```
attract-console --build-romlist mame-groovy-229 --full
```



 # GroovyArcade

 ## Arch Commands
 sudo pacman -Sy

 sudo pacman -S unzip

 sudo mount /dev/sdb2 /media/arcade/

```bash
vi /etc/fstab

/dev/sdb2               /mnt/arcade     ntfs-3g         uid=arcade,gid=arcade   0 0
```


