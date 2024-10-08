![[Pasted image 20240802230458.png]]Canvas size of entire game would be 1920x1080

When it comes to the spritesheet, Character is smaller than the size of each block to allow room for animations.

It seems the general rule is to increase by the power of 2, multiple of 2 or something that can divide by 2 when increasing resolution size (your choice).

Hitbox size is smaller than character for collision etc.
![](Pictures/Hitbox%20size,%20Character%20size.png)
Hitbox size (Right) and Character size (left)

![](Pictures/Character%20Canvas%20size.png)
Character canvas size 64x64

Character's feet must be planted flat on the canvas it seems

**Drawing things other than characters**

![](Pictures/Character%20Size%20diff.png)
If you draw something bigger than a character, you need to put them in the next resolution space, even if they're only a few pixels bigger. Use the main character as a frame of reference to see them next to each other, and import to see a screenshot in the game to see if the size feels right.

All the game really cares about is if everything is in scale relative to each other. Doesn't matter exactly how big the canvas is. These are generally just good guidelines to make sure characters and animations are similar.

![](Pictures/Asset%20Size.png)
Canvas size isn't a square anymore for this asset.
![](Pictures/Bigger%20Assets.png)
Some canvas sizes can be bigger than the screen.

![](Pictures/Cheat%20Sheet%20Resolution%20Size.png)