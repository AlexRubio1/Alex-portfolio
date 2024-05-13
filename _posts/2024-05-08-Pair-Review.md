---
toc: false
comments: false
layout: post
title: Pair Review Blog
description: Pair review
type: ccc
courses: { csse: {week: 10} }
---


## Finite state machines Key Compenents
- Class VendingMachine:
Represents the vending machine and its behavior.
- Constructor:
Initializes the vending machine's initial state to 'idle'.
- transition method:
Moves the vending machine from one state to another.
- selectItem method:
Simulates selecting an item, transitioning to the payment process if the machine is idle.
- processPayment method:
Simulates processing payment, transitioning to item dispensing if in payment process.
- dispenseItem method:
Simulates dispensing an item, transitioning back to idle state after dispensing.



```
%%javascript

class VendingMachine {
  constructor() {
    this.state = 'idle'; // Initial state
    this.processLogs = []; // Array to store process logs
  }

  // Function to transition to a new state
  transition(newState) {
    const transitionMsg = `Transitioning from ${this.state} to ${newState}`;
    this.processLogs.push(transitionMsg);
    this.state = newState;
  }

  // Function to simulate selecting an item
  selectItem(item) {
    if (this.state === 'idle') {
      const msg = `Selected item: ${item}`;
      this.processLogs.push(msg);
      this.transition('processingPayment');
    } else {
      this.processLogs.push('Please finish the current process before selecting a new item.');
    }
  }

  // Function to simulate processing payment
  processPayment(amount) {
    if (this.state === 'processingPayment') {
      const msg = `Payment processed: $${amount.toFixed(2)} received.`;
      this.processLogs.push(msg);
      this.transition('dispensingItem');
    } else {
      this.processLogs.push('Please select an item before processing payment.');
    }
  }

  // Function to simulate dispensing item
  dispenseItem() {
    if (this.state === 'dispensingItem') {
      const msg = 'Item dispensed. Enjoy your purchase!';
      this.processLogs.push(msg);
      this.transition('idle');
    } else {
      this.processLogs.push('Please complete the payment process before dispensing an item.');
    }
  }

  // Function to generate output message for the process
  generateOutput() {
    let output = '';
    this.processLogs.forEach(log => {
      output += log + '<br>';
    });
    return output;
  }
}

// Example usage
const vendingMachine = new VendingMachine();

// Simulating a vending machine process
vendingMachine.selectItem('Soda');
vendingMachine.processPayment(1.5);
vendingMachine.dispenseItem();

// Displaying process logs
element.innerHTML = vendingMachine.generateOutput();

```

## Objects in javascript
- Object Instantiation:
When you create a new vending machine, you use the new keyword to instantiate an object from the VendingMachine class.
For example, const vendingMachine = new VendingMachine(); creates a new vending machine object named vendingMachine.
- Object Properties:
Each vending machine object (such as vendingMachine) has its own set of properties, like state, which holds its current state.
- Object Methods:
The vending machine objects also have methods defined in the VendingMachine class.
These methods represent actions that the vending machine can perform, such as selectItem, processPayment, and dispenseItem.
When you call these methods on a vending machine object (e.g., vendingMachine.selectItem('Soda')), it simulates the corresponding action.

## How I incorported single responbiility principle into my own code

```
        escaper: {
          src: "/images/platformer/sprites/escaper.png",
          width: 130,
          height: 140,
          scaleSize: 150,
          speedRatio: 0.7,
          animationSpeed: 8,
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

- Scale Size: (scaleSize): Determined the scale of our sprite sheet having to fix it to an appropriate scaleSize
- Animations: (idle, walk, run, jump): Defines Defines the various different option for animation, Idle, Walk, Run, Jump, using (Left,Right,)
- AnimationSpeed: creating a timer causing the sprite to update slower making a smoother a fresher sprite animation pulling from Character.Js and much more using updateFrameX and
this.animationSpeed = data?.animationSpeed;
this.counter = this.animationSpeed;
causing the sprite to slow down in frames.
- Hitbox: Specifies the dimensions of the hitbox for collision detection purposes.

```
 updateFrameX() {
        if (this.frameX < this.maxFrame) {
            if(this.counter > 0){
                this.frameX = this.frameX;
                this.counter--;

            }
            else{
                this.frameX++;
                this.counter = this.animationSpeed;
            }
        } else {
            this.frameX = this.minFrame;
        }
    }
```

```
 this.animationSpeed = data?.animationSpeed;
        this.counter = this.animationSpeed;

```
this.animationSpeed = data?.anaimationSpeed; allowed the animation to slower down as this.counter caused updateFrameX to use if(this.cpunter > 0)
then this.frameX = this.frameX to slow down the frames used in the sprite sheet.