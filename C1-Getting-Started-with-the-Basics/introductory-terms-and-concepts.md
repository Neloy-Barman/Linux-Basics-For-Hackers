# Introductory Terms and Concepts

A quick reference for key Linux terms used throughout beginner hacking and penetration testing workflows.

## Key Terms

- **Binaries**: Executable files (similar to Windows executables).
  - Common locations: `/usr/bin`, `/usr/sbin`
  - Examples: `ps`, `cat`, `ls`, `cd`
  - Also includes applications such as `aircrackng` and `Snort`

- **Case sensitivity**: Linux treats names with different letter cases as different.
  - Example idea: `Desktop`, `desktop`, and `DeskTop` are all different names.
  - Common issue: If you see “file or directory not found” but it exists, check the case.

- **Directory**: Same concept as a folder in Windows.
  - Used to organize files, usually in a hierarchical structure.

- **Home**: Each user has their own home directory.
  - Location: `/home`
  - Default place where your created files are typically saved.

- **Kali**: A Linux distribution designed for penetration testing.
  - Includes hundreds of preinstalled tools.
  - Version referenced: Kali `2018.2` (released April 2018).

- **root**: The administrator (superuser) account in Linux.
  - Can do nearly anything on the system (reconfigure, add users, change passwords).
  - Common in hacking/pentesting because many tools require root access.

- **Script**: A series of commands run in an interpreted environment.
  - Many hacking tools are scripts.
  - Can run with interpreters such as `bash`, `Python`, `Perl`, or `Ruby`.
  - `Python` is noted as the most popular interpreter among hackers.

- **Shell**: The environment and interpreter used to run commands.
  - Most common: `bash` (Bourne-again shell)
  - Other examples: C shell, Z shell
  - Focus here: `bash` is used exclusively.

- **Terminal**: A command line interface (CLI).