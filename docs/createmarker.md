This function creates a marker. A marker is a 3D model in the world that can highlight a particular point or area, often used to instruct players where to go to perform actions such as entering buildings.

There are various limits that govern the maximum number of each type that can be visible at once. These are:

-   Coronas: 32
-   Checkpoints, Rings, Cylinders and Arrows combined: 32

You are able to create as many markers as you wish (memory and element limit permitting), but the player will only be able to see the nearest ones up to the limit.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
marker createMarker ( float x, float y, float z [, string theType = "checkpoint", float size = 4.0, int r = 0, int g = 0, int b = 255, int a = 255, visibleTo = getRootElement( ) ] )
```

### Required Arguments

-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.

### Optional arguments

-   **theType**: The visual type of the marker to be created. Possible values:

-   **size**: The diameter of the marker to be created, in meters.
-   **r**: An integer number representing the amount of red to use in the colouring of the marker (0 - 255).
-   **g**: An integer number representing the amount of green to use in the colouring of the marker (0 - 255).
-   **b**: An integer number representing the amount of blue to use in the colouring of the marker (0 - 255).
-   **a**: An integer number representing the amount of alpha to use in the colouring of the marker (0 - 255 where 0 is transparent and 255 is opaque).
-   **visibleTo**: This defines which elements can see the marker. Defaults to visible to everyone. See [visibility](/docs/visibility.md "wikilink").

</section>
<section name="Client" class="client" show="true">
``` lua
marker createMarker ( float x, float y, float z [, string theType = "checkpoint", float size = 4.0, int r = 0, int g = 0, int b = 255, int a = 255 ] )
```

### Required Arguments

-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.

### Optional arguments

-   **theType**: The visual type of the marker to be created. Possible values:

-   **size**: The diameter of the marker to be created, in meters.
-   **r**: An integer number representing the amount of red to use in the colouring of the marker (0 - 255).
-   **g**: An integer number representing the amount of green to use in the colouring of the marker (0 - 255).
-   **b**: An integer number representing the amount of blue to use in the colouring of the marker (0 - 255).
-   **a**: An integer number representing the amount of alpha to use in the colouring of the marker (0 - 255 where 0 is transparent and 255 is opaque).

</section>
### Returns

Returns the [marker](/docs/marker.md "wikilink") element that was created, or *false* if the arguments are incorrect.

Example
-------

<section name="Example 1" class="server" show="true">
This example creates a marker next to the player when they type 'createmarker':

``` lua
-- this function is called whenever someone types 'createmarker' in the console:
function consoleCreateMarker ( thePlayer, commandName )
   if ( thePlayer ) then
      local x, y, z = getElementPosition ( thePlayer ) -- get the player's position
      -- create a cylindrical marker next to the player:
      local theMarker = createMarker ( x + 2, y + 2, z, "cylinder", 1.5, 255, 255, 0, 170 )
      if ( theMarker ) then -- check if the marker was created successfully
         outputConsole ( "Marker created successfully", thePlayer )
      else
         outputConsole ( "Failed to create marker", thePlayer )
      end
   end
end
addCommandHandler ( "createmarker", consoleCreateMarker )
```

</section>
See Also
--------

[ru:createMarker](/docs/ru:createmarker.md "wikilink") [ar:createMarker](/docs/ar:createmarker.md "wikilink")
