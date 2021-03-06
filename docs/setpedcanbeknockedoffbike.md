This function controls if a ped can fall of his bike by accident - namely by banging into a wall.

Syntax
------

``` lua
bool setPedCanBeKnockedOffBike ( ped thePed, bool canBeKnockedOffBike )         
```

### Required Arguments

-   **thePed:** the ped whose knockoffstatus is being changed
-   **canBeKnockedOffBike:** *true* or *false*

Example
-------

This example adds a console command with which the local player can toggle if he can fall off bikes.

``` lua
function changeCanBeKnockedOff ( command )
    -- The player should enter /knock
    if canPedBeKnockedOffBike ( getLocalPlayer() ) then
        setPedCanBeKnockedOffBike ( getLocalPlayer(), false )
        outputChatBox ( "Now you can't be knocked off your bike." )
    else
        setPedCanBeKnockedOffBike ( getLocalPlayer(), true )
        outputChatBox ( "Now you can be knocked off your bike." )
    end
end
addCommandHandler ( "knock", changeCanBeKnockedOff )
```

See Also
--------
