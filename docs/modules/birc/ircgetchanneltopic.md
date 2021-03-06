This function returns the current channel topic and it's creator of the specified channel. The specified has to be in that channel.

Syntax
------

``` lua
string, string ircGetChannelTopic ( ircbot theBot, string channel )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **channel:** The name of the channel which channel topic you want to get

### Returns

Returns the currently set topic and it's creator of the specified channel. If no topic is set, it returns empty strings.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!topic' which can used to print out current channel topic.

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
    if message:find( "!topic" ) then
        local channelTopic, topicCreator = ircGetChannelTopic( theBot, channel )
        if channelTopic ~= "" then
            ircSendMessage ( theBot, channel, "Current topic is: '" .. channelTopic .. "' and it's set by " .. topicCreator )
        else
            ircSendMessage ( theBot, channel, "There is no topic set!" )
        end
    end
end
```

See Also
--------
