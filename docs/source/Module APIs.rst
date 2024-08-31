==========
Module API
==========
To use these modules and the function in them load them ``loadlib()``.

.. role:: raw-html(raw)
    :format: html

----

.. _PermissionsInfo:

FileSystem
==========
The FileSystem module utilizes four distinct permissions: ``R = Read, W = Write, D = Delete, and A = Admin``. :raw-html:`<br />`
Permissions should be formatted correctly, with multiple permissions separated by a hyphen (e.g., "R-W-D"). For single permissions, simply use the corresponding letter (e.g., "R" or "D"). :raw-html:`<br />`
These permissions govern actions such as reading, writing, deleting, and creating file objects. :raw-html:`<br />`


.. code-block:: luau  

    FileSystem.GetPartitions() -> table

Returns a table of all partitions in LimeOS.

----

.. code-block:: luau  

    FileSystem.GetOSDriveLetter() -> string

Returns the partition name where LimeOS is installed on.

----

.. code-block:: luau  

   FileSystem.GetPartitionByIndex(index:number) -> table

Returns a partition based on an index number. :raw-html:`<br />`
``index`` The index number of a partition. (e.g., 2 will always get the 2nd partition) :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetPartitionByName(name:string) -> table

Returns a partition based on a string name. :raw-html:`<br />`
``name`` The name of a partition. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool) -> table

Creates a new partition table and returns it. :raw-html:`<br />`
``name`` The name of the new partition. :raw-html:`<br />`
``PartitionSize`` The partition size in MB for the new partition. :raw-html:`<br />`
``IsOSDrive`` A bool value, that marks if LimeOS is installed on that partition. :raw-html:`<br />`
 **Warning** Do not enter any value for ``IsOSDrive`` :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.DelPartition(partition:string) -> bool

Deletes a partition based on a string name. The function will return ``true`` if the deletion was successful :raw-html:`<br />`
``partition`` The name for the to be deleted partition. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CheckPartitionSize(partition:string, Data:table) -> bool

Retuns ``true`` when there is still space on the partition for the provided data. :raw-html:`<br />`
``partition`` The name for the to be checked partition. :raw-html:`<br />`
``Data`` The partition data. :raw-html:`<br />`

----

.. code-block:: luau  

    FileSystem.GetUserPermissions(user:string) ->  string/table

Returns the permissions of the user. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
 **Warning** Do not enter any value for ``user`` **Warning** :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CheckPermissions(path:string, user:string, permissiontype:string) -> bool

Checks if the user has the same permissions as the provided permissions. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``permissiontype`` The permissions that will be checked for, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`
 **Warning** Do not enter any value for ``user``, only enter ``nil`` as a value :raw-html:`<br />`


----

.. code-block:: luau  

   FileSystem.CalculateObjectSize(path:string) -> number

Returns the KB or MB size of a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.FileExists(path:string) -> bool

Checks if a file object exists based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFile(path:string) -> table

Returns a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFiles(path:string) -> table

Returns the files inside a directory object based on a provided path. :raw-html:`<br />`
``path`` The string path to the directory object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.WriteFile(path:string, data:string, user:string, plaintext:bool) -> bool

Writes new data to a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``data`` The new data for the file. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``plaintext`` A bool value that toggels file encryption, ``true`` turns the encryption off. :raw-html:`<br />`
 **Warning** Do not enter any value for ``user``, only enter ``nil`` as a value, ``plaintext`` is not intened to be used for normal files :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string) -> table

Creates and retuns a new file object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``type`` The file type for the file object. :raw-html:`<br />`
``permissions`` The file objects permissions, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`
``Owner`` The name for the file object owner. :raw-html:`<br />`
 **Warning** Do not enter any value for ``Owner``, exept if you want to set the owner to another user. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreateDirectory(path:string, permissions:string, Owner:string) -> table

Creates and retuns a new directory object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``permissions`` The file objects permissions, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`
``Owner`` The name for the file object owner. :raw-html:`<br />`
 **Warning** Do not enter any value for ``Owner``, exept if you want to set the owner to another user. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.DeleteObject(path:string) -> bool

Delets a file or directory object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.HasAttribute(path:string, attribute:string) -> bool

Checks if a file or directory object has a certain Attribute. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to check for. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.SetAttribute(path:string, attribute:string) -> table

Creates or sets a new Attribute for a file or directory object. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to set. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.RemoveLastItemOfPath(path:string) -> string

Returns a modified string, where the string past the last ``/`` is cut. :raw-html:`<br />`
(e.g., "C:/System/Test" -> "C:/System") :raw-html:`<br />`
``path`` The path you want to check. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFinalObjectName(path:string) -> string

Returns a modified string, where the string before the last ``/`` is cut. :raw-html:`<br />`
(e.g., "C:/System/Test" -> "Test") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFileExtension(path:string, fileobj:table) -> string

Returns the string file extension of a provided path. :raw-html:`<br />`
(e.g., "C:/System/Test.txt" -> "txt") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.RemoveCharacterFromPathEnd(path:string, chartoremove:string) -> string

Returns a modified string, where the last character is cut. :raw-html:`<br />`
(e.g., "C:/System/" -> "C:/System") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.RemoveFileNameNotAllowedCharacters(path:string) -> string

Returns a modified string, where any non allowed characters are removed or replaced with underscores. :raw-html:`<br />`
(e.g., "Hello #World" -> "Hello_World") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`

