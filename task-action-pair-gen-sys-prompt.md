``````
# USER CONTENT
```
<user_book_content>
```

# TASK
Extract command references with task descriptions and explanations from the provided content. Follow the structure, rules, and formatting demonstrated in the examples. Return the response within 4-backticks enforced block.

# FORMAT RULES
1. Each entry starts with a dash (-) followed by an action/task description
2. Commands are placed inside ```bash``` code blocks
3. Explanatory notes use nested bullet points
4. Use **bold** for field names and key terms
5. Use `backticks` for values, commands, file paths, and technical terms
6. Group related commands under one task when appropriate
7. Include relevant output field explanations when applicable

# EXAMPLES
## EXAMPLE 1
### INPUT
```
Finding Yourself with pwd
Unlike when you’re working in a graphical user interface (GUI) environment like
Windows or macOS, the command line in Linux does not always make it apparent
which directory you’re presently in. To navigate to a new directory, you usually need to
know where you are currently. The present working directory command, pwd, returns
your location within the directory structure.
Enter pwd in your terminal to see where you are:
kali >pwd
/root
In this case, Linux returned /root, telling me I’m in the root user’s directory. And
because you logged in as root when you started Linux, you should be in the root user’s
directory, too, which is one level below the top of the filesystem structure (/).
If you’re in another directory, pwd will return that directory name instead.
```
### OUTPUT
````
- Finding Yourself in the current Directory
  ```bash
    pwd
  ```
````

## EXAMPLE 2
### INPUT
```
Checking Your Login with whoami
In Linux, the one “allpowerful” superuser or system administrator is named root, and
it has all the system privileges needed to add users, change passwords, change
privileges, and so on. Obviously, you don’t want just anyone to have the ability to make
such changes; you want someone who can be trusted and has proper knowledge of the
operating system. As a hacker, you usually need to have all those privileges to run the
programs and commands you need (many hacker tools won’t work unless you have root
privileges), so you’ll want to log in as root.
If you’ve forgotten whether you’re logged in as root or another user, you can use the
whoami command to see which user you’re logged in as:
kali >whoami
root
If I had been logged in as another user, such as my personal account, whoami would have
returned my username instead, as shown here:
kali >whoami
OTW
```
### OUTPUT
````
- Checking Logged in User
  ```bash
    whomai
  ```
````

## EXAMPLE 3
### INPUT
```
ANALYZING NETWORKS WITH IFCONFIG
The ifconfig command is one of the most basic tools for examining and interacting with
active network interfaces. You can use it to query your active network connections by
simply entering ifconfig in the terminal. Try it yourself, and you should see output
similar to 
Listing 31.
kali >ifconfig
➊eth0Linkencap:EthernetHWaddr 00:0c:29:ba:82:0f
➋inet addr:192.168.181.131 ➌Bcast:192.168.181.255 ➍Mask:255.255.255.0
snip
➎lo Linkencap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
snip
➏wlan0 Link encap:EthernetHWaddr 00:c0:ca:3f:ee:02
Listing 31: Using ifconfig to get network information
As you can see, the command ifconfig shows some useful information about the active
network interfaces on the system. At the top of the output is the name of the first
detected interface, eth0 ➊, which is short for Ethernet0 (Linux starts counting at 0
rather than 1). This is the first wired network connection. If there were more wired
Ethernet interfaces, they would show up in the output using the same format (eth1, eth2,
and so on).
The type of network being used (Ethernet) is listed next, followed by HWaddr and an
address; this is the globally unique address stamped on every piece of network
hardware—in this case, the network interface card (NIC), usually referred to as the
media access control (MAC) address.
The second line contains information on the IP address currently assigned to that
network interface (in this case, 192.168.181.131 ➋); the Bcast ➌, or broadcast address,
which is the address used to send out information to all IPs on the subnet; and finally
the network mask (Mask ➍), which is used to determine what part of the IP address is
connected to the local network. You’ll also find more technical info in this section of the
output, but it’s beyond the scope of this Linux networking basics chapter.
The next section of the output shows another network connection called lo ➎, which is
short for loopback address and is sometimes called localhost. This is a special software
address that connects you to your own system. Software and services not running on
your system can’t use it. You would use lo to test something on your system, such as
your own web server. The localhost is generally represented with the IP address
127.0.0.1.
The third connection is the interface wlan0 ➏. This appears only if you have a wireless
interface or adapter, as I do here. Note that it also displays the MAC address of that
device (HWaddr).
This information from ifconfig enables you to connect to and manipulate your local area
network (LAN) settings, an essential skill for hacking.
```
### OUTPUT
````
- Grab and Analyze Network Information
  ```bash
    ifconfig
  ```
  - **<detected_device><n>:** The name of the detected interface. For instance, `docker0`, `eth0`, `l0`. 
    - **eth0:** `Ethernet0`; First wired connection.
    - **l0:** `loopback address`; It is short for loopback address and sometimes is called localhost. It lets us to connect to our own system.
    - **docker0:** `Docker Bridge`; Virtual network interface created by Docker for container communication.
    - **wlan0:** `Wireless Interace/Adapter`.
  - **inet:** `IP Address` currently assigned to the network interface. 
  - **netmask:** `Network Mask` is used to determine what part of the IP address is connected to the network.
  - **broadcast:** `Broadcast Address` is used to send out information to all IPs on the subnet.
  - **inet6:** `IPv6 Address` currently assigned to the network interface.
  - **ether:** `MAC Address` (Media Access Control) is the unique hardware address assigned to the network interface.
