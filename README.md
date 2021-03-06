# Better Curses
Better Curses module for Foundry VTT

## Features

This module for the DND5e system exists to make it easier to run games where someone has a persistent effect that deals damage when hit with an attack, such as [Hunter's Mark](https://www.dndbeyond.com/spells/hunters-mark) or Hex.

To begin, select the item that can afflict the curse. For the purpose of example, Hunter's Mark will be used.

### Setting up the Curse item

Edit the Item and go to the "Curse" tab.

![Blank Curse tab on Hunter's Mark item](./img/blankCurseTab.png)

From here you can define whether the item is a curse, and give it a unique name. This name cannot have spaces, as the damage calculations rely on Roll's `_replaceData` function, which also cannot have spaces. You can also define what type of attacks trigger the curse.
Hunter's Mark deals 1d6 damage when hit with a weapon attack, so:

![Filled Curse tab on Hunter's Mark item](./img/filledCurseTab.png)

### Applying the Curse

To apply a curse to a target, run the script `BetterCurses.curse([Curse Name as defined above])` while having the curser selected, and the target targeted.
The module comes with a compendium pack with two macros, one simply setting a variable space for you to apply the curse.

#### Removing the curse

If you attempt to apply the curse to a target when they are already cursed by that actor, then it will remove the curse for that target from that curser.

## Installation

Install using the manifest URL: `https://raw.githubusercontent.com/Wigsinator/betterCurses/master/src/module.json`

## Module Compatibility

This module relies on the DnD5e system. Version 2.0 and greater requires Foundry 0.7.5 or higher, but will be fundamentally more compatible with other modules than version 1.0.

### Version >2.0

Version 2.0 and greater of this module relies on the Active Effects system of Foundry 0.7 and up. There is a chance that another module will use the same naming scheme for Active Effects as I did, and this would likely cause problems. If such a module pops up, or you have any other problems, please raise an issue in GitHub issues and/or ping me on The Foundry Discord @Wigsinator#2306. I can't guarantee I can fix the problem, but I can at least look into making it work.

### Version <=1.0.1

This module, in its functioning, hijacks use of the Item5e's rollDamage function. Any other module that also affects this function, or any module that bypasses the function entirely when rolling damage, is likely to cause problems with this module. If such a module pops up, please raise an issue in GitHub issues and/or ping me on The Foundry Discord @Wigsinator#2306. I can't guarantee I can fix the problem, but I can at least look into making it work.

One such module is MESS. Mess bypasses the rollDamage function entirely when using modified rolling, opting instead for its own internal getDmgData function. Seeing as I have no access to this function from outside the module, fixing compatibility with MESS modified rolling is impossible. I'm very sorry.

## List of functionality to create

- [x] Overhaul logic in preparation for version 0.7.x of Foundry
- [ ] Make it easier to know who is cursed, and by whom
- [x] Add a function to clear all curses affecting a target
- [ ] Alter targeting rules so that curses can only target one user
- [ ] Set other persistent effects, such as disadvantage on ability checks