## Table of contents.
1. [Basic navigation commands](#basic-navigation-commands)
2. [Quick notes on Linux Kernel and Shell](#quick-notes-on-linux-kernel-and-shell)
3. [Linux Directory Structure](#linux-directory-structure)


## Basic navigation commands
When using Linux on a production level, the common practice is to manage and maintain the system by using only the terminal. Since no mouse or GUI (Graphical User Interface) is installed on the servers, it is important to know at least some of the commands that are necessary to navigate through the multiple files and directories and visualize their contents.

Here are some of the most elemental commands to navigate inside Linux using a terminal or CLI (Command Line Interface):

- **pwd**: the pwd command shows in the terminal the full path to the current directory the user is located at. 

    >A "full path" describes a location starting from the root directory (/) and going through all the relevant subdirectores until the target destination is reached (e.g: /var/log/). 

- **cd**: the cd command allows the user to move to a different directory. The syntax for this command is the following: `cd <path>`, where the path can be either a full path or a relative path from the current location.

    Also, using `cd ..` makes it possible to go back one step, for example, when running `cd ..` while locating inside `/home/user/local`, the user will then be located inside `/home/user`.

    It is also possible to go back multiple steps with the same command. In the previous example, if a user runs `cd ../..` will go back two steps and the new location would be `/home`.

    Finally, by running `cd -` the user is able to go back to the previous location the user was located at. For example, if a user were located inside `/home/user` and decides to move to `/opt/`, the user can then run `cd - ` to go back to `/home/user` in just one step! 

- **ls**: provides a list of the contents of a directory. This command is very important because it allows us to see what is inside every directory we visit (and even from the outside). 

    The syntax for this command is the following: `ls [option] [path]`, there are multiple additional options that can be ran along with ls to customize the list that is returned. Also, it is possible to list the contents of any directory without being located inside it if a full or relative path is provided. Both the options and the path are optional attributes, so it is not mandatory to provide them every time.

    Some of the options available for ls are the following:

    - **ls -1**: lists the contents in ascending alphanumerical order.

    - **ls -r**: lists the contents in reverse order.

    - **ls -a**: lists the contents and also shows the hidden files inside the directory (hidden files have a dot at the start of the name).

    - **ls -l**: lists the files and shows the permissions, creation date, size, owner and group for the listed files/directories.

- **touch**: creates an empty file with the name provided and in the specified path. For example, `touch /opt/user/example.txt` would create an empty txt file in the chosen location. Touch cannot create an empty file if the chosen name is already in use.

- **nano**: nano is one of the most basic text editors available in Linux. By calling `nano <filename>` the editor will open. After editing the file, the changes can be saved by entering `ctrl + O`, then it is needed to enter `ctrl + X` in order to exit the nano editor.

- **echo**: this command allows the user to show information in the terminal, similar to how `print()` function works in Python or how `printf()` works in C++. This is useful for creating scripts and also for showing the values of the multiple variables available in Linux. 

    The variables, as the name implies, store information that can be modified by the user or Linux itself. There are a high amount of variables inside Linux, here are some variables that are used frequently:

    - **$USER**: stores the username for the active user.
    - **$SHELL**: stores the name of the shell that is in use.
    - **$UID**: stores the user ID, also known as UID.
    - **$PWD**: this variable stores the current directory the user is located at.
    - **$HOME**: stores the full path to the user's home directory.
    - **$PS1**: shows the prompt configuration. The prompt is the first line that is shown in the terminal each time that a new line is entered. For example, in Ubuntu when using the bash shell, the prompt has this format: `<user>@<hostname>:<current_location><type_of_user>`.

        >Note about the `type_of_user`: a normal user will show a `$` symbol at the end of the prompt, while the root user will always shown a `#` symbol.
 
## Quick notes on Linux Kernel and Shell: 
The Linux kernel is the main component of a Linux operating system (OS) and is the core interface between a computer’s hardware and its processes. It communicates between the two of them, managing resources as efficiently as possible. The kernel exists within the OS and controls all the major functions of the hardware, whether it’s a phone, laptop, server, or any other kind of computer.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/kernel.png?raw=true" alt="Linux kernel"/>
</p>

The Linux Shell is a program that takes commands from the keyboard and gives them to the operating system to perform. This kind of programs are also know as Command Line Interfaces or CLI's. In the old days, it was the only user interface available on a Unix-like system such as Linux, nowadays there are also graphical user interfaces (GUIs) in addition to command line interfaces (CLIs).

On most Linux systems a program called `bash` (which stands for Bourne Again SHell, an enhanced version of the original Unix shell program, sh) acts as the shell program. Besides bash, there are other shell programs available for Linux systems, including `ksh, tcsh` and `zsh`, among others. The shell is an intermediary between the user and the OS: inside Linux, it is possible to change the current shell in use by typing the name of the shell in the terminal, although most of the shells share their functionalities, they may vary in the commands and variables they include.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/shell.png?raw=true" alt="Linux Shell"/>
</p>

## Linux Directory Structure
In Linux, **everything** is treated as a file or a directory: from the internal logs to the USB devices, all thing inside Linux belong to one of those two categories.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/filesystem.png?raw=true" alt="Linux filesystem"/>
</p>

All Linux directories and subdirectories follow a structure that has its starting point in the `root` directory, also known as `/`. Although the subdirectories inside root may vary between distributions, there are some of them that are always present in the filesystem. The following list describes the core subdirectories that conform the Linux Directory Structure:

- **/bin**: this directory stores the main binary/executable files necessary for the proper functioning of the system. All the binaries stored there can be used by all the users of the OS.

    Some of the executables stored inside `/bin` are `cp, echo, tar, cat, mv, rm, ping, gzip, kill, ls, ping, su`, etc. Those files allow the user to perform the vast mayority of basic utilities through the CLI. The `/bin` directory will never have subdirectories. Also, the same contents inside `/bin` are found in `/usr/bin` and `/usr/local/bin`.

- **/sbin**: this directory stores binary/executable files as well, but in this case the files in this directory can only be accessed by the system admin, also called root user.

    The files included here are critical for booting, restoring and fixing the OS. Some of the executables stored inside `/sbin` are `fsck, init, reboot, shutdown, fastboot, etc`. The same contents inside `/sbin` are found in `/usr/sbin` and `/usr/local/sbin`.

- **/boot**: this directory contains all the necessary files for the booting of the OS, except for the config files. Some of the files stored inside `/boot` are the `kernel` and `grub`. All the files inside `/boot` are used by the OS before the Kernel is able to even run programs in user mode.

- **/dev**: GNU/Linux treats all hardware devices as if they were directories. So the files inside `/dev` represent all the files that belong to those hardware devices. Each time a hardware deviced is used, for example: a USB drive, a printer, an external disk drive, a mouse, etc. Linux acesses the device's hardware by reading and writing the device's directory inside `/dev`

    The hardware devices connected o the system receive a name depending on its type. The following list shows the names of the most common devices that are connected to a Linux OS:

    - **cdrom**: represents the CDROM device.

    - **sda**: represents a SATA HDD.

    - **audio**: represents the system's sound card.

    - **psaux**: represents the PS/2 port.

    - **lpx**: represents the printer.

    - **fd0**: represents the floppy disk.

- **/etc**: this directory stores all the configurations of the OS. Also, all the config files necessary to run numerous programs are stored there. Under certain circumstances, some of the files inside `/etc` can be complemented or replaced by files stored in the user's personal directory inside `/home`.

    There are multiple subdirectories inside `/etc` that can also hold configuration files, such as the following:

    - **/etc/apt**: contains the config files for the package manager called `apt`.

    - **/etc/opt**: it contains the config files for the programs stored inside `/opt`. 
    
    - **/etc/profile**: contains user specific config parameters to run and utilize the shell.
    
    - **/etc/X11**: contains config files for the X Window system, which handles the GUI (Graphical User Interface).

- **/home**: this directory has a personal subdirectory for each of the users in the system (except the root user), for example: `user1` will have a directory called `/home/user1` and `user2` will have a directory called `/home/user2`, and so on. Each one of the users will have all of their personal files inside their corresponding directory. This directory will also store the config files for each one of the programs that are run by the user.

- **/lib**: this directory stores the shared libraries that are necessary to run the executable files that are stored in `/bin` and `/sbin`. The kernel modules and drivers that are necessary to boot and operate the system are also stored there.

    > Note: a library is basically a collection of data and functions written to be reused by other programmers or programs.

- **/mnt**: this directory stores the mount point for the multiple storage devices, such as external disk drives or data partitions.

    > Note: a disk partition consists in creating one or more regions of the disk that will be separated from the rest, so those regions can be managed independently. This allows to dedicate a desired part of the disk to specific tasks, such as creating a Virtual Machine, for example.

- **/media**: this directory works in a very similar way `/mnt` and `/dev` do. It contains information about the connected mount points, such as USB devices, CD-ROMs, etc.

- **/opt**: the main purpose of this directory is to stored all the additional, non-core programs that are installed in the system, for example: Spotify, Splunk, Google Chrome, etc. This directory works similar to `/usr/local`, however, the programs that do not follow the standards for storing their content inside `/usr` are then installed in `/opt`.
    
- **/proc**: this directory is actually a virtual filesystem - it shows information about the processes that are being executed at the moment and the contents of `/proc` are stored in the RAM, not in the disk. Since the info lives inside the RAM, the contents of `/proc` are created and deleted by the OS itself (not user-managed).

- **/root**: this directory acts as the home directory for the `root` user.

- **/srv**: since GNU/Linux is a server-oriented OS, it is expected to host multiple servers and their corresponding files and directories. The `/srv` is meant to fulfill that specific role and store all the files/directories for the installed servers. Some examples of servers that could be stored inside `/srv` are the Apache web server (`/srv/www`) or a FTP server (`/srv/ftp`).

- **/tmp**: in this directory, all the temporary files and variables required for the programs to work propely are stored. Normally, the OS empties the `/tmp` directory upon restarting, so in case that the directory is not empty after a restart it is recommended to manually delete its contents.

- **/usr**: there are installed the mayority of programs in the OS. All the content inside this directory is read-only and is available for all users in the system. Normally, `/usr` has multiple subdirectories that store more specific information, here are some examples of the subdirectories available:

    - **/usr/bin**: stores all executables for the software in the system. Actually, `/bin` is a symbolic link to this subdirectory, so they share the same information.
    
    - **/usr/include**: it includes all header files that the system needs to run properly.
    
    - **/usr/lib**:  stores all the shared libraries. Same as with `/bin`, `/lib` is a link to this directory, so they share the same information.

    - **/usr/local**: since GNU/Linux is designed for networking environments, it is possible that `/usr` is not locally installed in the machine and that it is stored on a remote server. For those particular cases is that this subdirectory exists: it allows the system admin to store the programs that were locally installed in a place that is protected from automatic updates, thus creating a safe local environment for user programs.
    
    - **/usr/sbin**: stores all special executables for the software in the system that are only available to system admins. Actually, `/sbin` is a symbolic link to this subdirectory, so they share the same information.

    - **/usr/share**: there are stored all the text files that are indepent of the system architecture. For example: the documentation fo the `/man` command, info and help documents, images and icons, etc.
    
    - **/usr/src**: the source code for some applications and the kernel is usually stored inside this disrectory.
    
- **/var**: in this directory are stored all the data files that change over the time, for example: logs, spool files, registers, etc. The main purpose of this directory is to allow the user to detect issues and resolve them.

    The following are some of the most important subdirectories of `/var`:

    - **/var/cache**: stores application data in cache mode. For example, the `apt-get` command makes use of this when downloading and installing packages: a copy of the binary packege installed is stored inside `/var/cache/apt/archives`, so if the user wants to uninstall the package and install it again later, then it wont be necessary to download all the files again and the installation would be almost immediate.

        >Note: cache refers to a temporary storage area that facilitates faster access to data with the goal of improving application and system performance. 

    - **/var/lib**: stores information about the status of the applications and also system databases.
    
    - **/var/lock**: stores the lock files generated by some programs. The main goal of lock files is to prevent some resources from being used by programs other than the program who created them. The lock files disappear when the program who created them stops running.
    
    - **/var/log**: stores a big part of the registries of the OS and the programs. This directory is very important since it helps the user to determine the root cause of an issue in particular.
    
    - **/var/opt**: stores the variable data utilized by the programs installed inside `/opt`. 
    
    - **/var/run**: holds information about the current active session , such as the daemons, logged users, active processes, etc.
    
    - **/var/spool**: stores files that controls the pending tasks. For example, inside `/var/spool/cups` are the files that control the printing task pending and inside `/var/spool/cron` are the files who orchestrate the planified tasks pending of execution.
    
    - **/var/tmp**: as the name suggests, this directory also holds temporary files. The key difference is that the files stored here do not get automatically deleted upon restarting the machine.
    
- **/sys**: this directory stores information similar to the one found inside `/proc`. Inside this directory are lots of structured, hierarchical information about the system kernel, partitions, filesystems, drivers, etc.
