Quest
+++++

Send the player on a quest. Complete any number of quests and get rewards! This relies 
heavily on Scriptable Objects to create a flexible quest system. Each quest will retain its state, 
and each quest does not have to be completed in the level where it was accepted. Thus, you can easily 
design quests that can span across multiple game levels.

QuestInventorySO
================

This Scriptable Object will create quest objects - QuestSO - and will store them in a list where you 
can modify them in the inspector. To create a new QuestSO, simply name it and press the Create New Quest 
button. The new QuestSO will be placed in the AssetsFolder/Quests/QuestSO folder. If you want to delete them,
you must do so manually.

To create a QuestInventorySO, right click in the project window and go to Create/FlareEngine/QuestInventorySO.

QuestSO
=======

This object is in charge of storing all the quest information. Press the add button to add as many rewards 
as necessary. Press the delete button to delete the saved data.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Title
     - The name of the quest. This name must be unique across the entire game. Press the reload button if the name has
       been changed to update the asset name as well.
     
   * - Goal
     - The number of things the player has to accomplish. This can be one or greater. For example, the player can be tasked 
       with collecting three rare gems. 

   * - Icon
     - The quest's icon. This sprite will be displayed in QuestUI.

   * - Description
     - Describe the requirements of the quest. This will be displayed in QuestUI.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Quest rewards.

   * - Name
     - The name of the reward.
     
   * - Reward
     - The value of the reward. 

   * - World Float SO
     - Set the reference to the world float that will have its value incremented by the reward value once the quest has been completed. 
       This can be left empty if not required.

   * - Inventory Item
     - Set the reference to InventorySO and ItemSO. Once the quest has been completed, the inventory will have the specified item appended. 
       This can be left empty if not required.

Quest
=====

This component exists in the scene. It has two jobs. It will activate a quest if the 
user accepts the quest. In this case, place it on an npc or an object that can trigger
the accept method. And, it will check for progression of the quest, in which case place it 
on an item that needs to be collected or an enemy that needs to be destroyed. These objects
will need to trigger the progression method.

If the quest component has a 2D collider set to "Is Trigger" and the player 
has the PickUpItems component, the quest item can be automatically accepted by the player.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     -

   * - Quest SO
     - Choose the quest that needs to be activated.
     
   * - Quest UI
     - The reference to QuestUI, which will display quest information. This is optional.

   * - Add To Journal
     - If the item is found, it will be added to the specified journal if it exists in the scene.
     
   * - OnQuestAccepted
     - The Unity Event invoked when the quest has been accepted.

   * - OnQuestCompleted
     - The Unity Event invoked when the quest has been completed.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Methods

   * - OpenQuestWindow()
     - If QuestUI exists, it will be opened.
     
   * - AcceptQuest()
     - Call this method to accept the quest. This will invoke OnQuestAccepted, and the quest will be considered active.

   * - ProgressQuest()
     - Call this method to progress the quest. For example, if the player is tasked with collecting three coins, then 
       each coin should call this method when it's collected. Each time this method is called, it will increment the quest towards the goal, 
       and once it's of equal value to the goal, the quest will complete. This will invoke OnQuestCompleted.

QuestUIAccepted
===============

This UI class will display the quest title, description, and the rewards. All the UI are optional, just drag and drop the necessary 
UI references. The style and design of the UI is completely up to you.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Title
     - The TextMeshPro displaying the name of the quest.
     
   * - Description
     - The TextMeshPro displaying the description of the quest.

   * - Rewards
     - This takes an icon, name, reward value, and description

QuestUIAccepted
===============

This works in similar fashion to QuestUIAccepted. This UI class will display the quest title and a message once the quest is completed. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Title
     - The TextMeshPro displaying the name of the quest.
     
   * - Exit Button
     - Once this button is pressed, the UI window will close.

   * - Time Out
     - If no button exists, the UI window will close automatically after the time out period.