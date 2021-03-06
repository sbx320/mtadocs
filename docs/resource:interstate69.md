`*rewriting in prgress*`

Interstate69 is based on the Interstate series for PC. Its basicly a car game, with weapons mounted on the cars.

Creating a map for Interstate is rather simple. But Interstate also supports your own script, and can fairly easy be remade to basicly anything.

So... What do I do?
===================

-   Once you join you will be presented with a GUI where you can choose your vehicle and weapons.
    -   If you join in the middle of a game, you have to wait for the next round before you can spawn.
-   Spawnpoints are choosen randomly out of the ones provided in the .map file.
-   Once you spawn, destroy your opponents at all costs!
    -   Be sure not to die yourself.
-   Once every opponent has been eliminated, you will gain a “win” point, and the game will restart.

### Playing and weapons

-   Use mouse1 and mouse2 to fire your primary and secondary weapon.
-   The stinger is placed with R.

Creating an Interstate69 map
============================

Interstate69 is fairly easy to map. You have a few options to choose from.

-   create a map with the default settings.
-   create a map with your own setting
    -   requiers a script alongside your map file.

Map Syntaxes
============

To create an Interstate69 map, all of these syntaxes have to exsist. *Note that these elements may change before release.*

Interstate69 Settings Example
-----------------------------

``` xml
<settings respawntime="3000" maxdeath="5" elimination="1" spawnprotection="5000" allowedspawntime="300" />
```

#### Settings - description

-   **respawntime:** How long you have to wait before you respawn after being killed. Time is in milliseconds.
-   **maxdeath:** For elimination - how many times you can die before getting eliminated.
-   **elimination:** This small setting is one of the most important ones. Change this to “0” to use your own script.
    -   This setting will disable almost everything in Interstate, such as spawning, scoring, spectating etc etc.
-   **spawnprotection:** How long time after spawn should you be protected
-   **allowedspawntime:** Defines how long **new** people should be able to spawn after a round has begun. Time is in Minutes

Camera Example
--------------

``` xml
<camera posX="306.56988525391" posY="1412.0191650391" posZ="88.63539123535" targetX="579.46563720703" targetY="1344.4914550781" targetZ="10.268367767334" />
```

A camera view you will see when choosing a vehicle etc.

#### Camera - description

-   **posX, posY, posZ:** Position of the camera
-   **targetX, targetY, targetZ:** The position the camera will look at.

Gamearea Example
----------------

``` xml
<gamearea posX="505.837" posY="1443.684" posZ="4.6" size="380" />
```

A gamearea is a very good idea to have on maps without fysical walls. This prevents people from driving away and hide, instead of fight like a man!

#### Gamearea - description

-   **posX, posY, posZ:** The position of the area, should be in the center of the map/gamearea
-   **size:** the size of the allowed area, in radius.

Spawnpoints
-----------

``` xml
<spawnpoint posX="526.4742" posY="1561.264" posZ="1.4321" rot="100"/>
```

Spawnpoints defines where to spawn. You can have as many spawnpoints as you want.

#### Required Attributes

-   **posX, posY, posZ:** The position to spawn. Interstate uses an internal randInt of 10, to prevent people to spawn ontop of eachother.
-   **rot:** the rotation you will spawn with.
    -   this does not currently affect the rotation of the vehicles.

Vehicles: How-to add
--------------------

``` xml
<tehVehicle id="Elegy" model="562" image="elegy.png" resource="Interstate69"> 
    <primary name="Minigun" id="Minigun" type="minigun" model="2985" image="elegy_minigun.png" posX="0.5" posY="1.3" posZ="-0.7" rotX="0" rotY="0" rotZ="1.5"/>
    <primary name="Small Missile" id="Small Missile" type="explosion" model="3790" image="elegy_missile.png" posX="0.7" posY="1.4" posZ="-0.2" rotX="0" rotY="0" rotZ="-1.5" posX1="-0.7" posY1="1.4" posZ1="-0.2" rotX1="0" rotY1="0" rotZ1="-1.6" />
    <secondary name="SAM x4" id="SAM x4" type="sam4" model="3267" image="elegy_sam.png" posX="0" posY="-1.5" posZ="-0.7" rotX="-0.5" rotY="0" rotZ="0" />
    <secondary name="Molotov" id="Molotov" type="molotov" model="3267" image="elegy_sam.png" posX="0" posY="-1.5" posZ="-0.7" rotX="-0.5" rotY="0" rotZ="0" />
    <accessory name="Armor" id="Armor" type="armor" />
    <accessory name="Stinger" id="Stinger" type="stinger" />
  </tehVehicle>
```

Vehicles is the most important thing in Interstate. Wouldnt be much fun without them, right? Ok, lets go through all the syntaxes step by step.

#### The actual vehicle

-   **tehVehicle:** This is the elementname I use for detecting vehicles.
-   **id:** the ID. This should be the name of the vehicle.
-   **model:** the modelnumber, found in vehicles.ide in your gta san andreas/data folder.
-   **image:** This defines what image should be shown on the GUI.
-   **resource:** This tells the gamemode where to look for the images for the vehicle.

