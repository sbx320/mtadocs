This function find useful in the form of loading may be able to use guiCreateProgressBar but this function facilitates you the piece and increase as dx form and can easily control the shape and color , speed and you must use onClientRender to doing a function, because function mobile you use , and function do not bring a lot of least thus be I benefited a lot instead of ProgressBar

-   **This is made to be used clientside!.**

Syntax
------

[thumb|An example of how dxDrawLoading function works in practice.](/docs/file:mta-screen_2015-08-28_10-47-28.png.md "wikilink")

``` lua
bool dxDrawLoading ( int posX, int posY, int width , int height , int posX2 , int posY2 [ int size = 1.00 , int color = black , int color2 = green ,  int time  = 5000 ] )
```

Required Arguments
------------------

-   **posX:** x coordinates of the form
-   **posY:** y coordinates of the form
-   **width:** Display format
-   **height:** Length figure
-   **posX2:** Writing for the coordinates x
-   **posY2:** Writing for the coordinates y

Optional Arguments
------------------

-   **size:** size Text
-   **color:** Color hard form produced using tocolor
-   **color2:** Color animated form produced using tocolor
-   **time:** time for end Loading

Code :
------

<section name="Client" class="client" show="true">
``` lua
local start = getTickCount()
function dxDrawLoading (x, y, width, height, x2, y2, size, color, color2, second)
    local now = getTickCount()
    local seconds = second or 5000
    local color = color or tocolor(0,0,0,170)
    local color2 = color2 or tocolor(255,255,0,170)
    local size = size or 1.00
    local with = interpolateBetween(0,0,0,width,0,0, (now - start) / ((start + seconds) - start), "Linear")
    local text = interpolateBetween(0,0,0,100,0,0,(now - start) / ((start + seconds) - start),"Linear")
    dxDrawText ( "Loading ... "..math.floor(text).."%", x2, y2 , width, height, tocolor ( 0, 255, 0, 255 ), size, "pricedown" )
    dxDrawRectangle(x, y ,width ,height -10, color)
    dxDrawRectangle(x, y, with ,height -10, color2)
 end
```

</section>
Example :
---------

<section name="Client" class="client" show="true">
``` lua
    sx ,sy = guiGetScreenSize()
        function dxLoad ()
            local now = getTickCount()
        dxDrawLoading(196*sx/800, 482*sy/600,422*sx/800, 58*sy/600, 196*sx/800 , 450*sy/600 ,1.00*sx/800,tocolor(0,0,0,170),tocolor(0,255,0,170),10000)
        if now > start + 10000 then
        start = getTickCount()
        outputChatBox("Done Downloading",0,255,0)
        removeEventHandler("onClientRender",root,dxLoad)
        end
        end
    addEventHandler("onClientRender",root,dxLoad)
```

</section>
<section name="Client" class="client" show="true">
``` lua
sx ,sy = guiGetScreenSize()
cx, cy = 1440, 900
button = guiCreateButton(313*sx/cx, 354*sy/cy, 162*sx/cx, 24*sy/cy,"",false)
guiSetVisible(button, false)

local start = getTickCount()
    function dxx ()
    local now = getTickCount()
    local wi, hi = interpolateBetween(0,0,0,757*sx/cx,682*sy/cy,0, ( now - start ) / (( start + 5000 ) - start),  "Linear")
    local wit, hit = interpolateBetween(0, 0, 0, b1, b2, 0, (now - start) / ((start + 5000) - start), "Linear")
    dxDrawRectangle(319*sx/cx, 109*sy/cy, wi, hi, tocolor(0, 0, 0, 130), false)
    if now > start + 5000 then
    addEventHandler("onClientRender",root,dd)
    addEventHandler("onClientClick",root,Buton)
    showCursor(true)
    guiSetVisible(button, true)
    guiSetAlpha(button, 0)
    end
end
    function dd ()
    dxDrawRectangle(313*sx/cx, 354*sy/cy, 162*sx/cx, 24*sy/cy, tocolor(255,255,255, 255), false)
    end
function dxxx ()
    now = getTickCount()
    local wi, hi = interpolateBetween(757*sx/cx,682*sy/cy,0,0,0,0, ( now - start ) / (( start + 5000 ) - start),  "Linear")
    dxDrawRectangle(319*sx/cx, 109*sy/cy, wi, hi, tocolor(0, 0, 0, 130), false)
    end
        function dxLoad ()
            local now = getTickCount()
        dxDrawLoading(196*sx/800, 482*sy/600,422*sx/800, 58*sy/600, 196*sx/800 , 450*sy/600 ,1.00*sx/800,tocolor(255,255,255,170),tocolor(0,0,255,170),5000)
        if now > start + 5000 then
        start = getTickCount()
        outputChatBox("Done Downloading",0,255,0)
        removeEventHandler("onClientRender",root,dxLoad)
        addEventHandler("onClientRender",root,dxx)
            end
        end
    addEventHandler("onClientRender",root,dxLoad)
    addEventHandler("onClientGUIClick",button,
        function ()
        now = getTickCount()
        playSoundFrontEnd(3)
        start = getTickCount()
            addEventHandler("onClientRender",root,dxxx)
            removeEventHandler("onClientRender",root,dxx)
            removeEventHandler("onClientRender",root,dd)
            removeEventHandler("onClientClick",root,Buton)
            showCursor(false)
            guiSetVisible(button, false)
            if now > start + 5000 then
            removeEventHandler("onClientRender",root,dxxx)
        end
end)
```

</section>
Author : LoOs

See Also
--------
