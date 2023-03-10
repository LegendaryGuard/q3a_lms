Q3A Last Man Standing source code
===============================

A Quake 3 Arena gamemode was started from the late 90s to early 2000s.

<p align="center">
<img alt="q3lms" src="https://user-images.githubusercontent.com/49716252/195073433-66257e71-5b48-43f7-b8ff-afd81884dd8f.jpg" width=450 />
</p>

### History

Started: 1999 <br/> 
Ended: 2000

Last Man Standing (LMS for short) is a free for all variant of Elimination with a few minor twists.

The game is played in rounds. The goal of the game is to survive for as long as possible in each round and preferably make sure that your closest competitors don't survive for too long.

Each player begins with all weapons (ammo quantity selectable using variables), can't hurt himself with his own weapons, and there are no items in the maps. When you get fragged, you will have to wait until the end of the round.

By default Overtime (OT) is used so there can be at most 1 survivor each round.

Players might have multiple lives. If you set \g_lms_lives higher than 1, players will have more lives before they are out from each round: when someone is killed, he immediately returns in game (like in standard Free For All mode); when he runs out of lives, he will have to wait until the end of the round. You can see players' lives holding TAB key.

### How to build

- ### Windows:

* #### _Building QVM_: 

Execute `build.bat` to compile qvms, keep in mind you must be in the repository directory.

Once compiled successfully, look for `pak9.pk3`, copy and paste into `baseq3/` or mod Q3 game directory.

* #### _MSYS2 (mingw) (Building dynamic libraries (.dll))_:

IMPORTANT NOTE: Not tested on Windows 32-bit. MSYS2 comes with multilib disabled in gcc (means you can't compile for x86 in a 64-bit system), more info [here](https://sourceforge.net/p/msys2/discussion/general/thread/3941f2c9/).


To build, follow these instructions:

1. Install msys2 from https://msys2.github.io/, following the instructions there.It doesn’t matter which version you download, just get one appropriate for your OS.

2. Start "MSYS2 MinGW 64-bit" from the Start Menu. If you're using 32-bit system, use "MSYS2 MinGW 32-bit".

3. Install mingw-w64-x86_64-gcc:
```sh
pacman -S mingw-w64-x86_64-gcc
```
32-bit:
```sh
pacman -S mingw-w64-i686-gcc
```
4. Install make:
```sh
pacman -S make
```

5. Compile with make
```sh
make ARCH=x86_64
```
32-bit:
```sh
make ARCH=x86 WINDRES="windres -F pe-i386"
```

6. Find the dlls in `build/release-mingw64-x86_64`, for 32-bit: `build/release-mingw32-x86`. <br/>

If you can't compile 32-bit builds with MSYS2 MinGW, try [Cygwin](#cygwin-mingw-building-dynamic-libraries-dll) section.<br/>

* #### _Cygwin (mingw) (Building dynamic libraries (.dll))_: 

Detailed guide based on a [post by MAN-AT-ARMS](https://discourse.ioquake.org/t/how-to-build-ioquake3-using-cygwin/223).

1. Install Cygwin

Download the Cygwin setup package from http://cygwin.com/install.html.

Choose either the 32-bit or 64-bit environment. 32-bit will work fine on both 32 and 64 bit versions of Windows. The setup program is also your Cygwin environment updater. If you have an existing Cygwin environment, the setup program will, by default, update your existing packages.

Choose where you want to install Cygwin. The entire environment is self-contained in it's own folder, but you can also interact with files from outside the environment if you want to as well. The default install path is `C:\Cygwin`.
Choose a mirror to download packages from, such as the [kernel.org](https://kernel.org/) mirrors.
Choose a "storage area" for your package downloads.

2. Package selection

The next screen you see will be the package selections screen. In the upper left is a search box. This is where you will want to search for the necessary packages.

These are the package names you'll want to search for:

1- `mingw64-i686-gcc-core` (For building 32bit binaries)<br/>
2- `mingw64-i686-gcc-g++` (Also for 32bit... C++ support... not required for the game, but useful for compiling other software)<br/>
3- `mingw64-x86_64-gcc-core` (For building 64bit binaries)<br/>
4- `mingw64-x86_64-gcc-g++` (For 64bit, same as above)<br/>
5- `make`<br/>
6- `bison`<br/>
7- `git`

- ### Linux:

* #### _Building QVM_: 

The alternative to execute and get the compiled qvms with `build.bat` requires [`wine` package](https://www.winehq.org/). So, in that part, needs the i386 package:
```sh
sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install wine32-development
```
But it could be executed without using 32-bit package, if your system supports 64-bits. Go to WineHQ page anyways.

Keep in mind, you must be in the repository directory to execute the script:
```sh
wine cmd /c build.bat
```

Once compiled successfully, look for `pak9.pk3`, copy and paste into `baseq3/` or mod Q3 game directory.

NOTE: until now, there's no fully compileable QVM tool found for Linux.

* #### _Building shared libraries (.so)_:

If you don't have gcc tools, install the build-essential packages, which is also known as a meta-package, it contains the GCC compiler all the other essentials used to compile the software written in C and C++ language.
Also, requires `libc6-dev-i386` for x86 builds and `g++-multilib` and `gcc-mingw-w64` for cross-compiling. More info about MinGW question in Linux [here](https://stackoverflow.com/questions/44389963/how-to-install-mingw32-on-ubuntu).
```sh
sudo apt-get install build-essential libc6-dev-i386 g++-multilib gcc-mingw-w64
```

Simply execute: 
```sh
make
```
And find .so files in `build/release-linux-x86_64`, for 32-bit: `build/release-linux-x86`. <br/><br/>


- ### Optional:

You can execute optionally the parameters using the following ways:

* To compile debug x86 .so builds:
```sh
make debug ARCH=x86 PLATFORM=linux # compiles debug x86 .so builds (creates "debug-linux-x86" directory inside "build")
```

* To compile release x86 .dll builds:
```sh
make ARCH=x86 PLATFORM=windows # compiles release x86 .dll builds (creates "release-windows-x86" directory inside "build")
```

... Optionally, you can play the parameters like `ARCH=x86_64` (compiles 64-bits builds), `PLATFORM=windows` (compiles dlls), `PLATFORM=linux` (compiles shared libraries (.so files)) ...

<br/>

### Credits

[SantaClaws](https://web.archive.org/web/20030111110021/http://www.planetquake.com/crimsoft/lms/news.html)
