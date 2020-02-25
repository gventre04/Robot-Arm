# Robot-Arm

Link to Robot Arm project Wiki from 2018/2019

[CHS Sigma Wiki Robot Arm](http://wiki.chssigma.com/index.php?title=Robot_Arm_Ghislain_and_Eli)

## Table of Contents
* [Robot Arm Planning](#Robot-Arm-Planning)
* [Robot Arm Documentation](##Robot-Arm-Documentation)

## Robot Arm Planning
* [Problem/Solution](#Problem/Solution)
* [Criteria and Constraints](#Criteria-and-Constraints)
* [Scope](#Scope)
* [Schedule](#Schedule)
* [Design](#Materials)
* [Materials](#Materials)

## Problem/Solution

### Problem

Our problem is finishing the robot arm that Ghislain and Eli worked on last year.
We want to code/program the arm to specifically pick up a plastic cup and move it around using the W A S D keys.

### Solution

To utilze the the keyboard, we will use processing to build a keyboard interface.
We have no plans to use potentiometers, so this arm will require a computer to work. 

We will be picking up where we left off last year, polishing up the solidworks (as it was mainly finished) and completing the wiring and coding of the box, which will be our main focus this year.

Our arm will consist of gears that will make up the arm of the robot, as well as many servos to control each individual section of the robot arm.


## Criteria and Constraints

### Criteria

* Code the robot arm so that the W A S D buttons will control its movement, this will be done using processing and Circuit Python.

* The robot arm's motion should be initiated by 180 servos controlling the gripper, and the other sections of the arm. We need to implicate gears into our project, these will likely be used to function the robot arm's gripper (open and close the teeth).

* The box should be powered by an easily accessible battery pack, and have visible power indicator (LED) and power switch.

* We will shape the gripper around the goal of picking up and moving a plastic cup, which weigh approximately 50 grams.  (stall torque of S3003 Servo is 56.8 oz/in. 4.1kg.cm (6.0v), stall torque of SG92R is  2.5kg /cm(4.8v) )


### Constraints

* We should follow the schedule and avoid taking longer than planned. Working in a timely fashion time shouldn’t be a problem.

* We should avoid printing anything that we won’t use.

* We should also make sure not to waste batteries by leaving them on overnight.

* We should make the robot arm an appropriate size so that we can fit all of our different components without making the space too crammed.

* Same goes with not making it too big so the arm will not fall over

* Servo stall torque is rather limited, arm cannot be too long or heavy.

* New year, new partner. It will be a challenge to figure out work from old partner, and take time for new partner to catch up.




## Scope

This project will definitely be challenging, even though we are doing the most basic design of the robot arm (articulated robot arm). Last year, Eli and Ghislian finished the solidworks aspect of this project, minus a couple of design errors in the bottom piece of the assembly. The main focus this year will be wiring and coding. Wiring will simply consist of attaching all the servos of the actual robot arm to the arduino that will be at the bottom of the box, making sure that the wiring is done neatly and efficiently. The coding will consist of using processing to program the robot arm's servos to be controlled using the W A S D keys on the keyboard. My main area for concern will be the mechanics of the whole box, I am afraid that the arm will either be too heavy to move smoothly, or that the gear system that will turn the arm won't function properly, as it was the result of the scrapped harmonic drive idea. 

## Schedule

| Week | Goals for G   | Goals for Deo | What G Accomplished  | What Deo Accomplished |
|:-----:|:-------------:|:-------------:|:--------------------:|:---------------------:|
|12/2/2019|Finish Robot Arm planning and bottom piece of assembly|Make a servo move with processing|||
|12/9/2019|

## Design 



## Materials 

(Add more, make more specific)

* Adafruit Metro Express

* 1 Prototyping Shield

* Wires

* 9V battery pack

* Acrylic

* 4-40 Screws and nuts

* 180 Rotation Servos (4)

* 1 Universal Asynchronous Receiver/Transmitter(UART)

* 1 Breadboard

* Battery Pack

## Robot Arm Documentation
* [Pictures](#Pictures)
* [Fritzing](#Fritzing)
* [Reflection](#Reflection)

## Pictures

## Fritzing

## Reflection 
