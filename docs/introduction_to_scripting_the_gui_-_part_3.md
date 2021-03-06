**Introduction to Scripting the GUI - Part 3 (Teleport Window)**

In this tutorial we will make a simple city teleport window, with 3 buttons (one for each city) that when clicked will teleport you to that city.

**Note that this tutorial builds on content covered in the [GUI Scripting Introduction](/docs/introduction_to_scripting_the_gui.md "wikilink").**

[thumb|GUI Teleport Window](/docs/image:gui_teleport_tutorial.png.md "wikilink")

Making the GUI
--------------

### Getting set up

The first thing we need to do is create our GUI elements. For this tutorial we will be using one [window](/docs/element/gui/window.md "wikilink"), three [buttons](/docs/element/gui/button.md "wikilink") and one [label](/docs/element/gui/text_label.md "wikilink"). We will be using **absolute** position values.

As noted in [Previous tutorials](/docs/:category:gui_tutorials.md "wikilink"), all the GUI must be made client side.

If you are following on from that tutorial, open up your gui.lua file to work with.

If you are not, browse to /Your MTA Server/mods/deathmatch/resources/myserver/ directory, and create a folder named “client”. Under /client/ directory, create a text file and name it “gui.lua”.

If you have not already done so, do not forget to include the new gui.lua file in the meta.xml of the main resource, and label it as a client script:

``` xml
<script src="client/gui.lua" type="client" />
```

### Making the window

In this file we will now write a funtion that creates the window. To create a window we will use [guiCreateWindow](/docs/guicreatewindow.md "wikilink"):

``` lua
-- create the function that will hold our gui creation code
function createTeleportWindow()
    -- get the screen width and height
    local sWidth, sHeight = guiGetScreenSize()
 
    -- create the window, using some maths to find the centre of the screen
    local Width,Height = 231,188
    local X = (sWidth/2) - (Width/2)
    local Y = (sHeight/2) - (Height/2)
 
    -- create the window
    teleportWindow = guiCreateWindow(X,Y,Width,Height,"City Teleporter",false)
 
    -- stop players from being able to resize the window
    guiWindowSetSizable(teleportWindow,false)
end
```

This will create a basic window in the centre of the screen that cannot be resized, with the title “City Teleporter”.

### Making the label

Next, we will add the label describing what the buttons do. To create a label we will use [guiCreateLabel](/docs/guicreatelabel.md "wikilink"):

**Note that we are now writing more code for our existing 'createTeleportWindow' function. This is not a new function and is meant to replace what you already have.**

``` lua
function createTeleportWindow()
    local sWidth, sHeight = guiGetScreenSize()
 
    local Width,Height = 231,188
    local X = (sWidth/2) - (Width/2)
    local Y = (sHeight/2) - (Height/2)
 
    teleportWindow = guiCreateWindow(X,Y,Width,Height,"City Teleporter",false)
 
    guiWindowSetSizable(teleportWindow,false)
    
    -- create a label with our instructions on
    teleportLabel = guiCreateLabel(18,23,191,33,"Click a button to teleport to that location",false,teleportWindow)
    
    -- set the horizontal alignment of the label to center (ie: in the middle of the window)
    -- also note the final argument "true" 
    -- this turns on wordwrap so if your text goes over the edge of the label, it will wrap around and start a new line automatically
    guiLabelSetHorizontalAlign(teleportLabel,"center",true) 
end
```

You will now have a simple window with some centered instructions at the top.

### Making the buttons

Now we need to add the city teleport buttons. To create a button we will use [guiCreateButton](/docs/guicreatebutton.md "wikilink"):

**Note that we are now writing more code for our existing 'createTeleportWindow' function. This is not a new function and is meant to replace what you already have.**

