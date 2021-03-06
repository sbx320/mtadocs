This function allows you to make the server reveal whether or not voice is currently enabled.

Syntax
------

``` lua
bool isVoiceEnabled ( )
```

### Returns

Returns *true* if the voice is enabled on the server, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to forbid use voice for muted (in chat) players

    -- only if voice enabled
    if isVoiceEnabled() then
        -- adding handler for voice start event
        addEventHandler( 'onPlayerVoiceStart', root,
            function()
                -- if player is muted in chat
                -- do not broadcast his voice to other players
                if isPlayerMuted(source) then cancelEvent() end
            end
        )
    end

</section>
See Also
--------
