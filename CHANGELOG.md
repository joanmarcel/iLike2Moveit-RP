# Changelog

All notable changes to this pack are documented here. Versions match the `pack.mcmeta` version shown in
the in-game resource pack list.

## v1.1.0-beta.2 — minor model changes and companion mod compatibility

Minor changes to the model files, and better compatibility with the companion mod.

**Changed**

- Small clean-ups across the model files. Nothing you will notice in game — everything looks and
  behaves as before.
- The pack name is now written consistently as **iLike2MoveIt**, including in the in-game resource
  pack list.

**Better together with the companion mod**

- The [companion mod](https://github.com/joanmarcel/iLike2Moveit-Mod) has its own public repository
  now. It handles EMF's `asmMaths` setting for you and unlocks the parts that need code: the villager's
  trade item following the animated hands, the fox's Zzz particles, the wolf reunion greeting, and the
  warm chicken and pig variants. The pack still works without it.

**Worth mentioning, from the previous release**

- The wolf's water shake used to rotate the whole body as a single rigid block. It now shakes properly,
  with the body roll frozen on the vanilla parent so the motion comes from the rig. This landed in the
  first release but was never written down.

**Known limitations**

- The pig ships with its new model but no animation yet.

## v1.0.0-beta.1 — first public release

**Mobs covered**

- **Villager** — adult and baby models, awake and sleeping variants, 7 biome outfits, 14 profession
  outfits, randomized skin tones per villager, and name easter eggs.
- **Iron Golem** — rebuilt geometry with a full walking cycle and idle pelvis sway.
- **Wolf** — adult and pup, layered textures, sit and stand-up transitions with planted paws.
- **Cat** — adult and kitten, 11 breed textures.
- **Chicken** — hen, chick, rooster, plus warm and cold biome variants.
- **Fox** — adult, red kit and arctic kit, with run, sit, sleep and stalk animation.
- **Pig** — warm variant, new geometry only.

**Known limitations**

- The pig has no animation yet. Because the pack ships its model, the pig will not fall back to Fresh
  Animations' animation — it stands still until its animation is ported.
- Verified on NeoForge 1.21.1 with EMF 3.2.4 and ETF 7.1 only. Other loaders and versions are untested.
- Requires `"asmMaths": false` in the EMF config; without it the villager does not animate.
