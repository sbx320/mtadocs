This function creates a socket.

Syntax
------

``` lua
socket sockOpen ( string hostname, int port)
```

### Required arguments

-   **hostname:** The DNS or IP to connect to e.g. “www.google.com”
-   **port:** The port to bind the socket to e.g. 80

### Returns

Returns *userdata* that represents the socket if you correct arguments were given, *false* otherwise.

Example
-------

This piece of code connects to irc.gtanet.com, joins \#mta and quits in 10 seconds.

``` lua
local root = getRootElement()
local ircSocket = sockOpen("irc.gtanet.com",6667)

addEventHandler("onSockOpened",root,
   function (socket)
      if socket == ircSocket then
         sockWrite(socket,"USER mta mta * MCvarial & Gamesnert")
         sockWrite(socket,"NICK mta")
         sockWrite(socket,"JOIN #mta")

         outputServerLog("IRC: Connected!")
         setTimer(disconnect,10000,1)
      end
   end
)

addEventHandler("onSockData",root,
   function (socket,data)
      if socket == ircSocket then
         outputServerLog(data)
      end
   end
)

addEventHandler("onSockClosed",root,
   function (socket)
      if socket == ircSocket then
         outputServerLog("IRC: disconnected!")
      end
   end
)

function disconnect ()
   sockClose(ircSocket)
end
```

See also
--------
