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
.. note::  
    The FileSystem module utilizes four distinct permissions: :raw-html:`<br />` 
    ``R = Read, W = Write, D = Delete, and A = Admin``. :raw-html:`<br />` 
    Permissions should be formatted correctly, with multiple permissions separated by a hyphen (e.g., "R-W-D"). For single permissions, simply use the corresponding letter (e.g., "R" or "D"). :raw-html:`<br />` 
    These permissions govern actions such as reading, writing, deleting, and creating file objects. :raw-html:`<br />`

.. note::  
    The FileSystem has a linux like folder structure. :raw-html:`<br />` 

    .. code-block:: bash  

        root      
        ├── sys   : System files
        ├── bin   : Terminal commands
        ├── boot  : Boot files/options
        ├── dmp   : Crash dumps
        ├── init  : Programs which autostart
        ├── menu  : Custom start menu entries
        ├── etc   : Configuration files, etc.
        └── de    : Files for custom DEs
        users     
        └── app   : Application data

Partition Functions
-------------------

.. code-block:: luau  

    FileSystem.GetOSDriveLetter() -> string

Returns the partition name where LimeOS is installed on.

----

.. code-block:: luau  

    FileSystem.GetPartitions() -> table

Returns a table of all partitions in LimeOS.

----

.. code-block:: luau  

   FileSystem.GetPartitionByIndex(index:number) -> table or bool, string

Returns a partition based on an index number. :raw-html:`<br />`
``index`` The index number of a partition. (e.g., 2 will always get the 2nd partition) :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetPartitionByName(name:string) -> table or bool, string

Returns a partition based on a string name. :raw-html:`<br />`
``name`` The name of a partition. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CheckPartitionSize(partition:string, Data:table) -> bool

Retuns ``true`` when there is still space on the partition for the provided data. :raw-html:`<br />`
``partition`` The name for the to be checked partition. :raw-html:`<br />`
``Data`` The partition data. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool) -> table or bool, string

Creates a new partition table and returns it. :raw-html:`<br />`
``name`` The name of the new partition. :raw-html:`<br />`
``PartitionSize`` The partition size in MB for the new partition. :raw-html:`<br />`
``IsOSDrive`` A bool value, that marks if LimeOS is installed on that partition. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``IsOSDrive`` :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.DelPartition(partition:string) -> bool, string

Deletes a partition based on a string name. The function will return ``true`` if the deletion was successful :raw-html:`<br />`
``partition`` The name for the to be deleted partition. :raw-html:`<br />`

----

File OP Helper Functions
------------------------

.. code-block:: luau  

   FileSystem.CheckPermissions(path:string, user:string, permissiontype:string) -> bool

Checks if the user has the same permissions as the provided permissions. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``permissiontype`` The permissions that will be checked for, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``user``, only enter ``nil`` as a value :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CalculateObjectSize(path:string) -> string

Returns the KB or MB size of a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.FileExists(path:string) -> bool

Checks if a file object exists based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFile(path:string) -> table or bool, string

Returns a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.GetFiles(path:string) -> table or bool, string

Returns the files inside a directory object based on a provided path. :raw-html:`<br />`
``path`` The string path to the directory object. :raw-html:`<br />`

----

File OP Functions
-----------------

.. code-block:: luau  

   FileSystem.WriteFile(path:string, data:string, user:string, plaintext:bool) -> bool, string

Writes new data to a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``data`` The new data for the file. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``plaintext`` A bool value that toggels file encryption, ``true`` turns the encryption off. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``user``, only enter ``nil`` as a value, ``plaintext`` is not intened to be used for normal files :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string) -> table or bool, string

