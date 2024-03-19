## Dependencies

1. MinGW (gcc)
2. SDL2
3. Java

## Installing MinGW

Go to [winlibs.com](https://winlibs.com/) and get any gcc release for Win64 with POSIX threads. I recommend a more recent version, though.

Extract the (7-)zip file. You'll get a folder named mingw64/. Place it somewhere in your drive. Preferably not within a system directory or other users' directories.

Then you should add .../mingw64/bin/ to the Path environment variable. Here's a quick tutorial to help you with that: https://www.youtube.com/watch?v=EuoEYPLtsZ8

To check out if gcc is working, open up cmd and try running ```gcc --version```

## Installing SDL2

To facilitate things here, I created a sdl2-bundle zip so that you don't have trouble downloading and building everything. Just go to the releases page of this repo. You'll find it there.

Extract the zip file. There will be three folders: bin/, include/ and lib/.

Copy bin/ and paste it inside .../mingw64/.

Copy both include/ and lib/, then paste them inside .../mingw64/x86_64-w64-mingw32/

## Installing Java

I have a link to an openjdk release. Which is the one I used, of course: https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip

Extract the zip archive. You'll get a folder named jdk-11.0.2/. Now repeat the exact same process you did to setup gcc.

## Installing ceu

Download [ceu](https://github.com/fsantanna/dceu) (releases page), [pico-ceu](https://github.com/fsantanna/pico-ceu) and [pico-sdl](https://github.com/fsantanna/pico-sdl).

Extract the zip files.

Create the following folder structure:
```
ceu/
  ceu
  ceu.jar
  hello-world.ceu
  prelude.ceu
  pico/ (pico-ceu)
    README.md
    ceu.lib
    pico-0.ceu
    pico-x.ceu
    pico.ceu
    tst/
      ...
    sdl/ (pico-sdl)
      Makefile
      README.md
      open.png
      start.wav
      tiny.ttf
```

Open ceu/pico/ceu.lib with a text editor and add ```-lmingw32 -lSDL2main``` at the beginning.

Open ceu/pico/sdl/src/pico.h and add ```#include <stdio.h>``` at the top.

Download ceu.bat in this repo Releases page and place it inside ceu/.

## Testing ceu

__IMPORTANT__: Do __NOT__ forget to pass ```--lib=pico``` when compiling graphical apps and do __NOT__ use Windows path style. Use Unix path style. That basically means you must use ```/``` instead of ```\``` in any path you pass to ceu.

Open command prompt or powershell, cd into where ceu.jar is and run these commands:
```
ceu.bat hello-world.ceu
ceu.bat pico/tst/par.ceu --lib=pico
```
