NuclearGrid
A nuclear power plant simulation for Paper servers. Build a full plant with one command, run the reactor from a working control room, keep it cooled and maintained, and survive the meltdown when you don't.
NuclearGrid generates a complete, walkable nuclear plant: a reactor hall with a 5x3x5 iron core and beacon, a turbine hall with three generator sets, a control room with an airlock, a decontamination room, cooling towers and service corridors. Everything is physical. You start the reactor with a button, watch live signs, pipe in coolant with copper blocks, wire plants together with cable, and put on protective gear before you walk into a radiation zone.
> \*\*Status:\*\* an actively developed prototype. Features are added quickly and some systems have had limited in-game testing. Run it on a test server first and report anything that behaves oddly.
---
Features
A complete plant from one command
`/nuclear build` pastes a 120 x 80 block plant at your feet. The block you stand in becomes the floor level, and the plant extends 120 blocks east and 80 blocks south.
Reactor hall, turbine hall with three turbine-generator sets, control room with airlock, decontamination room, two cooling towers, an enclosed hallway with airlocks, and a fenced site.
Everything is placed from a bundled blueprint, so the layout is the same every time.
A working control room
Six physical stone buttons: Start, Shutdown, Dashboard, SCRAM, Inspect and Grid/Turbines. Each has its own sign.
Live signs on the wall showing reactor state, core temperature, power output, coolant and safety status, the turbine steam temperature, and a maintenance status.
A reactor GUI (crying obsidian console, or `/nuclear gui`) showing power, temperature, coolant and steam.
A main water-intake valve lever and a turbine shutdown lever, each with a sign reading OPEN/CLOSED or RUNNING/SHUT DOWN.
Three redstone output pads outside the control room. Their blocks turn to redstone blocks while the plant is generating at full power and back to smooth stone when it isn't, so you can wire the output to anything.
Cooling and water
The reactor needs cooling water. A cauldron intake sits at the east fence of the plant.
Water can come straight from a source block touching the cauldron, or through a continuous copper-block pipe from the cauldron to a water source (runs of 500+ blocks are supported).
`/nuclear intake add` registers up to 32 extra remote intake stations per plant.
The turbine room has its own water intake outside the turbine hall's east wall.
Close the main valve and the reactor loses its automatic water supply.
Turbines and power
Turbine steam temperature climbs slowly from cold toward 500 C while the reactor runs and the turbine room has water. Power output rises with it, reaching 1000 MW at 500 C, and the redstone outputs switch on at full power.
Without turbine water, with the reactor off, or in a meltdown, the steam cools and power drops with it.
A turbine lever shuts the turbines down without stopping the reactor.
Radiation and protective gear
Normal operation keeps radiation inside the reactor room: high while running, low while off.
A meltdown or explosion spreads radiation outward from the core, up to a configurable radius (default 500 blocks). It recedes after repair.
Radiation damages and poisons players. A full set of netherite armor protects you, and a gear stand in the airlock hands it out.
Radiation also kills mobs (configurable).
The decontamination room clears radiation effects.
During a meltdown or after an explosion, the control-room airlock stays locked to anyone without the full gear. Server operators are exempt.
Maintenance
While a reactor runs with cooling water, one random core block fails every 10 minutes. A warning sounds and the block must be replaced by hand with an iron block.
Each missing block raises the temperature the core settles at, and makes radiation leak out of the reactor room. Replace the blocks and the temperature falls slowly and the leak recedes.
Neglect it long enough and the core overheats into a meltdown.
Fully configurable, or switch it off.
Meltdown, explosion and repair
A meltdown starts a countdown (default 30 minutes), sounds alarms, shows boss bars, and melts core blocks into lava one at a time.
Repair it in three stages with `/nuclear repair` (water bucket, then 3 iron ingots and 2 redstone dust, then glowstone dust), or drop the whole kit into the repair chest in the control room.
If the countdown runs out, the reactor explodes, destroying the core and part of the building. Rebuild the 5x3x5 iron core and the beacon, then put the repair parts in the chest.
After any repair the reactor comes back off, and it cannot be restarted until the fallout has fully receded.
Linking plants into a grid
Each reactor has an amethyst coupler on the outside west wall of its building.
Build a continuous copper-block cable between two couplers, then right-click each coupler to link them. Up to 5 reactors can share one grid.
Linked reactors share start, shutdown and SCRAM, and the water-intake lever applies to the whole grid. Break the cable and the link goes inactive until it is restored.
---
Requirements
	
