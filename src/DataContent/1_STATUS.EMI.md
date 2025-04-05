# STATUS.EMI

<div class="warning">
This document is still being researched and is not yet complete. 
This means that some information could be erroneous or simply missing.
</div>

**Table of content:**
1. [Introduction](#introduction)
2. [The first data (Unknown)](#the-first-data-unknown)
3. [The StatusMenu texture (2 and 3)](#the-statusmenu-textures-2-and-3)
4. [Two palettes for menu](#two-palettes-for-menu)

-----------------------------------------------------------

## Introduction

This file represent all the `Status Menu` data, when you press `Square` in game.

The file contains 8 data:

| Index |  Size  |          Type          | Description                                      |
|:-----:|:------:|:----------------------:|:-------------------------------------------------|
|   1   | 117578 |          ???           | A big unknown data, seems really important       |
|   2   | 32768  |         Image          | Texture of the menu tiles                        |
|   3   | 32768  |         Image          | Texture of the menu backgrounds                  |
|   4   |  512   |        Palette         | Palette for the menu tiles and backgrounds       |
|   5   |  512   |        Palette         | Palette for the menu tiles and backgrounds (bis) |
|   6   |  3616  | Audio Samples (Header) | Audio samples header (menu buttons sounds?)      |
|   7   |   44   |          ???           | Small unknown file, maybe some pointers inside   |
|   8   | 64560  | Audio Samples (Binary) | Audio samples binary (menu buttons sounds?)      |

## The first data (Unknown)
At the moment, I found that this file contains pointers and texts of the menu, and it is now my focus.
The `RAM Index` of this data is `0x801D0C00`.

The data starts with a `PointerCount`, following by the pointers: Each pointer target a specific place in the file,
and starts with `0x801D`.

After this list of pointers, we have some short texts, ended each time by the `\0` byte.

> **[Edit 2025/04/04]**
> 
> The investigation continue here, and looks like we have a lot of interesting data:
> - Presence multiple palettes pointers (to be confirmed),
> - A lot of text/messages.
> I wonder if this file is _maybe_ the whole description of a `Game State` (Like pause, status menu, world map ...)

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