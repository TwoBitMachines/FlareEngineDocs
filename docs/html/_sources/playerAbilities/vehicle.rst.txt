Vehicle
+++++++

This ability behaves like a generic vehicle, allowing the main player to ride it. Even though this ability belongs to the Player class, this ability 
should be seen as belonging to an NPC. The vehicle will remain idle with its inputs deactivated until the main player mounts it. Once the main 
player mounts the vehicle, the main player's inputs will be blocked and the vehicle's inputs will become activated. The onVehicle animation signal 
will also be enabled for the main player to use.

Since the vehicle belongs to the Player class, it can make use of all the abilities in this class. Typically, this ability should be set 
to the highest priority. By default, it will coexist automatically with all other abilities.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
 
   * - Passenger Position
     - The position of the main player relative to the vehicle while riding it.

   * - Mount Time
     - The duration for which the vehicleMounted signal is set true to play a mounting animation.

   * - On Mount
     - The Unity Event invoked when the vehicle is mounted.

**Signals: vehicleMounted, onVehicle**