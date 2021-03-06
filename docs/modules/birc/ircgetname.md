This function is used to retrieve the name of the specified .

Syntax
------

``` lua
string ircGetName ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which name you want to get

### Returns

Returns a [string](/docs/string.md "wikilink") of the ircbot's name if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to a server. Once it has connected, it prints out a message with the bot's name to server log.

``` lua
function resourceStart ()
    dummyBot = ircCreateBot ( "DummyBot" )
    ircConnect ( dummyBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    outputServerLog ( ircGetName ( theBot ) .. " is now connected!" )
end
```

See Also
--------
