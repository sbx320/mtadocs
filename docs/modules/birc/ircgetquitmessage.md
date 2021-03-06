This function is used to retrieve the quit message of the specified .

Syntax
------

``` lua
string ircGetQuitMessage ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which quit message you want to get

### Returns

Returns a [string](/docs/string.md "wikilink") of the ircbot's quit message if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot*, sets it's quit message and makes it connect to a server. Once it has connected, it prints out the quit message to server log.

``` lua
function resourceStart ()
    dummyBot = ircCreateBot ( "DummyBot" )
    ircSetQuitMessage ( dummyBot, "Baibai" )
    ircConnect ( dummyBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    outputServerLog ( ircGetName ( theBot ) .. "'s quit message is " .. ircGetQuitMessage ( theBot ) )
end
```

See Also
--------
