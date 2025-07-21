# Linux-Essentials-Lab-D
Pipes, Redirection and REGEX
# 🐧 

This lab solves a typical beginner-level Linux command line task:  
**Extract a clean, sorted list of all unique service names** from the system file `/etc/services`.

The task was completed as part of the **NDG/Cisco Linux Essentials course**.

---

## 📌 Objective

- Extract all service names from `/etc/services`
- Exclude blank lines and comments
- Display only the first field (service name)
- Remove duplicates
- Sort alphabetically
- Save to a file called `uniqueservices.txt` in the home directory
- Count the total number of unique services

---

## 🛠️ Final Command Used

```bash
grep -v "^#" /etc/services | grep -v "^$" | awk '{print $1}' | sort | uniq > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt
