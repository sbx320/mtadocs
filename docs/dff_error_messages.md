From time to time DFF files might throw up error messages. These messages were added to find files which could potentially generate hard to reproduce and track down bugs in which the client can crash and tell you as a server owner that something is wrong.

Texture archive corrupt - File size mismatch with section headers, Re-exporting the file is recommended.
--------------------------------------------------------------------------------------------------------

a texture archive in this resource is corrupt and may need attention, this error occurs because sections inside the file are telling the game the file is larger or smaller than it is Textures use the .txd extension, it is recommended to open this up with something like txd editor which can be found online and re-save it which should fix the section headers

DFF file corrupt - File size mismatch with section headers, Re-exporting the file is recommended.
-------------------------------------------------------------------------------------------------

a DFF (model) in this resource is corrupt and may need attention, this error occurs because sections inside the file are telling the game the file is smaller than it is DFFs are models and use the .dff extension

This can be caused by inbuilt collision files being written to the file wrongly, to test this open up the file in RW Analyze and look at the bottom for a “frame extension” this is typically where collision data should be stored.

We are still unsure as to why this models are exported like this so if anyone has some information on this please visit bugs.mtasa.com and report any information you have under the new issues project

DFF file corrupt - frame with name ??? is over the 23 character limit
---------------------------------------------------------------------

A DFF frame name (or node) is beyond the limit of allowed characters this will certainly cause a crash and should be fixed immediately. This can be fixed by re-exporting the DFF file with a smaller name for the part in question.

DFF file corrupt - texture with name ??? is over the 32 character limit
-----------------------------------------------------------------------

A DFF frame name (or node) is beyond the limit of allowed characters this will certainly cause a crash and should be fixed immediately. This can be fixed by re-exporting the DFF file with a smaller name for the part in question

DFF Tried to read beyond the file size, Re-exporting the file is recommended.
-----------------------------------------------------------------------------

a DFF (model) in this resource is corrupt and needs attention, this error occurs because sections inside the file are telling the game the file is larger than the file size.

This model needs re-exporting as it is corrupted.
