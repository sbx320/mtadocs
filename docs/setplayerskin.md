Please use [setElementModel](/docs/setelementmodel.md "wikilink")

This function changes the skin of a player.

Syntax
------

``` lua
bool setPlayerSkin ( player thePlayer, int skinID )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose model will be changed.
-   **skinID:** A GTASA player model (skin) ID. See [Character Skins](/docs/character_skins.md "wikilink").

Example
-------

This example sets you a police skin when you type the command /law.

``` lua
 
function enterTheLaw(playerSource)
  if (getPlayerSkin(playerSource) == 280) then
    outputChatBox("You are already in the law!", playerSource)
  else
    setPlayerSkin(playerSource, 280)
    outputChatBox("Welcome to the law, protect the innocents.", playerSource)
  end
end

addCommandHandler("law", enterTheLaw)
```

See Also
--------
