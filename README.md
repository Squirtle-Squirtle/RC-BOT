# RC-BOT
Hardware-Based Project using Arduino Uno Board R3


![RC-BOT](https://user-images.githubusercontent.com/86001943/210730744-abdb5101-d96b-42dd-bf21-2555e1de143b.jpeg)


## Components Used
1. Arduino Uno R3-- The microcontroller board based on the ATmega328P. All the other components are connected to this board and the embeddded c code was also uploaded to this board only to provide instructions for controlling the bot.
2. Motor Driver Shield L293D-- The L293D is a dual-channel H-Bridge motor driver that can control two DC motors or a single stepper motor. The shield includes two such motor drivers, it can control up to four DC motors or two stepper motors. This is used to provide proper voltage supply to the 4 DC Motors.
3. Bluetooth Module HC-05-- The Module used in controlling the bot wirelssly using a Mobile device with an application to provide proper commands.
4. DC Motors-- The motors are used to drive the wheels attached to it.
5. Li-ion Battery-- The batteries are used to supply continous required voltage to the Micro-controller.
6. Jumper Wires(M-M,M-F,F-F)-- The wires are used in wiring and connecting all the other components of the bot.


## Software Used
1. Arduino IDE
2. Mobile Based Controller- Bluetooth RC Car

## Programming Language Used
1. Embedded C

## Code(Embedded C)
#include <AFMotor.h>

AF_DCMotor motor1(1);
AF_DCMotor motor2(2);
AF_DCMotor motor3(3);
AF_DCMotor motor4(4);

char bt='S';
void setup()
{
  Serial.begin(9600);
 
  motor1.setSpeed(155);
  motor2.setSpeed(155);
  motor3.setSpeed(155);
  motor4.setSpeed(155);
  Stop();
}


void loop() {
 
bt=Serial.read();

if(bt=='F')
{
 forward(); 
}

if(bt=='B')
{
 backward(); 
}

if(bt=='L')
{
 left(); 
}

if(bt=='R')
{
 right(); 
}

if(bt=='S')
{
 Stop(); 
}

}
void forward()
{
  motor1.run(FORWARD);
  motor2.run(FORWARD);
  motor3.run(FORWARD);
  motor4.run(FORWARD);
}

void backward()
{
     motor1.run(BACKWARD);
  motor2.run(BACKWARD);
  motor3.run(BACKWARD);
  motor4.run(BACKWARD);
}
void left()
{
  motor3.run(FORWARD);
  motor2.run(FORWARD);
  motor1.run(BACKWARD);
  motor4.run(BACKWARD);
}
void right()
{
  motor3.run(BACKWARD);
  motor2.run(BACKWARD);
  motor1.run(FORWARD);
  motor4.run(FORWARD);
}
void Stop()
{
  motor1.run(RELEASE);
  motor2.run(RELEASE);
  motor3.run(RELEASE);
  motor4.run(RELEASE);
}

