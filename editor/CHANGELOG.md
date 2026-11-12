# Editor changelog

- For plugin authors: two methods on `Game_Enemy` to replace instead of working around. `rrActionPatterns()` returns the action patterns an enemy chooses from, and the turn-based, Action and Tactical battle modes now all read them through it, so a plugin that gives an enemy other skills changes one method and every mode follows. `rrEquipSource()` returns the rows an enemy's equipment is first read from, so a plugin can equip an enemy from somewhere other than its database entry. Both return the database lists by default, so nothing changes for a project without such a plugin. (runtime 20261112.1)
- Effekseer animations keep up to 16000 particles at once instead of Effekseer's default 4000 (runtime 20261110.1), in the game and in the editor's animation previews. A full pool used to skip every new particle silently, so a big effect lost its later layers (an HDR effect and its companion, or one effect on several targets, share the pool). Each context reserves about 80 MB of Effekseer's memory for it instead of about 20 MB; `Graphics.effekseerContextSettings` holds the numbers.
- HDR sidecars can blend a second grade in over the effect with `gradeB` and `gradeKeys` (`[[frame, weight], ...]`, weight 0..1, straight lines between keys) on the effect's own clock (runtime 20261108.1). Older runtimes ignore both and play `grade`.
- Distortion layers of screen animations drawn in the battle scene bend the scene again instead of drawing a dark copy of it (runtime 20261104.1). WebGL refused Effekseer's backdrop copy from the alpha-less canvas, leaving the backdrop black; the scene is now blitted into an RGBA square first, its off-screen margins repeating the screen's edges.
- HDR sidecars can animate their bloom intensity over the effect with `bloom.intensityKeys` (`[[frame, intensity], ...]`, straight lines between keys) on the effect's own clock, slow motion included (runtime 20261031.2). Editor previews follow the keys; older runtimes play `bloom.intensity`.
- HDR sidecars can pair an ordinary companion with shared seed, transforms and lifetime, drawn before HDR light with optional depth occlusion (runtime 20261031.1). Missing companions select the graded twin; editor previews use the same pairing.
- Treasure chests wait for room. Conditional Branch › Reactor has **Can Receive** [Item/Weapon/Armor] [entry] × [amount], true when the whole amount fits under the cap the game reports when the event runs (`$gameParty.maxItems`, so VisuStella's `<Max: x>` and Reactor's limits apply); a missing entry is false. It saves as a tagged Script condition, reopens in the dialog, reads as "Can Receive Item: #1 Potion × 5" in the list, and stays a plain Script once edited by hand. Quick Event › Treasure adds **Check Inventory Space** (on by default) and a **Failure Message**: an item, weapon or armor chest opens, gives and sets Self Switch A only inside that branch, and a full party gets the message with the chest left closed for another try. Gold chests, and existing events, are unchanged. The Treasure dialog's Message field now reaches the event in the editor's language even when left untouched (it fell back to English). Guide: [docs/INVENTORY-CAPACITY.md](../docs/INVENTORY-CAPACITY.md).

The full technical list, one file per release or labeled development checkpoint, newest first. The short version of each release is in the [root changelog](../CHANGELOG.md).

- [0.99.5](changelog/0.99.5.md) - 2026-11-12
- [0.99.4](changelog/0.99.4.md) - 2026-11-02
- [0.99.3](changelog/0.99.3.md) - 2026-10-29
- [0.99.2](changelog/0.99.2.md) - 2026-10-25
- [0.99.1](changelog/0.99.1.md) - 2026-10-24
- [0.99.0](changelog/0.99.0.md) - 2026-10-12
- [0.98.9](changelog/0.98.9.md) (unreleased checkpoint; continued in 0.99.0)
- [0.98.8](changelog/0.98.8.md) - 2026-09-28
- [0.98.7](changelog/0.98.7.md) - 2026-09-21
- [0.98.6](changelog/0.98.6.md) - 2026-09-14
- [0.98.5](changelog/0.98.5.md) - 2026-09-07
- [0.98.4](changelog/0.98.4.md) - 2026-08-31
- [0.98.3](changelog/0.98.3.md) - 2026-08-24
- [0.98.2](changelog/0.98.2.md) - 2026-08-16
- [0.98.1](changelog/0.98.1.md) - 2026-08-11
- [0.98.0](changelog/0.98.0.md) - 2026-08-10
- [0.97.0](changelog/0.97.0.md) - 2026-08-03
- [0.96.0](changelog/0.96.0.md) - 2026-07-27
- [0.95.0](changelog/0.95.0.md) - 2026-07-20
- [0.94.8](changelog/0.94.8.md) - 2026-07-13
- [0.94.7](changelog/0.94.7.md) - 2026-07-13
- [0.94.5](changelog/0.94.5.md) - 2026-07-12
- [0.94.4](changelog/0.94.4.md) - 2026-07-11
- [0.94.3](changelog/0.94.3.md) - 2026-07-10
- [0.94.2](changelog/0.94.2.md) - 2026-07-10
- [0.94.1](changelog/0.94.1.md) - 2026-07-05
- [0.94](changelog/0.94.md) - 2026-06-27
- [0.93.1](changelog/0.93.1.md) - 2026-06-21
- [0.93.0](changelog/0.93.0.md) - 2026-06-21
- [0.91](changelog/0.91.md) - 2026-06-18
- [0.9.0](changelog/0.9.0.md) - 2026-05-31
- [0.8.0](changelog/0.8.0.md) - 2026-05-24
- [0.7.0](changelog/0.7.0.md) - 2026-02-15
- [0.6.0](changelog/0.6.0.md) - 2026-02-14
- [0.5.0](changelog/0.5.0.md) - 2026-02-14
- [0.4.5](changelog/0.4.5.md) - 2026-02-14
- [0.1.0](changelog/0.1.0.md) - 2024-11-18
