**Use [getZoneName](/docs/getzonename.md "wikilink") instead.**

Syntax
------

``` Lua
city getPlayerCityName ( string element )
```

Required Arguments
------------------

-   **element:** the element you want to get his city.

### Returns

Returns element City “LS,SF,LV”

Code
----

<section name="Shared (server and client)" class="both" show="true">
    local LS = createColRectangle (-800.81671, -2990.10657, 5100, 3330)
    local LV = createColRectangle (-810, 350, 5000, 3000)
    local SF = createColRectangle (-4000, -3000, 3190, 6000)

    function getPlayerCityName(element)
    if ( not isElement(element) ) then return end
        if (isElementWithinColShape(element, LS)) then
            result = "LS"
        elseif (isElementWithinColShape(element, LV)) then
            result = "LV"
        elseif (isElementWithinColShape(element, SF)) then
            result = "SF"       
        end
        return result
    end

</section>
-   Original author: *Has\[S\]oN*

Example
-------

This example say to player “welcome to LV” when he enterd LV.

<section name="Shared (Server and Client)" class="both" show="true">
    function enter()
    outputChatBox("Welcome To LV")
    end
    addEventHandler("onColShapeHit", LV, enter)

</section>
Example \#2
-----------

This example give player his city when he talking.

<section name="Shared (Server and Client)" class="both" show="true">
    function say()
    outputChatBox("You are in City: "..getPlayerCityName(source).." Now.!!!")
    end
    addEventHandler("onPlayerChat",getRootElement(),say)

</section>
See also
--------
