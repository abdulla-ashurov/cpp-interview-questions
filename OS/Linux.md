# JUNIOUR

## OS/Linux

### 1. What is a package manager?

A package manager is Linux is a tool that automates the process of installing, updating, configuring, and removing software packages on Linux system. It manages software dependencies and ensures that all required components are present. Package managers can work with local or remote software repositories and typically handle both command-line tools and graphical applications.

### 2. What types of package managers are there?

- apt (for Debian/Ubuntu-based systems)
- yum or dnf (for Red Hat-based systems)
- pacman (for Arch Linux)
- zypper (for openSUSE)
- rpm (for Red Hat-based systems, but more of a low-level package manager)
- snap and flatpak (for universal package management across distributions)

`snap` and `flatpak` allow developers to package software with all its dependencies, which makes it possible to install the software on different Linux distributions without worrying about compatibility issues. On the other hand, apt only works within the ecosystem of Debian/Ubuntu-based distributions, which typically rely on a set of pre-configured dependencies and library versions.

### 3. Wha is a PID?

PID stands for Process Identifier. It is a unique numerical value assigned by the operation system to each running process. The PID allows the system and users to manage processes, track their resource usage, and perform tasks like killing or pausing processes using commands such as `kill` or `ps` (process status).

We can use commands like `top`, `htop`, or `ps` to find the `PID` of a process. For example, `ps aux | grep <process_name>` will list all processes with that name and show their PIDs. top and htop provide an interactive view of all running processes along with their PIDs.

### 4. What are file descriptors used for?

A file descriptor is a non-negative integer used by the operating system to access and manage open files, sockets, pipes, and devices. In Linux, the standard file descriptors are 0 for standard input (`stdin`), 1 for standard output (`stdout`), and 2 for standard error (`stderr`). File descriptors are essential in low-level I/O operations, such as reading from or writing to a file or communcating over a network socket.

If you close any file descriptor, any attempt to write to using low level functions like `write(1, ...)` will fail and retur `-1`, with `errno` set to `EBADF` (Bad File Descriptor). High-level functions like `printf()` will also fail internally when they try to flush the output buffer, possible causing error messages or crashes.

### 5. Explain the standard process file descriptors

In Unix-like systems, each process is automatically assigned three standard file descriptors:

1. Standard Input (stdin): `fd 0` - used for reading input from the user or other sources.
2. Standard Output (stdout): `fd 1` - used for printing output to the screen or terminal.
3. Standard Error (stderr): `fd 2` - used for outputting error messages separately from the standard output.

### 6. What is a Pipe?

A pipe is a mechanism used in Unix-like operating systems (including Linux) to enable communication between two processes. It allows the output of one process to be used as input by another process, enabling a sort of "pipeline" of commands.

How it works:

- A pipe is represented by the `|` operator in the shell.
- When you use a pipe, the `stdout` of the first command is passed as `stdin` to the second command.

```bash
ls | grep "file"
# The ls command lists the files in the directory
# The grep "file" command filters the output of ls, showing only the lines that contain "file"
```

### 7. What is a Named Pipe?

Both named pipes and anonymous pipes allow communication between processes, but they have important differences.

**Anonymous Pipe**: An anonymous pipe is a temporary pipe used for inter-process communication (IPC) between related processes (e.g., a parent process and child process). The pipe exists only as long as the processes using it are alive. The pipe has no name or path and is typically identified by the system as a piple file descriptor (e.g., `pipe(fd)`). Anonymous pipes are commonly used in shell pipelines or between processes that share a parent-child relationship.

```bash
ps aux | grep "python"
```

**Named Pipe (FIFO)**: A named pipe, also known as a FIFO (First In, First Out), is a special file in the filesystem that allows communication between unrelated process. A named pipe persistes in the filesystem, and processes can open it and write to or read from it at different times. The pipe is given a name and exists as a special file (e.g., `/tmp/myfifo`). Named pipes are used when processes do not have a parent-child relationship and need to communicate via a common file.

```bash
mkfifo /tmp/myfifo # Create a named pipe
cat /tmp/myfifo # Process 1 reads from the named pipe
echo "Hello" > /tmp/myfifo # Process 2 writes to the named pipe
```

### 8. What is a UID?

UID stands for User Identifier. It is a unique number assigned to each user on a system to distinguish them. It is used to identify users and control access to system resources, such as files and processes. For example, `root` has UID 0, and regural users have higher UIDs.
