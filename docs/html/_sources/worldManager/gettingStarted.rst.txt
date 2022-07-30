Introduction
++++++++++++

Welcome! This is the documentation for Flare Engine. This tool provides an array of tools for creating
2d platformers much quicker and efficiently, all without touching a line of code! It comes equipped 
with a streamlined user interface that makes the editor easy to work with. This will allow you to 
quickly get you on your way and start creating your game!

If you are reading the pdf version, please feel free to go the docs website for a more readable experience.
If you have any questions or feedback, please feel free to contact us at TwoBitMachinesDev@gmail.com.

The Basics, Getting Started
===========================

At its core, like most custom implementations, the system uses raycasts. These raycasts will emit from 
the characters and detect the world, bypassing the physics engine. This will allow the user to have greater 
control over the game world. To get this foundation setup properly, each scene **must** contain a **World Manager**
gameobject. Once this component is in the scene, it will automatically install the following Layers and Tags
(if they don't already exist) to ensure smooth operation of the system:

**Layers**
* **World** - Ground, slopes, walls, ceilings. Use this layer on any gameobject that is a solid surface.
* **Platform** - Use this layer on any gameobject that is a Moving Platform.
* **Player** - Use this layer on the player gameobject.
* **Enemy** - Use this layer on any enemy gameobject.

**Tags**
* **Friction** - Use this tag on any ground gameobject that is using the Friction component.
* **NoClimb** - If the player can climb walls, use this tag on any wall gameobject that is *not* meant to be climbable.

And that's basically it. That's all you need to get started. From here you can add a player, choose its abilities,
design AI enemies, setup common systems such as Inventory or Dialogue, and implement world interactables to spice up your game.