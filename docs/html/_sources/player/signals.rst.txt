Signals
+++++++
.. complete!
During the life cycle of a character, the system, through the use of abilities and nodes, will
set the signals below to true or false. For example, if a character is moving to the right, the system
will read the character's velocity and set velXRight *true* if the velocity in the x direction is positive. 

If using Sprite Engine, these signals are automatically read to control the animation state. There is no need 
to worry about anything else. 

If you are not using Sprite Engine, then you can access the signals below through Character, which is the base class 
for player and AI. Use **Character.signals.signals** using namespace TwoBitMachines.FlareEngine. The signals 
class is a dictionary with a key-value pair of string and bool. Don't forget to reset these signals to false 
each frame or they will remain true.

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
* alwaysTrue
* alwaysFalse

