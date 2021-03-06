This function convert the R,G,B color codes to hexadecimal.

Syntax
------

``` lua
string rgb2Hex ( int red, int green, int blue)
```

### Required Arguments

-   **red:** The amount of [red](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).

<!-- -->

-   **green:** The amount of [green](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).

<!-- -->

-   **blue:** The amount of [blue](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).

Code
----

``` lua
function rgb2hex(r,g,b)
    
    local hex_table = {[10] = 'A',[11] = 'B',[12] = 'C',[13] = 'D',[14] = 'E',[15] = 'F'}
    
    local r1 = math.floor(r / 16)
    local r2 = r - (16 * r1)
    local g1 = math.floor(g / 16)
    local g2 = g - (16 * g1)
    local b1 = math.floor(b / 16)
    local b2 = b - (16 * b1)
    
    if r1 > 9 then r1 = hex_table[r1] end
    if r2 > 9 then r2 = hex_table[r2] end
    if g1 > 9 then g1 = hex_table[g1] end
    if g2 > 9 then g2 = hex_table[g2] end
    if b1 > 9 then r1 = hex_table[b1] end
    if b2 > 9 then r2 = hex_table[b2] end
    
    return "#" .. r1 .. r2 .. g1 .. g2 .. b1 .. b2

end
```

Example
-------

``` lua
local color = rgb2hex(255,50,25)

outputChatBox("255,50,25 = " .. color)
```

See Also
--------
