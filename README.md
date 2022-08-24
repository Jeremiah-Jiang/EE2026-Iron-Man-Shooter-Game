# EE2026-Iron-Man-Shooter-Game
Iron Man Game created for EE2026 Open Ended Project. Coded using Verilog.

Below is a video of the game in action.

https://user-images.githubusercontent.com/83870099/186472925-6adf1009-3323-4e17-a3bb-e9ca593a717c.MOV

## Character Sprites
The sprites were created by first using Microsoft Excel to draw the character for reference, then translating the referenced drawing to code by using array indexing and color coding each individual cell with a certain RGB value. The OLED screen is essentially a 2D array, so each character has a reference point, and the sprite is drawn from that reference point. Movement can be performed by translating this reference point.

## Player Actions
### Movement
- Performed using the Up-Down-Left-Right Buttons on the Basys3 FPGA board
### Attacks
- Regular attacks are performed by speaking at a normal volume into the microphone. Saying 'PEW' works great.
- Player can invoke the Ultimate ability if they have killed at least 5 enemies since the last time the ability was used, and if they shout into the mic.
  - The Ultimate ability instantly destroys all non-boss enemies on screen.

## UI (Not shown in video)
### First 7 Segment LED (AN3)
- Displays player health (maximum of 3). Player loses health is an enemy touches Iron Man, or if the enemy reaches the other side of the screen before it is destroyed.
### Second 7 Segment LED (AN2)
- Displays the kill count (maximum of 5). Refreshes when player performs the Ultimate Ability.
### Third 7 Segment LED (AN1)
- Displays a dash, does not indicate anything.
### Fourth 7 Segment LED (AN0)
- Displays the volume intensity (L,M,H). 
  - If AN0 displays L, Iron Man will shoot regular lasers, otherwise, he will perform the Ultimate ability if he has fulfilled the conditions.


## Enemy behaviour
The enemy is modelled after Ultron and Thanos and there are 4 stages. Drones will gradually increase in speed as Iron Man destroys more of them.
### First stage
- A single ultron drone spawns periodically, Iron Man loses 1 health if a drone touches him. When a certain number of drones are killed, the second stage occurs.

### Second stage
- More drones will spawn.

### Third stage
- Ultron will occasionally take over one of the drones, indicated by the drone's eye and booster colors turning red. Ultron moves significantly faster than regular drones. After a certain number of kills, the final stage occurs.

### Boss fight
- Iron Man regains full health and his Ultimate ability is disabled.
- Thanos will never move towards Iron Man, instead, he will use the powers of the Infinity Gauntlet to fight.
- Thanos will always move up and down to try and hit Iron Man with his lasers.
- Thanos will occasionally use his own Ultimate ability, indicated by him flashing blue to signal his use of the Space Stone.
  - When Thanos flashes blue, this is an indication that he is about to teleport. After a short delay, he teleports to Iron Man's last vertical position.
  - Immediately after teleporting, Thanos flashes purple and he uses the Power Stone, becoming invulnerable and firing a beam directly in front of him. Being caught in the hitbox deals 1 damage instantly, and staying inside the hitbox too long instantly kills Iron Man.
- Game ends when either Iron Man or Thanos is defeated. After victory/defeat screen is displayed, player can press the Down button to restart the game.




