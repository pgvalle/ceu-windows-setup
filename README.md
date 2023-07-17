# ceu windows setup guide

## Installing dependencies
WARNING: This tutorial should work in 32-bit windows but it targets only 64-bit windows. And I tested this in windows 10.
1. [mingw](#mingw-gcc)
2. [java](#java)
3. [sdl2](#sdl2)

### mingw (gcc)
__NOTE__: You should have a file extractor installed, like [winrar](https://www.win-rar.com/start.html?&L=0) or [7zip](https://www.7-zip.org/) (it must support .7z files).\
__BIG BRAIN NOTE__: Don't close the windows you open in step 3. The process to install java is exactly the same.

gcc download link: https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z/download

1. Extract the file and you'll get a folder named mingw64.
2. Rename and place it somewhere (Optional).
3. Add the subfolder mingw64\bin to PATH:
    1. Open mingw64\bin in explorer.
    2. Left-click the path bar in a blank area, then copy the highlighted text.
    3. Type "environment variables" in the search bar and hit Enter.
    4. Click on "Environment Variables...". You will see a window with 2 sections: "User variables for {your-username}" and "System variables". Both have an entry named "Path".
    5. Double-click one of those entries (user one recommended)
    6. Click on "New", hit Ctrl+v and then Enter.
4. Open up a command prompt (type cmd in the search bar then hit enter), type gcc and hit enter. If you see "gcc: fatal error: ...", it worked.

### java

java 11 download link: https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip

Now repeat the process to install gcc. But in the end type java instead of gcc. If you see a big output, it worked.

### sdl2