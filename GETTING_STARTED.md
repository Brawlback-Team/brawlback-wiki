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

<b> [Ishiiruka](https://github.com/WhiteTPoison5/Ishiiruka) </b> - A modified version of the Dolphin emulator. This project is responsible for handling things like: communication with the matchmaking server, writing Brawlback replay files, passing external data to the emulated game, and playing replays. 
<br> <i> Languages: </i> C++ 

<b> [Brawlback SSBM ASM](https://github.com/WhiteTPoison5/brawlback-asm) </b> - A series of ASM mods that are applied to Brawl in order make Brawlback work.
<br> <i> Languages: </i> PPC Assembly

### The Workflow

The user launches <b>Ishiiruka</b> and selects an .iso of Brawl to emulate. Upon lauching the emulation of Brawl, Ishiiruka injects the modifications made by <b> Brawlback ASM </b>. As the user interacts with the game, information is exchanged between Ishiiruka and the Brawlback SSBM ASM code. As a user begins an online match, Ishiiruka starts a log of in-game state reported by Brawlback ASM.


## Commonly Asked Questions
> "Where is the rollback code located?"  

Rollback is accomplished by work done between the [Brawlback ASM](https://github.com/WhiteTPoison5/brawlback-asm/search?p=1&q=rollback&unscoped_q=rollback) code and the [Ishiiruka](https://github.com/WhiteTPoison5/Ishiiruka/search?q=rollback&unscoped_q=rollback) code.

> "How is data moved between the game (assembly) and the emulator?"

Via [EXI communication](https://github.com/WhiteTPoison5/Ishiiruka/blob/slippi/Source/Core/Core/HW/EXI_DeviceSlippi.cpp). An example of such is demonstrated in [this video](https://www.youtube.com/watch?v=NOq49h0tkBI) by Fizzi.

## Guides & Resources

### Brawl Modding and Assembly
* [Fizzi Teaches Basic Assembly and Melee Modding](https://www.youtube.com/watch?v=NOq49h0tkBI) (video) - Recorded by the creator of Slippi, this video teaches some basic assembly and demonstrates EXI communication.
* [MKWii's Go From Noob to Veteran ASM Coder Guide Repo](https://mkwii.com/showthread.php?tid=1114) - A bunch of useful guides to learning ASM and related concepts, not necessarily PPC or Melee specific.
* [Intro to Wii Game Modding by InternetExplorer](https://www.youtube.com/watch?v=IOyQhK2OCs0&list=PL6GfYYW69Pa2L8ZuT5lGrJoC8wOWvbIQv) (video) - Recorded by Dan Salvato - A playlist of videos related to modding Wii games. An excellent resource for debugging with Dolphin.
* [Assembler Tutorial](http://wiibrew.org/wiki/Assembler_Tutorial) - A wii modding specific guide to PPC, and its instructions. 
* [PowerPC Instruction Set](https://www.ibm.com/support/knowledgecenter/en/ssw_aix_71/assembler/idalangref_ins_set.html) - Indepth documentation about PowerPC instructions and their behavior.
* [PowerPC Instruction Set Reference Card](http://www.tentech.ca/downloads/other/PPC_Quick_Ref_Card-Rev1_Oct12_2010.pdf) - An overview of various PowerPC instructions and their behavior.

## Tools

### Brawl Modding and Assembly
* [VSCode PPC ASM Extension](https://marketplace.visualstudio.com/items?itemName=OGoodness.powerpc-syntax) - A useful extension for syntax highlighting in VSCode
* [HxD](https://mh-nexus.de/en/hxd/) - A free Hex editor. Hex editors in general are useful for looking through memory dumps. 
* [SpeedCrunch](https://speedcrunch.org/) - A calculator for programmers. It allows for quick conversions and operations between hex, binary, octal, and decimal. 
* [Ghidra](https://ghidra-sre.org/) - A tool originally created by the NSA - it's used for reverse engineering programs. Particularly useful, is its ability to generate C code from assembly. 
