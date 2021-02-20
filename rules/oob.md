# Out of Bounds

Out of Bounds (abbreviated OOB) is the act of accessing certain parts of a sub-map or the Overworld that would normally be impossible through normal means. This can be done with glitches such as Ledge Buffering, Super Jumping (SJ), Superswimming (SS), Screen Wrapping, and the likes.

## Definitions
Out of Bounds is usually defined with two distinctive restrictions: a ruleset describing what you can and can't do in the game space and the global ban on super swimming (SS). 

### [Super Swim](/glitches/superswim)
SS is banned in all commonly used OOB rulesets. SS allows you to freely traverse through solid blocks and so is deemed too broken to be in most no OOB categories.

### Seabass Ruleset
*Conceived by oSeabass*

The Seabass Ruleset is used by the LADX community to define OOB and is solely based on one principal alone: which tiles on the screen are you allowed to stand on. To do so it defines three categories of tiles:

* **Normally Accessible Tiles (NATs)**, unsolid tiles that the player is able to access without use of tricks or glitches.
  * Doors that are able to open (for example boss/key doors in dungeons) are considered NATs since you can access the tile they are on once you open the door. Note that when doors are closed they are solid.
  * Raised block-switch blocks are considered as NATs because you are able to move on them regardless of their state - they simply prevent you from passing them when in an erect state.
  * Reachable pits and water are considered as NATs because you are still able to technically move on them.

* **Boundary Tiles (BTs)**, tiles that are directly (cardinally) next to a NAT. 
* **OOB Tiles**, any type of tile that is not directly (cardinally) next to a NAT (and therefore not normally accessible).

With those definitions in mind, the ruleset is as follows:

* Standing on BTs is allowed.
* Transitioning onto BT and solid tiles is allowed (for example: Villa Skip).
* Transitioning while on a SOLID tile is NOT allowed (for example: jumping through the boss key door in Catfish Maw).
* Standing on, transitioning onto, and "feather jumping" over OOB Tiles is not allowed. (for example: Blaino Skip).

### Warpless Ruleset
*Conceived by Aulos and Zmaster*

The Warpless ruleset is based on Tompa's ruleset (used primarily by the TAS community). It is used by the LA community to define OOB and is based on how the game forms cave and dungeon systems when warping. This makes a lot of the definition based on the game code with some added arbitrary restrictions. The rules are as follows:

* The player is not allowed to initiate a screen transition while standing on a solid tile.
  * Note that what a solid is is non-negotiable: if you can't move while standing on it, it is a solid.
* The player is not allowed to move from one cave system or dungeon system to another via screen transitions.
  * Dungeon systems are always contained within an 8x8 array of screens, and so they are defined as such. Cave systems are defined based on how they appear in their respective sub-maps - examples will be provided below.
    * Note that the overworld is its own system, and so there is no way to go OOB in it. Likewise, the sub-map of the Windfish's Egg acts very much like a dungeon, and so it is considered a dungeon system. Houses are considered to be cave systems as well.
* Super Swimming, Wrong Warps, and Screen Warping is banned.

## History
Before SJs were discovered, both the LA and LADX community defined OOB as so:

* Because Link is able to clip 3 pixels into a solid object via Wall Clipping, OOB is defined as clipping more than 3 pixels into a solid object.

However, this ruleset did not properly address SJs as there were some cases where Link was only jumping over boundaries, not clipping into them. Therefore, there needed to be a new definition made to address this problem.

Defining a new definition proved to be difficult as SJs opened up a whole new way of playing the game, from being able to access Key Cavern and Bottle Grotto without Wrong Warping or travel in the Overworld, to an easier method of doing Rooster Skip. Likewise, it was hard to define without banning tricks already used in the run, such as Villa Skip. However, two definitions were eventually made, which are used by the two communities: the Seabass Ruleset and the Warpless Ruleset.


* TODO: Example pictures

[source](https://web.archive.org/web/20180404215203/http://spiraster.x10host.com/LADXWiki/index.php/Out_of_Bounds)
