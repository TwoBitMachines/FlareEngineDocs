Transform Tracker
+++++++++++++++++

This class is in charge of holding a list of transforms. This list can be saved. 
One convenient aspect of this class is that you don't have to worry 
about creating a unique ID name for each transform. This can be useful for saving a list of all the 
killed enemies in the level. If this is the case, use the Reset AI node and check 
if the enemy's transform is in this list. 

To set this up, place this component on an empty gameobject. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Key 
     - The key name used for saving purposes. This name must be unique.
 
   * - AddToList (Transform transform)
     - Add a transform to this list

   * - AddToList (ImpactPacket impact)
     - Add a transform to this list using ImpactPacket.

   * - Save()
     - Call this method to save the current transforms in the list. 
       Resetting the game will clear any unsaved transforms.