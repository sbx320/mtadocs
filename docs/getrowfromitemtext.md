This function enables you to get row from gridlist by using itemtext.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **gridList**: The gridlist you want to get the row from.
-   **itemText**: The itemtext of the row.

### Optional Arguments

-   **column**: The column you want to check the itemtext on.

### Returns

Returns row if successful, false otherwise.

Code
----

<section name="Function source" class="client" show="true">
``` lua
function getRowFromItemText ( list, name, colum )
    if ( isElement(list) ) and ( getElementType(list) == "gui-gridlist" ) and ( type(name) == "string" ) then
        local colum = tonumber(colum) or 1
        local rows = guiGridListGetRowCount ( list ) - 1
        for i=0,rows do
            local text = guiGridListGetItemText ( list, i, colum )
            if ( text == name ) then
                return i
            end
        end
    end
    return false
end
```

</section>
Author: Bssol