Creates and retuns a new file object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``┗━>`` The file name is everything past the last ``/``, so ``/System/testfile.txt`` would have a file name of ``testfile.txt``. :raw-html:`<br />`
``type`` The file type for the file object. :raw-html:`<br />`
``permissions`` The file objects permissions, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`
``Owner`` The name for the file object owner. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``Owner``, exept if you want to set the owner to another user. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.CreateDirectory(path:string, permissions:string, Owner:string) -> table or bool, string

Creates and retuns a new directory object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a directory object. :raw-html:`<br />`
``┗━>`` The directory name is everything past the last ``/``, so ``/System/NewDir`` would have a directory name of ``newDir``. :raw-html:`<br />`
``permissions`` The directory objects permissions, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`
``Owner`` The name for the directory object owner. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``Owner``, exept if you want to set the owner to another user. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.DeleteObject(path:string) -> bool, string

Delets a file or directory object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.XCopy(path:string, newpath:string) -> bool, string

Copyies a file or dir to another location. :raw-html:`<br />`
``path`` The path to a file/dir. :raw-html:`<br />`
``newpath`` The new path for the file/dir, you can also rename the file/dir eg. ``../../NewName.txt``. :raw-html:`<br />`

----

FS Helper Functions
-------------------

.. code-block:: luau  

   FileSystem.HasAttribute(path:string, attribute:string) -> bool, string

Checks if a file or directory object has a certain Attribute. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to check for. :raw-html:`<br />`

----

.. code-block:: luau  

   FileSystem.SetAttribute(path:string, attribute:string, action:string) -> bool, string

Updates the Attributes of a file. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to set/remove. :raw-html:`<br />`
``action`` If you wan to ``add`` or ``remove`` the attribute. :raw-html:`<br />`

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
.. warning::
    Most of the Kernel functions can or will crash the system, be carefull when using them. :raw-html:`<br />`

.. code-block:: luau  

   Kernel.MemAlloc(memamount:number) -> nil

Allowcates a specified amount of memory. :raw-html:`<br />`
``memamount`` The amount of memory you want to allowcate in bytes. :raw-html:`<br />`

.. warning::
    Only enter a number for ``memamount`` :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemDealloc(memamount:number) -> nil

Deallocates a specified amount of memory. :raw-html:`<br />`
``memamount`` The amount of memory you want to deallocate in bytes. :raw-html:`<br />`

.. warning::
    Only enter a number for ``memamount`` :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemUpdate(applicationdata:table) -> nil

Recalculates and updates the required amount of memory for a provided application. :raw-html:`<br />`
``applicationdata`` The info table for an application. :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.ReturnMem(returnmax:bool) -> number

Returns the amount of system memory or the used amount of memory. :raw-html:`<br />`
``returnmax`` The toggle value for what it returns. :raw-html:`<br />`
``┗━>`` If ``true`` is provided, it returns the amount of memory the system has. :raw-html:`<br />`
``┗━>`` If nothing or ``false`` is provided, it returns the amount of used system memory. :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.MemCalc(application:instance) -> number

Calculates the amount of memory required for a specified app. :raw-html:`<br />`
``application`` The application you want to calculate the memory for :raw-html:`<br />`

----

.. code-block:: luau  

   Kernel.KernelPanic(errorcode:string) -> nil

Crashes the system and creates a dump file. :raw-html:`<br />`
``errorcode`` The error code you see in the crash screen :raw-html:`<br />`
Dump files can be found in ``/System/Dumps/``

----

.. code-block:: luau  

   Kernel.SystemStart() -> nil

Starts the system and loads everything required.

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
``CustomIP`` A value for an custom IP. :raw-html:`<br />`
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
``false`` The system is not connected. :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.GetIP() -> bool

Returns the IP the system is connected with. :raw-html:`<br />`

----

.. code-block:: luau  

   NetworkManager.ToggleStaticIP() -> bool

Toggels if you want a static or dynamic IP. :raw-html:`<br />`

.. warning::
    This function is still ``W.I.P``. :raw-html:`<br />`

----








NotificationManager
==========

.. code-block:: luau  

   NotificationManager.SendNotification(title:string, body:string) -> nil

Sends a side notification with a Title and body :raw-html:`<br />`
``title`` The title of the notification. :raw-html:`<br />`
``body`` The body of the notification. :raw-html:`<br />`

----