````

## EXAMPLE 4
### INPUT
```
Spoofing Your MAC Address
You can also use ifconfig to change your MAC address (or HWaddr). The MAC address is
globally unique and is often used as a security measure to keep hackers out of networks
—or to trace them. Changing your MAC address to spoof a different MAC address is
almost trivial and neutralizes those security measures. Thus, it’s a very useful technique
for bypassing network access controls.
To spoof your MAC address, simply use the ifconfig command’s down option to take
down the interface (eth0 in this case). Then enter the ifconfig command followed by the
interface name (hw for hardware, ether for Ethernet) and the new spoofed MAC address.
Finally, bring the interface back up with the up option for the change to take place.
Here’s an example:
kali >ifconfig eth0 down
kali >ifconfig eth0 hw ether 00:11:22:33:44:55
kali >ifconfig eth0 up
Now, when you check your settings with ifconfig, you should see that HWaddr has changed
to your new spoofed IP address!
```
### OUTPUT
````
- Spoof MAC Address to `00:11:22:33:44:55`
  ```bash
    ifconfig eth0 down
    ifconfig hw ether 00:11:22:33:44:55
    ifconfig eth0 up
  ```
````

## EXAMPLE 5
### INPUT
```
Assigning New IP Addresses from the DHCP Server
Linux has a Dynamic Host Configuration Protocol (DHCP) server that runs a daemon—
a process that runs in the background—called dhcpd, or the dhcp daemon. The DHCP
server assigns IP addresses to all the systems on the subnet and keeps log files of which
IP address is allocated to which machine at any one time. This makes it a great resource
for forensic analysts to trace hackers with after an attack. For that reason, it’s useful to
understand how the DHCP server works.
Usually, to connect to the internet from a LAN, you must have a DHCPassigned IP.
Therefore, after setting a static IP address, you must return and get a new DHCP
assigned IP address. To do this, you can always reboot your system, but I’ll show you
how to retrieve a new DHCP without having to shut your system down and restart it.
To request an IP address from DHCP, simply call the DHCP server with the command
dhclient followed by the interface you want the address assigned to. Different Linux
distributions use different DHCP clients, but Kali is built on Debian, which uses
dhclient. Therefore, you can assign a new address like this:
kali >dhclient eth0
The dhclient command sends a DHCPDISCOVER request from the network interface specified
(here, eth0). It then receives an offer (DHCPOFFER) from the DHCP server (192.168.181.131
in this case) and confirms the IP assignment to the DHCP server with a dhcp request.
kali >ifconfig
eth0Linkencap:EthernetHWaddr 00:0c:29:ba:82:0f
inet addr:192.168.181.131 Bcast:192.168.181.131 Mask:255.255.255.0
Depending on the configuration of the DHCP server, the IP address assigned in each
case might be different.
Now when you enter ifconfig, you should see that the DHCP server has assigned a new
IP address, a new broadcast address, and new netmask to your network interface eth0
```
### OUTPUT
````
- Assign new IP Address from DHCP
  ```bash
    dhclient eth0
  ```
  - If it raises issues, follow the directives from CLI.
    ```bash
      sudo apt install isc-dhcp-client
    ```
