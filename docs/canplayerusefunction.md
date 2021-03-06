This function can be used to check if the player can use a function, based on their current access level. Access levels for functions are stored in the server's config file. Use this if you want to prevent a player using a function unless they are logged in with enough rights.

Syntax
------

``` lua
bool canPlayerUseFunction ( player thePlayer, string functionName )
```

### Required Arguments

-   **thePlayer:** The player who you consider is running the function.
-   **functionName** The name of the function which you want to check.

### Returns

Returns *true* if the player specified can use the function specified, *false* otherwise.

Example
-------

This example adds a console function called *kill\_player* that can only be used by players with enough access rights. These access rights can be specified in the server's config file.

``` lua
function adminKillPlayer ( source, commandName, killPlayerName )
    if ( canPlayerUseFunction ( source, "kill_player" ) ) then     -- if the player can use the "kill_player" function
        local playerToKill = getPlayerFromNick ( killPlayerName )  -- look up the player to kill
        if ( playerToKill ~= false ) then                          -- check if we found him
            killPlayer ( playerToKill )                            -- if so, kill him
            outputConsole ( killPlayerName .. " has been killed!", source )   -- and notify the admin
        else
            outputConsole ( "Couldn't find a player called '" .. killPlayerName .. "'", source ) -- otherwise tell him the player was not found
        end
    else
        outputConsole ( "You do not have access to this function!", source ) -- if he isn't allowed to use the function, tell him so
    end
end
addCommandHandler ( "kill_player", adminKillPlayer )
```

See Also
--------
