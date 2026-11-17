# LOGIC — Engineering Sandbox

A browser-based, top-down 2D engineering sandbox. The first playable foundation focuses on free construction, node-based digital logic, editing quality-of-life, and local blueprints.

## Run

Open `index.html` in a modern browser, or enable GitHub Pages for the repository and publish from the `main` branch root. No build step, server, account, or external dependency is required.

## Phase 1 + Phase 2 features

- Infinite-feeling pan/zoom canvas with grid and snap controls
- Compact, searchable component library with logic, I/O, mechanical, electrical, sensor, structure, and computing categories
- Refined inspector with clearer empty, single-selection, and multi-selection states
- Mobile slide-out component browser and inspector
- Component placement, selection, multi-selection, move, rotate, delete
- Node-to-node connections with live signal visualization and ports that follow component rotation
- Working Boolean gates: AND, OR, NOT, XOR, NAND, NOR, XNOR, BUFFER
- Multi-pass signal propagation so connected combinational logic settles through longer chains within a simulation tick
- DEMUX signal routing
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

Phase 2 strengthens the editor and digital-logic runtime. Mechanical physics, circuit-level electrical solving, advanced computing simulation, and fully encapsulated custom-component execution remain future systems. The custom component library and reusable blueprint workflow are early foundations, not yet a full nested-subcircuit runtime.

Projects and blueprints are stored locally in the browser. Export JSON files to back up or move work between browsers.
