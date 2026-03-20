# Ghidra

## What is Ghidra?
Ghidra is a reverse engineering framework used, in this instance, to view compiled PowerPC instructions as C++ code with full symbols, namespaces, demangling, etc. In short, it allows us to look at an estimate of what Brawl's code would look like if a full decompile was available.

## Installation Instructions
1. Download the [latest version of Ghidra supported by the GameCube Loader extension](https://github.com/NationalSecurityAgency/ghidra/releases/tag/Ghidra_12.0.4_build), and extract it.
2. Download [Ghidra-GameCube-Loader](https://github.com/Cuyler36/Ghidra-GameCube-Loader) for the version of Ghidra you downloaded.
3. Copy the downloaded Ghidra GameCube Loader zip into the /Extensions/Ghidra folder of the extracted Ghidra folder.
4. Run ghidraRun.bat in the root of your Ghidra installation folder.
5. Go to File > Install Extensions, then check GameCubeLoader. Click Install Anyway.
6. Restart Ghidra.
7. Go to File > New Project > Shared Project.
8. Enter the OpenBrawl-CBM connection string in this Window. Join the [Discord](https://discord.gg/dzYRN32k4D) for this if you don't already have it.
9. Click Next. It'll ask you for credentials for RW access; enter them if you have them. If you don't have credentials, just click Request Anonymous Access. Hit OK.
10. Click OpenBrawl-CBM and then click Next.
11. Choose a location to save the project, then click Finish.

Ghidra has very slow search indexing on Servers, meaning it's advisable to copy the project to your local machine by copy-pasting the project in the same repository.

## Accessing OpenBrawl-CBM
1. If you haven't already authenticated since you opened Ghidra, it'll ask you for credentials for RW access; enter them if you have them. If you don't have credentials, just click Request Anonymous Access. Hit OK.
2. Once you are done, you should see a folder called OpenBrawl-CBM with three files, one also named OpenBrawl-CBM. Double click on the file OpenBrawl-CBM.
