<lowercasetitle/>

This class implements the lua coroutines and can be used to limit method calls to a specific amount / second. This can be very useful when loading big amounts of data on gamemode startup to avoid an infinite running script and termination.

Requirements
------------

*Knowledge*

Code
----

``` lua
--
-- Created by IntelliJ IDEA.
-- User: Noneatme
-- Date: 25.01.2015
-- Time: 14:33
--

cThread = {}
cThread.__index     = cThread;


Threads     = {}


function cThread:new(...)
    local obj = setmetatable({}, {__index = self});
    if obj.constructor then
        obj:constructor(...);
    end
    return obj;
end

function cThread:constructor(sName, func, iAmmounts)
    assert(Threads[sName] == nil);
    self.name = sName
    self.func = func

    self.iAmmounts = iAmmounts or 1;
--  outputConsole("[TRHEAD: "..sName.."] Constructor");

    Threads[sName]  = self;
end

function cThread:start(iMS)
    self.thread = coroutine.create(self.func)
    self.yields = 0;

    self.lastTickCount  = getTickCount();

    self:resume()

    self.timer  = setTimer(function()
        if(self:status() == "suspended") then
            if(getTickCount()-self.lastTickCount > 5000) then
                self.lastTickCount = getTickCount();
 --             outputConsole("[THREAD: "..self.name.."] Current Yields: "..self.yields);
            end
            for i = 1, self.iAmmounts, 1 do
                self.yields = self.yields+1;
                self:resume();
            end
        end

        if(self:status() == "dead") then
            killTimer(self.timer);
            self:stop()
        end
    end, iMS, -1)
end

function cThread:resume()
    coroutine.resume(self.thread)
end

function cThread:stop()
    self.thread = nil

--  outputConsole("[THREAD: "..self.name.."] Completed, Yields: "..self.yields);
end

function cThread:status()
    return coroutine.status(self.thread)
end
```

Example
-------

This example shows an UserVehicleManager class combined with a Thread which loads all vehicles from a specific database table on server startup.

<section name="Example" class="server" show="true">
``` lua
local CUserVehicleManager = inherit(cSingleton)

function CUserVehicleManager:createVehicles()
    local result = CDatabase:getInstance():query("SELECT * FROM user_vehicles;")           -- Big amount of data (> 10000 rows)
    if(result) and (#result > 0) then       -- Are there any vehicles?
        for index, row in pairs(result) do  -- Loop through the resultset
            Vehicle(unpack(row));           -- Create the Vehicle
            coroutine.yield()               -- Yield back to the thread manager, without the coroutine, the script will abort the loop (infinite running script)
        end
    end
end

function CUserVehicleManager:constructor()
    self.loadFunc       = function() self:createVehicles() end      -- The coroutine main loop function
    self.thread         = cThread:new("User Vehicle Loading Thread", self.loadFunc, 5) -- Limit to 5 yields / call
    self.thread:start(50);                                          -- Begin the loading process, limited to 5 yields / 50 miliseconds
end
```

</section>
See Also
--------
