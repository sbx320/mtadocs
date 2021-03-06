<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns the last error number of a MySQL connection.

Syntax
------

``` lua
int mysql_errno ( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

The last error number, zero if nothing failed. Visit <http://dev.mysql.com/doc/refman/5.0/en/error-handling.html> for a list of error codes.

Example
-------

**Example 1:** This example sends a query to the server and if it fails, shows the reason.

``` lua
result = mysql_query(handler, "SELECT FROM table") -- We have a syntax error in the query
if (not result) then -- The query failed
  outputDebugString("mysql_query failed: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler)) -- Show the reason
else
  mysql_free_result(result) -- Free the last query result data
end
```

See also
--------
