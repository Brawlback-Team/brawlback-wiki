# Rollback Documentation

## Introduction
Rollback is a form of netcode that attempts to aid in fixing some of the issues that plague delay-based netcode by adding some functionality to it. More specifically, it does this by introducing the concept of a savestate that holds a certain amount of game information from n-number of previous frames. In a fighting game with rollback netcode, instead of waiting for the opponent's input like in delay-based netcode, it will proceed like normal and rewind as needed to fix mistakes in assumptions made about dropped inputs. This allows for a smoother experience.

### Rollback in Brawl
