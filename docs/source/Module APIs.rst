==========
Module API
==========
To use these modules and the function in them load them ``loadlib()``.

.. role:: raw-html(raw)
    :format: html

----

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

Returns a partition based on an number index. :raw-html:`<br />`
``index`` A number index of all partitions. (e.g., 2 will always get the 2nd partition) :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetPartitionByName(name:string) -> table

Returns a partition based on a string name. :raw-html:`<br />`
``name`` A string name of a partition. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool) -> table

Creates a new partition table and returns it. :raw-html:`<br />`
``name`` A string name of the new partition. :raw-html:`<br />`
``PartitionSize`` A number size in MB for the new partition. :raw-html:`<br />`
``IsOSDrive`` A bool value, of LimeOS is installed on that partition. :raw-html:`<br />`
 **Warning** Do not enter any value for ``IsOSDrive`` **Warning** :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.DelPartition(partition:string) -> bool

Deletes a partition based on a string name. The function will return ``true`` if the deletion was successful :raw-html:`<br />`
``partition`` A string name for the to be deleted partition. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CheckPartitionSize(partition:string, Data:table) -> bool

Retuns ``true`` when there is still space on the partition for the provided data.
``partition`` A string name for the to be checked partition. :raw-html:`<br />`
``Data`` A data table. :raw-html:`<br />`

----

.. code-block:: luau  

    FileSystem.GetUserPermissions(user:string) ->  string/table

Returns the permissions of the user.
``user`` A string name for the user. :raw-html:`<br />`
 **Warning** Do not enter any value for ``user`` **Warning** :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CheckPermissions(path:string, user:string, permissiontype:string) -> bool

Checks if the user has the same permissions as the provided permissions.
``path`` A string for the path. :raw-html:`<br />`
``user`` A string name for the user. :raw-html:`<br />`
``permissiontype`` A string the checked permissions. :raw-html:`<br />`
 **Warning** Do not enter any value for ``user``, only enter ``nil`` as a value **Warning** :raw-html:`<br />`


----

.. code-block:: luau  

   FileSystem.CalculateObjectSize(path:string) -> number

Returns the KB or MB size of a file object based on a provided path.

----

.. code-block:: luau  

   FileSystem.FileExists(path:string) -> bool

Checks if a file object exists based on a provided path.

----

.. code-block:: luau  

   FileSystem.GetFile(path:string) -> table

Returns a file object based on a provided path.

----

.. code-block:: luau  

   FileSystem.GetFiles(path:string) -> table

Returns the files inside a directory object based on a provided path.

----

.. code-block:: luau  

   FileSystem.WriteFile(path:string, data:string, user:string, plaintext:bool) -> bool

Writes new data to a file object based on a provided path.
--This function writes new data to a file, set ``plaintext`` to true to disable encryption (not really supported)
--**Set** ``user:string`` **to** ``nil``

----

.. code-block:: luau  

   FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string) -> table

Creates and retuns a new file object, and placing it in the provided path.

----

.. code-block:: luau  

   FileSystem.CreateDirectory(path:string, permissions:string, Owner:string) -> table

Creates and retuns a new directory object, and placing it in the provided path.

----

.. code-block:: luau  

   FileSystem.DeleteObject(path:string) -> bool

Delets a file or directory object based on a provided path.

----

.. code-block:: luau  

   FileSystem.HasAttribute(path:string, attribute:string) -> bool

Checks if a file or directory object has a certain Attribute.

----

.. code-block:: luau  

   FileSystem.SetAttribute(path:string, attribute:string) -> table

Creates or sets a new Attribute for a file or directory object.

----

.. code-block:: luau  

   FileSystem.RemoveLastItemOfPath(path:string) -> string

Returns a modified string, where the string past the last ``/`` is cut. (e.g., "C:/System/Test" -> "C:/System")

----

.. code-block:: luau  

   FileSystem.GetFinalObjectName(path:string) -> string

Returns a modified string, where the string before the last ``/`` is cut. (e.g., "C:/System/Test" -> "Test")

----

.. code-block:: luau  

   FileSystem.GetFileExtension(path:string, fileobj:table) -> string

Returns the string file extension of a provided path (e.g., "C:/System/Test.txt" -> "txt")

----

.. code-block:: luau  

   FileSystem.RemoveCharacterFromPathEnd(path:string, chartoremove:string) -> string

Returns a modified string, where the last character is cut. (e.g., "C:/System/" -> "C:/System")

----

.. code-block:: luau  

   FileSystem.RemoveFileNameNotAllowedCharacters(path:string) -> string

Returns a modified string, where any non allowed characters are removed or replaced with underscores. (e.g., "Hello #World" -> "Hello_World")

----




Kernel
==========

.. code-block:: luau  

   Kernel.MemAlloc(memamount:number) -> nil

This function allowcates memory from system memory

----

.. code-block:: luau  

   Kernel.MemDealloc(memamount:number) -> nil

This function deallocates memory from system memory

----

.. code-block:: luau  

   Kernel.MemUpdate(applicationdata:table) -> nil

This function updates the memory used by apps

----

.. code-block:: luau  

   Kernel.ReturnMem(returnmax:bool) -> number

This function returns the used amount of memory, if ``returnmax:bool`` is set to ``true`` it returns the amount of memory the system has

----

.. code-block:: luau  

   Kernel.MemCalc(application:instance) -> number

This function calculates the amount of memory used by an app

----

.. code-block:: luau  

   Kernel.SystemBugCheck(errorcode:string) -> nil

This function crashes the system and creates a dump file
This file can be found at: */System/Dumps/*

----

.. code-block:: luau  

   Kernel.SystemStart(systemrestart:bool) -> nil

This function starts the system and loads everything requered

----

.. code-block:: luau  

 Kernel.SystemShutdown() -> nil 

This function shuts down the system or restarts it if ``systemrestart:bool`` is set to ``true``

----






AccountManager
==========

.. code-block:: luau  

   AccountManager.GetCurrentUser() -> string

This function returns the currently logged-in user

----

.. code-block:: luau  

   AccountManager.CreateAccount(username:string, pin:number, permissions:string) -> nil

This function creates a new user account

----

.. code-block:: luau  

   AccountManager.DeleteAccount(username:string) -> nil

This function deletes a user account

----

.. code-block:: luau  

   AccountManager.SetAccountPIN(username:string oldpin:number, newpin:number) -> bool

This function updates the pin on a user account

----





NetworkManager
==========

.. code-block:: luau  

   NetworkManager.NetConnect() -> nil

This function connects the system to the network

----

.. code-block:: luau  

   NetworkManager.NetDisconnect() -> nil

This function disconnect the system to the network

----

.. code-block:: luau  

   NetworkManager.Post(ToIP:string, Data:any) -> nil

This function sends data to a specified IP

----

.. code-block:: luau  

   NetworkManager.Receive(callback:function) -> function

This function calls the specified callback function when data has been received

----

.. code-block:: luau  

   NetworkManager.NetStatus() -> bool

This function returns the connection status of the system, true = connected, false = not connected

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

