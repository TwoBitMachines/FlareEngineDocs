Dialogue Bubble
+++++++++++++++

This component is similar to Dialogue, an interactive dialogue system,
but instead uses speech bubbles within world space to display conversations
between the player and NPC.

To set up the system, a minimum of two components are required: 
**DialogueBubble**, which stores the dialogue between the characters, and **Bubble**,
which manages the UI elements that will display the dialogue. The DialogueBubble
component can be placed on a relevant or empty game object, while each player and NPC 
should have an individual Bubble game object set as a child. These game objects 
should be deactivated; the system will be in charge of activating them.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
 
   * - Exit Button  
     - If this button exists, the user will be able to escape any dialogue.

   * - Skip Button
     - If this button exists, the user will be able to skip to the next message in the conversation at any time.

   * - Block Inventories
     - If enabled, any inventory trying to open will be blocked from opening.

   * - Block Player Input
     - If enabled, when dialogue is started, the player input will be automatically blocked.

   * - Fade In, Fade Out Times
     - This will dictate how fast the speech bubbles appear and disappear when they are active.

   * - Events
     - The Unity Events invoked when the player begins and exits a conversation.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - BeginConversation()
     - Call this method to begin the conversation. This will also set this gameObject active true.
 
   * - EndConversation()
     - Call this method to end the conversation.

Create any messenger that is relevant to the dialogue.

.. list-table::
   :widths: 25 100
   :header-rows: 1
     
   * - Property
     - 

   * - Messenger Bar
     - Choose the messenger's sprite icon and display name. From here, delete this messenger if necessary, 
       and toggle the box open for more fields.

   * - Bubble
     - Set the Bubble reference that belongs to this messenger.

   * - Choice
     - If this messenger needs to pick between multiple choices, set the reference for each Bubble that 
       will act as a choice bubble.

A dialogue is a series of conversations. Add as many as required. Each conversation will have a series 
of messages. Each message can either be of type Message or Choice. If Choice type is enabled, it should 
be the last message in the conversation because the player will be asked to make a choice, and each option
in the choice will branch into another conversation. The dialogue will end once the current conversation 
reaches the final message that is of type Message.

.. list-table::
   :widths: 25 100
   :header-rows: 1
   
   * - Property
     - 

   * - Conversation Bar
     - This displays the name of the conversation. From here, delete the conversation if necessary, 
       add a new message, or open the box for more fields.

   * - Message Bar
     - This displays the messenger's icon. Choose which messenger is talking and the type of message.

   * - Message To
     - If the speech bubbles are directional, specify who the message is being delivered to so the system 
       can know how to flip the speech bubble.

   * - On Message Complete
     - The Unity Event invoked after the message is finished loading.

   * - Message Type
     - If enabled, a standard message will be displayed. Type the desired message in the text box.
   
   * - Choice Type
     - If enabled, press the add button to create a series of options for the player to choose from. 
       Each option will have a white button on the left; toggle this button for extra settings and to
       choose which conversation to branch to.

.. note:: 
   When dialogue is started, the first conversation in the list will be the entry point.

Bubble
======

The Bubble component displays the text and changes the size of the UI image, typically the 
speech bubble, to fit around the text. Thus this component should exist on a Canvas gameObject that
is a child of the messenger (player or NPC). If a TextMeshProEffects component exists, it will 
use the typewriting effect to type the text on the screen.

If the player has to make choices, then a separate speech bubble should be created for each choice
required. These speech bubbles should then be referenced in the DialogueBubble component.

Place the speech bubble exactly where you want it to appear in the y direction. The system will override 
the x position. Please refer to the tidbit scene for an example of speech bubbles.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - References
     - 
   * - Text Mesh 
     - The reference to the textMeshPro used for displaying text.

   * - Image  
     - The reference to the speech bubble image.

   * - Is Directional
     - If enabled, the speech bubble will be flipped to face the other messenger.

   * - Size
     - Set the minimum and maximum size the speech bubble can ever be changed to.

   * - Padding 
     - The space between the text and the border of the speech bubble.

   * - Text Offset Y
     - The displacement of the text in the y direction.

   * - Bubble Offset X
     - The displacement between the messenger and the speech bubble in the x direction.

   * - Events
     - The Unity Events invoked when the speech bubble transitions in and transitions out into the scene, and when it loads its text.

