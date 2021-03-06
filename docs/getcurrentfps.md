<lowercasetitle/>

This clientside useful function returns the current *FPS* (frames per second) at which GTA: SA is running.

Syntax
------

``` lua
float/boolean getCurrentFPS( )
```

Returns
-------

This function returns a *number* telling the current *FPS* if they could be calculated. Returns *false* otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua
local fps = false
function getCurrentFPS() -- Setup the useful function
    return fps
end

local function updateFPS(msSinceLastFrame)
    -- FPS are the frames per second, so count the frames rendered per milisecond using frame delta time and then convert that to frames per second.
    fps = (1 / msSinceLastFrame) * 1000
end
addEventHandler("onClientPreRender", root, updateFPS)
```

</section>
-   Original author: *StiviK*.

Examples
--------

The next example draws the current *FPS* rounded to an integer in the up-right corner of the screen.

``` lua
local sx = guiGetScreenSize()
local function drawFPS()
    if not getCurrentFPS() then
        return
    end
    local roundedFPS = math.floor(getCurrentFPS())
    dxDrawText(roundedFPS, sx - dxGetTextWidth(roundedFPS), 0)
end
addEventHandler("onClientHUDRender", root, drawFPS)
```

The next script mitigates *FPS* variations by setting the *FPS* limit to the average *FPS* of the last 5 seconds.

``` lua
local function getAverageFPSOfFPSArray(table)
    -- Average FPS = (FPS1 + FPS2 + ... + FPSX) / X
    local totalFPS = 0
    for _, fps in pairs(table) do
        totalFPS = totalFPS + fps
    end
    return totalFPS / #table
end

local currentSecondFPS = {}
local lastSecondTicks = getTickCount()
local lastFiveSecondsFPS = {}
local function smoothFPS()
    -- Do we have a FPS rate already?
    if not getCurrentFPS() then
        return
    end
    -- Insert current FPS into a table for reference
    table.insert(currentSecondFPS, getCurrentFPS())
    -- If a second passed, get the average FPS using the table
    -- (We always have at least one frame rendered, so dividing by 0 it's not a problem)
    if getTickCount() - lastSecondTicks >= 1000 then
        local averageFPSPerSecond = getAverageFPSOfFPSArray(currentSecondFPS)
        -- Reset variables
        currentSecondFPS = {}
        lastSecondTicks = getTickCount()
        -- Update the table containing last five seconds FPS
        -- Also update the FPS limit accordingly
        table.insert(lastFiveSecondsFPS, averageFPSPerSecond)
        -- Silently discard too old average FPS
        if #lastFiveSecondsFPS == 6 then
            table.remove(lastFiveSecondsFPS, 1)
        end
        -- Get the average FPS of the average FPS of each of the last five seconds, and use the result as the frame limit
        setFPSLimit(math.ceil(getAverageFPSOfFPSArray(lastFiveSecondsFPS)))
    end
end
addEventHandler("onClientHUDRender", root, smoothFPS)
```

See also
--------
