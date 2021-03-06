<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a table with information about a field in a query result. You can call repeatedly this function to return all the result fields, and when it reaches the end returns nil. You can also go to a specific field using [mysql\_field\_seek()](/docs/modules/mta-mysql/mysql_field_seek.md "wikilink").

Syntax
------

``` lua
table mysql_fetch_field ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

A table with information about a field with the following keys:

-   **name:** The name of this field.
-   **org\_name:** If you used aliases in the query, the original name of the field.
-   **table:** The table of this field.
-   **org\_table:** If you used aliases for the table, the original name of the table.
-   **length:** The maximum length allowed by this field in the table definition.
-   **max\_length:** The maximum length of this field in all the result rows.
-   **not\_null:** True if the field can't be NULL (See [mysql\_null()](/docs/modules/mta-mysql/mysql_null.md "wikilink")).
-   **primary\_key:** True if the field is the table primary key.
-   **unique\_key:** True if the field value is unique.
-   **multiple\_key:** True if the field is part of a key.
-   **numeric:** True if the field is numeric.
-   **blob:** True if the field is a BLOB.
-   **unsigned:** True if the field is unsigned.
-   **zerofill:** True if the field is zero filled.
-   **type:** A string representing the type of this field.

### Example

**Example 1:** This example shows how to print the rows of a result set showing the field name.

``` lua
local result = mysql_query(handler, "SELECT * FROM account") -- Execute the query
for result,row in mysql_rows(result) do -- Iterate through all the result rows
  mysql_field_seek(result, 1) -- Reset the field cursor to the first field
  for k,v in ipairs(row) do
    local field = mysql_fetch_field(result) -- Retreive the field data
    if (v ~= mysql_null()) then
      outputDebugString("row[" .. field["name"] .. "] = " .. v)
    else
      outputDebugString("row[" .. field["name"] .. "] = NULL")
    end
  end
end
mysql_free_result(result) -- Free the result
```

See also
--------
