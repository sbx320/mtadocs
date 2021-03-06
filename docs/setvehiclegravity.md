Sets the gravity vector of a vehicle. The vehicle will fall in this direction, and the camera of any occupants will also be rotated to match it. Can be used for e.g. driving on walls or upside down on ceilings.

Syntax
------

``` lua
bool setVehicleGravity ( vehicle theVehicle, float x, float y, float z )
```

### Required Arguments

-   **theVehicle:** the vehicle of which to change the gravity.
-   **x, y, z:** the components of the new gravity vector. If this vector has length 1, the strength of the gravity will be same as the global gravity for other entities. If it is 2, it will be twice as strong, etc.

### Returns

Returns *true* if successful, *false* otherwise.

See Also
--------
