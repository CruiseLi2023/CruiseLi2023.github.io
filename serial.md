Arduino Controlled Space Defender

1. My Plan

For my project, I decided to create an arcade-style space shooting game called Arduino Controlled Space Defender using Python and PyGame.

My plan was to use a joystick sensor connected to an Arduino to control a spaceship on my laptop. Instead of using a keyboard, I wanted to use the physical joystick to move the spaceship around the screen.

The joystick has two axes:

X-axis: Moves the spaceship left and right.

Y-axis: Moves the spaceship up and down.

Button: Fires lasers at incoming enemies.

I chose a joystick because it allows me to control the game in a more interactive way. It also makes the project feel more like a real arcade game.

The goal of the game is to shoot the red enemy squares using the spaceship. Every time I hit an enemy, I earn 100 points.

2. My Process

Step 1: Creating the Game

First, I used Python and PyGame to build the basic game.

I created:

A green triangle to represent the player's spaceship.

Red squares to represent enemies.

Yellow rectangles to represent laser shots.

A scoreboard to keep track of points.

A dark background to make the game look more like space.

I also programmed the enemies to move down the screen. When an enemy is hit by a laser, it disappears and respawns in a random position.

Step 2: Connecting Arduino to Python

Next, I worked on connecting the Arduino to Python using the PySerial library.

The Arduino sends three values through serial communication:

JOY_X,JOY_Y,BUTTON

For example:

512,512,1

These values represent the horizontal joystick position, vertical joystick position, and button state.

Python reads these values using PySerial and converts them into game controls.

Step 3: Programming the Controls

I added a function called read_arduino_input() that reads the latest serial data from the Arduino.

I used different joystick values to determine which direction the spaceship should move.

If the X value is below 400, the spaceship moves left.

If the X value is above 600, the spaceship moves right.

If the Y value is below 400, the spaceship moves up.

If the Y value is above 600, the spaceship moves down.

If the button is pressed, the spaceship fires a laser.

I also added a cooldown system so that the spaceship cannot fire too quickly.

Step 4: Adding Keyboard Controls

I included keyboard controls as a backup in case the Arduino is disconnected.

The keyboard controls are:

Arrow keys or WASD to move.

Spacebar to shoot.

This allowed me to continue testing the game even without an Arduino connection.

How I Used AI

I used ChatGPT to help me understand how PySerial works and how to connect Arduino sensor values to my Python game.

AI also helped me organize the code, understand how to read serial data, and work through the game mechanics. I used these explanations to help build and understand my project.

3. My Results

I successfully created a playable space shooting game using Python and PyGame.

The game includes:

A controllable spaceship.

Five enemies that move down the screen.

A laser shooting system.

Collision detection between lasers and enemies.

A scoring system that awards 100 points for every enemy hit.

Keyboard fallback controls.

A serial connection status display.

The screenshot below shows my game running with a score of 400, meaning that four enemies have been hit.



Current Status: The game itself runs, and the keyboard controls work. The Arduino serial connection still needs to be verified. My screenshot shows COM3 as disconnected, while my current Python code is configured to use COM4. I need to make sure the correct port is selected and that the Arduino is sending data in the expected format.

4. What I Learned

Through this project, I learned how to combine hardware and software to create something interactive.

Some of the things I learned include:

How serial communication works between Arduino and Python.

How to use PySerial to receive sensor data.

How to use joystick values as game inputs.

How to create a game using PyGame.

How to detect collisions between different objects.

How to use conditional statements to control game mechanics.

One of the most interesting parts of this project was learning how information from a physical joystick can be converted into actions inside a computer game.

Overall, this project helped me understand how Arduino and Python can work together to create interactive applications.





There were lots of problems like the hardware not working, not understanding how to use pygame and serial. And sometimes the COM4 would just say not connected.
