# Ultrasonic Distance Warning System

For this project, I built an ultrasonic distance warning system using an Arduino Uno. The system uses an HC-SR04 ultrasonic sensor to measure how far away an object is. Depending on the distance, different LEDs turn on and the buzzer changes its sound.

I chose this project because I already had some experience with Arduino, wiring LEDs, and using `digitalWrite()`. I wanted to build on those skills by adding a new input component that could actually sense something in the environment.

My new component was the **HC-SR04 ultrasonic sensor**. I learned how to connect and program it using the Arduino Project Hub HC-SR04 tutorial. I also used the Makeability Lab Arduino `tone()` tutorial to learn how to control the buzzer.

Sources:
- [Arduino Project Hub - HC-SR04 Ultrasonic Sensor](https://projecthub.arduino.cc/)
- [Makeability Lab - Arduino tone()](https://makeabilitylab.github.io/physcomp/arduino/tone.html)

---

## My Process and Iterations

### Iteration 1: Getting the ultrasonic sensor working
My first goal was just to make the ultrasonic sensor measure distance correctly.
I connected the HC-SR04 sensor to power and ground, and connected its **Trig** and **Echo** pins to digital pins on the Arduino.
The Arduino sends a very short pulse from the Trig pin:

digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

Then I used:
duration = pulseIn(echoPin, HIGH);
distance = (duration * 0.0343) / 2;
I printed the result to the Serial Monitor so I could check whether the sensor was actually detecting objects.
Serial.print("Distance: ");
Serial.println(distance);

At first, this was important because I did not want to add the LEDs and buzzer until I knew the sensor itself worked.

## Iteration 2: Adding distance LEDs
Once the sensor was measuring correctly, I added three LEDs: green, yellow, and red.
I wanted them to act like a warning system.

Green = object is about 20–30 cm away
Yellow = object is about 10–20 cm away
Red = object is closer than 10 cm
No LED = object is farther than the warning range

I used if and else if statements to decide which LED should turn on.

if (distance < 30 && distance > 20) {
  digitalWrite(ledgreen, HIGH);
  digitalWrite(ledyellow, LOW);
  digitalWrite(ledred, LOW);
}

else if (distance < 20 && distance > 10) {
  digitalWrite(ledgreen, LOW);
  digitalWrite(ledyellow, HIGH);
  digitalWrite(ledred, LOW);
}

else if (distance < 10) {
  digitalWrite(ledgreen, LOW);
  digitalWrite(ledyellow, LOW);
  digitalWrite(ledred, HIGH);
}

One problem I had was making sure only one LED was on at a time. I fixed this by setting the other two LEDs to LOW inside every condition instead of only turning the wanted LED on.

## Iteration 3: Adding the buzzer
After the LEDs worked, I added a buzzer so the device could give an audio warning too.
My first attempt was to treat the buzzer like an LED using:
digitalWrite(buzz, HIGH);
and
digitalWrite(buzz, LOW);

This could make the buzzer turn on and off, but it did not give me much control over the sound.
I found the Arduino tone() function and changed my code so I could control the buzzer frequency.
For example:

tone(buzz, 300);

This creates a 300 Hz sound.
I then used different frequencies for different distances:

tone(buzz, 300);
tone(buzz, 800);
tone(buzz, 1200);

This made the warning much easier to understand because the pitch became higher as the object got closer.

## Iteration 4: Making the warning more responsive
In my next version, I added another distance range for objects closer than 5 cm.
Instead of using one fixed frequency, I experimented with changing the frequency based on the measured distance.

else if (distance < 5) {
  digitalWrite(ledgreen, LOW);
  digitalWrite(ledyellow, LOW);
  digitalWrite(ledred, HIGH);

  tone(buzz, (15 - distance) * 100);
}

Now the sound can change based on how close the object actually is instead of always playing exactly the same warning tone.
I also used:

noTone(buzz);

when there was no object inside the warning range.
This was better than my earlier version because the buzzer now gave more information than simply being on or off.

## Final Working Circuit
My final circuit included:

Arduino Uno
HC-SR04 ultrasonic distance sensor
Green LED
Yellow LED
Red LED
Resistors
Piezo buzzer
Breadboard
Jumper wires

The ultrasonic sensor continuously checks the distance in front of it. The Arduino then uses that distance to decide which LED and buzzer frequency should be activated.

The basic logic is:

Far away
    ↓
No warning

20–30 cm
    ↓
GREEN + low tone

10–20 cm
    ↓
YELLOW + medium tone

5–10 cm
    ↓
RED + high tone

Under 5 cm
    ↓
RED + changing/high warning tone

This was my final working version of the project.

Technical Tidbit: How the Ultrasonic Sensor Measures Distance

The HC-SR04 does not directly "see" distance. Instead, it measures how long a sound wave takes to travel to an object and come back.

The process is:

Arduino
   |
   | 10 microsecond trigger
   v
HC-SR04
   |
   | ultrasonic sound wave
   | -------------------->
   |                     OBJECT
   | <--------------------
   | reflected sound wave
   v
HC-SR04

The Arduino first sends a short signal to the Trig pin.

digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

The sensor sends an ultrasonic sound pulse. The frequency is too high for humans to hear.

When the sound hits an object, it reflects back toward the sensor.
The Echo pin stays HIGH for the amount of time the sound takes to travel out and return.
I measure this time with:

duration = pulseIn(echoPin, HIGH);

Then I calculate distance using:

distance = (duration * 0.0343) / 2;

0.0343 is approximately the speed of sound in centimeters per microsecond.

I divide by 2 because the sound travels the distance twice:

sensor → object → sensor

Without dividing by two, I would calculate the total round-trip distance instead of the distance from the sensor to the object.

This helped me understand that the sensor is really measuring time, and the Arduino converts that time into distance.

## Peer Support
During the project, I helped Bruce with both his wiring and his code.
He was having trouble understanding how some of the wires should connect and how the Arduino code controlled those connections. I showed him where the wires should go and explained how the pins in the code matched the physical pins on the Arduino.
I also helped explain how the conditions in the code worked and how the Arduino decided when an output should turn on.
After we went through it together, he understood the wiring and coding better and was able to continue working on his project.
Helping him also made me think more carefully about my own circuit because I had to explain why each connection and line of code was there instead of only knowing that it worked.

## Use-Case Reflection
A system like this could be useful as a parking distance sensor for a car or garage.
For example, a driver could use it to know when the front of a car is getting close to a wall. When the car is far away, there would be little or no warning. As the car gets closer, the warning light and buzzer could become more urgent.
My current project would need several improvements before it could actually be used for this.
I would probably need a stronger and more reliable distance sensor, a louder buzzer, a case to protect the electronics, and a better power source. It could also use several sensors instead of only one so it could detect objects from different directions.
The skill I would rely on most if I continued developing this project would be debugging. A system with more sensors and outputs would have more possible problems, so I would need to test one section at a time and use the Serial Monitor to check whether the sensor readings were correct.
This project showed me how an input such as distance can be converted into several different outputs and behaviors.


