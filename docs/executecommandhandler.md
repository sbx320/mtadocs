This function will call all the attached functions of an existing console command, for a specified player.

**NOTE:** You can only execute commands created by Lua. You cannot execute MTA harcoded commands due to security reasons.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 )
```

Required Arguments
------------------

-   **commandName:** The name of the command you wish to execute. This is what must be typed into the console to trigger the function.
-   **thePlayer:** The player that will be presented as executer of the command to the handler function(s) of the command.

Optional Arguments
------------------

-   **args:** Additional parameters that will be passed to the handler function(s) of the command that is called, separated by spaces.

</section>
<section name="Client" class="client" show="true">
``` lua
 )
```

Required Arguments
------------------

-   **commandName:** The name of the command you wish to execute. This is what must be typed into the console to trigger the function.

Optional Arguments
------------------

-   **args:** Additional parameters that will be passed to the handler function(s) of the command that is called, separated by spaces.

</section>
### Returns

Returns *true* if the command handler was called successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example defines a command handler for the command *createmarker* (which creates a red marker at the caller's position). It then creates a second command handler *createmarker2* which will call the first one.

``` lua
-- Define the function that will handle the 'createmarker' command
function consoleCreateMarker ( playerSource, commandName )
    -- If a player triggered it (rather than the admin) then
    if ( playerSource ) then
        -- Get that player's position
        x, y, z = getElementPosition ( playerSource )
        -- Create a marker at their position
        createMarker ( x, y, z, 0, "checkpoint", 255, 0, 0, 255 )
        -- Output it in the chat box
        outputChatBox ( "You got a red marker", playerSource )
    end
end
-- Add the function as a handler for the command
addCommandHandler ( "createmarker", consoleCreateMarker )

-- Define a second console command that will just call the first.
-- First define the function
function consoleCreateMarker2 ( playerSource, commandName )
    -- re-route back to the original
    executeCommandHandler ( "createmarker", playerSource )
end
-- Then add it as a handler for the new console command
addCommandHandler ( "createmarker2", consoleCreateMarker2 )
```

</section>
See Also
--------
