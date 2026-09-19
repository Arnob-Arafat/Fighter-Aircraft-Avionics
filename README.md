# **Fighter Aircraft Avionics** 

## Project Overview 

Automated Aircraft avionics where the aircraft can make decisions on its own using basic logic. The altitude control, weapons lock, weapons engage and defense capabilities are  controlled by predetermined functions of the simulated aircraft. 

There are four distinct modules of this project as shown in the project diagram. 

1. **Autopilot :** Target Y Coordinates are inputted(in a register)  and the simulated “aircraft” adjusts its current altitude(in a up/down counter)  with respect to the target.  Say, Yt = Target Altitude and Yc = Current Altitude 

When Yt  > Yc , Yc ++ → upcount per clock edge When Yt  < Yc , Yc - - → downcount per clock edge When Yt  < Yc , hold → no change 

Current X coordinates of the aircraft are increasing per clock edge (every 100 seconds). 

2. **Weapons Lock :** Any simulated target position(X, Y) is inputted(in a register) and the distance between the current position of aircraft and target will be measured and compared against previously inputted range of the aircraft. If the target is in range then the system will  “lock” the target(simulated through red or green LEDS) and allow us to fire (missile/bullets). 

3. **Weapons Engage:** If the target is “locked” then we can toggle either missiles or bullets to engage in combat. We have a limited number of missiles or bullets. Therefore after depleting ammunition we cannot engage in combat. 

4. **Defense:** Any simulated projectile can be toggled on. We have a limited number of flares (anti projectile ammunition). Therefore whenever the projectile is detected on the radar we will get warning. There are two stages of warning. When projectile distance is 7 the radar will light up and at 3 emergency led will turn on.  The projectile can be engaged with whenever it crosses the radar line. But once flares have been depleted we cannot defend against projectiles hence when the projectile hits the aircraft, the simulation stops. 

Explanation of how theoretical components covered in the course were applied in the project 

- **Register** : 

4-bit registers are used to store the target altitude and enemy X and Y coordinates. 8-bit registers are used to store the squared coordinate differences. 

- **Counter:** 

74193 Up/Down Counters are used to maintain the current altitude. Downcounters are used for missiles, bullets, projectile distance, and flares. A counter is also used to increment the aircraft's X coordinate over time. 

- **Comparator:** 

7485 Comparators are used to compare the target altitude with the current altitude and to compare the squared distance with the squared range for the weapon-lock decision. 

##### ● **Adder/Subtractor:** 

7483 Binary Adders with two's-complement logic are used to calculate (x1-x2) and (y1-y2), and to add their squared values to obtain the squared distance. 

- **Square Logic Circuit:** 

AND, OR, and NOT gates are used to calculate (x1-x2)², (y1-y2)², and Range². 

- **MUX:** 

A Multiplexer is used to select between missiles and bullets for weapon engagement. 

- **Logic Gates:** 

AND, OR, and NOT gates are used for altitude mode control, weapon-lock decision, projectile detection, enemy reset, flare control, and system shutdown. 

##### ● **7-Segment Display:** 

7-segment displays are used to show altitude, coordinate, distance, ammunition, projectile, and flare values. 

##### ● **LEDs:** 

LEDs are used to indicate weapon lock, danger zone, emergency zone, flare deployment, and system shutdown. 

##### **● Clock:** 

Clock signals are used to control the altitude counter, X-coordinate incrementing, projectile movement, and other sequential operations. 

#### ● Karnaugh Maps 

Karnaugh Map used to solve equations to find squares of binary numbers. 

## List of Features 

- Altitude is tuned every second. 

- X position of the aircraft keeps increasing every 100 seconds. 

- Finds out if the enemy target is within range of combat. 

- Enable Combat if enemy within range. 

- Lets users choose between missiles or bullets to shoot. 

- Keeps track of missile and bullet count. 

- Defensive capabilities include firing flares against projectiles. 

- Projectiles can be dissolved only when found in radar. 

- Limited amount of flares, missiles and bullets available. 

- If projectile hit or projectile distance becomes zero, system resets i.e. X Y position of aircraft Resetted (MR) to (0,0). 

## User guideline 

#### 1. Autopilot 

a. Set Target Altitude through toggling through  logic toggles. 

b. See real time altitude tuning. 

#### 2. Weapons Lock 

a. Set Enemy Position. 

b. If Range >= Distance between enemy aircraft and user then LED Green will turn on or else LED Red. 

#### 3. Weapons Engage 

a. Choose between Missiles(0) or Bullets(1) to use 

b. Use the Fire button to shoot. 

c. Watch Bullet/Missile Count go down. 

#### 4. Defense 

a. Start Projectile simulation by toggling 0 to 1. 

b. Fire Flares whenever Radar Lights Up. 
