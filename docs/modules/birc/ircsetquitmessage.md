This function is used to change the quit message of the specified .

Syntax
------

``` lua
bool ircSetQuitMessage ( ircbot theBot, string quitMessage )
```

### Required Arguments

-   **theBot:** The ircbot which quit message you want to change
-   **quitMessage:** The new quit message for the ircbot

### Returns

Returns *true* passed arguments were valid and quit message was changed, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to a server and join a channel once it has connected. It also includes an IRC command '!setquitmessage <name>' which can be used to change ircbot's quit message.

``` lua
function resourceStart ()
    dummyBot = ircCreateBot ( "DummyBot" )
    ircConnect ( dummyBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnText ( theBot, channel, sender, message )
    if message:find( "!setquitmessage" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!setquitmessage" which we don't need
        -- params[2] has the new name
        ircSetQuitMessage ( theBot, params[2] )
    end
end
```

See Also
--------
