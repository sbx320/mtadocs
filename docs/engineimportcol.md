This function imports a RenderWare Collision into the model identified by the model id. This function does not replace the collisions of all models of this type in-game.

To ensure proper replacement, please do not use this function for vehicles.

Syntax
------

``` lua
bool engineImportCOL ( col, int model_id ) 
```

### Required Arguments

-   **col:** The COL that was loaded with [engineLoadCOL](/docs/engineloadcol.md "wikilink")
-   **model\_id:** The model id to import the COL into

### Returns

Returns *true* if the function executed succesfully, *false* otherwise.

Example
-------

This example loads a combination of custom DFF, TXD and COL files to replace an in-game model of a set of floors.

``` lua
outputChatBox ( "> loading floor objects" )
txd_floors = engineLoadTXD ( "models/office_floors.txd" )
engineImportTXD ( txd_floors, 3781 )
col_floors = engineLoadCOL ( "models/office_floors.col" )
dff_floors = engineLoadDFF ( "models/office_floors.dff" )
engineImportCOL ( col_floors, 3781 )
engineReplaceModel ( dff_floors, 3781 )
```

See Also
--------
