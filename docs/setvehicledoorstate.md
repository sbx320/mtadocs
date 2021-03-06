This function sets the state of the specified door on a vehicle.

Syntax
------

``` lua
bool setVehicleDoorState ( vehicle theVehicle, int door, int state )
```

Required Arguments
------------------

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you wish to change the door state of.
-   **door:** An integer representing which door to set the state of. Valid values are:
    -   **0:** Hood
    -   **1:** Trunk
    -   **2:** Front left
    -   **3:** Front right
    -   **4:** Rear left
    -   **5:** Rear right
-   **state:** An integer representing the state to set the door to. Valid values are:
    -   **0:** Shut, intact
    -   **1:** Ajar, intact
    -   **2:** Shut, damaged
    -   **3:** Ajar, damaged
    -   **4:** Missing

Returns
-------

Returns *true* if the door state was successfully set, *false* otherwise.

Example
-------

``` lua
-- create a new vehicle
local newcar = createVehicle ( 520, 1024, 1024, 1024 )
-- break its front left door off
state = setVehicleDoorState ( newcar, 2, 4 )
```

See Also
--------
