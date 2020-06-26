# Elite Dangerous Reactive Lighting
>A reactive lighting project for Corsair keyboards

This is a project to add reactive lighting to Elite: Dangerous for Corsair keyboards.
All keyboard profiles have been created for the Strafe MK2.
I don't know if this program works for any other keyboards, so feedback is welcome.

I created this project because there is no other program to add reactive lighting for corsair keyboards yet.
The program uses a couple libraries and projects from other people, these are credited below.

# Usage

To start the program, click the `startup.bat` file.
This will start the 3 things necessary for this program to work.
1. Elite: Dangerous
1. The ICUE HTTP Server
1. The controller

## Elite: Dangerous
You need to own Elite: Dangerous on steam to run this program.
The `startup.bat` starts the game through steam, so it doesn't matter where the game is installed.
It won't work if you don't have the game on steam, because it will just redirect you to the store page.

## The ICUE HTTP Server
This is the server that 'talks' to the ICUE service to change the keyboard to the correct profiles for certain in-game events.
The server was created by @Zac-McDonald, and can be found at https://github.com/Zac-McDonald/iCUE-Custom-Game-Integration.

## The controller
This is the controller that controls what profiles show on the keyboard at certain in-game events
The controller was written by me, but with some inspiration from https://github.com/HectorBart/Elite-Dangerous-RGB-Lighting-Integration.
The referenced project is written for Razer keyboards, but doesn't include Corsair keyboards.

# How it works
Elite: Dangerous writes most of it's events to a log file.
From these files we can extract certain events that are of interest to us. 
The controller grabs the newest logfile, and reads the last line of the file on repeat.
Once the last line in the file includes an interesting event, the controller tells the server to set the keyboard to a specific profile that matches the event.
Some events need to last indefinitely.
These are called `States`.
States last forever, until cleared or overwritten by another state.
Some events only need to fire once or run out after a specific time.
These are called `Events`.
Events fire once, and the keyboard then returns to the state it was in before the event.

In the console of the Server, you can see the calls made to the server to set the states and events.

In the console of the Controller, you can see the last line written to the log file. Only some of these lines warrant a response from the controller.
The events the controller responds to are shown below.

# Events
