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

## Phase 4–5 — interactive components and unlimited sandbox

The project is an unlimited creative construction sandbox. There are no batteries, fuel, charging, energy costs, or resource requirements. Mechanical actuators are controlled directly from their inspector or by logic signals.

- DISPLAY and PROBE show live numeric signal readouts
- SWITCH is a latched input; BUTTON is a momentary pulse input
- RELAY is a signal-controlled logic gate, not an electrical power component
- Motors, gears, servos, pistons, hinges, springs, and wheels have distinct mechanical behaviors
- THRUSTER applies force to its own body in its facing direction
- MAGNET attracts nearby physical bodies, with a REPEL signal to reverse the force
- GRABBER clamps onto a nearby body, carries it, and releases it when disabled or given a RELEASE signal
- CONVEYOR pushes bodies across its belt in the direction it faces
- FAN blows nearby bodies away in a forward airflow cone
- Sensors report distance, light level, rotation, and collision state
- Mechanical modules have their own visual treatment, adjustable behavior values, and direct activation controls

### Phase 5 experiments

1. Attach a THRUSTER to a frame with a hinge or anchor and activate it to propel the assembly.
2. Place a MAGNET near loose weights and activate it; send a positive REPEL signal to push them away instead.
3. Activate a GRABBER near a weight, move the grabber assembly, then deactivate it to drop the weight.
4. Place a CONVEYOR under loose objects and activate it to move them along the belt.
5. Aim a FAN at a group of loose objects and activate it to scatter them.
6. Wire a SWITCH or BUTTON to an actuator's ENABLE input to control it without manually toggling the inspector.

To run a simulation, press Play or Step. Some mechanisms need to be mounted to an ANCHOR or attached to a frame if you want them to stay in place while acting on other objects.

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

The physics model is a lightweight 2D sandbox rather than a precision engineering solver. Collision geometry and some mechanical constraints are simplified; gear meshing and several actuator interactions are approximations intended for creative experimentation. The logic wires carry control values, not electrical energy. Projects and blueprints are stored locally in the browser; export JSON files to back them up or move them between browsers.
