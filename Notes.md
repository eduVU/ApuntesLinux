## Table of contents.
1. [Basic navigation commands](#basic-navigation-commands)
2. [Quick notes on Linux Kernel and Shell](#quick-notes-on-linux-kernel-and-shell)
3. [Linux Directory Structure](#linux-directory-structure)
4. [Creating aliases](#creating-aliases)
5. [Creating variables and scripts](#creating-variables-and-scripts)


## Basic navigation commands
When using Linux on a production level, the common practice is to manage and maintain the system by using only the terminal. Since no mouse or GUI (Graphical User Interface) is installed on the servers, it is important to know at least some of the commands that are necessary to navigate through the multiple files and directories and visualize their contents.

Here are some of the most elemental commands to navigate inside Linux using a terminal or CLI (Command Line Interface):

- **pwd**: the pwd command shows in the terminal the full path to the current directory the user is located at. 

    >A "full path" describes a location starting from the root directory (/) and going through all the relevant subdirectores until the target destination is reached (e.g: /var/log/). 

- **cd**: the cd command allows the user to move to a different directory. The syntax for this command is the following: `cd <path>`, where the path can be either a full path or a relative path from the current location.

    Also, using `cd ..` makes it possible to go back one step, for example, running `cd ..` while locating inside `/home/user/local` will make the user go to `/home/user`.

    It is also possible to go back multiple steps with the same command. In the previous example, running `cd ../..` will make the user go back two steps and the new location would be `/home`.

    Finally, by running `cd -` the user is able to go back to the previous location the user was located at. For example, if a user were located inside `/home/user` and decides to move to `/opt/`, the user can then run `cd - ` to go back to `/home/user` in just one step! 

- **ls**: provides a list of the contents of a directory. This command is very important because it allows the user to see what is inside every directory the user visits(and even from the outside). 

    The syntax for this command is the following: `ls [option] [path]`, there are multiple additional options that can be ran along with `ls` to customize the list that is returned. Also, it is possible to list the contents of any directory without being located inside it if a full or relative path is provided. Both the options and the path are optional attributes, so it is not mandatory to provide them every time.

    Some of the options available for ls are the following:

    - **ls -1**: lists the contents in ascending alphanumerical order.

    - **ls -r**: lists the contents in reverse order.

    - **ls -a**: lists the contents and also shows the hidden files inside the directory (hidden files have a dot at the start of the name, e.g: `.secret`).

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

    - **$PATH**: stores the list of paths that the system will automaticaly check when running a script. If the script is stored inside one of the locations of this variable, then it can be called from the prompt without specifying the full path to the script. 

    - **$PS1**: shows the prompt configuration. The prompt is the first line that is shown in the terminal each time that a new line is entered. For example, in Ubuntu when using the `bash` shell, the prompt has this format: `<user>@<hostname>:<current_location><type_of_user>`.

        >Note about the `type_of_user`: a normal user will show a `$` symbol at the end of the prompt, while the root user will always show a `#` symbol.
 
## Quick notes on Linux Kernel and Shell: 
The Linux kernel is the main component of a Linux operating system (OS) and is the core interface between a computer’s hardware and its processes. It communicates between the two of them, managing resources as efficiently as possible. The kernel exists within the OS and controls all the major functions of the hardware, whether it’s a phone, laptop, server, or any other kind of computer.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/kernel.png?raw=true" alt="Linux kernel"/>
</p>

The Linux Shell is a program that takes commands from the keyboard and gives them to the operating system to perform. This kind of programs are also know as Command Line Interfaces or CLI's. In the old days, it was the only user interface available on a Unix-like system such as Linux, nowadays there are also graphical user interfaces (GUIs) in addition to CLIs.

On most Linux systems a program called `bash` (which stands for Bourne Again SHell, an enhanced version of the original Unix shell program, `sh`) acts as the shell program. Besides `bash`, there are other shell programs available for Linux systems, including `ksh, tcsh` and `zsh`. The shell is an intermediary between the user and the OS: inside Linux, it is possible to change the current shell in use by typing the name of the shell in the terminal, although most of the shells share their functionalities, they may vary in the commands and variables they include.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/shell.png?raw=true" alt="Linux Shell"/>
</p>

## Linux Directory Structure
In Linux, **everything** is treated as a file or a directory: from the internal logs to the USB devices, all things inside Linux belong to one of those two categories.

<p align="center">
  <img src="https://github.com/eduVU/LinuxNotes/blob/main/images/filesystem.png?raw=true" alt="Linux filesystem"/>
</p>

All Linux directories and subdirectories follow a structure that has its starting point in the `root` directory, also known as `/`. Although the subdirectories inside root may vary among distributions, there are some of them that are always present in the filesystem. The following list describes the core subdirectories that conform the Linux Directory Structure:

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

    > Note: a library is a collection of data and functions written to be reused by other programmers or programs.

- **/mnt**: this directory stores the mount point for the multiple storage devices, such as external disk drives or data partitions.

    > Note: a disk partition consists in creating one or more regions of the disk that will be separated from the rest, so those regions can be managed independently. This allows to dedicate a desired part of the disk to specific tasks, such as creating a Virtual Machine, for example.

- **/media**: this directory works in a very similar way `/mnt` and `/dev` do. It contains information about the connected mount points, such as USB devices, CD-ROMs, etc.

- **/opt**: the main purpose of this directory is to store all the additional, non-core programs that are installed in the system, for example: Spotify, Splunk, Google Chrome, etc. This directory works similar to `/usr/local`, however, the programs that do not follow the standards for storing their content inside `/usr` are then installed in `/opt`.
    
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
    
    - **/var/spool**: stores files that controls the pending tasks. For example, inside `/var/spool/cups` are the files that control the printing tasks pending and inside `/var/spool/cron` are the files who orchestrate the planified tasks pending of execution.
    
    - **/var/tmp**: as the name suggests, this directory also holds temporary files. The key difference is that the files stored here do not get automatically deleted upon restarting the machine.
    
- **/sys**: this directory stores information similar to the one found inside `/proc`. Inside this directory are lots of structured, hierarchical information about the system kernel, partitions, filesystems, drivers, etc.

## Creating aliases

When creating scripts or performing multiple tasks from the CLI it could be tiresome to be typing all the commands one by one, specifically for those commands that are run very often by the user. This is when the aliases come into play: an alias is a shortcut defined by the user that allows for multiple commands to be run one after the other in only one use of the CLI. To create an alias, the `alias` command is used and it can chain together a very large amount of commands.

> Note: the structure of a Linux command is the following in almost all the cases.
>
> command [options] [arguments]
>
>A command can use multiple options at the same time, either grouped in a single flag, like `ls -lsh`, or by entering all the options separated by a single space, like `splunk start --accept-license -enable-bootstart`.
>
> The arguments are always given in a space-separated list: `touch file1 file2 file3`. 

By default, aliases are temporary, this means that they will be erased upon restarting the system or just closing the terminal. However, it is also possible to create permanent aliases by configuring a specific file for the shell in use. In the case of the bash shell, there are three main files that can be configured for this purpose:

- **/etc/bash.bashrc**: global configurations for bash, all users.

- **/~/.basrc**: global configurations for bash, user-specific.

- **/~/.bash_aliases**: this is the preferred configuration for setting the aliases according to the bash documentation. Also user-specific.

In both cases, it is important to locate the portion of the file that contains the aliases and add/remove the desired aliases to/from the list. After recently configuring this file, the `source` command must be run to load the changes. Finally, an alias created from the CLI can be deleted with the `unalias` command (this will not override the aliases stored in the config files).

Let's see an example of how to manage aliases:

> The alias for this example will use the `date` and `groups` commands one after the other:
>
> user@host:~$ alias shortcut="date; groups"
> 
> Now, by calling the new alias created it is possible to perform the desired tasks:
>
> user@host:~$ shortcut  
> lun 04 sep 2023 18:40:39 CST  
> user_group
>
> The `alias` command returns a list of the available aliases:
>
> user@host:~$ alias  
> alias shortcut="date; groups"
>
> This alias is temporary. A way to make it permament would be to edit one of the bashrc files (`/~/.basrc` for example) and then run `source` to load the changes.
>
> user@host:~$ source /~/.bashrc
>
> Finally, an alias can be deleted by using `unalias`.
>
> user@host:~$ unalias shortcut

## Creating variables and scripts

Linux variables store information that can be modified or that can change over time. The OS has a set of variables that store key information about the system, and the users can also create their own variables for multiple purposes (command execution, aliases, scripting, etc.). To create a variable, the following syntax is used: `name_of_variable="value"`, then the variable is called by adding a `$` symbol at the beginning of the name of the variable.

Let's see an example of setting a value for the variable called `random`:

> user@host:~$ random='something'

Now let's see how to call that variable from the prompt:

> user@host:~$ echo $random  
> something

By default, variables are local, meaning that they only exist in the shell environment they were created. So if a variable is created on a first shell and then a new shell is started, the variable won't be accesible in this new shell. The `set` command gives a complete list of all local variables for a shell environment.

It is also possible to create global variables with the use of the `export` command. This allows the user to reference the same variables inside different environments. All global variables can be checked by running the `env` command and they are stored inside `/etc/profile` and `/etc/bash.bashrc`, however, a global variable created with `export` will only exist as far as the session is active, so in order to make permanent it is necessary to manually set the new global variables in the config files previously mentioned. Finally, a variable can be deleted by using the `unset` command.

Following on the same example, this is how the `export` command is called:

> user@host:~$ export random

The variable then can be erased with `unset`:

> user@host:~$ unset $random

Both variables and aliases are very useful when creating scripts. A script could be any text file with code designed to fulfill a specific role, the key difference between a simple, plain text file and a script is that the script has the proper execution permissions configured for it to be run by at least one Linux user.

> Note: all script files start with a Shebang line, which has the following syntax: `#!<path_to_interpreter>`, in the case of a `bash` script, the shebang line will include the full path to the `bash` executable file: `#!/bin/bash`.

A script can always be called from the CLI by providing the full path to the script. However, there are multiple scripts and commands that can be called by just entering their names without any path description - these kind of scripts are the ones located inside the list of directories contained in the `$PATH` variable.

> For example, a command like `pwd` can be called from the terminal without having to speciy its full path: `/bin/pwd`.

It is possible to add more destinations to the `$PATH` variables so the custom scripts could be called by just entering their names. There are two main ways to accomplish this:

- Temporarily modifying the `$PATH` variable: by doing this, the changes will last until the session ends. Here is an example of how to this by recursively using the current value of the `$PATH` variable with `export`:

    > For example, let's try to add `/home` to `$PATH`:  
    > user@host:~$ export PATH="/home:$PATH"

    Linux will always run the first match for the script inside the directories of `$PATH`, so it is recommended to set the custom directories at the very beginning of the variable.

- Permanently modifying the `$PATH` variable: this is done by changing one of the bashrc files and setting the same command inside the file:

    > user@host:~$ nano /~/.bashrc  
    > export PATH="/home:$PATH"

Finally the `which` command is very useful when trying to determine the location of the files for a given script/command. This will allow the user to know if the target command is already inside `$PATH` and will provide the path that is necessary to append in case that it is not included in the variable. 

> For example, for the `pwd` command:  
> user@host:~ $ which pwd  
> /usr/bin/pwd

