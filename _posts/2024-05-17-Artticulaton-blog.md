---
toc: false
comments: false
layout: post
title: Artiuclation blog
description: Artiuclation Blog
type: ccc
courses: { csse: {week: 13} }
---



- 




```js 
skibidiToilet: {
        src: "/images/platformer/sprites/skibidiEnemy.png",
        width: 529,
        height: 884,
        scaleSize: 60,
        speedRatio: 0.85,
      },
      skibidiTitan: {
        src: "/images/platformer/sprites/skibidiTItan.png",
        width: 529,
        height: 884,
        scaleSize: 1500,
        speedRatio: 0.85,
      },

///
     escaper: {
        src: "/images/platformer/sprites/escaper.png",
        width: 130,
        height: 140,
        scaleSize: 150,
        speedRatio: 0.7,
        animationSpeed: 8, //AnimationSpeed slowed the framers per second causing a slower animation and smoother animation run
        ///animationspeed:6
        idle: {
            left: { row: 0, frames: 5 },
            right: { row: 0, frames: 5},
        },
        walk: {
            left: { row: 1, frames: 6 },
            right: { row: 1, frames: 6 },
        },
        run: {
            left: { row: 2, frames: 7 },
            right: { row: 2, frames: 7 },
        },
        jump: {
            left: { row: 3, frames: 8 },
            right: { row: 3, frames: 8 },
        },
        hitbox: { widthPercentage: 0.3, heightPercentage: 0.8 }
      },
```
The sprite animation I created to match the level theme was pretty self explanatory as we copy and pasted code while adding our own hitboxes and animations for the code to follow through by making it a enemy and sprite


``` js
assets: {
    obstacles: {
      toilet: { src: "/images/platformer/obstacles/toilet.png",
      hitbox: { widthPercentage: 0.5, heightPercentage: 0.5}
    },
      laser: { src: "/images/platformer/obstacles/laser.png",
      hitbox: { widthPercentage: 0.1, heightPercentage: 0.5}
    },
      tube: { src: "/images/platformer/obstacles/tube.png",
      hitbox: { widthPercentage: 0.5, heightPercentage: 0.5}
      },
      tubeU: { src: "/images/platformer/obstacles/blue-tube-up.png",
      hitbox: { widthPercentage: 0.5, heightPercentage: 0.5}
      },
      tubeD: { src: "/images/platformer/obstacles/blue-tube.png",
    hitbox: { widthPercentage: 0.5, heightPercentage: 0.5}
      },
      tubeGreece: {src: "/images/platformer/obstacles/blue-tube-up.png",
      hitbox: { widthPercentage: 0.5, heightPercentage: 0.5}
      },
      cabin: {
        src: "/images/platformer/obstacles/cabin.png",
        hitbox: { widthPercentage: 0.5, heightPercentage: 0.5 }
      },
      vbucks: { src: "/images/platformer/obstacles/vbucks.png"},
      coin: { src: "/images/platformer/obstacles/coin.png" },
      snowflake: { src: "/images/platformer/obstacles/snowflake.png" },
      tubeD: {
        src: "/images/platformer/obstacles/blue-tube.png",
        hitbox: { widthPercentage: 0.5, heightPercentage: 0.5 }
      },
      star: { src: "/images/platformer/obstacles/star.png" },
      tree: {
        src: "/images/platformer/obstacles/tree.png",
        hitbox: { widthPercentage: 0.5, heightPercentage: 0.5 }
      },
      flag: {
        src: "/images/platformer/obstacles/flag.png",
        hitbox: { widthPercentage: 0.5, heightPercentage: 0.5 }
      },
      snitch: { src: "/images/platformer/obstacles/snitch.png" },
      whompingwillow: {
        src: "/images/platformer/obstacles/whompingwillowtree.png",
        hitbox: { widthPercentage: 0.5, heightPercentage: 0.5 }
      },
    },
    platforms: {
      grass: { src: "/images/platformer/platforms/grass.png" },
      sand: { src: "/images/platformer/platforms/sand.png" },
      snowyfloor: { src: "/images/platformer/platforms/snowyfloor.png" },
      snowywood: { src: "/images/platformer/platforms/snowywood.png" },
      alien: { src: "/images/platformer/platforms/alien.png" },
      bricks: { src: "/images/platformer/platforms/brick_wall.png" },
      lava: { src: "/images/platformer/platforms/lava.jpg" },
      sandstone: { src: "/images/platformer/platforms/sandstone.png" },
      cobblestone: { src: "/images/platformer/platforms/cobblestone.png" },
      complete3: { src: "/images/platformer/backgrounds/skibidiCompletion.png" },
      yellowpattern: { src: "/images/platformer/platforms/yellowtowerpattern.jpg" },
      yellowredpattern: { src: "/images/platformer/platforms/yellowredpattern.jpg" },
      lionpattern: { src: "/images/platformer/platforms/lionpattern.jpg" },
      turf: { src: "/images/platformer/platforms/turf.png" },
      block: { src: "/images/platformer/platforms/brick_block.png" }, //MAY need 3 new variables: sizeRatio, widthRatio, and heightRatio
```

While adding our background images and our platforms with our assests. I changed as platform we made while merging the code into a sand platform as SkibidiSand could not be defined or found. We also created our own sort of coins using v-bucks and made them hard to get to with our new obstacles using sand.
## Game Level
```js
{ name: 'escaper', id: 'player', class: PlayerSkibidi, data: this.assets.players.escaper  },
      { name: 'laser', id: 'Laser', class: Laser, data: this.assets.obstacles.laser, xPercentage:  0.75, yPercentage: 0.5 },
      { name: 'toiletTube', id: 'toiletEnd', class: Tree, data: this.assets.obstacles.toilet },
      { name: 'complete3', id: 'background', class: BackgroundTransitions,  data: this.assets.backgrounds.complete3 },
    ];
```
- Mr, Mortenson suggested we should use class: Tube instead of tree because Tube is the origin for tree, Tree allowed us to have perfect portions/scale size while also having a Glowblock covering the toilet thanks to our team. We plan to make the toilet smaller although in the actually level its almost as big as the whole screen.

