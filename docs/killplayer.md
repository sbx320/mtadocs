This function kills the specified player.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") to kill

### Optional Arguments

-   **theKiller:** The player responsible for the kill
-   **weapon:** The ID of the weapon that should appear to have killed the player (doesn't affect how they die)
-   **bodyPart:** The ID of the body part that should appear to have been hit by the weapon (doesn't affect how they die)

### Returns

Returns *true* if the player was killed, *false* if the player specified could not be killed or is invalid.

Example
-------

**Example 1:** This simple example adds a **kill** command to commit suicide.

``` lua
function commitSuicide(sourcePlayer)
    -- kill the player and make him responsible for it
    killPlayer(sourcePlayer, sourcePlayer)
end
-- attach our handler to the "kill" command
addCommandHandler("kill", commitSuicide)
```

**Example 2:** This example enables 1 hit kills if a player is shot in the head.

``` lua
function headshotKill ( attacker, attackerweapon, bodypart, loss )
    if bodypart == 9 then --if the bodypart is the head
        --kill the player, emulating the correct killer, weapon and bodypart.
        killPlayer ( source, attacker, attackerweapon, bodypart )
    end
end
addEventHandler ( "onPlayerDamage", getRootElement(), headshotKill )
```

See Also
--------
