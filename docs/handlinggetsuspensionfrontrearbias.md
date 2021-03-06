Returns the suspension bias of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetSuspensionFrontRearBias ( handling theHandling )
float handlingGetSuspensionFrontRearBias ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension bias, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension bias.

### Returns

If you specified a handling element, returns its suspension bias if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the suspension bias that currently applies to vehicles of that ID. Returns *false* in case of failure.

The suspension bias is a number between 0 and 1. If it's 0, the back tires have all the suspension and the front tires have none. If it's 1, the front tires have suspension and the back tires have none. If it's 0.5, front and back tires have the same suspension strength.

Example
-------

``` lua
--TODO
```

See Also
--------
