TDMA Todo List
--------------

-   Make Wheetos client sided
-   Wheetos must only show on local team
-   Wheetos should be turn on/off-able
-   Make the game acctually finish (currently broken)
-   Pickups should allow WeaponModel and WeaponAmmo params (This is now done)
-   Player suicides/or when they just die on their own must subtract 1 point from their own team

TDMA v1.2
---------

### Fix List

-   TDMA rounds now really end properly
-   Mission timer has been fixed in order to allow the timer to be displayed for people who joined the server
-   Pickups defined in the <pickup /> syntax never worked when picked up by a player, this is now fixed

### Feature List

-   Added help.xml to the client download list
-   Enabled pickups to be able to be defined by the usual <pickup /> syntax

TDMA V1.1
---------

### Fix List

-   Fixed TDMA rounds not ending when a teams kills have been reached
-   Fixed the Double Spawning
-   Removed the random pickups script, you may now use (http://development.mtasa.com/index.php?title=Element/Pickup)
-   Attempted to fix spawn protection, this includes:
    -   Fixing the Red Spawn Protection Identifier appearing over people randomally...
    -   Fixing people not being able to get killed even after the Red Identifier has been removed.
-   Removed the Wheetos (Team Color Identifier)

### Feature List

-   Added the ability to lock the game clock in your game mode
    -   Do this by: <time h="1" m="1" locked="true"/>
-   Changed all findings of id= to model= in the gamemode .map files

TDMA V1.0
---------

-   Initial Release (Never was released, too buggy)

====
