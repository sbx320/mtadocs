This function retrieves a resource's GUI element. The resource's GUI element is the element in the element tree which is the default parent of all GUI elements that belong to a particular resource. This has the tag 'guiroot', and each resource has one of these. You can attach event handlers to this element to easily capture events that originate from your resource (and global events that originate from the root element).

Syntax
------

``` lua
 )
```

### Optional Arguments

-   **theResource:** the resource whose GUI element we are getting. If not specified, assumes the current resource.

### Returns

Returns the root GUI element that contains all the other GUI elements.

Example
-------

This example provides a function for destroying all the GUI elements of a resource.

``` lua
function destroyAllGUIs()
    -- Destroy all of the gui-root's children
    for _, guiElement in ipairs(getElementChildren(getResourceGUIElement())) do
        if isElement(guiElement) then -- This checks that the element still exists (in case we already destroyed it's parent).
            destroyElement(guiElement)
        end
    end
end
```

See Also
--------
