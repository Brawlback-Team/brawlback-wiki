# Rollback Documentation

## Introduction
Rollback is a form of netcode that attempts to aid in fixing some of the issues that plague delay-based netcode by adding some functionality to it. More specifically, it does this by introducing the concept of a savestate that holds a certain amount of game information from n-number of previous frames. In a fighting game with rollback netcode, instead of waiting for the opponent's input like in delay-based netcode, it will proceed like normal and rewind as needed to fix mistakes in assumptions made about dropped inputs. This allows for a smoother experience.

### Rollback in Brawl
Rollback in Brawl is implemented using a method similar to [Slippi](https://github.com/project-slippi); code is injected in the game via codes run in the backend of a custom build of Dolphin. In fact, most of the infastructure is very similar to Slippi. However, where we diverge is the method by which we reach this goal; while Melee is mostly pure ASM, Brawl has the benefit of being able to leverage injecting C++ code. This allows for smoother looking and acting codesets. See below for a diagram of how the injections function:
![image](https://user-images.githubusercontent.com/29901514/198723833-ebe2ec62-cca0-4edf-89fe-58cd6b2c5b66.png)

###
