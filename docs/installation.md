# Installation

## OS support and prerequisites

You can manage all your wordslab clusters and all your *cloud* virtual machines from a single **wordslab manager** installation.

But you also need to install **wordslab manager** on each machine on which you want to create, start and stop a *local* virtual machine.

You can install **wordslab manager** on :
- :fontawesome-brands-windows: Windows 10+
- :fontawesome-brands-linux: Linux - Ubuntu 18.04+
- :fontawesome-brands-apple: macOS - Catalina+

You don't need to be an administrator or to have root/sudo privileges to install and use wordslab manager, or even to create a *local* virtual machine.

But you may need admin priviledges to install some prerequisites on the machine (see below). 

The wordslab manager installation and its data always stays confined to the current user account.

wordslab manager will check and install (or guide you to install) all the necessary prerequisites.

These prerequisites are documented below for your information: you don't need to install them manually.

!!! Prerequisites to install and run **wordslab manager**

    === "Windows"

        - Windows 10 version 1703+ x64
        - Windows 11 version 22000+ x64
        - 100 MB of free disk space

    === "Linux"

        - Ubuntu version 16.04, 18.04, 20.04+ x64
        - Not tested but should also work: 
          - Alpine Linux 3.12+ x64
          - CentOS 7+ x64
          - Debian 10+ x64
          - Fedora 33+ x64
          - openSUSE 15+ x64
          - Red Hat Enterprise Linux 7+ x64
          - SUSE Enterprise Linux 12 SP2+ x64
        - 100 MB of free disk space

    === "macOS"

        - macOS	10.15+ x64
        - 100 MB of free disk space

!!! Prerequisites to create a *local* virtual machine

    === "Windows"

        - Windows 10 version 1903+ x64
        - 10 GB of free disk space
        - Admin privileges are only needed to:
          - enable Windows Subsystem for Linux

    === "Linux"

        - Ubuntu version 18.04+ x64
        - Not tested but should also work if qemu is installed :
          - Arch: pacman -S qemu
          - Debian/Ubuntu: apt-get install qemu
          - Fedora: dnf install @virtualization
          - Gentoo: emerge --ask app-emulation/qemu
          - RHEL/CentOS: yum install qemu-kvm
          - SUSE: zypper install qemu
        - 10 GB of free disk space
        - Admin privileges are only needed to:
          - install cpu-checker qemu qemu-utils qemu-kvm 

    === "macOS"

        - macOS	10.15+ x64
        - 10 GB of free disk space
        - Admin privileges are only needed to:
          - install homebrew

!!! Prerequisites to use a GPU in *local* virtual machine

    === "Windows"

        - Nvidia GPU with Pascal (GTX 1050) and later GPU architecture        
        - Windows 10 version 21H2+ (build 19044+) or Windows 11 x64
        - Nvidia driver version >= 496.76 (16 nov 2021)
        - Windows Subsystem for Linux Kernel version 5.10.16.3 or later

    === "Linux"

        - GPU sharing between host and guest OS **not supported**

    === "macOS"

        - GPU sharing between host and guest OS **not supported**

## Installation instructions

You can find the wordslab releases

!!! Installation commands

    === "Windows"

        - set installdir=%APPDATA%\wordslab
        - mkdir %installdir%
        - curl -L -o %installdir%\wordslab-win-x64.zip https://github.com/wordslab-org/wordslab/releases/download/v0.0.2/wordslab-win-x64.zip
        - tar -x -f %installdir%\wordslab-win-x64.zip -C %installdir%
        - del %installdir%\wordslab-win-x64.zip
        - cd %installdir%
        - wordslab version

    === "Linux"

        - installdir=$HOME/wordslab
        - mkdir $installdir
        - curl -L -o $installdir/wordslab-linux-x64.zip https://github.com/wordslab-org/wordslab/releases/download/v0.0.2/wordslab-linux-x64.zip
        - tar -x -f $installdir/wordslab-linux-x64.zip -C $installdir
        - rm $installdir/wordslab-linux-x64.zip
        - cd $installdir
        - wordslab version

    === "macOS"

        - to do

## First use and initial configuration

