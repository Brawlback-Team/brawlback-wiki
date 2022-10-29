# EXI Guide

## Introduction
The EXI bus on the GameCube and Wii both serve the same purpose: it simply connects external peripherals including the memory card to the system. Emulating such a memory card and injecting code that processes information across it proves to be fruitful in sending information from the console (emulator) to the game and vice versa. Such a workflow proves to be fundamental in how Brawlback in all facets functions.

## How to Use it in Codes
Within brawlback-asm, there is a folder Libraries, which serves as its title suggests; it has Brawl and Wii related functionality within it in the form of commonly used injections. Such an injection is one that allows you to use the EXI bus [here](https://github.com/Brawlback-Team/brawlback-asm/tree/rollback-refactor-brawlback/Libraries/Wii/EXI). To use this, simply call writeEXI to write from the game to the console and readEXI to read from the console to the game. On the console (emulator) side, you will need a way to also read and send EXI messages.
