# Installation

You need to install **wordslab manager** on each host machine on which you want to create, start and stop a *local* virtual machine.

You can manage all your *cloud* virtual machines from a single **wordslab manager** installation.

You can install **wordslab manager** on:

- :fontawesome-brands-windows: Windows 10+
- :fontawesome-brands-linux: Linux - Ubuntu 18.04+
- :fontawesome-brands-apple: macOS - Catalina+

You don't need to be an administrator or to have root/sudo privileges to install and use wordslab manager, or even to create a *local* virtual machine.

But you may need admin privileges to install some prerequisites on the machine (see below). 

The wordslab manager installation and its data always stays confined to the current user account.

wordslab manager will check and install for you all the necessary prerequisites.

## OS support and prerequisites

!!! info "Prerequisites to create a local virtual machine"

    === "Windows"

        - Windows 10 version 1903+ x64
        - 10 GB of free disk space
        - Admin privileges are only needed to enable Windows Subsystem for Linux

    === "Linux"

        - Ubuntu version 18.04+ x64
        - Not tested but should also work if qemu is installed :
           * Arch: pacman -S qemu
           * Debian/Ubuntu: apt-get install qemu
           * Fedora: dnf install @virtualization
           * Gentoo: emerge --ask app-emulation/qemu
           * RHEL/CentOS: yum install qemu-kvm
           * SUSE: zypper install qemu
        - 10 GB of free disk space
        - Admin privileges are only needed to install cpu-checker qemu qemu-utils qemu-kvm 

    === "macOS"

        - macOS	10.15+ x64
        - 10 GB of free disk space
        - Admin privileges are only needed to install homebrew

!!! info "Prerequisites to use a GPU in local virtual machine"

    === "Windows"

        - Nvidia GPU with Pascal (GTX 1050) and later GPU architecture        
        - Windows 10 version 21H2+ (build 19044+) or Windows 11 x64
        - Nvidia driver version >= 496.76 (16 nov 2021)
        - Windows Subsystem for Linux Kernel version 5.10.16.3 or later

    === "Linux"

        - GPU sharing between host and guest OS on Linux is **not supported**

    === "macOS"

        - GPU sharing between host and guest OS on macOS is **not supported**

## Installation instructions

You can find the changelog for all wordslab manager releases in the Github repository: [https://github.com/wordslab-org/wordslab/releases](https://github.com/wordslab-org/wordslab/releases).

To download and install wordslab manager, open a terminal and copy the installation commands below.

!!! example "Installation commands"

    === "Windows"

        ``` winbatch hl_lines="1"
        set installdir=%HOMEPATH%\wordslab
        mkdir %installdir%
        curl -L -o %installdir%\wordslab-win-x64.zip https://github.com/wordslab-org/wordslab/releases/download/v0.8.2/wordslab-win-x64.zip
        tar -x -f %installdir%\wordslab-win-x64.zip -C %installdir%
        del %installdir%\wordslab-win-x64.zip
        cd %installdir%
        wordslab version
        ```

    === "Linux"

        ``` bash hl_lines="1"
        installdir=$HOME/wordslab
        mkdir $installdir
        curl -L -o $installdir/wordslab-linux-x64.tar.gz https://github.com/wordslab-org/wordslab/releases/download/v0.8.2/wordslab-linux-x64.tar.gz
        tar -xf $installdir/wordslab-linux-x64.tar.gz -C $installdir
        rm $installdir/wordslab-linux-x64.tar.gz
        cd $installdir
        ./wordslab version
        ```

    === "macOS"

        ``` zsh hl_lines="1"
        installdir=$HOME/wordslab
        mkdir $installdir
        curl -L -o $installdir/wordslab-osx-x64.tar.gz https://github.com/wordslab-org/wordslab/releases/download/v0.8.2/wordslab-osx-x64.tar.gz
        tar -xf $installdir/wordslab-osx-x64.tar.gz -C $installdir
        rm $installdir/wordslab-osx-x64.tar.gz
        cd $installdir
        ./wordslab version
        ```


