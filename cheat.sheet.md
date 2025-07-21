# 🐧 Linux Cheat Sheet: Extracting Unique Services from /etc/services

## 🎯 Task Summary

Create a list of all unique service names from the `/etc/services` file:

- Exclude comments and empty lines
- Extract only the service names (first word in each line)
- Sort and remove duplicates
- Save the output to a file called `uniqueservices.txt` in the home directory
- Count the number of lines in the final output — **only if** the previous step was successful

---

## 💡 Final Command

```bash
grep -v "^#" /etc/services | grep -v "^$" | awk '{print $1}' | sort | uniq > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt

🔍 Explanation of Each Part

🔹 grep -v "^#"
	•	grep = searches for lines matching a pattern
	•	-v = inverts the match (i.e., exclude lines that match)
	•	"^#" = matches any line that starts with #, which means it’s a comment
	•	✅ Result: removes all comment lines

⸻

🔹 grep -v "^$"
	•	"^$" = matches empty lines (lines with nothing in them)
	•	-v = exclude those lines
	•	✅ Result: removes all blank lines

⸻

🔹 awk '{print $1}'
	•	awk = text processing tool
	•	'{print $1}' = prints only the first field (first word) from each line, which is the service name
	•	✅ Result: keeps only service names, removes the rest (like port numbers or descriptions)

⸻

🔹 sort
	•	Alphabetically sorts the list of service names
	•	Required before using uniq, which only removes adjacent duplicates

⸻

🔹 uniq
	•	Removes repeated lines, but only works if identical lines are next to each other — that’s why we sorted first
	•	✅ Result: ensures each service name appears only once

⸻

🔹 > ~/uniqueservices.txt
	•	> = redirects the final output to a file
	•	~ = shorthand for the current user’s home directory
	•	✅ Result: creates (or overwrites) a file uniqueservices.txt in your home folder with the cleaned list

⸻

🔹 &&
	•	Conditional execution
	•	Runs the next command only if the previous one was successful (i.e., exit code was 0)

⸻

🔹 wc -l ~/uniqueservices.txt
	•	wc = word count tool
	•	-l = counts lines
	•	✅ Result: tells you how many unique services are in your output file

⸻

📁 Final Output Preview
	•	🔹 File created: ~/uniqueservices.txt
	•	🔹 Contains exactly 340 unique service names (if using the default /etc/services)
	•	🔹 Use the following commands to view content:
head ~/uniqueservices.txt     # Shows the first 10 lines
tail ~/uniqueservices.txt     # Shows the last 10 lines
wc -l ~/uniqueservices.txt    # Confirms line count (should be 340)
