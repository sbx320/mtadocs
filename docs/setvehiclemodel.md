This function changes the model of the specified vehicle. If the new vehicle model has less seats than the current model, any excess passengers will be removed from the vehicle.

Syntax
------

``` lua
bool setVehicleModel ( vehicle theVehicle, int model )
```

### Required Arguments

-   **theVehicle:** the vehicle you want to change the model of.
-   **model:** the new model you want to set.

### Returns

Returns *true* if the new model was successfully applied, *false* if it failed.

Example
-------

This very simple example that allows a player to change the vehicle he is in with a console command. In actual gamemodes the function can be used for more interesting things, like vehicle change pickups.

<section class="server" name="Server" show="true">
``` lua
addCommandHandler("changeveh",
    function(thePlayer, command, newModel)
        local theVehicle = getPlayerOccupiedVehicle(thePlayer)  -- get the vehicle the player is in
        newModel = tonumber(newModel)                           -- try to convert the string argument to a number
        if theVehicle and newModel then                         -- make sure the player is in a vehicle and specified a number
            setVehicleModel(theVehicle, newModel)
        end
    end
)
```

</section>
After the above code is executed, a player can get in any vehicle and execute e.g. the command "/changeveh 520" to change it into a hydra.

See Also
--------
