==========
Module API
==========
To use these modules and the function in them load them *loadlib()*.

----

FileSystem
==========

.. code-block:: luau  

  table FileSystem.GetPartitions()

This function 

----

.. code-block:: luau  

  string FileSystem.GetOSDriveLetter()

This function 

----

.. code-block:: luau  

  table FileSystem.GetPartitionByIndex(index:number)

This function 

----

.. code-block:: luau  

  table FileSystem.GetPartitionByName(name:string)

This function 

----

.. code-block:: luau  

  table FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool)

This function 

----

.. code-block:: luau  

  bool FileSystem.DelPartition(partition:string)

This function 

----

.. code-block:: luau  

  table FileSystem.CheckPartitionSize(partition:string, Data:table)

This function 

----

.. code-block:: luau  

  table FileSystem.GetUserPermissions(user:string)

This function 

----

.. code-block:: luau  

  bool FileSystem.CheckPermissions(path:string, user:string, permissiontype:string)

This function 

----

.. code-block:: luau  

  number FileSystem.CalculateObjectSize(path:string)

This function 

----

.. code-block:: luau  

  bool FileSystem.FileExists(path:string)

This function 

----

.. code-block:: luau  

  table FileSystem.GetFile(path:string)

This function 

----

.. code-block:: luau  

  table FileSystem.GetFiles(path:string)

This function 

----

.. code-block:: luau  

  bool FileSystem.WriteFile(path:string, data:, user:string)

This function 

----

.. code-block:: luau  

  table FileSystem.CreateFile(path:string, type:string, permissions:string, Owner:string)

This function 

----

.. code-block:: luau  

  table FileSystem.CreateDirectory(path:string, permissions:string, Owner:string)

This function 

----

.. code-block:: luau  

  table FileSystem.DeleteObject(path:string, user:string)

This function 

----

.. code-block:: luau  

  bool FileSystem.HasAttribute(path:string, attribute:string)

This function 

----

.. code-block:: luau  

  table FileSystem.SetAttribute(path:string, attribute:string)

This function 

----

.. code-block:: luau  

  string FileSystem.RemoveLastItemOfPath(path:string)

This function 

----

.. code-block:: luau  

  string FileSystem.GetFinalObjectName(path:string)

This function 

----

.. code-block:: luau  

  string FileSystem.GetFileExtension(path:string, idk)

This function 

----

.. code-block:: luau  

  string FileSystem.RemoveCharacterFromPathEnd(path:string, chartoremove:string)

This function 

----

.. code-block:: luau  

  string FileSystem.RemoveFileNameNotAllowedCharacters(path:string)

This function 

----
