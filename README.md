# AttractMode
Repo to save common configuration files when using emulation with AttractMode

**mame.ini** - Common configuration changes for MAME or GroovyMAME
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

## Regular Expressions for creating romlists
Open the main romlist file like mame.txt do a find for the roms you are after e.g. "street fighter". Use notepad to find all in the document and use the below regex to delete the "Line 12345: " text.
    
    .*Line.\d+:.

## AttractMode Commands

Generate a ROM list. I received errors when mame had admin privliges and attract-console didn't.
    
    attract-console --build-romlist mame-groovy-229 --full
    
 # GroovyArcade
 
 ## Common Commands
 sudo pacman -Sy
 
 sudo pacman -S unzip
 
 sudo mount /dev/sdb2 /media/arcade/
