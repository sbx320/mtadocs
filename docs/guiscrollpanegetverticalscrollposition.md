This function is used to get the position of a vertical scroll pane as a percentage.

Syntax
------

``` lua
float guiScrollPaneGetVerticalScrollPosition ( element verticalScrollPane )
```

### Required Arguments

-   **verticalScrollPane**: The scroll pane you want to know the position of

### Returns

Returns a [float](/docs/float.md "wikilink") ranging between 0 and 100, or **false** otherwise.

Example
-------

This example gets the position of a scroll pane called “myScrollPane” created with [guiCreateScrollPane](/docs/guicreatescrollpane.md "wikilink"), and outputs it to the chatbox.

``` lua
if ( myScrollPane ) then -- if the scroll pane exist then
        -- get the position
    local position = guiScrollPaneGetVerticalScrollPosition( myScrollPane )
    -- output to the chatbox
    outputChatBox ( "Current position of scroll pane:" .. tostring(position) .. "%" )
else -- if the scroll pane was not found
       outputChatBox ("scroll pane not found!")
end
```

See Also
--------
