# PES-2021-Smoke-And-Tifo  
[Evoweb Thread https://evoweb.uk/threads/in-game-smokes-some-tifos.89796/]
- TOOLS NEEDED: PES ARCHIVE TOOL  
- LINK: https://evoweb.uk/threads/★-pes-2021-tools-thread.83967/
-----------------------------------
STEP 1 (Locating Files):
-----------------------------------
```
Locate stadium effect folder for the stadium you want to modify

BACKUP The Asset Folder just incase

Path: [STADIUM]\Asset\model\bg\[stxxx]\effect\#Win
```
------------------------
File Suffix Meanings
------------------------
```
df ----> Day Fine  
dr ----> Day Rainy  
nf ----> Night Fine  
nr ----> Night Rainy  
```
Choose the fpk (not fpkd) of the weather condition you want smokes to appear for.

-----------------------------------
STEP 2 (Prepping For Modification):
-----------------------------------
```
Drag the fpk in the effect folder you want to modify onto PES ARCHIVE TOOL.

There should now be an xml file generated in the same folder and a folder with the same name as the fpk

Within the new folder generated, there will be an effect_config file.

Open effect_config, scroll to the bottom and paste the code from the code file attached between the setting and effect tags as shown in the image.
```
![image](https://user-images.githubusercontent.com/77795437/210905736-70d31a31-b825-41d9-bd4c-08468612007c.png)

--------------------------------------
STEP 3 (Creating first smoke element):
--------------------------------------
```
scroll to the last create tag in the document and paste the following below it

<create type="SmokeBomb2" setting="1" floor="upper" dir="back" />

A "setting" corresponds to the index of the item you want to put in the game.
```
![image](https://user-images.githubusercontent.com/77795437/210905775-f15c1beb-1d92-4e91-b9e7-4cb41f6cc9bf.png)
```
Indexes work such that if n = 1 (Smoke)
n+1 = flare
n+2 = fire
n+3 = smoke

Items of the same type are 3 indexes away from each other

Since the setting of the create is set to 1, the corresponding values that can be edited for it are in setting index 1
```
-----------------------------------
STEP 4 (Modifying smoke element):
-----------------------------------

![image](https://user-images.githubusercontent.com/77795437/210905815-39a5642a-44a9-4c4f-8f83-049e7d1fda55.png)
```
Within setting indexes, there are a lot of parameters as shown above.

Key Values: (Experiment with the others)
pos: Lets you decide the position of the element in x,y,z format where x is left to right (left being negative); y is up or down (down is negative); z is depth (basically left or right of the stands behind the goals)
dir: Lets you decide the direction you want the smoke to blow in, in x,y,z format
life: How long the smoke lasts
scale: How big the smoke is
scale_range: How much the smoke is allowed to deviate in size
emit_interval: How quickly new smoke spawns
color_values: Colours that you want the smoke to produce in HEX. (You can mix and match the four HEX values)

For testing purposes set index 1's smoke pos to 0,0,0 and save the effect_config file (This will put it at the centre of the pitch)

Go back to [STADIUM]\Asset\model\bg\[stxxx]\effect\#Win

Drag xml file onto the archive tool and it will overwrite the previous fpk file.
If you want to leave the original stadium untouched, save your modifed fpk somewhere else and replace the stadium asset folder with the backup
```
-----------------------------------
STEP 5 (Creating an AddOn):
-----------------------------------  

```
If your stadium has an existing AddOn folder just create a new folder within AddOn with the following structure

AddOn\[yourfoldername]\Global\Asset\model\bg\[stxxx]\effect\#Win (where [stxxx] is the stadium ID)

then put your modified fpk in #win

In addon_config add xx = yourfoldername (where xx is the next available number)

If there's no AddOn folder you can use the template I've provided. Change the name of the folder within AddOn to whatever you want

Change the stxxx folder to your stadium ID

In addon_config add 01 = yourfoldername

then put your modified fpk in #win

Now you can edit the fpk via the Addon folder rather than working on the Stadium directly
```
------------------------------------------------------------------------------
ADDITIONAL ADDON STRUCTURE FOR COMPETITION BASED SMOKES
-------------------------------------------------------------------------------  
```
AddOn\[yourfoldername]\Comp\[COMPID]\Asset\model\bg\[stxxx]\effect\\#Win
```

NOTES:  
-If all has been done correctly, when you load into a match, you will see a white mist in the middle of the pitch.  
-Every time you edit the effect_config file, you must generate a new fpk by dragging the xml file of the fpk in the parent folder onto the archive tool.  
-To add more elements, just add new create tags with the setting equal to the corresponding index.  
-To test modifications, you can edit the effect_config, save it, generate a new fpk and just back in and out of a match without closing the game to see the new effects instantly. (Will come in handy for repositioning)  

# In-game demo

https://youtu.be/u02Pmypu0Zs
