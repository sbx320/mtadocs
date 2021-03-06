The SQLbans resource gives servers 100% flexibility (for example disabling ban logging) with their ban system as it can be edited to meet their needs. The bans are stored using the inbult SQL functions into the database “bans” rather than XML which is used by the inbuilt MTA ban system.

### Requirements for use:

-   Download can be found: [On the MTA community](http://community.mtasa.com/index.php?p=resources&s=details&id=1670).
-   Resource must have access to function.kickPlayer function.getClientIP and function.getPlayerSerial

Exported functions/events
-------------------------

<section name="Server" class="server" show="true">
### addBanSQL

``` lua
bool addBanSQL ( string banValue, string/element banisher, string reason, int duration )
```

### Required Arguments

-   **banValue:** A string for a players serial or IP address.
-   **banisher:** Either a string, player pointer, or resource pointer.
-   **reason:** The reason for the ban.
-   **duration:** Integer in minutes for the ban.

### Returns

Returns *true* if the ban was successfully added. If the ban was not successfully added then *false* will be returned

### getBansSQL

``` lua
table getBansSQL ()
```

### Returns

-   **Column 1 - banValue:** A string for a players serial or IP address.
-   **Column 2 - theBanisher:** A string for either a custom banisher, player name or resource name
-   **Column 3 - theReason:** The reason for the ban.
-   **Column 4 - theDuration:** The minutes left in the ban time.

### getBanDetailsSQL

``` lua
string banValue, string theBanisher, string theReason, int theDuration getBanDetailsSQL ( string banValue )
```

### Required Arguements

-   **banValue:** A string for a players serial or IP address.

### Returns

-   **banValue:** A string for a players serial or IP address.
-   **theBanisher:** Either a string, player pointer, or element pointer.
-   **theReason:** The reason for the ban.
-   **theDuration:** The minutes left in the ban time.

### banPlayerSQL

``` lua
bool banPlayerSQL ( player thePlayer, bool serial, bool ipAddress, string/player/resource theBanisher, string theReason, int theDuration )
```

### Required Arguements

-   **thePlayer:** The player to ban.
-   **serial:** Ban their serial?
-   **ipAddress:** Ban their IP address? (Can't ban both.)
-   **theBanisher:** A string, player, or resource that is banning the player.
-   **theReason:** The ban reason.
-   **theDuration:** Time in minutes the ban should last for.

### Returns

This function will return *true* if the player was successfully banned. If they weren't successfully banned *false* will be returned.

### removeBanSQL

``` lua
bool removeBanSQL ( string banValue, string/player/resource unbanisher )
```

### Required Arguements

-   **banValue:** An IP address or serial to unban
-   **serial:** A string, player or resource that is causing the unban.

### Returns

This function will return *true* if the ban was successfully removed. If the ban wasn't successfully removed or the ban didn't even exist *false* will be returned.

</section>
