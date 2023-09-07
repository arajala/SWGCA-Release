# SWG Combat Analysis

SWG Combat Analysis is a log parsing tool for Star Wars Galaxies, built in particular for SWG Legends, although you may find it works for other versions of the game.

## Current Version

The current version is Beta Build V1.0. This is the third published version and supports 'offline' log analysis, as well as a minimal, first version of 'realtime' log analysis where SWGCA can sit on top of the SWG window and show updates on the fly. As a Beta Build, it likely has undiscovered bugs and is not intended for widespread public use. If you've come across it, you're welcome to try it, but please don't judge my unfinished hacking.

## How To Use

### Prerequisites

In SWG's in-game `Chat` options, make sure `Combat Message Filter` is set to `All`, and choose `Verbose Combat Messages` and check all available boxes. Also make sure to check `Timestamp Incoming Messages`, or else DPS calculations are not possible.

### Setup Tab

Start here to configure the `Log File` by browsing to it or pasting the filepath. This is generally a `_chatlog.txt` file in `<your SWG install directory\profiles\<your profile name>\Omega\`.

You can also see the build version here and configure the following settings.

#### Show NPCs as players

Check the box to include NPCs in the sorted list of damage dealers, damage takers, and healers. For a long chat log, showing NPCs will tend to make the list *very* long, as it includes *all* NPCs that have created any log message within your configured combat log range, whether it related to your group's activity or not.

__NOTE__: Detection of whether a character is an NPC or PC is *not* robust, as there is no definitive indication in the chat log one way or the other. Leaving the box unchecked will exclude many NPCs, especially those from common heroics, but not all. NPCs that have names that fit the player character creation guidelines (1 or 2 words, no reserved words) will be falsely detected as PCs. Future updates of the tool may hardcode more NPC names for correct detection.

#### Keep SWGCA on top

Check the box to make the SWGCA window stay on top of all other Windows applications, including SWG *if* SWG is running in Borderless Window mode. If SWG is in Fullscreen mode, it will not work. In SWG, start logging, and create a macro (looped or manual trigger) to type `/logchat` *twice* (toggle it off, then back on) to force a refresh of the log file, which will trigger an update of SWGCA.

### Damage Tab

This tab shows information about the damage done from the perspective of your own player (and your group, if looking at PvE content). The default list shows total damage and DPS estimates of all player characters. Selecting a specific player will update the list to show enemies that player has dealt damage to. Selecting a specific enemy will update the list to show damage any players have dealt to that enemy.

The throughput column shows how much of your raw, outgoing damage actually lands on the target (after armor absorption and defense rolls).

The window on the right shows detailed statistics such as min/max hits, and effective combat roll results. By default, the statistics are calculated on all attacks done by any player in the damage list.

Single-click on a character in the list to update the statistics window on the right to refer only to that characters's attacks. Single-click on any whitespace to return to the default all-character statistics.

__NOTE__: In the damage tab, the defensive statistics (miss, dodge, block, etc.) refer to how often the attacker's outgoing attacks were missed, dodged, blocked, etc. by their targets.

Double-click on a player to jump into a detailed view of skills and weapons they used. Double-click on any skill or weapon to see all individual events of that type. Double click on any individual event to see the exact message that was logged from the game.

### Defense Tab

This tab shows information about the damage taken from the perspective of your own player (and your group, if looking at PvE content). The default list shows total damage take and TPS estimates of all player characters. Selecting a specific player will update the list to show enemies that dealt damage to that player. Selecting a specific enemy will update the list to show damage dealt to all players by that enemy.

The mitigation column is the inverse of the damage tab's throughput - how much of the raw, incoming damage actually lands on you (after armor absorption and defense rolls).

The leader of the total defense column will be who tanked the most in the group, but the leader of the mitigation column could be who has the tankiest build.

The window on the right shows detailed statistics such as min/max hits, and effective combat roll results. By default, the statistics are calculated on all attacks done to any character in the damage list.

Single-click on a character to update the statistics window to refer only to that character's incoming damage. Single-click on any whitespace to return to the default all-character statistics.

__NOTE__: In the defense tab, the offensive statistics (crit, strikethrough, etc.) refer to how often the *defenders* were crit, struckthrough, etc. by their attackers.

Double-click on a character to jump into a detailed view of the skills and weapons they were hit by. Double-click on any skill or weapon to see all individual events of that type. Double click on any individual event to see the exact message that was logged from the game.

### Healing Tab

This tab shows a list of players who healed others in the log.

The window on the right shows the minimal statistics that are available for healing events.

Single-click on a character to update the statistics window to refer only to that character's healing data. Single-click on any whitespace to return to the default all-character statistics.

Double-click on a character to see all individual events from that character. Double click on any individual event to see the exact message that was logged from the game.

### Session

Log analysis is separated by login sessions. Every time you login to your character, a chat message is logged with the time and date. SWG Combat Analysis separates all combat messages logged by this login time and date, and you can select a session in the Session drop down box on the top-right.

### Player

All player (or NPC, if the appropriate setting is enabled) characters that appeared in at least 1 combat event in the session should appear in this dropdown. Selecting one will update all tabs to only show relevant information from the perspective of this player.

__NOTE__: Detection of whether a character is an NPC or PC is *not* robust, as there is no definitive indication in the chat log one way or the other. Leaving the box unchecked will exclude many NPCs, especially those from common heroics, but not all. NPCs that have names that fit the player character creation guidelines (1 or 2 words, no reserved words) will be falsely detected as PCs. Future updates of the tool may hardcode more NPC names for correct detection.

### Enemy

All characters that appeared in at least 1 combat event in the session should appear in this dropdown. Selecting one will update all tabs to only show relevant information involving this enemy. In the healing tab, this is the friendly target receiving heals, rather than an "enemy".

### Period

This is disabled and will be added with future features. It will allow you to see a realtime DPS leaderboard only for the most recent N seconds (whatever duration is selected in the Period dropdown).

### ^ Button

This button in the far top-right will bring you back to the top-level 'all-characters' view of the given tab, if you have double-clicked into any of the detailed views.

Re-selecting the session from the dropdown has the same effect as pressing this button.