----




Kernel
==========
 **Warning** Most of the Kernel functions can or will crash the system, be carefull when using them. :raw-html:`<br />`

.. code-block:: luau  

   Kernel.MemAlloc(memamount:number) -> nil

Allowcates a specified amount of memory :raw-html:`<br />`
``memamount`` The amount of memory you want to allowcate in bytes. :raw-html:`<br />`
 **Warning** Only enter a number for ``memamount`` :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemDealloc(memamount:number) -> nil

Deallocates a specified amount of memory :raw-html:`<br />`
``memamount`` The amount of memory you want to deallocate in bytes. :raw-html:`<br />`
 **Warning** Only enter a number for ``memamount`` :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemUpdate(applicationdata:table) -> nil

Recalculates and updates the required amount of memory for a provided application :raw-html:`<br />`
``applicationdata`` The info table for an application. :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.ReturnMem(returnmax:bool) -> number

Returns the amount of system memory or the used amount of memoryThe amount of memory you want to deallocate in bytes :raw-html:`<br />`
``returnmax`` The toggle value for what it returns. :raw-html:`<br />`
``┗━>`` If ``true`` is provided, it returns the amount of memory the system has. :raw-html:`<br />`
``┗━>`` If nothing or ``false`` is provided, it returns the amount of used system memory. :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemCalc(application:instance) -> number

Calculates the amount of memory required for a specified app :raw-html:`<br />`
``application`` The application you want to calculate the memory for :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.SystemBugCheck(errorcode:string) -> nil

Crashes the system and creates a dump file :raw-html:`<br />`
``errorcode`` The error code you see in the crash screen :raw-html:`<br />`
Dump files can be found in ``/System/Dumps/``

----

.. code-block:: luau  

   Kernel.SystemStart() -> nil

Starts the system and loads everything required

----

.. code-block:: luau  

 Kernel.SystemShutdown(systemrestart:bool) -> nil 

Shuts down or Reboots the system, also saves the file system. :raw-html:`<br />`
``systemrestart`` The toggle value for if it restarts. :raw-html:`<br />`
``┗━>`` If ``true`` is provided, it will reboot the system. :raw-html:`<br />`
``┗━>`` If nothing or ``false`` is provided, it shuts down and kicks the player. :raw-html:`<br />`

----






AccountManager
==========

.. code-block:: luau  

   AccountManager.GetCurrentUser() -> string

Returns the currently logged-in user

----

.. code-block:: luau  

   AccountManager.CreateAccount(username:string, pin:number, permissions:string) -> nil

