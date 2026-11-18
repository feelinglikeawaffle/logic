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

## Phase 8 — simple controls and physical mechanisms

- Mechanical actuators use clear binary trigger inputs: **0 = off, 1 = on**. Motors, pistons, thrusters, fans, conveyors, magnets, grabbers, wheels, and launchers no longer expose confusing numeric output ports. Their speed, force, range, or target values are configured on the part itself.
- Added a **ROCKET LAUNCHER**. Connect a SWITCH or other logic output to its TRIGGER input. Each rising edge (0 to 1) launches a physical rocket in the direction the launcher faces. Rocket speed is configurable in the inspector.
- Sensors now report simple binary detections: distance detects a nearby body, light detects an illuminated lamp, rotation detects a moving mechanism, and collision detects a nearby body. The distance sensor's range is configurable.
- **Attach to motor shaft** is available when two physical parts are selected and one is a MOTOR. Select the motor and the part to attach; the attached part rotates around the motor shaft as the motor spins. Use a weld to mount the motor housing to a frame first.
- Rope and spring are physical connectors, not library blocks. Select two parts and create a **Rope connector** or **Spring connector**. Ropes hang slack when short and pull taut at their saved length; springs are drawn as coils and pull toward their rest length with damping.
- The inspector labels control inputs as 0/1 and explains that 0 is off and 1 is on. Actuator settings stay on the actuator rather than being encoded as extra signal inputs.

### Quick mechanism setup

1. Place a SWITCH and a MOTOR.
2. Connect SWITCH OUT to MOTOR TRIGGER.
3. Mount the motor body to a FRAME with a weld.
4. Place an arm or wheel where you want it, shift-select the MOTOR and the part, then choose **Attach to motor shaft**.
5. Press Play and toggle the switch. The motor shaft and attached part should rotate together.

For a launcher, connect SWITCH OUT to ROCKET LAUNCHER TRIGGER and press Play. Toggle the switch off and on again to fire another rocket.

The solver remains a lightweight 2D approximation. Motor-shaft links, rope tension, spring forces, and collisions are intended for sandbox building rather than precision engineering simulation.


## Phase 9 — universal physical attachment nodes

- Physical parts can be joined at named mounting nodes instead of only at their centers. Select two parts and choose a node for each endpoint: center, top, right, bottom, left, or one of the four corners.
- The chosen local attachment points rotate with their components. Springs and ropes now measure their length between those exact points, so attaching a spring to the end of a beam pulls on the beam at that end rather than at its center.
- Spring forces include an approximate turning effect when applied away from a part's center of mass. Rope tension is applied only when the rope is stretched; slack rope does not push.
- Added a rigid link / strut connector that maintains a fixed distance between its two mounting nodes. It behaves as a two-ended structural member, unlike a rope (tension only) or spring (push and pull).
- Existing hinge, weld, rope, spring, and motor-shaft joints remain supported. PIN and ANCHOR parts can be used as fixed attachment endpoints; BEAM remains a physical structural member that can be connected at its ends.
- Connector and attachment settings are stored in project data and continue to work with local autosave and JSON export.

The solver remains an approximate 2D sandbox solver. Attachment points and force transfer are improved, but this is not a finite-element or precision multibody simulation.


## Phase 10 — configurable connections and creative mechanisms

- Connected springs, ropes, and rigid links can be configured from either attached part's inspector. Spring settings include rest length, stiffness, and damping; rope and rigid-link settings include rest length. Zero damping is supported.
- **DECOUPLER** automatically holds the nearest body in front of it while its TRIGGER is 0, then releases it when TRIGGER becomes 1. Set its capture range in the inspector. It is useful for payload bays, traps, launch gates, and staged contraptions.
- **BUMPER** kicks an approaching body away from its facing direction on contact. **SPRINGBOARD** launches bodies upward when they land on it. Both have configurable interaction range and distinct physical behavior; they use cooldowns to avoid applying continuous force every frame.
- Existing GRABBER remains the powered grab-and-release tool. All new mechanisms are physical bodies and can be attached to beams, frames, pins, and other parts using the connector system.

As elsewhere in this project, these are lightweight game-physics approximations rather than precision engineering simulations.


## Phase 11 — pulley routing and connector winches

- Added a **PULLEY** mechanical part that acts as a physical cable guide. Mount it to a frame, beam, pin, or anchor, then select an existing rope or spring connector in the connected-hardware inspector and choose that pulley under **PULLEY GUIDE**. The cable is drawn around the sheave and its tension is solved across both cable spans.
- Rope, spring, and rigid-link connectors can be configured as winches directly from their connector settings. Set reel speed and direction, then enable the winch. The connector's first endpoint supplies its binary **TRIGGER** signal (or use the endpoint's manual actuator control); a manual reel button is also available.
- Winches change the connector's actual rest length during simulation, so the cable physically pulls the attached assembly as it reels in and pays out. This is connector hardware, not a separate powered resource system.
- Pulley routing and winch settings are saved with the joint in project JSON, autosaves, and undo/redo. A pulley can be mounted using the existing weld/hinge connector system; a fixed PIN or ANCHOR is also a suitable support.

