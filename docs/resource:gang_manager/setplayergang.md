Sets player's gang if the player is not currently in a gang.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setPlayerGang ( player Player, string Gang )
```

Required Arguments
------------------

-   **Player:** Player element whose gang you want to set
-   **Gang:** ID of the gang that you want to set as the player's gang

</section>
<section name="Client" class="client" show="true">
``` lua
bool setPlayerGang ( player Player, string Gang )
```

Required Arguments
------------------

-   **Player:** Player element whose gang you want to set
-   **Gang:** ID of the gang that you want to set as the player's gang

</section>
Returns
-------

-   **Success:** Boolean that is true if the player's gang has been set or false if the player already is in the gang
