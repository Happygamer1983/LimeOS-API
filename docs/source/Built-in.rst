============
Built-in API
============
These are functions that dont need to be loaded with ``loadlib()``.

----

.. code-block:: luau  

  Lime.CreateWindow(name:string, icon:number) -> instance

Creates and returns a new application Window
``name: The name of your application``
``icon: An optional icon ID for your application``

----

.. code-block:: luau  

  Lime.CreateUI(parent:instance, name:string) -> instance

Creates and returns a new UI object, placing it inside the specified parent instance.
``parent: The parent instance of your ui element``
``name: What ui element you want to create (eg. TextLable)``

----

.. code-block:: luau  

  Lime.GetService(name:string) -> table

Returns a Roblox service by its name.
``name: The name of the Roblox Service you want to get``

----

.. code-block:: luau  

  Lime.Encryption(ModuleVersion:string) -> table

Returns an encryption module and its functions.
``ModuleVersion: An optional flag, which encryption module should be returned``
``--> If "AES" is provided, it returns an AES encryption module``
``--> If nothing is provided it returns the standart LimeOS encryption module``

----

.. code-block:: luau

  loadlib(name:string) -> table

Returns a LimeOS module and its functions
``name: The name of the LimeOS module you want to get``

----

.. code-block:: luau

  print() -> nil

Prints output to the Script Editor console.

----

.. code-block:: luau

  log() -> nil

Logs output to the Roblox console.
