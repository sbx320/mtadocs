This allows you to set the width of an existing column in a gridlist.

Syntax
------

``` lua
bool guiGridListSetColumnWidth ( element gridList, int columnIndex, number width, bool relative )
```

### Required Arguments

-   **gridList:** The grid list you want to add a column to
-   **columnIndex:** Column ID of the size you want to change
-   **width:** A float or integer of the width of the column depending on the **relative** argument.
-   **relative:** A boolean defining whether **width** measurements will be relative to the Gridlist size, or absolute pixels.

### Returns

Returns *true* if the gridlist column width was successfully set, *false* if bad arguments were given.

Example
-------

This example creates a gridlist with one column that is too small to display. After the column has been successfully created, we give it a new width so you can see column.

``` lua
local gridlist = guiCreateGridList ( 332, 195, 286, 249, false ) 
local column = guiGridListAddColumn ( gridlist, "My column", 0 )

if column then
    guiGridListSetColumnWidth ( gridlist, column, 0.5, true)
end
```

See Also
--------
