This function allows you to check is the element's range to the main point is smaller than (or as big as) the maximum range.

Syntax
------

``` lua
bool isElementInRange( element theElement, float x, float y, float z, float range )
```

### Required Arguments

-   **theElement:** the element whose range we want to check.
-   **x:** the x coordinate of the main point.
-   **y:** the y coordinate of the main point.
-   **z:** the z coordinate of the main point.
-   **range:** the range of the main point to the element.

### Returns

-   Returns *true* if the element is in range of the main point, *false* otherwise.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isElementInRange(ele, x, y, z, range)
   if isElement(ele) and type(x) == "number" and type(y) == "number" and type(z) == "number" and type(range) == "number" then
      return getDistanceBetweenPoints3D(x, y, z, getElementPosition(ele)) <= range -- returns true if it the range of the element to the main point is smaller than (or as big as) the maximum range.
   end
   return false
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
``` lua
addCommandHandler("killnear",
function (player)
   local x, y, z = getElementPosition (player)
   for _,p in ipairs (getElementsByType ('player')) do
      if isElementInRange (p, x, y, z, 25) then -- check if the player's range to the command user is 25m.
         if p ~= player then
            killPed (p, player) -- kill player within 25m from the command user.
         end
      end
   end
end
)
```

</section>
Function created by **KenXeiko**.

See Also
--------
