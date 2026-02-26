# Linux File System

So far, we have understood what Linux is and why it is important.

By now, you should have your playground ready --- either a local Linux
installation or a cloud VM --- so you can experiment alongside this
guide.

Let's begin with the Linux file system.

------------------------------------------------------------------------

## Everything in Linux Is a File (or a Directory)

This statement may sound strange at first.

But it is fundamental to understanding Linux.

Linux treats almost everything as a file:

-   Regular files
-   Directories
-   Devices
-   Processes
-   Memory information
-   System configuration

We will unpack this idea step by step.

------------------------------------------------------------------------

## What Is a File System?

In simple terms:

> A file system defines how an operating system stores, organizes, and
> retrieves data.

In Linux, the file system is structured as a hierarchical tree.

At the top of this tree is a single directory:

    /

This is called the **root directory**.

Everything in Linux exists under `/`.

Unlike Windows, where you see separate drives like `C:` or `D:`, Linux
does not divide storage that way. Instead:

-   All storage devices are **mounted** into the same directory tree.
-   Everything ultimately connects back to `/`.

You can visualize the root structure using:

``` bash
tree -L 1 -d /
```

------------------------------------------------------------------------

# Important Directories Under `/`

Let's go through each folder and understand its purpose.

------------------------------------------------------------------------

## `/` --- Root Directory

The root directory is the top-most directory in Linux.

All other directories branch out from here.

Think of it as the base of the entire filesystem hierarchy.

Every path in Linux starts from `/`.

Examples:

    /home/user
    /etc/passwd
    /var/log

------------------------------------------------------------------------

## `/bin` --- Essential User Binaries

`/bin` contains essential command binaries required for basic system
functionality.

These are programs that both users and the system rely on.

Examples include:

-   `ls`
-   `cp`
-   `mv`
-   `chmod`
-   `cat`

To see what exists inside `/bin`:

``` bash
cd /bin
ls
```

These commands are critical for system operation. Even in minimal or
rescue mode, `/bin` must be available.

------------------------------------------------------------------------

## `/boot` --- Bootloader Files

This directory contains files necessary for the system to start.

If `/boot` is corrupted, the system may fail to boot.

It typically contains:

-   Bootloader configuration files\
-   The Linux kernel image\
-   Initramfs (Initial RAM File System)

Initramfs is a temporary root file system loaded into memory during the
early boot process.

Modifying files in `/boot` should be done carefully.

------------------------------------------------------------------------

## `/dev` --- Device Files

`/dev` contains device files.

In Linux, hardware devices are represented as files.

Examples:

-   `/dev/sda` → Hard disk\
-   `/dev/tty` → Terminal device\
-   `/dev/null` → Discards all data written to it

This is where the statement *"everything is a file"* becomes powerful.

When you write to a device, you are writing to a file.\
When you read from a disk, you are reading from a file.

Linux abstracts hardware interaction through the filesystem.
