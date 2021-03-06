Allows you to change an object's rotation while playing a map. The object can be from the map file or created in a script.

Syntax
------

``` lua
bool setObjectRotation ( object theObject, float rotX, float rotY, float rotZ )        
```

### Required Arguments

-   **theObject:** The object to be rotated
-   **rotX:** Rotation around the X axis
-   **rotY:** Rotation around the Y axis
-   **rotZ:** Rotation around the Z axis

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

In this example, I refer to an object in the map file with the ID “pirateship”:

``` xml
<object id="pirateship" posX="-1627.319092" posY="128.543411" posZ="6.581001" rotX="-0.760854" rotY="2.421000" rotZ="0.851000" model="8493"/>
```

``` lua
function onResourceStart ( name, root )
    -- predefined variables, needed for the math code below
    rotX = 0
    rotY = 0
    rotZ = 0
    -- assign element named 'pirateship' in map file to variable
    pirateship = getElementByID ( "pirateship" )
end

function chatboxShipRotateLeft ( playerSource, commandName ) -- On console command 'increaserotations'
    outputChatBox ( "Rotational values increased" )
    -- rotations = rotations + 10
    rotX = rotX + 10
    rotY = rotY + 10
    rotZ = rotZ + 10
    -- Changed rotation is applied
    setObjectRotation ( pirateship, rotX, rotY, rotZ )
end     

function chatboxShipRotateRight ( playerSource, commandName ) -- On console command 'decreaserotations'
    outputChatBox ( "Rotational values decreased" )
    -- rotations = rotations - 10
    rotX = rotX - 10
    rotY = rotY - 10
    rotZ = rotZ - 10
    -- Changed rotation is applied
    setObjectRotation ( pirateship, rotX, rotY, rotZ )
end

-- Set up event and command handlers
addEventHandler ( "onResourceStart", resourceRoot, onResourceStart )

addCommandHandler ( "increaserotations", chatboxShipRotateLeft )
addCommandHandler ( "decreaserotations", chatboxShipRotateRight )
```

See Also
--------
