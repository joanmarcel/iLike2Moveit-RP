# Changelog

All notable changes to this pack are documented here. Versions match the `pack.mcmeta` version shown in
the in-game resource pack list.

## v1.1.2-beta.4 — baby presentations and model consistency

This release adds selectable Tiny Takeover baby presentations and refines model, texture and attachment behavior across the existing sixteen-mob roster. Pair it with Core v0.2.1-beta.2 for the corresponding model selectors and rendering fixes.

**Current pairing:** Core v0.2.1-beta.2 is currently available for NeoForge; its Fabric release is pending.

**Changed**

- Tiny Takeover baby presentations for chicken, wolf, cat, ocelot, pig and rabbit coexist with their Classic options.
- Cat and ocelot baby models use isolated layers; texture routing and upper body/tail UVs are corrected.
- Baby rabbits receive a corrected vertical offset. Fox mouth items and iron-golem flowers use animated attachment points.
- Sheep baby base and tintable wool use complementary masks, with dedicated sheared routing; adult Classic and Alternate presentations remain separate.
- Existing turn, pose and model refinements are consolidated into one pack.

**Installation and limitations**

- Minecraft 1.21.1 with EMF/ETF and the Fresh Animations stack. Keep iLike2MoveIt above its base packs.
- Install matching Core and VanillaBackport dependencies for Core-backed selectors and behavior.
- The roster remains sixteen mobs. Deferred animation tiers, riding poses and extreme transition/world-generation cases remain documented limitations; this release does not claim full coverage of every combination.

## v1.1.1-beta.3 — nine new mobs and a fully animated pig

The roster grows from seven mobs to sixteen. This release adds nine complete ports, turns the pig
from a static model into one of the pack's most detailed animated mobs, and tightens the existing
cat, wolf and chicken ports without changing the Fresh Animations fallback for everything else.

**New mobs**

- **Rabbit** — rebuilt adult geometry and colour atlases, breathing and look tracking, short and long
  hops, jump/fall poses, landing bounce and stepped turns.
- **Ocelot** — a dedicated wild-feline port with walk/run/sneak, swimming, breathing, look tracking,
  random idles, turn-in-place and airborne poses, without domestic cat states.
- **Wandering Trader** — its own geometry and textures, swimming, drinking, airborne motion and
  different passenger poses for boats and minecarts.
- **Turtle** — adult, baby and hatchling models with breathing, land movement, swimming, airborne
  poses, landing bounce, blinking and look tracking.
- **Frog** — all three climate variants, articulated hands and feet, walking, turning, swimming,
  jumping, landing, blinking, tongue attacks and the full croak/inflate gesture.
- **Dolphin** — adult and calf presentation, swimming, idle motion, look tracking, blinking, a
  water-to-beached state machine and the named tonina variant.
- **Cow** — animated temperate, warm and cold adults and calves, a persistent Birch Forest breed and
  the named bull/lidia presentation with its own model and texture.
- **Mooshroom** — red and brown adults and calves using the cow animation rig, with dedicated atlases
  and all six adult mushrooms restored.
- **Sheep** — adult and lamb geometry, correctly separated tintable wool, walking/running, breathing,
  grazing, turning, random idles, swimming and airborne/landing motion.

**Major upgrades**

- **Pig** — now has adult and piglet models, 21 authored clips, walk/run/turn, jump/fall/bounce,
  collective resting, climate and persistent breeds, tusks, name variants and dedicated saddle
  layers. Server-backed resting and persistent custom breeds require Core on both client and server.
- **Cat and ocelot** — the shared feline gait keeps every leg attached to the moving torso. Cat
  resting, sleeping head direction, seated turns and posture transitions are smoother.
- **Wolf** — standing/seated calibration, resting look tracking, seated turn supports and the seams
  between sit, rest and stand have been refined.
- **Chicken** — chick placement, adult leg UVs and turn-in-place animation are corrected across the
  base, rooster and climate models.

**Reliability and maintenance**

- Every distributed model is checked against the mob-version registry before a ZIP can replace the
  active pack, preventing a valid but incomplete release from silently dropping a mob.
- Runtime models, animation clips and active build contracts use functional public names throughout;
  release-time and build-time audits reject private identifiers and attribution leaks.
- Source-to-pack builds preserve the approved runtime output while keeping historical evidence out of
  the distributed ZIP.

**Known limitations**

- Rabbit still uses the adult model path for young animals and does not yet include its random-idle
  pool.
- Frog and sheep do not yet have their planned riding poses; the frog's nocturnal variant and the
  sheep's persistent snowy breed remain future work.
- Some extreme pig/cow transition and world-generation combinations remain on the visual UAT matrix,
  although their automated build and routing checks pass.

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
