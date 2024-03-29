Crouch
++++++

Let the player crouch and crawl. This will modify the size of the BoxCollider2D.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button
     - If pressed, the player will crouch.

   * - Crouch Height
     - The new height of the player. This will modify the vertical size of the BoxCollider2D.

   * - Crawl
     - If enabled, the player will be able to crawl. Set the scale applied to the player's x speed
       and the maximum speed the player can have while crawling.

   * - Jump
     - If enabled, the player will be able to jump while crouching and crawling. Specify how much to scale the jump force. 

   * - High Jump
     - If enabled, the player will perform a high jump from the crouch state. 

   * - Jump Boost
     - The player's jump force will be multiplied by this number during the High Jump.

   * - Charge Time
     - The total crouch time that has to elapse before triggering a High Jump. The player's x velocity will have to be zero during this time.

   * - On High Jump
     - The Unity Event invoked when a High Jump executes.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - On Crouch
     - The Unity Event invoked when the player crouches.
 
   * - On Exit
     - The Unity Event invoked when the player stands up.
 