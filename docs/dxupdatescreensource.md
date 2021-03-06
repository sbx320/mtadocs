This function updates the contents of a screen source [texture](/docs/texture.md "wikilink") with the screen output from GTA

Syntax
------

``` lua
bool dxUpdateScreenSource ( element screenSource [, bool resampleNow = false ] )
```

### Required Arguments

-   **screenSource:** The screen source element whose pixels we want to fill with the screen capture

### Optional Arguments

-   **resampleNow:** A bool to indicate if the screen should be captured immediately. The default is *false* which means the screen from the end of the previous frame is used (better for performance and consistency). Use *true* for layering fullscreen effects.

### Returns

Returns *true* if the screen was successfully captured, *false* otherwise.

Example
-------

This example will update the screen capture when F7 is pressed

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myScreenSource = dxCreateScreenSource( 500, 500)    -- Create a screen source texture which is 500 x 500 pixels
    end
)

bindKey( "F7", "down", 
    function()
        if myScreenSource then
            dxUpdateScreenSource( myScreenSource )          -- Capture the screen
        end
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myScreenSource then
            dxDrawImage ( 0, 0, 300, 300, myScreenSource )  -- Draw the result in top left corner
        end
    end
)
```

Changelog
---------

See Also
--------