### Phase 11 experiments

1. Place two physical parts and connect them with a rope.
2. Place a PULLEY between the endpoints, mount it to a support, then select either rope endpoint and set its **PULLEY GUIDE** to that pulley.
3. Enable the winch on the rope, set direction to **Reel in**, and connect a SWITCH to the first endpoint's TRIGGER input. Toggle the switch to shorten the cable.
4. Use **Pay out** to reverse the reel direction, or press **Reel manually** to test without logic wiring.
5. Try the same winch controls on a spring or rigid-link connector for retracting tension lines or adjustable-length struts.

The pulley solver is intentionally lightweight: a guided cable is approximated as two tension spans meeting at one guide, rather than a full multi-sheave rope solver. Complex cable routing and precise pulley torque are future refinements.


## Phase 12 — simple connector drawer and cable handling

- The Connectors button opens a real slide-out drawer with clear choices: Rope/Cable, Spring, Rigid Link, Hinge, and Rigid Weld.
- Choose a connector, then click two physical parts on the canvas. No Shift key or inspector setup is required for the basic connection workflow.
- A rope automatically uses a nearby pulley as its guide when one is placed close to the midpoint between the two parts. The existing pulley-guide selector remains available for manual routing.
- Connector winches use two simple controls in the connected-hardware inspector: **Reel in / Stop winch** and **Pay out instead**. The winch directly changes the connector length while the simulation runs.
- Rope, spring, and rigid-link connectors still collide with physical bodies as capsule-like obstacles. Pulley-routed ropes collide along both spans.

The connector collision model is intentionally approximate: it treats each cable/strut segment as a thin capsule and uses a simplified body radius. Pulley routing currently supports one guide per rope, not a full multi-sheave cable system.

## Phase 13 — construction kits, marble runs, fluids, and gases

### Construction parts
- Added a dedicated set of marble-run construction pieces: **Straight Track**, **Curved Track**, **Tube Track**, **Funnel**, **Splitter**, **Track Gate**, and **Support**.
- Track pieces are fixed in place by default and can be rotated with **R** to create slopes, turns, drops, and branching layouts. Supports give you simple structural legs to build elevated systems.
- Added a small **Marble** body with its own gravity, rolling movement, track contact, and marble-to-marble collisions. Track channels and gates use dedicated contact geometry rather than treating the entire piece as a solid rectangular block.
- **Track Gate** can be activated/deactivated from its inspector to hold or release a marble.

### Rotation and sizing
- Every component can be rotated to any angle from **0° through 359°** using the inspector's numeric field or slider.
- Press **R** to rotate the selected component by 15° at a time.
- The inspector's **Size** control scales components from **25% to 300%**. Component graphics, signal-port positions, track geometry, attachment offsets, and the main body collision bounds scale with the part.

### Construction kit
- The marble-run construction pieces remain available: Straight Track, Curved Track, Tube Track, Funnel, Splitter, Track Gate, Support, and Marble.
- Track pieces remain fixed by default and can be rotated and resized to make slopes, turns, drops, and branching layouts.
- Marble movement and track contact are lightweight approximations, not a precision engineering solver.

### Scope and performance
The fluid and gas particle system has been removed. Existing saved projects are still loadable; legacy fluid-source components are ignored during import. The focus is back on mechanical construction, physical parts, and marble-run systems.


## Quality-of-life and usability overhaul

- Reworked the workspace styling with clearer panel separation, calmer contrast, larger touch targets, and a more consistent visual hierarchy.
- The parts library is now a clean single-column list that is easier to scan and tap.
- **Placing parts is now a two-step action:** choose a part in the library, then click the exact spot on the canvas. Parts no longer unexpectedly appear in the middle of the build.
- A placement prompt tells you what you are placing; use **Cancel** or **Escape** to leave placement mode.
- The empty canvas gives a short three-step guide for getting started.
- Connector drawer, inspector, canvas tools, and mobile panels have more consistent spacing and touch-friendly controls.
- Existing keyboard shortcuts and advanced editing tools remain available.

### Updated basic workflow

1. Open **Components** and choose a part.
2. Click the desired location on the canvas to place it.
3. Drag parts to move them. Shift-click to select multiple parts.
4. Select a part to edit its settings in the inspector.
5. Open **Connectors**, choose a connector, then click the two physical parts to join.
6. Press **Play** to run the construction; use **Step** to advance one simulation step.


## World selection and monochrome UI overhaul

