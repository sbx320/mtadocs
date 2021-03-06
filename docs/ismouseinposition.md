<lowercasetitle/>

This function allows you to check whether the mouse cursor/pointer is within a rectangular position

Syntax
------

``` lua
bool isMouseInPosition ( int x, int y, int width, int height )
```

### Required arguments

-   **x**: Left-most X position for detection (absolute)
-   **y**: Top-most Y position for detection (absolute)
-   **width**: Width for detection (absolute)
-   **heigh**: Height for detection (absolute)

### Return

Returns true/false depending on whether the mouse is within the specified position or not

Code
----

``` lua
    function isMouseInPosition ( x, y, width, height )
    if ( not isCursorShowing ( ) ) then
        return false
    end
 
    local sx, sy = guiGetScreenSize ( )
    local cx, cy = getCursorPosition ( )
    local cx, cy = ( cx * sx ), ( cy * sy )
    if ( cx >= x and cx <= x + width ) and ( cy >= y and cy <= y + height ) then
        return true
    else
        return false
    end
end

-- Modified version for DX Text
function isCursorOverText(posX, posY, sizeX, sizeY)
    if(isCursorShowing()) then
        local cX, cY = getCursorPosition()
        local screenWidth, screenHeight = guiGetScreenSize()
        local cX, cY = (cX*screenWidth), (cY*screenHeight)
        if(cX >= posX and cX <= posX+(sizeX - posX)) and (cY >= posY and cY <= posY+(sizeY - posY)) then
            return true
        else
            return false
        end
    else
        return false    
    end
end
```

Example
-------

<section name="Example" class="client" show="true">
Changes the image when you move your cursor over it.

``` lua
    addEventHandler ( "onClientRender", root,
    function ( )
        local imgX, imgY, imgWidth, imgHeight = 50, 50, 200, 200
        dxDrawImage ( imgX, imgY, imgWidth, imgHeight, ( isMouseInPosition ( imgX, imgY, imgWidth, imgHeight ) and "myImage2.png" or "myImage.png" ), tocolor ( 255, 255, 255 ) )
    end
)
```

</section>
Author: Castillo

See Also
--------
