Used to get the meta tags attached to a sound. These provide information about the sound, for instance the title or the artist.

Syntax
------

``` lua
table getSoundMetaTags ( element sound )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") element.

### Returns

Returns a [table](/docs/table.md "wikilink") with all data available (keys are listed below) for the sound if successful, *false* otherwise.

Example
-------

``` lua
addEventHandler("onClientSoundFinishedDownload",root,function(length)
    local meta = getSoundMetaTags(source)
    outputChatBox("The sound: "..(meta.title).." has finished in :"..length.."ms.")
        outputChatBox("The sound meta tags: Artist:"..(meta.artist).." Album:"..(meta.album).." Genre:"..(meta.genre).." Year:"..(meta.year).." Comment:"..(meta.comment).." Track:"..(meta.track).." Composer:"..(meta.composer).." Copyright:"..(meta.copyright).." SubTitle:"..(meta.subtitle).." Album Artist:"..(meta.album_artist)..".")
end)
```

See Also
--------

[AR:getSoundMetaTags](/docs/ar:getsoundmetatags.md "wikilink")
