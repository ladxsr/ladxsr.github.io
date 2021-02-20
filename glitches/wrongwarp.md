# Wrong Warp
*Not to be confused with [screen wrapping](/glitches/screenwrap)*

Also known as the Kennel Glitch, Kennel World, or Glitch Dungeon, a Wrong Warp (abbreviated WW) allows Link to access a corrupted version of the game's underworld and dungeon maps.

Wrong Warp is done by touching a door warp (normally entered from below) from above. Collision data for floor tiles, sprite appearances, items within chests, and more are altered when within these maps. This leads to very interesting effects, some of which are helpful in a speedrun.

The differences between glitched maps are directly dependent upon your kill counter, normally used to deterine whether the Piece of Power should drop or not. For example, killing three enemies before doing a Wrong Warp will have different effects than if you kill four enemies.

## How to Perform
There are two known ways of Wrong Warping.

### Doghouse Method

1. Destroy the desired number of enemies for the particular glitched map. See Chest Guide for more information.
2. Head to Madam Meow-Meow's house in Mabe Village.
3. On the right side of her house is a doghouse with a door. Move Link to the top-right corner of the doghouse and face down.
4. Perform a Wall Clip so that Link's down-facing left side overlaps with the right wall by a few pixels.
5. Hold down-left until Link touches the warp from above.

Below is a video showing this method.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ep5bhUTW5_s" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Super Swim Method

1. Perform a [Super Swim](/glitches/superswim)
2. Walk to any doorway and position Link on the top of the doorway's tile
3. Equip Roc's Feather (if you haven't already) and jump. When Link lands, he should warp from above (if he doesn't, move towards the doorway.)

Note that, although this method is convenient, it is less predictable as it can be done on a plethora of doorways. Therefore, unless it is being done on the Doghouse's doorway, any info, maps or guides will not be based on this method.

## Mechanics
*Discovered by mabdulra, drenn, Artemis251*

Each room can have 4 warp points, numbered from 0 to 3. The tile positions of these warps are stored in RAM at D416-D419. Each warp has 5 bytes of data describing the post-warp destination at D401, D406, D40B, and D410, respectively. For example, warp 0's data (whose tile position is stored at D416) is stored in these 5 bytes:

**Warp 0 Destination Bytes**
Address | Purpose
-- | --
D401 | Map Category
D402 | Sub-Map
D403 | Room
D404-D405 | Post-warp X and Y pixel positions (respectively)

When you touch a warp, the game will check the 4 bytes at D416-D419 to see if one of them corresponds to Link's position. If none of them do, the game attempts to load the invalid "warp 4" (the 5th warp, since this is counting from 0). This occurs when touching a door from the top. It loads from these bytes:

**Warp 4 Destination Bytes**
Address |	Purpose
-- | --
D415 | Piece of Power counter (used for Map Category)
D416 | Warp 0's position in tiles (used for Sub-Map)
D417 | Warp 1's position in tiles (used for Room)
D418-D419 |	Warp 2 and 3's positions; usually 0x00 (used for Post-Warp X and Y positions)

### Map Category
The map category determines which type of map you are going to warp in:

* 0x00 - Overworld map
* 0x01 - Underworld or Dungeon map
* 0x02 - Side-scrolling map

As stated before, when you enter a door warp in the overworld from the reverse side, the map category byte gets set by the Piece of Power counter.

### Sub-Map
Link's Awakening has three base maps, but Link's Awakening DX has four. The first three base maps contain 256 tiles and are arranged in a 16x16 grid. All sub-maps and the fourth base map contain 64 tiles and are arranged in an 8x8 grid. The arrangement of rooms in the base maps is not the same as they are arranged in game, save for the Overworld base map. The sub-maps pull data from the appropriate base map and rearranges the rooms for the particular dungeon or cave you are trying to enter.

The list of base maps is as follows:

* Overworld (Koholint Island)
* [Underworld 1](https://s3.amazonaws.com/zeldaspeedruns/app/public/system/images/1041/original/LADX%20Underworld%201%20Map.png) (Levels 1-6, some caves)
* [Underworld 2](https://s3.amazonaws.com/zeldaspeedruns/app/public/system/images/1051/original/LADX%20Underworld%202%20Map.png) (Levels 7-8, many caves)
* Color Dungeon (LADX only)

**Sub-Maps**
Map ID | Map Description
-- | --
0x00 | Tail Cave
0x01 | Bottle Grotto
0x02 | Key Cavern
0x03 | Angler's Tunnel
0x04 | Catfish's Maw
0x05 | Face Shrine
0x06 | Eagle's Tower
0x07 | Turtle Rock
0x08 | Windfish's Egg
0x09 | Blank
0x0A | Caves
0x0B-FE | Underworld base map
0xFF | Color Dungeon

Sub-maps 0x0B to 0xFE all refer to individual rooms within the underworld maps, but they load different graphical tilesets. For example: house tileset, Kanalet Castle tileset, cave tileset, etc. Kanalet Castle is not in its own sub-map, but rather the arrangement of maps in the Underworld 2 base map keeps Kanalet Castle whole. As such, there is no need to rearrange the rooms as with the other dungeons.

#### Glitched Map
When you use the Doghouse Method for the first time you will appear in the Underworld 1 map, but the tilesets will be glitched. If you entered the Doghouse with 2 kills you will immediately warp to a glitched version of the Underworld 2 map.

### Room
The third byte determines which room within the map you will arrive it. All base maps contain 256 tiles divided in a 16x16 grid. The sub-maps are contain 64 tiles divided in an 8x8 grid. When within a sub-map, if you were to obtain Out of Bounds you would be able to walk from one sub-map to another if they were connected. For example, from the Face Shrine sub-map it is possible to obtain an Out of Bounds and walk to the Tail Cave's sub-map. Should you do this, the graphical tileset will be the same as the sub-map you originally entered; you would see the Tail Cave with the Face Shrine tileset.

### Wrong Warping in Glitched Maps
Upon entering a glitched map it is possible to perform wrong warps into other glitched maps that would otherwise be inaccessible. The one requirement for this to be possible is for there to be door tiles located in rooms that do not contain warp destination data. The fastest way to ensure this is to kill three enemies before activating the Wrong Warp. This will make all bottom walls, as well as certain other tiles, behave like door warps.

Touching staircases within a glitched map will warp you out of the glitched map to where the staircase normally leads. This is because proper warp destination data will be set upon entering the room. However, if you leave the room the warp data will remain set with one modification: the map category byte will change to 0xFF, the glitched byte. If you were to touch a warp tile under this condition you would end up where that warp would have led, but in a glitched version of that map. Using this mechanic it is possible to enter glitched versions of dungeons from the initial glitched underworld map. This has repercussions for speedruns since it allows you to skip bosses and obtain instruments.

Below is a video example of using wrong warps after getting into a Glitched Map in order to obtain the Conch Horn. The room I11 was entered in order to set the warp point to the basement of Bottle Grotto. Following that, the warp tile from I10 (a room with no natural warp point in it) was used in order to enter a glitched version of the dungeon. The Conch Horn was easily obtained from within the glitched Bottle Grotto.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ugR7sTLiiiw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[source](https://web.archive.org/web/20180404215105/http://spiraster.x10host.com/LADXWiki/index.php/Wrong_Warp)
