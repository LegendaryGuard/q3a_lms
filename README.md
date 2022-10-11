Q3A Last Man Standing source code
===============================

A Quake 3 Arena gamemode was started from the late 90s to early 2000s.

<p align="center">
<img alt="q3lms" src="" width=440 />
</p>

### History

Started: 1999 <br/> 
Ended: 2000

Last Man Standing (LMS for short) is a free for all variant of Elimination with a few minor twists.

The game is played in rounds. The goal of the game is to survive for as long as possible in each round and preferably make sure that your closest competitors don't survive for too long.

Each player begins with all weapons (ammo quantity selectable using variables), can't hurt himself with his own weapons, and there are no items in the maps. When you get fragged, you will have to wait until the end of the round.

By default Overtime (OT) is used so there can be at most 1 survivor each round.

Players might have multiple lives. If you set \g_lms_lives higher than 1, players will have more lives before they are out from each round: when someone is killed, he immediately returns in game (like in standard Free For All mode); when he runs out of lives, he will have to wait until the end of the round. You can see players' lives holding TAB key.

### How to build

- Windows:

Execute `build.bat` to compile qvms, keep in mind you must be in the repository directory.

Once compiled successfully, look for `pak9.pk3`, copy and paste into `baseq3/` or mod Q3 game directory.

### Credits

SantaClaws