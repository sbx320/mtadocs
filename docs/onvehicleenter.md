This event is triggered when a player enters a vehicle.

Parameters
----------

``` lua
player thePlayer, int seat, player jacked
```

-   **thePlayer**: A player element representing the player who is entering the vehicle
-   **seat**: An integer representing the seat in which the player is entering. Seat 0 is the driver's seat.
-   **jacked**: A player element representing a player who has been jacked

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [vehicle](/docs/vehicle.md "wikilink") that was entered.

Example
-------

**Example 1:** This example forces a player out of a police vehicle if he is not a policeman.

``` lua
policeVehicles = { [598]=true, [596]=true, [597]=true, [599]=true }
policeSkins = { [280]=true, [281]=true, [282]=true, [283]=true, [284]=true, [285]=true, [286]=true }

function enterVehicle ( thePlayer, seat, jacked ) -- when a player enters a vehicle
    if ( policeVehicles[getElementModel ( source )] ) and ( not policeSkins[getElementModel ( thePlayer )] ) then -- if the vehicle is one of 4 police cars, and the skin is not a police skin
        removePedFromVehicle ( thePlayer ) -- force the player out of the vehicle
        outputChatBox ( "Only policeman can enter police cars!", thePlayer ) -- and tell the player why
    end
end
addEventHandler ( "onVehicleEnter", getRootElement(), enterVehicle ) -- add an event handler for onVehicleEnter
```

**Example 2:** This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off (only works with players using CJ skin).

``` lua
function addHelmetOnEnter ( thePlayer, seat, jacked )
    if ( getElementModel ( source ) == 522 ) then -- if its a nrg
        addPedClothes ( thePlayer, "moto", "moto", 16 ) -- add the helmet
    end
end
addEventHandler ( "onVehicleEnter", getRootElement(), addHelmetOnEnter )

function removeHelmetOnExit ( thePlayer, seat, jacked )
    if ( getElementModel ( source ) == 522 ) then -- if its a nrg
        removePedClothes ( thePlayer, 16 ) -- remove the helmet
    end
end
addEventHandler ( "onVehicleExit", getRootElement(), removeHelmetOnExit )
```
