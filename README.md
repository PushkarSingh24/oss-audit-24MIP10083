# OSS Audit — Mozilla Firefox

**Student:** Pushkar Singh  
**Roll Number:** 24MIP10083  
**Course:** Open Source Software (NGMC)  
**Software Chosen:** Mozilla Firefox  
**Licence:** Mozilla Public License 2.0 (MPL 2.0)

---

## About This Project

This repository is the shell script submission for the Open Source Audit capstone project. The project involves a structured audit of Mozilla Firefox — covering its origin story, licence analysis, Linux footprint, ecosystem, and a comparison with proprietary alternatives. The full written report is submitted separately on the VITyarthi portal.

---

## Repository Structure

```
oss-audit-24MIP10083/
├── README.md
├── script1_system_identity.sh
├── script2_package_inspector.sh
├── script3_disk_permission_auditor.sh
├── script4_log_analyzer.sh
└── script5_manifesto_generator.sh
```

---

## Script Descriptions

### Script 1 — System Identity Report
**File:** `script1_system_identity.sh`  
Displays a formatted welcome banner with information about the Linux system: distribution name, kernel version, logged-in user, home directory, uptime, current date/time, and the open-source licence covering the OS (GPL v2 for the Linux kernel).  
**Concepts:** variables, command substitution `$()`, `echo`, `date`, `uname`, `uptime`, `whoami`

---

### Script 2 — FOSS Package Inspector
**File:** `script2_package_inspector.sh`  
Checks whether Firefox is installed on the system using `dpkg` (Debian/Ubuntu) or `rpm` (Fedora/RHEL), prints version and package metadata, and uses a `case` statement to output a short open-source philosophy note for Firefox and several other FOSS packages.  
**Concepts:** `if-then-else`, `case` statement, `dpkg`/`rpm` querying, `grep` with `-E`, `awk`, pipe `|`

---

### Script 3 — Disk and Permission Auditor
**File:** `script3_disk_permission_auditor.sh`  
Loops through a list of important Linux directories (`/etc`, `/var/log`, `/home`, `/usr/bin`, `/tmp`, `/opt`) and reports the permissions, owner, group, and disk usage of each. Also specifically checks Firefox's user profile directory at `~/.mozilla/firefox` and the Firefox binary location.  
**Concepts:** `for` loop over an array, `-d` directory test, `ls -ld`, `awk`, `du -sh`, `cut`, `$HOME`

---

### Script 4 — Log File Analyzer
**File:** `script4_log_analyzer.sh`  
Reads a log file line by line and counts how many lines contain a given keyword (defaults to `error` if not specified). Includes a do-while style retry loop for empty files, and prints the last 5 matching lines at the end. Accepts the log file path and keyword as command-line arguments.  
**Concepts:** `while read` loop, `if-then`, counter variables `$(( ))`, `$1`/`$2` arguments, default parameters `${2:-default}`, `grep -i`, `tail`, `wc -l`

---

### Script 5 — Open Source Manifesto Generator
**File:** `script5_manifesto_generator.sh`  
Interactively asks the user three questions using `read -p`, then composes a personalised open-source philosophy paragraph using those answers and saves it to a `.txt` file named after the current user. The file is written using `>` and `>>` redirection and displayed using `cat`.  
**Concepts:** `read` for user input, string concatenation with variables, `>` and `>>` file redirection, `cat`, `date`, `$(whoami)`, shell functions, aliases (demonstrated via comments)

---

## How to Run

### Prerequisites
- A Linux system (tested on Ubuntu/Debian via online terminal)
- Bash shell (`bash --version` to verify)
- For Script 2: either `dpkg` or `rpm` package manager, or Firefox installed manually
- For Script 4: a readable log file (e.g. `/var/log/syslog`)

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/<your-username>/oss-audit-24MIP10083.git
cd oss-audit-24MIP10083
```

**2. Make all scripts executable**
```bash
chmod +x script*.sh
```

**3. Run each script**

```bash
# Script 1 — no arguments needed
./script1_system_identity.sh

# Script 2 — no arguments needed (package is set inside the script)
./script2_package_inspector.sh

# Script 3 — no arguments needed
./script3_disk_permission_auditor.sh

# Script 4 — pass a log file path; keyword is optional (defaults to 'error')
./script4_log_analyzer.sh /var/log/syslog error
./script4_log_analyzer.sh /var/log/syslog warning

# Script 5 — no arguments; will prompt you interactively
./script5_manifesto_generator.sh
```

---

## Dependencies

| Script | Dependencies |
|--------|-------------|
| Script 1 | `uname`, `whoami`, `uptime`, `date`, `cat` — all standard on any Linux system |
| Script 2 | `dpkg` (Ubuntu/Debian) or `rpm` (Fedora/RHEL); `grep`, `awk` |
| Script 3 | `ls`, `du`, `awk`, `cut` — all standard |
| Script 4 | `grep`, `wc`, `tail` — all standard |
| Script 5 | `date`, `whoami`, `cat` — all standard |

No external packages need to be installed. All dependencies are part of a standard Linux installation.

---

## Notes

- Scripts were written and tested on an online Linux terminal (Ubuntu base).
- Script 2 auto-detects whether the system uses `dpkg` or `rpm` and adjusts accordingly.
- Script 4 will exit with an error message if no log file path is provided or the file does not exist.
- Script 5 saves the generated manifesto as `manifesto_<username>.txt` in the current directory.

---

## Reference

- Mozilla Firefox source: [searchfox.org](https://searchfox.org)  
- MPL 2.0 licence text: [mozilla.org/en-US/MPL/2.0](https://www.mozilla.org/en-US/MPL/2.0/)  
- GNU Bash Manual: [gnu.org/software/bash/manual](https://www.gnu.org/software/bash/manual/)  
- The Linux Command Line (Shotts): [linuxcommand.org](http://linuxcommand.org)
