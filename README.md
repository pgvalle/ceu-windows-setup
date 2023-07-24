# ceu windows setup guide

## Installing dependencies

__WARNING__: This tutorial was tested only in windows 10 64bit.

### mingw (gcc)

__NOTE__: You should have a file extractor installed, like [winrar](https://www.win-rar.com/start.html?&L=0) or [7zip](https://www.7-zip.org/) (it must support .7z files).\
__BIG BRAIN NOTE__: Don't close the windows you open in step 3. The process to install java is exactly the same.

download link: https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z/download

1. Extract the file and you'll get a folder named mingw64.
2. Rename and place it somewhere (Optional).
3. Add the subfolders mingw64\\bin to PATH:
    1. Open mingw64\\bin in explorer.
    2. Left-click the path bar in a blank area, then copy the highlighted text.
    3. Type "environment variables" in the search bar and hit Enter.
    4. Click on ```Environment Variables...``` You will see a window with 2 sections: ```User variables for {your-username}``` and ```System variables```. Both have an entry named ```Path```.
    5. Double-click one of those entries (user one recommended).
    6. Click on ```New```, hit ```Ctrl+v``` and then Enter.
4. Open up a command prompt or powershell and run ```gcc```. If you see ```gcc: fatal error: ...``` it worked.

### sdl2

1. Go to this repo Releases page and download sdl2-bundle-64bit.zip.
2. Extract the file. You will get three folders: bin, include and lib.
3. Copy include and lib then paste them inside the subfolder mingw64\\x86_64-w64-mingw32.
5. Go to the bin folder you extracted and copy everything inside of it.
6. Go to mingw64\\bin and paste.

### java

Download link: https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip \
Now repeat the process to install gcc. But in the end type java instead of gcc. If you see a big output, it worked.

## Installing ceu

Download links:\
https://github.com/fsantanna/dceu/releases/download/v0.2.1/ceu-v0.2.1.zip (ceu)\
https://github.com/fsantanna/pico-ceu/archive/27a1d54699dee3c1566382736b9bfb02096c7e7c.zip (pico-ceu)\
https://github.com/fsantanna/pico-sdl/archive/refs/heads/main.zip (pico-sdl)

1. Extract ceu-v0.2.1.zip to a folder.
2. Extract pico-ceu and rename the output folder to pico.
3. Open pico\\ceu.lib with a text editor and add ```-lmingw32 -lSDL2main``` in the beginning of it
4. Extract pico-sdl and rename the output folder to sdl.
5. Open sdl\\src\\pico.h and add ```#include <stdio.h>``` at the top
6. Place sdl inside pico.
7. Place pico inside the folder you extracted ceu-v0.2.1.zip to.
8. Download ceu.bat in this repo Releases page and place it where you placed pico.

## Testing ceu

__IMPORTANT__: Do __NOT__ forget to pass ```--lib=pico``` when compiling pico apps and do __NOT__ use ```\``` in any path you pass to ceu. Always use ```/```.

Open command prompt or powershell, cd into where ceu.jar is and run these commands:\
```ceu.bat hello-world.ceu```\
```ceu.bat pico/tst/par.ceu --lib=pico```