- How DHCP works
    - The dhclient command sends a DHCPDISCOVER request from the network interface specified
    - It then receives an offer (DHCPOFFER) from the DHCP server
    - It confirms the IP assignment to the DHCP server with a dhcp request.
````

## EXAMPLE 6
### INPUT
```
GRANTING PERMISSIONS
Each and every file and directory must be allocated a particular level of permission for
the different identities using it. The three levels of permission are as follows:
r Permission to read. This grants permission only to open and view a file.
w Permission to write. This allows users to view and edit a file.
x Permission to execute. This allows users to execute a file (but not necessarily view or
edit it).
In this way, the root user can grant users a level of permission depending on what they
need the files for. When a file is created, typically the user who created it is the owner of
the file, and the owning group is the user’s current group. The owner of the file can
grant various access privileges to it. Let’s look at how to change permissions to pass
ownership to individual users and to groups.
```
### OUTPUT
````
- What does the symbol mean?
  - `r` -> The permission to read. The user can only open and view the file.
  - `w` -> The permission to write. The user can view and perform changes to the file.
  - `x` -> The permission to execute. The user can exectute the file.
````

## EXAMPLE 7
### INPUT
```
Granting Ownership to an Individual User
To move ownership of a file to a different user so that they have the ability to control
permissions, we can use the chown (or change owner) command:
kali >chown ➊bob ➋/tmp/bobsfile
Here, we give the command, the name of the user we are giving ownership to, and then
the location and name of the relevant file. This command grants the user account for
Bob ➊ ownership of bobsfile ➋.
```
### OUTPUT
````
- Create a file `/tmp/kalifile`
    ```bash
        touch /tmp/kalifile
    ```
- Grant ownership of `/tmp/kalifile` to `kali`
    ```bash
        chown kali /tmp/kalifile
    ```
- Delete file `/tmp/kalifile`
    ```bash
        rm /tmp/kalifile
    ```
````

## EXAMPLE 8
### INPUT
```
Changing Permissions with UGO
Although the numeric method is probably the most common method for changing
permissions in Linux, some people find chmod’s symbolic method more intuitive—both
methods work equally well, so just find the one that suits you. The symbolic method is
often referred to as the UGO syntax, which stands for user (or owner), group, and
others.
UGO syntax is very simple. Enter the chmod command and then the users you want to
change permissions for, providing u for user, g for group, or o for others, followed by one
of three operators:-Removes a permission
+Adds a permission
=Sets a permission
After the operator, include the permission you want to add or remove (rwx) and, finally,
the name of the file to apply it to.
So, if you want to remove the write permission from the user that the file
hashcat.hcstat belongs to, you could enter the following:
kali >chmod u-w hashcat.hcstat
This command says to remove (-) the write (w) permission from hashcat.hcstat for the
user (u).
Now when you check the permissions with ls –l again, you should see that the
hashcat.hcstat file no longer has write permission for the user:
kali >ls -l
total 32952
drwxrxrx 5     root  root        
4096    Dec 5 10:47 charsets
rxrxr 1     root  root    33685504   June 28 2018 hashcat.hcstat
rwr r 1     root  root    33685504   June 28 2018 hashcat.hctune
drwxr xrx 2    root  root        
4096    Dec 5 10:47 masks
drwxr xrx 2    root  root        
drwxr xrx 3    root  root        
4096    Dec 5 10:47 OpenCL
4096    Dec 5 10:47 rules
You can also change multiple permissions with just one command. If you want to give
both the user and other users (not including the group) execute permission, you could
enter the following:
chmod u+x, o+x hashcat.hcstat
This command tells Linux to add the execute permission for the user as well as the
execute permission for others for the hashcat.hcstat file.
```
### OUTPUT
````
- Indicators for
  - User -> `u`
  - Group -> `g`
  - Others -> `o`
