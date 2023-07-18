# ceu windows setup guide
## Known issues
__No executable for graphical apps__: ceu keeps generating the .exe forever when compiling graphical apps, but you can get the .c output file and compile it with gcc.\
__Worse in powershell__: Compiling ceu command-line apps in powershell doesn't give you an executable as well. But waiting a couple seconds and hitting Ctrl+c makes the .exe appear.

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
    4. Click on "Environment Variables...". You will see a window with 2 sections: "User variables for {your-username}" and "System variables". Both have an entry named "Path".
    5. Double-click one of those entries (user one recommended).
    6. Click on "New", hit Ctrl+v and then Enter.
4. Open up a command prompt (type cmd in the search bar then hit enter), type gcc and hit enter. If you see "gcc: fatal error: ...", it worked.

### sdl2

1. Go to the latest release in Releases page and download sdl2-bundle-64bit.zip.
2. Extract the file. You will get three folders: bin, include and lib.
3. Copy include and lib then paste them inside the subfolder mingw64\\x86_64-w64-mingw32.
5. Go to the bin folder you extracted and copy everything inside of it.
6. Go to mingw64\\bin and paste.

### java

download link: https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip

Now repeat the process to install gcc. But in the end type java instead of gcc. If you see a big output, it worked.

## Installing ceu

download links:\
https://github.com/fsantanna/dceu/releases/download/v0.2.1/ceu-v0.2.1.zip (ceu)\
https://github.com/fsantanna/pico-ceu/archive/27a1d54699dee3c1566382736b9bfb02096c7e7c.zip (pico-ceu)
https://github.com/fsantanna/pico-sdl/archive/refs/heads/main.zip (pico-sdl)

1. Extract ceu-v0.2.1.zip to a folder.
2. Extract pico-ceu and rename the output folder to pico.
3. Extract pico-sdl and rename the output folder to sdl.
4. Open sdl\src\pico.h and at the top add "#include <stdio.h>" without the quotes
4. Place sdl inside pico.
5. Place pico inside the folder you extracted ceu-v0.2.1.zip to.

## Testing ceu

### No graphics

__REMINDER__: If you are using powershell, be aware it leads to a bug listed [here](#known-issues).

Open a command prompt, cd into the directory where ceu.jar is and run this command:\
```java -Xmx500M -Xms500M -ea -cp ceu.jar dceu.MainKt hello-world.ceu```

### With graphics (pico)

1. Run this command:\
```java -Xmx500M -Xms500M -ea -cp ceu.jar dceu.MainKt ./pico/tst/par.ceu --verbose```
2. When you see ```... c -> exe ...``` press Ctrl+c.
3. Now run this command:\
```gcc par.c -o par -lmingw32 -lSDL2main -lSDL2 -lSDL2_gfx -lSDL2_image -lSDL2_ttf -lSDL2_mixer -include ./pico/sdl/src/hash.c -include ./pico/sdl/src/pico.c```
4. Run par.exe