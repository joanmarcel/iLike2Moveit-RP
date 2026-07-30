# Changelog

All notable changes to this pack are documented here. Versions match the `pack.mcmeta` version shown in
the in-game resource pack list.

## v1.0 — first public release

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
