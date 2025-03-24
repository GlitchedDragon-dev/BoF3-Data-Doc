# Texture and Palette

<div class="warning">
This document is still being researched and is not yet complete. 
This means that some information is erroneous or simply missing.
</div>

**Table of content:**
1. [Introduction](#introduction)
2. [Texture](#texture)
3. [Palette](#palette)
4. [How palettes are used in textures](#how-palettes-are-used-in-textures)
5. [Todo - Missing elements](#todo---missing-elements)

-----------------------------------------------------------

## Introduction
Textures and palettes represent most of the visuals that will appear on screen:
- Characters, monsters, ...
- Texts and menus,
- Textures applied to 3D meshes,
- ...

In this document, we'll look at how these data are encoded and how they relate to each other.

## Texture
Textures in the [EMI files](1_TheEmiFiles.md) all seem to have the same `Data Type`, which is `3`.
They have no `header`, and no information about their width, height, bits per pixel and palette used.
There's only raw texture data.

> **Information**
>
> There are ways of finding this information relatively easily:
> - Find out what platform the game is running on (Playstation), and what formats are available on it,
> - Use raw image-reading software (such as [TileMolester](https://github.com/toruzz/TileMolester)),
>   and change the settings until you find the right format.

To compress textures size, a palette system (also known as [CLUT: Color Lookup table](https://en.wikipedia.org/wiki/Palette_(computing)))
allows you to use only a color index found in a table:
- If an image's pixels are encoded in 4 bits, then the image can contain 16 different colors,
- If an image's pixels are encoded in 8 bits, then the image can contain 256 different colors.

However, in BoF3, two formats in particular stand out:
- For textures encoded in **4 bits per pixel**, the **width is 128 pixels**,
- For textures encoded in **8 bits per pixel**, the **width is 64 pixels**.

> Keep in mind that there are other possible formats.

Textures can themselves be split into several tiles, with a size not specified in the data.
___(This information is probably hardcoded directly when the texture is used)___

## Palette
___TODO___

## How palettes are used in textures
___TODO___

## Todo - Missing elements
___TODO___