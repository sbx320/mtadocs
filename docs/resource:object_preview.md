This resource lets you create an object that will be drawn on the screen provided size and position - just like when drawing an image. This way it is easy to create object preview on GUI (supports drawing in a separate render target). Works with peds, world objects and vehicles.

Overview
--------

The resource itself adds exported client-side functions:

Exported functions
------------------

#### createObjectPreview

<section name="Client" class="client" show="true">
Creates the preview for provided world,ped or vehicle element.

``` lua
)
```

### Required Arguments

-   **float rotX, rotY, rotZ:** Object rotation in camera space.
-   **float projPosX, projPosY:** Projector left corner on the screen.
-   **float projSizeX, projSizeY:** Projector size.

### Optional Arguments

-   **bool isRelative:** Are the projector parameters relative.
-   **bool postGUI:** Should the object be drawn before or after MTA GUI elements.
-   **isSecRT:** Should the object be drawin to second render target.

### Returns

The function returns the element if set successfully, 'false' otherwise.

</section>
#### destroyObjectPreview

<section name="Client" class="client" show="true">
Destroys previously created preview - without destroying the object it was applied to.

``` lua
bool exports.object_preview:destroyObjectPreview(element objectPreviewElement)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### saveRTToFile

<section name="Client" class="client" show="true">
Save render target to png file. (Only when drawing to second render target is enabled)

``` lua
bool exports.object_preview:saveRTToFile(element objectPreviewElement, string path)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **string path:** An exact client resource path the file is to be saved to.

### Returns

The function returns true if set successfully, false otherwise. It saves the image in client resource path.

</section>
#### setRotation

<section name="Client" class="client" show="true">
This function sets object rotation.

``` lua
bool exports.object_preview:setRotation(element objectPreviewElement,float rotX, rotX, rotZ)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **float rotX, rotX, rotZ:** Object rotation in camera space.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setProjection

<section name="Client" class="client" show="true">
This function sets object on screen position and size.

``` lua
)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **float projPosX, projPosY:** Projector left corner on the screen.
-   **float projSizeX, projSizeY:** Projector size.

### Optional Arguments

-   **bool isRelative:** Are the projector parameters relative.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setAlpha

<section name="Client" class="client" show="true">
This function sets object alpha transparency.

``` lua
bool exports.object_preview:setAlpha(element objectPreviewElement,int alpha)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **int alpha:** Object alpha (0 - 255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### getRenderTarget

<section name="Client" class="client" show="true">
This function returns a renderTarget (Only when drawing to second render target is enabled)

``` lua
bool exports.object_preview:getRenderTarget()
```

### Returns

The function returns render target if set successfully, false otherwise.

</section>
#### setDistanceSpread

<section name="Client" class="client" show="true">
This function sets the difference between object to camera distance set by MTA and that set by shader.

``` lua
bool exports.object_preview:setDistanceSpread(element objectPreviewElement,float zSpread)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **float zSpread:** Object Distance spread.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setPositionOffsets

<section name="Client" class="client" show="true">
This function sets object position to camera offsets (standard is 0,0,0)

``` lua
bool exports.object_preview:setPositionOffsets(element objectPreviewElement,float posX, posX, posX)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **float posX, posX, posX:** Object position to camera offsets.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setRotationOffsets

<section name="Client" class="client" show="true">
This function sets object rotation centre offsets (standard is 0,0,0)

``` lua
bool exports.object_preview:setRotationOffsets(element objectPreviewElement,float posX, posX, posX)
```

### Required Arguments

-   **element objectPreviewElement:** A previously declared preview element.
-   **float posX, posX, posX:** Object rotation centre offsets.

### Returns

The function returns true if set successfully, false otherwise.

</section>
Example
-------

``` lua
local scx, scy = guiGetScreenSize ()
local myObject,myElement, guiWindow = nil, nil, nil
local myRotation = {0,0,0}

addEventHandler("onClientResourceStart", getResourceRootElement( getThisResource()), function()
    local x1, y1, z1 = getCameraMatrix()
    myElement = createVehicle (429, x1, y1, z1)

    myObject = exports.objectPreview:createObjectPreview(myElement,0, 0, 0, 0.5, 0.5, 1, 1, true, true, true)
    guiWindow = guiCreateWindow((scx/2)-100,(scy/2) - 100,200,200, "Test area", false, false)
    guiSetAlpha(guiWindow, 0.05 + 0.2)
    local projPosX, projPosY = guiGetPosition(guiWindow,true)
    local projSizeX, projSizeY = guiGetSize(guiWindow, true)    
    exports.object_preview:setProjection(myObject,projPosX, projPosY, projSizeX, projSizeY,true,true)
    exports.object_preview:setRotation(myObject,myRotation[1], myRotation[2], myRotation[3])
    
    bindKey ( "num_4", "down", function() myRotation[1] = myRotation[1] - 5 end)
    bindKey ( "num_6", "down", function() myRotation[1] = myRotation[1] + 5 end)
    bindKey ( "num_add", "down", function() myRotation[2] = myRotation[2] - 5 end)
    bindKey ( "num_sub", "down", function() myRotation[2] = myRotation[2] + 5 end)
    bindKey ( "num_2", "down", function() myRotation[3] = myRotation[3] - 5 end)
    bindKey ( "num_8", "down", function() myRotation[3] = myRotation[3] + 5 end)
    bindKey ( "o", "down", function() exports.object_preview:saveRTToFile(myObject,math.random(100)..".png") end)
end)

addEventHandler("onClientPreRender", root, function()
    if not myElement or not myObject then return end
    local projPosX, projPosY = guiGetPosition(guiWindow,true)
    local projSizeX, projSizeY = guiGetSize(guiWindow, true)
    exports.object_preview:setProjection(myObject,projPosX, projPosY, projSizeX, projSizeY, true, true)
end, true, "high" )

addEventHandler("onClientResourceStop", getResourceRootElement( getThisResource()), function()
    exports.object_preview:destroyObjectPreview(myObject)
end
)
```

This creates a vehicle, applies object preview and scales it using dimensions of a window element.

Of course when you want to use these functions in your resources you have to include the object\_preview resource in meta.

See Also
--------

[Object Preview resource on community](https://community.multitheftauto.com/index.php?p=resources&s=details&id=11836)
