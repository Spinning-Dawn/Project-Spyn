# Project-Spyn
Engineering project for an autonomous EV3 compatible robot built for course navigation and payload pick up/drop off. 

## Team
- Angel Garcia    (Programmer/builder)
- Chas Scichilone (Programmer/builder)
- Jose Villagrana (Programmer/builder)

## Overview
Using a touch sensor, color sensor, and an ultrasonic sensor, our robot "UY" can navigate randomized courses and avoid obstacles. The robot frame was custom built by our team using parts from Robot Shop's EV3 kit. Our goal was for our robot to navigate from the starting position to a pickup point where a person in a wheelchair (a cardboard mockup) would be waiting. Our robot would pick them up, drive to another point in the course, safely drop them off, then return to its starting position.

## How It Works
Our first decision when building the robot was to have our claw front facing. We figured it would be easier to program course navigation having in mind the front of the robot is where the claw is (the claw will be called using C in our code). The claw will lower its tongs so they slide just below the wheelchair, then we lift the claw slightly so the wheelchair is picked up at a 20-30 degree angle. This allowed us to keep the wheelchair on the claw even while our robot was bumping around and stopping and moving a bunch. For movement we had 2 motors, each powered one tire in the back of the robot (in the code you'll see calls with A and B). The motors for these tires were big enough that we based our EV3 brick support structure on top of them (the wired mess on top of the robot). Finally, our sensor suit saw multiple changes across development. The goal was to navigate using the wall follower technique, having our robot trace the right most wall and turning left whenever we hit something in front of us. Initially, we wanted just a gyro and touch sensor, but we found the gyro to be very inaccurate. When using it for course correction while driving straight, the gyro would report 2-8 degree variations from any slight bumps or abrupt movements. This led to it over correcting and our robot started driving into walls seconds after we launched it. We found out most of the class had the same problem, and decided not to use the gyro. Our professor even mentioned them not working very well in some kits (the kits are reused, so all our parts had some wear on them or didn't function as well). Our next design was to use the touch sensor from before, placed on the front next to the claw, but use an ultrasonic sensor on the left side of the robot to scan the wall. The ultrasonic sensor allowed us to turn left whenever there was an opening in the wall, and after some trial and error we found if the distance was less than 50 we wouldn't turn, else we would. Then we added the color sensor (the block very close to the ground in the photo) which allowed us to recognize when we were in a pick up/drop off zone. To summarize, we had 1 touch sensor, 1 ultrasonic sensor, and 1 color sensor by the end of our navigation development. How they worked together was as follows; The robot starts up, moves forward for a few seconds, and then stops and uses the ultrasonic sensor to check if there's an opening to our left. If there is an opening to our left, we turn 90 degrees then continue forward with the same commands as before. If there isn't an opening to our left, then we drive forward again for a few seconds and repeat the same steps. Once we made it to the pick up zone, we were able to activate remote control of the robot and manually drive it over to the person and pick them up. Once we left the colored zone the robot automatically takes back control and navigates until it hit the next color, which was drop off. We again take control, lower the claw, and drop them off. Then we drive off and let the robot navigate all the way back to where we started.                          

## Tech stack
**Software**
- MATLAB: Programming and robot control
- MATLAB: Support Package for LEGO MINDSTORMS EV3

**Hardware**
- EV3 compatible robotics kit (RobotShop)
- EV3 programmable brick
- Sensors: touch, color, ultrasonic
- Motors: 2 drive + 1 claw motor

<img width="776" height="582" alt="b1edd723-475e-4767-a233-baff46d83515" src="https://github.com/user-attachments/assets/bfa6e44c-5d4d-4c7c-91fd-6c7fc96158f7" />

