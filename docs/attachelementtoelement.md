This function attaches one element to another, so that the first one follows the second whenever it moves.

If an attempt is made to attach two elements that are already attached the opposite way (eg theElement becomes theAttachToElement and vice versa), the 1st attachment order is automatically detached in favor of the 2nd attachment order. For example, if carA was attached to carB, now carB is attached to carA. Also, an element cannot be attached to two separate elements at one time. For example, two cars can be attached to one single car, but one single car cannot be attached to two separate cars. If you attempt to do this, the existing attachment will automatically be dropped in favor of the new attachment. For example, if carA is asked to attached to carB then carC, it is only attached to carC.

This is not compatible with all elements. The following elements are compatible:

-   [Markers](/docs/Marker.md "wikilink")
-   [Blips](/docs/Blip.md "wikilink")
-   [Objects](/docs/Object.md "wikilink")
-   [Players](/docs/Player.md "wikilink")
-   [Vehicles](/docs/Vehicle.md "wikilink")

Syntax
------

``` lua
bool attachElementToElement ( element theElement, element theAttachToElement, [ float xPosOffset, float yPosOffset, float zPosOffset, float xRotOffset, float yRotOffset, float zRotOffset ] )
```

### Required Arguments

-   **theElement:** The element to be attached.
-   **theAttachToElement:** The element to attach the first to.

### Optional Arguments

-   **xPosOffset:** The x offset, if you want the elements to be a certain distance from one another (default 0).
-   **yPosOffset:** The y offset (default 0).
-   **zPosOffset:** The z offset (default 0).
-   **xRotOffset:** The x rotation offset (default 0).
-   **yRotOffset:** The y rotation offset (default 0).
-   **zRotOffset:** The z rotation offset (default 0).

### Returns

Returns *true* if the attaching process was successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This example attaches a marker to the player who steals the Mr. Whoopee:

``` lua
-- create the vehicle
local vehicleMrWhoopee = createVehicle ( 423, 237.472 -54.225 1.518, 0, 354.488, 0 )

function onMrWhoopeeEnter ( thePlayer, seat, jackedPlayer )
    outputChatBox ( getClientName ( thePlayer ) .. " stole the Whoopee!", getRootElement (), 255, 0, 0 )
    -- create the marker to attach
    local arrowMarker = createMarker ( 0, 0, 0, "arrow", .75, 255, 0, 0, 170 )
    -- attach the marker to the player with a vertical offset of 2 units
    attachElementToElement ( arrowMarker, thePlayer, 0, 0, 2 )
end

-- attach it to an event
addEventHandler ( "onVehicleEnter", vehicleMrWhoopee, onMrWhoopeeEnter )
```

**Example 2:** This function adds a tank on top of a player (for extra defense):

``` lua
function tankHat( source, commandName )
      local x, y, z = getElementPosition( source ) --Get the players position
      local tank = createVehicle( 432, x, y, z + 5 ) --Create a tank
      attachElementToElement( tank, source, 0, 0, 5 ) --Attach the tank to the player.
end
addCommandHandler( "hat", tankHat )
```

</section>
<section name="Client" class="client" show="false">
**Example 3:** This function adds a tank on top of a player (for extra defense), clientside. This means it will be invisible to other players.

``` lua
function tankHat( commandName )
      local x, y, z = getElementPosition( source ) --Get the players position
      local tank = createVehicle( 432, x, y, z + 5 ) --Create a tank
      attachElementToElement( tank, source, 0, 0, 5 ) --Attach the tank to the player.
end
addCommandHandler( "hat", tankHat )
```

</section>
See Also
--------