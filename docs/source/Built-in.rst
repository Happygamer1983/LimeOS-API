============
Built-in API
============
These are functions that dont need to be loaded with ``loadlib()``.

.. role:: raw-html(raw)
    :format: html

----

.. code-block:: luau  

  Lime.CreateWindow(name:string, icon:number) -> instance

Creates and returns a new application Window :raw-html:`<br />`
``name: The name of your application`` :raw-html:`<br />`
``icon: An optional icon ID for your application`` :raw-html:`<br />`

----

.. code-block:: luau  

  Lime.CreateUI(parent:instance, name:string) -> instance

Creates and returns a new UI object, placing it inside the specified parent instance. :raw-html:`<br />`
``parent: The parent instance of your ui element`` :raw-html:`<br />`
``name: What ui element you want to create (eg. TextLable)`` :raw-html:`<br />`

----

.. code-block:: luau  

  Lime.GetService(name:string) -> table

Returns a Roblox service by its name. :raw-html:`<br />`
``name: The name of the Roblox Service you want to get`` :raw-html:`<br />`

----

.. code-block:: luau  

  Lime.Encryption(ModuleVersion:string) -> table

Returns an encryption module and its functions. :raw-html:`<br />`
``ModuleVersion: An optional flag, which encryption module should be returned`` :raw-html:`<br />`
``--> If "AES" is provided, it returns an AES encryption module`` :raw-html:`<br />`
``--> If nothing is provided it returns the standart LimeOS encryption module`` :raw-html:`<br />`

----

.. code-block:: luau

  loadlib(name:string) -> table

Returns a LimeOS module and its functions :raw-html:`<br />`
``name: The name of the LimeOS module you want to get`` :raw-html:`<br />`

----

.. code-block:: luau

  print() -> nil

Prints output to the Script Editor console.

----

.. code-block:: luau

  log() -> nil

Logs output to the Roblox console.
