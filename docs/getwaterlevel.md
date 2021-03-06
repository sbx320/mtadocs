This function allows you to retrieve the water level from a certain location. The water level is 0 in most places though it can vary (e.g. it's higher near the dam).

Syntax
------

``` lua
float getWaterLevel ( float posX, float posY, float posZ [ , bool bCheckWaves = false ] )
```

``` lua
float getWaterLevel ( water theWater )
```

### Required Arguments

-   **x:** The X axis position
-   **y:** The Y axis position
-   **z:** The Z axis position

*or:*

-   **theWater:** the water element

### Optional Arguments

-   **bCheckWaves** Include the water levels of waves in the ocean, lakes and ...

### Returns

Returns an *integer* of the water level if the [localPlayer](/docs/localplayer.md "wikilink")/position is near the water (-3 to 20 on the Z coordinate) else *false* if there's no water near the [localPlayer](/docs/localplayer.md "wikilink")/position.

Example
-------

This example will tell you what's the water level where the specified player is located.

``` lua
function scriptGetLevel ( command, playername ) --when getlevel is called
  local thePlayer = getPlayerFromName ( playername ) --get the player from nickname
  if ( thePlayer ~= false ) then --if there is a player from the nickname
    local x, y, z = getElementPosition ( thePlayer ) -- get his position
    local level = getWaterLevel ( x, y, z )
      if level then -- if it's not false
        level = z - level -- calculate how far away is he from the water
        outputChatBox( "You are " .. level .. " units away from the water!", source )
      else outputChatBox ( "There's no sign of water" )
      end
  else outputChatBox ( "Player does not exist" )
  end
end
addCommandHandler( "getlevel", scriptGetLevel ) -- add a command "getloc" which
```

See Also
--------
