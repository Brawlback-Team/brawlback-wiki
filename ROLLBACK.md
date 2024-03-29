# Rollback Documentation

## Introduction
Rollback is a form of netcode that attempts to aid in fixing some of the issues that plague delay-based netcode by adding some functionality to it. More specifically, it does this by introducing the concept of a savestate that holds a certain amount of game information from n-number of previous frames. In a fighting game with rollback netcode, instead of waiting for the opponent's input like in delay-based netcode, it will proceed like normal and rewind as needed to fix mistakes in assumptions made about dropped inputs. This allows for a smoother experience.

## Rollback in Brawl
Rollback in Brawl is implemented using a method similar to [Slippi](https://github.com/project-slippi); code is injected in the game via codes run in the backend of a custom build of Dolphin. In fact, most of the infastructure is very similar to Slippi. However, where we diverge is the method by which we reach this goal; while Melee is mostly pure ASM, Brawl has the benefit of being able to leverage injecting C++ code. This allows for smoother looking and acting codesets. See below for a diagram of how the injections function:

![white](https://user-images.githubusercontent.com/29901514/198829504-45f73473-8e0f-41b4-ab5d-c20cfff366af.png)

The rollback implementation is **mostly finished at this point**. The biggest gap in this area is in savestates, and if anyone is looking to help with the netcode I would suggest looking at those instead.

## Savestates in Brawl
Brawl state is currently maintained via a collection of heaps that must be sifted through for a minimal savestate. These heaps are named:

- System 
- Fighter1Instance 
- Fighter2Instance 
- InfoInstance 
- InfoExtraResource 
- InfoResource 
- Physics 
- WiiPad 
- Fighter1Resource 
- Fighter2Resource 
- FighterEffect 
- FighterTechqniq 
- GameGlobal

Currently, we save **all portions of the heap**, however; they are currently **broken** and **desync** the game, meaning an alternative method must be devised. The savestate regions are also hardcoded, which is problematic as modification packs of Brawl such as P+ utilize different definitions. A direct quote from PiNE suffices to explain the current predicement with savestates: "Savestates can be slow when the amount of memory they copy to/from the game is too large. We want to be able to copy all relevant gamestate in (ideally) about 1 millisecond. Getting closer to 2ms per copy is pushing it, but is still alright. Anything above 2ms per copy is too slow. (Note: on my cpu (i7-9750H), ~21mb savestate takes ~2ms to copy. Anything below 10mb would be ideal, but if it gets below 15mb i’d consider that usable)
Savestates can desync when particular regions of memory that hold data that the game relies on to compute the next frame (relevant gamestate) is not included in the regions copied during rollbacks." A full explanation can be found [here](https://docs.google.com/document/d/1JYE3UB3GcUUH0nWNdq04xvFxBocS4NM8rcHxDzx6bmc).
