# AttractMode
Repo to save common configuration files when using emulation with AttractMode

**mame.ini** - Common configuration changes for MAME or GroovyMAME
## AttractMode/romlists
**StreetFighter.txt** - All Street Fighter, Marvel vs, Capcom vs, SNK vs Games. (MAME v0.194)

**Mortal Kombat All.txt** - All Mortal Kombat ROMs. (MAME v0.232)

## Regular Expressions for creating romlists
Open the main romlist file like mame.txt do a find for the roms you are after e.g. "street fighter". Use notepad to find all in the document and use the below regex to delete the "Line 12345: " text.
    
    .*Line.\d+:.
    
