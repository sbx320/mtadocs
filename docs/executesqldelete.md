This function deletes any rows (from the database) that meet the specified conditions in the specified table.

The SQLite database contains globally stored data and can be used by scripts to store and retrieve data in a structured manner.

The executed SQL query is the following:

``` sql
DELETE FROM <table> WHERE <conditions>
```

Syntax
------

``` lua
bool executeSQLDelete ( string tableName, string conditions )
```

### Required Arguments

-   **tableName:** The name of the table you want to modify.
-   **conditions:** The conditions that need to be met before a row is deleted.

### Returns

The function returns a *boolean* which is *true* on success, and *false* on failure.

### Example

This example creates a table and add's a command to delete the row called “row” inside the table.

``` lua
-- Create's the table named "table" on resource start.
function tableCreate()
    executeSQLCreateTable("table", "row TEXT")
end
addEventHandler("onResourceStart", getResourceRootElement(), tableCreate)

-- Add's a command "deleterow" to delete the row called "row"

function rowDelete()
    executeSQLDelete("table", "row")
end
addCommandHandler("deleterow", rowDelete)
```

See Also
--------
