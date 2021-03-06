---
layout: page
title: How to build the QEMU binaries?
permalink: /qemu/build-procedure/

date: 2015-09-04 17:02:00 +0300

---

The latest version of the build script is a single run, multi-platform build, generating the Windows 32, Windows 64, GNU/Linux 32, GNU/Linux 64 and macOS distribution packages at once.

The script was developed on macOS, but it also runs on any recent GNU/Linux distribution (only that in this case it cannot generate the macOS package).

## Prerequisites

The main trick that made the multi-platform build possible is [Docker](https://www.docker.com).

Containers based on three docker images are used, one packing MinGW-w64 in a Debian 8, and two packing the basic system (gcc & x11) in Debian 8 (separate 32/64-bits containers). The more conservative Debian was preferred to generate the GNU/Linux versions, to avoid problems when attempting to run the executables on older versions.

### macOS

#### Install the Command Line Tools

The macOS compiler and other development tools are packed in a separate Xcode add-on. The best place to get it is from the [Developer](https://developer.apple.com/xcode/downloads/) site, although this might require enrolling to the developer program (free of charge).

To test if the compiler is available, use:

```
$ gcc --version
Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
Apple LLVM version 6.1.0 (clang-602.0.49) (based on LLVM 3.6.0svn)
Target: x86_64-apple-darwin14.3.0
Thread model: posix
```

#### Install a custom instance of Homebrew

The build process is quite complex, and requires tools not available in the standard Apple macOS distribution. These tools can be installed with Homebrew. To keep these tools separate, a custom instance of Homebrew is installed in `${HOME}/opt/homebrew-gae`. 

In a separate run, the **[MacTex](http://www.tug.org/mactex/)** tools are also installed in `${HOME}/opt/texlive`. Alternatively you can install MacTex in `/usr/local` using the official distribution, but this will add lots of programs to the system path, and this is a bad thing.

The entire process can be automated with two scripts, available from GitHub:

```
$ mkdir -p ${HOME}/opt
$ git clone https://github.com/ilg-ul/opt-install-scripts \
    ${HOME}/opt/install-scripts.git
$ bash ${HOME}/opt/install-scripts.git/install-homebrew-gae.sh
$ bash ${HOME}/opt/install-scripts.git/install-texlive.sh
```

The scripts run with user credentials, no `sudo` access is required.

#### Install Docker

On macOS, Docker can be installed by following the official [Install Docker on macOS](https://docs.docker.com/installation/mac/) instructions.

### GNU/Linux

#### Install Docker

For any GNU/Linux distribution, follow the [specific instructions](https://docs.docker.com/installation/#installation).

#### Configure Docker to run as a regular user

To allow docker to run as a regular user, you need to be a member of the `docker` group.

```
$ sudo groupadd docker
$ sudo gpasswd -a ${USER} docker
$ sudo service docker restart
```

To make these changes effective, logout and login.

The above are for Ubuntu and the Debian family. For other distributions, the last line may differ, for example for Arch Linux use:

```
$ systemctl restart docker
```

#### Install required packages

Since most of the build is performed inside the Docker containers, there are not many requirements for the host, and most of the time these programs are in the standard distribution (`curl`, `git`, `automake`, `patch`, `tar`, `unzip`).

The script checks for them; if the script fails, install them and re-run.

### Docker images

The Docker images are available from [Docker Hub](https://hub.docker.com/u/ilegeul/). They were build using the Dockerfiles available from [ilg-ul/docker](https://github.com/ilg-ul/docker) on GitHub.

## Download the build scripts repo

The build script is available from GitHub and can be [viewed online](https://github.com/gnuarmeclipse/build-scripts/blob/master/scripts/build-openocd.sh).

To download it, clone the [gnuarmeclipse/build-scripts](https://github.com/gnuarmeclipse/build-scripts) Git repo. 

```
$ git clone https://github.com/gnuarmeclipse/build-scripts.git \
  ~/Downloads/build-scripts.git
```

## Check the script

The script creates a temporary build `Work/qemu` folder in the the user home. Although not recommended, if for any reasons you need to change this, you can redefine WORK_FOLDER variable before invoking the script.

## Preload the Docker images

Docker does not require to explicitly download new images, but does this automatically at first use.

However, since the images used for this build are relatively large, it is recommended to load them explicitly before starting the build:

```
$ bash ~/Downloads/build-scripts.git/scripts/build-qemu.sh preload-images
```

Please be patient, this will bring about 5 GB, which on a regular broadband line might take more than 30 minutes.

The result should look similar to:

```
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
ilegeul/debian32    8-gnuarm-gcc-x11-v3   14a0dcce0dd7        11 months ago       1.633 GB
ilegeul/debian      8-gnuarm-gcc-x11-v3   a461714e9b42        11 months ago       1.771 GB
ilegeul/debian      8-gnuarm-mingw        1c04c24123c1        15 months ago       2.486 GB
```

## Build all distribution files

```
$ bash ~/Downloads/build-scripts.git/scripts/build-qemu.sh --all
```

On macOS, to prevent entering sleep, use:

```
$ caffeinate bash ~/Downloads/build-scripts.git/scripts/build-qemu.sh --all
```

About half an hour later, the output of the build script is a set of 5 files in the output folder:

```
$ ls -l output
total 105616
total 51336
drwxr-xr-x  6 ilg  staff      204 May 12 22:07 debian32
drwxr-xr-x  6 ilg  staff      204 May 12 21:43 debian64
-rw-r--r--  1 ilg  staff  4462782 May 12 22:30 gnuarmeclipse-qemu-debian32-2.3.50-201505121804-dev.tgz
-rw-r--r--  1 ilg  staff  4601903 May 12 22:06 gnuarmeclipse-qemu-debian64-2.3.50-201505121804-dev.tgz
-rw-r--r--  1 ilg  staff  5378788 May 12 22:34 gnuarmeclipse-qemu-osx-2.3.50-201505121804-dev.pkg
-rw-r--r--  1 ilg  staff  3257398 May 12 21:42 gnuarmeclipse-qemu-win32-2.3.50-201505121804-dev-setup.exe
-rw-r--r--  1 ilg  staff  3782102 May 12 21:25 gnuarmeclipse-qemu-win64-2.3.50-201505121804-dev-setup.exe
drwxr-xr-x  4 ilg  staff      136 May 12 22:35 osx
drwxr-xr-x  6 ilg  staff      204 May 12 21:26 win32
drwxr-xr-x  6 ilg  staff      204 May 12 21:04 win64
```

## Subsequent runs

### Separate platform specific builds

Instead of `--all`, you can use any combination of:

```
--win32 --win64 --debian32 --debian64 --osx
```

### clean

To remove all build files, use:

```
$ bash ~/Downloads/build-scripts.git/scripts/build-qemu.sh clean
```

## The Work folder

The entire build process is contained in a Work folder, located on the host and mounted in the Docker containers.

A typical Work folder includes sub-folders for each project:

```
$ tree -L 1 qemu
qemu
├── README.txt
├── build
├── gnuarmeclipse-qemu.git
├── install
├── output
├── patches
├── scripts
└── xcode
```

The build and include subfolders look like:

```
$ tree -L 2 qemu/build/ qemu/install
qemu/build/
├── debian32
│   └── qemu
├── debian64
│   └── qemu
├── osx
│   └── qemu
├── win32
│   └── qemu
└── win64
	└── qemu
qemu/install
├── debian32
│   ├── archive
│   └── qemu
├── debian64
│   ├── archive
│   └── qemu
├── osx
│   └── qemu
├── win32
│   └── qemu
└── win64
	└── qemu

22 directories, 0 files
```

## Install procedure

The procedure to install GNU ARM Eclipse QEMU is platform specific, but relatively straight forward (a Windows setup, an macOS install or a TGZ archive on GNU/Linux). The setup/install asks no special questions, and the defaults are generally ok for most installations.

## Install hierarchy

After install, the package should create a structure like this (only the first two depth levels are shown):

```
$ tree -L 2 /Applications/GNU\ ARM\ Eclipse/QEMU/2.3.50-201505141607-dev
/Applications/GNU\ ARM\ Eclipse/QEMU/2.3.50-201505141607-dev
├── INFO.txt
├── bin
│   ├── libffi.6.dylib
│   ├── libgmp.10.dylib
│   ├── libgnutls.28.dylib
│   ├── libhogweed.2.dylib
│   ├── libiconv.2.dylib
│   ├── libintl.8.dylib
│   ├── libnettle.4.dylib
│   ├── libp11-kit.0.dylib
│   ├── libtasn1.6.dylib
│   ├── libz.1.dylib
│   └── qemu-system-gnuarmeclipse
├── doc
│   ├── qemu-doc.html
│   ├── qemu-doc.pdf
│   ├── qemu-tech.html
│   ├── qemu-tech.pdf
│   └── qmp-commands.txt
├── etc
│   └── qemu
├── gnuarmeclipse
│   ├── BUILD.txt
│   ├── CHANGES.txt
│   ├── build-helper.sh
│   ├── build-qemu.sh
│   └── config.log
├── license
│   └── qemu-2.3.50
├── man
│   └── man1
└── share
    └── qemu

11 directories, 22 files
```

No other files are installed in any system folders or other locations.

## Uninstall

To uninstall QEMU from a Windows machine, use the `qemu-uninstall.exe` program.

On macOS and GNU/Linux, the GNU ARM Eclipse QEMU install folder is self-contained and removing it is enough for completely removing the application.

## Test

A simple test is performed by the script at the end, by launching the executable to check if all shared/dynamic libraries are correctly used.

For a true test you need to first install the package and then run the program form the final location. For example on macOS the output should look like:

```
$ /Applications/GNU\ ARM\ Eclipse/QEMU/2.2.91-201504021111-dev/bin/qemu-system-gnuarmeclipse --version
GNU ARM Eclipse QEMU 64-bits emulator version 2.2.91
Copyright (c) 2003-2008 Fabrice Bellard
```

## More build details

The script is quite complex, and an attempt to explain its functionality would require some effort. For the final authoritative details, please refer to the comments available in the [script](https://github.com/gnuarmeclipse/build-scripts/blob/master/scripts/build-qemu.sh).