#### Primary Weapons

-   **name:** This is the name that is displayed in the GUI.
    -   NOTE: The name MUST be the same as the ID! Otherwise the images WILL screw up!
-   **id:** The id tells the gui where to look for the data
    -   NOTE: The ID MUST BE UNIQUE for all vehicles! I suggest you add spaces, like id=“Minigun” etc.
-   **type:** This tells the script what kind of weapon it is.
    -   Currently only minigun and explosion are reconized.
-   **model:** The object id of the object to attach.
-   **image:** An image to show the weapon in the GUI. Should be the same size as the vehicle image, but with transparent background
-   **posX, posY, posZ:** The position it should attach on.
-   **posX1, posY1, posZ1:** If you want to attach more than one object as primary weapon, define them with “posX1” etc...
    -   A maximum of 4 objects are supported.
-   **rotX, rotY, rotZ:** The rotation of the object.

#### Secondary Weapons

-   **name:** This is the name that is displayed in the GUI.
    -   NOTE: The name MUST be the same as the ID! Otherwise the images WILL screw up!
-   **id:** The id tells the gui where to look for the data
    -   NOTE: The ID MUST BE UNIQUE for all vehicles! I suggest you add spaces, like id=“Minigun” etc.
-   **type:** This tells the script what kind of weapon it is.
    -   sam, sam4, sam8, molotov and mine is supported atm.
-   **model:** The object id of the object to attach.
-   **image:** An image to show the weapon in the GUI. Should be the same size as the vehicle image, but with transparent background
-   **posX, posY, posZ:** The position it should attach on.
-   **posX1, posY1, posZ1:** If you want to attach more than one object as primary weapon, define them with “posX1” etc...
    -   A maximum of 3 objects are supported.
-   **rotX, rotY, rotZ:** The rotation of the object.

#### Accessories

-   **name:** This is the name that is displayed in the GUI.
-   **id:** The id tells the gui where to look for the data
    -   NOTE: the ID does NOT have to be unique for the accessories.
-   **type:** This tells the script what kind of weapon it is.
    -   Only armor and stinger is supported.

Images: How-to add
------------------

Adding your own images for vehicles and weapons in interstate is easy. Just follow theese guidelines and you should be fine.

### Sizing

Images should be in **200x296px** .PNG format. Weapons should be the same size as the vehicle image, but with transparent background.

### Including Images with your map

open up your **meta.xml**.

``` xml
<meta>
    <info author="Lucif3r" description="Interstate" version="1" type="map" gamemodes="Interstate69"/>
    <map src="interstate.map" />
    <file src="elegy.png" />
    <file src="elegy_minigun.png" />
    <file src="elegy_missile.png" />
    <file src="elegy_sam.png" />
</meta>
```

-   **file:** This is where you include your images.
    -   NOTE: You can include as many images as you want. but try to keep the size down.

### Adding the image to the menu

Adding images is a breeze.

Open up your .map-file, and read on.

``` xml
<tehVehicle id="Elegy" model="562" image="elegy.png" resource="Interstate69">
```

-   **image and resource:** This is all you need to change to get your images ingame. Image should be the **filename** of your image, while resource should be the name of your map**resource**
    -   NOTE: You only have to define resource for the **vehicle**, not the weapons. Weapons automaticly reads from the same resource as the vehicle.
    -   NOTE: You can define different resources for different vehicles.

**Example:**

``` xml
<tehVehicle id="Elegy" model="562" image="elegy.png" resource="Interstate69">
```

``` xml
<tehVehicle id="Bandito" model="568" image="bandito.png" resource="Interstate_de" >
```

This tells the gamemode to read all images for **Elegy** from the gamemode itself, Interstate69, and read all images for **Bandito** from the map resource, Interstate\_de.

### Hardcoded vehicleimages

Interstate69 has a few “hardcoded” vehicleimages. Those are:

-   **Elegy**
-   **Bandito**
-   **BF Injection**
-   **Sabre**
-   **Bus**
    -   NOTE: All thats “hardcoded” is the images. They can still be changed by changing the resource argument in the mapfiles.

Example map
-----------

Look at Interstate\_de on tweaks FTP.

OMFG OMFG! I FOUND A BUG!!!
===========================

Im sure you did, but before you come whining to me, please read this list of known bugs and flaws.

-   GUI is not always appearing
-   Textitems overlap eachother
-   Weapons are not being set properly (making you unable to shoot)
-   Sometimes you may spawn at the same location as someone else, causing you to get stuck.
-   Camera position is not being set.
-   The GUI wont disapear.
-   The aim for the secondary weapon is abit off.
-   The primary aim sometimes disapear.
-   Minigun sometimes aint making any damage.
-   ~~Images only work from the gamemode's root folder.~~

If you find something not listed here, that you think needs fixing, give me a shout on IRC.
