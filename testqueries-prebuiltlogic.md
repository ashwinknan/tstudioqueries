## Query ID - PB0001

### Category
Prebuilt Logic

### Query Text
How can I kill a player when he clicks on a stone object in the screen? 

### Expected Answer
You need to use the `Kill Player` pre-built logic template. 
1. Select the stone asset
2. Goto `Logic` tab on the Quick Access Menu and under `Mechanics` select the `Kill Player` logic
3. Drag and drop the `Kill Player` pre-built logic to the stone asset
4. Customize the following parameters of the `Kill Player` logic in the Inspector Panel: 

    1. `Kill Player on` - Select "Mouse Click"
    2. `Player Animation` - Select the player animation to play when the player gets killed 
    3. `Kill Delay` - This will introduce a delay between the click and the player getting killed. Make this zero, if you want instant kill 
    4. `Respawn Type` - This defines the movement to the last checkpoint. You can select one of two options from this dropdown - "lerp" or "instant"
    5. `Lerp time` - You can specify the number of seconds it must take to lerp from the kill spot to the previous checkpoint. Applicable only if you selected "lerp" for `Respawn Type`

### Difficulty
Easy

### Keywords/Tags
#killplayer #checkpoint #lerp


## Query ID - PB0002

### Category
Prebuilt Logic

### Query Text
In my game, I want my enemies to move not in a straight line but instead in an L shape continuously. The Move prebuilt logic allows only straight line motion from point A to point B. How can I achieve this? 

### Expected Answer
This functionality can be achieved by using the `Multi-Point Move` move pre-built logic block.
1. Select the enemy asset by clicking on it 
2. Goto `Logic` tab on the Quick Access Menu and select the `Multi-Point Move` logic
    1. `Move On` - Select "Game Start"
    2. `Speed` - Enter a number greater than zero to specify the speed at which the enemies move
    3. `Waypoints` - Click on "Defined Area", it will play the game and you can use the Gizmo to indicate the path
        1. Delete any existing points in the path
        2. Move the enemy to the first point of the L shape.
        3. Click on Add point
        4. Do the same for the vertex of the L and the end point.
        5. Once all points are marked, click, Stop Record. You will be taken back to the editor 
    4. `Loop Type` - Select "Forever" since you want to move continuously
    5. `Pause at Points` - Keep this field empty since we don't need any pause

    The enemy will then move in a straight line between each of the points specified continuously in a loop. 

### Difficulty
Easy

### Keywords/Tags
#movement #multipointmove #path

## Query ID - PB0003

### Category
Prebuilt Logic

### Query Text
How do I move in a curved path using Multipoint Move?  

### Expected Answer
`Multi-Point` move only helps move in straight lines between specified points and cannot generate curved paths. Curved path movement is possible but you need to write your own T# script for that. 

### Difficulty
Easy

### Keywords/Tags
#movement #curvedpath 

## Query ID - PB0004

### Category
Prebuilt Logic

### Query Text
I want to play a VFX on the completion of a certain event (say collection of 10 coins). How do I do that? 

### Expected Answer
Let us assume that you have already setup the generation of a broadcast on the completion of this event. Let's say the name of the broadcast is  `collected10` , which is generated as soon as you collect 10 coins. 

Now, follow these steps: 
1. Select the  `Particles` tab on the Quick Access Menu and choose the VFX you want to play. 
2. Drag and drop your chosen VFX you want to play in the scene near the region where you want the VFX to play. The VFX you dropped will appear in the `Layers` tab of the quick access menu in the bottom along with all the assets you have added in the scene
3. Select the VFX you added from `Layers` - you will notice a `Particle Effect` tab showing up in the `Inspector Panel` on the right with a list of its customizable properties.
4. Adjust the following parameters for the chosen VFX in the inspector Panel: 

`Play On` - Enter "Broadcast Listened"

`Listen To` - Enter "collected10"

`Play Forever` - Set toggle to ON