.. code-block:: luau  

   NotificationManager.PopUp(Title:string, Prompt:string, AnswerType:number, MsgType:number, callback:function) -> nil

Creates a popup with diffrent options :raw-html:`<br />`
``title`` The title of the popup, located in the topbar of the popup. :raw-html:`<br />`
``body`` The body of the popup. :raw-html:`<br />`
``AnswerType`` The answer options of the popup. :raw-html:`<br />`
``┗━>`` ``1`` is a Yes/No answer option. :raw-html:`<br />`
``┗━>`` ``2`` is a OK answer option. :raw-html:`<br />`
``MsgType`` What type of popup. :raw-html:`<br />`
``┗━>`` ``1`` is a Info popup. :raw-html:`<br />`
``┗━>`` ``2`` is a Warning popup. :raw-html:`<br />`
``┗━>`` ``3`` is an Error popup, the popup text is also the color red. :raw-html:`<br />`
``callback`` A function that gets called if a Yes has been clicked on a Yes/No popup. :raw-html:`<br />`

----








ExtraUIElements
==========

.. code-block:: luau  

   ExtraUIElements.OpenSaveFileMenu(InputData:table) -> table

Opens a save file dialog and returns the saved file. :raw-html:`<br />`

.. note::
    The ``InputData`` table has to have these values inside with these exact names! :raw-html:`<br />`

``StartPath`` The path where the save dialog should open in. :raw-html:`<br />`
``AllowedFileTypes`` The file extestions that are allowed to be saved. (e.g. ``{".txt", ".txt2"}``) :raw-html:`<br />`
``Data`` The data to be saved in the file. :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.OpenOpenFileMenu(InputData:table) -> table

Opens a open file dialog and returns the opened file. :raw-html:`<br />`

.. note::
    The ``InputData`` table has to have these values inside with these exact names! :raw-html:`<br />`

``StartPath`` The path where the open dialog should open in. :raw-html:`<br />`
``ExtraText`` Some info text displayed in the dialog. :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.CreateDropdownMenu(OptionsFrame:instance, Options:table, callback:function) -> string

Creates a dropdown menu and calls a callback function once a option has been selected. :raw-html:`<br />`
``OptionsFrame`` The UI object under which the dropdown menu apears. :raw-html:`<br />`
``Options`` The options the menu should have. (e.g. ``{"Option 1", "Option 2"}``) :raw-html:`<br />`
``callback`` The function that gets called once a option has been picked, this also returns the option picked. :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.OpenColorPicker(callback:function, cancelcallback:function, confirmcallback:function) -> nil

Opens a new window with a color picker. :raw-html:`<br />`
``callback`` Gets called when the color changes in the color picker. :raw-html:`<br />`
``cancelcallback`` When the user picks a color". :raw-html:`<br />`
``confirmcallback`` When the user canceles and closes the color picker. :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.CreatePrefabUI(Parent:instance, Size:udim2, Position:udim2, UI:string) -> nil

Creates a premade UI. :raw-html:`<br />`
``Parent`` The Parent of the new UI object. :raw-html:`<br />`
``Size`` The size of the UI object. :raw-html:`<br />`
``Position`` The position of the UI object. :raw-html:`<br />`
``UI`` The name of the premade UI. :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.CreateSlider(Parent:instance, Position:udim2, Size:udim2, MinValue:number, MaxValue:number, callback:function) -> nil

Creates a Slider with a Min and Max value. :raw-html:`<br />`
``Parent`` The Parent of the slider. :raw-html:`<br />`
``Position`` The position of the slider. :raw-html:`<br />`
``Size`` The size of the slider. :raw-html:`<br />`
``MinValue`` The minimum value that the slider can go to. :raw-html:`<br />`
``MaxValue`` The maximum value that the slider can go to. :raw-html:`<br />`
``callback`` The function that gets called when the slider value changes :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.CreateCheckBox(BoxParent:instances, Position:udim2, Size:udim2, StartingState:bool, callback:function) -> nil

