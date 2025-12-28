# The Practical Ethical Hacking Roadmap
*From Zero to Exploit: A Sequence for Hands-On Mastery*

This roadmap is designed to build skills layer-by-layer: Operating System -> Networking -> Methodology -> Web Applications -> Automation -> Binary Exploitation.

---

### Phase 1: The Foundation (Operating System)
**Book:** *Linux Basics for Hackers*
**Author:** OccupyTheWeb
*   **Why here:** You cannot secure or attack what you cannot control. Before touching tools or networks, you must master the command line.
*   **What you learn:** Bash scripting, file permissions, managing services, and using Linux specifically as a hacking platform (Kali Linux).
*   **Goal:** Stop relying on a GUI (mouse) and become comfortable in the terminal.

### Phase 2: The Infrastructure (Networking)
**Book:** *Network Basics for Hackers*
**Author:** OccupyTheWeb
*   **Why here:** Tools are useless if you don't understand the traffic they generate. This bridges the gap between the OS and the attack.
*   **What you learn:** TCP/IP handshakes, DNS, SMTP, wireless protocols, and packet analysis with Wireshark—all explained through the lens of how they can be exploited, rather than how to configure office printers.
*   **Goal:** Understand exactly how data moves and where it is vulnerable during transit.

### Phase 3: The Methodology (Network Attacks)
**Book:** *The Hacker Playbook 3: Practical Guide to Penetration Testing*
**Author:** Peter Kim
*   **Why here:** Now that you know Linux and Networking, you are ready to simulate an adversary. This book is a "playbook" of specific moves.
*   **What you learn:** Red Teaming strategies, lateral movement, pivoting through networks, credential dumping, and bypassing antivirus.
*   **Goal:** Learn to think and act like an adversary on a corporate network.

### Phase 4: The Target (Web Application Security)
**Book:** *Real-World Bug Hunting: A Field Guide to Web Hacking*
**Author:** Peter Yaworski
*   **Why here:** The network is often just the road; the website is the destination. This moves you up the stack to the Application Layer (Layer 7).
*   **What you learn:** XSS, SQL Injection, CSRF, and IDOR. It uses actual bug bounty reports from major tech companies to show how these vulnerabilities look in real code.
*   **Goal:** Learn to spot logic errors and coding flaws in web applications.

### Phase 5: The Automation (Scripting & Tool Development)
**Book:** *Black Hat Python (2nd Edition)*
**Authors:** Justin Seitz & Tim Arnold
*   **Why here:** Eventually, pre-made tools (like Nmap or Metasploit) won't work or will be detected. You need to build your own.
*   **What you learn:** Writing network sniffers, keyloggers, trojans, and privilege escalation scripts using Python.
*   **Goal:** Transition from a "Script Kiddie" (tool user) to a Hacker (tool builder).

### Phase 6: The Deep Dive (Memory & Binary Exploitation)
**Book:** *Hacking: The Art of Exploitation (2nd Edition)*
**Author:** Jon Erickson
*   **Why here:** This is the "Final Boss." It covers low-level architecture that underlies everything else.
*   **What you learn:** C programming, memory corruption, buffer overflows, and shellcode. It explains how the computer processes instructions physically.
*   **Goal:** Master the machine at the binary level.

---

### ➕ Enhanced Additions (Recommended Supplements)

#### 🔹 **Phase 3.5: Intelligence Gathering (OSINT)**
*   **Resource:** *OSINT Techniques: Resources & Methods for Investigating Online* by Michael Bazzell
*   **Tools to Learn:** theHarvester, Maltego, Shodan, WHOIS, GitHub dorking
*   **Why:** Real-world attacks often begin with minimal information. OSINT teaches how to profile targets, discover infrastructure, and identify attack surfaces using public data.

#### 🔹 **Phase 4.5: Web Proxies & Interception (Burp Suite Deep Dive)**
*   **Tool:** PortSwigger Burp Suite (Community/Professional)
*   **Practice Platform:** [PortSwigger Web Security Academy](https://portswigger.net/web-security) (Free)
*   **Why:** Essential for mastering manual web application testing. Learn to intercept, modify, and replay HTTP(S) requests to exploit vulnerabilities like XSS, IDOR, and CSRF effectively.

#### 🔹 **Parallel Track: Blue Team Awareness (Defensive Counterparts)**
*   **Pair each offensive skill with defensive understanding:**
    *   After network attacks → Study how Snort/Suricata (IDS) detect malicious traffic.
    *   After web exploits → Learn how WAFs (e.g., ModSecurity) block injection attempts.
    *   After privilege escalation → Explore logging with `auditd`, Sysmon, or EDR tools.
*   **Why:** Building a “purple team” mindset improves detection evasion and makes you a more effective and responsible ethical hacker.

#### 🔹 **Phase 6.5: Binary Exploitation Support Resources**
*   **Video Series:** [LiveOverflow YouTube Channel](https://www.youtube.com/c/LiveOverflow) – Practical binary hacking & CTF walkthroughs
*   **Book Supplement:** *Computer Systems: A Programmer’s Perspective (3rd Ed)* – For deeper understanding of assembly, memory, and program execution
*   **CTF Practice Platforms:** pwnable.kr, pwnable.tw, Hack The Box (Pwn challenges)
*   **Why:** *Hacking: The Art of Exploitation* is dense. These resources provide modern context, visual explanations, and hands-on practice with protections like ASLR, DEP/NX, and stack canaries.

#### 🔹 **Post-Roadmap: Future-Proofing Your Skills**
*   **Mobile App Security:** Learn Android/iOS reverse engineering with tools like MobSF, Frida, and Drozer.
*   **Cloud Security:** Explore AWS, Azure, and GCP misconfigurations, IAM flaws, and serverless risks.
*   **API Security:** Master testing GraphQL and REST APIs for auth bypasses, IDOR, rate limiting issues, and business logic flaws.
*   **Why:** As technology evolves, these domains represent high-value attack surfaces in modern enterprises.

---

### Execution Strategy
1.  **Build a Lab:** Do not read these in bed. Set up a virtual machine (Kali Linux) using VirtualBox or VMware.
2.  **Type the Code:** Do not copy-paste. Typing builds muscle memory.
3.  **Respect the Order:** Do not skip Phase 2 (Networking). It is the most common reason beginners fail at Phase 3 and 4.