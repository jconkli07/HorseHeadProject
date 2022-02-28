# Horse Head Project

---

## Table of Contents
* [Project Planning](#Project-Planning)
* [Material List](#Material-List)
* [Wiring Diagram](#Wiring-Diagram)
* [Commented Code](#Commented-Code)
* [CAD Renderings](#CAD-Renderings)
* [Pics and Videos](#Pics-and-Videos)
* [Schedule](#Schedule)
* [Problems and Advice](#Problems-and-Advice)

---

## Project Planning
The planning for this project was a long and difficult task as we had to not only figure out how and where the horse motors were and worked but then how to code them for our specific needs and ideas. We started our planning by figuring out where the motors were and how to control them, which proved fairly simple as they were just DC motors controlled by two wires. We originally thought that the contact sensors on the face were the motors instead of the real ones on the neck which set back our planning. Once we figured out how the DC motors worked we were able to do a test of concept where we simply made the motors spin. The thing about our project was that we didn't really need to do much cad or planning and just simply needed to figure out how the horse worked, what it did, and how we could control that with the proper wiring and code. So we really didn't have a planning phase but just figuring out how the horse worked and how we could control it.

[Planning Doc 1](https://docs.google.com/document/d/101RoSjEOMPQxE0AH37Yg2qaNu6mBjdQd-6u1tl4LlXM/edit?usp=sharing)
<br>
[Planning Doc 2](https://docs.google.com/document/d/1hOP8ASZTMSHkqOUh0E6MfzvBzJc0gdXY6JWhEddZjh0/edit?usp=sharing)

---

## Material List
 - 2 Metro express boards
 - 2 Breadboards
 - 21 wires(approxamation)
 - 2 Drv8833 Motor drivers
 - 2 battery packs
 - 12 batteries
 - 1 Mecahnical horse
 - 1 box to hold batteries and wiring
 - Duct tape

---

## Wiring Diagram
![This is the Wiring](https://github.com/jconkli07/HorseHeadProject/blob/main/Pictures/Horseheadwiringdiagram.PNG)

### A Few Notes About The Wiring Diagram
The motor drivers in the diagram are not the same as the ones we used(Tinkercad didn't have those) so the wires going in and out of the motor driver on the diagram are simply a representation of what it would look like on the Drv8833 motor driver(the one we actually used) meaning that where the wires are placed is the same poistion they are in on the Drv8833. Other than that, the wiring is all correct besides the wiring for the battery boxes which is relativley simple as the two wires from the battery box go into the two ports in the Drv8833 that aren't connected to the breadboard and need to be screwed in(Should be self explanatory when you see the Drv8833). 

---

## Commented Code
### Code for first MetroExpress
```python
#Jay Conklin
#Make 2 motors of the horse head turn based on the input from 2 potentiometers

import board
import motor
import pwmio
import time
from analogio import AnalogIn

pwm1 = pwmio.PWMOut(board.D4, frequency=50)     #Sets 4 pwm outputs, 2 for each dc motor
pwm2 = pwmio.PWMOut(board.D3, frequency=50)
pwm3 = pwmio.PWMOut(board.D5, frequency=50)
pwm4 = pwmio.PWMOut(board.D6, frequency=50)

motor1 = motor.DCMotor(pwm1, pwm2)      #Uses the pwm outputs to crate 2 motor objects
motor2 = motor.DCMotor(pwm3, pwm4)

analog_in1 = AnalogIn(board.A0)     #Sets up the pins that it will use to read the potentiometers
analog_in2 = AnalogIn(board.A1)

sensors = [0, 0]       #This array will hold the throttle values of the 2 motors

def sensor_read():      #Takes the potentiometer values, runs them through the formula to convert them to the appropriate range,
                        #and sets them as values to be returned to the motors' throttles
    sensor1 = round(motor_calc(analog_in1.value, 1.625),2)
    sensor2 = round(motor_calc(analog_in2.value, 6.5),2)
    return[sensor1,sensor2,]
def motor_calc(input, n):
    if input==0:    #It will return -0.7 if the input is 0 to avoid an error
        return -0.7
    input=input/10000       #Takes the potentiometer's input (0-6.5), and makes it a range from -x to -0.5 and 0.5 to x, where x is dependent on the input value of n
                            #It will not output a number between -0.5 and 5 because that much power isn't strong enough to make the motors move.
    input1 = abs(input-3.25)/(input-3.25)
    input1 = input1*(abs(input-3.25)+5*n)
    input1 = input1/n
    if input1>5.1 or input1<-5.1:
        return input1/10
    else:                   #If the input is between -5.1 and 5 or between 5 to 5.1 it returns 0 so that is when the motors don't move
        return 0

while True:
    sensors = sensor_read()     #Calls the function that reads the sensors and returns the appropriate throttle values
    print(sensors)
    motor2.throttle = sensors[0]    #Sets the throttle of the motors based on the return values from sensor_read()
    motor1.throttle = sensors[1]
    time.sleep(.1)
```

### Code for second MetroExpress
```python
#Jay Conklin
#Make a motor on the horse head turn based on the input from a potentiometer
#For explanation see horse_code, this is the exact same code but with 1 motor/potentiometer instead of 2.

import board
import motor
import pwmio
import time
from analogio import AnalogIn

pwm1 = pwmio.PWMOut(board.D4, frequency=50)
pwm2 = pwmio.PWMOut(board.D3, frequency=50)

motor1 = motor.DCMotor(pwm1, pwm2)

analog_in1 = AnalogIn(board.A0)

sensors = 0

def sensor_read():
    sensor1 = round(motor_calc(analog_in1.value, 6.5),2)
    return sensor1
def motor_calc(input, n):
    if input==0:
        return -0.7
    input=input/10000
    input1 = abs(input-3.25)/(input-3.25)
    input1 = input1*(abs(input-3.25)+5*n)
    input1 = input1/n
    if input1>5.1 or input1<-5.1:
        return input1/10
    else:
        return 0

while True:
    sensors = sensor_read()
    print(sensors)
    motor1.throttle = sensors
    time.sleep(.1)
```

---


## Cad Renderings

---

## Pics and Videos
### Pics
<img src="Pictures/LeftView.png" alt="Left View" width="200" height="200">
<img src="Pictures/TopView.png" alt="Top View" width="200" height="200">
<img src="Pictures/RightView.png" alt="Right View" width="200" height="200">
<img src="Pictures/WideView.png" alt="Wide View" width="200" height="200">

### Mouth Chewing
[Video Link](https://drive.google.com/file/d/19oo2u8CKr6djT2KYptHYxpuuNmc0SYO_/view?usp=sharing)

### Mouth Chewing and Head Moving Up and Down
[Video Link](https://drive.google.com/file/d/1nHndtD1vkDzf1oPBAY6UI3tfLxE9DLCr/view?usp=sharing)

### Head Shaking and Blinking
[Video Link](https://drive.google.com/file/d/1g3tOSRPO_4eeNxPeC8NJDWHLcA9pIUPU/view?usp=sharing)

---

## Schedule
### Nov 17 - Christmas Break
We spent this time researching and testing out horse. We neede to do a lot of research about what kind of electronics the horse used and how we could control them. We were also looking for replacement parts if they would be needed.

### After Break - Jan 14
We spent this time getting the motors wired into the Metroexpress. This was harder than we thought as we had to use a motor driver (we used a DRV8833). It was hard to find data about people using DC motors with the DRV8833, but we figured it out eventually, [Adafruit's documentation](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-drv8833-dc-stepper-motor-driver-breakout-board.pdf) helped a lot with this.

### Jan 21 - Feb 4
We spent this time getting the motor working and figuring out the library that you have to use to control them (adafruit_motor.motor). We used 2 pwm outputs for each motor. The [Adafruit documentation for the motor library](https://docs.circuitpython.org/projects/motor/en/latest/api.html) and [Adafruit documentation for pwm in circuit python](https://learn.adafruit.com/circuitpython-essentials/circuitpython-pwm) helped me a lot with figuring this out. We got the motors moving off of set input from the computers.

### Feb 4 - Feb 18
We spent this time getting the potentiometers to control the movement of the servos. We had to write an algorithm to convert the range of potentiometer values to a motor throttle value [(linked here)](https://www.desmos.com/calculator/lihu1dxsw2). We also realized that to control the third motor we will need a 2nd metro express board so we wired a second board and motor driver to control it. We also designed a box to go onto the horse's neck that will hold all of the electronics.

### Feb 18 - Feb 25
We spent this time attaching the horse head back onto the body and documenting our project.

---

## Problems and Advice
One of our biggest problems was assuming that the electronic pictured above was a stepper motor, when it was in fact a contact sensor. We went into this project belieing that it was a motor that we could use to move the horse. We began taking apartthe horse and doing research on how to wire stepper motors. We then wrote all of the code for stepper motors and wired them up, and spent a long time trying to figure out why it wasn't turning. We eventually took it apart and realized that it was a contact sensor and not even a motor. This could have had terrible consequences for our project, however we ended up finding the real (dc) motors that controlled the horse. My advice for people to avoid this in the future is to plan out even tiny details when planning your project, and make sure to test your proof of concepts as early as possible. The reason that we couldn't test the proof of concept earlier is because there was a ton of research, planning wiring, and coding that needed to happen so that we could even use any of the electronics on the horse.

Another piece of advice that we learned from this project is not to make things more complicated if they don't have to be. We had a timer issue that meant that one board could only control 2 motors, and there are 3 total. This means that we needed 2 arduinos in order to control all of the motors, and we were at one point trying to chain them together so that one could control the other and we would just run code on one. After research this turned out to be very diffuclt and we decided to just have code running seperately on 2 arduinos.This ended up saving us a lot of time and it was just as effective as the original plan.
