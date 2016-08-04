<pageclass class="resource" subcaption="Script"></pageclass> This page lists all the gui class objects. This will only work with: <http://community.mtasa.com/index.php?p=resources&s=details&id=241>

This system is created by the well known 50p!

GUI Classes made scripting gui objects easier!

Installation
------------

The installation is pretty simple. All you need to do is copy and paste folder **“gui\_class/classes/”** into your resource which you want to use these classes in. Then just copy specified lines from **“gui\_class/meta.xml”** into your meta.xml. As you know gui\_class is not actually a resource that you can use exported functions of. It just includes all the classes that make scripting GUI cleaner, so that's why you have to copy the directory and include the files which are inside into meta.xml to tell the server/client which files you're using (that is, the classes you want to use).

You can also start gui\_class resource and uncomment some examples which are located in **“test.lua”**

Useful information
------------------

Once you create a GUI Object, it has a bunch of variables that you can access. One of them is **.gui** which represents the gui element that can be used with native GUI functions. Lets say, you want to use guiSetVisible() and you don't want to use object:Visible() then you can do so like this:

``` lua
-- create our object
local button = Button:Create( 10, 200, 100, 18, "Woot!" );
-- now use native GUI function
guiSetVisible( button.gui, false );
```

Classes
-------

### Button class

### Check Box class

### Gridlist class

### Label class

### Memo class

### Progress Bar class

Progress bar with this class is a little bit different from the native one. What's different is that I added a label on top, so that you can have a progress bar with some text on it.

### Radio Button class

### Scroll Bar class

### Static Image class

### Tab class

### Tab panel class

### Text Box class (formally known as Edit)

### Window class

### Shared methods with all classes