Walk
++++

Allow the player to move in the x direction. This ability is enabled by default.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
     
   * - Speed
     - The speed of the player in the x direction.

   * - Smooth
     - A smoothing effect is applied to the speed every time the player starts or stops moving in the x direction. 
       A value of one means there is no smoothing.

   * - Damp Air Change
     - The resistance towards changing direction while the player is in the air.
       A value of zero means the player can instantly change direction in the air.

   * - Infinite Walk
     - If enabled, the character will walk infinitely and change direction upon wall contact. To enter this state, 
       specify the button or call InfiniteWalkActivate (bool value). You can also disable this ability by calling InfiniteWalkAbility (bool value).
       These methods are found on the Player component.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Run
     - If enabled, this will boost the Speed value, and the running signal will be set true.

   * - Type
     - If Button is enabled, the user has to hold a button to run. If Time Threshold is enabled, the player has
       to walk on the ground for a specified time uninterrupted before starting to run. If Double Tap is enabled, 
       the user must double tap the run button within the tap threshold time to start running, and the player will stop running 
       once the button is released. If Button Is LeftRight is enabled, it means the button is mapped to the left and right input,
       and this will prevent entering the run state if the player direction is simply being changed.

   * - Speed Boost
     - Speed will be multiplied by Boost while the player is running.

   * - Jump Boost
     - This will boost the jump force if the player is running.

   * - Ease Into Run
     - If enabled, the player will ease into the running speed instead of accelerating instantly. Specify the duration of the ease time.

.. list-table::
   :widths: 25 100
   :header-rows: 1
   
   * - Ground Hit
     - The Unity Event invoked when the player initially hits the ground. Call a World Effect with the dynamic Activate method.

   * - Not On Ground
     - The Unity Event invoked when the player initially leaves the ground. Call a World Effect with the dynamic Activate method.

   * - Walking On Ground
     - The Unity Event invoked when the player is walking/running on ground. Call a World Effect with the dynamic Activate method.

   * - On Direction Changed
     - The Unity Event invoked when the player changes direction on the x-axis. Call a World Effect with the dynamic Activate method.

**Signals: running**

