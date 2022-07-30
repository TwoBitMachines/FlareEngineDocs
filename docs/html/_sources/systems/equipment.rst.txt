Equipment
+++++++++
.. complete
The Equipment class keeps track of all the tools the character has. A tool is simply a child gameobject of a 
character that contains a component that inherits from Tool. This class belongs to the Character class.

As of right now, the only tool the system implements is the Firearm class, but it's possible 
to create more tools as long as the new tool inherits from the Tool class. Call the following methods to 
activate or deactivate tools (firearms).

.. list-table::
   :widths: 75 150
   :header-rows: 1

   * - Method
     - 
   * - ActivateTool (string toolName)
     - Activate this tool.
       
   * - ActivateThisToolOnly (string toolName)
     - Activate this tool and turn off all others.

   * - DeactivateTool (string toolName)
     - Deactivate this tool.

   * - DeactivateAllTools ( )
     - Deactivates all tools.

   * - DeactivateAllToolsExcept (string toolName)
     - Deactivates all tools except this tool.

   * - EquipmentIsActive ( )
     - Returns true if more than one tool is active.

   * - RegisterTool(Tool tool)
     - Register the following tool into the system.

   * - RemoveTool(Tool tool)
     - Remove the following tool from the system.
  
   * - ToggleTool (string toolName)
     - Toggle the active state of this tool.
       
   * - ToggleThisToolOnly (string toolName)
     - Toggle the active state of this tool and turn off all others.
   
   * - ToolIsActive (string toolName)
     - Returns true if this tool is active.

   * - ToggleOrActivateOnly(bool toggleTool, string toolName)
     - If toggleTool is enabled, the activate state of the tool will be toggled. If it's false, the tool will activate and turn off all others.
       This is used by the inventory system.
   
   * - ToggleOrActivate(bool toggleTool, string toolName)
     - If toggleTool is enabled, the activate state of the tool will be toggled. If it's false, the tool will activate. This is used by the inventory system.

   * - ChangeFirearmProjectile (ItemEventData itemEventData)
     - This is called by the inventory system to change the projectile of the first active tool(firearm).
     
   * - ResetAll()
     - Calls the ResetAll method for each tool.