# Replays Documentation

## Introduction
With the introduction of Slippi to the Melee scene, the bar for the quality of replays has risen. While true that Brawl has existing "replays", these "replays" are just a collection of inputs, RNG values, and game settings locked behind a file that is encrypted and compressed using algorithms unknown to anyone, meaning you can't do anything particularly interesting with them. The goal of the replays portion of this project is to open up the replay format for Brawl to make them more Slippi-like; files that have compression/encryption methods known to developers and users alike so that they can utilize these files in other ways, most notably for the Brawlback launcher to contain more replays at once and provide statistical analysis about each match.

## Recording Schema
At the moment, each replay file (\*.brba), contains information about the following:
- The frame the game starts on.
- The RNG values.
- The stage the match was on.
- The number of players in the match.
- Frame data
  - Frame number currently on, both consistent (starts at end of count down) and persistent (starts at stage load).
  - The inputs of each player.
  - The character each player is playing.
  - The position of the character.
  - The damage taken and stock count.

Recording is done by injecting C++ codes; once at the end of the 3...2...1... timer to collect information about the game itself, and at the beginning of each frame to collect the frame data. After collecting this data in the form of objects, a C++ code sends the data over EXI to the emulator where it's added to an existing UBJSON file created at the start of the game. This file is then saved to the disk once the match ends.

## Playback
**No work has been done on playback as of yet**, though theoretically it should just be the inverse of recording the data.

## Menuing
The replay data is stripped from each replay file and injected into the game to replace the vanilla replays in the replay menu. Currently, it will do this for an infinite number of replays. This will likely crash the game, so it should be figured out what the maximum number of replays is and updated to conceed to that number with a message somehow that says to go to the launcher for the rest.
