==========
FileSystem
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

The FileSystem module is responsable for the filesystem in LimeOS. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 

The LimeOS filesytem uses 4 permissions. (``R = Read, W = Write, D = Delete, and A = Admin``) :raw-html:`<br />` 
These permissions need to be formatted correctly, multible permissions are separated by a hyphen (e.g. "R-W-D").
For single permissions, simply use the corresponding letter (e.g. "R" or "D")

When a functions fails, most of them return 2 values a bool and a string, the string being an error message. :raw-html:`<br />` 
The ``:number`` is the type the function expects as input.

The LimeOS folder structure looks like this.

.. code-block:: txt  

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

These functions handle everything partition related.

GetOSDriveLetter
~~~~~~~~~~~~~~~~

.. code-block:: luau  

    FileSystem.GetOSDriveLetter() -> string

Returns the partition name where LimeOS is installed on.


GetPartitions
~~~~~~~~~~~~~

.. code-block:: luau  

    FileSystem.GetPartitions() -> table

Returns a table of all partitions in LimeOS.


GetPartitionByIndex
~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetPartitionByIndex(index:number) -> table or bool, string

Returns a partition based on an index number. :raw-html:`<br />`
``index`` The index number of a partition. (e.g., 2 will always get the 2nd partition) :raw-html:`<br />`


GetPartitionByName
~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetPartitionByName(name:string) -> table or bool, string

Returns a partition based on a string name. :raw-html:`<br />`
``name`` The name of a partition. :raw-html:`<br />`


CheckPartitionSize
~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CheckPartitionSize(partition:string, Data:table) -> bool

Retuns ``true`` when there is still space on the partition for the provided data. :raw-html:`<br />`
``partition`` The name for the to be checked partition. :raw-html:`<br />`
``Data`` The partition data. :raw-html:`<br />`


CreatePartition
~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool) -> table or bool, string

Creates a new partition table and returns it. :raw-html:`<br />`
``name`` The name of the new partition. :raw-html:`<br />`
``PartitionSize`` The partition size in MB for the new partition. :raw-html:`<br />`
``IsOSDrive`` A bool value, that marks if LimeOS is installed on that partition. :raw-html:`<br />`

.. warning::
   The ``IsOSDrive`` argument should be left at ``nil``. :raw-html:`<br />`
    


DelPartition
~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.DelPartition(partition:string) -> bool, string

Deletes a partition based on a string name. The function will return ``true`` if the deletion was successful :raw-html:`<br />`
``partition`` The name for the to be deleted partition. :raw-html:`<br />`





File OP Helper Functions
------------------------

These functions are helper functions for file operations.

CheckPermissions
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CheckPermissions(path:string, user:string, permissiontype:string) -> bool

Checks if the user has the same permissions as the provided permissions. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``permissiontype`` The permissions that will be checked for, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`

.. warning::
    The ``user`` argument should be left at ``nil``. :raw-html:`<br />`


CalculateObjectSize
~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CalculateObjectSize(path:string) -> string

Returns the KB or MB size of a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`


FileExists
~~~~~~~~~~

.. code-block:: luau  

   FileSystem.FileExists(path:string) -> bool

Checks if a file object exists based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`


GetFile
~~~~~~~

.. code-block:: luau  

   FileSystem.GetFile(path:string) -> table or bool, string

Returns a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`


GetFiles
~~~~~~~~

.. code-block:: luau  

   FileSystem.GetFiles(path:string) -> table or bool, string

Returns the files inside a directory object based on a provided path. :raw-html:`<br />`
``path`` The string path to the directory object. :raw-html:`<br />`yea





File Operation Functions
------------------------

These functions handle the normal file interactions such as creating and writing.

WriteFile
~~~~~~~~~

.. code-block:: luau  

   FileSystem.WriteFile(path:string, data:string, user:string, plaintext:bool) -> bool, string

