==========
Module API
==========
To use these modules and the function in them load them ``loadlib()``.

.. role:: raw-html(raw)
    :format: html

----

FileSystem
==========
The FileSystem uses a set of 4 permissions, they need to be in a set format to be used correctly. :raw-html:`<br />`
``R = Read, W = Write, D = Delete, A = Admin``. :raw-html:`<br />`
When setting permissions, seperate them with a - when using multible (``"R-W-D"``), otherwise just a singular permission (``"R"`` or ``"D"``) :raw-html:`<br />`
Permissions only effect changes to a fileobj such as deleting or writing or when creating new ones. :raw-html:`<br />`


.. code-block:: luau  

  table FileSystem.GetPartitions()

This function returns all partitions on LimeOS

----

.. code-block:: luau  

  string FileSystem.GetOSDriveLetter()

This function returns the drive letter that LimeOS is installed on

----

.. code-block:: luau  

  table FileSystem.GetPartitionByIndex(index:number)

This function returns a partition

----

.. code-block:: luau  

  table FileSystem.GetPartitionByName(name:string)

This function returns a partition

----

.. code-block:: luau  

  table FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool)

This function creates a partition and returns it

----

.. code-block:: luau  

  bool FileSystem.DelPartition(partition:string)

This function deletes a partition

----

.. code-block:: luau  

  bool FileSystem.CheckPartitionSize(partition:string, Data:table)

This function checks if a files data still has space on a partition

----

.. code-block:: luau  

  string/table FileSystem.GetUserPermissions(user:string)

This function returns the permissions of a specified user, leave ``user:string`` blank to get the permissions of the currently logged-in user

----

.. code-block:: luau  

  bool FileSystem.CheckPermissions(path:string, user:string, permissiontype:string)

This function checks if a user has permissions to edit a fileobj, leave ``user:string`` blank to check the currently logged-in user
Permissions need to be in this format: "R-W"- or "R"


----

.. code-block:: luau  

  number FileSystem.CalculateObjectSize(path:string)

This function returns the size of a files data on KB or MB

----

.. code-block:: luau  

  bool FileSystem.FileExists(path:string)

This function checks if a fileobj exists

----

.. code-block:: luau  

  table FileSystem.GetFile(path:string)

This function returns a fileobj

----

.. code-block:: luau  

  table FileSystem.GetFiles(path:string)

This function returns the children of a directory

----

.. code-block:: luau  

  bool FileSystem.WriteFile(path:string, data:string, user:string, plaintext:bool)

This function writes new data to a file, set ``plaintext`` to true to disable encryption (not really supported)
**Set** ``user:string`` **to** ``nil``

----

.. code-block:: luau  

  table FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string)

