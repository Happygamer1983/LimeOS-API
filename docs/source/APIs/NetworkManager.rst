==========
NetworkManager
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

With this module you can talk to other connected LimeOS systems and send data between them. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Networking Functions
--------------------

NetConnect
~~~~~~~~~~

.. code-block:: luau  

   NetworkManager.NetConnect(CustomIP:string) -> nil

Connects the system to the LimeOS Network. :raw-html:`<br />`
``CustomIP`` A value for an custom IP. :raw-html:`<br />`
``┗━>`` If an IP is provided, it will use that IP. :raw-html:`<br />`
``┗━>`` If nothing is provided, it will generate you a IP if you dont already have one. :raw-html:`<br />`



NetDisconnect
~~~~~~~~~~~~~

.. code-block:: luau  

   NetworkManager.NetDisconnect() -> nil

Disconnect the system from the LimeOS Network.


Post
~~~~

.. code-block:: luau  

   NetworkManager.Post(ToIP:string, Port:string Data:any) -> nil

Sends data to an IP on a port. :raw-html:`<br />`
``ToIP`` The IP you want to send data to. :raw-html:`<br />`
``Port`` The Port you want to send the data too. :raw-html:`<br />`
``Data`` The data you want to send, can be anything exept instances. :raw-html:`<br />`


Receive
~~~~~~~

.. code-block:: luau  

   NetworkManager.Receive(Port:string, callback:function) -> function

Calls a connected function if any data is received on a specified Port. :raw-html:`<br />`
``Port`` The port you want to listen on for data. :raw-html:`<br />`
``callback`` The function you want the NetworkManager to call once you receive data. :raw-html:`<br />`





Config Functions
----------------

NetStatus
~~~~~~~~~~~~~

.. code-block:: luau  

   NetworkManager.NetStatus() -> bool

Returns the connection status of the system. :raw-html:`<br />`
``true`` The system is connected. :raw-html:`<br />`
``false`` The system is not connected. :raw-html:`<br />`


GetIP
~~~~~~~~~~~~~

.. code-block:: luau  

   NetworkManager.GetIP() -> bool

Returns the IP the system is connected with. :raw-html:`<br />`


ToggleStaticIP
~~~~~~~~~~~~~

.. code-block:: luau  

   NetworkManager.ToggleStaticIP() -> bool

Toggels if you want a static or dynamic IP. :raw-html:`<br />`

