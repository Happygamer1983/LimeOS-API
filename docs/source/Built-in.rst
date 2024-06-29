Built-in API
============
These are functions that dont need to be loaded with *loadlib()*.
----

.. code-block:: luau  

  instance Lime.CreateWindow(name:string, icon:number)

This function creates an returns an app, the icon is not needed for this function
----

.. code-block:: luau  

  instance Lime.CreateUI(parent:instance, name:string) 

This function creates an UI obj and places it inside a specified parent, and then returns it
----

.. code-block:: luau  

  table Lime.GetService(name:string)

This function returns a Roblox service
----

.. code-block:: luau  

  table Lime.Encryption(ModuleVersion:string)

This function returns either the normal encryption module or an AES module *(WIP ATM)*, if you leave ModuleVersion blank it defaults to the normal encryption module
----

.. code-block:: luau

  table loadlib(name:string)

This function loads and retuns a LimeOS module
----

.. code-block:: luau

  nil print()

This function prints output to the Script Editor console
----

.. code-block:: luau

  nil log()

This function prints to the normal Roblox console
