Dialogue
++++++++
.. complete!
This is an interactive dialogue system for the player and NPCs. Create conversations, add message effects, call Unity Events, and
even include simple animations for complex interactions. All this is accomplished within the inspector window.

The setup requires at least two components: **Dialogue**, where the dialogue between the characters is created and stored,
and **DialogueUI**, which controls the UI elements that will display the dialogue. The Dialogue component will typically
exist on an NPC, an empty gameobject, or wherever it is needed, and the DialogueUI should exist on a canvas element, to properly
reference all the necessary UI elements. If the UI and message need special effects, the **LetsWiggle** component, a tweening library, 
can move and scale UI elements, and the **TextMeshProEffects** can add a typewriting effect, among other effects, to the message.

.. note:: 
   When dialogue is started, player input will be automatically blocked.

------------

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - DialogueUI    
     - The reference to DialogueUI. 
 
   * - Exit Button  
     - If this button exists, the user will be able to escape any dialogue.

   * - Skip Button
     - If this button exists, the user will be able to skip to the next message in the conversation.

   * - Block Inventories
     - If enabled, any inventory trying to open will be blocked from opening.

   * - Position Icon
     - If enabled, the messenger icons will be positioned on the left or right of the message box,
       depending on the relative position of the messengers.

   * - Is Random
     - If enabled, this will display random conversations. If this is desired,
       enable the Is Random flag that also exists in each conversation for any conversation that should be treated as random.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - BeginConversation()
     - Call this method to begin the conversation. This will also set the gameobject active true.
 
   * - EndConversation()
     - Call this method to end the conversation.

------------

Create any messenger that is relevant to the dialogue.

.. list-table::
   :widths: 25 100
   :header-rows: 1
     
   * - Property
     - 

   * - Messenger Bar
     - Choose the messenger's sprite icon and display name. From here, delete this messenger if necessary, 
       and toggle the box open for more fields.

   * - Transform
     - If Position Icon is enabled, specify the transform of the messenger to compare its position relative to the other messengers.

   * - Background
     - This is optional. Choose a personal background image for this messenger. If left null, the default background will be used instead.

   * - Create Animation
     - If applied, the messenger's icon will be replaced by an animation. Name the animation and create it. Create as many as necessary. 
       Once created, each animation will have an add button for adding each individual sprite in the animation.

   * - FPS
     - Frames per second. The rate at which the animation plays.

   * - Loop
     - If this is enabled, the animation will loop.  This could be useful for simple talking animations.

------------

A dialogue is a series of conversations. Create as many as required. Each conversation will have a series of messages. Each message
can either be of type Message or Choice. If type Choice is enabled, it should be the last message in the conversation because the player will
be asked to make a choice, and each option in the choice will branch into another conversation. The dialogue will end once the current conversation 
reaches the final message that is of type Message.

.. list-table::
   :widths: 25 100
   :header-rows: 1
   
   * - Property
     - 

   * - Conversation Bar
     - This displays the name of the conversation. From here, delete the conversation if necessary, add a new message, or open the box for more fields.

   * - Name
     - Conversation name.

   * - Is Random
     - If enabled, this conversation will be treated as a random conversation.

   * - Message Bar
     - This displays the messenger's icon. Choose which messenger is talking and the type of message. From here, delete the message if necessary, or open the box
       for more fields.

   * - Animation
     - If enabled, type the name of the animation that needs to play during the conversation.

   * - Message To
     - If Position Icon is enabled, specify who the message is being delivered to so the system can know how to position the UI icon.

   * - On Message Complete
     - The Unity Event invoked after the message is finished loading.

   * - Message Type
     - If enabled, a standard message will be displayed. Type the desired message in the text box.
   
   * - Choice Type
     - If enabled, press the red button to create a series of options for the player to choose from. Typically, the option response should be as short as possible, since
       the options will be mapped to UI button elements.

   * - Branch To 
     - If the player chooses this option, this will become the next conversation.

   * - On Choice 
     - If the player chooses this option, this will be the Unity Event that is invoked.

.. note:: 
   When dialogue is started, the first conversation in the list will be the entry point.

------------

DialogueUI
==========

The system implements Unity's UI system to display the dialogue box. The UI elements in the dialogue box can be configured to your personal taste. 
The important part is to set the UI references so that the system knows when to enable them and set their content. 

The demo contains a basic UI dialogue structure, which can be used as a starting point for other designs, but in general, the system 
will be looking for five basic elements: an icon image, a background image, a next signal image, a TextMeshPro for the message itself 
and the messenger's name. If any UI elements are missing, the system will simply ignore them. In reality, only one of these is truly 
needed, and that is the message element. Thus the dialogue box can be configured as complex or as simple as necessary.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - References
     - 

   * - Icon  
     - The image of the messenger's avatar (or animation).

   * - Background 
     - The image background for the entire message. This image can be personalized for each messenger in the Dialogue component.
       This UI element should be considered the main component of the dialogue box. All other UI elements should be children to it.

   * - Next Signal
     - The image that will appear once the message has been completely loaded, signaling the user to continue with the conversation. Implement a bouncing effect with LetsWiggle.
  
   * - Message
     - The TextMeshPro of the message.

   * - Messenger Name
     - The TextMeshPro of the messenger's name.

   * - Choices
     - The buttons mapped to a choice in the conversation. Create the required amount. These buttons will be clicked or pressed by the user.

------------

The following Unity Events are optional. If they're not used, the message will load immediately. But if used, they will be able to 
add special effects to any dialogue. It is, however, very important to connect them properly, or the dialogue system will not work correctly. 

The system comes included with two very useful classes that will add effects to the dialogue box. **LetsWiggle** is a tweening library 
that can be used in the inspector to setup tweens, like moving and scaling UI. **TextMeshProEffects** will add special effects, like a typewriting or wobble effect, to a message. It is these 
classes that can be used for OnTransitionIn, OnTransitionOut, and On Load Message. These classes should be placed on the background UI Element.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - On Begin 
     - The Unity Event that is invoked when a dialogue begins.
 
   * - On End
     - The Unity Event that is invoked when a dialogue ends.

   * - On Transition In
     - Invoke this Unity Event when a new message is about to begin. How it's intended to work: This event should call another class, like a tweening library, to move or scale the background image.
       In this case, since it's a transition In, the background image can be scaled from a 0 to 1. Once complete, it is very *important* for this other class to call **TransitionInComplete** in 
       DialogueUI. If this event is used, there should *always* be a return signal to let the system know it can move forward, or else the system will stay stuck.
  
   * - On Transition Out
     - Invoke this Unity Event when a message ends. This works exactly as On Transition In, but in reverse. The important part is for the other class to  call
       **TransitionOutComplete** in DialogueUI once complete.

   * - On Load Message
     - Once a Transition In is complete, this Unity Event will be invoked. Typically you call a class that will add special effects to the message itself. As with the previous two events,
       once the other class is complete, it must return a complete signal by calling **MessageLoadingComplete** in DialogueUI. If it does not, the system will get stuck.
  
.. warning:: 
   If using OnTransitionIn, OnTransitionOut, or OnLoadMessage, it is very important to set the Unity Events properly or the system will get stuck.