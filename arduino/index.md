# My Arduino Circuit Designs :

Visit Circuit Designs [Home](https://sparkscratch-p.github.io/circuit-designs/) and discover more !!!

[![cdl](https://raw.githubusercontent.com/SparkScratch-P/circuit-designs/b28d1d84b3db9c04819ff8a560a1fc33a76c74ed/circuit%20designs%20logo.svg)](https://sparkscratch-p.github.io/circuit-designs/)

This contains some of my best arduino circuit designs from TinkerCAD. Scroll Down to see and simulate!
---
 
### Arduino LED blink

Blinking an LED build with Arduino

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/kUPuxhc6anK?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Dual RGB LED Blink (Arduino)

ALternatively blinks red, green, and blue LED bulbs, along with the same color RGB.

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/cnrxaSt0ftD?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Emergency Car Alert

Have hurry for office? feeling sleepy? fear to sleep in the car? No Worry! Strange right? It is quiet XD !!! As u move closer to a car, or a wall, this alert engine in ur car will sense u getting closer, and it will make noises, and vibrate, to wake u up! The closer u move, the wider is the voice, to wake u up!
It is indeed useful!

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/jMlUbANbkLv?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Ultrasonic Vehicle Distance Indicator

It is an ultrasonic Arduino distance indicator that uses a single RGB LED to alert or indicate a driver getting close to another vehicle on the road. It uses the Red-yellow-green traffic light format to suggest your action.

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/cggjhz7kMEH?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Automatic Air-Cooler Controller

A very simple design of a circuit that automatically starts the motor of an Air Cooler when the temperature rises above 27 deg. C and switches it off once it goes down! This will help save lots of electrical energy and reduce pollution caused by all-time running ACs.

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/eYvK2NJuWKA?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Automatic Water-Pump (Arduino Zero-Radiation Edition)

It is a new tilt-based water pump controller. The tilt sensor is to be attached to a fulcrum-floating rod, like in a cistern. This will automatically switch on the pump when the water level reduces and switches it off once the tank gets filled!

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/czAL5FY1VsI?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Heating Alert

This alert-based sensor will ring the buzzer once the ambient temperature of the sensor grown more than 50 degrees Celcius. This can be very useful to detect unexpected or harmful temperature increase in circuit equipment and chemical apparatus.

<iframe width="560" height="350" src="https://www.tinkercad.com/embed/6ERZGU1c7QK?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>


### Smart Dustbin

This is the mechanism of a Smart Dustbin. It is fitted with two systems : (i) The system of automatic closing snd opening when it detects and humanoid movement in front of the dustbin. This is sensed by a PIR, provided, there is space to dump more. (ii) The Second system includes a HCSR04 Ultrasonic Distance Sensor that measures the level of trash in the bin. Once it is filled to an optimum level, it will send an SMS to the Control Room, that will include the Dustbin number.

The embd doesnt contain GSM. So, the rest of the entire is available here.

```
#include <Servo.h>
#include <GSM.h>

#define PINNUMBER ""

// initialize the library instance
GSM gsmAccess;
GSM_SMS sms;


int movement = 0;

int remoteNum = 3322861212;

int txtMsg = 1001234;

int height = 0;

int i = 0;

int j = 0;

Servo servo_2;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  pinMode(8, OUTPUT);
  pinMode(11, OUTPUT);
  servo_2.attach(2, 500, 2500);

  pinMode(13, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(4, INPUT);

Serial.begin(9600);
  while (!Serial) {
    ; // wait for serial port to connect. Needed for native USB port only
  }

 // If your SIM has PIN, pass it as a parameter of begin() in quotes
  while (notConnected) {
    if (gsmAccess.begin(PINNUMBER) == GSM_READY) {
      notConnected = false;
    } else {
      Serial.println("Not connected");
      delay(1000);
    }
}

void loop()
  digitalWrite(8, HIGH);
  digitalWrite(11, LOW);
  servo_2.write(0);
  digitalWrite(13, HIGH);
  height = 0.01723 * readUltrasonicDistance(13, A0);
  if (height > 7) {
    digitalWrite(8, HIGH);
    digitalWrite(11, LOW);
    digitalWrite(7, HIGH);
    movement = digitalRead(4);
    if (movement == HIGH) {
      digitalWrite(7, LOW);
      servo_2.write(90);
    }
    delay(1000); // Wait for 1000 millisecond(s)
    digitalWrite(7, HIGH);
    movement = digitalRead(4);
    if (movement == LOW) {
      servo_2.write(0);
    }
    if (movement == LOW) {
      servo_2.write(0);
    }
  } else {
    if (height <= 7) {
      digitalWrite(8, LOW);
      digitalWrite(11, HIGH);
  sms.beginSMS(remoteNum);
  sms.print(txtMsg);
  sms.endSMS();
  Serial.println("\nCOMPLETE!\n");
       while (!(height > 7)) {
        delay(60000); // Wait for 60000 millisecond(s)
      }
    }
  }
  delay(10); 
}
```
<iframe width="560" height="350" src="https://www.tinkercad.com/embed/frbvXMCDgij?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>
---
## Keep a track on us and get more ideas for your projects!!!



































