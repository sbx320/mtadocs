This function tells you how open a door is (the 'open ratio'). Doors include boots/trunks and bonnets on vehicles that have them.

Syntax
------

``` lua
float getVehicleDoorOpenRatio ( vehicle theVehicle, int door )
```

Required Arguments
------------------

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you wish to get the door open ratio of.
-   **door:** A whole number, 0 (hood), 1 (trunk), 2 (front left), 3 (front right), 4 (rear left), 5 (rear right)

Returns
-------

Returns a number between 0 and 1 that indicates how open the door is. 0 is closed, and 1 is fully open. Returns *false* if invalid arguments are passed.

Example
-------

This example opens all the doors of the vehicle gradually over 2.5 seconds.

``` lua
addCommandHandler ( "carshowoff", function ( playerSource )
    local vehicle = getPedOccupiedVehicle ( playerSource )
    if vehicle then
        for i=0,5 do
            setVehicleDoorOpenRatio ( vehicle, i, 1 - getVehicleDoorOpenRatio ( vehicle, i ), 2500 )
        end
    end
end )
```

See Also
--------
