The Basics
==========

Here are some small code examples which you can use in your projects

.. role:: raw-html(raw)
    :format: html

----

Creating an App
---------------

To create an app we only need the :doc:`Built-in`
 
.. code-block:: luau  

  local App = Lime.CreateWindow("Appname") -- Change Appname to the name of your app, but leave the ""
  -- Here we create an App and store it in the "App" variable so we can use it later
  -- You can also add an IconId after the Appname, but that is optional

Now we have an empty window, but thats boring, so lets add some Ui!

.. code-block:: luau  

  local TextLabel = Lime.CreateUI(App, "TextLabel") -- Change the TextLable to something else to create other UI objects, you can find a list of them on the Roblox API website
  -- This creates a TextLabel and places it inside of your App
  -- Now lets edit our new TextLabel

  TextLabel.Text = "Hello, World!"
  TextLabel.BackgroundTransparency = 1
  TextLabel.Size = UDim2.new(0.5, 0, 0.2, 0)
  TextLabel.TextScaled = true
  TextLabel.TextColor3 = Color3.fromRGB(255,255,255)
  TextLabel.Position = UDim2.new(0.25, 0, 0.4, 0)

Now we have our first App! :raw-html:`<br />` 
Heres the complete code without the comments :raw-html:`<br />` 

.. code-block:: luau  

  local App = Lime.CreateWindow("Appname")
  
  local TextLabel = Lime.CreateUI(App, "TextLabel")
  TextLabel.Text = "Hello, World!"
  TextLabel.BackgroundTransparency = 1
  TextLabel.Size = UDim2.new(0.5, 0, 0.2, 0)
  TextLabel.TextScaled = true
  TextLabel.TextColor3 = Color3.fromRGB(255,255,255)
  TextLabel.Position = UDim2.new(0.25, 0, 0.4, 0)

----

Using other Modules
-------------------

Another important part of App development is storing or reading data from the :doc:`FileSystem API <Module APIs>`. :raw-html:`<br />` 
To use the non builtin modules we first need to load them with ``loadlib()`` , so lets do that :raw-html:`<br />` 

.. code-block:: luau  

  local FileSystem = loadlib("FileSystem") -- Here we load and strore the FileSystem module
  local AccountManager = loadlib("AccountManager") -- Here we load and strore the AccountManager module
  local NotificationManager = loadlib("NotificationManager") -- Here we load and strore the NotificationManager module

Now that we have acess to the functions of the FileSystem module we can modify our newly created app

.. code-block:: luau  

  local App = Lime.CreateWindow("Appname")
   
  local TextButton = Lime.CreateUI(App, "TextButton") -- Editing this to a TextButton
  TextButton.Text = "Press Me!" -- Changing the text
  TextButton.BackgroundTransparency = 1
  TextButton.Size = UDim2.new(0.5, 0, 0.2, 0)
  TextButton.TextScaled = true
  TextButton.TextColor3 = Color3.fromRGB(255,255,255)
  TextButton.Position = UDim2.new(0.25, 0, 0.4, 0)

Now that we have a TextButton, we can make it do things. :raw-html:`<br />` 
When we press the button we'll create a .txt file in the users directory and send a Notification that the file has been created. :raw-html:`<br />` 

.. code-block:: luau  

  TextButton.MouseButton1Click:Connect(function() -- This function runs once our TextButton has been pressed
    local OSDriveLetter = FileSystem.GetOSDriveLetter() -- Here we get the drive letter that LimeOS has been installed on, cause that can chnage
    local CurrentUser = AccountManager.GetCurrentUser() -- Here we get the currently loggedin user
    local FileName = "Tutorial File.txt" -- You can change this to anything
    local FilePath = OSDriveLetter..":/users/"..CurrentUser.."/"..FileName

    FileSystem.CreateFile(FilePath, "txt", "R-W") -- Here we create our File and set some properties, like the permissions
    FileSystem.WriteFile(FilePath, "This is some data for the file!") -- Here we add some data to the file

    NotificationManager.SendNotification("Tutorial", "New File created!") -- Send a notification that a file was created
  end)

Now lets put everthing together

.. code-block:: luau 

  local FileSystem = loadlib("FileSystem")
  local AccountManager = loadlib("AccountManager")
  local NotificationManager = loadlib("NotificationManager")
  local App = Lime.CreateWindow("Appname")
     
  local TextButton = Lime.CreateUI(App, "TextButton")
  TextButton.Text = "Press Me!"
  TextButton.BackgroundTransparency = 1
  TextButton.Size = UDim2.new(0.5, 0, 0.2, 0)
  TextButton.TextScaled = true
  TextButton.TextColor3 = Color3.fromRGB(255,255,255)
  TextButton.Position = UDim2.new(0.25, 0, 0.4, 0)
  
  TextButton.MouseButton1Click:Connect(function()
    local OSDriveLetter = FileSystem.GetOSDriveLetter()
    local CurrentUser = AccountManager.GetCurrentUser()
    local FileName = "Tutorial File.txt"
    local FilePath = OSDriveLetter..":/users/"..CurrentUser.."/"..FileName

    FileSystem.CreateFile(FilePath, "txt", "R-W")
    FileSystem.WriteFile(FilePath, "This is some data for the file!")

    NotificationManager.SendNotification("Tutorial", "New File created!")
  end)

Advanced functions
==================

Creating Terminal Commands
--------------------------

In LimeOS 3.2 and above you can create your own Terminal commands, heres how you can do that! :raw-html:`<br />` 
LimeOS commands are stored in form of ``.bin`` files in the ``/root/bin/`` folder. :raw-html:`<br />` 
They also have ``.meta`` files, metadata files store some info about the command, like the text that gets displayed when you type ``help`` :raw-html:`<br />` 
:raw-html:`<br />` 
First lets see how we can make our command file, for this example we create a command that creates a file at a given path. :raw-html:`<br />` 

.. code-block:: luau 

  local FileSystem = loadlib("FileSystem") -- Load the FileSystem module
  local input = args -- Gets the args that where used with the command

  FileSystem.CreateFile(input[1], "", "R-W-D") -- Creates a file at the given path

  print("Command executed\n") -- prints to the Terminal

Thats it, a very simple Terminal command! :raw-html:`<br />` 
:raw-html:`<br />` 
Now save that script in ``/root/bin/``, the name of the file is also the name of the command. :raw-html:`<br />` 
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

Test
----

Test2
~~~~~

