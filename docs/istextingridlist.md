<lowercasetitle/>

As the tile says, this function checks if some text exist or not in the GridList.

Syntax
------

``` lua
bool isTextInGridList (element gridList,string text)
```

### Required arguments

-   **gridList**: The grid list element.
-   **text**: The text that you are looking for.

### Return

Returns true if the text exist in the GridList, false if otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua
    function isTextInGridList(gridList, text)
      for i=0, guiGridListGetRowCount(gridlist)-1 do
    local t = guiGridListGetItemText(gridlist, i, 1)
      if (t) then
        if (t == text) then
          return true
        end
        end
    end
    return false
end
```

</section>
Example
-------

<section name="Example" class="client" show="true">
``` lua
    addEventHandler("onClientResourceStart", resourceRoot,
function ()
    playerList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true)
    local column = guiGridListAddColumn(playerList, "Player", 0.85)
    if (column) then
        for id, players in ipairs(getElementsByType("player")) do
            local row = guiGridListAddRow(playerList)
            guiGridListSetItemText(playerList, row, column, getPlayerName(players), false, false)
        end
    end
end)
 

function findText(cmd,text)
  if not tostring(text) then return end 
    if isTextInGridList(playerList, tostring(text)) then
      outputChatBox("Text exist!",0,255,0) 
   end 
end 
addCommandHandler("check",findText)
```

</section>
Author: Walid

See Also
--------