Your setup is now complete. When you click play - the system will wait for the `collected10` broadcast to be generated. As soon as it is generated, your selected VFX will play forever

### Difficulty
Easy

### Keywords/Tags
#particles #vfx #juice #polish

## Query ID - PB0005

### Category
Prebuilt Logic

### Query Text
I want to play a background score in the game to add to the game experience. This should play at the same level irrespective of where the player is. How can I achieve this? 

### Expected Answer
To play a background score, you need to follow these steps: 
1. Select the  `SFX` tab on the Quick Access Menu and choose the SFX you want to play as a background score.
2. Drag and drop your chosen SFX you want to play in the scene. The SFX you dropped will appear in the `Layers` tab of the quick access menu in the bottom along with all the assets you have added in the scene. 
3. Adjust the following parameters for the chosen background music in the inspector Panel:

`Play On` - Select "Game Start" from the dropdown

`3D Audio` - Select "None" from the dropdown. This ensures that the audio file's level is the same everywhere. 

`Loop` - Turn the toggle ON. This will be needed if the SFX chosen is of a very short duration, so for the background score , you will need to repeat the same SFX on loop to make it sound like a background score. 

This completes the setup of the background score. Your background score will now play right from the beginning of the game. 

### Difficulty
Easy

### Keywords/Tags
#bgm #backgroundscore #sfx #sound

# Query ID - PB0006

## Query Text
I am building a treasure hunt game where the objective is to collect keys.  To ensure these keys are easily identifiable,  I want to make the keys rotate. How do I solve this? 

### Category
Prebuilt Logic

## Expected Answer
You need to make use of the `Rotate` pre-built logic template. Here's how you achieve this: 
1. Goto the `Logic` tab on the Quick Access Menu and scroll to find the `Rotate` pre-built logic. 
2. Drag and drop the `Rotate` logic to the key in the editor. You will notice the Inspector Panel for Rotate show up (if Advanced Mode is turned on)
3. Adjust the following parameters for Rotate logic in the inspector Panel:

`Rotate On` - Select "Game Start"

`Rotation Axis` - Select "Z-Axis"

`Speed` - Enter any number greater than zero to set the rotation speed

`Direction` - Select "Clockwise" (or "Anticlockwise") from the dropdown

Your key is now set up to rotate clockwise about the z-axis with the speed you specified. 

## Difficulty
Easy

## Keywords/Tags
#rotation #rotate

# Query ID - PB0007

## Category
Prebuilt Logic

## Query Text
I want the next level to be loaded only both two events are completed - player has collected all coins and player touches the finish line. I have already set up broadcasts when these events are completed. How do I achieve this?  

## Expected Answer
You need to first ensure that both the events generate a broadcast when they are completed. Let's call `collected_all_coins` the broadcast generated when player has collected all coins and `finish_touch` when the player touches the finish line. 

To ensure new scene load on completion of BOTH games, we'll use the `AND` pre-built logic template in conjunction with the `Load Scene` pre-built logic template. 

1. Select the object with the collider that is corresponding to the finish line in the game
2. From the `Logic` tab in the Quick Access Menu, we need to add the `AND Operator` pre-built logic template and the `Load Scene` pre-built logic template
3. Select the tab for the `AND Operator` in the Inspector Panel. In this: 

    1. The first `Listen For` field must be "Broadcast Listened" with value as  `collected_all_coins`

    2. Click on the + button and add the second condition

    3. The second `Listen For` field must be "Broadcast Listened" with value as  `finish_touch`

    4. Set `Broadcast` as `start_new_level`. This will generate the `start_new_level` broadcast once both `collected_all_coins` and `finish_touch` are generated

4. Now select the tab for the `Load Scene` tab from the Inspector panel.
    1. The field `Load Scene` when must be set to "Broadcast Listened"
    2. The field `Listen To` must be `start_new_level`
    3. `Scenes to Load` - Select the level you want to load next


## Difficulty
Easy

