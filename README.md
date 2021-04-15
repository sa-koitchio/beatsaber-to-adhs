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

For the most part, you don't need this, unless you want to manipulate or create maps.

## Other files used for custom maps
**song.ogg** : the song file in ogg format. Has to be in the same folder as map.ini

*optional:* **cover.jpg** : a song cover artwork. If none is provided, the game will use a default background.
