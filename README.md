# C++ Command Line Calculator

This is an simple calculator I made while learning C++.

It has two modes, regular and scientific, that a user can switch between.

### Overview

The program has 2 classes. A simple calculator class called Calculator, and a class that inherits Calculator called Scientific.

Some of the member functions of Calculator are virtual and are overridden in the Scientific class.

The program flow is:
1. Prompt user for the desired operation (polymorphically determine the message based on the current mode; show more options while in scientific mode)
2. Get additional data from the user (if doing addition, get 2 numbers)
3. Perform calculation, print to screen
4. Repeat from (1)

#### Calculator Class

This is the base class for the calculator program. It has data members and member functions that will display messages to the screen, prompt for user input, and perform calculations.

Specifically, Calculator has 2 protected data members, `result` and `mem`. `result` stores the result of the last computation. `mem` is used by the user to store a number in memory and access it later for further computation. They are both doubles, and they are initialized to 0 in the constructor.

As this class contains virtual functions, a virtual destructor will be included.

#### Scientific Class

Scientific inherits from the base class calculator. It calls the Calculator constructor to initialize `result` and `mem`.
It has many additional operation functions. `sin`, `cos`, `tan`, `ln`, `log`, `abs`, and `pow` all prompt the user for input, perform a calculation, save it in result, and print that result.

A virtual destructor is also included.

#### Main

The class set up allows the program to polymorphically call object methods depending on the type of the object. The main program will be one user entry loop. In the loop, a base class Calculator pointer (`calcPtr`) pointed at a Calculator object is used to call the Calculator member functions.

The switch to scientific mode will be made by pointing this Calculator class pointer at a derived Scientific class object. Now the program dynamically calls different member functions based on the state.

This simplifies the main code as the statement `calcPtr->welcome()` will automatically call the right welcome function, detailing out the proper options for the current mode.