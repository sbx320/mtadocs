This function converts a string range to a table containing number values.

Syntax
------

``` lua
table rangeToTable ( string range )
```

### Required Arguments

-   **range**: The range string (eg. “1,4,10-15,2”).

### Returns

Returns a table containing all ranged values.

Code
----

``` lua
function rangeToTable( range )
    assert(range, type(range)=="string", "Bad argument @ rangeToTable. Expected 'string', got '"..type(range).."'")
    local numbers = split(range, ",")
    local output = {}
    for k, v in ipairs(numbers) do
        if tonumber(v) then
            table.insert(output, tonumber(v))
        else
            local st,en = tonumber(gettok(v, 1, "-")), tonumber(gettok(v, 2, "-"))
            if st and en then
                for i = st, en, (st<en and 1 or -1) do
                    table.insert(output, tonumber(i))
                end
            end
        end
    end
    return output
end
```

**Author: MrTasty**

Example
-------

Needs example.

``` lua
--TODO
```

See Also
--------
