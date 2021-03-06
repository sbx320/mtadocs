Can be used to check if the user has Voice or higher

Syntax
------

``` lua
function ircIsVoice ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so that people with voice or higher can use !say

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!say" ) == 1 then
        if ( ircIsVoice( pIRC, szChannel, szNick ) ) then
            local Message = string.sub(szText, 5)
            outputChatBox("* " .. szNick .. " [IRC]: " .. Message)
        end
    end
end
```

See also
--------
