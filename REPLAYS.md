# Replays Documentation

## Introduction
With the introduction of Slippi to the Melee scene, the bar for the quality of replays has risen. While true that Brawl has existing "replays", these "replays" are just a collection of inputs, RNG values, and game settings locked behind a file that is encrypted and compressed using algorithms unknown to anyone, meaning you can't do anything particularly interesting with them. The goal of the replays portion of this project is to open up the replay format for Brawl to make them more Slippi-like; files that have compression/encryption methods known to developers and users alike so that they can utilize these files in other ways, most notably for the Brawlback launcher to contain more replays at once and provide statistical analysis about each match.

## Existing Replay Format
When replays are saved, they are represented in the file system as the infamous rp_\*.bin files. These files are **not** video files; they simply hold information about the match in a stream, similar to Slp files. The file schema can be found [here](https://github.com/heinermann/vgce/blob/master/docs/Nintendo/Super%20Smash%20Bros.%20Brawl/downloadable%20content.txt). However, these files are both **compressed** and **encrypted**, in that order.  
  
The encryption method used for both the first half and the rest of the body is is [**AES-256-CBC with no padding**](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). The IV for the first 0x10 bytes of the header are different from the rest of the file, but for some reason it's replaced on top of the encrypted file. *No, I will not be giving out the key or IV, for obvious reasons.*  
  
The compression method used on the body (not including the header, AKA 0x20 bytes after the start of the file after decryption) is **LZ11**, a varient of **LZSS**. Credit to [**@magical**](https://github.com/magical) for the algorithm found [here](https://github.com/magical/nlzss).

## Complications with Rollback
**White T write stuff here!** :3