Writes new data to a file object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``data`` The new data for the file. :raw-html:`<br />`
``user`` The name of a user. :raw-html:`<br />`
``plaintext`` A bool value that toggels file encryption, ``true`` turns the encryption off. :raw-html:`<br />`

.. warning::
    The ``user`` argument should be left at ``nil``. :raw-html:`<br />`


CreateFile
~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string) -> table or bool, string

Creates and retuns a new file object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``┗━>`` The file name is everything past the last ``/``, so ``../testfile.txt`` would have a file name of ``testfile.txt``. :raw-html:`<br />`
``type`` The file type for the file object. :raw-html:`<br />`
``permissions`` The file objects permissions, see the start of this page. :raw-html:`<br />`
``Owner`` The name for the file object owner. :raw-html:`<br />`

.. warning::
    The ``user`` argument should be left at ``nil`` unless you need to enter another User. :raw-html:`<br />`



CreateDirectory
~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CreateDirectory(path:string, permissions:string, Owner:string) -> table or bool, string

Creates and retuns a new directory object, and placing it in the provided path. :raw-html:`<br />`
``path`` The path to a directory object. :raw-html:`<br />`
``┗━>`` The directory name is everything past the last ``/``, so ``../NewDir`` would have a directory name of ``newDir``. :raw-html:`<br />`
``permissions`` The directory objects permissions, see the start of this page. :raw-html:`<br />`
``Owner`` The name for the directory object owner. :raw-html:`<br />`

.. warning::
    The ``user`` argument should be left at ``nil`` unless you need to enter another User. :raw-html:`<br />`



DeleteObject
~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.DeleteObject(path:string) -> bool, string

Delets a file or directory object based on a provided path. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`



XCopy
~~~~~

.. code-block:: luau  

   FileSystem.XCopy(path:string, newpath:string) -> bool, string

Copyies a file or dir to another location. :raw-html:`<br />`
``path`` The path to a file/dir. :raw-html:`<br />`
``newpath`` The new path for the file/dir, you can also rename the file/dir eg. ``../../NewName.txt``. :raw-html:`<br />`






Helper Functions
----------------

These functions are helper functions for the filesystem as a whole.

HasAttribute
~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.HasAttribute(path:string, attribute:string) -> bool, string

Checks if a file or directory object has a certain Attribute. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to check for. :raw-html:`<br />`



SetAttribute
~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.SetAttribute(path:string, attribute:string, action:string) -> bool, string

Updates the Attributes of a file. :raw-html:`<br />`
``path`` The path to a file object. :raw-html:`<br />`
``attribute`` The attribute you want to set/remove. :raw-html:`<br />`
``action`` If you wan to ``add`` or ``remove`` the attribute. :raw-html:`<br />`



RemoveLastItemOfPath
~~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.RemoveLastItemOfPath(path:string) -> string

Returns a modified string, where the string past the last ``/`` is cut. :raw-html:`<br />`
(e.g., "C:/System/Test" -> "C:/System") :raw-html:`<br />`
``path`` The path you want to check. :raw-html:`<br />`



GetFinalObjectName
~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetFinalObjectName(path:string) -> string

Returns a modified string, where the string before the last ``/`` is cut. :raw-html:`<br />`
(e.g., "C:/System/Test" -> "Test") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`



GetFileExtension
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetFileExtension(path:string, fileobj:table) -> string

Returns the string file extension of a provided path. :raw-html:`<br />`
(e.g., "C:/System/Test.txt" -> "txt") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`



RemoveCharacterFromPathEnd
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.RemoveCharacterFromPathEnd(path:string, chartoremove:string) -> string

Returns a modified string, where the last character is cut. :raw-html:`<br />`
(e.g., "C:/System/" -> "C:/System") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`



RemoveFileNameNotAllowedCharacters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.RemoveFileNameNotAllowedCharacters(path:string) -> string

Returns a modified string, where any non allowed characters are removed or replaced with underscores. :raw-html:`<br />`
(e.g., "Hello #World" -> "Hello_World") :raw-html:`<br />`
``path`` The path you want to modify. :raw-html:`<br />`



