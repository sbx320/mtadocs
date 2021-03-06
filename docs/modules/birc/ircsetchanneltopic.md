This function can be used to change the topic of specified channel. The specified has to be in that channel and often it needs to have suitable privileges.

Syntax
------

``` lua
bool ircSetChannelTopic ( ircbot theBot, string channel, string topic )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **channel:** The name of the channel which channel topic you want to change
-   **topic:** The new topic of the channel

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if the channel topic was successfully changed or *false* if it wasn't changed. You can check if the channel topic was changed by using callback .

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!settopic' which can used change the current channel topic.

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
    if message:find( "!settopic" ) then
        local topic = message:sub( 11 ) -- subtract "!settopic " from the message
        ircSetChannelTopic ( theBot, channel, topic )
    end

end
```

See Also
--------
