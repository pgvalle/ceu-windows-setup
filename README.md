## Notice

[ceu](https://github.com/fsantanna/dceu) (repo) is a synchronous programming language created by Francisco Figueiredo Goytacaz Sant'anna.
It allows you to use Concurrency alongside Event-Driven Programming in a structured manner, extending the classical structured paradigm we all know and use.

Here's the official website (Old Version): http://ceu-lang.org/.

## Dependencies

1. MinGW (gcc)
2. SDL2
3. Java

## Installing MinGW

Go to [winlibs.com](https://winlibs.com/) and get any gcc release for Win64 with POSIX threads. I recommend a more recent version, though.

Extract the (7-)zip file. You'll get a folder named mingw64/.

Place it somewhere in your drive. Preferably not within a system directory or other users' directories.

Then you should add .../mingw64/bin/ to the Path environment variable. Here's a quick tutorial to help you with that: https://www.youtube.com/watch?v=EuoEYPLtsZ8

To check out if gcc is working, open up cmd and try running `gcc --version`

## Installing SDL2

To facilitate things here, I created a sdl2-bundle zip so that you don't have trouble downloading and building everything.
Just go to the releases page of this repo. You'll find it there.

Download and extract the zip file. There will be three folders: bin/, include/ and lib/.

Copy bin/ to .../mingw64/.

Copy both include/ and lib/ to .../mingw64/x86_64-w64-mingw32/

## Installing Java

I have a link to an openjdk release. Which is the one I used, of course: https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip

Extract the zip file. You'll get a folder named jdk-11.0.2/.

Place it somewhere in your drive. Preferably not within a system directory or other users' directories.

Then you should add .../jdk-11.0.2/bin/ to the Path environment variable. Here's a quick tutorial to help you with that: https://www.youtube.com/watch?v=EuoEYPLtsZ8

To check out if java is working, open up cmd and try running `java --version`

## Installing ceu

Download [ceu](https://github.com/fsantanna/dceu/releases/download/v0.3.1/ceu-v0.3.1.zip) (v3.1),
[pico-ceu](https://github.com/fsantanna/pico-ceu/archive/refs/heads/main.zip) and [pico-sdl](https://github.com/fsantanna/pico-sdl/archive/refs/heads/main.zip).

Extract the zip files.

Create the following folder structure:
```
ceu/
  ceu
  ceu.jar
  hello-world.ceu
  prelude.ceu
  pico/ (originally pico-ceu-main folder)
    README.md
    ceu.lib
    pico-0.ceu
    pico-x.ceu
    pico.ceu
    tst/
      ...
    sdl/ (originally pico-sdl-main folder)
      Makefile
      README.md
      open.png
      start.wav
      tiny.ttf
```

Replace ceu/pico/ceu.lib with the ceu.lib of this repo's releases page.

Go to ceu/pico/, delete pico.ceu and rename pico-x.ceu to pico.ceu.

(Optional) Delete ceu/ceu. It's a bash script, so it won't serve any purpose.

Download ceu.bat from this repo Releases page and place it inside ceu/.


## Testing ceu

__IMPORTANT__: Do __NOT__ forget to pass ```--lib=pico``` when compiling graphical apps and do __NOT__ use Windows path style;
use Unix path style. That basically means you must use ```/``` instead of ```\``` in any path you pass to ceu.

Go to ceu/ inside cmd or powershell and run these commands:
```
ceu.bat hello-world.ceu
ceu.bat pico/tst/{test-program-filename} --lib=pico
```