Creates a new user account :raw-html:`<br />`
``username`` The name of the new user account. :raw-html:`<br />`
``pin`` The PIN number for the account, can be left empty. :raw-html:`<br />`
``permissions`` The permissions that the user will have, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`

----

.. code-block:: luau  

   AccountManager.DeleteAccount(username:string) -> nil

Deletes a user account. :raw-html:`<br />`
``username`` The name of the user account you want to delete. :raw-html:`<br />`

----

.. code-block:: luau  

   AccountManager.SetAccountPIN(username:string oldpin:number, newpin:number) -> bool

Updates the PIN number on a user account. :raw-html:`<br />`
``username`` The name of the user account you want to change the PIN for. :raw-html:`<br />`
``oldpin`` The current PIN number of the user account. :raw-html:`<br />`
``newpin`` The new PIN number of the user account. :raw-html:`<br />`

----





NetworkManager
==========

.. code-block:: luau  

   NetworkManager.NetConnect(CustomIP:string) -> nil

Connects the system to the LimeOS Network. :raw-html:`<br />`
``CustomIP`` The toggle value for if you want to use an custom IP. :raw-html:`<br />`
``┗━>`` If an IP is provided, it will use that IP. :raw-html:`<br />`
``┗━>`` If nothing is provided, it will generate you a IP if you dont already have one. :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.NetDisconnect() -> nil

Disconnect the system from the LimeOS Network.

----

.. code-block:: luau  

   NetworkManager.Post(ToIP:string, Port:string Data:any) -> nil

Sends data to an IP on a port. :raw-html:`<br />`
``ToIP`` The IP you want to send data to. :raw-html:`<br />`
``Port`` The Port you want to send the data too. :raw-html:`<br />`
``Data`` The data you want to send, can be anything exept instances. :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.Receive(Port:string, callback:function) -> function

Calls a connected function if any data is received on a specified Port. :raw-html:`<br />`
``Port`` The port you want to listen on for data. :raw-html:`<br />`
``callback`` The function you want the NetworkManager to call once you receive data. :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.NetStatus() -> bool

Returns the connection status of the system. :raw-html:`<br />`
``true`` The system is connected. :raw-html:`<br />`
``false`` The system is not connected :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.ToggleStaticIP() -> bool

Toggels if you want a static or dynamic IP. :raw-html:`<br />`
 **Warning** This function is still ``W.I.P``. :raw-html:`<br />`

----




NotificationManager
==========

.. code-block:: luau  

   NotificationManager.SendNotification(title:string, body:string) -> nil

This function sends a side notification

----




ClockManager
==========

.. code-block:: luau  

   ClockManager.ConvertTime(Value:number, From:string, To:string) -> number

This function converts the gives value from one format to another, eg. Seconds to Minutes, the function will return ``-1`` if the ``From`` or ``To`` value couldnt be found :raw-html:`<br />`
These are all avalible formats: :raw-html:`<br />`
``"second"``, :raw-html:`<br />`
``"minute"``, :raw-html:`<br />`
``"hour"``, :raw-html:`<br />`
``"day"``, :raw-html:`<br />`
``"week"``, :raw-html:`<br />`
``"month"``, :raw-html:`<br />`
``"year"``, :raw-html:`<br />`

----

.. code-block:: luau  

   ClockManager.CurrentTime(FormatString:string) -> string

This function returns a formatted version of the current time/date, without any ``FormatString`` provided it returns ``Hour:Minute`` in 24 Hour time :raw-html:`<br />`
These are the diffrent formats: :raw-html:`<br />`
``"%Y" = Year``, :raw-html:`<br />`
``"%m" = Month``, :raw-html:`<br />`
``"%d" = Day``, :raw-html:`<br />`
``"%H" = Hour (24-hour clock)``, :raw-html:`<br />`
``"%I" = Hour (12-hour clock)``, :raw-html:`<br />`
``"%M" = Minute``, :raw-html:`<br />`
``"%S" = Second``, :raw-html:`<br />`
``"%p" = AM/PM``, :raw-html:`<br />`

----







ApplicationManager
==========

.. code-block:: luau  

   ApplicationManager.GetProcesses() -> nil

This function returns all open processes

----

.. code-block:: luau  

   ApplicationManager.ExecuteLEF(lefdata:string) -> nil

This function executes LEF files

----

.. code-block:: luau  

   ApplicationManager.UpdateProcess(processid:string, toupdate:string, data:string) -> nil

This function updates a specified property of an process

----

.. code-block:: luau  

   ApplicationManager.StartProcess(processname:string, processdata:table) -> instance

This function starts a new process and returns the app obj for it

----

.. code-block:: luau  

   ApplicationManager.ExitProcess(processid:string) -> nil

This function closes a process

----

.. code-block:: luau  

   ApplicationManager.CloseAllProcesses() -> nil

This function closes all open processes

----





DesktopManager
==========

.. code-block:: luau  

   DesktopManager.LogOut() -> nil

This function logs the currently logged-in user out

----

.. code-block:: luau  

   DesktopManager.InitDesktop() -> nil

This function starts the desktop

----

.. code-block:: luau  

   DesktopManager.LoginSetup() -> nil

This function starts the login screen

----

.. code-block:: luau  

   DesktopManager.UpdateWallpaper() -> nil

This function updates the desktop wallpaper

----





RegistryHandler
==========

.. code-block:: luau  

   RegistryHandler.CreateKey(key:string, data:string) -> bool

This function creates a new registry key

----

.. code-block:: luau  

   RegistryHandler.DeleteKey(key:string) -> bool

This function deletes a registry key

----

.. code-block:: luau  

   RegistryHandler.SetKey(key:string, data:string) -> nil

This function updates the data of a registry key

----

.. code-block:: luau  

   RegistryHandler.GetKey(key:string) -> table

This function returns a registry key

----

.. code-block:: luau  

   RegistryHandler.SaveRegistry() -> nil

This function saves the registry

----

.. code-block:: luau  

   RegistryHandler.LoadRegistry() -> nil

This function loads the registry

----

.. code-block:: luau  

   RegistryHandler.InitRegistry() -> nil

This function sets up the registry

----






ExecutableHost
==========

.. code-block:: luau  

  number ExecutableHost.readlef(data:string) -> 

This function reads LEF files

----

.. code-block:: luau  

  string ExecutableHost.createlef(code:string, admin:bool, publisher:string, env:table) -> 

This function creates new LEF files

----

.. code-block:: luau  

  string ExecutableHost.createlefraw(code:string, admin:bool, publisher:string) -> 

This function creates new LEF files

----

.. code-block:: luau  

  number ExecutableHost.selftest() -> 

``nil``

----





Http
==========

.. code-block:: luau  

  unknown Http.HttpGet(url, nocache, headers, contentType, requestType) -> 

This function makes http Get requests

----

.. code-block:: luau  

  unknown Http.HttpPost(url, data, content_type, compress, headers) -> 

This function makes http Post requests

----

.. code-block:: luau  

  string Http.JSONEncode(data:table) -> 

This function JSON encodes tables to strings and returns them

----

.. code-block:: luau  

  table Http.JSONDecode(data:string) -> 

This function JSON decodes JSON encoded tables and returns a table

----





EnvTable
==========

.. code-block:: luau  

  nil EnvTable.nil() -> 

``nil``

----

