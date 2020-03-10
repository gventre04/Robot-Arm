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
* [Code](#Code)
* [Fritzing](#Fritzing)
* [Reflection](#Reflection)

## Pictures

## Code

### Mu Code


Put Mu Code Here 

import board #pylint: disable-msg=import-error
import busio #pylint: disable-msg=import-error
import time
from adafruit_motor import servo #pylint: disable-msg=import-error
import pulseio #pylint: disable-msg=import-error

uart = busio.UART(board.TX, board.RX, baudrate=9600)#transmit with pin tx, receive with rx, at a speed of 9600 pulses per second

pwm = pulseio.PWMOut(board.D13, frequency=50, duty_cycle=0)#set up the servos
pwm2 = pulseio.PWMOut(board.D12, frequency=50, duty_cycle=0)
pwm3 = pulseio.PWMOut(board.D11, frequency=50, duty_cycle=0)
pwm4 = pulseio.PWMOut(board.D4, frequency=50, duty_cycle=0)

servo1 = servo.Servo(pwm, min_pulse=500, max_pulse=2400)
servo2 = servo.Servo(pwm2, min_pulse=500, max_pulse=2400)
servo3 = servo.Servo(pwm3, min_pulse=500, max_pulse=2400)
servo4 = servo.Servo(pwm4, min_pulse=500, max_pulse=2400)

servo1angle = 0
servo2angle = 0
servo3angle = 0
servo4angle = 0

temp = ''#the most recent digit/symbol from the uart
store = []#an array of digits from the uart
empty = ''#used for combining strings into digitsaa


while True:
    temp = uart.read(1)#read one byte frmo uart
    if temp is not None:#check to see if there is data
        temp = temp.decode("utf-8")#turn the byte into a string

        if temp == "%":
            servo1angle = int(empty.join(store))#combine the contents of store with empty in between each element, then cast as an int
            store.clear()#remove every element from store
        elif temp == "#":
            servo2angle = int(empty.join(store))
            store.clear()
        elif temp == "$":
            servo3angle = int(empty.join(store))
            store.clear()
        elif temp == "@":
            servo4angle = int(empty.join(store))
            store.clear()

        else:
            store.append(temp)#add an element to store with value of temp
            servo1.angle = servo1angle#write an angle to a servo
            servo2.angle = servo2angle
            servo3.angle = servo3angle
            servo4.angle = servo4angle


            print(servo1angle, end="\t")
            print(servo2angle, end="\t")
            print(servo3angle, end="\t")
            print(servo4angle)

    else:
        print("all is quiet")

    time.sleep(0.01)#wait a little bit
### Processing Code

Put Processing Code Here
''''
import processing.serial.*;
Serial myPort;
color b = color(0, 0, 0);  // Define color 'b'
int servo1angle = 0;
int staticAngle = 0;
int servo2angle = 0;
int staticAngle2 = 0;
int servo3angle = 0;
int staticAngle3 = 0;
int servo4angle = 0;
int staticAngle4 = 0;

int oldmillis = 0;
String message = "";

void setup() {
  size(300, 400);
  background(0);
  println("Available serial ports:");
  println(Serial.list());
  myPort = new Serial(this, Serial.list()[2], 9600);
}
void draw() {
  servo1angle = round(map(mouseX, 0, 300, 0, 179));//maps the X position into something the servo would like
  servo2angle = round(min(179, map(mouseX, 0, 300, 0, 179)));
  servo3angle = round(min(179, map(mouseX, 0, 300, 0, 179)));
  servo4angle = round(min(179, map(mouseX, 0, 300, 0, 179)));

  background(230);//makes the background gray
  stroke(255, 0, 0);//gets the color to red
  strokeWeight(1);//makes the pen thickness very thin
  line(150, 0, 150, 300);//draws a line
  stroke(150, 0, 255);//sets the color to purple
  strokeWeight(5);
  fill(0, 0, 0, 0);//makes it so there's only an outline, so the rectangles will be border only
  rect(1, 2, 297, 299);//draw a rectangle
  rect(1, 300, 297, 97);
  textSize(30);//set text size
  fill(b);//set color
  text("Servo:", 20, 335);//write text
  text(servo1angle+"°", 160, 335);

  stroke(0);
  ellipse(mouseX, mouseY, 1, 1);
}
void keyPressed() {
  message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";

  if (keyPressed) {
    if (key == 'a' || key == 'A') {
      staticAngle = servo1angle;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }

    if (key == 'd' || key == 'D') {
      staticAngle++;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }

    if (key == 's' || key == 'S' ) {
      staticAngle--;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }

    if (key == 'q' || key == 'Q') {
      staticAngle2 = servo2angle;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'w' || key == 'W' ) {
      staticAngle2--;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'E' || key == 'e') {
      staticAngle2++;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'z' || key == 'Z') {
      staticAngle3 = servo3angle;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'c' || key == 'C') {
      staticAngle3--;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'x' || key == 'X') {
      staticAngle3++;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
    if (key == 'i' || key == 'I') {
      staticAngle4 = servo4angle;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }
     if (key == 'o' || key == 'O') {
      staticAngle4++;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }

    if (key == 'p' || key == 'P') {
      staticAngle4--;
      message = staticAngle+"%"+staticAngle2+"#"+staticAngle3+"$"+staticAngle4+"@";
    }

    if (millis()-oldmillis>=100) {//check if it has baaaeen 100 milliseconds since it last sent a message
      oldmillis =  millis();
      print(message);
      myPort.write(message);
    }
  }
}


## Fritzing

## Reflection 
