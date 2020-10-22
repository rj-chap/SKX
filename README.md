# **Thank You Dana!  (Overview)**
***Note**:  If you're looking for an open source remake of the **arcade** version of Solomon's Key, see the [Open Solomon's Key](https://github.com/mdodis/OpenSolomonsKey) project.*

SKX is an open source port (with enhancements) of the 1986 Tecmo game Solomon's Key for the NES.  Graphics and sound effects are borrowed from the original,  however the code is completely fresh.   SKX is written in C# for .NET Core using the MonoGame (formerly XNA) framework for input, audio, and graphics and runs on Windows, Mac, and Linux.

**Features**
* Keyboard or gamepad input
* Automatic save feature using one of 8 save slots
* Easy, normal, and difficult modes
* Various levels of scale
* Multi-track dynamic music
* Fullscreen mode
* Classic mode -- the original 52 levels from the NES
* Classic+ mode -- the original 52 levels with added items and 20 new secret levels
* SKX mode -- a new set of 60 levels specifically designed with the new gameplay elements in mind
* New gameplay elements (see **New Gameplay Elements** below)
* Debug mode
* Integrated level editor

# **Usage**
SKX should run on any system that supports .NET core,  simply download the binary version of the game,  and either run **SKX.exe** (Windows), or run the command `dotnet skx.dll` from the appropriate directory.

Key/button bindings can be modified in the menu,  but the game comes with two sets of default controls for ease of use:

## **Default Controls (Arrows)**
| Binding | Keyboard | Gamepad |
|--|--|--|
| Up | Up Arrow | D-Pad Up
| Down | Down Arrow | D-Pad Down
| Left | Left Arrow | D-Pad Left
| Right | Right Arrow | D-Pad Right
| Magic | S | A button 
| Fireball | A | X button 
| Pause | Enter | Start button

## **Alternate Controls (WASD)**
| Binding | Keyboard | Gamepad |
|--|--|--|
| Up | W | D-Pad Up
| Down | S | D-Pad Down
| Left | A | D-Pad Left
| Right | D | D-Pad Right
| Magic | Right Shift | A button 
| Fireball | / | X button 
| Pause | Enter | Start button

# **Known Issues/Missing Functionality**

* Enemy UI needs some minor tweaking to be accurate to the original
* Dana's collision with the level might need some review
* Fairy UI is smoother but less accurate

# **A Note on Accuracy**
The goal of the project is to use NES-accurate physics and enemy behavior.  Any help correcting parameters to make the game behave more accurately is appreciated.  Most classes contain a section of (usually private) variables labelled "Behavioral Parameters" that can be adjusted to tweak the gameplay of those elements.

The mere act of implicitly removing technical limitations imposed by the NES changes the nature of the game.  Many rooms have slightly different enemy timimg as a result of the mere removal of lag and sprite limits.  

# **New Gameplay Elements**
## **New block types**
* **Frozen blocks** are items or empty space trapped in ice.  The ice can be melted by coming in contact with a fireball (either Dana's or an enemy's) or a Burns (flame enemy), or by picking up the **Blue Jar** which immediately melts all frozen blocks in the room.   Dana can stand on frozen blocks but cannot break them using magic.

* **Blue Doors** take Dana to a different part of the same room.   They must be opened first by finding a key.

## **New items**
| Item | Appearance | Reward |  
|:-----------:|:-----------:|-----------|  
| Super Medicine of Mapros | Blue bottle with an "E" on it | Rewards Dana with a 5-up. |  
| Copper Jewel | Red jewel | 5,100 points
| Opal Jewel | Rainbow jewel | 9,900 points
| Red Loot Block | Red diamond | 10,000 points,  or cast magic on it to switch between a Red Loot Block, Copper Jewel, Red Crystal of Rad, or Red Spell Jar |
| Red Spell Jar | Red-colored Jar of Magdora | Adds a death spell to Dana's scroll.  When used (using the Fireball button),  behaves identically to collecting a Red Medicine of Meltona |
| Red Crystal of Rad | Red and white crystal | Normally Dana can only shoot a fireball once all previous fireballs have been extinguished.  The Red Crystal of Rad increases Dana's capability to create simultaneously concurrent fireballs by one. |
| Red Medicine of Meltona | Jar filled with red liquid | Like the Orange Jar of Meltona (which kills Demonheads and Salamanders) but also kills Ghosts, Nuels, and Wyverns.
| Green Medicine of Meltona | Jar filled with green liquid | Like the Red Medicine of Meltona,  but also kills all Goblins, Wizards, and Panel Monsters
| Black Medicine of Meltona | Jar filled with black liquid | Quite rare-- immediately kills all enemies in the room
| Magdora Cocktail | Half-blue and half-orange Jar of Magdora | **Combination Item**: Adds both a super fireball and a regular fireball to Dana's scroll at the same time. |
| Time and Money | White Jar with Gold Jewel | **Combination Item**:  Same as collecting a full bottle of life (Medicine of Edlem) as well as a gold jewel at the same time.
| Scroll and Spell | Scroll and Blue Jar | **Combination Item**: Same as collecting a scroll and a fireball (Blue Jar of Magdora) at the same time. |
| Blue Medicine of Meltona | Jar filled with blue liquid | Immediately melts all ice/frozen blocks in the room 
| Hourglass of Peace | Purple/Pink Hourglass | Destroys all enemy-spawning mirrors
| Question Potion | Potion with a '?' | Executes room-specific functionality -- or maybe even nothing -- it's a mystery

## **New enemies**
* All enemies now come in four different speeds (Slow, Normal, Fast, and Faster).  The original had between 1-3 speeds depending on enemy type.
* Panel Monsters have a new variant (set the `Clockwise` flag), which breathe fire (like Dragons and Salamanders) when Dana or a brick is directly in front of them, instead of shooting fireballs periodically.

## **Miscellaneous Improvements (over the NES code)**
* The engine supports rooms larger than a single screen.   The camera will pan to follow Dana as he gets near the edge of the viewport if the room is larger than the current view.
* Rooms can have multiple doors (leading to different rooms or to the same room)
* Rooms can have multiple keys
* Keys can open multiple doors (if applicable)
* Rooms may contain more than two mirrors that spawn enemies
* Dana's starting position in a room may be influenced by which exit he used in the previous room.
* Rooms wrap vertically and horizontally -- just remove the walls.  (technically possible on the NES but not used in any actual rooms)
* Dynamic Audio -- Each room can have a different "Audio Effect" which manipulates the pan and fade of each of the tracks in the multitrack music as a function of dana's position, life remaining, etc.
* In game modes other than Classic, Dana can grow his scroll up to 18 slots (instead of 8).


## **Game Difficulty**
| Difficulty | Starting Lives | Scroll Size | Fireball Range
|--|--|--|--|
| Normal | 3 | 3 | 16 half-blocks
| Easy | 5 | 5 | 20 half-blocks
| Difficult | 3 | 1 | 16 half-blocks

## **Game Modes**
| Mode | Description |
|--|--|
| Classic | All 52 original levels with all of the original gameplay logic |
| Classic+ | All 52 original levels with new item types added, and 20 additional secret levels
| SKX | 60 new levels making use of all of the new gameplay elements

# **Debug Mode**
Debug mode is very helpful during development and gives the developer control over a number of settings that aide in game code development.
Activate debug mode by typing the letters "DEBUG" during the pause menu.

Once Debug Mode is active,  the following items will appear in the game's HUD:
* X and Y position of the selected object (defaults to Dana)
* X and Y velocity of the selected object (defaults to Dana)
* FPS based on the elapsed duration of the previous game tick
* Development variables A/B/C/D
* Status of Dana:
   * J - Jumping flag
   * F - Falling flag
   * O - On Floor flag
   * C - Crouching flag
   * U/D/L/R - Dana's collision detection in the up/down/left/right directions

## **Debug Controls**

The following additional key bindings will be active whenever the debug HUD is shown:
| Key | Unmodified Action | Action when Shift is held |
|--|--|--|
| F1 | Restart level | Restart game
| F2 | Increase life | 
| F4 | Switch story |
| F5 | Open all doors | Next room
| F6 | Turn off debug mode
| F7 | Pause game  |
| F8 | Run game while held |
| F9 | Single step frame by frame |
| F10 | Toggle collision view | Toggle selected game object for collision |
| F11 | Enter level editor (resets layout) | Enter level editor (preserves layout)
| F12 | Kill Dana | Time Over |
| U / H | Game Dev Variable A +/-
| J / I | Game Dev Variable B +/-
| K / O | Game Dev Variable C +/-
| L / P | Game Dev Variable D +/-
| M | Toggle music info
| V | Toggle inventory info
| S | Toggle spells info
| R | Toggle routine counters on objects
| T | Toggle timers on objects
| B | Toggle hit boxes | Toggle hurt boxes
| Y | Save Game Dev Variables

## **Collision View**
Press F10 to toggle **Collision View**.   When collision view is active,  the following additional information is drawn to the gameplay area:
* White rectangles representing game objects' hitboxes (collision area) (turn on with B key)
* A Yellow rectangle shows the hitbox of the game object currently selected for collision view
* Red rectangles representing game objects' hurtboxes (pain/damage area) (turn on with Shift+B)
* White number indicating the game objects' routine counter (turn on with R key)
* Wallhugger objects (Sparkies, Dana's fireballs, etc.) will show the current travel direction (U/D/L/R) as well as the direction in which they are hugging a wall (U/D/L/R). 
* Cyan dots indicating collision sensors
* Internal timer values (turn on with T key)
* Music tracker debug info (turn on with M key)

You can press Shift+F10 to cycle through the active game objects,  which displays their properties in the HUD.

Additionally,  the selected collision view object (which can be selected by using Shift+F10 to cycle through the active game objects) will replace the X/Y position and velocity displays in the HUD,  and the blocks the current object is colliding with will be tinted based on the sensor they are colliding with:

| Collision Sensor | Color |
|--|--|
| Left Center | Maroon |
| Left Upper | Pink | 
| Left Lower | Red |
| Right Center | Dark Blue |
| Right Upper | Light Blue |
| Right Lower | Blue |
| Down Center | Dark Green |
| Down Left | Light Green |
| Down Right | Green |
| Up Center | Orange | 
| Up Left | Gold |
| Up Right | Yellow |
| Object Center | Gray |

**Game Dev Variables** refer to four general purpose integer variables (`Game.DevA` through `Game.DevD`) that can be used during development of the game code to tweak parameters in real time without recompiling and restarting the game.    If `Y` is pressed, the contents of the variables is saved to `dev.json` and if this file exists at startup,  the contents of the variables are automatically loaded from this file.  If the file is not present,  the variables all default to zero.

# **Level Editor**
The Level Editor is invoked by pressing F11 when Debug Mode is active.   By default,  the layout of the current room is reloaded from disk,  but you can hold down shift to use the current layout (including any modifications made by Dana/enemies).   Press F11 again once in the editor to resume gameplay.   Pressing Shift+F11 while in the editor will start the room from the beginning,  including the titlecard and intro animations.

When a new room is loaded, the level layout (and thus all of the room's initial properties) are loaded from the game's embedded asset store,  however if a file named `room_xxx.json` exists in the current directory (where `xxx` is a room number,  optionally followed by `p` for Classic+ mode or `x` for SKX mode),  it is loaded instead of the embedded room layout.

Modified levels can be saved to the appropriate JSON file (in the current directory) by pressing F3.   Pressing Shift+F3 deletes this file (and thus reverts the room back to the stock layout included with the game).

## **Level Editor Modes**
The current mode is shown in the HUD at the top-left.   A description of these modes and the mode-specific controls is below.
| Key Binding | Mode | Description |
|--|--|--|
| L | Layout Mode | Used to edit blocks in the level layout
| B | Background Mode | Used to edit tiles in the room's background
| O | Object Mode | Used to edit the room's initial object placements
| K | Keys Mode | Used to link keys with doors
| D | Doors Mode | Used to edit destinations and other properties of doors 
| S | Spawns Mode | Used to edit the location and behavior of dynamic spawns (mirrors)
| M | Magic Mode | Used to edit room-specific magic triggers (like the original used in the Princess, Solomon, Page of Time, and Page of Space rooms)
| C | Camera Mode | Used to edit dynamic camera boundaries for large levels

## **Controls for all Modes**
The following controls work in all level editor modes:
| Key Binding | Description |
|--|--|
| F1 | Reset level and layout to the one on disk
| F3 | Save level to disk as `room_xxxy.json`
| Shift+F3 | Delete the level file on disk (restores the room to its stock layout)
| F4 | Room swap (prompts for room to swap with)
| Shift+F4 | Save as... (prompts for room number to save to)
| Ctrl+F4 | Copy room to... (prompts for story ID and room number to save to)
| F9 / Shift+F9 | Cycles through the **shrine** for the current room
| F7 | Increase room width by 1 column
| Shift+F7 | Decrease room width by 1 column
| F8 | Increase room height by 1 row
| Shift+F8 | Decrease room height by 1 row
| F10 | Lock camera (Camera is automatically locked for levels that are 17x14 or smaller)
| Shift+F10 | Unlock camera
| F11 | Resume gameplay (including changes made in the editor)
| Shift+F11 | Resume gameplay from disk (including title screen and intro animation)
| F12 | Next room (by number)
| Shift+F12 | Previous room (by number)
| Backspace | | Delete everything
| , | | Toggle mouse coordinate display

## **Level Mode**
Level mode is used to edit the grid cells that make up a room.   Each cell in the room can be empty or contain an item (cell type), and also has a modifier:
* **Normal** - Used for empty space, regular tan and gray blocks, and items that are visible for Dana to grab
* **Covered** - Used when an item is inside of a tan block.  If Dana breaks the block the item will become visible (Normal), unless Dana hits the block from below in which case the block will become Cracked.
* **Cracked** - The item is inside of a cracked tan block.   Dana can usually hit the block again from below to completely break the block (unless the item is a "hard" item like a key, door, mirror, bat, etc.)
* **Hideen** - The item is hidden and is treated as empty space unless Dana creates a block in this cell (in which case it turns into a Covered block,  and can then be broken to reveal the previously hidden item).
* **Frozen** - The item is encased in ice and must be freed into its Normal state with fire.

| Key | Mouse | Action |
|--|--|--|
| '/" | Mouse Wheel | Scroll through selected cell type
| Space | Middle Click | Cycle through cell modifiers (Normal, Covered, Cracked, Hidden, Frozen)
|  | Left Click | Draw selected cell type to the clicked location 
|  | Right Click | Pick up (like a dropper tool) the type of the clicked cell and set that as the selected cell type and modifier
| | Ctrl+Left Click | Fill a rectangle with the selected item (from the last clicked position to the position of the ctrl+click)
| ` (Tilde) | | Pulls open the cell picker
| / | | Select dynamic audio effect
| . | | Select music for level
| N | | Edit room name (optional)


## **Background Mode**
The Background Mode is used to modify the tiles that make up the background.   In the original (NES), the background was made up of a single tile that was tiled throughout the entire room,  plus an optional "motif" that was selected based on the current room's "shrine".   In SKX, the background can be made of any combination of tiles.

| Key | Mouse | Action |
|--|--|--|
| '/" | Mouse Wheel | Scroll through selected tile
| Space | Middle Click | Paste the current shrine's motif graphic at the current mouse position
|  | Left Click | Draw selected tile to the clicked location 
|  | Ctrl+Left Click | Fill a rectangle with the selected tile (from the last clicked position to the position of the ctrl+click)
|  | Right Click | Pick up (like a dropper tool) the tile of the clicked cell and set that as the selected tile
| ` (Tilde) | | Pulls open the tile picker
|   | Ctrl+Mouse Wheel | Changes the room's background color via list of presets
|   | Shift+Mouse Wheel | Changes R component of background color
|   | Ctrl+Shift+Mouse Wheel | Changes G component of background color
|   | Alt+Shift+Mouse Wheel | Changes B component of background color
| F | | Fills the entire room with the currently selected tile
| T | | Cycles the selected tile through the 3 "normal" tiles used in the original NES game (bricks, blocks, and stucco)

## **Object Mode**
Object mode is used to edit the initial placement of objects in the level (where everything starts off).

| Key | Mouse | Action |
|--|--|--|
|  | Left Click | Select an object
|  | Left Drag | Move an object
|  | Right Click | Deletes an object (if clicked on an object) or creates a new object (if clicked in empty space)
| Space | Middle Click | Toggles or cycles through the object's **direction**.  Some objects only have Left/Right directions,  others have Up/Down/Left/Right as valid directions.
| '/" | Mouse Wheel | Change the selected object's object **type**
| 1/2/3/4 | | Change the selected object's **speed** to 1, 2, 3 4
| 5 | | Toggles an enemy's **drops fairy** flag.  In the original NES game,  only object number 0 would drop a fairy (if it was killable).
| 6 | | Toggles an enemy's **drops key** flag.   Keys dropped by enemies act like an unconfigured key (opens all doors).
| 7 | | Toggles the **clockwise** flag for Sparkies (or makes Panel Monsters breath fire)
| 8 | | Toggles the **alternate graphics** flags.   Goblins become Wizards,  Ghosts becomes Wyverns,  Demonheads become weird looking demonheads.   In the original NES game this was done based on the ROM bank (based on the room's graphics skin) but in SKX this can be changed on a per-enemy basis.

## **Keys Mode**
Keys mode is used to link keys to doors.   Place keys and doors using layout mode first.
* Without any configuration,  a key will open every door in a room.
* Keys can be lined to one or more doors.
* When a room has multiple keys,  if every door that a key would have opened has already been opened,  the key will disappear.

| Key | Mouse | Action |
|--|--|--|
|  | Left Click on Key | Selects a key
|  | Left Click on Door | Toggles the selected key's link to that door
|  | Right Click on Key | Deletes all key links

## **Doors Mode**
Doors mode is used to configure door exits.  Place doors using layout mode first.

If a door is not configured, the following default logic is used when Dana enters the door:
* If Dana found a Golden Wing item in the current room,  Dana will be taken to the room defined by the current room's **Gold Wing Room** property.
* If Dana found a shrine (constellation symbol) in the current room,  Dana will be taken to the Game's **General Hidden** room (and then back to the current room's **Next Room** after that room is completed).
* If the door is a normal door,  Dana will be taken to the current room's **Next Room** property.
* If the door is a dark door,  Dana will be taken to the current room's **Next Secret Room** property.

Configured doors can have one of three exit types:
* Go to a specific room number.
* Go to a specific room number and start at a specific location.
* Warp to a specific location in the current room  (blue doors).

| Key | Mouse | Action |
|--|--|--|
|  | Left Click on Door | Selects a door
|  | Right Click on Door | Deletes door configuration
| Space | Middle Click | Toggle selected door's exit type
| x/X | | Adjust target X position +/- 
| z/X | | Adjust target Y position +/-
| q/Q | | Adjust next room number
| w/W | | Adjust golden wing room number
| e/E | | Adjust secret room number (used by dark doors or 'secret exit' spells)
| N | | Toggle room number sign above door
| F | | Toggle "fast stars" for exit  (alternate exit and intro animations)

## **Spawns Mode**

Spawns mode is used to configure the automatic enemy spawns (which typically occur from a Mirror of Camirror,  but don't really have to).

Each spawn point has a list of 1 or more items which will spawn (in the order listed) from that spawn point.   Use `[` and `]` to select which item in the list is being configured -- most of the same controls used in **Objects mode** applies to selected spawn list items.

Just like in the NES version,  each spawn point has two sets of flags (32-bit bitmasks) that dictate how often an enemy is spawned from that spawnpoint.  **Phase 1** timing is used as soon as a level begins, and **Phase 2** timing is used once Phase 1 ends, and is looped for the remainder of the level.   Timings restart after a player dies.  In the editor,  timings are indicated by the red and green dots and can be toggled by clicking on each dot (or using the 9/0 keys as noted below).

Each spawn point also has a **TTL** (time to live) which determines how long certain enemies (Demonheads and Salamanders) from that spawn point will live for until they disappear.

| Key | Mouse | Action |
|--|--|--|
|  | Left Click on Spawn | **Selects** a spawn point
|  | Right Click on Spawn | **Deletes** spawn point
|  | Right Click on Empty | **Creates** a spawn point
| + | | **Adds** an enemy to the end of the spawn list
| - | | **Removes** last enemy from the spawn list
| [ | | **Previous item** in the spawn list 
| ] | | **Next item** in the spawn list
| Space | Middle Click | Change **direction** of selected spawn list item
| '/" | Mouse Wheel | Cycle **type** of selected spawn list item 
| 1/2/3/4 | | Change **speed** of selected spawn list item
| 5 | | Change **drop fairy** flag of selected spawn list item
| 6 | | Change **drop key** flag of selected spawn list item
| 7 | | Change **clockwise** flag of selected spawn list item (Sparkies only)
| 8 | | Change **alternate graphics** flag of selected spawn list item
| z/Z | | Increase/decrease the **TTL** for spawn point
| 0 | | Clears all **timing** bits
| 9 | | Sets all **timing** bits
| Shift+9 | | Sets every 2nd **timing** bit
| Shift+0 | | Sets evert 4th **timing** bit

## **Camera Mode**

Camera mode is used to configure camera properties and dynamic resize routines.

When the level is larger than the screen, the camera is always in one of three modes:
* Locked -- It doesn't move
* Unlocked -- It moves to follow Dana
* LockedUntilNear -- The camera's locked but will unlock if Dana begins to move off the screen

When the camera is unlocked, **CameraBounds** determines how far the camera can scroll before
stopping.  By default CameraBounds is the same as the level bounds minus 8 pixels on the left and
right sides

Resize routines can be added to update the CameraBounds based on where Dana is located.  Any time Dana enters
one of the resize routine's trigger areas,  the associated boundaries will be set.  You should avoid overlapping
resize trigger areas.

| Key | Mouse | Action |
|--|--|--|
|  | Left Click | Sets rectangle top-left
|  | Right Click | Sets rectangle bottom-right
| '/" | Mouse Wheel | Select routine to edit
| Space | Middle Click | Toggle between editing routine trigger and routine bounds
| q | | Select initial camera mode
| + | | Add new resize routine
| - | | Delete selected resize routine

## **Magic Mode**
Magic mode is used to configure location specific triggers (**Spells**) that account for a lot of gameplay logic that was hard-coded into the original NES game.

* A spell may have a prerequisite of having an inventory item of a specific type from a specific room
* A spell may have a prerequisite of a previous spell being invoked (so that several triggers can be required for a specific action)
* When a spell is invoked it is added to Dainventory" so it can be referenced/checked in the future
* A spell can have one of several triggers and action types:

### **Triggers**
| Trigger | Description
|--|--|
| Immediate | The spell executes as soon as pre
| CastsMagic | The spell executes when Dana casts magic on the spell's location
| DanaTouches | The spell executes when Dana touches the spell's location
| Potion | The spell executes when Dana ingests a Question Potion
| HeadHit | The spell executes when Dana hits his head on the block at the spell's location

### **Types**
| Spell Type | Parameters | Behavior | Used in NES Rooms
|--|--|--|--|
| Change Cell | Position, Cell Type, Modifier, Animate | Changes the layout cell at a specific X/Y to a specific type and modifier.  If "Animate" is true, an effect is shown, otherwise the cell is changed without any fanfare.  Note that the "FAKECONCRETE" cell type can be used to make a block that Dana can break but still looks gray. | Solomon, Princess, Page of Time, Page of Space
| Spawn Object | Spawn ID | Spawns one or more objects from a specific spawn point.  You should create a spawn point in Spawns mode that has no timing bits set. | 17, 39
| Disable Scroll | None | Disable's Dana's scroll / ability to create fireballs | Solomon
| Enable Scroll | None | Re-enables Dana's scroll | None
| Secret Exit | None | Change the default room exit to the "secret" exit room number | 20, 44
| Random Cell | Position | Pulls a random item from the room's "random list" and changes the cell at the specified position to a **Covered** block with that item (and removes the entry from the "random list").  If no more items exist in the random list,  a normal tan block is used. | 52 (Hidden)

Controls used in Magic mode:

| Key | Mouse | Action |
|--|--|--|
|  | Left Click on Spell | **Selects** a spell
|  | Right Click on Spell | **Deletes** spell
|  | Right Click on Empty | **Creates** a spell
| Space | Middle Click | Change **type** of selected spell
| '/" | Mouse Wheel | Change **action** of selected spell
| q/Q |  | Adjust required inventory room number
| w | | Set required inventory cell type (opens cell picker)
| e/E | | Adjust required spell room number
| r/R | | Adjust required spell ID
| z/Z | | Adjust requirement count

Controls for action **Change Cell**:
| Key | Mouse | Action |
|--|--|--|
|  | Ctrl+Left Click | Set target cell location
| | Ctrl+Right Click | "Pick up" (like a dropper tool) the type and modifier to change the target cell to (the cell that's clicked can be changed once the information is picked up)
| A | | Toggle "animate" flag

Controls for action **Spawn Object**:
| Key | Mouse | Action |
|--|--|--|
|  | Ctrl+Left Click | Set target spawn point

Controls for action **Random Cell**:
| Key | Mouse | Action |
|--|--|--|
|  | Ctrl+Left Click | Set target cell location
|  | Ctrl+Right Click | "Pick up" (like a dropper tool) the type of a cell to add to the "random list"
| - (minus) |  | Removes the last item from the "random list"

# **Object Model**
| Class | Lifetime Coupled To| Purpose|
|--|--|--|
| **Game** | Application/Singleton | The main class that runs the game;  contains global properties applicable to the entire game. |
| **Sesh** | Game Save Slot | (Short for "session") Represents all the data that persists between rooms and (potentially) is saved to a save slot.  A default instance is created at startup and then replaced if an existing save slot is loaded from disk.
| **World** | (Abstract) | Base class that represents the current game mode.  `Game.World` is a reference to the current World.   Levels, Title Screens, and Menus inherit from World.
| **Level** | Room | Subclass of World that represents a currently running level in the game.  Includes the title screen, starting and ending animations, game over, time over, and "thank you dana" states.  Contains all properties/data related to the currently played level, including the currently active GameObjects (sprites).
| **GameObject** | (Abstract) | Base class for all game objects (Dana, Enemies, non-static pickups, special effects/animations).  Almost completely analogous to sprites in the NES code.
| **Layout** | Room Attempt | Represents the a level layout (both on disk including initial object placements,  as well as the currently active level layout being manipulated by Dana/enemies).  
| **ObjectPlacement** | Child of Layout | Used to define the starting position for a **GameObject** in a Layout
| **Spawn** | Child of Layout | Used to define a spawn point in a room's layout
| **SpawnItem** | Child of Spawn | Used to define an item in the list of enemies that are spawned from a **Spawn** point
| **Spell** | Child of Layout | Used to define a level-specific scripted behavior
| **KeyInfo** | Child of Layout | Configures key information
| **DoorInfo** | Child of Layout | Configures door information
| **InventoryItem** | Child of Sesh | When Dana collects an item that is used later in gameplay logic,  it is added to his "inventory".   This includes keys, constellation symbols, shrines, golden wings, pages of time/space, etc.   The item stores what room, and at what location in that room, it was collected.
| **Assets** | Application/Singleton | Holds the game's assets when loaded into memory |
| **Sound** (Static methods) | (Static) | Manages sound
| **Sound** (as an instance) | Application Lifetime | An instance of a loaded sound effect
| **MultiTrack** | Application Lifetime | (inherits Sound) An instance of a sound that plays multiple tracks in parallel
| **Track** | Application Lifetime | A single track in a MultiTrack sound; references the underlying sound as well as pan/fade controls
| **Control** | (Static) | Manages input (keyboard, mouse, gamepad)
| **Animation** | (Static) | Animation scripts
| **Resize** | Child of Layout | Dynamic camera resize routine
| **ExecutedSpell** | Child of Sesh | Goes into the Sesh once a spell has run so it can be detected later to compose complex logic conditions