Server	Paper (the plugin declares `api-version: 26.3`)
Java	25
Optional	Essentials, Vault and LuckPerms are declared as soft dependencies. None of them is required
Installation
Download the latest `nuclear-grid-<version>.jar` (or build it yourself).
Drop it into your server's `plugins/` folder.
Start the server. A `plugins/NuclearGrid/` folder with `config.yml` is created, and plants are saved to `plants.yml` in the same folder.
Quick start
Go to a large, empty, flat area. The build replaces every block in its 120 x 80 footprint.
Stand where you want the plant's north-west corner and floor level, and run `/nuclear build`.
Walk into the control room through the airlock and press START.
Give the reactor water: connect the cauldron at the east fence to water with copper blocks, or touch it directly to a source block. Do the same for the turbine cauldron.
Wait for the steam to reach 500 C. The redstone outputs turn on, and you can wire redstone dust to the output pads.
---
Commands
All commands are `/nuclear <subcommand>`.
Subcommand	What it does	Permission
`build`	Generate a plant at your location	`nucleargrid.admin`
`status`	List registered plants and their state	`nucleargrid.status`
`gui`	Open the reactor status GUI	`nucleargrid.admin`
`start` / `shutdown`	Start or stop the reactor (and its grid)	`nucleargrid.admin`
`scram`	Emergency trip and alarm	`nucleargrid.admin`
`grid`	Turbine and grid dashboard	`nucleargrid.admin`
`maintenance`	Inspect equipment (reactor must be off)	`nucleargrid.admin`
`decon`	Decontaminate inside the decon room	`nucleargrid.admin`
`intake <add|list|remove>`	Manage remote water intake stations	`nucleargrid.admin`
`signs`	Reinstall or refresh the control-room signs	`nucleargrid.admin`
`meltdown`	Trigger a test meltdown	`nucleargrid.admin`
`repair`	Staged meltdown repair	`nucleargrid.repair`
`remove`	Unregister the nearest plant (blocks are left in place)	`nucleargrid.admin`
The physical buttons, levers and the repair chest are for players too. They need `nucleargrid.use`.
Permissions
Permission	Default	Allows
`nucleargrid.use`	everyone	Operate the control-room buttons, levers, console and couplers
`nucleargrid.status`	everyone	View plant status
`nucleargrid.repair`	everyone	Perform emergency repairs
`nucleargrid.admin`	operators	Build and manage plants
Configuration
`plugins/NuclearGrid/config.yml`. Restart the server after editing. New options are not added to an existing `config.yml` automatically, so any key you leave out uses the default shown here.
Key	Default	Description
`meltdown.countdown-seconds`	`1800`	Time to finish repairs before the reactor explodes
`meltdown.core-lava`	`true`	Core blocks melt into lava during a meltdown
`meltdown.core-lava-max-blocks`	`8`	Most core blocks that can be lava at once
`meltdown.core-lava-interval-seconds`	`60`	Seconds between one more block melting
`radiation.kill-mobs`	`true`	Radiation damages and kills mobs
`radiation.max-radius`	`500`	Largest radiation radius in blocks (raise it for a bigger blast)
`radiation.require-gear-to-exit-airlock`	`true`	Lock the control-room airlock exit without full gear during a meltdown or after an explosion
`maintenance.enabled`	`true`	Core blocks fail over time while running with water
`maintenance.damage-interval-minutes`	`10`	Minutes between failures
`maintenance.temperature-per-missing-block`	`50.0`	Degrees C each missing block adds to the core's settling temperature
`maintenance.temperature-rise-per-second`	`2.0`	How fast the core climbs to that level
`maintenance.temperature-fall-per-second`	`0.5`	How fast it falls back after repairs
`maintenance.overheat-meltdown`	`true`	A damaged core reaching 200 C melts down
`maintenance.radiation-growth-per-missing-block`	`5`	Blocks of radius gained per minute per missing block
`turbine.steam-rise-per-second`	`2.0`	Steam heating rate (about 4 minutes to 500 C)
`turbine.steam-fall-per-second`	`1.0`	Steam cooling rate
Control room reference
All offsets are from the plant's origin (the corner and floor level where you ran `/nuclear build`).
Item	Offset (X, Y, Z)
Operator buttons (start, shutdown, dashboard, SCRAM, inspect, grid)	X 48/52/56/60/64/66, Y+2, Z+71
Water-intake lever	44, +2, 71
Turbine lever	67, +2, 71
Reactor core (5x3x5 iron)	X 14-18, Y 1-3, Z 24-28
Beacon	16, +4, 26
Repair chest	60, +1, 64
Reactor water intake cauldron	119, +1, 35
Turbine water intake cauldron	69, +1, 27
Grid coupler (amethyst)	7, +3, 27
Redstone output pads	X 47/52/57, Y 0, Z 74-76
Decon button	99, +2, 56
How a typical shift goes
Start up. Press START. The core runs, the steam begins to climb, and the signs update.
Watch the water. If the intake loses water, the coolant drains and the core heats toward a meltdown.
Handle maintenance. Every 10 minutes a core block fails. Replace it with an iron block before the temperature steps up and radiation starts to leak.
If it goes wrong. Put on the netherite gear, repair the reactor, and wait for the radiation to recede before starting it again. Miss the countdown and the reactor explodes.
Building from source
```bash
git clone <your-repo-url>
cd NuclearGrid
mvn package
```
The jar is written to `target/nuclear-grid-<version>.jar`. You need JDK 25 and Maven. The project compiles against the Paper API from the PaperMC repository.
Project layout
```
src/main/java/com/nucleargrid/NuclearGridPlugin.java   commands, build, reactor tick, radiation, controls
src/main/java/com/nucleargrid/PlantStore.java          plant state saved to plants.yml
src/main/resources/nuclear-grid-blueprint.bin          the plant blueprint
src/main/resources/plugin.yml                          commands and permissions
src/main/resources/config.yml                          default configuration
```
Notes
`/nuclear build` replaces blocks in its footprint. Use an empty test area.
`/nuclear remove` unregisters a plant but leaves its blocks in the world.
Radiation only affects loaded chunks.
