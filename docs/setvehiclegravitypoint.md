This clientside function sets a vehicle's gravity in the direction of a 3 dimensional coordinate with the strength specified.

Syntax
------

``` lua
bool setVehicleGravityPoint( vehicle targetVehicle, float pointX, float pointY, float pointZ, float strength )
```

### Required Arguments

-   **targetVehicle**: The vehicle you want to set the gravity of.
-   **pointX**: The X position of the gravity point.
-   **pointY**: The Y position of the gravity point.
-   **pointZ**: The Z position of the gravity point.
-   **strength**: The strength of the gravity as a multiple of the global gravity.

### Returns

Returns *true* if the function was successful, *false* otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua
function setVehicleGravityPoint( targetVehicle, pointX, pointY, pointZ, strength )
    if isElement( targetVehicle ) and getElementType( targetVehicle ) == "vehicle" then
        local vehicleX,vehicleY,vehicleZ = getElementPosition( targetVehicle )
        local vectorX = vehicleX-pointX
        local vectorY = vehicleY-pointY
        local vectorZ = vehicleZ-pointZ
        local length = ( vectorX^2 + vectorY^2 + vectorZ^2 )^0.5
        
        local propX = vectorX^2 / length^2
        local propY = vectorY^2 / length^2
        local propZ = vectorZ^2 / length^2
        
        local finalX = ( strength^2 * propX )^0.5
        local finalY = ( strength^2 * propY )^0.5
        local finalZ = ( strength^2 * propZ )^0.5
        
        if vectorX > 0 then finalX = finalX * -1 end
        if vectorY > 0 then finalY = finalY * -1 end
        if vectorZ > 0 then finalZ = finalZ * -1 end
        
        return setVehicleGravity( targetVehicle, finalX, finalY, finalZ )
    end
    return false
end
```

</section>
Example
-------

<section name="Client" class="client" show="true">
This example makes a command that will make the player's current vehicle “fall” towards 0,0,50 with 5 times the global gravity.

``` lua
function toFarm()
        setVehicleGravityPoint(getPedOccupiedVehicle(getLocalPlayer()), 0, 0, 50, 5) -- Make the vehicle "fall"
end
addCommandHandler("tofarm", toFarm, false) -- Create the tofarm command
```

</section>
Author: Cecer1

See Also
--------
