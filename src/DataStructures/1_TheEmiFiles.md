# The "EMI" files format

<div class="warning">
This document is still being researched and is not yet complete. 
This means that some information is erroneous or simply missing.
</div>

**Table of content:**
1. [Introduction](#introduction)
2. [Header](#header)
3. [Data](#data)
4. [Libraries and tools](#libraries-and-tools)

-----------------------------------------------------------

## Introduction
The `EMI` files are the containers for all the game's data, apart from the videos.
These files are located in the `BIN` directory on the CD, themselves organized by category in sub-folders.

They are binary files, with a [header](#header) containing a `table of contents` of the data they contain,
followed by the data in raw format.

> ___Information___
>
> The same data can be found identically in several `EMI` files.
>
> The reason for this is that loading several pieces of data in different places on a disk can be slow.
> So, if the data to be loaded is grouped together in the same place, loading will be much faster, limiting the number of readings required.

## Header
The `header` structure is composed as follows:
- The number of data contained in the file,
- A magic word `MATH_TBL`,
- A table of contents of the various data.

Let's take a closer look at the data in this `header`:

| From |  To  | Size |  Type | Description           |
|:----:|:----:|:----:|:-----:|:----------------------|
| 0x00 | 0x03 |   4  |  u32  | Data entry count      |
| 0x04 | 0x07 |   4  |   ?   | ??? Version ???       |
| 0x08 | 0x0F |   8  | u8[8] | Magic word "MATH_TBL" |

Just after these **16 bytes**, we have the table of contents.
This consists of several (same number as the number of data) “lines” indicating:
- The size of the data,
- Data parameters (details below),
- The first 4 bytes of the data,
- Data type _(to be confirmed)_,

Here are the details for one line in the table of content:

| From |  To  | Size |  Type | Description     |
|:----:|:----:|:----:|:-----:|:----------------|
| 0x00 | 0x03 |   4  |  u32  | Data size       |
| 0x04 | 0x07 |   4  |  u32  | Pointer in RAM  |
| 0x08 | 0x0B |   4  | u8[4] | First 4 bytes   |
| 0x0C | 0x0D |   2  |  u16  | Data type ?     |
| 0x0E | 0x0F |   2  |   ?   | _Garbage data_  |

A list of known data types:

| Type ID | Description                    |
|:-------:|:-------------------------------|
|    3    | Image                          |
|    6    | Header samples audio (PSX/VH)  |
|    7    | Data samples audio (PSX/VB)    |
|   10    | Music Sequencer/Midi (PSX/SEQ) |

A lot of data has type `0`, but it's varied data that doesn't correspond to a particular type.

## Data
Note that in EMI files, **the start of the data is always on a multiple of 2048 (0x800)**.

For example:
- The start of the first data in EMI files will always be at file position 2048 (0x800),
- The position of the second data will depend on:
    - where the previous data begins,
    - the size of the previous data,
    - finding the next multiple of 2048 in relation to the previous data.

If we were to write it in code, it would look like this (In C++, the binary shift loses data):
```c++
unsigned int next_data_position = current_data_position + (current_data_size + 0x7FF >> 0xB) * 0x800;

/*
For example, my first data starts at 0x800 and has a size of 2100 bytes
To find the next data, I will do:
- First let's understand the complex part: "current_data_size + 0x7FF >> 0xB" -> "(2100 + 2047) >> 11" -> "4147 >> 11" -> "2".
  This is the times we have to multiple 2048 from the current data to find the next one.
  
- Let's continue: "current_data_position + (current_data_size + 0x7FF >> 0xB) * 0x800" -> "2048 + 2 * 2048" -> 6144 (0x1800).
  This is the actual position of the next data in the file
*/
```

Between two data, you will see mostly garbage bytes like a series of `2E` or `5F`.

## Libraries and tools
You can use the [Emi Extractor](https://github.com/glitch-in-the-herring/emi-extractor/) tool made by 
`Navarchos/RedHerring` to extract the data from your EMI files.