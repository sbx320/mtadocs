Syntax
------

``` lua
float, float, float getLightDirection ( light theLight )
```

### Required Arguments

-   **theLight:** The [light](/docs/element/light.md "wikilink") that you wish to retrieve the direction of.

### Returns

Returns three [ints](/docs/int.md "wikilink") corresponding to the x, y and z coordinates (respectively) of the light direction, *false* if invalid arguments were passed.

### Example

``` Lua
function()
 local light = createLight(0, 1, 0, 4)
local lx, ly, lz = getLightDirection(light)
outputChatBox("light direction: " .. lx .. ", " .. ly .. ", " .. lz)
end 
end
)
```

See also
--------
