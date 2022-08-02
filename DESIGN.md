TYPING TERROR - DESIGN

Synopsis

I decided to create Typing Terror using Unity because I have used Unity and C# in the past to create a different game, and this was the perfect opportunity to brush up on some skills I learned a few years back. I also really enjoy game design, so I thought I would have a ton of fun with this project.


MAIN MENU

The Main Menu layout is fairly simple. There are four objects: Main Camera, Canvas, EventSystem, and BackgroundMusic.
    The Main Camera is simply the window that players will be able to see when they play the game, giving you the ability to place everything you would like in the game view precisely
    The Canvas is another designated window on which UI elements can be painted onto. In this case, the Canvas has three elements: the background image, the title, and the three buttons located under the Main Menu object.
    The EventSystem works with the Canvas to detect interactions with the UI, such as buttons and clicks.
    The BackgroundMusic object simply used to play the background music in the scene.
There is also a script called "MainMenu" attached to the Main Menu object. In this script, the methods declared are attached to each button individually via the Inspector tab. Buttons have a built in method called "OnClick ()" which allows for you to execute a method in your own script only if the button is clicked.


HOW TO PLAY

The How to Play scene is even simpler, with the same exact objects and only one button, which is the Back button. This button is attached to the same Main Menu script in order for it to take you back to the Main Menu scene when it is clicked. Also in this scene is a text element attached to the canvas that details how to play the game with simple instructions.


GAME

The Game scene is much more complex with a few more objects but many more scripts involved for the word typing mechanics. This scene has the same objects as the previous scenes, with the addition of a score UI element, a sound for the house and boulders exploding, and three copies of the house object. The collision between the house and the boulder is detected in the House.cs script using Box Collider 2D components in both the house objects and boulder/word objects. The reason why the boulders do not appear in the object hierarchy is because they only spawn once the game begins.

Word-related Scripts (the code for these scripts were accessed froma tutorial at https://www.youtube.com/watch?v=HvMrOoUeqO0&t=664s&ab_channel=Brackeys):

WordManager - main word script with the role of instantiating new words on the screen, keeping track of what words are being typed by the player, and checking how many lives the player has left until it has to transition to the EndScene

WordGenerator - contains the array of words that have a chance of spawning on the boulders, and also contains the method for choosing a word at random to spawn in

WordInput - responsible for checking whether the each letter in the game scene is typed and executing the TypeLetter() method from WordManager

WordSpawner - spawns the physical boulders with the words written on them at random x positions and the same y position

WordDisplay - takes care of accessing the Canvas UI elements to spawn the boulder sprite in or destroying it once the word is typed

Word - deals with individual words and making sure that other scripts can access the indices of each word/letter

WordTimer - ensures that words spawn with a delay in between each spawn, with the delay becoming shorter and shorter after each word typed

Score/Visual Scripts:

House - displays an explosion animation when a house is destroyed and plays the explosion sound, as well as takes care of removing the house from the screen

ScoreManager - displays the score in the Canvas UI element, and it is based on a score counter that is accessed from WordManager


ENDSCENE

This scene is also fairly straightforward, and bares many similarities to the main menu. However, this scene also displays the player's final score, which is done with the EndScore script. It accesses the score from WordManager and displays it the same way the score was displayed in the game scene.

The Play Again button is controlled using a separate script that changes the scene to the game scene if clicked. The Quit button is the same as how it was in the main menu.