Creates a checkbox UI object. :raw-html:`<br />`
``BoxParent`` The Parent of the checkbox. :raw-html:`<br />`
``Position`` The position of the checkbox. :raw-html:`<br />`
``Size`` The size of the checkbox. :raw-html:`<br />`
``StartingState`` The state the checkbox starts. :raw-html:`<br />`
``callback`` The function that gets called when the checkbox state changes :raw-html:`<br />`

----

.. code-block:: luau  

   ExtraUIElements.CreateCheckBoxWithText(BoxParent:instance, Text:string, TextFieldSize:udim2, Position:udim2, StartingState:bool, callback:function) -> nil

Creates a checkbox UI object with text on the left side. :raw-html:`<br />`
``BoxParent`` The Parent of the checkbox. :raw-html:`<br />`
``Text`` The text next to the checkbox. :raw-html:`<br />`
``TextFieldSize`` The size of the text. :raw-html:`<br />`
``Position`` The position of the checkbox. :raw-html:`<br />`
``Size`` The size of the checkbox. :raw-html:`<br />`
``StartingState`` The state the checkbox starts. :raw-html:`<br />`
``callback`` The function that gets called when the checkbox state changes :raw-html:`<br />`

----








ClockManager
==========

.. code-block:: luau  

   ClockManager.ConvertTime(Value:number, From:string, To:string) -> number

Converts the gives value from one format to another. :raw-html:`<br />`
``Value`` The value you want to convert. :raw-html:`<br />`
``From`` The current format the value is now. :raw-html:`<br />`
``To`` The format to which you want to convert. :raw-html:`<br />`

.. warning::
    If it cant find the ``From`` or ``To`` values it will return ``-1`` :raw-html:`<br />`

All avalible formats: :raw-html:`<br />`
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

Returns a formatted version of the current time/date. :raw-html:`<br />`
``FormatString`` The string that the formatter uses, see `os.date <https://create.roblox.com/docs/reference/engine/libraries/os#date>`_. :raw-html:`<br />`
``┗━>`` If nothing is provided, it defaults to this format ``Hour:Minute`` (24 Hour time). :raw-html:`<br />`

Here are some formats, you can see more at `os.date <https://create.roblox.com/docs/reference/engine/libraries/os#date>`_: :raw-html:`<br />`
``"%Y" = Year``, :raw-html:`<br />`
``"%m" = Month``, :raw-html:`<br />`
``"%d" = Day``, :raw-html:`<br />`
``"%H" = Hour (24-hour clock)``, :raw-html:`<br />`
``"%I" = Hour (12-hour clock)``, :raw-html:`<br />`
``"%M" = Minute``, :raw-html:`<br />`
``"%S" = Second``, :raw-html:`<br />`
``"%p" = AM/PM``, :raw-html:`<br />`

----








ApplicationHandler
==========

.. code-block:: luau  

   ApplicationManager.GetProcesses() -> nil

Returns all open processes.

----

.. code-block:: luau  

   ApplicationManager.ExecuteLEF(lefdata:string) -> nil

Executes LEF files.
``lefdata`` The LEF file data. :raw-html:`<br />`

----

.. code-block:: luau  

   ApplicationManager.UpdateProcess(processid:string, toupdate:string, data:string) -> nil

Updates a property of a process to a new value. :raw-html:`<br />`
``processid`` The process ID of the process that you want to update. :raw-html:`<br />`
``toupdate`` The property you want to update. :raw-html:`<br />`
``data`` The new value for the property. :raw-html:`<br />`

----

.. code-block:: luau  

   ApplicationManager.StartProcess(processname:string, processdata:table) -> instance

Starts a new process and returns the newly created app.
``processname`` The name for your new process, use the :doc:`Built-in` when you are creating new process. :raw-html:`<br />`
``processdata`` The process ID of the process that you want to update. :raw-html:`<br />`

----

.. code-block:: luau  

   ApplicationManager.ExitProcess(processid:string) -> nil

Closes a process. :raw-html:`<br />`
``processid`` The process ID of the process that you want to close. :raw-html:`<br />`

----

