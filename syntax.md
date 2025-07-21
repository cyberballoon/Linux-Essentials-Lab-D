# 🧾 Syntax Reference: Extract Unique Services from /etc/services

This file contains all the command-line syntax used to complete the lab task, explained simply.

---

## 🔹 Main Command

```bash
grep -v "^#" /etc/services | grep -v "^$" | awk '{print $1}' | sort | uniq > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt
