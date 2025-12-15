# Finding Yourself with `pwd`

- **GUI vs CLI**: In the command line, your current directory is not always obvious.
- **Why it matters**: To navigate effectively, you usually need to know your current location first.
- **Command**: `pwd` (present working directory)
- **Purpose**: Prints your current directory path in the filesystem.

## Example

```bash
kali >pwd
/root
```

- **Meaning**: You are currently in `/root` (the root user’s home directory).
- If you log in as **root**, you are typically placed in `/root`, which is one level below `/`.
- If you are in another directory, `pwd` prints that directory path instead.

# Checking Your Login with `whoami`

- **root user**: The superuser/system administrator account with privileges such as adding users, changing passwords, and changing privileges.
- **Why it matters**: Many tools and commands require **root privileges**, so you may need to be logged in as root.
- **Command**: `whoami`
- **Purpose**: Displays the username of the account currently logged in.

## Examples

```bash
kali >whoami
root
```

```bash
kali >whoami
OTW
```

# Navigating the Linux Filesystem

Navigation in the terminal is essential for finding applications, files, and directories in a text-based environment.

## Changing Directories with `cd`

- **Command**: `cd`
- **Purpose**: Change the current directory from the terminal.

### Change to a specific directory

- **Example**: Move to `/etc` (stores configuration files)

```bash
kali >cd /etc
root@kali:/etc#
```

- **Note**: The prompt updates (example: `root@kali:/etc#`) to show the current directory.

### Confirm your current directory

- **Command**: `pwd`

```bash
root@kali:/etc# pwd
/etc
```

### Move up one level with `..`

- **Command**: `cd ..`
- **Purpose**: Move up one directory level (toward `/`).

```bash
root@kali:/etc# cd ..
root@kali:/# pwd
/
root@kali:/#
```

### Move up multiple levels

- **Rule**: Use one `..` per level you want to move up.
  - **One level**: `..`
  - **Two levels**: `../..`
  - **Three levels**: `../../..`

- **Example**: Move up two levels (`/` between pairs)

```bash
kali >cd .. ..
/
```

### Jump to the filesystem root

- **Command**: `cd /`
- **Purpose**: Move directly to `/` from anywhere.

## Listing Directory Contents with `ls`

- **Command**: `ls`
- **Purpose**: List files and subdirectories in a directory.
- **Windows comparison**: Similar to `dir`.

### Example output

```bash
kali >ls
bin    initrd.img        
media        
boot   initrd.img.old    mnt          
dev    lib               
etc    lib64             
opt          
proc         
home   lost+found        
srv        
root         
run        
sbin       
var
vmlinuz
vmlinuz.old
tmp
usr
```

### List another directory without entering it

- **Example**: Show contents of `/etc`

- **Command pattern**: `ls <directory>`
  - Example mentioned: `ls /etc`

## Long Listing with `ls -l`

- **Command**: `ls -l`
- **Purpose**: Show more details about files and directories.
- **Includes**: Permissions, owner, group, size, timestamps (created/modified), name, link count, and whether an entry is a file or directory.

## Show Hidden Files with `-a`

- **Hidden files**: Not shown by `ls` or `ls -l` by default.
- **Command**: `ls -a` (or combined with long listing)

```bash
kali >ls -la
```

- **Tip**: If a file is missing from a listing, try using the `-a` flag.

# Getting Help in Linux

Most commands, applications, and utilities include built-in help output that explains usage and available options.

## Built-in Help Options

- **Help file access**: Run a command with a help option to see guidance and a short description.

### Word options use `--`

- **Convention**: Use a double dash `--` before word options (example: `help`).

```bash
kali >aircrack-ng --help
```

### Single-letter options use `-`

- **Convention**: Use a single dash `-` before single-letter options (example: `-h`).

```bash
kali >nmap -h
```

## Common Variations

- **Possible help flags**: `--help`, `-h`, `-?`
- **Note**: Not every application supports all of these.
- **Tip**: If one help option does not work, try another.

# Referencing Manual Pages with `man`

Manual pages provide detailed documentation for most Linux commands and applications, including a description and command synopsis.

## Open a Manual Page

- **Command pattern**: `man <command>`

### Example

```bash
man aircrack-ng
```

- **Result**: Opens the manual page for `aircrack-ng` with more detail than a basic help screen.

## Navigate and Exit in `man`

- **Scroll forward**: `ENTER`
- **Page down**: `PG DN`
- **Page up**: `PG UP`
- **Quit / Exit**: `q`
  - Returns you to the command prompt.