## Keywords/Tags
#loadnewlevel #andoperator #broadcast

# Query ID - PB0008

## Category
Prebuilt Logic

## Query Text
I want to stun a player for 2 seconds, where his movement stops once the player touches an orb in the game. How do I achieve this? 

## Expected Answer
Here is where you use the `Toggle Player Movement` pre-built logic in combination with `Delay` pre-built logic
1. Select the orb asset which you want to use to stun the player
2. From the `Logic` tab in the Quick Access Menu, we need to add the `Toggle Player Movement` logic to the orb by dragging and dropping it on the orb
3. Customize the `Toggle Player Movement` on the inspector panel: 
    1. `Stop Movement On` - Set to "Player Collides"
    2. `Play Stun Animation` - Toggle it to ON state
    3. `Broadcast on Stop` - Enter a value , say `stun`
    4. `Resume Movement On` - Set to "Broadcast Listened"
    5. `Listen to` - Enter a value say `endstun`
4. From the `Logic` tab in the Quick Access Menu, we need to add the `Delay` logic to the orb by dragging and dropping it on the orb:
5. Set the following properties of the `Delay` logic on the inspector panel:
    1. `Delay On`: Set as "Broadcast Listened"
    2. `Listen to`: Enter `stun` 
    3. `Delay Time`: Enter the number 2 to give a 2 second delay
    4. `Broadcast`: Enter `endstun`

This will ensure that the `stun` broadcast creates a delay to inactivate the player for 2 seconds and then the `endstun` broadcast resumes movement giving a 2 second stun effect.  

## Difficulty
Medium 

## Keywords/Tags
#toggleplayer #stun 

Format 
# Query ID - PB0009

## Category
Prebuilt Logic

## Query Text
I want the game to have a count down timer of 125 seconds, and the level should reload from the player's initial spawn point  if the player does not reach the finish line in 125 seconds. 

## Expected Answer
You will need a combination of the `Load Scene` Logic and the `In Game Timer` global logic. 

1. Add an `In Game Timer` from the Main Toolbar. 
2. You will see this timer show up in the `Essentials` tab of the Quick Access Menu
3. Once you click `In Game Timer` from there, you will be shown the customization tab for the timer on the Inspector Panel on the right. Make these changes to the customization panel: 
    1. `Timer Type` - Set as "Count Down"
    2. `Timer` - Enter 125 
    3. `Broadcast` At Timer End - Enter "reload_level" 
4. Add the `Load Scene` logic to any empty object in the scene. Customize it as follows
    1. `Load Scene when` - Set as "Broadcast Listened"
    2. `Listen to` - Set as "reload_level"
    3. `Scenes to Load` - Set as the current scene

This will ensure that the reload_level broadcast is generated as soon as 125 seconds are over and triggers the Scene reload through the Load Scene template. 

## Difficulty
Medium 

## Keywords/Tags
#timer #timedgames 

# Query ID - PB0010

## Category
Prebuilt Logic

## Query Text
I have a fox in a game which initially plays head movement animation but do a jumping animation as soon as the player reaches the checkpoint next to it. How do I do this? 

## Expected Answer
1. Ensure that the asset collider next to the fox has a `Checkpoint` logic added to it. You can find the `Checkpoint` logic in the `Logic` tab of the Quick Access Menu. In the Inspector Panel for this `Checkpoint`, set `BroadcastData` to `change_fox_animation`. 

2. Ensure that the fox asset is an animated asset. Add the `Play Animation` logic from the `Logic` tab on the Quick Access Menu to the fox. In the Inspector Panel for this, make these changes: 
    1. Set the `Default Animation` to the animation corresponding head movement
    2. Click on the + button to add more animations
    3. Set `Start On` to "Broadcast Listened"
    4. Set `Listen to` to "change_fox_animation"
    5. Set `Anim Dropdown` to the jumping animation 

Your desired interaction will now happen

## Difficulty
Easy

## Keywords/Tags
#animation #playanimation #checkpoint




