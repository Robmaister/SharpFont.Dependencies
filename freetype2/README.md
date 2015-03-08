FreeType2
=========

This directory contains all of the FreeType2 builds, a copy of the FreeType
Project License, and a patch file for when compiling new versions of freetype
for 64-bit Windows.

## Windows x64

A patch file, [win64.patch][1], is included in this directory that will force
several types to be 64 bits wide. On Linux and OS X, the native `long` type is
64 bits wide on x64, but on Windows, it's still 32 bits wide for backwards
compatibility of applications assuming `sizeof(long) == sizeof(int)`. A list
of the affected types:

  - `FT_Long`
  - `FT_ULong`
  - `FT_Fixed`
  - `FT_F26Dot6`
  - `FT_Pos`
  
To apply the patch file, you need a copy of the `patch` utility built for
Windows. If using msysgit, it is already installed and is available from Git
Bash. Otherwise, a build is available from [GnuWin32][2]. Utilities such as
TortoiseDiff can provide a graphical way to do this same task.

After downloading and decompressing FreeType2, copy `win64.patch` into the
root folder (i.e. the folder containing `builds/`, `/include`, `/src`, etc.)
and run the following command:

```
patch -p0 < win64.patch
```

[1]: https://github.com/Robmaister/SharpFont.Dependencies/blob/master/freetype2/win64.patch
[2]: http://gnuwin32.sourceforge.net/packages/patch.htm