- Indicators for
  - Adding a permission -> `+`
  - Setting a permission -> `=`
  - Removing a permission -> `-`
- Remove the `write` permission from user for file `/usr/share/hashcat/hashcat.hcstat2`
    ```bash
        chmod u-w /usr/share/hashcat/hashcat.hcstat2 
    ```
- Give `execute` permission to both the owner and group for file `/usr/share/hashcat/hashcat.hcstat2`
    ```bash
        chmod u+x,g+x /usr/share/hashcat/hashcat.hcstat2 
    ```
- Reset back to the default permission `rw-r--r--` of `/usr/share/hashcat/hashcat.hcstat2`
    ```bash
        chmod u=rw,g=r,o=r /usr/share/hashcat/hashcat.hcstat2 
    ```
````

## EXAMPLE 9
### INPUT
```
VIEWING PROCESSES
In most cases, the first step in managing processes is to view what processes are
running on your system. The primary tool for viewing processes—and one of the Linux
.
administrator’s best friends—is the ps command. Run it in your command line to see
what processes are active:
kali >ps
PID    TTY      TIME      CMD
39659  pts/0    00:00:01  bash
39665  pts/0    00:00:00  ps
The Linux kernel, the inner core of the operating system that controls nearly
everything, assigns a unique process ID (PID) to each process sequentially, as the
processes are created. When working with these processes in Linux, you often need to
specify their PIDs, so it is far more important to note the PID of the process than the
name of the process.
Alone, the ps command doesn’t really provide you with much information. Running the
ps command without any options lists the processes started (said to be invoked) by the
currently loggedin user (in our case, root) and what processes are running on that
terminal. Here, it simply says that the bash shell is open and running and that we ran
the ps command. We want and need far more information than that, particularly on
those processes run by other users and by the system in the background. Without this
information, we know very little of what is actually taking place on our system.
Running the ps command with the options aux will show all processes running on the
system for all users, as shown in 
Listing 61. Note that you don’t prefix these options
with a dash (-) and that everything is in lowercase; because Linux is casesensitive,
using uppercase options woud give you significantly different results.
kali >ps aux
USER  PID   %CPU  %MEM    VSZ    RSS TTY    STAT START   TIME   COMMAND
Root    1    0.0   0.4    202540  6396 ?    Ss   Apr24    0:46  /sbin/init
Root    2    0.0   0.0         0     0 ?    S    Apr24    0:00  [kthreadd]
Root    3    0.0   0.0         0     0 ?    S    Apr24    0:26  [ksoftirqd/0]
snip
root  39706  0.0  0.2  36096  3204 pts/0    R+ 15:05  0:00    ps aux
Listing 61: Using the aux options to see processes for all users
As you can see, this command now lists so many processes, they likely run off the
bottom of your screen. The first process is init, listed in the final column, and the last
process is the command we ran to display, ps aux. Many of the details (PID, %CPU, TIME,
COMMAND, and so on) may be different on your system but should have the same format.
For our purposes, here are the most important columns in this output:
USER The user who invoked the process
PID The process ID
%CPU The percent of CPU this process is using
%MEM The percent of memory this process is using
COMMAND The name of the command that started the process
In general, to perform any action on a process, we must specify its PID. Let’s see how to
use this identifier to our advantage.
```
### OUTPUT
````
- View processes running in current terminal session
  ```bash
    ps
  ```
  - **PID:** Process ID - unique identifier assigned by the kernel to each process sequentially as they are created.
  - **TTY:** Terminal associated with the process.
  - **TIME:** CPU time consumed by the process.
  - **CMD:** Command/name of the process.

