This resource lets You create some coronas. Not just your typical gtasa coronas that often times fail to appear. Since in this case corona Elements are created using dxDrawMaterialLine3d MTA function. I have changed the behaviour of the material to act as cylindrical billboards do.

Overview
--------

It is easy to use, gives a few options to manage coronas.

The resource itself adds exported clientside functions:

Exported functions
------------------

#### createCorona

<section name="Client" class="client" show="true">
This function creates a shadered materialLine3d Corona.

``` lua
)
```

### Required Arguments

-   **float posX, posY, posZ:** Position in world space.
-   **float size:** Size of the corona.
-   **int colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Optional Arguments

-   **bool isSoftParticle:** The aim with soft particles is to remove the ugly artifact that appears when the particle quad intersects the scene. The option requires DepthBuffer access.

### Returns

The function returns coronaElement if set successfully, false otherwise.

</section>
#### createMaterialCorona

<section name="Client" class="client" show="true">
This function creates a shadered materialLine3d Corona with a custom material.

``` lua
)
```

### Required Arguments

-   **element material:** Material to replace the standard corona texture with.
-   **float posX, posY, posZ:** Position in world space.
-   **float size:** Size of the corona.
-   **int colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Optional Arguments

-   **bool isSoftParticle:** The aim with soft particles is to remove the ugly artifact that appears when the particle quad intersects the scene. The option requires DepthBuffer access.

### Returns

The function returns coronaElement if set successfully, false otherwise.

</section>
#### destroyCorona

<section name="Client" class="client" show="true">
This function destroys a shadered materialLine3d Corona element.

``` lua
bool exports.custom_coronas:destroyCorona(element coronaElement)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaMaterial

<section name="Client" class="client" show="true">
This function sets custom material for the corona.

``` lua
bool exports.custom_coronas:setCoronaMaterial(element coronaElement,element material)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **element material:** Material to replace the standard corona texture with.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaSize

<section name="Client" class="client" show="true">
This function sets size of the corona.

``` lua
bool exports.custom_coronas:setCoronaSize(element coronaElement,float size)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **float size:** Size of the corona.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaSizeXY

<section name="Client" class="client" show="true">
This function sets size of the corona (width and height).

``` lua
bool exports.custom_coronas:setCoronaSizeXY(element coronaElement,float width,height)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **float width, height:** Size of the corona.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaDepthBias

<section name="Client" class="client" show="true">
On createCorona the depthBias is set properly (0-1). You can however set other value depending on your needs. To see the results you'll need to set enableDepthBiasScale to true.

``` lua
bool exports.custom_coronas:setCoronaDepthBias(element coronaElement,float depthBiasValue)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **float depthBiasValue:** depthBias value.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaPosition

<section name="Client" class="client" show="true">
This function sets corona position.

``` lua
bool exports.custom_coronas:setCoronaPosition(element coronaElement,float posX,posY,posZ)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **float posX, posY, posZ:** Position in world space.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronaColor

<section name="Client" class="client" show="true">
This function sets light color values.

``` lua
bool exports.custom_coronas:setCoronaColor(element coronaElement,float colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **element coronaElement:** A previously declared corona element.
-   **float colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setCoronasDistFade

<section name="Client" class="client" show="true">
Set the Max distance of the corona to sync and the distance on which the it starts to fade out.

``` lua
bool exports.custom_coronas:setCoronasDistFade(int MaxEffectFade,int MinEffectFade)
```

### Required Arguments

-   **int MaxEffectFade:** Set the Max distance of the corona to sync.(Must be greater than MinEffectFade).
-   **int MinEffectFade:** Set the distance on which the corona starts to fade out.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### enableDepthBiasScale

<section name="Client" class="client" show="true">
Standard depthBias for GTASA coronas is about 1 unit, despite the corona scale. This function elables depthBias scaling.

``` lua
bool exports.custom_coronas:enableDepthBiasScale(bool isDepthScaleEnabled)
```

### Required Arguments

-   **bool isDepthScaleEnabled:** Enable/disable depthBias scaling.

### Returns

The function returns true if set successfully, false otherwise.

</section>
Examples
--------

``` lua
function addStuff()
    for i=1,30 do
        for j=1,30 do
            exports.custom_coronas:createCorona(i * 7,j * 7,10,4,math.random()*255,math.random()*255,math.random()*255,1*255,false) 
        end 
    end
end

addEventHandler("onClientResourceStart", getResourceRootElement( getThisResource()), addStuff)
```

This creates a 400 coronas near position (0,0,0)

``` lua
local vehicle1 = nil
addEventHandler("onClientVehicleEnter", getRootElement(),
    function(thePlayer, seat)
        if thePlayer == getLocalPlayer() then
            vehicle1 = source
        end
    end
)

local carLight = exports.custom_coronas:createCorona(0,0,0,4,math.random()*255,math.random()*255,math.random()*255,1*255)
addEventHandler("onClientPreRender", root, function()
    if vehicle1 then 
        xxx1,yyy1,zzz1 = getElementPosition(vehicle1)
        exports.custom_coronas:setCoronaPosition(carLight,xxx1,yyy1,zzz1)
    end
end
) 
```

This creates a corona and attaches it to a vehicle that the player enters.

Of course when you want to use these functions in your resources you have to include the custom\_coronas resource in meta.

See Also
--------

[A youtube video](http://www.youtube.com/watch?v=5lruyY1fviQ)

[Custom Coronas resource on MTA Community](http://community.multitheftauto.com/index.php?p=resources&s=details&id=9558)

[WebGL Orthographic 3D](http://www.html5rocks.com/en/tutorials/webgl/webgl_orthographic_3d)