This function creates a new file, the file name is the last part of the path
.path/**filename**.ext

----

.. code-block:: luau  

  table FileSystem.CreateDirectory(path:string, permissions:string, Owner:string)

This function creates a new directory

----

.. code-block:: luau  

  bool FileSystem.DeleteObject(path:string)

This function delets a fileobj

----

.. code-block:: luau  

  bool FileSystem.HasAttribute(path:string, attribute:string)

This function checks if a fileobj has a certain attribute

----

.. code-block:: luau  

  table FileSystem.SetAttribute(path:string, attribute:string)

This function sets a fileobj attributes

----

.. code-block:: luau  

  string FileSystem.RemoveLastItemOfPath(path:string)

This function removes the last item from a path, seperated by ``/`` and returns the new path

----

.. code-block:: luau  

  string FileSystem.GetFinalObjectName(path:string)

This function returns the last item from a path, seperated by ``/`` and returns the last item

----

.. code-block:: luau  

  string FileSystem.GetFileExtension(path:string, fileobj:table)

This function returns the file extension of a file, you can either set a path or a fileobj

----

.. code-block:: luau  

  string FileSystem.RemoveCharacterFromPathEnd(path:string, chartoremove:string)

This function removes the last character from a path and returns the new path

----

.. code-block:: luau  

  string FileSystem.RemoveFileNameNotAllowedCharacters(path:string)

This function removes not allowed characters from a path and returns the cleaned path

----




Kernel
==========

.. code-block:: luau  

  nil Kernel.MemAlloc(memamount:number)

This function allowcates memory from system memory

----

.. code-block:: luau  

  nil Kernel.MemDealloc(memamount:number)

This function deallocates memory from system memory

----

.. code-block:: luau  

  nil Kernel.MemUpdate(applicationdata:table)

This function updates the memory used by apps

----

.. code-block:: luau  

  number Kernel.ReturnMem(returnmax:bool)

This function returns the used amount of memory, if ``returnmax:bool`` is set to ``true`` it returns the amount of memory the system has

----

.. code-block:: luau  

  number Kernel.MemCalc(application:instance)

This function calculates the amount of memory used by an app

----

.. code-block:: luau  

  nil Kernel.SystemBugCheck(errorcode:string)

This function crashes the system and creates a dump file
This file can be found at: */System/Dumps/*

----

.. code-block:: luau  

  nil Kernel.SystemStart(systemrestart:bool)

This function starts the system and loads everything requered

----

.. code-block:: luau  

  nil Kernel.SystemShutdown()

This function shuts down the system or restarts it if ``systemrestart:bool`` is set to ``true``

----






AccountManager
==========

.. code-block:: luau  

  string AccountManager.GetCurrentUser()

This function returns the currently logged-in user

----

.. code-block:: luau  

  nil AccountManager.CreateAccount(username:string, pin:number, permissions:string)

This function creates a new user account

----

.. code-block:: luau  

  nil AccountManager.DeleteAccount(username:string)

This function deletes a user account

----

.. code-block:: luau  

  bool AccountManager.SetAccountPIN(username:string oldpin:number, newpin:number)

This function updates the pin on a user account

----





NetworkManager
==========

.. code-block:: luau  

  nil NetworkManager.NetConnect()

This function connects the system to the network

----

.. code-block:: luau  

  nil NetworkManager.NetDisconnect()

This function disconnect the system to the network

----

.. code-block:: luau  

  nil NetworkManager.Post(ToIP:string, Data:any)

This function sends data to a specified IP

----

.. code-block:: luau  

  function NetworkManager.Receive(callback:function)

This function calls the specified callback function when data has been received

----

.. code-block:: luau  

  bool NetworkManager.NetStatus()

This function returns the connection status of the system, true = connected, false = not connected

----




NotificationManager
==========

.. code-block:: luau  

  nil NotificationManager.SendNotification(title:string, body:string)

This function sends a side notification

----




ClockManager
==========

.. code-block:: luau  

  number ClockManager.ConvertTime(Value:number, From:string, To:string)

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

  number ClockManager.CurrentTime(FormatString:string)

This function returns a formatted version of the current time/date, without any ``FormatString`` provided it returns ``Hour:Minute`` in 24 Hour time :raw-html:`<br />`
These are the diffrent formats: :raw-html:`<br />`
``"%Y" = Year``, :raw-html:`<br />`
``"%m" = Month ``, :raw-html:`<br />`
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

  nil ApplicationManager.GetProcesses()

This function returns all open processes

----

.. code-block:: luau  

  nil ApplicationManager.ExecuteLEF(lefdata:string)

This function executes LEF files

----

.. code-block:: luau  

  nil ApplicationManager.UpdateProcess(processid:string, toupdate:string, data:string)

This function updates a specified property of an process

----

.. code-block:: luau  

  instance ApplicationManager.StartProcess(processname:string, processdata:table)

This function starts a new process and returns the app obj for it

----

.. code-block:: luau  

  nil ApplicationManager.ExitProcess(processid:string)

This function closes a process

----

.. code-block:: luau  

  nil ApplicationManager.CloseAllProcesses()

This function closes all open processes

----





DesktopManager
==========

.. code-block:: luau  

  nil DesktopManager.LogOut()

This function logs the currently logged-in user out

----

.. code-block:: luau  

  nil DesktopManager.InitDesktop()

This function starts the desktop

----

.. code-block:: luau  

  nil DesktopManager.LoginSetup()

This function starts the login screen

----

.. code-block:: luau  

  nil DesktopManager.UpdateWallpaper()

This function updates the desktop wallpaper

----





RegistryHandler
==========

.. code-block:: luau  

  bool RegistryHandler.CreateKey(key:string, data:string)

This function creates a new registry key

----

.. code-block:: luau  

  bool RegistryHandler.DeleteKey(key:string)

This function deletes a registry key

----

.. code-block:: luau  

  nil RegistryHandler.SetKey(key:string, data:string)

This function updates the data of a registry key

----

.. code-block:: luau  

  table RegistryHandler.GetKey(key:string)

This function returns a registry key

----

.. code-block:: luau  

  nil RegistryHandler.SaveRegistry()

This function saves the registry

----

.. code-block:: luau  

  nil RegistryHandler.LoadRegistry()

This function loads the registry

----

.. code-block:: luau  

  nil RegistryHandler.InitRegistry()

This function sets up the registry

----





ClockManager
==========

.. code-block:: luau  

  nil ClockManager.nil()

This module is ``WIP``

----





ExecutableHost
==========

.. code-block:: luau  

  number ExecutableHost.readlef(data:string)

This function reads LEF files

----

.. code-block:: luau  

  string ExecutableHost.createlef(code:string, admin:bool, publisher:string, env:table)

This function creates new LEF files

----

.. code-block:: luau  

  string ExecutableHost.createlefraw(code:string, admin:bool, publisher:string)

This function creates new LEF files

----

.. code-block:: luau  

  number ExecutableHost.selftest()

``nil``

----





Http
==========

.. code-block:: luau  

  unknown Http.HttpGet(url, nocache, headers, contentType, requestType)

This function makes http Get requests

----

.. code-block:: luau  

  unknown Http.HttpPost(url, data, content_type, compress, headers)

This function makes http Post requests

----

.. code-block:: luau  

  string Http.JSONEncode(data:table)

This function JSON encodes tables to strings and returns them

----

.. code-block:: luau  

  table Http.JSONDecode(data:string)

This function JSON decodes JSON encoded tables and returns a table

----





EnvTable
==========

.. code-block:: luau  

  nil EnvTable.nil()

``nil``

----