.. code-block:: luau  

   ApplicationManager.CloseAllProcesses() -> nil

Closes all processes. :raw-html:`<br />`

----








DesktopEnvironment
==========

.. note::
    When creating your own DE your module needs to have these functions! :raw-html:`<br />`

.. code-block:: luau  

   DesktopEnvironment.UnloadDesktop() -> nil

Unloads the Desktop. :raw-html:`<br />`

----

.. code-block:: luau  

   DesktopEnvironment.LoadDesktop() -> nil

Loads the Desktop. :raw-html:`<br />`

----

.. code-block:: luau  

   DesktopEnvironment.CreateLink(Name:string, Type:string, FilePath:string, Icon:string) -> nil	

Creates a new Icon on the current users desktop. :raw-html:`<br />`
``Name`` The name of the desktop icon, this is also the text under the icon itself. :raw-html:`<br />`
``Type`` The type of the link, like: ``(dir, LEF, etc)``. :raw-html:`<br />`
``FilePath`` The path to the linked object, eg. a directory you want to open.. :raw-html:`<br />`
``Icon`` The icon ID of the desktop icon. :raw-html:`<br />`

----

.. code-block:: luau  

   DesktopEnvironment.ChangeTaskbarSize(NewSize:number) -> nil

Changes the taskbar hight/size :raw-html:`<br />`
``NewSize`` The new size in px of the taskbar. :raw-html:`<br />`

----

.. code-block:: luau  

   DesktopEnvironment.AddTaskbarTab(AppName:string, ProcID:string, AppIcon:string) -> nil

Adds a new tab to the taskbar :raw-html:`<br />`
``AppName`` The name of the app, gets displayed on the tab itself. :raw-html:`<br />`
``ProcID`` The process ID of the process. :raw-html:`<br />`
``AppIcon`` The icon ID of the process for the icon in the tab. :raw-html:`<br />`

----

.. code-block:: luau  

   DesktopEnvironment.RemoveTaskbarTab(ProcID:string) -> nil

Removes a tab from the taskbar :raw-html:`<br />`
``ProcID`` The process ID of the process. :raw-html:`<br />`

----








ConsoleManager
==========

.. note::
    These functions are only relevant to you when creating your own commands. :raw-html:`<br />`

.. code-block:: luau  

   ConsoleManager.CheckLocalPath(path:string) -> string

Handles path proccesing  which enables shotcuts like ``./`` or ``../``. :raw-html:`<br />`
And returns a real path. :raw-html:`<br />`

----

.. code-block:: luau  

   ConsoleManager.PrintTable(table:table/string) -> string

Either returns a formatted string based on the table or returns just the input if its not a table. :raw-html:`<br />`

----





RegistryHandler
==========
.. note:: 
    The registry keys use a path like system (e.g. "System/FileExtensions/txt"). :raw-html:`<br />`

.. code-block:: luau  

   RegistryHandler.CreateKey(key:string, data:string) -> bool

Creates a new registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`
``┗━>`` The key name is everything past the last ``/``, so ``/System/NewRegKey`` would have a key name of ``NewRegKey``. :raw-html:`<br />`
``data`` The data for the registry key. :raw-html:`<br />`

----

.. code-block:: luau  

   RegistryHandler.DeleteKey(key:string) -> bool

Deletes a registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`

----

.. code-block:: luau  

   RegistryHandler.SetKey(key:string, data:string) -> nil

Updates the data of a registry key to a new value. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`
``data`` The new registry key data. :raw-html:`<br />`

----

.. code-block:: luau  

   RegistryHandler.GetKey(key:string) -> table

Returns a registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`

----

.. code-block:: luau  

   RegistryHandler.SaveRegistry() -> nil

Saves the registry to a file.

----

.. code-block:: luau  

   RegistryHandler.LoadRegistry() -> nil

Loads the registry from a file.

----

.. code-block:: luau  

   RegistryHandler.InitRegistry() -> nil

Sets up the registry.

----








SystemLogs
==========

.. code-block:: luau  

   SystemLogs.Log(Info:string) -> string

