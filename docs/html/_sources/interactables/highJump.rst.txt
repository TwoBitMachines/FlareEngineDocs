High Jump
++++++++++

This will launch a character into the air effortlessly. This component has
two modes available, Trampoline and Wind, that can be added to an empty gameobject.
Once added, a blue rectangle gizmo will appear for character detection, and 
you can modify the rectangle's size to your preference. Trampoline mode has a 
smaller collider area, while Wind mode has a larger collider area.

.. image:: ../images/interactables/TrampolineGif.gif
   :align: center
   :width: 100%
   
|

.. important::
   High Jump must be enabled as a player ability. There is also a High Jump node for AI.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Type 
     - Launch the character with Trampoline, or gradually push the character upward with Wind.

   * - Force  
     - The amount of force acting on the character.  Trampolines typically have forces above 20, 
       while wind has forces above 5. The force of the High Jump can be applied in any direction 
       based on the gameobject's rotation, whereas the direction of the wind must be specified.

   * - On Trampoline
     - The Unity Event invoked when a trampoline jump is triggered. Call a World Effect with the dynamic 
       Activate method.