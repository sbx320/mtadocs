Syntax
------

``` lua
bool setVehicleSirens ( vehicle theVehicle, int sirenPoint, float posX, float posY, float posZ, float red, float green, float blue, [float alpha = 255, float minAlpha = 0.0] )
```

### Required Arguments

-   **theVehicle:** The vehicle to modify
-   **sirenPoint:** The siren point to modify
-   **posX:** The x position of this siren point from the center of the vehicle
-   **posY:** The y position of this siren point from the center of the vehicle
-   **posZ:** The z position of this siren point from the center of the vehicle
-   **red:** The amount of red from 0 to 255
-   **green:** The amount of green from 0 to 255
-   **blue:** The amount of blue from 0 to 255

### Optional Arguments

-   **alpha:** The alpha of the siren from 0 to 255
-   **minAlpha:** The minimum alpha of the light during day time

### Returns

Returns *true* if the siren point was successfully changed on the vehicle, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example adds a siren then sets the vehicle siren in the center of the car. (Not sure if it works...)

``` lua
addEventHandler("onVehicleEnter",root,function(player,seat)
   if(player)and(seat==0)then
      addVehicleSirens(source,1,1)
      setVehicleSirens(source,1,0,0,0,100,0,100)
   end
end)
addEventHandler("onVehicleExit",root,function(player,seat)
   if(player)and(seat==0)then
      removeVehicleSirens(source)
   end
end)
```

</section>
Requirements
------------

See Also
--------
