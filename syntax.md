# 🧾 Syntax Reference: Extract Unique Services from /etc/services

This file contains all the command-line syntax used to complete the lab task, explained simply.

---

## 🔹 Main Command

```bash
grep -v "^#" /etc/services | grep -v "^$" | awk '{print $1}' | sort | uniq > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt

🔍 Breakdown of Syntax
Command Part
Explanation
grep -v "^#"
Exclude lines that start with a # (comments)
grep -v "^$"
Exclude empty (blank) lines
awk '{print $1}'
Print only the first word of each line (the service name)
sort
Sort the list alphabetically
uniq
Remove duplicate lines (needs sorted input)
>
Redirect output into a file
~/uniqueservices.txt
File path — creates or overwrites this file in your home directory
&&
Run the next command only if the previous one was successful
wc -l ~/uniqueservices.txt
Count the number of lines in the output file
head ~/uniqueservices.txt   # Show first 10 lines
tail ~/uniqueservices.txt   # Show last 10 lines
ls ~                        # Check if the file was created
