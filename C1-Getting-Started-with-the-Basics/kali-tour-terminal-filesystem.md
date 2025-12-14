<!-- File: kali-tour-terminal-filesystem.md -->

# A Tour of Kali

Overview of initial Kali access, the terminal, and the Linux filesystem layout.

## Login Basics

- **Login screen**: Use the root account to log in.
  - **Username**: `root`
  - **Default password**: `toor`
- **Desktop access**: After login, you can access the Kali desktop.

## The Terminal

- **Terminal**: The command line interface (CLI) used to run commands.
- **How to open**:
  - **Desktop icon**: Terminal icon at the bottom of the desktop (double click)
  - **Keyboard shortcut**: `CTRL+ALT+T`
- **Shell**: The command-line environment where commands run.
  - Linux has multiple shells.
  - **bash**: Most popular shell and the default in Kali (and many other distributions).
- **Change password**:
  - **Command**: `passwd`

## The Linux Filesystem

- **Filesystem model**:
  - Linux uses a logical filesystem.
  - No drive letters like Windows (no `C:` at the base).
- **Top of the filesystem**:
  - **/**: The top-level directory, called the root of the filesystem.
  - Note: This is different from the **root user**.

### Key Directories

- **/root**: Home directory of the root user.
- **/etc**: Configuration files that control when and how programs start.
- **/home**: Home directories for users.
- **/mnt**: Where other filesystems are attached (mounted).
- **/media**: Where CDs and USB devices are usually attached (mounted).
- **/bin**: Application binaries (similar to Windows executables).
- **/lib**: Libraries (shared programs similar to Windows DLLs).

### Practical Note on Root Usage

- **Routine work**: Avoid logging in as root for everyday tasks.
- **Risk**: If someone compromises your system while you are logged in as root, they gain root privileges.
- **Use a regular user**: For regular applications, web browsing, and tools like `Wireshark`.