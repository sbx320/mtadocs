This function can be used to set a channel mode the specified channel. The specified often needs to have suitable privileges in order for the change to have an effect.

Syntax
------

``` lua
bool ircSetChannelMode ( ircbot theBot, string channel, string mode )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **channel:** The name of the channel on which you want to set a channel mode
-   **mode:** The channel mode string

### Returns

Returns *true*.
**Note:** Does not return *true* if a channel mode was successfully set or *false* if it wasn't set. You can check if the channel mode was set by using callback .

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!limitusers' which can used to change the channel's maximum user limit.

``` lua
function resourceStart ( )
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnText ( theBot, channel, sender, message )
    if message:find( "!limitusers" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!limitusers" which we don't need
        -- params[2] has the user count
        if tonumber( params[2] ) then -- check if it's a number, but don't convert it to a number
            ircSetChannelMode ( theBot, channel, "+l " .. params[2] )
        elseif params[2] == "off" then -- if user passes 'off' as the number, remove the limit
            ircSetChannelMode ( theBot, channel, "-l" )
        end
    end
end
```

See Also
--------
