This function checks to see if a line between two points collides with the water. This is similar to [processLineOfSight](/docs/processlineofsight.md "wikilink"), but only collides with water. Waves are taken into account when testing the line.

Syntax
------

``` lua
bool float float float testLineAgainstWater ( float startX, float startY, float startZ, float endX, float endY, float endZ )
```

### Required Arguments

-   **startX, startY, startZ:** the position of the starting point of the line.
-   **endX, endY, endZ:** the position of the end point of the line.

### Returns

Returns *true* and the position of the intersection point of the line and the water surface if there is a collision, or *false* if there is no collision.

Example
-------

This code snippet adds a /isanywaterbelowme command, which checks if there is water at 500 units below the ground at the position of the player who types it.

``` lua
function checkForWater()
    if isPedOnGround(localPlayer) then
        local px, py, pz = getElementPosition(localPlayer)
        if testLineAgainstWater(px, py, pz, px, py, pz - 500) then
            outputChatBox("Yes, there is water below you.")
        else
            outputChatBox("This place looks a bit dry.")
        end
    end
end
addCommandHandler("isanywaterbelowme", checkForWater)
```

See Also
--------
