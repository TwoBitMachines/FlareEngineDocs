Journal
+++++++

The **Journal** allows the player to keep track of a list of items and quests, 
with all entries being saved automatically. This is especially useful for quests
as it allows the player to track completion progress.

The Journal is built using UI elements and utilizes the **JournalSlot** game object as a display
template for all items. The structure is customizable based on the desired UI elements. 
Refer to the Journal Scene for an example.

During runtime, the Journal Slot will contain a reference to the corresponding item
or quest and displays relevant information if the associated UI elements exist.
It is important to note that all UI elements are optional.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Name
     - The name of the Journal. This name must be unique.

   * - Save Key
     - Items or quests added to the Journal are saved automatically using a unique save key name.

   * - Activate
     - Toggle the Journal with a button, and pause the game if necessary during this time. Make 
       sure the Journal is a child of the World Manager to toggle properly, otherwise activate the game object manually.

   * - Back, Forward
     - If present, these inputs will navigate the Journal's list of items.
     
   * - Range View
     - Enabling this option sets the maximum number of items visible at once. If the number 
       of items exceeds this limit, they will loop back into view.

   * - Slot Prefab
     - Reference to the game object with the Journal Slot component.

   * - Slot Parent
     - The transform that will serve as the parent of the newly created item.

   * - Slot Highlight
     - The UI image used to highlight the selected item, with optional offset.

   * - Descriptors
     - The Icon, Title, Extra Info, and Description are optional UI references used to display
       data related to the selected item.

   * - Inventory
     - Every item or quest must be present in its corresponding InventorySO or QuestInventorySO
       scriptable object for reference. Place these inventories here.