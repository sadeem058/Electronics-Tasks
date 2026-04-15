![t1](https://github.com/sadeem058/Electronics-Tasks/blob/main/task1.png)

# Solve Q1:
The project uses an Arduino Uno to control a small kettle simulation system.
![c](https://github.com/sadeem058/Electronics-Tasks/blob/main/componint1.png)

## Components
Components used in this project:

Arduino Uno
HC-SR04 Ultrasonic Sensor
TMP36 Temperature Sensor
Buzzer
LED
Push Button
Resistor
Breadboard
Jumper wires

## Wiring & Pin Mapping

Component	Arduino Pin
Temperature Sensor (TMP36)	A0
Buzzer	8
LED	13
Push Button	7
Ultrasonic Trig	9
Ultrasonic Echo	10
VCC	5V
GND	GND

## How It Works

This project simulates a smart kettle system.
The Ultrasonic Sensor detects if a person is near the kettle.
If someone comes closer than 20 cm, the system starts working.

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/ultra1.png)

The system can also start by pressing the push button.

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/buzzer1.png)

When the system starts:
The LED turns on to indicate that the kettle is heating.
The temperature value increases gradually to simulate water heating.
When the temperature reaches 100°C, the buzzer plays a sound once to indicate that the water has boiled, and the LED turns off.
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/ultra2.png)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/buzzer2.png)
The alarm only plays once to avoid repeating the sound.