``` lua
function createTeleportWindow()
    local sWidth, sHeight = guiGetScreenSize()
 
    local Width,Height = 231,188
    local X = (sWidth/2) - (Width/2)
    local Y = (sHeight/2) - (Height/2)
 
    teleportWindow = guiCreateWindow(X,Y,Width,Height,"City Teleporter",false)
 
    guiWindowSetSizable(teleportWindow,false)
    
    teleportLabel = guiCreateLabel(18,23,191,33,"Click a button to teleport to that location",false,teleportWindow)
    
    guiLabelSetHorizontalAlign(teleportLabel,"center",true) 
    
    -- create the button for teleporting to Los Santos
    teleportButtonLS = guiCreateButton(18,63,195,35,"Los Santos",false,teleportWindow)
    
    -- slightly below that, create another button for teleporting to San Fierro
    teleportButtonSF = guiCreateButton(18,103,195,35,"San Fierro",false,teleportWindow)
    
    -- slightly below that again, create another button for teleport to Las Venturas
    teleportButtonLV = guiCreateButton(18,143,195,35,"Las Venturas",false,teleportWindow)   
    
    -- hide the gui
    guiSetVisible(teleportWindow,false)
end
```

### Using the function we wrote

Now our 'createTeleportWindow' function is ready, but it wont do anything until we call it. It is recommended to create all GUI when the client resource starts, hide them, and show them to the player later when needed.

Therefore, we'll write an event handler for [onClientResourceStart](/docs/onclientresourcestart.md "wikilink") to create the window:

``` lua
-- add our event handler, using the root element of the resource
-- this means it will only trigger when its own resource is started
addEventHandler("onClientResourceStart", getResourceRootElement(getThisResource()), 
    function ()
        -- call the createTeleportWindow function to create our gui
        createTeleportWindow()
    end
)
```

Now that we have our GUI created, we need a way for the players to open the window.

### Opening the GUI

There are several ways this could be done, depending on your personal preference or the particulars of the situation. For this tutorial, we will use a simple [command](/docs/addcommandhandler.md "wikilink").

To open the GUI, we will use the command /teleportme :

``` lua
-- create our function
function openTeleportWindow()
    -- show the window
    guiSetVisible(teleportWindow,true)
        
    -- show the mouse cursor
    showCursor(true,true)
end

-- define the command /teleportme to call the openTeleportWindow function
addCommandHandler("teleportme",openTeleportWindow)
```

Next, we need to make the buttons actually teleport the player.

Scripting the button
--------------------

Now that we have created our GUI and the players are able to open it, we need to make it work.

### Detecting the click

As described in previous tutorials, when the player clicks on any part of the GUI, the event “onClientGUIClick” will be triggered for the GUI component you clicked on. With that in mind, we will attach an event handler to each of our 3 teleport buttons:

``` lua
-- attach the event onClientGUIClick to teleportButtonLS and set it to trigger the 'teleportPlayer' function
addEventHandler("onClientGUIClick", teleportButtonLS, teleportPlayer, false)

-- attach the event onClientGUIClick to teleportButtonSF and set it to trigger the 'teleportPlayer' function
addEventHandler("onClientGUIClick", teleportButtonSF, teleportPlayer, false)

-- attach the event onClientGUIClick to teleportButtonLV and set it to trigger the 'teleportPlayer' function
addEventHandler("onClientGUIClick", teleportButtonLV, teleportPlayer, false)
```

Put this code into your 'createTeleportWindow' function, **after** the buttons have been created.

Note how we have set all 3 buttons to trigger the 'teleportPlayer' function.

This allows us to easily expand our code later on (for example, to add more teleport locations) with a simple if statement in the function.

### Managing the clicks

Now that we can detect clicks on all our buttons, we need to manage what happens when we do.

As we just noted, we will do this using the 'teleportPlayer' function. We will use if statements to check which button has been clicked, then trigger a custom server event with the specified teleport coordinates to move the player:

