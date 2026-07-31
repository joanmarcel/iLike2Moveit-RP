<p align="center">
  <img src="pack.png" alt="iLike2Moveit" width="180">
</p>

<h1 align="center">iLike2Moveit</h1>

<p align="center">
  <a href="https://github.com/joanmarcel/iLike2Moveit-RP/releases/latest"><img src="https://img.shields.io/github/v/release/joanmarcel/iLike2Moveit-RP?label=release" alt="Latest release"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue" alt="License"></a>
  <img src="https://img.shields.io/badge/Minecraft-1.21.1-brightgreen" alt="Minecraft 1.21.1">
  <img src="https://img.shields.io/badge/requires-EMF%20%2B%20ETF-orange" alt="Requires EMF and ETF">
</p>

A Minecraft **Java Edition** resource pack that brings livelier, more expressive animation to vanilla
mobs, using OptiFine CEM through the **EMF + ETF** mods.

It is built to **extend Fresh Animations, not replace it**. Each mob is hand-rigged and added one at a
time, and everything not covered yet keeps animating through FA. The roster grows with every release.

Inspired by Fresh Animations and by the lively, exaggerated style of Bedrock animation packs.

<!--
GALLERY — uncomment this block once the files exist in screenshots/.
See screenshots/README.md for the shot list and the capture settings.

## Gallery

| | |
|:---:|:---:|
| ![Villager](screenshots/villager.png) | ![Iron Golem](screenshots/iron-golem.png) |
| **Villager** — biome and profession outfits | **Iron Golem** — walk cycle and pelvis sway |
| ![Wolf](screenshots/wolf.png) | ![Cat](screenshots/cat.png) |
| **Wolf** — sit and stand-up transitions | **Cat** — 11 breeds |
| ![Chicken](screenshots/chicken.png) | ![Fox](screenshots/fox.png) |
| **Chicken** — hen, chick, rooster | **Fox** — run, sit, sleep, stalk |
-->


---

## Works with Fresh Animations

This pack overrides **only** the mobs listed below. Every other mob in the game keeps its Fresh
Animations behaviour untouched — that's the point of the design, not a limitation. As new mobs are
finished they move from FA's side to this pack's side, one release at a time.

### Load order matters

⚠️ Resource pack order is **not cosmetic here**. Get it wrong and nothing changes at all.

In **Options → Resource Packs**, iLike2Moveit must sit **above** Fresh Animations in the *Selected*
column. The pack at the top wins.

In `options.txt` the same order reads left to right, with later entries winning:

```
resourcePacks:["vanilla","Fresh Animations","Fresh Animations Extensions","iLike2Moveit-v1.0.zip"]
```

If iLike2Moveit ends up **below** FA, Fresh Animations' models win and you will see no change whatsoever.
That is the single most common installation mistake.

<p align="center">
  <img src="screenshots/load-order.png" alt="A correct resource pack order, with iLike2Moveit above Fresh Animations" width="420">
</p>

The `Weskersons3DItems` entry at the top of that screenshot is **optional and not part of this pack**. It
gives villagers and foxes 3D held items instead of flat ones, but it needs the companion mod plus
Modefite and Puzzle. Without those, leave it out — held items render in 2D, which is the expected
fallback.

---

## Mobs covered so far

| Mob | What you get |
|---|---|
| **Villager** | Adult and baby models, awake and sleeping variants, 7 biome outfits, 14 profession outfits, randomized skin tones per villager, name easter eggs |
| **Iron Golem** | Rebuilt geometry with a full walking cycle and idle pelvis sway |
| **Wolf** | Adult and pup, layered textures, sit and stand-up transitions with planted paws |
| **Cat** | Adult and kitten, 11 breed textures |
| **Chicken** | Hen, chick, rooster, plus warm and cold biome variants |
| **Fox** | Adult, red kit and arctic kit, with run, sit, sleep and stalk animation |
| **Pig** | Warm variant — **new geometry, animation still to come** |

**The pig is the current exception.** It ships with its new model but no animation yet, so it will stand
still instead of using FA's pig animation. Animating it is next on the list. Every other mob either
appears above with full animation, or isn't touched by this pack at all and keeps its FA behaviour.

---

## Requirements

This pack does **not** work on its own. It needs the OptiFine CEM implementation provided by EMF and ETF.

