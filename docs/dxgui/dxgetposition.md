<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this function to get dxElement position.

Syntax
------

``` lua
float x, float y (float Title:x,float Title:y) dxGetPosition (element dxElement, [bool relative = false])
```

### Required Arguments

-   **dxElement:** A dxGUI element.

### Optional Arguments

-   **relative:** This is whether sizes and positioning are relative. If this is *true*, they send relative x,y,(Title:x,Title:y) positions.

### Returns

-   **x**: An element x position
-   **y**: An element y position
-   **Title:x**: An element titlebar x position.(It's for only dxWindows)
-   **Title:y**: An element titlebar y position.(It's for only dxWindows)

Example
-------

This example gets window position and multiply with 2.

``` lua
local x,y = dxGetPosition(ourWindow)
dxSetPosition(ourWindow,x*2,y*2) 
```

See Also
--------

[Back to dxGUI page](/docs/dxgui.md "wikilink")
