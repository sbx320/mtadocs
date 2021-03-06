Returns the length of the string passed.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **i:** An integer representing the beginning position for measuring the length of the section (may be negative).
-   **j:** An integer representing the ending position for measuring the length of the section (may be negative).

### Returns

Returns the length of the string as an *integer*.

Example
-------

<section name="Client" class="client" show="true">
This example calculates the length of the input of the command /length and shows it in the chatbox.

``` lua
addCommandHandler("length", 
    function (command, ...)
        local input = table.concat({...}, " ")

        if input then
            local length = utf8.len( input )
            outputChatBox( "* Length of your input: ".. length )
        end
    end
)
```

</section>
See Also
--------
