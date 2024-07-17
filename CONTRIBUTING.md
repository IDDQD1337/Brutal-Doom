# How to contribute

One of the easiest ways to contribute is to participate in discussions on GitHub issues. You can also contribute by submitting pull requests with code changes.

## General feedback and discussions?

Start a discussion on the [issue tracker](https://github.com/Brutal-Doom/Brutal-Doom/issues).

## WORKFLOW GUIDELINES / HOW TO WORK

### SPRITE GUIDELINES
- Save as 32 bpp (bits per pixel) png images ONLY.
- Selective 8 bpp for images that appear for ~1 tick or dont have many colors.
- Image resolutions should be to the power of 2, examples of proper, optimized resolutions:
- ``
32x32, 32x64, 32x128, 32x256
64x32, 64x64,64x128, 64x256
128x32, 128x64, 128x128, 128x256
256x32, 256x64, 256x128, 256x256
``

OFFSETS:
- If working with monsters/vanilla-related actors, use [this file](https://drive.google.com/file/d/1WrkyGcHv926K4Xvu9Ehskjne5gtrtUXP/view?usp=sharing) for proper offset placements.
- No automatic offsets. AT ALL. (automation is fine as long as you manually clean it up).
- If adding new custom sprites, try to align them with their corresponding angles.
- When dealing with possibly mirrored sprites (A2A8), don't use the mirrored version (A8) as a base, try to find the actual A8 frame if possible and use that.


### SOUND GUIDELINES
- ogg files only.

### Code style
I feel like we should all follow a some sort of decorate standard, so it's easier to read. 
Not only for decorate, but any lump. Some are REALLY BAD... like SNDINFO.

I propose an example for decorate:
- Tab is 4 spaces
- 1 tab for properties/flags
- 1 tab for "states" and its bracket
- 1 tab for state name
- 2 tabs for stuff inside a state

- Properties, state names, functions should follow the PascalCase convention (First letter capitalized)
- FLAGS, SPRITES are FULLCAPS.
``` 
ACTOR Object: Clip replaces Clip
{
    //Properties first...
    Width 10
    Height 12
    Speed 80
    BounceType doom
    BounceFactor 0.3
	
    //... then flags.
    +FORCEXYBILLBOARD
    +CLIENTSIDEONLY
    +FLOAT
	
    States
    {
    Spawn:
        TNT1 A 1 A_Jump(256, "State1", "State2")
    State1:
        CLIP A -1
        stop      
    State2:
        CLIP B -1
        stop
  }
}
```

### KEEP THE CODE ERROR FREE!
Before commiting changes to the repository, clean up every warning you may have caused!
We want to avoid the avalanche of orange/red text older bd versions are notorious for, and in geenral this gives a bad look.
