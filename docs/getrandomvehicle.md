This function returns a random [vehicle](/docs/vehicle.md "wikilink") between every vehicle created.

Syntax
------

``` lua
vehicle getRandomVehicle( )
```

### Returns

It returns a random [vehicle](/docs/vehicle.md "wikilink") if possible. If not, it returns *false*.

Code
----

``` lua
function getRandomVehicle( )
    local vehicles = getElementsByType "vehicle"
    local numberOfVehs = #vehicles

    if numberOfVehs == 0 then
        return false
    end

    return vehicles[ math.random( 1, numberOfVehs ) ]
end
```

**Original function made by**: Abdul KariM

Examples
--------

<section name="Client and server examples" class="both" show="true">
This example adds a */warptoveh* command which warps the player who types it to a random car.

``` lua
addCommandHandler( "warptoveh",
    function ( player )
        local isServer = isElement( player )
        local success

        -- If we are on the server side, get a random car and warp the player to it
        if isServer then
            local veh = getRandomVehicle( )
            if veh then
                success = warpPedIntoVehicle( player, veh )
            end
        else
            local veh = getRandomVehicle( )
            if veh then
                -- Discard clientside only vehicles we can't warp to
                -- In the strange case that there are no server vehicles MTA will abort the loop after a bit
                while isElementLocal( veh ) do
                    veh = getRandomVehicle( )
                end
                success = warpPedIntoVehicle( localPlayer, veh )
            end
        end
        
        -- Tell the player what we did
        outputChatBox( success and "You have been warped to a random vehicle." or "Could not warp you to a random vehicle.", isServer and player or ( success and 0 or 255 ), isServer and ( success and 0 or 255 ) or ( success and 255 or 0 ), isServer and ( success and 255 or 0 ) or 0, isServer and 0 or nil )
    end
)
```

This example adds a */blowveh* command to blow a random vehicle.

``` lua
addCommandHandler( "blowveh",
    function ( player )
        local veh = getRandomVehicle( )
        local success
        if veh then
            success = blowVehicle( veh )
        end
        
        -- Tell the player what we did
        local isServer = isElement( player )
        outputChatBox( success and "A random vehicle has been blown!" or "Could not blow a random vehicle.", isServer and player or ( success and 0 or 255 ), isServer and ( success and 0 or 255 ) or ( success and 255 or 0 ), isServer and ( success and 255 or 0 ) or 0, isServer and 0 or nil )
    end
)
```

</section>
See also
--------
