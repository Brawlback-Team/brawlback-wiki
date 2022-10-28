# Replays Documentation

## Introduction
With the introduction of Slippi to the Melee scene, the bar for the quality of replays has risen. While true that Brawl has existing "replays", these "replays" are just a collection of inputs, RNG values, and game settings locked behind a file that is encrypted and compressed using algorithms unknown to anyone, meaning you can't do anything particularly interesting with them. The goal of the replays portion of this project is to open up the replay format for Brawl to make them more Slippi-like; files that have compression/encryption methods known to developers and users alike so that they can utilize these files in other ways, most notably for the Brawlback launcher to contain more replays at once and provide statistical analysis about each match.

## Schema
At the moment, each replay file (\*.brba), contains information about the following:
- The frame the game starts on.
- The RNG values.
- The stage the match was on.
- The number of players in the match.
- Frame data
  - Frame number currently on, both consistent (starts at end of count down) and persistent (starts at stage load).
  - The inputs of each player.
  - The character each player is playing.
  - Inputs.
  - The position of the character.
  - The damage taken and stock count.
