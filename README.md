## Custom map file structure
Custom maps  must follow a certain structure in order to be detected correctly by the game.
The **map.ini** is based on the ini structure and contains the following keys:

 

  

    [Map]
	songname = Name of the song:STRING
	songartist = Name of the artist:STRING
	leftnotes = Timestamps in frames after song start, when to spawn left key notes:INT-ARR
	upnotes = Same as above, for up-facing notes.
	rightnotes = Same as above, for right-facing notes.
	notemovespeed = The default note speed used by the game:INT
	songlength = Length of the song in seconds:INT
	converted = Tells the game wether or not the map is using lowercase keys:INT

For the most part, you don't need this, unless you want to manipulate or create maps. Keep in mind: if you set "converted = 1", the game will use all-lowercase ini-keys.
If it is set to 0, it will use camelCase keys: eg. songName

## Other files used for custom maps
**song.ogg** : the song file in ogg format. Has to be in the same folder as map.ini

*optional:* **cover.jpg** : a song cover artwork. If none is provided, the game will use a default background.


# Mods

Mods are supported by the game. Below, you will find a short copy of the mod help file included in the game folder:

###########################
DISCLAIMER: ADD DLLs AT YOUR OWN RISK! THEY CAN CONTAIN MALICIOUS CODE!
###########################

## Introduction to modding

Mods are dll files and bumped by the game every time it changes a scene (for example going from menu to a level)

If there is a problem compiling the mods, the mod feature will be disabled for the current game-
as soon as you fixed the problems, restart the game.

API can be found at #API
##########################

If you broke your mods, here is a backup of the content for the modloader.ini file:

[modfiles]
fnames = ["empty"]
funcnames = ["none"]

Paste the content above into the modloader.ini, remove everything else. This should get rid of all problems

#########################

## How-to-add-mods:

Step 1: 
Paste the .dll file in this folder.

Step 2: 
Edit the "modloader.ini" file as following:

[modfiles] 	   <--- this has to be left like it is
fnames = ["empty"] <-- if it says empty as it says here, change the values to the name of the .dll file like so:
			fnames = ["yourdllfile.dll"] If you have multiple mod dlls, add them like this: fnames = ["yourdllfile.dll","secondfile.dll"]

funcnames = ["none"] <-- edit this to whatever the function is called in your dll file. I recommend using the same name as the dll filename itself when compiling the dll.
		         the same rules for editing and multiple files also apply here.

onstart = ["empty"] <-- These mods are only bumped at the start of the game, they get passed a macro that can be specified in "osvalues"


osnames = ["none"] <-- the same as funcnames but for onstart mods


osvalues = ["none"] <-- Put the macro you want to pass to your mod here



Step 3: Start the game. It should say it successfully loaded your mods now.

## macro list

all macros pass strings to the dll:

"gmversion" : the current gameversion

"discordid" : the game's discord identifier used to connect to rpc



## Mods-requirements:

Before adding mods into the game blindly, make sure they follow certain aspects.
If they don't, the game could crash or not even start properly.

Also, don't trust any .dll files floating around on the web, it is safest to make and compile them yourself in Visual Studio for example.

REQUIREMENTS:

-Only 1 function per dll file. I know its stupid but thats how it is due to the way I load the mods.

-The function must take 2 string values and MUST RETURN an Integer value (Wether successful execution of the mod or not, to prevent the game from crashing).

-The dll files can use libraries or web requests. (For example rich presence or other system stuff)

Also make sure to compile them as C / C++ dlls.

Here is a video on how to create/compile dlls on your own:

https://www.youtube.com/watch?v=jkgMxrDvwPs&list=PLevT-1lvngTgf1KdZZs2RsQAKNv9uv4wx&index=41

## API

The current game API bumps the mods everytime it changes rooms.
It will pass 2 string parameters:
If the player is playing a song, the first parameter will contain the song name, the second will be the song artist. If in any other room, it will pass 2x "Menu".
The API may change in the future.

# Using Undertale Mod Tool

The game was compiled using GameMaker Studio 1.4 default compiler (not YYC) so you can also use the Undertale Mod Tool to make changes
directly to the data.win

## Legal notice:
The whole project (including the main game) is licensed under "Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)" and MIT License.

This means:
You are free to:
Share — copy and redistribute the material in any medium or format
Adapt — remix, transform, and build upon the material

Under the following terms:

Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

NonCommercial — You may not use the material for commercial purposes.

ShareAlike — If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
