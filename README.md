# HorseHeadProject

## Project Planning:
The planning for this project was a long and difficult task as we had to not only figure out how and where the horse motors were and worked but then how to code them for our specific needs and ideas. We started our planning by figuring out where the motors were and how to control them, which proved fairly simple as they were just DC motors controlled by two wires. We originally thought that the contact sensors on the face were the motors instead of the real ones on the neck which set back our planning. Once we figured out how the DC motors worked we were able to do a test of concept where we simply made the motors spin. The thing about our project was that we didn't really need to do much cad or planning and just simply needed to figure out how the horse worked, what it did, and how we could control that with the proper wiring and code. So we really didn't have a planning phase but just figuring out how the horse worked and how we could control it. 

## Material List: 
 - 2 Metro express boards
 - 2 Breadboards
 - 21 wires(approxamation)
 - 2 Drv8833 Motor drivers
 - 2 battery packs
 - 12 batteries
 - 1 Mecahnical horse
 - 1 box to hold batteries and wiring
 - Duct tape

## Schedule:


## Problems/Advice
One of our biggest problems was assuming that the electronic pictured above was a stepper motor, when it was in fact a contact sensor. We went into this project belieing that it was a motor that we could use to move the horse. We began taking apartthe horse and doing research on how to wire stepper motors. We then wrote all of the code for stepper motors and wired them up, and spent a long time trying to figure out why it wasn't turning. We eventually took it apart and realized that it was a contact sensor and not even a motor. This could have had terrible consequences for our project, however we ended up finding the real (dc) motors that controlled the horse. My advice for people to avoid this in the future is to plan out even tiny details when planning your project, and make sure to test your proof of concepts as early as possible. The reason that we couldn't test the proof of concept earlier is because there was a ton of research, planning wiring, and coding that needed to happen so that we could even use any of the electronics on the horse.

Another piece of advice that we learned from this project is not to make things more complicated if they don't have to be. We needed 2 arduinos in order to control all of the motors, and we were at one point trying to chain them together so that one could control the other and we would just run code on one. After research this turned out to be very diffuclt and we decided to just have code running seperately on 2 arduinos.This ended up saving us a lot of time and it was just as effective as the original plan.

## Wiring diagram
![This is the Wiring](https://github.com/jconkli07/HorseHeadProject/blob/main/Pictures/Horseheadwiringdiagram.PNG)

### A Few Notes About The Wiring Diagram
The motor drivers in the diagram are not the same as the ones we used(Tinkercad didn't have those) so the wires going in and out of the motor driver on the diagram are simply a representation of what it would look like on the Drv8833 motor driver(the one we actually used) meaning that where the wires are placed is the same poistion they are in on the Drv8833. Other than that, the wiring is all correct besides the wiring for the battery boxes which is relativley simple as the two wires from the battery box go into the two ports in the Drv8833 that aren't connected to the breadboard and need to be screwed in(Should be self explanatory when you see the Drv8833). 
