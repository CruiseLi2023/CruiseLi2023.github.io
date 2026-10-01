# Simple Spinning Scanner

## Starting the 3D Scanner Project

For this project, we are beginning to build our own scanner using Arduino parts. This is the first stage of a larger project where we will eventually try to create a more complete 3D scanner.

Before we started building, we got to see a real 3D scanner being used for paleontology. The scanner was able to collect information about the surface and shape of an object and turn it into a digital model. In paleontology, this is useful because fossils can be studied digitally without always having to handle the real object.

Seeing the real scanner helped us understand what a 3D scanner is actually doing. It is not just taking a normal picture. It is collecting measurements from many different positions and using those measurements to understand the shape of an object.

## Recreating the Idea With Arduino

Our scanner will be much simpler than the professional scanner we saw. Instead of using expensive scanning equipment, we are trying to recreate the basic idea using Arduino parts.

The main parts we are using right now are an Arduino Uno, an ultrasonic sensor, a motor, a breadboard, and jumper wires.

![Scanner setup](images/basic.jpg)

The Arduino is basically the controller of the project. It can send instructions to the other parts and receive information from the sensors.

The ultrasonic sensor is meant to measure distance. It sends out a sound wave and can measure how far away an object is based on how long the sound takes to return.

The motor is important because eventually we want the sensor to move or rotate instead of only looking in one direction.

Right now, we are still putting these different parts together and figuring out how they will connect.

## The "Skateboard"

This first version is basically the "skateboard" of the 3D scanner.

The idea of the skateboard is that we are not trying to build the entire complicated scanner immediately. We are starting with the most basic parts and creating something simple that we can improve later.

At first, the goal is just to work toward a simple spinning 2D scanner. If the sensor can eventually rotate and measure distances from different directions, it can start collecting information about the area around it.

Later, more parts and more movement could be added to make the scanner more advanced and eventually work toward 3D scanning.

## Starting the Arduino Code

![Arduino code](images/basic_code.jpg)

We have also started looking at Arduino code for the ultrasonic sensor.

The code has different pins assigned for sending and receiving signals from the sensor. The Arduino can use these signals to eventually calculate distance.

At this point, we are still in the building stage. The first version is not complete yet. We are connecting the electronics, looking at the code, and trying to understand how all of the components are supposed to work together.

There are a lot of wires and different connections, so part of the process is making sure each component is connected to the correct place on the Arduino and breadboard.

## Why We Are Starting Simple

A real 3D scanner is much more complicated than what we are building right now. It can collect a huge amount of data and create very detailed models.

Instead of trying to copy the entire machine at once, we are breaking the problem into smaller steps.

The simple spinning scanner is our first step. It lets us focus on the basic idea of measuring distance and eventually moving the sensor around an object.

Once we understand how this basic version works, we can keep adding to it.

This is just the beginning of the project, but it gives us the foundation for the more advanced scanner we will build later.
