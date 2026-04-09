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

## Components

This project is built using an Arduino Uno to detect distance and give visual and sound alerts.

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
If the object is within 20 cm, the yellow LED turns on.
If the object is within 10 cm, the red LED turns on.

The buzzer also gives different alerts depending on the distance:

When the object is very close (≤10 cm), the buzzer makes a fast high-pitch sound.
When the object is medium distance (≤20 cm), the buzzer makes a slower sound.
When the object is farther than 20 cm, the buzzer stops.

This helps simulate a simple distance warning system, similar to parking sensors in cars.

## Code

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
