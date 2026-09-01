/* Self directed embedded systems project where I am trying to learn the fundamental building blocks behind a drone motor 
system. The 2 files (joystickMotorControl and MotorSpeedDirection) were the first 2 things I looked into. Below is what is in this
repo currently. 

1. MotorSpeedDirection.ino
The basic building block: controlling the speed and direction of a single DC motor using an H-bridge driver.
	-	Used an L293D dual H-bridge motor driver to control a 3–6V DC motor from an Arduino Uno
	-	Set motor direction by toggling two digital pins high/low
	-	Controlled motor speed using analogWrite() on a third pin

2. JoystickMotorControl.ino
Built on the first sketch by adding a joystick as an analog input to control motor speed and direction in real time.
	-	Read the joystick’s Y-axis value via an analog pin (0–1023 range, ~512 at rest/equilibrium)
	-	Derived a piecewise linear transfer function mapping joystick position to motor speed:
	-	Below center (jVal < 512): motor spins one direction, speed scales from max down to zero as the joystick approaches center
	-	Above center (jVal ≥ 512): motor spins the other direction, speed scales from zero up to max as the joystick moves further from center
	-	Worked out the two linear equations by hand from the joystick’s input range and the motor’s 0–255 PWM output range, then implemented        them directly in code

No AI was used in creation of code for the ELEGOO*

Hardware used
	•	ELEGOO UNO R3 (Arduino-compatible board)
	•	L293D dual H-bridge motor driver
	•	3–6V DC motor with fan blade
	•	Analog joystick module
	•	Breadboard, 9V battery, power supply module, jumper wires

What I have learned so far
My goal is to build a drone that can carry a dji camera so my dad can capture aerial pictures of stages and events that he runs. Here are
some of the things I have learned so far:
- H-Bridge wiring
- How to control speed and direction of a DC motor with code
- Benchmarking my specific joystick outputs to ensure code accuracy
- How to Wire a joystick that controls a single motor
- How to control speed and direction of a DC motor using my benchmarked joystick

My dad could have just bought a drone but I wanted to learn what goes into a drone as embedded systems is an area that I want to get more into. Also he mentioned that he is not on a strict timeline so I plan to chip away at learning other concepts into building this drone 
during the school year when I can squeeze it in. Here are the next few things I plan to do:

- Modify the JoyStickMotorControl code for 2 ESP32's that communicate joystick imput data to DC motor output data wirelessly.
  Real drones are wireless and learning how to code that into ESP32's would be a good next step
- Once the ESP32's are communicating wirelessly, I would like to add some sort of encryption model. Encrypting this drone
  might be a little bit overkill for what my dad wants but encryption is something that I am not familiar with yet but I find it 
  super fascinating and I want to learn how it works and this would be a good, real life example.
- Purchase 4 drone motors and create code for controlling all 4 motors for desired drone movements. This would involve
  learning the flight dynamics of a quad copter drone-which I was a little familiar with at one point but would need a refresher.
- Look into what else needs to go into a drone (batteries, transmitters/recievers, actual flight controllers, etc.)
- Design and Print a custom frame that can carry the dji camera that my dad already has. My friend has a 3D printer I can
  use and I am familiar in SolidWorks which I can use for free through my university login

Still a lot to do, but I am excited to see if there is overlap between any of my aerospace or electrical engineering classes
I am taking this year. I think my Model-Based Systems Engineering project could prove useful. Also making these first 2 files and running the code and working through troubleshoots was really enjoyable. It seems simple but when I got my code to run and work just to turn on the DC motor at a constant speed, that was extremely satisfying. Excited to keep going on this project. 
*/
