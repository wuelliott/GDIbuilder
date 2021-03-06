GDIbuilder
==========

Utility to assist with building Dreamcast .gdi images from scratch

When provided with a folder of data files, the IP.BIN bootsector, and optional raw CDDA tracks, 
this tool will automatically generate the data track(s) for the high density area of a GD-ROM image.
It also generates the track TOC which is written into the bootsector.

A bootable GD-ROM requires the primary executable (usually called 1ST_READ.BIN) to be placed at the
end of the final data track or it will not be loaded by the console. This requirement does not exist 
for MIL-CD's.

ISO9660 code was forked from .NET DiscUtils, with a number of modifications made:
- When Joilet is disabled (which it is for this tool), don't output supplementary file tables
- Reversed the order that DiscUtils outputs the ISO sections. (Directory Tables come before files now)
- Fixed bug in non-joilet filename output. Filenames were not being appended with ;1 like they should be.
- Added Start LBA offset for entire image
- Added End LBA offset for entire image. Image will be padded to desired size.
- Added End of last file LBA, if set all files will be pushed back in the image to this location.
- Added properties to set most of the text identifiers (Application, Volume Set, Preparer, etc.)
- Removed stuff not being used by this application, such as other image formats and filesystems.
