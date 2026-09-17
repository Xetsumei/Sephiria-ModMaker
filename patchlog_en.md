# Sephiria ModMaker — Update history

## 2.5.23 — 2026-09-17

- Choose which individual constant stats to share with your party. Shared rows receive a **Stat sharing** label in the game tooltip.
- Stat conversion and reservation now support maximum HP, maximum MP and related values, also available to activation criteria and damage formulas. Fixed several stats, including defense, critical damage and elemental amplification, being read as zero.
- Corrected usage-count tooltips for limited-use artifacts after dropping or selling them.
- Fixed **buff lost** effects being skipped when a buff linked to an item is removed as that item is lost. Applies to both normal and active artifacts.

After updating the editor, use **Install to game** to update the bundled runtime to 2.5.23 too. Mods saved with this version require runtime 2.5.23 or later.

## 2.5.22 — 2026-09-16

- Added an **asset library** to the vanilla browser. Read images, frame animations and original animation data from the installed game without launching it, then search, preview and import them.
- Image and animation browse buttons also open the library. Imports preserve image pivots, in-game scale, animation FPS and looping information.
- Search and preview sound effects and BGM, then select them for weapon attack sounds. The extraction tool is bundled; no separate Python installation is needed.

## 2.5.21 — 2026-09-16

- Updated the distribution files.


## 2.5.20 — 2026-09-16

- Fixed **trigger effects on active artifacts never running**. The editor let you author them, but the game dropped them entirely. Active artifacts now handle triggers exactly like normal ones.
- Updated the distribution files.


## 2.5.19 — 2026-09-16

- Fixed ModMaker-provided stats (merchant stock, merchant legendary stock, merchant money, potion drink speed, miniboss reward dice, and the existing size stats) showing in game only as **"(unknown stat)"** in 2.5.18. The stats were re-registered in the wrong order and dropped out of the game's stat table.
- Updated the distribution files.


## 2.5.18 — 2026-09-16

- Fixed item tooltips showing **another artifact's description**. A single stat name the game does not know kept the tooltip from refreshing at all; now only that one stat line is skipped.
- **Merchant stock, merchant legendary stock, merchant money, potion drink speed and miniboss reward dice** are now supported by ModMaker itself, so they work without any additional add-on.
- These stats ship with names and descriptions, and their **tooltip line writes itself** (for example, "Merchants in a new area stock 2 more artifacts") — no effect text needed.
- Stats registered by other add-ons are hidden from the stat list, because they do nothing for players who do not have that add-on. Mods already built with such a stat still save normally. (Run the game once to refresh the reference dump.)
- List rows now render color and bold tags in names **as they look**, instead of printing the tags as text.
- Updated the distribution files.


## 2.5.17 — 2026-09-16

- README and patch notes are available in the GitHub repository and are not included in release ZIPs.
- The editor checks for updates on every launch. A new version opens an update dialog; dismiss it to update later from the banner. Automatic dialogs respect disabled checks and skipped versions.

- Updated the distribution files.


## 2.5.16 — 2026-09-16

- Updated the distribution files.


## 2.5.15 — 2026-09-16

- Updated the distribution files.


## 2.5.14 — 2026-09-16

- Item effect descriptions can include values for each level, with a preview.
- Updated the distribution files.


## 2.5.13 — 2026-09-15

- Updated the included documentation.

## 2.5.12 — 2026-09-15

- Release update history is available in the `patchlog` files.

## 2.5.11 — 2026-09-15

- The editor checks for new releases at startup. Click Update now to download and restart it.
- Check manually under Tools → Check for updates. Automatic checks can be disabled, and individual versions can be skipped.
- Failed update checks no longer report that you are up to date.
- Updates preserve your mods and settings. If replacement fails, the original files are restored.
