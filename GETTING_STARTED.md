# Getting Started

## Introduction
This wiki is a fork of the [Slippi-wiki](https://github.com/project-slippi/slippi-wiki) meant to assist developers interested in learning about and contributing to the Brawlback codebase. 

<i> What this document is: </i> <br>
* An overview of the various components that make up the Brawlback Project. 
* A collection of resources and tools. 

<i> What this document is <b> not </b>: </i> <br>
* An in-depth programming tutorial.

## Overview

### The Project
The Brawlback project is comprised of a number of different applications, each with their own purpose. Below is an overview of each of these applications function, and their relevant technologies.

<b> [Dolphin](https://github.com/Brawlback-Team/dolphin) </b> - A modified version of the Dolphin emulator. This project is responsible for handling things like: communication with the matchmaking server, passing external data to the emulated game, and playing replays. 
<br> <i> Languages: </i> C++ 

<b> [Brawlback SSBB ASM](https://github.com/Brawlback-Team/brawlback-asm) </b> - A series of ASM mods that are applied to Brawl in order make Brawlback work.
<br> <i> Languages: </i> PPC Assembly, C++

### The Workflow

The user launches <b>Dolphin</b> and selects an .iso of Brawl to emulate. Upon lauching the emulation of Brawl, Dolphin injects the modifications made by <b> Brawlback ASM </b> as placed on an SD card. As the user interacts with the game, information is exchanged between Dolphin and the Brawlback SSBB ASM code. As a user begins an online match, Dolphin starts a log of in-game state reported by Brawlback ASM.


## Commonly Asked Questions
> "Where is the rollback code located?"  

Rollback is accomplished by work done between the [Brawlback ASM](https://github.com/Brawlback-Team/brawlback-asm/search?p=1&q=rollback&unscoped_q=rollback) code and the [Dolphin](https://github.com/Brawlback-Team/Dolphin/search?q=rollback&unscoped_q=rollback) code.

> "How is data moved between the game (assembly) and the emulator?"

Via [EXI communication](https://github.com/Brawlback-Team/dolphin/blob/master/Source/Core/Core/HW/EXI/EXIBrawlback.cpp). An example of such is demonstrated in [this video](https://www.youtube.com/watch?v=NOq49h0tkBI) by Fizzi.

> When will BrawlBack be ready for a public release?

When it passes the quality control gates. AKA: when it's ready.

> What will the UI look like? Are you going to reuse Brawl's matchmaking UI?

Unknown at the moment. The current plan is to reutilize as much of the UI as possible.

## Guides & Resources

### Brawl Modding and Assembly
* [SSBB Modding Wiki](https://brawlre.github.io/public/) - Created by fudgepop01, a wiki for all things Brawl modding!
* [Custom Brawl Modding Discord](https://discord.gg/GbxJhbv) - A Discord where you can get all your questions answered about Brawl modding.
* [MKWii's Go From Noob to Veteran ASM Coder Guide Repo](https://mkwii.com/showthread.php?tid=1114) - A bunch of useful guides to learning ASM and related concepts, not necessarily PPC or Melee specific.
* [Fizzi Teaches Basic Assembly and Melee Modding](https://www.youtube.com/watch?v=NOq49h0tkBI) (video) - Recorded by the creator of Slippi, this video teaches some basic assembly and demonstrates EXI communication.
* [fudgepop01's Git Guide on Setting Up Fracture's Framework for C++ Codes Development](https://github.com/Fracture17/ProjectMCodes/tree/master/notes/guides) - GitHub reference for how to setup Fracture's C++ Injection Framework.
* [fudgepop01 Shows How to Setup Environment for Brawl Modding in Fracture's C++ Framework](https://youtu.be/oGg2dgYN1Do) (video) - Recorded by fudgepop01, this video teachs you how to setup your environment for C++ development
* [Intro to Wii Game Modding by InternetExplorer](https://www.youtube.com/watch?v=IOyQhK2OCs0&list=PL6GfYYW69Pa2L8ZuT5lGrJoC8wOWvbIQv) (video) - Recorded by Dan Salvato - A playlist of videos related to modding Wii games. An excellent resource for debugging with Dolphin.
* [Assembler Tutorial](http://wiibrew.org/wiki/Assembler_Tutorial) - A wii modding specific guide to PPC, and its instructions. 
* [PowerPC Instruction Set](https://www.ibm.com/support/knowledgecenter/en/ssw_aix_71/assembler/idalangref_ins_set.html) - Indepth documentation about PowerPC instructions and their behavior.
* [PowerPC Instruction Set Reference Card](http://www.tentech.ca/downloads/other/PPC_Quick_Ref_Card-Rev1_Oct12_2010.pdf) - An overview of various PowerPC instructions and their behavior.
### Rollback
* [GGPO Article on Rollback](https://drive.google.com/file/d/1cV0fY8e_SC1hIFF5E1rT8XRVRzPjU8W9/view) - An article from GGPO on how rollback functions specific to emulators.
* [Rollback Pseudocode](https://gist.github.com/rcmagic/f8d76bca32b5609e85ab156db38387e9) - Some pseudocode used to show the basics of rollback.
* [GDC Talk on Rollback in MK and Injustice 2](https://youtu.be/7jb0FOcImdg) (video) - A talk Netherrealm Games (Mortal Kombat, Injustice) gave on rollback.
* [Rollback in INVERSUS](http://blog.hypersect.com/rollback-networking-in-inversus/) - A great blog post from the developer of the game INVERSUS on implementing rollback and the different challenges within.
* [Fightin' Words Rollback In-depth Guide](https://ki.infil.net/w02-netcode.html) - Another great blog post on the intricacies of rollback.
### Slippi
* [Slippi's Wiki](https://github.com/project-slippi/slippi-wiki) - Slippi's wiki
* [Slippi's Main GitHub](https://github.com/project-slippi/project-slippi) - Slippi's main repo
* [Slippi Community Discord](http://discord.gg/pPfEaW5) - Slippi's Discord to ask questions about development
## Tools

### Brawl Modding and Assembly
* [GCT RealMate Code Editor](https://marketplace.visualstudio.com/items?itemName=fudgepops.gctrm-editor) - A useful extension for syntax highlighting in VSCode related to Brawl modding
* [HxD](https://mh-nexus.de/en/hxd/) - A free Hex editor. Hex editors in general are useful for looking through memory dumps.
* [SpeedCrunch](https://speedcrunch.org/) - A calculator for programmers. It allows for quick conversions and operations between hex, binary, octal, and decimal.
* [Ghidra](https://ghidra-sre.org/) - A tool originally created by the NSA - it's used for reverse engineering programs. Particularly useful, is its ability to generate C code from assembly.
* [Dolphin Memory Engine](https://github.com/aldelaro5/Dolphin-memory-engine) - A RAM search program designed to search, track, and edit the emulated memory of the Dolphin emulator during runtime.
* [CodeWrite](https://github.com/TheGag96/CodeWrite/) - Convert PPC ASM code to/from C2 codes.
* [VSDSync](https://cdn.discordapp.com/attachments/653828058079297557/857446879406981120/VSDSync-0.1.3.2_2021reupload.zip) - A collection of utilities and scripts to automate updating your virtual SD card.
* [GCTRealMate](https://github.com/Brawlback-Team/brawlback-asm/blob/master/Build/GCTRM/GCTRealMate.exe) - An application to generate cheats for Brawl based on provided ASM in txt files.
