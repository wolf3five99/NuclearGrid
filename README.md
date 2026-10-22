# NuclearGrid

**NuclearGrid** is a nuclear power plant simulation plugin for Minecraft Paper servers. Build a plant, operate its reactor, manage coolant and power output, connect plants into a grid, and respond to radiation incidents and meltdowns.

- **Latest release:** [NuclearGrid v0.3.79](https://github.com/wolf3five99/NuclearGrid/releases/tag/v0.3.79) *(if this tag has been published)*
- **Downloads:** [GitHub Releases](https://github.com/wolf3five99/NuclearGrid/releases)
- **Report a bug or request a feature:** [GitHub Issues](https://github.com/wolf3five99/NuclearGrid/issues)

> This repository is intended for player/server-owner documentation and downloads. It does not include the Java source code.

## Table of contents

- [What NuclearGrid includes](#what-nucleargrid-includes)
- [The plant build](#the-plant-build)
- [Reactor operation](#reactor-operation)
- [Cooling and water intake](#cooling-and-water-intake)
- [Power generation and reactor grids](#power-generation-and-reactor-grids)
- [Radiation and meltdowns](#radiation-and-meltdowns)
- [Repair and recovery](#repair-and-recovery)
- [Commands](#commands)
- [Installation](#installation)
- [Permissions and configuration](#permissions-and-configuration)
- [Troubleshooting](#troubleshooting)
- [Compatibility and safety](#compatibility-and-safety)
- [Support](#support)

## What NuclearGrid includes

NuclearGrid is designed around a physical plant players can explore and operate in-game. Its systems include:

- A generated nuclear plant with reactor, control-room, turbine, cooling, and maintenance areas.
- Reactor start, shutdown, status, inspection, and emergency SCRAM controls.
- Temperature and coolant monitoring, with warning indicators.
- Water intake and coolant supply systems.
- Power output indicators and links between multiple plants.
- Radiation hazards, boss-bar/status feedback, and decontamination mechanics.
- Meltdown alerts, emergency response, reactor repair, and recovery workflows.
- Protective gear and airlock areas intended to support safer movement between contaminated and protected spaces.

Feature behavior can differ between releases. Check the release notes for the exact version installed on your server.

## The plant build

Use the in-game build command to generate the plant structure:

```
/nuclear build
```

The generated complex is designed around several connected functional areas:

| Area | Purpose |
|---|---|
| Reactor building | Houses the reactor/core and its operating area. |
| Control room | Provides plant monitoring and controls, including status and emergency actions. |
| Turbine hall | Represents the plant's power-generation section. |
| Cooling systems | Visual cooling equipment and coolant-related systems support reactor operation. |
| Water intake | Supplies the coolant system when configured and connected correctly. |
| Maintenance/repair area | Supports inspection, repairs, and recovery tasks. |
| Decontamination room | Provides a designated area for radiation-related cleanup. |
| Airlocks and connecting hallway | Connect protected areas and help separate the control/decontamination spaces from exposed areas. |

The build uses a large footprint and includes structural details such as access routes, catwalks, stairs, railings, pipes, windows, warning lamps, and monitoring signs. Exact layout and block placement depend on the plugin release.

**Before generating a plant:** make a world backup, ensure the target area is clear, and use the command only where you are comfortable with a large structure being placed.

## Reactor operation

The plant is intended to be operated through in-world controls and supported NuclearGrid commands.

Typical operating tasks include:

1. Inspect the plant and review the status display.
2. Check coolant availability and the temperature indicators.
3. Start the reactor using the available control-room controls.
4. Monitor temperature, water level, and power output while running.
5. Use a normal shutdown for planned stops or **SCRAM** for an emergency.

Control-room panels may include start, shutdown, status, inspection, turbine, and emergency controls, depending on the release. Do not assume every control is available or working identically in every version; check the server console if an interaction fails.

## Cooling and water intake

Cooling is a core part of plant operation. NuclearGrid includes coolant/water-level behavior and visual indicators for water status and temperature.

- Check the coolant level before operating the reactor.
- The water-level indicator is intended to show a normal/full level and warn when water is low.
- Temperature warning lamps indicate elevated reactor temperature.
- The intake uses a physical pipe connection concept; copper-family blocks are used for the coolant connection system in supported builds.
- Long-distance intake behavior and pipe scanning may vary by release. If a distant source is not detected or the water level does not recover, test the connection nearby first and review the server log.

Do not assume that placing any arbitrary line of blocks will provide coolant. Follow the connection behavior implemented by the exact version you have installed.

## Power generation and reactor grids

NuclearGrid supports power-output monitoring and a physical method for linking plants into a grid in versions that include the grid feature.

In releases using the **End Rod grid coupler**, the intended interaction is:

1. Locate the coupler for the first plant.
2. Right-click it to select the first plant.
3. Right-click the second plant's coupler to link the two plants.
4. Sneak-right-click a linked coupler to disconnect the link.

Grid linking is intended for plants in the same world and follows the limits implemented by the installed release. Keep couplers accessible and avoid confusing them with decorative blocks. Verify the link and combined output in the in-game grid/status display.

## Radiation and meltdowns

A meltdown is an emergency event, not a routine operating mode. Depending on the release and configuration, incident behavior can include:

- Audible and visual alarms with nearby-player alerts.
- Radiation exposure and status/boss-bar feedback.
- Poison or other damage effects for unprotected players in affected areas.
- A configurable countdown before a major meltdown event.
- An explosion that may damage blocks, followed by a persistent contaminated area.
- Radiation spread that can be affected by water placed over the reactor core in supported versions.

Protective equipment and designated control/decontamination areas are intended to help players manage exposure. These mechanics are game simulations and do not represent real-world nuclear engineering.

## Repair and recovery

Supported releases include reactor inspection and repair mechanics. Depending on the stage and release, recovery can involve repair materials, a bucket, redstone/iron components, glowstone dust, and a repair chest or checklist.

General recovery guidance:

1. Keep players away from the contaminated area and follow the in-game alerts.
2. Use SCRAM if the reactor is still operating and the control is available.
3. Check the inspection output or repair checklist to identify missing parts.
4. Gather the required materials and follow the in-game repair workflow.
5. Confirm the plant has returned to a safe state before attempting to restart it.

A severe meltdown may destroy part of the physical reactor structure. Repairing the plugin's state does not necessarily rebuild destroyed blocks; the affected structure may need to be rebuilt using the supported in-game workflow. Exact repair requirements are version-dependent.

## Commands

The following command families have been used by NuclearGrid releases. Availability and exact syntax can vary by version.

| Command | Purpose |
|---|---|
| `/nuclear build` | Generate a nuclear plant structure. |
| `/nuclear maintenance` | Open or use maintenance-related functionality. |
| `/nuclear inspect` | Inspect reactor/plant condition and repair status. |
| `/nuclear grid` | View reactor-grid information where grid support is enabled. |
| `/nuclear decon` | Access decontamination functionality. |
| `/nuclear scram` | Trigger emergency shutdown functionality. |

If a command is not recognized, check the installed version, the server console, and the plugin's in-game command help. Do not assume command aliases or extra arguments that are not shown by your installed release.

## Installation

1. Download the desired `.jar` from [GitHub Releases](https://github.com/wolf3five99/NuclearGrid/releases).
2. Stop your Paper server.
3. Copy the JAR into the server's `plugins/` directory.
4. Start the server.
5. Check the console for plugin load errors and confirm NuclearGrid is enabled.
6. Back up the world before generating a plant or testing destructive incident behavior.

To update, stop the server, replace the old NuclearGrid JAR with the new release, then start the server and review the console. Keep a backup of your world and plugin configuration before updating.

## Permissions and configuration

The plugin has used the following permission nodes:

- `nucleargrid.use` — general use of NuclearGrid features.
- `nucleargrid.admin` — administrative access to supported features.

Exact permission requirements can differ by command and version. Use your permissions plugin and the server's plugin output to confirm access.

Some releases support a configurable meltdown countdown; a documented example setting is:

```yaml
meltdown:
  countdown-seconds: 1800
```

That example represents 30 minutes. Only use configuration keys present in the config file generated by your installed release; unknown settings may be ignored.

## Troubleshooting

**The plugin does not load**
- Confirm the JAR is in the server's `plugins/` folder.
- Check the console for the exact error.
- Confirm the Paper/server version is compatible with the release.

**A command or control does nothing**
- Check that the plugin loaded successfully.
- Confirm you have the required permission.
- Try the supported command from the table above and inspect the console for errors.
- Confirm you are using a release that includes that feature.

**The coolant level does not rise**
- Check the water source and physical pipe connection.
- Test with a shorter connection first.
- Confirm the pipe blocks and intake behavior match the installed release.
- Review console messages for intake or plant errors.

**The grid does not link or output looks wrong**
- Confirm both plants and couplers exist and are in the same world.
- Follow the coupler interaction sequence for your version.
- Recheck the grid/status display after linking.

**The plant or radiation area is damaged**
- Use the in-game inspection and repair workflow where available.
- Restore from a world backup if the structure was unintentionally damaged.

## Compatibility and safety

NuclearGrid is a Minecraft gameplay plugin, not a real-world nuclear simulator or safety system. Reactor behavior, radiation, coolant, and repairs are fictional game mechanics.

Compatibility can change between releases. Check the release notes and server console rather than assuming a version works with every Paper build. Always test on a backup or staging server before using it on an important world.

## Support

- **Downloads and release notes:** [GitHub Releases](https://github.com/wolf3five99/NuclearGrid/releases)
- **Bug reports and feature requests:** [GitHub Issues](https://github.com/wolf3five99/NuclearGrid/issues)

When reporting a problem, include the NuclearGrid version, Minecraft/Paper version, relevant console errors, and the steps that reproduce the issue. Do not include private server credentials or other secrets.

## License

No license has been specified in this repository. Until a license is added, standard copyright restrictions apply.
