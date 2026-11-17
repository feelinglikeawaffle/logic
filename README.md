# LOGIC — Engineering Sandbox

A browser-based, top-down 2D engineering sandbox. The first playable foundation focuses on free construction, node-based digital logic, editing quality-of-life, and local blueprints.

## Run

Open `index.html` in a modern browser, or enable GitHub Pages for the repository and publish from the `main` branch root. No build step, server, account, or external dependency is required.

## Phase 1–3 features

- Infinite-feeling pan/zoom canvas with grid and snap controls
- Compact, searchable component library with logic, I/O, mechanical, sensor, structure, and computing categories
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


## Phase 6 — connected machine assemblies

- Added **rigid weld joints** alongside hinges and springs. Select two physical parts and use “Rigidly weld together” to lock their relative position and orientation while the simulation runs.
- Welds preserve the relative angle as well as the joint anchor, so a welded frame, motor, thruster, or other part behaves more like one assembly.
- Spring links now include velocity damping to reduce endless oscillation and make linked mechanisms settle more naturally.
- Improved body-to-body collision response with tangential friction and a small rotational response, so impacts transfer a little more motion instead of only sliding blocks apart.
- Joint types have distinct canvas styling, and all joint data continues to be saved in project JSON, local autosaves, undo/redo, and blueprints where applicable.

### Phase 6 experiments

1. Shift-click a FRAME and MOTOR, then choose **Rigidly weld together**. The motor now rides with the frame as one rigid assembly.
2. Weld a THRUSTER to a frame, then activate it. The entire welded construction should accelerate together.
3. Connect a moving arm to a fixed ANCHOR with a hinge, then attach a second part to the arm with a weld.
4. Join two weights with a spring and observe the damping as they settle after being disturbed.

The physics remains a lightweight 2D creative solver. Welds and collision geometry are approximations, not a precision rigid-body engine; highly complex or very fast assemblies may still show some jitter.

## Phase 7 — stable zoom, pinned parts, and connectors

- Component glyphs, names, and connection-node markers now keep a consistent screen size while the canvas zooms; the component bodies still scale with the world.
- Physical parts have a **Physics simulation enabled** toggle in the inspector. Turn it off to pin that part in place and make it immovable by gravity, collisions, joints, and actuator forces. ANCHOR and PIN start with physics disabled.
- Added a **PIN** structure part for a fixed attachment point.
- ROPE and SPRING are connectors between two selected physical parts, not standalone blocks. Shift-click two parts and choose **Connect with rope** or **Connect with spring**. A rope goes slack when the parts are closer than its length and becomes taut when stretched; a spring pulls toward its resting length and includes damping.
- The old SPRING block remains supported when loading older projects, but it is no longer offered as a new library component.

The physics toggle and connector settings are stored with project objects and joints. The 2D physics solver remains approximate, so complex assemblies may still show some jitter.
