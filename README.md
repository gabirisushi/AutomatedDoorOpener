# AutomatedDoorOpener
Automated Garage Door Opener using a Particle Photon

A couple of files here to help you get started...

(1) INO File - this is the firmware code to use with your Photon in the Particle Build UI.  Anything that references Particle. - you can comment out at this stage if you do not want to send the events to the Particle Cloud.

(2) Fritzing - If you are using Fritzing, this file should help you get started with the Breadboard layout and 2D schematic.  It could be a little different based on what components you use - such as relays and reed switches.

_

#Tutorial

_Approach_
_Simulating a Button Press_
_First step_: determine how you could simulate a button press - either from the mounted remote on the wall of the garage, on the opener unit itself, or through a remote. Since there are a lot of different garage door opener models and brands out
there, your method may be completely different than mine. For my application, I wanted to keep the wiring through the garage at a minimum, so I decided to sacrifice the remote and mount it near the wall unit.
Open up the remote and pull out the PCB (printed circuit board).  From there, find the terminals where the button is attached to and you are good to go.  All you need to do is wire your relay up to these 2 terminals so when you want to
open or close the door, the relay will short across these 2 terminals simulating a physical button press.

_Door Open or Closed_
_Second step_: install a couple of magnetic reed switches that will tell the general position of the door. Reed switches can either be On or OFF, based on the location of the matching component. In the "Closed" state, one of the reed switches has
continuity while the other is open - and vice versa.  
> With the magnetic reed switch based on the garage door to monitor the "Closed" state. So this approach required installing a reed switch at the base of the garage door opener and a second switch on the horizontal rail to capture when the door was
completely open.  I installed these in 2 stages - when the door was closed and open and both stages have the corresponding reed switch's matching up so they complete their respective circuit.

_Developing the circuit_
_Third step_: hook the reed switches to Photon's D2 and D4 pins to know what position they are in. They have 2 wires and which ones you connect to the digital pins or ground do not matter. However, you should add the resistors (R1 and R2),
otherwise, it will not work.
> Important: note that the Particle Photon operates at 3.3V as opposed to the standard 5V that you may be used to working with on an Arduino. That being said, you will need a 3V relay!

_Code_
_Fourth step_: The code is fairly straightforward and commented, so just read it. However, to monitor the position of the garage door you should use a State Machine, this will allow you to know what state the garage door is in (Closed, Door
Opening, Open, Door Closing) instead of just Closed or Open. Also, you should create some Particle Variables and Functions so you can monitor the status/location of the door and send the Photon button press commands from the Particle
Console, CLI (command line interface), web page/or custom app

_Testing_ // lol you should always test
_Fifth step_: Just put everything on a breadboard first to test out both the relay operating properly and the reed switches being either opened or closed. The reed switches should be pretty solid and close the circuit if the magnets are placed
within about 4 to 6 inches of the wired switch.  Since all you are simulating is a button press, not too much can go wrong here (Hopefully, otherwise just StackOverflow like the rest of us). However, you definitely should make sure your door is
operating properly before installing everything to realize only after that the sensor that you're using for your door isn't functioning. Trust me, the only good thing about squashing your dog or partner with the garage door is that
hopefully you are in a remote location far from the incident and can run away before the cops arrive.

_Next step_
Add this to your cv, now you are an IoT developer
