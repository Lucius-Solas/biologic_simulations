# biologic_simulations

A 2-D evolution and game-theory simulation inspired by the evolution-of-aggression model.

## Quick start

Open **`simulation.html`** in any modern browser – no build step or server required.

## What you will see

| Colour | Species | Strategy |
|--------|---------|----------|
| 🔵 Blue | Blue creature | Shares food with other blues |
| 🔴 Red  | Red creature  | Fights for food against everyone |
| 🟢 Green | Food | Spawns automatically |

## Rules

* Each creature starts with **15 frames of lifespan** (ticks down every frame except while eating).
* Food (green pixel) spawns automatically every **15 frames** (~5 s at the default FPS of 3).
* Creatures detect food within a **15-unit vision radius** and move toward it.
* Eating takes **3 frames** (no lifespan loss during eating).
* Solo eating restores **+15 lifespan**.
* When two creatures reach the same food (within a **3-unit interaction radius**):
  * **Blue × Blue** → each gets **+7** lifespan (share)
  * **Red × Red**  → each gets **+4** lifespan (costly fight)
  * **Red × Blue** → Red gets **+12**, Blue gets **+3** (red wins)
* A third creature that arrives at occupied food is **blocked** and must wander away.
* If a creature's lifespan would exceed **18** after eating, it **reproduces** (spawns a copy nearby).
* Creatures move at **1 unit per frame** using a smooth wander behaviour that keeps a
  consistent heading (updated by ±30° every few frames) so they cover ground efficiently.

## Configuration

All tunable constants are at the top of the `<script>` block in `simulation.html`:

| Variable | Default | Description |
|----------|---------|-------------|
| `GRID_SIZE` | `10` | Screen pixels per simulation unit (the "10×10 grid" scale) |
| `WORLD_W` / `WORLD_H` | `80` / `60` | World dimensions in simulation units |
| `FPS` | `3` | Target frames per second |
| `INITIAL_BLUE` | `6` | Starting blue creatures |
| `INITIAL_RED` | `6` | Starting red creatures |
| `INITIAL_FOOD` | `20` | Starting food items |
| `FOOD_SPAWN_INTERVAL` | `15` | Frames between automatic food spawns |
| `LIFESPAN` | `15` | Starting lifespan (frames) |
| `EATING_TIME` | `3` | Frames to consume one food item |
| `REPRODUCE_THRESHOLD` | `18` | Lifespan above which the creature reproduces |
| `VISION_RANGE` | `15` | Food detection radius (sim units) |
| `INTERACTION_RADIUS` | `3` | Radius around food for encounters (sim units) |
| `SPEED` | `1` | Movement speed (sim units per frame) |