- View all processes running on the system for all users
  ```bash
    ps aux
  ```
  - Note: Options are not prefixed with a dash (-) and must be lowercase (Linux is case-sensitive).
  - **USER:** The user who invoked the process.
  - **PID:** The process ID.
  - **%CPU:** The percent of CPU this process is using.
  - **%MEM:** The percent of memory this process is using.
  - **VSZ:** Virtual memory size.
  - **RSS:** Resident set size (physical memory used).
  - **TTY:** Terminal type (`?` means no terminal attached).
  - **STAT:** Process state.
  - **START:** Time the process started.
  - **TIME:** CPU time consumed.
  - **COMMAND:** The name of the command that started the process.

- Why is the PID more important than the process name?
  - When working with processes in Linux, you often need to specify their PIDs to perform any action on a process.
  - The kernel assigns a unique PID to each process sequentially as processes are created.
````

## EXAMPLE 10
### INPUT
```
Filtering by Process Name
When we inquire about or perform an action on processes, we usually don’t want all of
the processes displayed on the screen. It’s simply a problem of too much information.
Most often, we want to find information on a single process. To do so, we can use the
filtering command grep, which I introduced in 
Chapter 1.
To demonstrate, we’ll use the Metasploit exploitation framework, the most widely used
exploitation framework and nearly every hacker’s good friend. This comes installed on
your Kali system, so start Metasploit with the following:
kali >msfconsole
Once the exploitation framework has been started, let’s see whether we can find it in
the list of processes. To do so, use the ps aux command and then pipe it (|) to grep
looking for the string msfconsole, as in 
Listing 62.
kali >ps aux | grep msfconsole
root 39756  0.0  0.0  4304  716  pts/2 Ss+  15:13  0:00 sh c service
postgresql start && msfdb init & msfconsole
root 39759  35.1  15.2  4304  227888  pts/2 Sl+  15:13  1:36 ruby /usr/bin/
msfconsole
root 39892  0.0  0.0  4304  940  pts/2 S+  15:18  0:00 grep msfconsole
Listing 62: Filtering a ps search to find a particular process
From the filtered output in this listing, you should see all the processes that match the
term msfconsole. The PostgreSQL database, which is the database Metasploit uses, is
shown first, then the msfconsole program itself from /usr/bin/msfconsole. Finally, you
should see the grep command you used to look for msfconsole. Notice that the output did
not include the column header list from ps. Since the keyword, msfconsole, is not in the
header, it is not displayed. Even so, the results are displayed in the same format.
From this, you can learn some important information. If, for example, you need to
know how many resources Metasploit is using, you can consult the third column (the
CPU column), to see that it’s using 35.1 percent of your CPU, and consult the fourth
column to see that it’s using 15.2 percent of your system memory. That’s quite a bit. It’s
a demanding beast!
```
### OUTPUT
````
- Start the Metasploit exploitation framework
  ```bash
    msfconsole
  ```

- Filter processes by name to find a specific process (e.g., msfconsole)
  ```bash
    ps aux | grep msfconsole
  ```
  - The `grep` command filters the output to show only processes matching the specified string.
  - The pipe (`|`) sends the output of `ps aux` to `grep` for filtering.
  - Note: The column headers are not displayed because they don't contain the search keyword.
  - Note: The `grep` command itself will also appear in the results since it contains the search term.

- Understanding filtered process output
  - The results maintain the same column format as `ps aux`:
    - **USER:** The user who invoked the process.
    - **PID:** The process ID.
    - **%CPU:** The percent of CPU this process is using.
    - **%MEM:** The percent of memory this process is using.
    - **COMMAND:** The name of the command that started the process.
  - Example: If `%CPU` shows `35.1` and `%MEM` shows `15.2`, the process is using 35.1% of CPU and 15.2% of system memory.
````

## RESPONSE RETURN FORMAT
````
- <action/task description>
  ```bash
    <command(s)>
  ```
  - **<field/option>:** `<value>` - <explanation>
    - <nested details if needed>

- <concept/explanation without command>
  - `<term>` -> <explanation>
  - **<label>:** <description>
````
``````

_**Note:** Use `Claude Opus 4.5-Think` from `outlier.ai` to prepare the responses._