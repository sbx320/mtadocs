This event is triggered whenever the local player's radio station is changed

Parameters
----------

``` lua
int stationID
```

-   **stationID**: An [integer](/docs/int.md "wikilink") representing the station the player switched to.

Station ID's:

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the local [player](/docs/player.md "wikilink").

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the Radio station will not change.

Example
-------

``` lua
label = guiCreateLabel ( 0.8, 0.9, 0.2, 0.1, "Radio off", true) --create a label to show the station

function stationDraw(station)
    guiSetText ( label, getRadioChannelName(station)) --Show the station Name
end

addEventHandler("onClientPlayerRadioSwitch", getLocalPlayer(), stationDraw) -- add an event handler
```

See Also
--------

### Client player events

### Client Audio functions
