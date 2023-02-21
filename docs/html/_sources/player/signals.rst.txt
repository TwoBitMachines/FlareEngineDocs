Signals
+++++++

During the life cycle of a character, the system, through the use of abilities and nodes, will
set the signals below to true or false. For example, if a character is moving to the right, the system
will read the character's velocity and set velXRight signal *true* if the velocity in the x direction is positive. 

If using Sprite Engine, these signals are automatically read to control the animation state. There is no need 
to worry about anything else. 

If you are not using Sprite Engine, you can use Sprite Engine UA as an alternative to use the functionality of 
Sprite Engine with unity animations. Or you can access the signals below through Character, which is the base class 
for the Player and AI. You will need to use **Character.signals.signals** and include the namespace TwoBitMachines.FlareEngine. 
The signals class is a dictionary with a key-value pair of string and bool. Don't forget to reset these signals to false 
each frame or they will remain true. It can look something like this:

.. code-block:: c#
    
   using System.Collections.Generic;
   using TwoBitMachines.FlareEngine;
   using UnityEngine;

   public class YourClass: MonoBehaviour
   {
        // set the player reference
        public Character character; 
        private Dictionary<string, bool> signals = new Dictionary<string, bool> ( );

        // list of your variables
        public bool variable1; 
        public bool variable2;

        private void Awake ( )
        {
                signals = character.signals.signals;
        }

        // flare will set all the character signals during Update, so you can use LateUpdate
        // or rename this method and call it manually
        public void LateUpdate ( )
        {
                // map the signals
                // you have to make sure these signals exist or you will get an error
                // variable1 = signals["velXRight"]; -- this can give you an error
                // variable2 = signals["climb"];

                // so do it like this instead
                // the out bool can be named whatever you want
                if (signals.TryGetValue ("velXRight", out bool velXRight)) variable1 = velXRight; 
                if (signals.TryGetValue ("climb", out bool climbWall)) variable2 = climbWall;

                // clear list;
                signals.Clear ( ); 
        }
   }

------------

* velX
* velXLeft
* velXRight
* velXZero
* velY
* velYUp
* velYDown
* velYZero
* onGround
* jumping
* airJump
* airGlide
* highJump
* windJump
* running
* hover
* ladderClimb
* ceilingClimb
* crouch
* crouchSlide
* crouchWalk
* friction
* sliding
* autoGround
* dashing
* dashX
* dashY
* dashDiagonal
* pushBack
* pushBackLeft
* pushBackRight
* pushBlock
* pullBlock
* pickAndThrowBlock
* pickingUpBlock
* holdingBlock
* throwingBlock
* rope
* inWater
* swimming
* floating
* wall
* wallLeft
* wallRight
* wallClimb
* wallHold
* wallSlide
* wallHang
* wallSlideJump
* wallCornerGrab
* slopeSlide
* slopeSlideAuto
* recoil
* recoilLeft
* recoilRight
* recoilUp
* recoilDown
* recoilShake
* recoilSlide
* mouseDirectionLeft
* mouseDirectionRight
* meleeCombo
* zipline
* vehicleMounted
* onVehicle
* alwaysTrue
* alwaysFalse

