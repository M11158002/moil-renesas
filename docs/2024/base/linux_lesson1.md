# Introduction to Linux: First Lesson Guide

## **1. What is Linux?**

Linux is an open-source operating system, which means that anyone can freely use, modify, and distribute it. It is based on Unix but offers more flexibility, and is widely used in servers, desktop systems, and embedded devices.

### **Why use Linux?**

- **Open-source and Free**: Linux is free to use and most distributions (such as Ubuntu, CentOS, Debian, etc.) can be downloaded and installed without cost.
- **Stability and Security**: Linux is known for being a highly stable and secure system, especially suited for servers and large-scale systems.
- **Flexibility**: Due to its open-source nature, Linux can be highly customized to meet specific needs.
- **Community Support**: With a large developer and user community, there is a wealth of support and resources available online.

## **2. Understanding Linux Desktop vs Command Line**

In Linux, there are two main ways of interacting with the system:

- **Graphical User Interface (GUI)**: This is the graphical interface you see, similar to Windows or macOS. You interact with the system by clicking on icons.
- **Command Line Interface (CLI)**: This is where you type commands into a terminal to interact with the system. Many advanced Linux users and system administrators rely on the command line for efficiency.

Today's lesson will focus primarily on the **Command Line Interface (CLI)**, as it is the foundation of working with Linux.

## **3. Basic Linux Commands**

### **Launching the Terminal**

In Linux, you need to open a **Terminal** to execute commands. Usually, you can open the terminal in the following ways:

- **Ubuntu Desktop**: Press `Ctrl` + `Alt` + `T`, or search for "Terminal" in the application menu.
- **Other Desktop Environments**: The method will vary, but most Linux distributions allow you to find the terminal in the application menu.

### **Command Structure**

Each Linux command typically consists of three parts:
1. **Command**: The operation to perform (e.g., `ls`, `cd`).
2. **Option** (optional): Modifies the behavior of the command (e.g., `-l`, `-a`).
3. **Argument** (optional): Specifies the target of the command (e.g., a file or directory name).

For example, `ls -l /home`:
- `ls` is the command to list files.
- `-l` is an option to display detailed information.
- `/home` is the argument, specifying the directory to list.

### **Common Basic Commands**

#### `pwd` – Print Working Directory

The `pwd` command stands for "print working directory," and it shows the current directory you're in.

```bash
$ pwd
/home/username
```

#### `ls` – List Files in a Directory

The `ls` command lists the files and directories in the current directory.

```bash
$ ls
Documents  Downloads  Pictures  Videos
```

Use `ls -l` for detailed information, and `ls -a` to show hidden files.

#### `cd` – Change Directory

The `cd` command is used to change directories.

```bash
$ cd Documents
$ pwd
/home/username/Documents
```

#### `touch` – Create a New File

The `touch` command creates a new empty file.

```bash
$ touch newfile.txt
```

#### `mkdir` – Create a New Directory

The `mkdir` command creates a new directory.

```bash
$ mkdir new_directory
```

#### `cp` – Copy Files or Directories

The `cp` command copies files or directories.

```bash
$ cp source.txt destination.txt
```

#### `mv` – Move or Rename Files

The `mv` command is used to move or rename files.

```bash
$ mv oldname.txt newname.txt
```

#### `rm` – Remove Files

The `rm` command removes files. Be careful when using `rm` because it does not move files to the trash—they are deleted permanently.

```bash
$ rm unwantedfile.txt
```

#### `cat` – Display File Contents

The `cat` command is used to display the contents of a file.

```bash
$ cat example.txt
Hello, this is a sample file.
```

#### `man` – View Command Manual

Every Linux command has a manual page, which you can view using the `man` command. This is useful for learning more about the options and syntax of each command.

```bash
$ man ls
```

### **Basic File Permissions**

Linux is a multi-user system, and every file and directory has associated permissions. Each file has three basic types of permissions:
- **r**: Read
- **w**: Write
- **x**: Execute

Permissions are assigned to three different groups of users:
- **Owner**: The user who owns the file.
- **Group**: The group associated with the file.
- **Other**: All other users.

You can see a file's permissions by using `ls -l`:

```bash
$ ls -l example.txt
-rw-r--r-- 1 user user 1234 Jan 1 12:00 example.txt
```

### **Understanding File Permissions**

- The first column (`-rw-r--r--`) represents the permissions:
  - `-` means this is a regular file.
  - `rw-` means the owner has read and write permissions.
  - `r--` means the group has read-only permission.
  - `r--` means others have read-only permission.

### **4. Practice Tasks**

1. Open the terminal and type `pwd` to check your current directory.
2. Use `ls` to list the files in your current directory.
3. Use `mkdir` to create a new directory, then use `cd` to enter that directory.
4. Use `touch` to create a new file and verify it with `ls`.
5. Use `rm` to delete the file you just created.

### **5. Summary**

In this lesson, we covered basic Linux commands that allow you to navigate the file system, create and manage files, and query help for commands. These basic operations form the foundation of using Linux effectively. Once you get comfortable with these commands, you can move on to more advanced topics, such as file manipulation tools (`grep`, `awk`, `sed`) and writing shell scripts to automate tasks.

---

This tutorial is designed to help students get started with the basic Linux command line operations. As they progress, they can move on to more advanced topics like text processing, file system management, and scripting.