| | Tested version |
|---|---|
| Minecraft Java | **1.21.1** |
| Loader | **NeoForge 1.21.1**, Java 21 |
| **EMF** (Entity Model Features) | **3.2.4** |
| **ETF** (Entity Texture Features) | **7.1** |

`pack.mcmeta` declares `pack_format 34` with `supported_formats 34–64`. Other loaders and Minecraft
versions may work, but the combination above is the only one verified.

### Required: turn off `asmMaths`

**The villager will not animate until EMF's `asmMaths` option is off.** Two ways to get there — pick one:

**Either install the [iLike2MoveIt companion mod](https://github.com/joanmarcel/iLike2Moveit-Mod).** It
turns the option off for you at load time, in memory, and never rewrites your config file. Nothing else
to do.

**Or edit the config yourself.** Open `config/entity_model_features.json` and set:

```json
"asmMaths": false
```

**Why it's needed.** EMF 3.x compiles each animation into a single bytecode method, and this pack's
animation block (~152k characters) exceeds the JVM's 64 KB per-method limit, throwing
`MethodTooLargeException`. With `asmMaths` off, EMF uses its expression interpreter instead, which has no
such limit. It costs slightly more CPU and works correctly.

Do not mix EMF 2.x with ETF 7.x — that combination fails with
`NoSuchMethodError: EntityIntLRU.defaultReturnValue`.

---

## Installation

1. Install **EMF 3.2.4** and **ETF 7.1** into `mods/`.
2. Install the companion mod, **or** set `"asmMaths": false` yourself (see above). One or the other —
   without it the villager stands still.
3. Download `iLike2Moveit-vX.Y.zip` from the [Releases](../../releases) page.
4. Drop it into your `resourcepacks/` folder.
5. Enable it in **Options → Resource Packs**, and make sure it sits **above Fresh Animations**
   (see [Load order matters](#load-order-matters)).

### The companion mod

A separate client-side mod, [**iLike2MoveIt — Mod**](https://github.com/joanmarcel/iLike2Moveit-Mod),
does two things. It handles the `asmMaths` setting for you, and it adds behaviour the resource pack
alone cannot express: the trade item following the villager's hands, wolf reunion and cat lie-down
signals, and warm/cold/rooster chicken compatibility on Java 1.21.1. It requires VanillaBackport
1.1.7.10 and Platform 1.3.3.

The pack works without it, as long as you set `asmMaths` yourself — you just won't get those extras.

---

## Troubleshooting

**Nothing changes at all.**
Load order, nine times out of ten: the pack is below Fresh Animations. It can also mean EMF/ETF isn't
installed. Press F3+T to reload and check the log for EMF/ETF startup errors.

**The mob renders in the new style but stands perfectly still.**
Almost always the `asmMaths` setting. Confirm it's `false`, restart, and check the log for
`MethodTooLargeException`. If it's the pig, that's expected — see the roster above.

**A mob still looks like plain Fresh Animations.**
It probably isn't covered yet. Check the roster above; if it's not listed, FA is doing its job.

**Held items look flat.**
That's expected without the optional 3D item setup — see the note under the load-order screenshot. The
2D fallback is deliberate, and you should never get a magenta cube.

---

## Reporting bugs and contributing

Open an [issue](../../issues) — the bug template asks for the mob, the pack version, your EMF/ETF
versions and a screenshot. Those four things are what make a rendering bug reproducible.

Pull requests are welcome for textures and variant routing. By opening one you confirm the work is your
own and that you license it under CC BY-NC-SA 4.0.

Merges are handled by the repository owner.

---

## License

This pack is released under
[**CC BY-NC-SA 4.0**](https://creativecommons.org/licenses/by-nc-sa/4.0/). You may share and adapt it
for non-commercial purposes, with attribution, under the same license.

That license covers the work created by this project: the CEM rigs, the molang animation curves, the
`.properties` model-swap and randomization logic, and the layered clothing system.

### About this project

iLike2MoveIt is an independent, non-commercial fan project, inspired by Fresh Animations and by the
lively, exaggerated style of Bedrock animation packs. It is **not affiliated with or endorsed by** any
other pack, addon or studio.

## Community

Discord: **https://discord.gg/45YFupj5Q7** — for questions, screenshots and anything that is not a bug
report.
