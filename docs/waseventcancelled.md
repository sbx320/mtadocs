This function checks if the last completed event was cancelled. This is mainly useful for custom events created by scripts.

Events can be cancelled using [cancelEvent](/docs/cancelevent.md "wikilink"), this indicates that the resource which triggered the event should do whatever it can to reverse any changes made by whatever caused the event. See [triggerEvent](/docs/triggerevent.md "wikilink") for a more detailed explanation of this.

Syntax
------

``` lua
bool wasEventCancelled ( )   
```

### Returns

Returns *true* if the event was cancelled, *false* if it wasn't or doesn't exist.

Example
-------

This example implements a custom event *onFlagPickup* that would be triggered if an *onMarkerHit* event was triggered on a marker whose parent was a *flag* element. If the event isn't canceled then an element data value is set on the player.

``` lua
addEvent ( "onFlagPickup", true )

function flagHitcheck ( thePlayer )
    parentElement = getElementParent ( source ) -- get the parent of the marker
    if ( getElementType ( parentElement ) == "flag" ) then -- if it was a flag element then
        triggerEvent ( "onFlagPickup", source, thePlayer ) -- trigger our onFlagPickup event
        
        if ( not wasEventCancelled() ) then -- if handlers for 'onFlagPickup' didn't cancel it then
            setElementData ( thePlayer, "hasFlag", true ) -- set that the player picked up the flag
        end
    end
end
addEventHandler ( "onMarkerHit", getRootElement(), flagHitCheck )
```

See Also
--------
