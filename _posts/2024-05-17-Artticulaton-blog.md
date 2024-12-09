---
toc: false
comments: false
layout: post
title: Artiuclation blog
description: Artiuclation Blog
type: ccc
courses: { csse: {week: 13} }
---

>## Javascript Gameobjects to Game Level

- For our objects we used our own various blocks and platforms for access to reach our coins called `V-bucks`. Also adding our own sprite animation/player being called `escaper` and our own enemies being called `SkibidiToilets` and our main enemy being called `SkibidiTitan` which is also our boss in the background. 
- While adding the SkibidiTitan we had to add our own collisons, we took the collisions used in `playerhill.js` and incorporated it into our own file called `PlayerSkibidi.js`. Using these collision we branched that off to our Titan which used this collisions to use Laser.Js. By doing this we had to use our imports and exports. We also had to use the collisions for our `laser.js` file to allow the Titan to attack the player which is why we created our own colissions.


<br>


>## GameLevel to and Array of Gamelevels
- Laser would branch off of skibidititan, we would have to include the laser as it has it's own sprite so as the titan.
- Commented out areas are ideas that could have been implemented but got held off
- Skibidi toilets would be our enemies, coming from their file skibiditoilet.j
- JavaScript objects/Gameobjects

```js
  const skibidiGameObjects = [
    // GameObject(s), the order is important to z-index...
    { name: 'desert', id: 'background', class: Background, data: assets.backgrounds.desert },
    //{ name: 'clouds', id: 'background', class: BackgroundClouds, data: assets.backgrounds.clouds },
    { name: 'laser', id: 'Laser', class: Laser, data: assets.obstacles.laser, xPercentage:  0.75, yPercentage: 0.5 },
    { name: 'skibidiTitan', id: 'skibidiTitan', class: skibidiTitan, data: assets.enemies.skibidiTitan, xPercentage:  0.35, yPercentage: 0.5, minPosition: 0.5 }, 
    { name: 'sand', id: 'platform', class: Platform, data: assets.platforms.sand },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.2, yPercentage: 1 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.4, yPercentage: 0.6 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.325, yPercentage: 0.8 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.2, yPercentage: 0.5 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.225, yPercentage: 0.5 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.0, yPercentage: 0.5 } ,
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.025, yPercentage: 0.5 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.025, yPercentage: 0.5 },
    { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: assets.platforms.sand, xPercentage: 0.5, yPercentage: 0.5 },
    ///{ name: 'coin', id: 'coin', class: Coin, data: assets.obstacles.vbucks, xPercentage: 0.475, yPercentage: 0.5 },
    { name: 'coin', id: 'coin', class: Coin, data: assets.obstacles.vbucks, xPercentage: 0.325, yPercentage: 0.7 },
    { name: 'coin', id: 'coin', class: Coin, data: assets.obstacles.vbucks, xPercentage: -0.0125, yPercentage: 0.4 },
    { name: 'coin', id: 'coin', class: Coin, data: assets.obstacles.vbucks, xPercentage: 0.0125, yPercentage: 0.4 },
    { name: 'coin', id: 'coin', class: Coin, data: assets.obstacles.vbucks, xPercentage: 0.0325, yPercentage: 0.4 },
    { name: 'SkibidiToilet', id: 'SkibidiToilet', class: SkibidiToilet, data: assets.enemies.skibidiToilet, xPercentage:  0.3, minPosition: 0.07 },
    { name: 'SkibidiToilet', id: 'SkibidiToilet', class: SkibidiToilet, data: assets.enemies.skibidiToilet, xPercentage:  0.5, minPosition: 0.3 },
    { name: 'SkibidiToilet', id: 'SkibidiToilet', class: SkibidiToilet, data: assets.enemies.skibidiToilet, xPercentage:  0.75, minPosition: 0.5 },
    { name: 'escaper', id: 'player', class: PlayerSkibidi, data: assets.players.escaper  },
     // { name: 'laser', id: 'Laser', class: Laser, data: assets.obstacles.laser, xPercentage:  0.75, yPercentage: 0.5 },
    { name: 'tolietfinish', id: 'finishline', class: FinishLine, data: assets.obstacles.toiletfinish, xPercentage: 0.85, yPercentage: 0.77 },
    { name: 'complete3', id: 'background', class: BackgroundTransitions,  data: assets.backgrounds.complete3 },
  ];
  ;

  const GameSetterSkibidi = {
    tag: 'Skibidi',
    assets: assets,
    objects: skibidiGameObjects
  }
```



<br>