## Code

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/code1-1.png)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/code1-2.png)
![3](https://github.com/sadeem058/Electronics-Tasks/blob/main/code1-3.png)

## Explanation

int buzzer = 8;
This line defines the buzzer pin connected to pin 8.

int led = 13;
Defines the LED pin used as an indicator.

int button = 7;
Defines the push button pin.

int trigPin = 9;
Defines the trigger pin for the ultrasonic sensor.

int echoPin = 10;
Defines the echo pin used to receive the ultrasonic signal.

bool kettleOn = false;
A variable used to check if the kettle system is running.

bool alarmPlayed = false;
This variable prevents the buzzer from repeating.

long duration;
Stores the time taken for the ultrasonic wave to return.

int distance;
Stores the calculated distance from the sensor.

float temperature = 25;
Initial temperature value used to simulate heating.

pinMode(buzzer, OUTPUT);
Sets the buzzer pin as an output.

pinMode(led, OUTPUT);
Sets the LED pin as an output.

pinMode(button, INPUT_PULLUP);
Configures the button as input with internal pull-up resistor.

pinMode(trigPin, OUTPUT);
Sets the ultrasonic trigger pin as output.

pinMode(echoPin, INPUT);
Sets the echo pin as input.

digitalWrite(trigPin, HIGH);
Sends a signal from the ultrasonic sensor.

duration = pulseIn(echoPin, HIGH);
Measures the time taken for the echo to return.

distance = duration * 0.034 / 2;
Calculates the distance in centimeters.

if (distance <= 20)
Checks if someone is close to the sensor.

kettleOn = true;
Turns the system on.

digitalWrite(led, HIGH);
Turns on the LED to show that the kettle is heating.

temperature = temperature + 4;
Gradually increases the temperature value.

if (temperature >= 100)
Checks if the water reached boiling temperature.

tone(buzzer, 1000);
Plays the buzzer sound.

noTone(buzzer);
Stops the buzzer.

alarmPlayed = true;
Prevents the buzzer from repeating again.

# Solve Q2:

This project is built using an Arduino Uno to detect distance and give visual and sound alerts.
![c2](https://github.com/sadeem058/Electronics-Tasks/blob/main/componint2.png)

## Components

Components used:

Arduino Uno
HC-SR04 Ultrasonic Sensor
Buzzer
3 LEDs (Green, Yellow, Red)
3 Resistors
Breadboard
Jumper wires

## Wiring & Pin Mapping

Arduino Pin
Ultrasonic Trigger	6
Ultrasonic Echo	5
Green LED	8
Yellow LED	9
Red LED	10
Buzzer	3
VCC	5V
GND	GND

## How It Works

This project uses an ultrasonic sensor to measure the distance between the sensor and an object.

Depending on the distance, different LEDs turn on:

If the object is within 30 cm, the green LED turns on.
![g](https://github.com/sadeem058/Electronics-Tasks/blob/main/green.png)
If the object is within 20 cm, the yellow LED turns on.
![y](https://github.com/sadeem058/Electronics-Tasks/blob/main/yellow.png)
If the object is within 10 cm, the red LED turns on.
![r](https://github.com/sadeem058/Electronics-Tasks/blob/main/red.png)
The buzzer also gives different alerts depending on the distance:

When the object is very close (≤10 cm), the buzzer makes a fast high-pitch sound.
When the object is medium distance (≤20 cm), the buzzer makes a slower sound.
When the object is farther than 20 cm, the buzzer stops.

This helps simulate a simple distance warning system, similar to parking sensors in cars.

## Code
![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/code2-1.png)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/code2-2.png)

## Explanation

int val = 0;
A variable used to store the measured distance.

int buzzer = 3;
Defines the pin connected to the buzzer.

long readUltrasonicDistance(int triggerPin, int echoPin)
This function measures the distance using the ultrasonic sensor.

pinMode(triggerPin, OUTPUT);
Sets the trigger pin as an output.

digitalWrite(triggerPin, LOW);
Clears the trigger signal.

digitalWrite(triggerPin, HIGH);
Sends a pulse from the ultrasonic sensor.

delayMicroseconds(10);
Keeps the pulse active for 10 microseconds.

pinMode(echoPin, INPUT);
Sets the echo pin to receive the reflected signal.

return pulseIn(echoPin, HIGH);
Measures how long the echo signal takes to return.

Serial.begin(9600);
Starts serial communication to display distance in the serial monitor.

pinMode(8, OUTPUT);
Sets the green LED pin as output.

pinMode(9, OUTPUT);
Sets the yellow LED pin as output.

pinMode(10, OUTPUT);
Sets the red LED pin as output.

val = 0.01723 * readUltrasonicDistance(6, 5);
Converts the ultrasonic signal time into distance in centimeters.

Serial.println(val);
Prints the measured distance in the serial monitor.

digitalWrite(8, val <= 10);
Turns on the green LED if the distance is 10 cm or less.

digitalWrite(9, val <= 20);
Turns on the yellow LED if the distance is 20 cm or less.

digitalWrite(10, val <= 30);
Turns on the red LED if the distance is 30 cm or less.

tone(buzzer, 2000);
Makes the buzzer produce a high-pitch sound.

tone(buzzer, 1000);
Produces a lower sound.

noTone(buzzer);
Stops the buzzer sound.

![t2](https://github.com/sadeem058/Electronics-Tasks/blob/main/Screenshot%20(74).png)

# Solve Q1,2:
![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/WhatsApp%20Image%202026-04-16%20at%201.58.21%20AM.jpeg)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/WhatsApp%20Image%202026-04-16%20at%201.58.22%20AM%20(1).jpeg)
![3](https://github.com/sadeem058/Electronics-Tasks/blob/main/WhatsApp%20Image%202026-04-16%20at%201.58.22%20AM.jpeg)

This project is built using an Arduino Uno to control two motors and display the status on an LCD.
![c3](https://github.com/sadeem058/Electronics-Tasks/blob/main/components3.png)

## Components
Components used:
Arduino Uno
L293D Motor Driver
2 DC Motors
LCD I2C (16x2)
9V Battery
Jumper wires

## Wiring & Pin Mapping
Arduino Pin
L293D IN1    8
L293D IN2    9
L293D IN3    10
L293D IN4    11
LCD SDA      A4
LCD SCL      A5
VCC          5V
GND          GND

## How It Works
This project controls the movement of two motors in a specific sequence while displaying the direction on the LCD.
Depending on the code, the motors perform these movements:
First, both motors move forward for 30 seconds.
![f](https://github.com/sadeem058/Electronics-Tasks/blob/main/forword.png)
Then, both motors move backward for 60 seconds.
![b](https://github.com/sadeem058/Electronics-Tasks/blob/main/back.png)
After that, the robot moves right and left repeatedly for 1 minute.
Finally, all motors stop.
The LCD shows the current command (Forward, Backward, Right, Left, or Stop) during each step.

## Code

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/code3-1.png)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/code3-2.png)
![3](https://github.com/sadeem058/Electronics-Tasks/blob/main/code3-3.png)
![4](https://github.com/sadeem058/Electronics-Tasks/blob/main/code3-4.png)
![5](https://github.com/sadeem058/Electronics-Tasks/blob/main/code3-5.png)

## Explanation

#include <Wire.h>
Library for I2C communication.

#include <LiquidCrystal_I2C.h>
Library to control the LCD display.

LiquidCrystal_I2C lcd(0x27, 16, 2);
Defines the LCD address and size.

int IN1 = 8;
Defines the pin for motor control.

lcd.init();
Initializes the LCD screen.

lcd.backlight();
Turns on the screen light.

forward();
Function to move both motors forward.

backward();
Function to move both motors backward.

stopMotors();
Function to turn off all motor signals.

lcd.clear();
Clears the screen to write a new message.

lcd.print("Forward");
Displays the word "Forward" on the screen.

delay(30000);
Wait for 30 seconds while moving.

unsigned long startTime = millis();
Starts a timer to track the 1-minute movement.

while (millis() - startTime < 60000)

![task3](https://github.com/sadeem058/Electronics-Tasks/blob/main/task3.png)

# Solve Q1:
![com4](https://github.com/sadeem058/Electronics-Tasks/blob/main/components4.png)

## Components

Arduino Uno
5 × Servo Motors (SG90)
Breadboard
Jumper Wires

## Wiring & Pin Mapping

Power Connections:
All servos:
Red (VCC) → 5V on Arduino (via breadboard)
Brown/Black (GND) → GND on Arduino
Signal Connections:
Servo 1 → Pin 3
Servo 2 → Pin 5
Servo 3 → Pin 6
Servo 4 → Pin 9
Servo 5 → Pin 10

## How It Works

In this project:

All 5 servo motors move together using a sweeping motion.
They rotate from 0° to 180° and back.
![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/1.png)
This motion runs for 2 seconds only.
After that:
All servos move to 90° (center position).
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/2.png)
The program stops completely.

## Code 

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/code4-1.png)
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/code4-2.png)

## Explanation

#include <Servo.h>
Includes the Servo library to control servo motors.

Servo s1, s2, s3, s4, s5;
Creates 5 servo objects.

int pos = 0;
Variable to store the servo position (angle).

unsigned long startTime;
Stores the start time of the program.

void setup() {
Runs once when the Arduino starts.

  s1.attach(3);
  s2.attach(5);
  s3.attach(6);
  s4.attach(9);
  s5.attach(10);
Attaches each servo to its corresponding pin.

  startTime = millis();
Records the start time in milliseconds.

void loop() {
Runs continuously after setup.

while (millis() - startTime < 2000) {
Runs the sweeping motion for 2 seconds (2000 ms).

for (pos = 0; pos <= 180; pos++) {
Moves the servos from 0° to 180°.

  s1.write(pos);
  s2.write(pos);
  s3.write(pos);
  s4.write(pos);
  s5.write(pos);
Sends the same angle to all servos (they move together).

delay(15);
Adds a small delay for smooth movement.

for (pos = 180; pos >= 0; pos--) {
Moves the servos back from 180° to 0°.

s1.write(90);
s2.write(90);
s3.write(90);
s4.write(90);
s5.write(90);
After 2 seconds:
Sets all servos to the center position (90°).
while(true);
Stops the program completely (no further execution).
A loop that repeats movements for 60 seconds.

while (1);
Ends the program so it doesn't repeat.

# Solve Q2:

![com1](https://github.com/sadeem058/Electronics-Tasks/blob/main/components5-1.png)

## Components

ESP32
Stepper Motor
A4988 Stepper Driver
Jumper Wires

## Wiring & Pin Mapping

![comp2](https://github.com/sadeem058/Electronics-Tasks/blob/main/components5-2.png)

A4988 Driver → ESP32:
STEP → GPIO 18
DIR → GPIO 19

Power Connections:
VMOT → External motor power (e.g., 9V–12V)
GND (driver) → GND (ESP32)
VDD → 3.3V (ESP32)

Motor Connections:
The 4 wires of the stepper motor → connected to A4988 outputs (1A, 1B, 2A, 2B)

Note:
Always connect GND of ESP32 and driver together.

## How It Works

In this project:

The ESP32 controls a stepper motor using the A4988 driver.
The motor performs:
One full rotation clockwise
![2](https://github.com/sadeem058/Electronics-Tasks/blob/main/5-3.png)
One full rotation counterclockwise
![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/5-2.png)
Gradual acceleration
Constant high-speed rotation for 2 seconds
Gradual deceleration
After completing all actions, the program stops.
![3](https://github.com/sadeem058/Electronics-Tasks/blob/main/5-1.png)

## Code 

![1](https://github.com/sadeem058/Electronics-Tasks/blob/main/code5.png)

## Explanation

#define STEP_PIN 18
#define DIR_PIN 19
Defines the pins used to control the stepper driver:

STEP → controls stepping
DIR → controls direction
#define STEPS_PER_REV 200
Number of steps for one full revolution (typical stepper motor).

void stepMotor(int steps, int delayTime) {
Function to rotate the motor a specific number of steps.

for (int i = 0; i < steps; i++) {
Loop for each step.

digitalWrite(STEP_PIN, HIGH);
delayMicroseconds(delayTime);
digitalWrite(STEP_PIN, LOW);
delayMicroseconds(delayTime);
Creates a pulse signal:

HIGH → step forward
LOW → complete the step
delay controls speed
void setup() {
Runs once at startup.

pinMode(STEP_PIN, OUTPUT);
pinMode(DIR_PIN, OUTPUT);
Sets control pins as outputs.

void loop() {
Main loop of the program.

1. Full Rotation Clockwise

digitalWrite(DIR_PIN, HIGH);
stepMotor(STEPS_PER_REV, 1000);
Sets direction to clockwise
Moves one full revolution
delay(500);
Short pause.

2. Full Rotation Counterclockwise

digitalWrite(DIR_PIN, LOW);
stepMotor(STEPS_PER_REV, 1000);
Reverses direction
Moves one full revolution
delay(1000);
Pause before next stage.

3. Gradual Acceleration
digitalWrite(DIR_PIN, HIGH);
Sets direction again.

for (int d = 2000; d > 500; d -= 100) {
  stepMotor(20, d);
}
Starts slow (delay = 2000 µs)
Gradually increases speed (delay decreases)

4. Constant High Speed (2 seconds)

unsigned long startTime = millis();
while (millis() - startTime < 2000) {
  stepMotor(20, 500);
}
Runs motor at maximum speed for 2 seconds

5. Gradual Deceleration
for (int d = 500; d < 2000; d += 100) {
  stepMotor(20, d);
}
Slowly reduces speed until it stops
while (true);
Stops the program completely.
