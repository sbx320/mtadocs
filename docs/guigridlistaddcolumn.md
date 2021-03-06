This function is used to create columns in grid lists.

Syntax
------

``` lua
int guiGridListAddColumn ( element gridList, string title, float width )
```

### Required Arguments

-   **gridList:** The grid list you want to add a column to
-   **title:** Title of the column
-   **width:** Column width, relative to the grid list width

### Returns

Returns the column id if it was created, *false* otherwise.

Example
-------

This example creates a player list on the right side of the screen and fills it with the currently connected players.

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
addEventHandler ( "onClientResourceStart", resourceRoot, clientsideResourceStart )
```

See Also
--------
