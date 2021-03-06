This function sets a table protected from editing, so if you want to define constants that cannot be changed, this would be a way. I found that function from [Internet](http://www.gammon.com.au/forum/bbshowpost.php?bbsubject_id=8028), by Nick Gammon.

Syntax
------

``` lua
table setTableProtected( table tbl )
```

### Required Arguments

-   **tbl**: The table, which is to be set protected

### Returns

Returns the table which can't be modified anymore

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function setTableProtected (tbl)
  return setmetatable ({}, 
    {
    __index = tbl,  -- read access gets original table item
    __newindex = function (t, n, v)
       error ("attempting to change constant " .. 
             tostring (n) .. " to " .. tostring (v), 2)
      end -- __newindex, error protects from editing
    })
end
```

</section>
Example
-------

<section name="Server- and/or clientside Script" class="both" show="true">
This example shows the above function in work.

``` lua
my_constants =
  {
  WIDTH = 22,
  HEIGHT = 44,
  FOO = "bar",
  }

-- protect my table now
my_constants = setTableProtected (my_constants) -- it's important to redeclare that variable what you want to protect, since you could still modify the original table.
my_constants.WIDTH = 11
my_constants.HEIGHT = 11
-- These will return errors, because _newindex always returns error for that table
-- test it
print ("WIDTH",  my_constants.WIDTH)  --> WIDTH 22 -- and these remain unchanged
print ("HEIGHT", my_constants.HEIGHT) --> HEIGHT 44
```

</section>
Author: Nick Gammon, commented a bit and found from Internets - Lordy

See Also
--------
