# Relajet C Series Open Source SDK

Author: Wig Cheng <wig.cheng@relajet.com>

Last Update: 2018/05/25

This SDK is based on Relajet C Series product and seperated 4 parts: Linux Kernel, Buildroot OS, build script and image flash tool:

## Environment Setup

General Packages based on Ubuntu 14.04 or above:

    $ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
      build-essential chrpath  socat bc liblz4-tool \
      libsdl1.2-dev xterm  sed cvs subversion coreutils texi2html \
      docbook-utils python-pysqlite2 help2man make gcc g++ desktop-file-utils \
      libgl1-mesa-dev libglu1-mesa-dev mercurial autoconf automake groff curl lzop asciidoc

For Ubuntu 12.04 host setup only:

    $ sudo apt-get install uboot-mkimage

For Ubuntu 14.04 or above host setup:

    $ sudo apt-get install u-boot-tools

## To get the SDK you need to have repo installed and use it as:

Download the SDK source in the same folder:

Step 1. Featured Linux Kernel 3.2 (GPL License)

    $ git clone -b relajet-mstar_3.2.7_1.0.0_ga-wip https://github.com/RelaJet/linux-relajet.git linux

Step 2. Featured Buildroot OS 2018.02 (GPL License)

    $ git clone -b relajet_201802_1.0.0_ga-wip https://github.com/RelaJet/buildroot.git

Step 3. Customize Build Tool (MIT License)

    $ git clone -b relajet_c-series_c8238_1.0.0-ga https://github.com/RelaJet/cookers.git

Step 4. Image Flash Tool

    $ wget https://github.com/RelaJet/c-series_linux_setup/raw/master/img_generator.zip
    $ unzip img_generator.zip

## Starting compile the source code and flashing the image:

To setup the configuration (it's necessary)

    $ source cookers/env.bash.relajet.ait8328q

To build the all source code

    $ cook -j<N> (N is up to cors number on your host PC)

To re-build the all source code

    $ heat -j<N> (N is up to cors number on your host PC)

To clean the all source code

    $ throw

To clean-build the all source code (optional)

    $ throw
    $ cook -j<N> (N is up to cors number on your host PC)

To build Linux Kernel or Buildroot only (opional)

    $ cd linux ( or cd buildroot)
    $ cook -j<N> (N is up to cors number on your host PC)

To add/remove the driver/app to/from configuration on Linux Kernel or Buildroot only (opional)

    $ cd linux ( or cd buildroot)
    $ recipe

create a flashed uSD card (recommend use class 10) :

    $ flashcard /dev/sdx
    NOTE: sdx is your device node, example: flashcard /dev/sdb
    After done the flashcard, plug the uSD card to c-series and starting flash process
    Enjoy!!