- Added a dedicated startup world menu with **Continue building** and three new-world presets: **2D Flat**, **2D Hilly**, and **2D Mountainous**.
- World terrain type is stored in local saves and exported project files. Older projects without a terrain field continue to load as flat worlds.
- Hilly and mountainous worlds draw a procedural terrain profile and use terrain height in the ground collision response. Objects also gain a small downhill acceleration from the terrain slope.
- The interface now uses a near-black, monochrome palette with white text, grayscale controls, subtle hover/press transitions, and animated menu entry.
- The Worlds button returns to the world menu. Starting a new world preserves a local backup of the previously saved world under a separate browser-storage key.


## Machine-building gameplay overhaul

The sandbox is now centered on building physical machines from blocks rather than designing logic circuits. The visual style, world-generation presentation, and existing construction workflow remain in place.

### New machine-building parts

- **Structure & armor:** frames, beams, weights, armor plates, anchors, pins, and the existing marble-run construction kit.
- **Drive & propulsion:** engines for forward thrust, motors for rotating shafts and torque, gears, wheels, propellers, thrusters, wings for lift, rudders for steering, pistons, servos, and pulleys.
- **Water & handling:** floats for buoyancy, ballast for sinking / trim, grabbers, decouplers, conveyors, fans, and magnets.
- **Weapons:** cannons, rapid-fire machine guns, rocket pods, bomb bays, and harpoons, alongside bumpers and springboards.
- **Controls:** simple switches and buttons remain available for basic trigger wiring. Most mechanisms can also be activated directly from their inspector.

### Ocean world

- Added **2D Ocean** to the world menu.
- The ocean has a visible waterline, an underwater region, and a deep seafloor.
- Objects experience underwater drag and buoyancy; FLOAT parts rise more strongly while BALLAST parts sink.
- PROPELLER thrust is strongest underwater and much weaker in air, encouraging boats and submarines.
- The ocean is a lightweight arcade-style physics environment, not a fluid simulation.

### Machine experiments

1. **Car:** weld a chassis from FRAME and BEAM parts, add WHEEL parts and an ENGINE, then activate the engine.
2. **Aircraft:** build a light frame, add WINGS and a rear THRUSTER, and tune the wing and thrust angles.
3. **Boat:** build a wide hull, attach FLOAT parts, and use rear-facing PROPELLERS for water movement.
4. **Submarine:** add BALLAST to sink, PROPELLERS to move, and RUDDERS to steer.
5. **Armored vehicle:** reinforce a frame with ARMOR, add wheels and an engine, then mount a CANNON or ROCKET POD.
6. **Weapons test rig:** mount a CANNON, MACHINE GUN, ROCKET POD, BOMB BAY, or HARPOON and activate it from the inspector.

### Simulation scope

This is an early machine-physics pass. Engines, wings, rudders, propellers, buoyancy, and weapons use simple force-based approximations. Welded assemblies are the intended way to make separate blocks behave as one machine. The current weapon projectiles are physical moving objects; advanced damage, explosions, target health, and full rope-tethered harpoon behavior are not implemented yet. Complex assemblies may still need further physics tuning.


## Grid-block machine building

The construction model is now a simple square-tile builder inspired by physics-based vehicle-building games:

- Every part is placed on a **32 × 32 world grid** as a square block tile. Parts no longer need to be positioned by eye.
- Place a block beside another block and the game automatically creates a hidden rigid weld between their touching faces. There are no visible attachment nodes or manual weld steps for ordinary construction.
- Click any block in a connected machine to select and move the entire welded assembly. Shift-click can add or remove whole assemblies from a selection.
- Dragging a machine keeps its blocks aligned to the grid. Press **R** to rotate the selected blocks by 90 degrees.
- Block-to-block collision is disabled inside the same welded assembly, so adjacent tiles don't push themselves apart.
- Engines and driven wheels apply forces to their entire welded machine. Rudders apply turning torque to the assembly; propellers and wings also act on the complete connected build.
- The inspector is simplified: select one part to activate it and tune its settings; select multiple blocks to save the assembly as a reusable part or delete it.
- The previous connector drawer, wire display, visible port nodes, mounting-node selectors, and manual multi-part weld workflow are hidden or removed from the main building flow. Existing saved builds are loaded without logic wires, and adjacent grid blocks are automatically joined when a save is restored.

### Quick vehicle build

1. Place FRAME blocks in a rectangle or long chassis. Each touching block automatically welds to its neighbors.
2. Place WHEEL blocks on the lower edge of the chassis, adjacent to it.
3. Place an ENGINE block at the rear or front of the chassis, pointing in the direction you want to travel. Rotate with **R** before placing if needed.
4. Select the engine and press **Activate mechanism** in the inspector.
5. Press Play. The engine pushes the complete welded vehicle; the wheels provide driven traction when activated.
6. Add ARMOR, FLOATS, PROPELLERS, WINGS, or weapons as additional grid blocks.

### Current physics scope

Welded assemblies share movement through face-to-face constraints and group force / torque application. This is a lightweight 2D arcade physics implementation rather than a full rigid-body solver: complex high-speed collisions, very large assemblies, and intricate multi-joint mechanisms still need further tuning and browser playtesting.
