# Foundry-Tavern-Games

# The Mules Master Ledger: Tavern Game Suite
### A Persistence-Based Game Collection for Foundry VTT

This suite provides a collection of interactive mini-games designed to transform tabletop taverns into living hubs of activity. It features a centralized Master Ledger that automatically tracks player progress, betting pools, and standings using hidden chat metadata.

## The Core Innovation: Persistence via Chat Scraping
Traditional Foundry macros often lose temporary variable data when a player refreshes their browser or a session ends. This suite solves that problem through a persistent data engine.
* **Metadata Storage:** Game states (gold, rounds, dice remaining) are stored in hidden HTML tags within chat messages.
* **Universal Scraper:** Macros scan the chat history to reconstruct the current state of a game instantly.
* **The Reset Wall:** A specialized Tavern Game Reset macro places a marker in the chat log. The Ledger and all games ignore data preceding this marker, allowing for fresh tournament starts without clearing your entire chat history.

---

## Game Profiles

### Dead Eye Dice
*Flavor:* A game of high stakes and dwindling odds. Originally a pirate's game used to settle disputes without blood, each die represents a part of the player's luck.
* **Mechanics:** Players start with a hand of six dice (d20, d12, d10, d8, d6, d4). 
* **The Dead Eye:** Any die that rolls a 1 is considered a "Dead Eye" and is removed from the player's hand.
* **Winning:** Rounds continue until only one player has dice remaining.

### Chimera Shots
*Flavor:* Named after the mythical three-headed beast, this game tests a traveler's constitution against three distinct infusions.
* **The Heads:**
    * Lion's Head: Smooth bourbon. A palate cleanser.
    * Dragon's Head: Spicy fire-sauce. Requires a DC 14 CON Save or the player takes Stomach Damage.
    * Goat's Head: Curdled sour milk. Requires a CON Save with a DC that increases by 2 for every Goat shot taken.
* **Failure:** Accumulate Stomach Damage until you forfeit or reach your limit and vomit.

### 18 Mules
*Flavor:* Based on the task of securing gear to a pack animal. One too many ropes and the whole thing snaps.
* **Mechanics:** A push-your-luck game where players attempt to roll as close to 18 as possible without going over.
* **The Golden Wagon:** Rolling exactly 18 is a perfect success, granting maximum points in the Ledger.
* The number of mules you have (i.e. your total) when you decide to stop adding is the number of points you get, first to 100 wins.

### The Great Critter Race
*Flavor:* A fully automated betting system for animal racing. Each animal has a unique movement formula based on its "vibe."
* The Racers:
* Dog: The Reliable Pro. Moves a steady 2d4.
* Fox: The Sprinter. Moves 1d4 plus 2. Quick and never stumbles.
* Pig: The Wildcard. Moves 1d8 minus 1. Fast, but easily distracted.
* Rat: The Chaotic Blur. Moves 1d12. Unpredictable burst speed that can dominate or fail.
* Badger: The Underdog. Moves 1d6. Slow, but keeps on going.

*DM/Player Sync:* Players use a betting macro to generate tickets; the DM macro calculates the race and automates the payouts based on the odds.

### Beast Rodeo
*Flavor:* A test of strength and agility where the ground is harder than it looks.
* **Mechanics:** A series of contested rolls. The rider uses Strength (Athletics) or Dexterity (Acrobatics) to stay mounted while the beast attempts to buck them. 
* **House Rule:** Once a player falls, the ride is over. The Ledger records the highest number of rounds survived.

### Dragonchess
*Flavor:* A battle of wits where the board is as complex as the battlefield.
* **Mechanics:** A Best-of-3 series of contested Intelligence checks simulating tactical maneuvering across a three-tiered board.

### The King's Vault
*Flavor:* A shell game involving silver cups and a hidden coin.
* **Mechanics:** A test of Wisdom (Perception). Players wager gold or silver; a success doubles the wager, while a failure adds the coin to the tavern's coffers.

---

## The Master Ledger
Executing the Ledger macro generates a comprehensive report in the chat sidebar. It identifies all active players and displays:
1. Active Pots: Total gold wagered in Dead Eye, Chimera Shots, and 18 Mules.
2. Player Standings: Current HP, remaining dice, and total wins.
3. Live Statistics: Data is compiled in real-time from the chat log.

---

## Setup and Installation

### Requirements
* Foundry VTT (v11, v12, or v13).
* Monk's Active Tile Triggers: Required to trigger macros via player interaction with scene objects.

### Installation
1. Create a new Script Macro for each file in this repository.
2. At the start of a session, run the Tavern Game Reset macro.
3. Create a Tile in your scene (e.g., a bottle for Chimera Shots or a dice tray for Dead Eye).
4. In the Monk's Active Tile Trigger settings, set the action to "Run Macro" and select the corresponding script. 
5. Ensure "Run as GM" is unchecked for game macros so they record data for the specific player who clicked the tile.
