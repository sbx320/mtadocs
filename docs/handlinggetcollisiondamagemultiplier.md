Returns the collision damage multiplier of a handling element or vehicle ID. The higher the value, the more sensitive the vehicle is to collisions.

Syntax
------

``` lua
float handlingGetCollisionDamageMultiplier ( handling theHandling )
float handlingGetCollisionDamageMultiplier ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the collision damage multiplier, *or*
-   **vehicleID:** the vehicle ID of which you want to get the collision damage multiplier.

### Returns

If you specified a handling element, returns its collision damage multiplier if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the collision multiplier that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
