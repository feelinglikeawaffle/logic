# LOGIC — Engineering Sandbox

A browser-based, top-down 2D engineering sandbox. The first playable foundation focuses on free construction, node-based digital logic, editing quality-of-life, and local blueprints.

## Run

Open `index.html` in a modern browser, or enable GitHub Pages for the repository and publish from the `main` branch root. No build step, server, account, or external dependency is required.

## Phase 1–3 features

- Infinite-feeling pan/zoom canvas with grid and snap controls
- Compact, searchable component library with logic, I/O, mechanical, electrical, sensor, structure, and computing categories
- Refined inspector with clearer empty, single-selection, and multi-selection states
- Mobile slide-out component browser and inspector
- Component placement, selection, multi-selection, move, rotate, delete
- Node-to-node connections with live signal visualization and ports that follow component rotation
- Working Boolean gates: AND, OR, NOT, XOR, NAND, NOR, XNOR, BUFFER
- Multi-pass signal propagation so connected combinational logic settles through longer chains within a simulation tick
- DEMUX signal routing
- Dynamic 2D physics with gravity, a ground plane, mass, bounce, friction, and basic body-to-body collision response
- Powered motors and gears with adjustable rotational speed
- Servo angle control, powered pistons with extension and pushing force, driven wheels, and free-spinning hinges
- Select two physical parts to create a hinge pivot or spring link; links are drawn on the canvas and saved in project JSON
- Physics toggle in the simulation toolbar; actuator power, mass, bounce, and target/speed settings in the inspector
- Distance, rotation, and collision sensors can read the physical scene
- Basic stateful / utility components: switches, buttons, constants, clocks, SR latch, D flip-flop, counter, mux, adder, comparator, register, memory, relay, lamp, display, and probe
- Simulation play/pause, fixed-step advance, reset, and speed choices from 0.1× to 10×
- Undo/redo, copy/paste, duplicate, and keyboard shortcuts
- Blueprint library for saving selected constructions or the entire current construction, and placing saved blueprints
- JSON project export/import
- Local autosave in browser storage
- Component inspector with editable labels, positions, rotation, and basic parameters

## Controls

| Action | Control |
|---|---|
| Select | V |
| Connect nodes | C |
| Pan | Space + drag or middle mouse |
| Zoom | Mouse wheel |
| Multi-select | Shift + click |
| Copy / paste | Ctrl/Cmd + C / V |
| Duplicate | Ctrl/Cmd + D |
| Undo / redo | Ctrl/Cmd + Z / Y |
| Rotate selection | R |
| Delete | Delete / Backspace |
| Cancel connection | Escape |

## Notes

Phase 3 adds a lightweight 2D rigid-body layer for construction experiments. It is a creative sandbox physics model rather than a precision engineering solver: collision geometry is simplified, hinge joints are pivot constraints, and electrical circuit solving, advanced computing simulation, and fully encapsulated custom-component execution remain future systems. The custom component library and reusable blueprint workflow are early foundations, not yet a full nested-subcircuit runtime.

Projects and blueprints are stored locally in the browser. Export JSON files to back up or move work between browsers.

## Phase 4 — component behaviors and machine interaction

Phase 4 makes several previously placeholder-like parts perform distinct actions:

- DISPLAY and PROBE draw a live numeric readout on their module face while the simulation runs
- SWITCH is a latched input; BUTTON is now a momentary pulse input
- BATTERY supplies an adjustable voltage; GENERATOR produces voltage from nearby rotating machinery
- RESISTOR calculates current from incoming voltage and its configured resistance; RELAY gates its voltage output with CONTROL
- LIGHT sensor measures nearby active LAMP outputs; DISTANCE and ROTATION provide numeric scene readings; COLLISION reports nearby body contact
- MOTOR accepts a SPEED signal, while meshed MOTOR/GEAR and GEAR/GEAR pairs transfer opposite-direction rotation
- SPRING responds to its LOAD input; existing piston, wheel, servo, hinge, gravity, and body collision behaviors remain in place
- GEAR can be manually enabled and adjusted from its inspector

To see live behavior, wire the relevant named output/input ports, then press Play or Step. For example, connect BATTERY VOLTAGE → RESISTOR VOLTAGE and connect RESISTOR CURRENT → DISPLAY IN. Enable a MOTOR beside a GEAR to see the gear counter-rotate. Turn on a LAMP near a LIGHT sensor to see its reading rise.

The physics and circuit systems are still deliberately lightweight. This is not a precision electrical circuit solver or a full rigid-body engineering engine; gear meshing is proximity-based and the 2D collision solver remains simplified.
