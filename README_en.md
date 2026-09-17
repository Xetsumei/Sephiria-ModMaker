# Sephiria ModMaker

For manual installation, download **only SephiriaModMaker-version.zip** from the release. **You do not need to download update.json or put it in the installation folder.** The updater reads it to check the version and verify the download. Using the update command in the editor also handles the ZIP download for you.

- README and patch notes are available in the GitHub repository and are not included in release ZIPs.
- The editor checks for updates on every launch. A new version opens an update dialog; dismiss it to update later from the banner. Automatic dialogs respect disabled checks and skipped versions.

[한국어](README_ko.md) · [English](README_en.md) · [日本語](README_jp.md) · [中文](README_zh.md)

## 2.5.24 — 2026-09-17

- Redesigned the **Asset library** window. It now opens as a thumbnail grid and can switch to a list view. Added per-type result counts, sorting, thumbnail size, zoom and background options, and shortcuts to other animations of the same subject. Scrolling stays smooth even with a very large library.
- Added **save backups and autosave**. Each save keeps the previous `mod.json` in the mod folder's `.modmaker-backups` (10 copies by default), and the editor now asks before the first save overwrites a folder that already contains a mod. Autosave can be toggled and its interval changed in Settings (10 minutes by default). Open backups from **Save backups** in the Tools menu.
- Fixed values oscillating endlessly when stat conversion fixed elemental damage or moved it to another element, interacting with the **Highest elemental damage** bonus.
- Fixed artifacts with an **on first pickup** effect still appearing unused after the effect had fired.
- Stats that potions grant without a duration are now applied the same way as vanilla potions. Fixed them disappearing after continuing a save or carrying over into the next run.

After updating the editor, use **Install to game** to update the bundled runtime to 2.5.24 too. Mods saved with this version require runtime 2.5.24 or later.

Full update history: [한국어](patchlog_ko.md) · [English](patchlog_en.md) · [日本語](patchlog_jp.md) · [中文](patchlog_zh.md)

## Using the asset library

Open the asset library in the vanilla browser and read the game assets. The first scan takes time and does not require launching the game. Search by name, type or source file, and preview images, frame animations and sounds.

Save your mod, then use the image or animation browse button to import into `Assets/Library`. Keep the `.sprite.json` beside each PNG to preserve its pivot and in-game scale. The file picker still accepts PNG, GIF and frame folders. Sounds are stored as game event references, not extracted as WAV files. Importing an animation does not copy attack logic, events or AI.

## Sharing individual stats

Enable **Party share** on each constant-stat row you want to share. **Share all effects with your party** overrides the individual selections without erasing them. Shared stats are marked at the end of their game tooltip rows.

## 2.5.11

- The editor checks for new releases at startup. Click Update now to download and restart it.
- Check manually under Tools → Check for updates. Automatic checks can be disabled, and individual versions can be skipped.
- Failed update checks no longer report that you are up to date.
- Updates preserve your mods and settings. If replacement fails, the original files are restored.

After updating the editor, use Install to game to update the bundled game runtime too. Older builds without automatic updates need one manual ZIP installation first.

A tool for making Sephiria mods without writing code.
Fill in the fields in the editor and it produces a `mod.json`; a runtime running inside the game reads it and builds the actual items, weapons, magic and enemies.
Installing to the game and building a package for other players are both one button.

[한국어](README.md) · **English** · [日本語](README_jp.md) · [中文](README_zh.md)

The editor UI is available in Korean / Japanese / English / Chinese.

## Workflow

Check your work in the order `Save → Validate → Install to game`. The game itself is started from `Launch game` in the `Tools` menu or with `F5`. Files for other players are built with `Create package`. Draft storage, draft recovery and the example startup menu have been removed.

Artifact copy limits, stat inputs in the game's own display units, and inventory inversion labels have been added. Stat values in an existing `mod.json` are preserved as they are. Undo, fixed content IDs and save and install backups all continue to work. Projects saved in this version require runtime 2.5.24.

---

## Installation

