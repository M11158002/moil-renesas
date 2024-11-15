# Linux: Third Lesson - Managing Processes, File Compression, and Shell Scripting

## **1. Review of Previous Lessons**

Before we dive into new topics, let's quickly review what we covered in the previous lessons:

- **First Lesson**: Basic file and directory manipulation, navigating the filesystem, understanding basic commands (`pwd`, `ls`, `cd`, `touch`, `mkdir`, `cp`, `mv`, `rm`, `cat`, `man`).
- **Second Lesson**: Searching files (`find`, `locate`, `which`), working with directories and files (`rmdir`, `tar`, `zip`, `unzip`), text processing tools (`grep`, `sed`, `awk`), and managing file permissions (`chmod`, `chown`).

Today, we will:
1. Learn how to manage processes in Linux.
2. Dive deeper into file compression and archiving tools.
3. Start writing simple shell scripts to automate tasks.

---

## **2. Managing Processes**

Linux, like any modern operating system, runs multiple processes simultaneously. As a user, you often need to know how to manage and interact with these processes.

### **`ps` – View Running Processes**

The `ps` (process status) command shows the current processes running on the system. 

- Basic command to list your own processes:
  ```bash
  $ ps
  ```

- To see more detailed information, including process IDs (PIDs), use:
  ```bash
  $ ps aux
  ```

  - `a` shows processes from all users.
  - `u` displays the processes in a user-oriented format.
  - `x` includes processes not attached to a terminal (background processes).

- To filter for specific processes, use `grep`:
  ```bash
  $ ps aux | grep firefox
  ```

### **`top` – Monitor System Resource Usage**

The `top` command displays real-time information about processes, including CPU and memory usage. This is helpful for monitoring system performance.

- Simply type:
  ```bash
  $ top
  ```

- In the top view, you will see a list of processes, their CPU and memory usage, and the time they have been running.

- To quit `top`, press `q`.

### **`kill` – Terminate a Process**

Sometimes you need to stop a process that's not responding. The `kill` command sends a signal to a process to terminate it.

- To kill a process by PID (Process ID):
  ```bash
  $ kill <PID>
  ```

  For example:
  ```bash
  $ kill 1234
  ```

- If the process does not stop with `kill`, you can forcefully terminate it with the `-9` option:
  ```bash
  $ kill -9 1234
  ```

### **`nohup` – Run Processes in the Background**

`nohup` (short for "no hangup") is used to run a command that will continue running even after you log out or close the terminal.

- Example:
  ```bash
  $ nohup python myscript.py &
  ```

  The `&` symbol runs the process in the background, and `nohup` ensures it keeps running even after the terminal session ends.

### **`jobs`, `bg`, `fg` – Managing Background Processes**

You can run a process in the background and bring it back to the foreground.

- To run a process in the background:
  ```bash
  $ sleep 300 &
  ```

- List jobs running in the background:
  ```bash
  $ jobs
  ```

- To bring a job to the foreground:
  ```bash
  $ fg %1
  ```

  `%1` refers to the job number (you can see this from the `jobs` output).

---

## **3. File Compression and Archiving**

Linux provides many utilities for compressing and archiving files. In this section, we’ll explore more advanced options for handling file compression.

### **`tar` – Create and Extract Archives**

The `tar` command is essential for compressing and extracting files and directories into single archive files.

- To create an archive:
  ```bash
  $ tar -cvf archive.tar /path/to/directory
  ```

  - `c` means create.
  - `v` means verbose (shows file names as they are archived).
  - `f` specifies the filename of the archive.

- To create a compressed `.tar.gz` archive:
  ```bash
  $ tar -czvf archive.tar.gz /path/to/directory
  ```

  - `z` adds gzip compression.

- To extract a `.tar` archive:
  ```bash
  $ tar -xvf archive.tar
  ```

- To extract a `.tar.gz` archive:
  ```bash
  $ tar -xzvf archive.tar.gz
  ```

### **`zip` and `unzip`**

The `zip` and `unzip` commands are used to handle `.zip` files, which are commonly used for file compression.

- To create a `.zip` archive:
  ```bash
  $ zip archive.zip file1.txt file2.txt
  ```

- To unzip an archive:
  ```bash
  $ unzip archive.zip
  ```

### **`gzip` and `gunzip`**

`gzip` is another utility for file compression. It's typically used to compress single files.

- To compress a file:
  ```bash
  $ gzip file.txt
  ```

  This will create a compressed file called `file.txt.gz`.

- To decompress a `.gz` file:
  ```bash
  $ gunzip file.txt.gz
  ```

---

## **4. Introduction to Shell Scripting**

One of the most powerful features of Linux is the ability to automate tasks using shell scripts. A shell script is a file containing a series of commands that are executed in sequence.

### **Creating a Simple Shell Script**

1. Open a text editor (e.g., `nano` or `vim`) and create a new file with a `.sh` extension:
   ```bash
   $ nano myscript.sh
   ```

2. Add the following lines to the script:

   ```bash
   #!/bin/bash
   echo "Hello, world!"
   ```

   - `#!/bin/bash` is called a **shebang** and tells the system to use the Bash shell to execute the script.
   - `echo "Hello, world!"` prints the message to the terminal.

3. Save the file and exit the text editor.

### **Making the Script Executable**

Before you can run your script, you need to make it executable:

```bash
$ chmod +x myscript.sh
```

### **Running the Script**

To run the script:

```bash
$ ./myscript.sh
```

This will print `Hello, world!` to the terminal.

### **Adding More Commands to the Script**

You can add more commands to your script to automate tasks. For example:

```bash
#!/bin/bash
echo "Starting backup process..."
cp -r /home/user/data /backup/
echo "Backup completed!"
```

This script will copy data from the `data` directory to a backup directory and display a message before and after the backup process.

### **Using Variables in Shell Scripts**

You can use variables in your shell script to store values. For example:

```bash
#!/bin/bash
filename="backup_$(date +'%Y%m%d').tar.gz"
echo "Creating backup archive: $filename"
tar -czvf $filename /home/user/data
```

This script will create a backup archive with the current date in the filename.

---

## **5. Practice Tasks**

1. **Process Management**: Use `ps`, `top`, and `kill` to identify and terminate processes on your system.
2. **File Compression**: Create a `.tar.gz` archive of a directory, and then extract it.
3. **Shell Script**: Write a script that takes a directory as input, creates a backup, and logs the time the backup was created.

---

## **6. Summary**

In this lesson, we covered:

- **Managing Processes**: Using commands like `ps`, `top`, `kill`, and `nohup` to manage processes.
- **File Compression and Archiving**: Advanced techniques with `tar`, `zip`, `gzip`, and `gunzip` for handling compressed archives.
- **Shell Scripting**: Introduction to creating simple shell scripts to automate tasks, using variables and running commands in sequence.

These skills will help you automate repetitive tasks, manage system resources, and work more efficiently in a Linux environment. In future lessons, we will explore more advanced scripting techniques and delve deeper into system administration tasks.

---

This lesson provides an introduction to process management, file compression, and shell scripting—key topics that enable users to work more efficiently in a Linux environment. The next lesson can cover more advanced topics like user management, permissions, and working with network tools.