Syntax
------

``` lua
bool setWindowFlashing ( bool shouldFlash [, int count = 10 ] )
```

### Required Arguments

-   **shouldFlash:** whether the window should flash

### Optional Arguments

-   **count:** the number of times the window should flash, defaults to **10 times**

### Returns

Returns **false** if:

-   the window is already in focus
-   the client has disabled this feature

Returns **true** otherwise

Example
-------

A command that allows the player to flash their window three times after one second.

``` lua
addCommandHandler("flash",
    function()
        setTimer(setWindowFlashing, 1000, 1, true, 3)
    end
)
```

A command that allows the player to flash their window after a certain period of time for a certain count.

``` lua
addCommandHandler("flash",
    function(_, wait, count)
        wait = tonumber(wait) -- makes "wait" a number, this will be false if it can't be converted
        shouldFlash = type(wait) == "number" -- if wait is given, we should flash, otherwise we shouldn't
        wait = wait or 5-- make wait default to 1 second if it isn't a number
        count = tonumber(count) or 5 -- makes "count" a number, 5 if it can't be converted

        setTimer(setWindowFlashing, wait*1000, 1, shouldFlash, count)
    end
)
```

See also
--------
