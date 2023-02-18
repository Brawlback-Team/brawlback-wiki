# Replays Documentation

## Introduction
With the introduction of Slippi to the Melee scene, the bar for the quality of replays has risen. While true that Brawl has existing "replays", these "replays" are just a collection of inputs, RNG values, and game settings locked behind a file that is encrypted and compressed using algorithms unknown to anyone, meaning you can't do anything particularly interesting with them. The goal of the replays portion of this project is to open up the replay format for Brawl to make them more Slippi-like; files that have compression/encryption methods known to developers and users alike so that they can utilize these files in other ways, most notably for the Brawlback launcher to contain more replays at once and provide statistical analysis about each match.

## Existing Replay Format
When replays are saved, they are represented in the file system as the infamous rp_\*.bin files. These files are **not** video files; they simply hold information about the match in a stream, similar to Slp files. The file schema can be found [here](https://github.com/heinermann/vgce/blob/master/docs/Nintendo/Super%20Smash%20Bros.%20Brawl/downloadable%20content.txt). However, these files are both **compressed** and **encrypted**, in that order.  
  
The encryption method used is [**AES-128-CBC with no padding**](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). *No, I will not be giving out the key or IV, for obvious reasons.*  
  
The compression method used on the body (not including the header, AKA 0x20 bytes after the start of the file after decryption) is **LZ11**, a varient of **LZSS**. Credit to [**@magical**](https://github.com/magical) for the algorithm found [here](https://github.com/magical/nlzss).
## Recording Schema
At the moment, each replay file (\*.brba), contains information about the following:
- The frame the game starts on.
- The RNG values.
- The stage the match was on.
- The number of players in the match.
- A buffer holding the scene information.
- Frame data
  - Frame number currently on, both consistent (starts at end of count down) and persistent (starts at stage load).
  - The inputs of each player.
  - The character each player is playing.
  - The position of the character.
  - The damage taken and stock count.
  - The items spawned and where.

Recording is done by injecting C++ codes; once at the end of the 3...2...1... timer to collect information about the game itself, and at the beginning of each frame to collect the frame data. After collecting this data in the form of objects, a C++ code sends the data over EXI to the emulator where it's added to an existing UBJSON file created at the start of the game. This file is then saved to the disk once the match ends.

## Playback
After setting up the replay via EXI, each frame inputs are pulled via EXI and applied to the pad. At the end of the replay, it returns to menus. There is currently a bug with this where inputs in the loading screen contribute to desyncs due to an input leak.

## Menuing
The replay data is stripped from each replay file and injected into the game to replace the vanilla replays in the replay menu. Currently, it will do this for an infinite number of replays. This will likely crash the game, so it should be figured out what the maximum number of replays is and updated to conceed to that number with a message somehow that says to go to the launcher for the rest.
