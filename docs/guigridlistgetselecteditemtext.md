This function gets the item text of the selected item in a grid list .

Syntax
------

``` lua
string guiGridListGetSelectedItemText ( element gridList [, int column = 1 ] )
```

Required Arguments
------------------

-   **gridList :** The gridLsit to get the selected item text from .

Optional Arguments
------------------

-   **column :** The column to get the selected item text from .

Code
----

<section name='Client' class='client' show='true'>
``` lua
function guiGridListGetSelectedItemText ( gridList, column )
    local item = guiGridListGetSelectedItem ( gridList )
    
    if item then
        return guiGridListGetItemText ( gridList, item, column or 1 )
    end

    return false
end
```

</section>
Returns
-------

-   A *string* containing the selected item text, *false* otherwise .

Example
-------

-   This example gets a player name from the grid list, and out puts it in the chat .

``` lua
local window = guiCreateWindow ( 350, 100, 200, 250, "The Players", false )
--- Create a window !
local gridList = guiCreateGridList ( 0.8, 0.1, 0.15, 0.6, true, window )
--- Create a grid list in the window !
local players = getElementsByType( 'player' )
--- Create a table containing all the players !

for i,player in ipairs ( players ) do
--- Loop the table !
local row = guiGridListAddRow ( gridList )
--- Add a row to the grid list !
guiGridListSetItemText ( gridLsit, row, 1, getPlayerName ( player ), false, false )
--- Set the row's text to the players names !

function selectAPlayer ( )
--- Start a function !
    if ( guiGridListGetSelectedItem ( gridList ) ) then
--- If there was a selected item in the grid list !
        local thePlayerName = guiGridListGetSelectedItemText ( gridList )
--- Get the selected item text !
        outputChatBox ( thePlayerName..' is a player in the server!' )
--- Out put his name in the chat !
    end 
--- Close the ' if ' !
end
--- Close the ' function ' !
addEventHandler ( 'onClientDoubleGUIClick', root, selectAPlayer )
--- Add the event handler of the function !
```

-   '''Author : ''' \#Pai\_\[N\]

See Also
--------
