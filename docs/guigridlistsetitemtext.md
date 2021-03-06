This function changes the text of a gridlist item.

Syntax
------

``` lua
bool guiGridListSetItemText ( element gridList, int rowIndex, int columnIndex, string text, bool section, bool number )
```

### Required Arguments

-   **gridList:** The grid list element
-   **rowIndex:** Row ID
-   **columnIndex:** Column ID
-   **text:** The text you want to put in (does NOT accept numbers, use tostring() for that)
-   **section:** Determines if the item is a section
-   **number:** Tells whether the text item is a number value or not (used for sorting)

### Returns

Returns *true* if the item text was set successfully, *false* otherwise.

Example
-------

This example creates a player list on the right of the screen and fills it

``` lua
function clientsideResourceStart ()
        local playerList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true ) -- Create the grid list
        local column = guiGridListAddColumn( playerList, "Player", 0.85 ) -- Create a 'players' column in the list
        if ( column ) then -- If the column was successfully created
                for id, playeritem in ipairs(getElementsByType("player")) do 
                --Loop through all the players, adding them to the table
                        local row = guiGridListAddRow ( playerList )
                        guiGridListSetItemText ( playerList, row, column, getPlayerName ( playeritem ), false, false )
                end
        end
end
addEventHandler ( "onClientResourceStart", getResourceRootElement(), clientsideResourceStart )
```

See Also
--------
