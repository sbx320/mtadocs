This function renames a resource.

Syntax
------

``` lua
bool renameResource ( string resourceName, string newResourceName, [ string organizationalPath ] )
```

### Required Arguments

-   **resourceName:** The name of resource to rename.
-   **newResourceName:** The name of what the resource should be renamed to.

### Optional Arguments

-   **organizationalPath:** If you want to store the new resource inside a category.

### Returns

Returns *true* if the resource has been renamed successfully, *false* otherwise. This could fail if the resource name already is in use, if a directory already exists with the name you've specified (but this isn't a valid resource) or if the name you specify isn't valid. It could also fail if the disk was full or for other similar reasons. Won't work on a started resource or if the resource is not loaded (not known by MTA (use /refresh))

Example
-------

This example renames the resource “reload” to “reload2”:

``` lua
function renameReloadResource()
    renameResource("reload", "reload2");
end
addEventHandler("onResourceStart", resourceRoot, renameReloadResource);
```

Requirements
------------

See Also
--------
