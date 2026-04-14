# biologic_simulations

A 2-D evolution and game-theory simulation.

## Quick start

Open **`simulation.html`** in any modern browser – no build step or server required.

## What you will see

| Colour | Entity | Behavior |
|--------|--------|----------|
| 🔵 Blue | Blue creature | Shares food with non-red creatures |
| 🟣 Purple | Purple creature | Same behavior as blue |
| 🔴 Red  | Red creature | Fights for food; optional predation mode |
| 🟢 Green | Food | Spawns automatically |

## Rules

* Each creature starts with **22 frames of lifespan** (ticks down every frame except while eating).
* Food spawns automatically every frame by default.
* Creatures detect food within a **18-unit vision radius**.
* Eating takes **3 frames** (no lifespan loss during eating).
* Solo food resolution gives **+15 lifespan**.
* Two-creature food interactions:
  * **Blue/Purple × Blue/Purple** → each gets **+7** lifespan.
  * **Red × Red** → each gets **+4** lifespan.
  * **Red × Blue/Purple** → Red gets **+12**, other gets **+3**.
* If lifespan exceeds the reproduce threshold (**25**), one child is spawned nearby.
* Offspring start moving in the opposite direction of the parent.
* Optional **Red predation mode**:
  * Red no longer seeks food.
  * Red moves **50% faster**.
  * Red-vs-red food interactions are disabled while predation mode is on.
  * On contact with a non-red creature, there is a **30% chance** to consume it.
  * If the chance fails, both creatures survive and continue moving normally.

## Interface

* Title: **The Game of Death**.
* Left panel: simulation world, stats, and controls.
* Right panel: population graph (lines for blue, red, purple).
* Graph shows the latest **50 frames** by default and can be scrolled horizontally to inspect earlier frames.
* Controls include:
  * Pause / Resume
  * Reset
  * Time scale slider (slow down / speed up)
  * Red predation mode toggle