1. Download the zip from [Releases](https://github.com/Xetsumei/Sephiria-ModMaker/releases) and extract it anywhere.
2. Install [.NET Desktop Runtime 10](https://dotnet.microsoft.com/download/dotnet/10.0).
3. Run `ModMakerEditor.exe`.

The game folder is detected on first launch. If it is not found, set it in `Preferences`.

Opening the editor does not modify the game on its own. The bundled runtime and the installed copy are compared and applied when you press `Install to game`. If you want it installed automatically at startup, turn that on in the settings.
Status and reinstall are under `Preferences` → `ModMaker Runtime`.

No separate loader is needed. The game's built-in add-on loader reads it as is.

---

## Quick Start

1. `New mod`, then pick an empty folder. `mod.json` and `Assets/` are created.
2. In the `Mod info` tab, fill in mod ID, display name and author. `New content start ID` is the numbering base for new content. Numbers given to your items, weapons and magic survive sorting and deletion.
3. `Items` tab, then `Add`. Set the internal name, type and rarity, then the display text and an icon PNG (16×16 to 32×32 pixel art recommended).
4. Add stats under `Passive stats`. Click a stat field to search by ID, name or description. Per-level values are comma separated and need **(max level + 1)** entries.
5. Press `Validate`, then `Install to game`, then start the game with `F5`. Start a new run and your content shows up in rewards and shops.

> Add-ons load when you enter a game session, not at the title screen. You need to reach the lobby or a run.

To check things quickly, set `"testGiveItems": true` in `AddOns\ModMakerRuntime\config.json`. Every custom item is granted once when you enter a run.
Set it back to `false` before sharing. `Create package` turns it off automatically.

---

## What You Can Make

| Type | Contents |
|---|---|
| **Artifact** | Passive stats and triggered effects. Activation criteria, appearance rules, cosmetic attachments, screen effects, stat conversion, stat occupation |
| **Active Artifact** | Used from the quick slot. No MP, just its own cooldown |
| **Stone Tablet** | Level bonuses on nearby cells. Can also lift criteria and invert levels |
| **Potion** | Actions to run when drunk |
| **Grimoire** | An item that carries a spell |
| **Companion Token** | Summons a companion. **Game monsters can be used as companions directly** |
| **Buff** | Duration and stacks. Permanent buffs supported |
| **Perk** | Stats per level and level 5/10/20 bonuses |
| **Combo** | A new item category with set effects by count |
| **Miracle** | A blessing chosen between floors |
| **Destiny Engraving**\* | An unlock node bought with sapphires at the village tree |
| **Keyword** | A `<tag=…>` name for descriptions, with color and icon |
| **Stat** | A new stat name your mod counts itself |
| **Weapon**\* | A derivative of an existing weapon. Sprites, per-hit values, projectiles, crossbow specs, on-hit buffs |
| **Magic**\* | Adjust an existing spell. **Buff magic** also gets its behavior built for you |
| **Enemy Tweaks**\* | HP, damage, speed and size of vanilla enemies and bosses |
| **New Enemies**\* | Clone an existing monster and place it on floors by replacement or addition |
| **Costume**\* | Character stats and starting gear |
| **Companion Unit**\* | Adjust an existing monster’s HP, move speed and body size |
| **Item Patch**\* | Price, rarity and stats of existing items, plus icon, name and flavor text |
| **Combo Patch**\* | Rewrite the tier table of a vanilla combo |
| **Costume Patch**\* | Stats and starting items of existing characters |

\* Marked entries are still in development. They may not work as expected, so use them with care. Opening one of those tabs shows the same notice at the top of the editor.

Images and frame animations can be imported or replaced. New attack logic, AI and spell behavior are limited to what each form supports; other behavior requires scripts.
For behavior the forms cannot express, write a [custom script](#custom-c-scripts).

---

## Items

### Triggered Effects

Stack `trigger + condition + action` like cards. Common combinations are available as one-click templates.

* **36 triggers:** kill, taking damage, hit, miss, evade, dodge, parry, counter, guard success/break, revive, buff/debuff gained or lost, battle start/end, potion, breaking props, MP spent, gold gained, stage entry, game clear, every N seconds, first pickup, HP/MP healed, per amount of HP/MP lost or healed, HP/MP crossing a percentage
* **26 actions:** heal HP/MP (% and flat), self damage, spend MP, shield, raise max HP/MP, give or take gold, give, remove or upgrade items, random item, reroll dice, temporary stats, permanent stats (for the run), apply or remove buffs, brief invulnerability, stun immunity, fire a projectile, on-screen message
* **Fire a projectile** borrows a projectile from a weapon of your choice and sets damage, element, stagger and pierce count. Pierce 1 stops at the first target hit, 0 keeps flying until its lifetime runs out. Leave it empty to keep the borrowed projectile's own value.
* **Attack kind** is one of basic attack, dash attack, special attack, own attack and monster attack. The first four borrow from a weapon, the last one borrows from a monster.
* **Monster attack** takes a monster first and then one of that monster's attack slots. Monsters carry their attacks in the same data weapons use, so it fires as it is. Only monsters with a borrowable attack are listed, and both fields must be filled before anything fires. The list fills once you enter the game with the runtime installed.
* **Conditions:** proc chance (per level), cooldown, HP/MP ratio, in combat only

> For effects that must expire reliably, use `Apply buff` instead of `Apply temporary stat`. Buffs go through the game's own buff system, so the icon, remaining time and stacks show up in the UI.

Artifacts that grow over time are also possible with forms alone.

* `Permanent` in the Buffs tab makes a buff that never expires.
* `Remove when the item is lost` on `Apply buff` must be on for permanent buffs. Without it, picking up and dropping the item repeatedly stacks the effect forever.
* `Max total` on `Apply temporary stat` expresses "1 per hit, up to 50" directly.
* `Show total` on `Apply permanent stat` and `Show cooldown` on the effect row display the value as an on-screen icon. The runtime creates those display buffs for you.

### Activation Criteria

Restrict when an artifact is active. The game itself only has 10 built-in criteria, but `★ Custom` lets you stack conditions row by row. **All rows must hold at the same time.**

| Condition | What it looks at |
|---|---|
| Inventory position | Inside, edge, top/bottom row, left/right end, both end columns, corner |
| Specific row / column | Nth row from the top, Nth column from the left |
| Neighbors and detailed surroundings | Up, down, left, right, diagonals, all 8 cells × artifact / active / grimoire / companion / tablet / potion / empty / any item / a given combo / a given item / item whose name contains text |
| Whole inventory | N or more of the above |
| HP, MP, gold | Full, not full, at or below N%, at or above N% |
| Your stat value | A named stat above or below a value |
| Active buffs | Any, buffs only, debuffs only |
| Floor, in combat, this artifact's level | As written |

Each row can be flipped with `Invert` and tightened with `All` (every listed cell must match).
`Auto-write description` fills the `Activation condition` field in the text tab with a sentence matching your conditions. That line goes straight into the tooltip and you can edit it.

Turn on `Cannot ignore criteria` and criteria-lifting tablets or engravings will not work on this artifact.

> HP, MP and combat conditions can only be evaluated while the item is held, so they do not affect the placement preview. The game's own `when HP is full` criterion behaves the same way.

The game only re-evaluates criteria when the inventory changes. So the runtime watches only the artifacts whose conditions shift during combat, such as HP or stats, checking them every 0.25 seconds and refreshing just that one when the answer changes. Turn it off with `watchDynamicCriteria` in `config.json`.

### Appearance Rules

The same condition table decides whether an item can appear in rewards and shops. Position-based conditions are excluded since the item is not in the inventory yet.
If you set a single-weapon restriction, the item only appears while that weapon is equipped and the tooltip marks it as exclusive.

### Cosmetic Attachments

The same slot the game uses for the Absolute Ring glowing on the weapon grip or the Agma Projection Blade floating wings behind your back.

* Attach to the player body (rises with jumps), the ground position (stays on the floor), the weapon grip, or the weapon blade.
* Set `Follow` to lag behind for a wing or cape trailing feel.
* Offset (1 is 16 pixels), size, draw order, tint, minimum upgrade level and flip with facing are all configurable.
* If activation criteria are set, the attachment can be shown only while the effect is on.

Sprite fields take a single PNG or a folder. A folder plays its PNGs as frames in name order. Pick a GIF and the editor extracts it into a PNG folder for you.

> Purely cosmetic. It has nothing to do with hitboxes or damage.

### Screen Effects

Effects applied to your own screen while the conditions hold. The same slot as the game's blue ring.

`Overlay` · `Tint` · `Vignette` · `Saturation` · `Grayscale` · `Brightness` · `Contrast` · `Hue shift` · `Invert` · `Shake` · `Zoom` · `Glitch` · `Distortion` · `Black screen` · `Blue ring`

Anchor (full, sides, top, bottom), intensity, fade in and out, repeat interval and a breathing pulse are set per row. Effects can also be shared with party members.

### Stat Conversion

Converts the excess of one stat into another. The same idea as Berut's Scythe turning critical chance above 100% into execution chance, and you can wire any stat into any other.

### Stat Occupation

Locks up part of one stat and raises another in exchange. The same slot the Orb of Craving uses to occupy MP for magic damage.

Occupying MP uses the game's own reserved MP, so it shows as the purple bar. Any other stat is simply reduced by that amount.
The granted value can be listed per level with commas, and you can cap it. The tooltip line is generated for you in the same word order the Orb of Craving uses, so there is nothing to write by hand.

> Only about half of the game's 300-odd stat keys have a display name. Occupying a nameless stat prints the raw key in the tooltip, so type a name into the `Occupied stat name` field.

### Tablet Grid

On the 7×7 grid, **left click +1 / right click −1 / middle click clears**.
A single cell can carry a level together with `Ignore criteria` (blue) and `Invert level` (purple). When stacked, the game sums all levels first and then applies the inversion.
Cells the game cannot express (more than 4 straight, more than 1 diagonal) are locked. Special rules such as `CHECKERBOARD` go in the `Advanced (text)` tab.

### Dual Artifacts

Set by the `Create as dual artifact` checkbox. Picking two combos does not make an item dual on its own; the game has 15 items with two combos that are not dual.
Rarity is independent of dual status. Dual is not a grade that replaces rarity, it is a marker on top of it. Checking the box fills in `Rare` by default, following vanilla convention.

---

## Weapons

Weapons are made **only as derivatives** of existing weapons. Behavior and motion come from the template weapon; you change sprites, numbers and names.

> The weapon list, hit counts and type-specific attacks come from the game. Enter a run once with the runtime installed before the weapon tab fills in.

* **Template weapon** is the original you clone. **Parent weapon** is the weapon that upgrades into yours. If the parent is tier 1, yours is tier 2. When typing an ID, `0` is not empty but Sword and Shield tier 1, so use `-1` to clear it.
* **Hit values** are one row per hit, and the template decides how many rows there are. Basic fields are multiplier, element, stagger and knockback; `Advanced` adds hitstop, forward motion, bonus damage per MP, aim assist, hit tags and damage formula. Empty fields keep the template value.
* **Who it hits** sets the target side (enemies or allies) and can turn damage into healing, with a heal ratio for how much.
* **Projectile sprite** swaps the art of whatever that hit fires, along with pivot and rotation.
* **Projectile movement** covers speed multiplier, lifetime, pierce, scale, homing and homing strength, wall collision behavior and bounce count.
* **Burst fire** gives a shot count and an interval in milliseconds.
* **On-hit buffs and debuffs** can be applied to the target or to yourself.
* **Elements** are limited to physical, fire, ice and lightning. Other elements have no matching elemental stat to multiply, so damage drops sharply.
* **Type-specific attacks** appear as separate fields for some weapons. The fire staff, for example, never uses the basic combo. If your basic combo edits do nothing in game, look here.
* **Crossbow specs** are magazine size, magazine count, reload time and fire interval. Crossbow lineages can only be chained to crossbows.
* **Sprites** are the journal and anvil images plus the in-world sprites (body, sub or shield, blade overlay, head). Parts the template does not have are locked. Pivots inherit from the template if left empty, so they rarely need touching.

`Reset to template defaults` puts everything back at any time.

---

## Magic

Clone an existing spell and change name, icon, MP cost per level, cooldown, uses, cast speed, element line and label color. Your spell shows up in game once you make a `Grimoire` item and pick it under `Spell to use`.

* **Template behavior** uses the existing spell’s behavior. What flies out and how it bursts stays with the cloned spell.
* **Buff magic** has its behavior built by this tool. Casting heals HP and applies a buff, optionally to every nearby party member. MP cost and blocking a cast without enough MP are handled by the game.

> Healing over time belongs on the buff. The game's `HP_REGEN` is healing per 10 seconds, so healing 4 per second for 5 seconds means duration 5 with `HP_REGEN 40`.

---

## Characters (Costumes)

Clone an existing costume and change its stats, starting items and default weapon. The character appears on the selection screen. State transitions and hitboxes come from the cloned costume.

---

## Companions

A companion artifact summons a unit, switches it to the owner's faction and makes the owner its leader. The game already does the faction switch, so **enemy monsters work as companions as they are.**

* **To use a game monster directly**, set the item type to `Companion Token` and pick it under `Unit to summon`. The choices are the units marked `Can be a companion` in the `Units` tab of `Vanilla Reference`.
* **To draw your own**, use the `Companions` tab to clone a vanilla monster and change sprites, name, HP, move speed and body size. Your unit then appears in the artifact's `Unit to summon` field too.

Attack power, revive time and per-level growth live on the artifact, not the unit.

> Bosses and mini-bosses cannot be used. Their dedicated AI holds the phases and staging.
> Attack patterns and movement (AI) cannot be authored. `Monster to clone` is effectively the choice of how it fights.
> `Body size` is the value used to find a spawn spot. Enlarging only the sprite without it spawns the companion stuck in a wall.

---

## Enemies

* **Enemy Tweaks** edits HP multiplier, bonus damage, move speed, size, pattern interval and stats of vanilla enemies and bosses. Target by AI class name, prefab name or unit ID; leave it empty to hit the whole category. Empty fields stay vanilla. Values are applied once per spawn on the host side.
* **New Enemies** clones a vanilla monster with new sprites, name and numbers, then places it on floors. Replacement leaves floor layout and counts untouched and is the safest option; adding to waves raises difficulty accordingly.

Writing new patterns or reordering them cannot be expressed in forms, since every boss has its own code. Use a custom script. Creating the script project also generates a `SampleEnemy.cs` example.

---

## Other Tabs

* **Perks** are stats per level plus level 5/10/20 bonuses. Leave the frame empty and it borrows a vanilla perk frame tinted with your color; leave a level bonus icon empty and it borrows the vanilla art for that tier.
* **Combos** are new item categories with set effects by count.
* **Miracles** are blessings chosen between floors. Once picked, their stats stay for the rest of the run.
* **Destiny Engravings** are unlock nodes bought with sapphires at the village tree. Nodes you make attach after their prerequisite and unlock items with `Requires unlock` enabled. Comma separated sapphire prices make a node you can buy multiple times.
* **Keywords** are the `<tag=…>` names used in descriptions. Give them a color and icon and they behave exactly like vanilla keywords. Names that already exist in the game are skipped.
* **Stats** are new stat names your mod counts. The game's stats are a single dictionary of labeled numbers, so registering a name is enough for it to accumulate and be read like a vanilla stat. The game will not use it on its own, so wire it up through activation criteria (`Your stat value`) or stat conversion.

---

## Patching Vanilla

* **Item Patch** changes price, sapphire price, rarity, categories, max level and stats of existing items, and swaps icon, name and flavor text.
* **Combo Patch** rewrites the tier table of a vanilla combo. Use `Load vanilla values` to fill in the current table and edit from there. Vanilla only has 2, 3, 4, 5 and 6 item tiers, but there is no limit here, so a 20 item tier works. Writing even one row replaces the vanilla table entirely.
* **Costume Patch** adjusts stats, starting items and default weapon of existing characters.

Patches hold for the current session. Restart the game to revert them.

---

## Vanilla Reference

So you do not have to check things in game, the runtime's readings are shown across six tabs. The search box applies to all six.

* **Items** type, rarity, price, max level, combos, criteria, stats
* **Weapons** weapon family, upgrade tier, parent weapon, hit count, sprite slots used, body sprite pivot, type-specific attack slots, crossbow specs
* **Perks** max level, stats per level, level 5/10/20 bonuses
* **Combos** fruit name, number of vanilla items using it, set effects per tier, whether it is usable
* **Buffs** duration, max stacks, granted stats, implementing class
* **Units** faction, disposition, AI, whether it can be a companion

Select a row and press `Create patch from selection` to turn it into an item patch on the spot.

> A combo marked not usable is a category that is registered but used by no item and has no effect (`PARTY`, for example). Picking it does nothing, so it is dropped from the item tab's choices automatically.

---

## Editor Conveniences

* **Searching lists** Every left-hand list has a search box. It matches the display name and the internal name, and Korean names also match on **initial consonants alone** (ㄱㅁㅅ finds 고물상); typed syllables and initial consonants can be mixed. Names in the other languages match too, even though the list does not show them. Filtering hides rows instead of removing them, so the order never shifts, and a folder stays visible only while something inside it matches. Esc clears the box, ↓ and Enter move down into the list.
* **Organizing lists** Right click anywhere in a left-hand list to insert separators and folders. Items do not join a folder just by sitting below it; only what you drop into it goes in. Drag to the far left to pull something back out. Rename with `F2`. These markers are editor-only, have no effect in game, and only their positions are stored in `mod.json`.
* **Drag to reorder** works in every left-hand list. Multiple rows can be moved at once, and there is a duplicate button.
* **Import from another mod** copies content from another mod into yours. The source is not modified. Opening a folder with `mod.json` carries triggered effects across as they are; reading an installed mod carries numbers, text and structure only, since behavior written in C# cannot come along. The second method needs one game launch with that mod and the runtime installed before the list exists.
* **Validate** separates errors that block saving from informational warnings. Errors are internal name violations and duplicates, per-level value count mismatches, and unknown stat IDs. Warnings include missing icons, items with no effect, `<tag=…>` values the game does not have, and low start IDs.
* **Languages** The editor UI is changed in `Preferences`; saving restarts the editor automatically. The button always keeps the word `Preferences`, so you can find your way back from a language you cannot read. Text inside your mod is configured in the `Mod info` tab by picking a base language and extra translation languages.

### The In-Game `ModMaker Info` Window

`ModMaker Info` in the options screen shows the runtime version and the installed mod list.

* Click a mod row to enable or disable it. `[ Apply Changes ]` saves and quits the game; the change takes effect on the next launch. It is hidden during a run because it would break saves.
* `Show mod name in item descriptions` appends a `#ModName` line to every custom item description. This one applies immediately and leaves the original text intact when turned off.
* `Only show rooms from players with the same mods` is on from the start. See [Multiplayer](#multiplayer) below.

---

## Custom C# Scripts

For behavior the forms cannot express, write it yourself. ModMaker handles the plumbing, so one class is all you need.

1. Expand `Advanced custom script` and press `Open script project`. A `Scripts/` project is created in your mod folder with game DLL references, target framework and output path already set.
2. Write a class.

   ```csharp
   public class BloodPact : ModMakerCharm
   {
       public override void OnCharmEffectRefreshed()
       {
           base.OnCharmEffectRefreshed();
           Log($"Level {Level}");
       }
   }
   ```
3. `Build scripts` produces `Scripts.dll` in the mod folder.
4. Type the class name into the `Custom script` field.

| Base class | Used for | Game class it extends |
|---|---|---|
| `ModMakerCharm` | Items | `Charm_StatusInstance` |
| `ModMakerPerk` | Perk bonuses | `PassiveObject` |
| `ModMakerWeaponAddon` | Weapons | `WeaponAddon` |
| `ModMakerEnemy` | Enemies | `MonoBehaviour` |

Passive stats, text, icons, IDs and translations still come from the form. Only the behavior is yours.

Use `DealDamage` when dealing damage directly.

```csharp
DealDamage(target, 30f, EDamageElementalType.Fire);
```

The game groups dealt damage by `DamageInstance.id` for the results screen. An unknown string shows up as `Name (Unknown)`. `DealDamage` uses the ID ModMaker created for that content, so it is tallied under its name and icon.
To split by effect, register an ID with `ModMakerDamage.Register("MyMod_Echo", "Echo")` and pass it to `ModMakerDamage.Deal(...)`.

> * One `Build scripts` compiles every script in the mod into a single `Scripts.dll`. Each build refreshes the game DLL references and checks that the class names typed into the forms actually exist.
> * Building needs the .NET SDK.
> * Mirror's `SyncVar` requires weaving and cannot be added from a mod. Keep state in plain fields.
> * Exceptions are isolated so the rest of your content survives, but check `Player.log`.
> * **Sharing a mod with scripts means the recipient runs arbitrary code.** Say so when you distribute it.
> * Every usable class and name can be found by opening the game's `Sephiria_Data\Managed\Assembly-CSharp.dll` in ILSpy or dnSpy.

---

## Multiplayer

**While you have mods enabled, only players with the same mods can see each other in the room list.**

The game has no channel for asking which add-ons a player has installed from the room list.
It does, however, **already filter rooms by a single version string.** Creating a room writes that value into the Steam lobby info (`HandleCreated`), and the room list **does not draw rooms whose version differs from yours at all** (`HandleFound`). Joining by code and Steam invites compare the same value, and even if that were bypassed, connection authentication (`HorayNetworkAuthenticator`) rejects it.

So the runtime appends **the names and versions of your enabled mods** after the version string.

```
1.2.3                              vanilla
1.2.3 +MM[mycharms v1.0.0]         one mod enabled
1.2.3 +MM[4#8f2c1a90]              long lists collapse into a count and a fingerprint (the filtering is the same)
```

This exists to prevent someone who does not have your custom items from joining, receiving unknown IDs and ending up with a broken save.

* **The mod lists must match exactly.** Even the same mod at a different version can shift item numbering, so you cannot play together. Load order does not matter; the string is always sorted by name.
* **With no mods enabled, nothing is appended.** Someone who only installed the runtime still plays with vanilla users.
* Turn it off with `Only show rooms from players with the same mods` in the in-game `ModMaker Info` window, or `"lockMultiplayer": false` in `config.json`. It applies immediately, but **a room you already created carries the version string from the moment it was made**, so you have to recreate the room.
* Apart from filtering rooms, the version string is only used for display and for a record field in the save, and nothing in the game reads that field back for comparison. **Saves are unaffected.**
* If another add-on touches the same place, several markers are appended. In that case only players who also have that add-on can see your rooms.

---

## Distribution

`Create package` produces a zip the recipient only has to extract. It includes the game-relative folder structure and an install note.

| Option | Contents |
|---|---|
| **Include runtime** | The recipient does not need to install the runtime separately |
| **Single archive** | Packs the mod structure into one `mod.pak` file |
| **Encrypt mod** | Stops people from opening the folder and copying it as is |

> Packed mods only load on ModMaker Runtime 0.4.0 or later.
> Encryption is not real protection. The game has to read it, so the runtime can always unpack it.

**Do not zip it yourself.** Handing over the whole `AddOns` folder ships `testGiveItems` still enabled, drags other people's mods from `Mods\` along, and includes cache files. `Create package` handles all three.

> **Multiplayer**: everyone playing together needs the same mod installed. An item's network ID is a hash of `modID:itemName`, so the same mod matches on every side.

---

## Troubleshooting

### The mod does not show up in game

Nothing is displayed on screen. Check the log.

```
C:\Users\<user>\AppData\LocalLow\TEAMHORAY\Sephiria\Player.log
```

Open Player.log in the Tools menu opens that folder with the file selected.

A healthy load looks like this.

```
[AddOnLoader] ✓ 'ModMaker Runtime' v2.5.24 by ModMaker
[ModMakerRuntime] Mod found: My Mod v1.0.0 (3 items, 0 patches)
```

If there is nothing at all, the runtime is not installed. Reinstall from `Preferences` → `ModMaker Runtime`.
If `[AddOnLoader]` is there but `[ModMakerRuntime]` is not, you have not reached the lobby or a run yet.

### My changes are not applied

The game needs a restart after value changes. If you suspect the editor, check the `build` timestamp in the title bar; you may be running an old copy.

### The weapon tab fields are empty

The weapon list, hit counts, type-specific attacks and crossbow specs come from the game. They are generated once you enter a run with the runtime installed. The same notice can appear right after updating ModMaker.

### I changed weapon values but nothing changed in game

Some weapon types never use the basic combo. Hit something with your custom weapon and `Player.log` records which data was actually used.

```
[ModMakerRuntime] 'MyMod/MyBlade': basic hit 1 fired, data 'Weapon_GreatSword_Attack1(M)-MM'
```

A name ending in `-MM` means ModMaker's values were used. Otherwise that weapon used its own attack data. Turn the log off with `"logWeaponAttacks": false` in `config.json`.

### My weapon does not appear in the upgrade list

The anvil shows only 3 random candidates out of the parent's upgrades. With 8 to 10 candidates per tier 1 weapon, not seeing it immediately is normal. Reroll with dice or check in the training area. Whether it registered at all is recorded in `Player.log`.

### The stat list is short, or I get "unknown stat ID"

Some stats such as `CRITICAL` only appear after launching the game once. Entering a run builds the full list and the editor keeps a copy. While the list is incomplete, an unknown ID does not block saving.

### An error dialog appeared in the editor

Your work is kept and you can continue. Details are written to `%TEMP%\modmaker_error.log`.

---

## Limitations

* Images and frame animations can be imported or replaced. New attack logic, AI and spell behavior are limited to what each form supports; other behavior requires scripts.
* Weapon hit counts cannot be changed. The motion decides how many times you swing.
* Crossbows can only upgrade from crossbows, and cannot upgrade into non-crossbow weapons.
* The weapon tab's lists and the Vanilla Reference need one game launch to fill in.
* New stats can be registered but the game will not use them on its own. They only mean something once wired through activation criteria or stat conversion.
* HP, MP and combat conditions in custom activation criteria do not affect the placement preview.
* Custom magic supports adjustments to existing templates and buff magic. New cast behavior or projectiles are not possible.
* State transitions and hitboxes come from the cloned costume.
* Attack patterns and movement come from the cloned monster.
* Bosses cannot be used as companions.
* For custom companions to look right in multiplayer, both sides need the same mod installed.
* Features marked as still in development have not finished in-game verification.
* Building custom scripts needs the .NET SDK, and a game update may require rebuilding.
* There is no automatic substitution such as `{VALUE}` in effect text. Write the numbers yourself.
* Content IDs are written into save data. Item, weapon and magic numbers are fixed automatically and removed numbers stay reserved. Keep your mod ID and the game's `id-map.json`.

---

---

## License

This repository is distributed under the [MIT License](LICENSE).
See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for the copyright and
license notices of third-party libraries included in distributions.

---

## Disclaimer

Sephiria ©TEAM HORAY.
Sephiria Mod Maker by **Xetsumei**. This is an unofficial modding tool for Sephiria.
Built with the assistance of Claude.

Contact: Discord `Xetsumei`

This repository and its contributors are in no way affiliated with Sephiria, TEAM HORAY, or any related organizations.
Game assets are not included in this repository, and you should not redistribute game files when sharing mods.

## Hide from Journal / Training (2.5.5)

Enable **Hide from Journal / Training** at the top of the item details to hide an item from both lists and prevent retrieving it there. This also applies to journal search and favorites, and bulk retrieval of training favorites. Items already obtained remain usable.

Reward, shop, unlock and dimensional-pocket rules stay unchanged. To make a secret artifact obtainable only through a specific item effect, also enable **Exclude from rewards**. This is saved as `hideFromJournalAndTraining` in JSON; existing mods without the field remain visible. Use editor and game runtime version 2.5.5 or later.
