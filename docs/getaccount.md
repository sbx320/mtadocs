This function returns an [account](/docs/account.md "wikilink") for a specific user.

Syntax
------

``` lua
account getAccount ( string username, [ string password ] )
```

### Required Arguments

-   **username:** The username of the account you want to retrieve

### Optional Arguments

-   **password:** The password for the account. If this argument is not specified, you can get the account whatever password it is, otherwise the password must match the account's.

### Returns

Returns an [account](/docs/account.md "wikilink") or *false* if an account matching the username specified (and password, if specified) could not be found.

Example
-------

``` lua
addEventHandler("onPlayerJoin",root,function()
    if getAccount(getPlayerName(source)) then
        outputChatBox("Please Login!",source)
    else
        outputChatBox("Please Register!",source)
    end
end)
```

See Also
--------

[ar:getAccount](/docs/ar:getaccount.md "wikilink") [es:getAccount](/docs/es:getaccount.md "wikilink") [pl:GetAccount](/docs/pl:getaccount.md "wikilink") [ru:getAccount](/docs/ru:getaccount.md "wikilink")