Logs and action with a timestamp. :raw-html:`<br />`
``Info`` The info that you want to log. :raw-html:`<br />`

----

.. code-block:: luau  

   SystemLogs.GetLogs() -> table

Returns a copy of the log table.

----

.. code-block:: luau  

   SystemLogs.LogDump() -> nil

Creates a dump file of all logs, can be found at ``/root/dmp``.

----







StringFiltering
==========

.. code-block:: luau  

   StringFiltering.FilterString() -> string

Uses Robloxes string filter for any inappropriate words.

----







DRMManager
==========

.. code-block:: luau  

   DRMManager.OwnsAsset(assetID:number) -> bool

Checks if the player owns an asset. :raw-html:`<br />`
``assetID`` The ID to the asset. :raw-html:`<br />`

----

.. code-block:: luau  

   DRMManager.OwnsApp(id) -> string

N/A. :raw-html:`<br />`
``assetID`` The ID to the asset. :raw-html:`<br />`

----

.. code-block:: luau  

   DRMManager.GetProductInfo(assetID:number) -> table?

Returns info about an asset. :raw-html:`<br />`
``assetID`` The ID to the asset. :raw-html:`<br />`

----

.. code-block:: luau  

   DRMManager.PromptPurchase(assetID:number) -> bool

Prompts the player to buy an asset. :raw-html:`<br />`
``assetID`` The ID to the asset. :raw-html:`<br />`

----

.. code-block:: luau  

   DRMManager.PromptGamePassPurchase(gamepassID:number) -> bool

Prompts the player to buy a gamepass. :raw-html:`<br />`
``gamepassID`` The ID to the gamepass. :raw-html:`<br />`

----

.. code-block:: luau  

   DRMManager.OwnsGamePass(gamepassID:number) -> bool

Check if the player own a gamepass. :raw-html:`<br />`
``gamepassID`` The ID to the gamepass. :raw-html:`<br />`

----







LEFCharEncode
==========

.. code-block:: luau  

   LEFCharEncode.Encrypt(Text:string) -> bool

Encrypts a string so it can be saved/written to a file. :raw-html:`<br />`
``Text`` The string you want to encrypt. :raw-html:`<br />`

----

.. code-block:: luau  

   LEFCharEncode.Decrypt(Text:string) -> bool

Decrypts an encrypted string. :raw-html:`<br />`
``Text`` The string you want to decrypt. :raw-html:`<br />`

----







ExecutableHost
==========

.. code-block:: luau  

    ExecutableHost.readlef(data:string) -> number

This function reads LEF files

----

.. code-block:: luau  

    ExecutableHost.createlef(code:string, admin:bool, publisher:string, env:table) -> string

This function creates new LEF files

----

.. code-block:: luau  

    ExecutableHost.createlefraw(code:string, admin:bool, publisher:string) -> string

This function creates new LEF files

----

.. code-block:: luau  

    ExecutableHost.selftest() -> number

``nil``

----








Executor
==========

.. code-block:: luau  

  Executor.compile(source, env, strip) -> number

``nil``

----

.. code-block:: luau  

  Executor.run(compiled, env, strip) -> number

``nil``

----

.. code-block:: luau  

  Executor.innerCompile(source, env, strip) -> number

``nil``

----

.. code-block:: luau  

  Executor.innerRun(compiled, env, strip) -> number

``nil``

----







Http
==========

.. code-block:: luau  

    Http.HttpGet(url, nocache, headers, contentType, requestType) -> unknown

This function makes http Get requests

----

.. code-block:: luau  

    Http.HttpPost(url, data, content_type, compress, headers) -> unknown

This function makes http Post requests

----

.. code-block:: luau  

    Http.JSONEncode(data:table) -> string

This function JSON encodes tables to strings and returns them

----

.. code-block:: luau  

    Http.JSONDecode(data:string) -> table

This function JSON decodes JSON encoded tables and returns a table

----








EnvTable
==========

.. code-block:: luau  

    EnvTable.nil() -> nil

``nil``

----

