---
toc: false
comments: false
layout: post
title: Artiuclation blog
description: Artiuclation Blog
type: ccc
courses: { csse: {week: 13} }
---


## Artiuclation blog 

## Sprite animation

```js
escaper: {
        src: "/images/platformer/sprites/escaper.png",
        width: 130,
        height: 140,
        scaleSize: 150,
        speedRatio: 0.7,
        animationSpeed: 3,
        ///animationspeed:6
        idle: {row: 0, frames: 5 },
        walk: {  row: 1, frames: 6 },
        run: {  row: 2, frames: 7 },
        jump: {row: 3, frames: 8 },
        hitbox: { widthPercentage: 0.3, heightPercentage: 0.8 }
```
### src, width, height

- We had to find the right width and height through the window, Mr mortensen told me about.

### scaleSize, speedRatio

- Finding the scaleSize as well as the speedRatio took time to eventually find out. I checked many different scaleSizes while also using .1 increments to find the speedRatio

### AnimationSpeed

The animationSpeed property controls how quickly the character's animation frames are updated during the game. It determines the rate at which the animation cycles through its frames, affecting the smoothness and speed of the visual animation.

For example, if animationSpeed is set to 3, the frame index will only increment every 3 update cycles, ensuring that the animation progresses at a consistent rate.

### Animations, idle, walk, run, jump

The animations property, such as idle, walk, run, jump, used to feature 2 rows. being left and right which were soon deleted because of us using PlayerBaseOneD which allowed our sprite sheet to not only go right but left also. By deleting "left" and "right" PlayerBaseOneD used only that one row, creating a mirror. This allowed our sprite to be flipped without any animation problems.



## UpdateFrameX timer

``` js
    updateFrameX(){
        // Check if the current frame is less than the maximum frame
        if (this.frameX < this.maxFrame) {
            // If the counter is greater than 0, keep the current frame and decrement the counter
            if(this.counter > 0){
                //this.frameX = this.frameX;  This line is actually not needed; it does nothing
                this.counter--;
            }
            // If the counter is 0 or less, advance to the next frame and reset the counter
            else{
                this.frameX++;
                this.counter = this.animationSpeed;
            }
        } else {
            // If the current frame is at or beyond the maximum frame, reset to the minimum frame
            this.frameX = this.minFrame;
        }
    }
```

### Inital condition check
```js
if (this.frameX < this.maxFrame)
 ```

The method first checks if the current frame index (frameX) is less than the maximum frame index (maxFrame).
This ensures that the frame index does not exceed the total number of frames available for the animation.

### Counter Management:

```js
if(this.counter > 0){
    this.counter--;
}
```

If the counter is greater than 0, the frame index (frameX) remains unchanged.
The counter is decremented by 1. This mechanism controls the speed of the animation by delaying the frame update until the counter reaches 0.


### Advance Frame and Reset Counter:

```js 
else{
    this.frameX++;
    this.counter = this.animationSpeed;
}
```

When the counter reaches 0, the frame index (frameX) is incremented by 1, advancing to the next frame in the animation sequence.
The counter is then reset to the value of animationSpeed, which our animationSpeed equals 3. Which determines how many update cycles must pass before the frame advances again, which is three.

### Reset Frame Index:

```js
} else {
    this.frameX = this.minFrame;
}
```

If the frame index (frameX) has reached or exceeded the maximum frame index (maxFrame), FrameX is reset to the minimum frame index (minFrame).
This creates a looping effect, where the animation restarts from the beginning once it reaches the end of the timer.







## Draw.io Diagram

![Alt text]({{site.baseurl}}/images/Draw.io-explanation.png)
