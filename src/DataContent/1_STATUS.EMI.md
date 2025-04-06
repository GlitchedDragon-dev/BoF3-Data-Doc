# STATUS.EMI

<div class="warning">
This document is still being researched and is not yet complete. 
This means that some information could be erroneous or simply missing.
</div>

**Table of content:**
1. [Introduction](#introduction)
2. [The first data: Executable of the current game mode](#the-first-data-executable-of-the-current-game-mode-statusmenu)
3. [The StatusMenu texture (2 and 3)](#the-statusmenu-textures-2-and-3)
4. [Two palettes for menu](#two-palettes-for-menu)

-----------------------------------------------------------

## Introduction

This file represent all the `Status Menu` data, when you press `Square` in game.

The file contains 8 data:

| Index |  Size  |          Type          | Description                                      |
|:-----:|:------:|:----------------------:|:-------------------------------------------------|
|   1   | 117578 |       Executable       | Executable of the current game mode `StatusMenu` |
|   2   | 32768  |         Image          | Texture of the menu tiles                        |
|   3   | 32768  |         Image          | Texture of the menu backgrounds                  |
|   4   |  512   |        Palette         | Palette for the menu tiles and backgrounds       |
|   5   |  512   |        Palette         | Palette for the menu tiles and backgrounds (bis) |
|   6   |  3616  | Audio Samples (Header) | Audio samples header (menu buttons sounds?)      |
|   7   |   44   |          ???           | Small unknown file, maybe some pointers inside   |
|   8   | 64560  | Audio Samples (Binary) | Audio samples binary (menu buttons sounds?)      |

## The first data: Executable of the current game mode `StatusMenu`
The `RAM Index` of this data is `0x801D0C00`.

This data is actually the “StatusMenu” game mode executable.
This is MIPS code, and there are interactions with the base executable `SLES_......`.

This executable contains all the menu behavior.

## The StatusMenu textures (2 and 3)

This texture is located at the second index of the `STATUS.EMI` file, and contains tiles of:
- Characters portraits
- Menu Icons
- Menu Layout

The texture has a width of 128 pixel, and is encoded in 4bpp.

For the characters portraits, they are tiles of 40x48. 
They use the following palette in file like this:

| Characters | Palette index | Palette Row |
|:----------:|:-------------:|:-----------:|
| Adult Ryu  |    fourth     |     01      |
| Young Ryu  |    fourth     |     11      |
|    Tepo    |    fourth     |     12      |
| Young Rei  |    fourth     |     13      |
| Adult Rei  |    fourth     |     13      |
| Young Nina |    fourth     |     15      |
| Adult Nina |    fourth     |     15      |
|    Momo    |    fourth     |     00      |
|    Garr    |    fourth     |     02      |
|    Pico    |     fifth     |     13      |
|   Dragon   |    fourth     |     14      |

> **Information**
> 
> Looks like the tiles are aligned in rows of 256 x 40 pixels 


## Two palettes for menu
They are the forth and fifth data of the `STATUS.EMI`: They contain characters portraits and menu colors.

## Todo
**Still a lot to do in this file!**