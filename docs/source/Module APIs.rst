==========
Module API
==========
To use these modules and the function in them load them ``loadlib()``.

----

FileSystem
==========

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
