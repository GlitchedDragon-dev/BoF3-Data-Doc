# STATUS.EMI

<div class="warning">
This document is still being researched and is not yet complete. 
This means that some information could be erroneous or simply missing.
</div>

**Table of content:**
1. [Introduction](#introduction)
2. [The StatusMenu texture](#the-statusmenu-textures)
3. [Two palettes for menu](#two-palettes-for-menu)

-----------------------------------------------------------

## Introduction

This file represent all the `Status Menu` data, when you press `Square` in game.

## The StatusMenu textures

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