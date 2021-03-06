This function “unloads” a custom model identified by a model id, and reloads the original GTA model.

Syntax
------

``` lua
bool engineUnloadModel ( int model_id ) 
```

### Required Arguments

-   **model\_id:** The model id used to identify the model that is being reloaded.

### Returns

Returns *true* if the custom model was unloaded succesfully, *false* otherwise.

Example
-------

This example loads a combination of custom DFF, TXD and COL files to replace an in-game model of a set of floors and unloads it again.

``` lua
outputChatBox ( "> loading floor objects" )
txd_floors = engineLoadTXD ( "models/office_floors.txd" )
engineImportTXD ( txd_floors, 3781 )
col_floors = engineLoadCOL ( "models/office_floors.col" )
dff_floors = engineLoadDFF ( "models/office_floors.dff" )
engineImportCOL ( col_floors, 3781 )
engineReplaceObjectModel ( dff_floors, 3781 )

-- do your logic

engineUnloadModel ( 3781 )
```

See Also
--------
