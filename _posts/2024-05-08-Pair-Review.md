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

## Objects In javascript
- Object Instantiation:
When you create a new vending machine, you use the new keyword to instantiate an object from the VendingMachine class.
For example, const vendingMachine = new VendingMachine(); creates a new vending machine object named vendingMachine.
- Object Properties:
Each vending machine object (such as vendingMachine) has its own set of properties, like state, which holds its current state.
- Object Methods:
The vending machine objects also have methods defined in the VendingMachine class.
These methods represent actions that the vending machine can perform, such as selectItem, processPayment, and dispenseItem.
When you call these methods on a vending machine object (e.g., vendingMachine.selectItem('Soda')), it simulates the corresponding action.
- In summary, the VendingMachine class serves as a template for creating vending machine objects, each with its own state and behavior, allowing you to model and interact with virtual vending machines in JavaScript.