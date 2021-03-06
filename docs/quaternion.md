<lowercasetitle>Quaternion</lowercasetitle>

Quaternion is used to define the rotation angle by GTA:SA game engine, which is different from MTASA which is based on Euler angle This function returns the Euler angle(rotx,roty,rotz) from quaternion(rotx,roty,rotz,rotw).this is non-mtasa function, user need to put this function in your lua scripts.

Syntax
------

``` lua
float, float, float fromQuaternion ( rotx,roty,rotz,rotw)
```

### Required Arguments

-   **rotx,roty,rotz,rotw**: The quaternion from IPL file

### Returns

-   **rotx,roty,rotz**: The Euler angle

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function math.arad(number)
    if type(number) == "number" then
        return (number/(math.pi*2))*360
    end
end

function fromQuaternion(x,y,z,w)
    local heading = math.atan2(2*(w*x+y*z),1-2*(x^2+y^2))
    local attitude = math.asin(w*y-z*x) 
    local bank = math.atan2(2*(w*z+x*y),1-2*(y^2+z^2))
    return math.arad(heading),math.arad(attitude),math.arad(bank)
end
```

</section>
Example
-------

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua">

function math.arad(number)

`   if type(number) == `“`number`”` then`
`       return (number/(math.pi*2))*360`
`   end`

end

function fromQuaternion(x,y,z,w)

`   local heading = math.atan2(2*(w*x+y*z),1-2*(x^2+y^2))`
`   local attitude = math.asin(w*y-z*x) `
`   local bank = math.atan2(2*(w*z+x*y),1-2*(y^2+z^2))`
`   return math.arad(heading),math.arad(attitude),math.arad(bank)`

end

local rotx, roty, rotx, rotw = 233,666,888,999 -- you can read the Quaternion from IPL file createObject ( 1337, 5540.6654, 1020.55122, 1240.545,fromQuaternion(rotx, roty, rotx, rotw))

</syntaxhighlight>
</section>
Author: KawaNoII (http://www.chinesemta.com)

See Also
--------
