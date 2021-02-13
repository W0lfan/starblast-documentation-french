# Starblast Modding

**Note:** This is the GitHub version of the Official Documentation.

Official version can be found here: https://starblastio.gamepedia.com/Modding_Tutorial
<details>
  <summary markdown="span">Contents</summary>

1.  **[Information](#information)**
1.  **[Documentation and Tutorial](#documentation-and-tutorial)**
    1.  **[Important Notes](#important-notes)**
    1.  **[Creating your first mod](#creating-your-first-mod)**
    1.  **[Running and testing a mod](#running-and-testing-a-mod)**
        1.  **[Change region](#change-region)**
        1.  **[Start mod](#start-mod)**
        1.  **[Test the mod](#test-the-mod)**
        1.  **[ALWAYS keep the Mod Editor Tab being active while running the mod!](#always-keep-the-mod-editor-tab-being-active-while-running-the-mod)**
        1.  **[Stop the currently running mod](#stop-the-currently-running-mod)**
        1.  **[Other terminal commands](#other-terminal-commands)**
            1.  **[echo](#echo)**
            1.  **[clear](#clear)**
            1.  **[help](#help)**
    1.  **[Main code parts](#main-code-parts)**
        1.  **[Options](#options)**
            1.  **[Definition](#definition)**
            1.  **[Custom ships and custom tree](#custom-ships-and-custom-tree)**
            1.  **[Customizing the emote-chat system](#customizing-the-emote-chat-system)**
            1.  **[Custom asteroids maps](#custom-asteroids-maps)**
            1.  **[Survival mode specific options](#survival-mode-specific-options)**
            1.  **[Team mode specific options](#team-mode-specific-options)**
            1.  **[Deatmatch mode specific options](#deatmatch-mode-specific-options)**
        1.  **[Ticking](#ticking)**
            1.  **[Definition](#definition-1)**
        1.  **[Events](#events)**
            1.  **[General](#general)**
            1.  **[Available events](#available-events)**
    1.  **[Game step](#game-step)**
        1.  **[Definition](#definition-2)**
        1.  **[Unit](#unit)**
        1.  **[Uses](#uses)**
    1. **[Ships](#ships)**
        1.  **[Accessible fields](#accessible-fields)**
        1.  **[Configuration](#configuration)**
        1.  **[Instructor](#instructor)**
            1.  **[Calling instructor](#calling-instructor)**
            1.  **[Available characters](#available-characters)**
        1.  **[Custom UI components](#custom-ui-components)**
            1.  **[General](#general-1)**
            1.  **[Subcomponents' accepted options](#subcomponents-accepted-options)**
            1.  **[Combining with events](#combining-with-events)**
            1.  **[Customizing the scoreboard or radar](#customizing-the-scoreboard-or-radar)**
            1.  **[Global UI](#global-ui)**
        1.  **[Other methods and instances](#other-methods-and-instances)**
            1.  **[Remove all ship's secondary slots](#remove-all-ships-secondary-slots)**
    1.  **[Aliens](#aliens)**
        1.  **[Creation](#creation)**
        1.  **[Configuration](#configuration-1)**
    1.  **[Collectibles](#collectibles)**
        1.  **[Creation](#creation-1)**
        1.  **[Accessing](#accessing)**
    1.  **[Asteroids](#asteroids)**
        1.  **[Creation](#creation-2)**
        1.  **[Configuration](#configuration-2)**
    1.  **[Add 3D objects to the scenery](#add-3d-objects-to-the-scenery)**
        1.  **[Object type options](#object-type-options)**
        1.  **[Object instance options](#object-instance-options)**
        1.  **[Accessing](#accessing-1)**
        1.  **[Changing or moving an object](#changing-or-moving-an-object)**
        1.  **[Removing an object](#removing-an-object)**
        1.  **[Example](#example)**
    1.  **[Reading game's detailed options](#reading-games-detailed-options)**
        1.  **[Accessing](#accessing-2)**
        1.  **[Accessible fields](#accessible-fields-1)**
        1.  **[Team mode specific accessible fields](#team-mode-specific-accessible-fields)**
    1.  **[Assigning custom properties to some entities/objects](#assigning-custom-properties-to-some-entitiesobjects)**
        1.  **[Accessing and assigning](#accessing-and-assigning)**
        1.  **[Supported objects/entities](#supported-objectsentities)**
        1.  **[Example](#example-1)**
    1.  **[Other game instances and methods](#other-game-instances-and-methods)**
        1.  **[Set custom maps in-game](#set-custom-maps-in-game)**
        1.  **[Lock/unlock the mod from attracting new players](#lockunlock-the-mod-from-attracting-new-players)**
    1.  **[Common problems and how to fix them](#common-problems-and-how-to-fix-them)**
        1.  **[Black screen issue](#black-screen-issue)**
        1.  **[My mod closed accidentally but the game is not stopped](#my-mod-closed-accidentally-but-the-game-is-not-stopped)**
1.  **[Community resources](#community-resources)**
    1.  **[Tutorial and Documentation](#tutorial-and-documentation)**
    1.  **[Tools](#tools)**
    1.  **[Code resources](#code-resources)**
</details>

## Information
![Standard Modding Interface, you can see the minimap of the mod in the bottom right corner while the mod is running](https://raw.githubusercontent.com/Bhpsngum/img-src/master/ModdingInterface.png)

*Standard Modding Interface, you can see the minimap of the mod in the bottom right corner while the mod is running*


Starblast Modding interface can be found here: https://starblast.io/modding.html ([ECP](https://starblastio.gamepedia.com/Elite_Commander_Pass) required)


Starblast Modding interface allows you to create custom mods for Starblast. The interface is made of a code editor window, on the left, and a console window, on the right. The code editor is where you type the JavaScript code for your mod. The console is where you can type commands to start your mod, stop it or interact with it while it is running.


Main programming language uses in this interface is [JavaScript (ECMAScript)](https://www.w3schools.com/js/DEFAULT.asp)

## Documentation and Tutorial
### Important Notes
In newer version of browsers' updates, you can't use the Modding Client in incognito mode anymore as they restrict some incognito features which are used by the editor.

And make sure to read all of these from the start to the end so that you won't miss any important info!

### Creating your first mod
In the Mod Code window, type the code for your first mod:
```js
this.options = {
  root_mode: "survival",
  map_size: 30
};

this.tick = function(game) {
};
```

### Running and testing a mod
#### Change region
Once your mod code is ready, in the console, start by selecting your preferred region for modding using the command `region <region name>`. For example with Europe:
```
> region Europe
Region set to Europe
> █
```
(Currently modding is only available in these 3 zones: Europe, America, Asia)
#### Start mod
Then to start running your mod, type command `start`:
```
> start
Mod started
https://starblast.io#1234@12.34.56.78:2000
Use 'test' to open game frame for testing
> █
```
#### Test the mod
As instructed by the console, you may want to open a test window to join your modded game with a Starblast client. Type `test`:
```
> test
> █
```
#### ALWAYS keep the Mod Editor Tab being active while running the mod!
This is one of the most important things you need to keep in your mind!

Why? Because that's nuances of how browsers work.

Browsers slow down all javascript in non-active tabs in order to decrease the CPU processes.

For some mods (e.g Battle Royale), it doesn't matter like with ship tree and options only,

but for other mods where some logic in tick function or events - it will affect them A LOT!

Ticks start to work slower and slower...

Soon everything will be lagging in game, like any reactions on mod buttons, any mod logic like spawning something in tick, etc.

And... depending on mod complexity it can just CRASH THE ENTIRE MOD - locally, server will continue to work so game will work but without mod logic anymore.

So, always keep the mod editor tab online or you will have unpredictable results!

Also, you need to have a stable internet connection if you don't want your mods becoming laggy.

#### Stop the currently running mod
You can stop your mod anytime by using command `stop`. Note that this will kill the game and disconnect all connected players:
```
> stop
Mod stopped
> █
```
#### Other terminal commands
##### `echo`
Print any values to the terminal, can be used in both mod code (after mod started) and terminal

Syntax: `echo(<item>)`
```
> echo("Message from terminal!")
Message from terminal!
> █
```
##### `clear`
Clear the the terminal, only available in terminal

Syntax: `clear`
##### `help`
Display help message inside the terminal, terminal use only

Syntax: `help`

### Main code parts
#### Options
##### Definition
Stored in `this.options` is a data structure where you can set options for your custom, modded game. These options are used for initializing the game when you start your mod. Changing them while the mod is running does not affect the game.
##### Custom ships and custom tree

You can import ships made with Starblast Ship Editor. In the Ship Editor, use "Mod Export" feature to export a JavaScript code snippet for the modding interface. Then paste this snipped in the coding window and add this:
```js
var myship_101 = "{ … … <this is your exported ship code> …";

var ships = [myship_101]; // add your ship to an array of ship

this.options = {
  root_mode: "survival",
  ships: ships,         // specifying a list of ships to complement / replace existing ships
  reset_tree: true,     // set to true if you want to remove the original ship tree, false if you just want to replace some of the ships
  map_size: 30
};

this.tick = function(game) {
};
```
Then run your mod. If your ship is set to level=1 model=1, your ship will replace the Fly. You can replace other ships in the tree in a similar way, using `reset_tree: false`. Or you can remove the original ship tree completely and provide a whole new one using `reset_tree: true`.
##### Customizing the emote-chat system
The vocabulary used for the emote-chat system can be customized by setting the field `vocabulary` in the game option
as follows:
```js
var vocabulary = [
      { text: "Hello", icon:"\u0045", key:"O" },
      { text: "Bye", icon:"\u0046", key:"B" },
      { text: "Yes", icon:"\u004c", key:"Y" },
      { text: "No", icon:"\u004d", key:"N" },

      { text: "Flower", icon:"\u{1F33B}", key:"F" },
      { text: "Snowman", icon:"\u26c4", key:"M" },
      { text: "Shark", icon:"\u{1F988}", key:"S" },
      { text: "Ghost", icon:"\u{1F47B}", key:"G" }
    ] ;

this.options = {
  vocabulary: vocabulary,
  // ...
};
```
This allows using Starblast built-in emote icons, which are listed here for reference: https://starblast.io/glyphs.html

You can also use unicode icons, here is a good source for reference: https://unicode.org/emoji/charts/full-emoji-list.html

Note that wide unicode characters (using more than 2 bytes) require a specific Javascript syntax as shown in the example above (example: `\u{1F47B}`)

##### Custom asteroids maps
You can create a custom map of asteroids. This allows creating a maze for example. The custom map you provide is actually a JavaScript character string which is used to "paint" the map.

For example:
```js
var map =
"999999999999999999999999999999\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"99                          99\n"+
"999999999999999999999999999999" ;


this.options = {
  custom_map: map,
  map_size: 30
}
```

In the example above, 9 sets the biggest size of asteroid. You can use smaller values for adding smaller asteroids to the grid. Any value other than a digit will be interpreted as no asteroid. If your `map_size` is set to 30, make sure to create 30 lines and 30 columns, or you may get unpredictable results.

**Note:** Use `""` for blank custom map

You can use [Online Map Editor](https://bhpsngum.github.io/starblast/mapeditor/) (a community tool) to create, edit and export maps.

##### Other common options
Most of the options are inherited from the usual custom games. A few more options have been added, specifically for modding (top of the list):
| Option | Description | Default value<br>(if omitted) |
| - | - | - |
| root_mode | The mod to inherit from: "survival", "team", "invasion", "deathmatch", "battleroyale" (or unspecified) | Unspecified |
| reset_tree | Set to true to remove the original ship tree | false |
| ships | An array of ships to add to the tree | None |
| map_size | Size of the map, range from 20 to 200 | 100 (survival)<br>80 (team and Battle Royale)<br>60 (unspecified)<br>30 (Invasion)<br>20 (deathmatch) |
| soundtrack |"procedurality.mp3", "argon.mp3", "crystals.mp3", "red_mist.mp3, "civilisation.mp3" or "warp_drive.mp3" | None |
| max_players | From 1 to 240 | 70 (team)<br>60 (survival)<br>40 (unspecified)<br>30 (Battle Royale)<br>20 (deathmatch)<br>6 (invasion) |
| crystal_value | Float, from 0 to 10 | 2 (team)<br>0 (deathmatch and Battle Royale)<br>1 (others) |
| lives | Number of lives, from 1 to 5 | 4 (team)<br>1 (deathmatch and Battle Royale)<br> 3 (others) |
| max_level | Max level you can reach, from 1 to 7 | 7 |
| friendly_colors | Serves to define teams; how many teams (or 0) | 3 (team)<br>1 (invasion)<br>0 (others) |
| map_name | Name of the map | Auto-generated name |
| survival_level | Level which triggers survival mode (8 for no trigger) | 7 (survival)<br>8 (others) |
| starting_ship | Enter desired ship code: 101, 201, 404, etc. | 101 |
| starting_ship_maxed | true or false | false |
| asteroids_strength | 0 to 10 | 5 (deathmatch)<br>0.5 (Battle Royale)<br>1 (others) |
| friction_ratio | 0 to 2 | 1 |
| strafe | strafing speed factor, an integer from 0 to 1 | 0 |
| speed_mod | 0 to 2 | 1.25 (deathmatch)<br>1.2 (survival and team)<br>1 (others) |
| rcs_toggle | true or false | true |
| map_id | Number in the range [0-9999] | Game id |
| map_density | Density of the map | None |
| weapon_drop | 0 to 1 (probability that an asteroid will drop a weapon) | 0 |
| crystal_drop | percentage of gems can be collected when a ship drain gems | 0.5 (deathmatch)<br>1 (others) |
| release_crystal | true/false for allowing/forbidding `[V]` to release gems | true (team)<br>false (others) |
| mines_self_destroy | true or false | true |
| mines_destroy_delay | all landed mines will be destroyed after this interval if no enemies triggered the mines (in [ticks](#unit)) | 3600 (Battle Royale)<br>18000 (others) |
| healing_enabled | true or false | true (team)<br>false(others) |
| healing_ratio | 0 to 2 | 1 |
| shield_regen_factor | 0 to 2 | 1 |
| power_regen_factor | 0 to 2 | 1 |
| weapons_store | Set to false to remove access to the weapon store | true |
| radar_zoom | Set value to 1, 2 or 4 | 2 |
| auto_refill | When set to true, collecting an energy or shield pill immediately refills energy or shield ; the collected pill is not added to the active weapons | false |
| projectile_speed | Affects the speed of rockets, missiles and torpedoes; use 1 for default speed | 1 |
| choose_ship | e.g. setting to `[301,302,303]` will let player choose a ship from these 3 ships before entering the game | None |
| collider | enable/disable (true/false) collisions of player ships with anything | true |


##### Survival mode specific options
| Option | Description | Default value<br>(if omitted) |
| - | - | - |
| survival_time | When to trigger survival mode; 0 or a value in minutes | 60 |


##### Team mode specific options
| Option | Description | Default value<br>(if omitted) |
| - | - | - |
| hues | array of hue numbers for teams, with the same amount of elements as used for `friendly_colors` | Auto-generated hues |
| station_regeneration | factor to apply to station shield regen | 1 |
| station_size | size of the stations; integer from 1 to 5 | 2 |
| station_crystal_capacity | factor to apply to the station crystal capacity, range [0.1,10] | 1 |
| station_repair_threshold | part of the station crystal capacity that must be refilled to repair a module. In the range [0,1] | 0.25 |
| auto_assign_teams | allow assigning players to a specific team (true) or let them choose the team themselves (false) | false |

##### Deatmatch mode specific options
| Option | Description | Default value<br>(if omitted) |
| - | - | - |
| ship_groups | an array containing some arrays, each of them representing one ship group (by name) available for selection<br>See the example below.<br>The longer the array is, the lower chance for each ship group being available in a single match | See [Deathmatch](https://starblastio.gamepedia.com/Deathmatch) for a list of default ship groups<br>**Note:** The mod won't run if `reset_tree` option is set to true |

Example:
```js
ship_groups: [
  ["U-Sniper","Howler"],
  ["Crusader","Pioneer"]
]
```
#### Ticking
##### Definition
Found in `this.tick` is a JavaScript function which is called 60 times per second. In this function’s body, you will be able to code specific actions that your mod needs to take automatically while the game is running. This function can be modified while the modded game is running and the changes will apply automagically.
#### Events
##### General
Your mod can receive events through the function `this.event`:
```js
this.event = function(event,game) {
  switch (event.name)
  {
    case "ship_spawned":
      if (event.ship != null)
      {
        shipJustSpawned(event.ship) ;
      }
      break ;
  }
} ;
```

##### Available events
| Event name | Description | Additional event fields |
| - | - | - |
| ship_spawned | A ship just spawned in game or respawned | event.ship |
| ship_destroyed | A ship was just destroyed | event.ship, event.killer |
| alien_destroyed | An alien was just killed | event.alien, event.killer |
| asteroid_destroyed | An asteroid was just destroyed | event.asteroid, event.killer |
| collectible_picked | A ship just picked a collectible item | event.collectible, event.ship |
### Game step
#### Definition
Can be accessible through `game.step`, is an integer presenting game's duration
#### Unit
The unit of this value is tick, where 1 tick = 1/60 seconds

Which means that 60 ticks = 1 second, 120 ticks = 2 seconds and so on.
#### Uses
This code uses to set the first ship in the list to the center of the map in the first minute of the mod and reset its crystals every 5 seconds (assume that there is one ship staying from the start of the mod):
```js
this.tick = function (game)
{
  if (game.step == 3600) { // 1 minute = 60 seconds * 60
    game.ships[0].set({x:0,y:0}); // Center teleport
  }
  if (game.step % 300 === 0) { // 5 seconds * 60
    game.ships[0].set({crystals: 0}); // Reset crystals
  }
}
```

### Ships
You can access to the list of ships (players) through the array `game.ships`

You can also find a ship with specific id using `game.findShip(id)`, which returns an object represent the matched ship or `null` (if there are no ships matching the provided id)
#### Accessible fields
You have read access to the ship’s main fields and options:
| Field | Description |
| - | - |
| x | X coordinate |
| y | Y coordinate |
| vx | Velocity vector X component |
| vy | Velocity vector Y component |
| r | Rotation angle of the ship (in radian) |
| name | player's name |
| alive | Whether the ship is alive or destroyed |
| type | Ship type code (e.g. 101) |
| stats | Ship current stats upgrades, compiled into a single integer.<br>For example: 10012301 means the 8 stats upgrade levels are 1,0,0,1,2,3,0 and 1 |
| idle | tells if the ship is in idle status or not |
| team | the id of the team this ship is in |
| score | player's score |
| shield | current shield value |
| generator | current generator value |
| crystals | current crystals value |
| healing | whether the ship's lasers are in healing mode or not |

#### Configuration
You can set different options on the ships. For example:
```
> game.ships[0].set({x:0,y:0});
> █
```
Will move the first ship in the list to the center of the map

List of accepted options when using `ship.set`:
| Option | Description | Server response error message<br>(if improper) |
| - | - | - |
| x | X coordinate | Wrong coordinate |
| y | Y coordinate | Wrong coordinate |
| vx | Velocity vector X component | Wrong coordinate |
| vy | Velocity vector Y component | Wrong coordinate |
| invulnerable | Use to set the ship invulnerable for X ticks (e.g. 60 for one second invulnerability) | Wrong invulnerable time |
| type | changes the type of ship (use the ship code, e.g. `{type:403}` ) | None |
| angle | changes the direction the ship is facing | Wrong angle |
| score | sets player's score | Wrong score |
| idle | set to true to force the ship to stay idle (and false to revert) | None |
| shield | sets the value of the shield | Wrong shield value |
| generator | sets the value of the generator | Wrong generator value |
| healing | sets ship's lasers mode to healing (true or false) | None |
| crystals | sets ship's crystal ammount | Wrong crystals |
| stats | sets the stats upgrades of the ship | None |
| kill | Set `kill: (any "truthy" value, e.g: true)` to destroy the ship | No violation |
| team | Changes the team this ship belongs to (in range [0-X] where X is teams - 1) | None |
| hue | Sets the color of the ship (range [0-359])![Hue map](https://i.stack.imgur.com/YOBFy.png) | None |

#### Intermission
You can send the ship to intermission (a screen with results, offering to respawn). This screen allows you to display custom results information:
```
> game.ships[0].intermission({"Best Achievement":"Managed to run the mod","Score":1234});
> █
```
#### Triggering and Customizing player's GameOver screen
You can also trigger the gameover screen for any given ship. Here again, you can pass results information to pass on to the player:
```
> game.ships[0].gameover({"Rating":"Can do better","Score":1234});
> █
```
#### Instructor
##### Calling instructor
You can have the flight instructor send instructions to the player. For this find the players’s ship and use:
```
> ship.instructorSays("Hello!")
> █
```
You can hide the instructor window using:
```
> ship.hideInstructor()
> █
```
You can later show it again using:
```
> ship.showInstructor()
> █
```
A second, optional parameter allows you to choose which one of the instructor characters will talk to the player. Example:
```
> ship.instructorSays("Here is your report, Commander","Maria")
> █
```
##### Available characters
|Lucina|Klaus|Maria|Kan|Zoltar|
|-|-|-|-|-|
|![Lucina](https://starblast.data.neuronality.com/img/tutorial-survival.png)|![Klaus](https://starblast.data.neuronality.com/img/tutorial-battleroyale.png)|![Maria](https://starblast.data.neuronality.com/img/tutorial-team.png)|![Kan](https://starblast.data.neuronality.com/img/tutorial-invasion.png)|![Zoltar](https://starblast.data.neuronality.com/img/tutorial-deathmatch.png)|

#### Custom UI components
##### General
The mod can create custom UI components that will show up on the player’s screen. This is done by calling `setUIComponent` on the ship, passing in a component descriptor.

For example:
```
> ship.setUIComponent({
    id:"myid",
    position:[0,0,25,25],
    clickable: true,
    shortcut: "X",
    visible: true,
    components: [
      { type:"box",position:[0,0,100,100],fill:"#456",stroke:"#CDE",width:2},
      { type: "text",position: [0,0,100,50],color: "#FFF",value: "My Text"},
      { type: "player",id: 1, position: [0,0,50,50],color: "#FFF"},
    ]
  })
> █
```
Here is the list of UIComponent's accepted options:
| Option | Description | Default value<br>(if omitted) |
| - | - | - |
| id | a unique identifier for this component, mandatory | None |
| position | expressed in percentage of the main screen, the position of the component [x,y,width,height]. Example: [45,45,10,10] creates a component in the center of the screen, which width and height are 10% of the screen width and height. | None |
| visible | Whether the component is visible or not. Resend the same data with visible set to false to hide the component | true |
| clickable | Whether this component can be clicked or not | false |
| shortcut | When the component is clickable, a keyboard shortcut allowing to trigger the click event | None |
| components | gives a list (array) of graphical features to render within the component, which will be described below | Empty array |

##### Subcomponents' accepted options
| Option | Description | Default value (if omitted) |
| - | - | - |
| type | type of the subcomponents<br>currently supported: "round", "text", "box" or "player" | None |
| id ("player" type only) | id of the player associated with the subcomponent, which will be disapleyd as their name and badge (if exists) in the rendered subcomponent | None |
| position | positions of the subcomponents, formatted as `[x,y,width,height]`<br>these subcomponents are meant within the main component coordinates | None |
| value | value of the subcomponent, e.g `value:"Sample text"` | Empty string |
| color | text color of the subcomponent, this can be a string with any color formats (hex, hsla, rgb, etc.), e.g `"#fff"` | None |
| fill | background color of the subcomponent, same format as the `color` property | None |
| width | width of the subcomponent's border (in percent) | 0 |
| stroke | border color of the subcomponent, same format as the `color` property | None |
| align | alignment of the texts inside the subcomponent<br>"left", "right" or "center" only | `"center"` |

##### Combining with events
The example below creates a warp button for every player, which can be clicked and results in the ship warping to another random location, also adding 3 seconds invulnerability to it:

Full example: https://github.com/pmgl/starblast-modding/blob/master/examples/warp_button.js
```js
var warp_button = {
  id: "warp",
  position: [2,50,8,14],
  clickable: true,
  shortcut: "W",
  visible: true,
  components: [
    { type:"round",position:[0,0,100,100],fill:"#456",stroke:"#CDE",width:2},
    { type: "text",position:[10,35,80,30],value:"WARP",color:"#CDE"},
    { type: "text",position:[20,70,60,20],value:"[W]",color:"#CDE"}
    ]
};

var warpShip = function(ship) {
  x = (Math.random()-.5) * ship.game.options.map_size*10 ;
  y = (Math.random()-.5) * ship.game.options.map_size*10 ;
  ship.set({x:x,y:y,vx:0,vy:0,invulnerable:180}) ;
} ;

this.tick = function(game) {
  if (game.step%60==0) // ensure this is done only once per second
  {
    for (var i=0;i<game.ships.length;i++)
    {
      var ship = game.ships[i] ;
      if (!ship.custom.warp_button_installed)
      {
        ship.custom.warp_button_installed = true;
        ship.setUIComponent(warp_button);
      }
    }
  }
} ;

this.event = function(event,game) {
  switch (event.name)
  {
    case "ui_component_clicked":
      var ship = event.ship ;
      var component = event.id ;
      if (component == "warp") // check that this is our component "warp"
      {
        warpShip(ship);
      }
      break ;
  }
} ;
```

##### Customizing the scoreboard or radar
The built-in scoreboard can be replaced by your own custom scoreboard component. As soon as an UI component with id `"scoreboard"` or `"radar_background"` is created, you will be responsible for updating the scoreboard/radar. Your custom scoreboard/radar component does not have to include a `position` because it will automatically fill the area already reserved for the perspective UI Component.

##### Global UI
You can use `game.setUIComponent({ options })` to set the UI to all current players in the game

#### Other methods and instances
##### Remove all ship's secondary slots
Syntax: `ship.emptyWeapons()`

### Aliens
Vous pouvez accéder à la liste des extraterrestres par le array `game.aliens`

Vous pouvez aussi trouver un extraterrestre avec une id spécifique en utiliant `game.findAlieb(id)`, qui va renvoyer l'object représentant l'extraterrestre demandé, ou `null` s'il n'y a aucun extraterrestre avec l'id demandée.

#### Création
Pour créer un extraterrestre, utilisez `game.addAlien({ options })`
Listes des options acceptées:

(Note: Le serveur va répondre par `Incorrect data` si au moins une de ces valeurs est fausse)
| Option | Description | Valeur par défaut (si omis) |
| - | - | - |
| x | Coordonnées X | 0 |
| y | Coordonnées Y | 0 |
| vx | Vitesse dans une direction X | 0 |
| vy | Vitesse dans une direction Y | 0 |
| code | Type d'extraterrestre, le nombre doit être entre [10-20] | 10 |
| level | Niveau d'un extraterrestre, entre [0-X] où X dépend du type d'extraterrestre | 0 |
| points | Le nombre de points que va donner l'extraterrestre une fois tué | None |
| crystal_drop | Le nombre de cristaux que va lâcher l'extraterrestre une fois tué | None |
| weapon_drop | Le code d'une arme secondaire qui peut être lâchée par un extraterrestre quand il est tué | None |

Voici la liste des codes d'extratrrestres (eliens) disponibles:
| Code | Nom de l'extraterrestre |
| - | - |
| 10 | Chicken |
| 11 | Crab |
| 12 | Fortress |
| 13 | Alien bizarre |
| 14 | Candlestick |
| 15 | Hirsute |
| 16 | Piranha |
| 17 | Pointu |
| 18 | Fork |
| 19 | Saucer |
| 20 | Final Boss |

Un nouvel object `Alien`est immédiatement ajouter à `game.aliens` ; cependant, il ne peut pas être utilisé avant que le serveur ait assigné une id (nombre positif) à cet extraterrestre.
#### Configuration
Une fois que le premier extraterrestre (alien) est en vie et qu'il a une id assignée, vous pouvez le modifier avec des options. Par exemple:
```
> game.aliens[0].set({x:0,y:0});
> █
```
Cela va faire bouger le premier extraterrestre de la liste au centre de la carte.

Accepted options when using `alien.set`:
| Option | Description |  Réponse du serveur si erreur<br>(if improper) |
| - | - | - |
| x | Coordonnées X | Wrong coordinate |
| y | Coordonnées Y | Wrong coordinate |
| vx | Vitesse dans une direction X | Wrong coordinate |
| vy | Vitesse dans une direction Y | Wrong coordinate |
| shield | Bouclier | Wrong shield value |
| regen | Régénration du bouclier | Wrong regen value |
| damage | Laser damage | Wrong damage value |
| laser_speed | Rapidité du laser | Wrong damage value |
| rate | Nombre de tirs par seconde | Wrong rate value |
| kill | Utilisez `kill: (any "truthy" value, e.g: true)` pour détruire une extraterrestre (alien) | No violation |

### Armes secondaires
Vous pouvez faire apparaitre des armes secondaires dans le champ de jeu.

Vous pouvez aussi trouver une arme secondaire avec une id spécifique en utiliant `game.findCollectible(id)`, qui va renvoyer l'object représentant l'arme secondaire demandée, ou `null` s'il n'y a aucune arme secondaire avec l'id demandée.

#### Création
Voici un exemple:
```
> game.addCollectible({code:10,x:0,y:0});
> █
```
Cela va ajouter une nouvelle arme secondaire (1 pack de 4 rockettes) aux coordonnées (0;0)

Voici la liste des codes d'armes secondaires disponibles:

(Note: Le serveur va répondre par `Incorrect data` si au moins une de ces valeurs est fausse)
| Code | Description |
| - | - |
| 10 | 1 pack de 4 rockettes |
| 11 | Un pack de deux missiles |
| 12 | 1 torpille |
| 20 | Un pack de 8 mines légères |
| 21 | Un pack de 4 mines lourdes|
| 40 | Pod de minage |
| 41 | Pod d'attacque |
| 42 | Pod de défense |
| 90 | Recharge de l'énergie (barre jaune)|
| 91 | Recharge du bouclier |

#### Accès
Vous pouvez voir les armes secondaires toujours disponibles à collecter dans le champ de jeu en utilisant: `game.collectibles`.

### Astéroïdes
Vous pouvez accéder à la liste des astéroïdes qui bougent par le array `game.asteroids`.

Vous pouvez aussi trouver un astéroïde avec une id spécifique en utilisant `game.findAsteroid(id)`, ce qui va renvoyer un object qui représente l'astéroîde voulut, ou `null` si il n'y a pas d'astéroïdes avec l'id donnée.

#### Création
Pour créer un astéroïde, utilisez `game.addAsteroid({ options })`.

Voici la liste des options acceptées:

(Note: Le serveur va répondre par `Incorrect data` si au moins une de ces valeurs est fausse)
| Option | Description | Valeur par défaut<br>(Si omis) |
| - | - | - |
| x | Coordonnée X | 0 |
| y | Coordonnée Y | 0 |
| vx | Vitesse de l'astéroïde dans une direction X | 0 |
| vy | Vitesse de l'astéroïde dans une direction Y | 0 |
| size | La taille de l'astéroide, pour un nombre entre [1-100] | 30 |

Un nouvel `Asteroid` est un objet qui est immédiatement ajouté à `game.asteroids` ; cependant, il ne peut pas être utilisé sans qu'une id ne lui ait été assignée (nombre positif) par le serveur.

#### Configuration
Une fois qu'un astéroïde est "en vie" et qu'il détient une id qui lui est assignée, vous pouvez lui apporter des modifications. Par exemple:
```
> game.asteroids[0].set({x:0,y:0});
> █
```
Ceci va faire bouger le premier astéroïde de la liste des astéroïdes et va l'emmener au centre de la carte.

Listes des options acceptées lorsque `asteroid.set` est utilisé:
| Option | Description | Réponse du serveur si erreur<br>(if improper) |
| - | - | - |
| x | coordonnée X  | Wrong coordinate |
| y | coordonnée Y  | Wrong coordinate |
| vx | Composante X du vecteur vitesse | Wrong coordinate |
| vy | Composante Y du vecteur vitesse | Wrong coordinate |
| size |La taille d'un astéroîdes, entre [1-100]<br>(notez que changer la taille d'un astéroïde lui permet de "régénérer" sa vie) | Incorrect size |
| kill | Utilisez `kill: (any "truthy" value, e.g: true)` Pour détruire un astéroide | No violation |

### Ajouter des objets en 3D dans l'arrière plan/le premier plan
Votre mod peut créer des objets 3D customisées, avec des textures, et les ajouter à l'arrière plan/premier plan, en utilisant `game.setObject`. Ces objets n'ont pas de masse physique pour le moment (la masse physique est planifiée pour un futur proche).

Par exemple:
```js
var cube = {
  id: "cube",
  obj: "https://raw.githubusercontent.com/pmgl/starblast-modding/master/objects/cube/cube.obj",
  diffuse: "https://raw.githubusercontent.com/pmgl/starblast-modding/master/objects/cube/diffuse.jpg"
} ;

game.setObject({
  id: "cube",
  type: cube,
  position: {x:0,y:0,z:0},
  rotation: {x:0,y:0,z:0},
  scale: {x:1,y:1,z:1}
}) ;
```

#### Object type options
| Option | Description |
| - | - |
| id | Un élément unique à l'objet qui permet de l'identifier (obligatoire, car il permet de modifier l'objet: coordonées, etc) |
| obj | un lien (HTTPS) qui mène au fichier (OBJ) |
| type | Object instance options, see the section below for more details |
| diffuse | a URL (HTTPS) to a diffuse texture file (optional) |
| emissive | a URL (HTTPS) to an emissive texture file (optional) |
| specular | a URL (HTTPS) to a specularity texture file (optional) |
| bump | a URL (HTTPS) to a bump texture map (optional) |
| diffuseColor | diffuse color of the object, e.g. 0xFF0000 (for red) |
| emissiveColor | emissive color of the object, e.g. 0x00FFFF (for cyan) |
| specularColor | specular color of the object |
| transparent | Si la texture de l'objet est transparente ou pas |
| bumpScale | scale for bump mapping (default: 0.1) |

#### Options de l'objet
| Option | Description |
| - | - |
| id | Un élément unique à l'objet qui permet de l'identifier (obligatoire, car il permet de modifier l'objet: coordonées, etc)|
| type | Le type d'objet |
| position | Coordonnées pour placer l'objet |
| scale | Permet de mettre l'objet à une certain échelle |
| rotation | Permet de faire effectuer une rotation à l'objet |
| shape | Forme de l'objet (utilisée pour créer les boites de collisions<br>**Note:** Il est conseillé de ne pas utiliser, car elle ne fonctionne pas comme elle devrait fonctionner|
#### Accés
Le propriété `game.objects` garde tous les objets en 3d que le mod contient.
Vous ne devriez pas modifier cette propriété, afin de faire en sorte que votre mod fonctionne doucement.

#### Changer ou faire bouger un objet
Utilisez encore `game.setObject` avec l'id de l'objet.

#### Supprimer un objet
`game.removeObject(id)` supprime l'objet avec une id donnée. Vous pouvez ommetre le paramètre 'id', ce qui supprimera tous les objets customisés dans l'arrière plan.
#### Exemple
Exemple qui marche: ajouter des cubes (objet) dans l'arrière plan en jeu: https://github.com/pmgl/starblast-modding/blob/master/examples/adding_cube.js
### Les options détaillés de la partie
#### Accés
Une fois que le mod a démarré, toutes les options détaillés passerons dans l'object `game.options`
#### Champs accessibles
Cela inclut toutes les propriétés définies dans [`this.options`](#options), et également des champs étendus listés çi dessous (sauf s'ils ne sont pas définis):
| Champ | Description |
| - | - |
| bouncing_lasers | Si les lasers rebondissant sont activés ou pas |
| max_tier_lives | Le nombre de vie quand le joueur a atteint le vaisseau maximal autorisé (définit dans l'option `max_level`) | 
#### Champs accesibles dans le mode équipe
| Champ | Description |
| - | - |
| teams | Un array représentant les informations basiques des différentes équipes: <br>`base_name`: Nom de la station<br>`faction`: Nom de la faction de la station<br>`hue`: la couleur de l'équipe|
| crystal_capacity | an array presenting the capacity of the stations in the increasing level order |
| deposit_shield<br>spawning_shield<br>structure_shield | Un array qui représente la vie des dépôts, spawneurs (modules permétant aux vaisseaux d'apparaître), petits modules, du plus petit au plus grand niveau. |
| deposit_regen<br>spawning_regen<br>structure_regen | Un array qui représente la régénération des dépôts, spawneurs (modules permétant aux vaisseaux d'apparaître), petits modules, du plus petit au plus grand niveau.|

### Assigner des propriétés personalisées à des entités/objets
Vous pouvez assigner des propriétés à des entités du jeu (ou des objects) comme les notes annexes et indicateurs.
#### Accéder et assigner
Faites simplement appel à la propriété `custom` (qui est toujours un object) et assignez lui des propriétés.

#### Entités/Objets supportés
* `game` objet
* tous les vaisseaux
* tous les extraterrestres (aliens)
* toutes les armes secondaires (secondaries)
* tous les astéroïdes
#### Exemples
```js
game.custom.hasMod = true // game object
game.ships[0].custom.userScore = 6712 // ship entity
game.aliens[0].custom = {created: true, rating: "10stars"} // alien entity
game.asteroids[0].custom = {init: true} // asteroid entity
```

### Autres instances de jeu et méthodes
#### Mettre une carte customisée en jeu
Vous pouvez utiliser `game.setCustomMap(<map pattern>)` pour mettre une carte customisée en jeu.

Où <map pattern> a le même format que [la carte customisée dans `this.options`](#custom-asteroids-maps)

#### Lock/unlock the mod from attracting new players
Utilisez `game.setOpen(true/false)` pour fermer/ouvrir votre mod (visibilité par les joueurs) (seulement pour les mods du [Modding Space (https://starblastio.gamepedia.com/Modding_Space).

Il y a aussi des propriétés booléennes `game.is_open` est utiliser pour déterminer si le mod est ouvert ou pas.

### Problèmes communs et comment les fixer
#### Problème de l'écran noir
Dans la plupart des cas, votre écran est noir après que le mod ait chargé car votre arbre des vaisseaux contient une erreur.
Suivez ces règles pour empêcher un écran noir:

1. Votre arbre des vaisseaux doit avoir au moins un vaisseau de tier 1.
1. Si votre arbre des vaisseaux a 2 vaisseaux de niveau 2, alors il faudra 1 vaisseau de niveau 1.
1. Certains modéles doivent être dans le bon ordre: 1,2,3 etc (et non 1,6,17, par exemple) ou contrôler les chemins d'accès à un vaisseau par le paramètre "next" (mais garder un ordre correcte pour les vaisseaux qu'on ne peut pas atteindre).
1. Vous ne pouvez pas avoir un nombre infini de chemins pour accéder à unu vaisseau, fait par le paramètre "next" - tous les chemins vont aboutir à un vaisseau, ils ne pourront pas revenir à un certain vaisseau (inférieur au vaisseau actuel).
#### Mon mod s'est arrêté accidentellement mais la partie ne s'est pas arrêtée
Quelquefois, des problèmes non-attendus peuvent faire crasher votre mod, mais cela déconnecte seulement le "contrôleur" du mod, ce qui fait que la partie en elle-même va continuer, mais sans être contrôlée par l'éditeur de mods jusqu'à qu'elle se ferme (ou même dans des occasions sérieuses, les développeurs du jeu - comme PMGL - doivent fermer le mod d'eux-même).
Voici quelques raisons qui peuvent mener au crash d'un mod:

1. Fermer/Actualiser l'onget de l'éditeur de mod sans d'abord arrêter le mod (raison la plus commune)
1. Connection internet très instable
1. Le serveur a une erreur (ce qui contrôle le mod va automatiquement être arrêter par le serveur)
1. L'onglêt de votre naviguateur a crashé (faites attentions avec les boucles infinies avec for/while)

Rapellez-vous que vous ne pouvez pas vous reconnecter au serveur qui a crashé, même s'il est encore en ligne.

## Ressources de la communauté
### Tutoriels et documentation
* [How to add ship to the mod - by InterdictorSD](https://www.youtube.com/watch?v=3b2zKArOkXk)
* [Modding Live #2 by PMGL](https://www.twitch.tv/videos/270359062)

### Outlis
* [Map Editor](https://bhpsngum.github.io/starblast/mapeditor/)

### Ressources de codes
* [Archive des mods de la communauté](https://bhpsngum.github.io/starblast/mods/)
* [WIP Modding plus de Dpleshkov](https://github.com/dpleshkov/starblast-modding-plus)
* [Starblast code reference by Bhpsngum](https://github.com/bhpsngum/starblast/)
* [Starblast codes et objets reference by 45rfew](https://github.com/45rfew/Starblast-mods-n-objs)
* [Starblast code reference by Wolfan](https://github.com/W0lfan/Starblast-code-snippets)