``` lua
-- create our function, and add button and state parameters (these are passed automatically with onClickGUIClick)
function teleportPlayer(button,state)
    -- if our button was clicked with the left mouse button, and the state of the mouse button is up
    if button == "left" and state == "up" then
        -- if the player clicked on the LS teleport button
        if source == teleportButtonLS then
        
            -- trigger the server with our Los Santos coordinates
            triggerServerEvent("movePlayerToPosition",getLocalPlayer(),1479.6,-1612.8,14.0,0)
            
            -- output a message to the player
            outputChatBox("Welcome to Los Santos!")
            
        -- otherwise, if the player clicked on the SF teleport button
        elseif source == teleportButtonSF then
        
            -- trigger the server with our San Fierro coordinates
            triggerServerEvent("movePlayerToPosition",getLocalPlayer(),-2265.5,534.0,35.0,270)

            -- output a message to the player
            outputChatBox("Welcome to San Fierro!")
            
        -- otherwise, if the player clicked on the LV teleport button
        elseif source == teleportButtonLV then
        
            -- trigger the server with our Las Venturas coordinates
            triggerServerEvent("movePlayerToPosition",getLocalPlayer(),2036.9,1545.2,10.8,270)

            -- output a message to the player
            outputChatBox("Welcome to Las Venturas!")
            
        end
        
        -- hide the window and all the components
        guiSetVisible(teleportWindow, false)
        
        -- hide the mouse cursor
        showCursor(false)       
    end 
end
```

If you wanted to add more locations, you could simply add a new button to your GUI and check for it in this function using another if statement. For example:

``` lua
function teleportPlayer(button,state)
    if button == "left" and state == "up" then
        ...
        
        elseif source == yourNewButton then
            triggerServerEvent("movePlayerToPosition",getLocalPlayer(),xCoord,yCoord,zCoord,rotation)
        end
        ...
    end
end
```

### Creating the serverside event

At this point we now have all the code needed on the client side, so open up your serverside 'script.lua' file (from the [Introduction to Scripting](/docs/scripting_introduction.md "wikilink")) or another suitable serverside file to work with.

On the clientside, we are triggering the server event “movePlayerToPosition”. So, we will first define that event. To do that we will use [addEvent](/docs/addevent.md "wikilink"), then [addEventHandler](/docs/addeventhandler.md "wikilink"):

``` lua
-- create our function, with the x,y and z values we passed from the client
function moveThePlayer(x,y,z)

end

-- define our custom event, and allow it to be triggered from the client ('true')
addEvent("movePlayerToPosition",true)
-- add an event handler so that when movePlayerToPosition is triggered, the function moveThePlayer is called
addEventHandler("movePlayerToPosition",root,moveThePlayer)
```

### Moving the player

Now all that is left is to move the player to their new position.

**Note that we are now writing more code for our existing 'moveThePlayer' function. This is not a new function and is meant to replace what you already have.**

``` lua
-- create our function, with the x,y and z values we passed from the client
function moveThePlayer(x,y,z,rotation)
    -- check we have a position and rotation
    if x and y and z and rotation then
        -- get the players current skin, so we can spawn them again without losing it
        local skin = getElementModel(client)
        
        -- spawn the player
        spawnPlayer(client,x,y,z,rotation,skin)
        
        -- make sure the players camera is on his character
        setCameraTarget(client,client)
    end
end
```

Note the use of [spawnPlayer](/docs/spawnplayer.md "wikilink") rather than, for example, [setElementPosition](/docs/setelementposition.md "wikilink"). Using [spawnPlayer](/docs/spawnplayer.md "wikilink") has several advantages, such as being able to set the position when 'de-spawned' or dead, and automatically refilling health. Of course, [setElementPosition](/docs/setelementposition.md "wikilink") would work just as well to simply move them, so the choice is yours.

Also note the use of the variable “client”, it's an internal variable used by MTA to identify the player who triggered the event.

At this point, you should have a basic teleport window, allowing the player to teleport to any of the 3 major cities in San Andreas.

For further help with GUI, see the [GUI tutorials](/docs/:category:gui_tutorials.md "wikilink").

[Category:GUI\_Tutorials](/docs/category:gui_tutorials.md "wikilink")
