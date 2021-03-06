<lowercasetitle/>

This function allows you to get the respawn position of a specific [vehicle](/docs/vehicle.md "wikilink") element. **Note:** Please insert this code in a file that stands on the top of your meta.xml file to work correctly.

Syntax
------

``` lua
float, float, float, float, float, float getVehicleRespawnPosition( element theVehicle )
```

### Required Arguments

-   **theVehicle**: A vehicle that have been created using [createVehicle](/docs/createvehicle.md "wikilink").

### Returns

Returns 6 variables representing the vehicle's respawn position. (x, y, z, rotx, roty, rotz) If the vehicle is incorrect or the table is missing, it returns false.

Code
----

<section name="Server and Clientside script" class="both" show="true">
``` lua
local vehSpawn = {}

_createVehicle = createVehicle
_setVehicleRespawnPosition = setVehicleRespawnPosition

-- Overwrite the existing functions --
function createVehicle(id, x, y, z, rx, ry, rz, ...)
    local veh = _createVehicle(id, x, y, z, rx, ry, rz, ...)
    if(veh) then
        vehSpawn[veh] = {x, y, z, rx, ry, rz}
        return veh
    else
        return false
    end
end


function setVehicleRespawnPosition(theVehicle, ...)
    assert(vehSpawn[theVehicle], "Bad Argument @ setVehicleRespawnPosition (Vehicle respawn position does not exists)")
    vehSpawn[theVehicle] = {...}
    return _setVehicleRespawnPosition(theVehicle, ...)
end 

-- Add's the new function --
function getVehicleRespawnPosition(theVehicle)
    if(vehSpawn[theVehicle]) then
        return vehSpawn[theVehicle][1], vehSpawn[theVehicle][2], vehSpawn[theVehicle][3], vehSpawn[theVehicle][4], vehSpawn[theVehicle][5], vehSpawn[theVehicle][6]
    else
        return false
    end
end
```

</section>
Author: Noneatme

See Also
--------
