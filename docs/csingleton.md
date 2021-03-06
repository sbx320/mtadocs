<lowercasetitle/>

This class allows you to restrict the instantiation of a specific class to one object.

Requirements
------------

sbx320's classLib, can be found Here[1](https://github.com/sbx320/lua_utils/blob/master/classlib.lua)

Code
----

``` lua
Singleton = {}

function Singleton:getSingleton(...)
    if not self.ms_Instance then
        self.ms_Instance = self:new(...)
    end
    return self.ms_Instance
end

function Singleton:new(...)
    self.new = function() end
    local inst = new(self, ...)
    self.ms_Instance = inst
    return inst
end

function Singleton:isInstantiated()
    return self.ms_Instance ~= nil
end

function Singleton:virtual_destructor()
    for k, v in pairs(super(self)) do
        v.ms_Instance = nil
        v.new = Singleton.new
    end
end
```

Original Author: Jusonex

Example
-------

See Also
--------
