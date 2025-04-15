=================
Custom Terminal Commands
=================

.. role:: raw-html(raw)
    :format: html

Here you can learn how to create custom commands for the Terminal.

In LimeOS 3.2 and above you can create your own Terminal commands, heres how you can do that! :raw-html:`<br />` 
LimeOS commands are stored in form of ``.bin`` files in the ``/root/bin/`` folder. :raw-html:`<br />` 
They also have ``.meta`` files, metadata files store some info about the command, like the text that gets displayed when you type ``help`` :raw-html:`<br />` 
:raw-html:`<br />` 

Creating Terminal Commands
--------------------------

First lets see how we can make our command file, for this example we create a command that creates a file at a given path. :raw-html:`<br />` 

.. code-block:: luau 

  local FileSystem = loadlib("FileSystem") -- Load the FileSystem module
  local input = args -- Gets the args that where used with the command

  FileSystem.CreateFile(input[1], "", "R-W-D") -- Creates a file at the given path

  print("Command executed\n") -- prints to the Terminal

Thats it, a very simple Terminal command! :raw-html:`<br />` 

Now you need to save that script as a ``.bin`` inside this dir ``/root/bin/``. The name of the command is the file name.

Creating Meta Files
-------------------

The last thing needed is the ``.meta`` file, heres a script to generate a ``.meta`` file. :raw-html:`<br />` 
Just fill out the ``MetaData`` table and ``CommandName``, then run it in the script editor. :raw-html:`<br />` 

.. code-block:: luau 

  local Http = loadlib("Http")
  local FileSystem = loadlib("FileSystem")
  local MetaData = {
    Help = "", -- The help text for the help command
    Visible = true, -- Is the command visible to the help command?
  }
  local CommandName = "" -- Needs to be the same as the command name / .bin file name
        
  FileSystem.CreateFile(FileSystem.GetOSDriveLetter()..":/root/bin/meta/"..CommandName..".meta", "metadata", "R-W-D") -- Creates the .meta file
  FileSystem.WriteFile(FileSystem.GetOSDriveLetter()..":/root/bin/meta/"..CommandName..".meta", Http.JSONEncode(MetaData)) -- writes the metadata to the file

And now you have your own working Terminal Command! :raw-html:`<br />` 