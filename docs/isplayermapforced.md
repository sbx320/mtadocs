This function checks if the specified player's radar map has been forced on or not.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool isPlayerMapForced ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** A [player](/docs/player.md "wikilink") object referencing the specified player

### Returns

Returns *true* if the player's radar map is forced on, *false* otherwise.

</section>
<section name="Client" class="client" show="true">
``` lua
bool isPlayerMapForced ()
```

### Returns

Returns *true* if the local player's radar map is forced on, *false* otherwise.

</section>
Example
-------

<section name="Server" class="server" show="true">
This example forces a players radar map on for 10 seconds if it hasn't been already.

``` lua
function forceMapForPlayer ( callingPlayer, command, whoNick )
    local who = getPlayerFromName ( whoNick )                                   -- Look up the specified player
    if ( who ) then
        if ( not isPlayerMapForced ( who ) ) then                           -- if his radar map isn't already forced on
            forcePlayerMap ( who, true )                                -- force it on
            setTimer ( forcePlayerMap, 10000, 1, who, false )           -- force it off in 10secs
            outputChatBox ( "Forcing Map for " .. whoNick, callingPlayer ) -- output a message to the one who entered the command
        else
            outputChatBox ( "Map already forced for " .. whoNick, callingPlayer ) -- if the map is already forced, output a message
        end
    else
        outputChatBox ( "Couldn't find " .. whoNick, callingPlayer )        -- if the player wasn't found, output a message
    end
end
addCommandHandler ( "forcemap", forceMapForPlayer ) -- add a command handler
```

</section>
See Also
--------