>## Single Responsiblility
### UpdateFrameX Timer
- First Condition: if (this.frameX < this.maxFrame) {
This condition checks if the current frame frameX is less than the maximum frame maxFrame.
If this condition is true, it means we haven't reached the end of the animation sequence.
- Second Condition: if (this.counter > 0) {
This condition checks if the counter variable is greater than 0.
If counter is greater than 0, it means we are still counting down to keep the current frame for a number of animation frames.
- Incrementing Frame and Resetting Counter:
If the second condition (this.counter > 0) is true, we decrement the counter and keep the current frame (this.frameX).
If the second condition is false (i.e., this.counter is 0 or less), we advance to the next frame (this.frameX++) and reset the counter to this.animationSpeed.
- Resetting Frame:
If the first condition (this.frameX < this.maxFrame) is false, meaning this.frameX is at or beyond this.maxFrame, we reset this.frameX to this.minFrame.

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
>## Single Responsiblity
### Sprite animation
- featuring animationSpeed and PlayerbaseOneD

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


>## Finite State Machines
- Featuring code in PlayerBaseOneD allowing the sprite to updates it's movement using states such as left, right, idle, and jump. With idle having nothing with no animation to flip and  
- This finite state machine is used in PlayerBaseOneD which is what we used in our level for our sprite to move left and not only right.
If(this.state.direction === `left` is incorporated with the key A which allows your sprite to move left creating the state "Left" 
- Same as the left instead we use d as our "right". When the key d is pressed it initates state 
`right` which allows your sprite to move right.



```js
updateMovement() {
        switch (this.state.animation) {
            case 'idle':
                break;
            case 'jump':
                // Check condition for player to jump
                this.state.movement.up = true
                if (this.state.movement.up && !this.state.movement.falling) {
                    // jump
                    GameEnv.playSound("PlayerJump");
                    this.updateJump();
                    // start falling
                    this.state.movement.falling = true;
                }
                // break is purposely omitted to allow default case to run 
            default:
                // Player is moving left
                if (this.state.direction === 'left' && this.state.movement.left && 'a' in this.pressedKeys) {
                    // Decrease the player's x position according to run or walk animation and related speed
                    this.setX(this.x - (this.state.animation === 'run' ? this.runSpeed : this.speed));
                // Player is moving right
                } else if (this.state.direction === 'right' && this.state.movement.right && 'd' in this.pressedKeys){
                    // Increase the player's x position according to run or walk animation and related speed
                    this.setX(this.x + (this.state.animation === 'run' ? this.runSpeed : this.speed));
                }
                GameEnv.PlayerPosition.playerX = this.x
                GameEnv.PlayerPosition.playerY = this.y
        }
    }
```


## Draw.io Diagram
<br>

![Alt text]({{site.baseurl}}/images/Draw.io-explanation.png)








<br>

>## Transition Between Game levels
- Game loop is constantly running with GameEnv.update updating the game constatly
- 



```js
  * //Transitions to a new level. Destroys the current level and loads the new level.
     * @param {Object} newLevel - //The new level to transition to.
     */
    async transitionToLevel(newLevel) {
        this.inTransition = true;

        // Destroy existing game objects
        GameEnv.destroy();

        // Load GameLevel objects
        if (GameEnv.currentLevel !== newLevel) {
            GameEnv.claimedCoinIds = [];
        }
///

gameLoop() {
        // Turn game loop off during transitions
        if (!this.inTransition) {

            // Get current level
            GameEnv.update();
            const currentLevel = GameEnv.currentLevel;

            // currentLevel is defined
            if (currentLevel) {
                // run the isComplete callback function
                if (currentLevel.isComplete && currentLevel.isComplete()) {
                    const currentIndex = GameEnv.levels.indexOf(currentLevel);
                    // next index is in bounds
                    if (currentIndex !== -1 && currentIndex + 1 < GameEnv.levels.length) {
                        // transition to the next level
                        this.transitionToLevel(GameEnv.levels[currentIndex + 1]);
                    } 
                }
            // currentLevel is null, (ie start or restart game)
            } else {
                // transition to beginning of game
                this.transitionToLevel(GameEnv.levels[0]);
            }
        }
```


>## My Favorite feature that I made

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


- The reason that this is my favorite feature is because how I grew from this code and what I learned, and what I was able to do becausse of it

- From learning how to make UpdatePlayerX and OnePlayerbaseD It was challenging but eventually helped me in the end.

```js
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
- Because of UpdateFrameX I was able to learn more about conditional statments and single responsiblity.

```js
updateMovement() {
        switch (this.state.animation) {
            case 'idle':
                break;
            case 'jump':
                // Check condition for player to jump
                this.state.movement.up = true
                if (this.state.movement.up && !this.state.movement.falling) {
                    // jump
                    GameEnv.playSound("PlayerJump");
                    this.updateJump();
                    // start falling
                    this.state.movement.falling = true;
                }
                // break is purposely omitted to allow default case to run 
            default:
                // Player is moving left
                if (this.state.direction === 'left' && this.state.movement.left && 'a' in this.pressedKeys) {
                    // Decrease the player's x position according to run or walk animation and related speed
                    this.setX(this.x - (this.state.animation === 'run' ? this.runSpeed : this.speed));
                // Player is moving right
                } else if (this.state.direction === 'right' && this.state.movement.right && 'd' in this.pressedKeys){
                    // Increase the player's x position according to run or walk animation and related speed
                    this.setX(this.x + (this.state.animation === 'run' ? this.runSpeed : this.speed));
                }
                GameEnv.PlayerPosition.playerX = this.x
                GameEnv.PlayerPosition.playerY = this.y
        }
    }
```

- Althought I didn't make this code, tambien did, I had to learn what some of the code did to actually flip the sprite animation around without us needing to do much except delete the `right and left` rows we had in our orginal block of code for our sprite animation
