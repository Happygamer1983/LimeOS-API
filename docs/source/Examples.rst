========
Examples
========
Here are some small code examples which you can use in your projects

----

Creating an App
===============

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

Now we have our first App!
Heres the complete code without the comments

.. code-block:: luau  

  local App = Lime.CreateWindow("Appname")
  
  local TextLabel = Lime.CreateUI(App, "TextLabel")
  TextLabel.Text = "Hello, World!"
  TextLabel.BackgroundTransparency = 1
  TextLabel.Size = UDim2.new(0.5, 0, 0.2, 0)
  TextLabel.TextScaled = true
  TextLabel.TextColor3 = Color3.fromRGB(255,255,255)
  TextLabel.Position = UDim2.new(0.25, 0, 0.4, 0)

