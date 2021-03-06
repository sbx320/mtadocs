This function gets the size of a blip.

Syntax
------

``` lua
int getBlipSize ( blip theBlip )
```

### Required Arguments

-   **theBlip:** The blip you wish to get the size of.

### Returns

Returns an [int](/docs/int.md "wikilink") indicating the size of the blip. The default value is 2.

Example
-------

This example will reset the size of all blips to the default.

``` lua
-- Retrieve a table containing all the blips that exist
blips = getElementsByType ( "blip" )
-- Loop through the list, storing the blip from the table in the variable blipValue
for blipKey, blipValue in ipairs(blips) do
    -- Retrieve the blip's size into the variable 'blipSize'
    blipSize = getBlipSize ( blipValue )
    -- If the blip's size wasn't 2 (the default size) already
    if ( blipSize ~= 2 ) then
        -- Set the blip's size to the default
        setBlipSize ( blipValue, 2 )
    end
end
```

See Also
--------
