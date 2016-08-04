Syntax
------

``` lua
 )
```

### Required Arguments

-   **width:** The browser's native width
-   **height:** The browser's native height
-   **isLocal:** Sets whether the browser can only show local content or content from the internet (see examples for more information)

''

### Optional Arguments

-   **transparent:** *true* if you want the browser transparent, *false* for opaque.

### Returns

Returns an [texture](/texture.md "wikilink") of the [browser](/browser.md "wikilink") if it was created successfully, *false* otherwise. Returns also *false*, if the user disabled remote pages and *isLocal* was set to *false*.

Local Example
-------------

This example shows you how to create a fullscreen web browser (showing a local html file) without input-handling.

``` lua
--In order to render the browser on the full screen, we need to know the dimensions.
local screenWidth, screenHeight = guiGetScreenSize()

--Let's create a new browser in local mode. We will not be able to load an external URL.
local webBrowser = createBrowser(screenWidth, screenHeight, true, false)
    
--This is the function to render the browser.
function webBrowserRender()
    --Render the browser on the full size of the screen.
    dxDrawImage(0, 0, screenWidth, screenHeight, webBrowser, 0, 0, 0, tocolor(255,255,255,255), true)
end

--The event onClientBrowserCreated will be triggered, after the browser has been initialized.
--After this event has been triggered, we will be able to load our URL and start drawing.
addEventHandler("onClientBrowserCreated", webBrowser, 
    function()
        --After the browser has been initialized, we can load our file.
        loadBrowserURL(webBrowser, "http://mta/local/html/site.html")
        --Now we can start to render the browser.
        addEventHandler("onClientRender", root, webBrowserRender)
    end
)
```

Remote Example
--------------

This example shows you how to create a fullscreen web browser (showing youtube.com) without input-handling.
Remember, that youtube.com is on the global whitelist. If you want to load a domain/page that is not on the global whitelist, you have to request it with [requestBrowserDomains](/requestBrowserDomains.md "wikilink").

``` lua
--In order to render the browser on the full screen, we need to know the dimensions.
local screenWidth, screenHeight = guiGetScreenSize()

--Let's create a new browser in remote mode.
local webBrowser = createBrowser(screenWidth, screenHeight, false, false)
    
--Function to render the browser.
function webBrowserRender()
    --Render the browser on the full size of the screen.
    dxDrawImage(0, 0, screenWidth, screenHeight, webBrowser, 0, 0, 0, tocolor(255,255,255,255), true)
end

--The event onClientBrowserCreated will be triggered, after the browser has been initialized.
--After this event has been triggered, we will be able to load our URL and start drawing.
addEventHandler("onClientBrowserCreated", webBrowser, 
    function()
        --After the browser has been initialized, we can load www.youtube.com
        loadBrowserURL(webBrowser, "http://www.youtube.com")
        --Now we can start to render the browser.
        addEventHandler("onClientRender", root, webBrowserRender)
    end
)
```

See Also
--------