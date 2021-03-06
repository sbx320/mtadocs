This function checks if a ped is aiming and if it is at an certain distance from the object you specified. Returns true if yes and false if not.
**Important : ONLY WORKS CLIENT SIDE.**

Syntax
------

``` lua
bool isPedAimingNearPed ( ped thePed , element theElement, int range )
```

### Required Arguments

-   **thePed**: The ped element.
-   **theElement**: The element you want to see if thePed is aiming to.
-   **range**: Range of the colshape.

### Returns

Returns true if ped is aiming a weapon to the element and within the range, false if not.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function isPedAimingNearPed ( thePed, theElement, range )
    if isElement(thePed) and isElement(theElement) and type(range) == "number" then
        if (getElementType(thePed) == "player" or getElementType(thePed) == "ped") then
            local x, y, z = getElementPosition(theElement)
            local col = createColTube(x, y, z-1, range, 2)
            attachElements(col, theElement)
            if getPedTask(thePed, "secondary", 0) == "TASK_SIMPLE_USE_GUN" and getPedTarget(thePed) == theElement and isElementWithinColShape(thePed, col) then
                return true
            end
        end
    end
    return false
end
```

</section>
Example
-------

``` lua
--TODO
```

See Also
--------
