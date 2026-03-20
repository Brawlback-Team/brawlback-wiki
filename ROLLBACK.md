# Rollback Documentation

## Introduction
Rollback is a form of netcode that attempts to aid in fixing some of the issues that plague delay-based netcode by adding some functionality to it. More specifically, it does this by introducing the concept of a savestate that holds a certain amount of game information from n-number of previous frames. In a fighting game with rollback netcode, instead of waiting for the opponent's input like in delay-based netcode, it will proceed like normal and rewind as needed to fix mistakes in assumptions made about dropped inputs. This allows for a smoother experience. 

## Rollback in Brawl
Rollback in Brawl is implemented using a method similar to [Slippi](https://github.com/project-slippi); code is injected in the game via codes run in the backend of a custom build of Dolphin. In fact, most of the infastructure is very similar to Slippi. However, where we diverge is the method by which we reach this goal; while Melee is mostly pure ASM, Brawl has the benefit of being able to leverage injecting C++ code. This allows for smoother looking and acting codesets. See below for a diagram of how the injections function:

### Final release

![white](https://user-images.githubusercontent.com/29901514/198829504-45f73473-8e0f-41b4-ab5d-c20cfff366af.png)

## Savestates in Brawl
- All memory at the launch of the game is marked as read-only. As the game tries to make
writes to memory over the course of the game, it marks the page that memory was on
as dirty and flips it to read-write. At the end of the frame, the dirty pages are copied into
a buffer. This is the current state for the frame. Rinse and repeat for each frame.

- When a discrepancy that requires a rollback is detected, the game rewinds to each
frame before it’s state to the frame required to rollback to. This will, in theory,
restructure the state the game was in at that frame.
