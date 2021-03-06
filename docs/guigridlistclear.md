This function clears all the data from a grid list.

Syntax
------

``` lua
bool guiGridListClear ( element gridList )
```

### Required Arguments

-   **gridList:** The grid list element to be cleared

### Returns

Returns *true* if the grid list element is valid and has been cleared successfully, *false* otherwise.

Example
-------

This example creates a grid list, puts 2 items in to display the text “Hello” and “world” and clears the grid list after 5 seconds.

``` lua
function clientsideResourceStart ()
        -- Create the grid list element
    local testList = guiCreateGridList ( 0.45, 0.45, 0.15, 0.15, true ) 
        -- Create a column in the list and add 2 rows displaying "Hello" text and "world" text
    local column = guiGridListAddColumn( testList, "test", 0.85 ) 
    guiGridListSetItemText ( testList, guiGridListAddRow ( testList ), column, "Hello", false, false )
    guiGridListSetItemText ( testList, guiGridListAddRow ( testList ), column, "World", false, false )
        -- Set a timer to call the guiGridListClear function to clear the grid list items in 5 seconds
    setTimer ( guiGridListClear, 5000, 1, testList ) 
end
addEventHandler ( "onClientResourceStart", resourceRoot, clientsideResourceStart )
```

See Also
--------
