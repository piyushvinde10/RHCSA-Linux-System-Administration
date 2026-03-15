# grep and egrep Command (Linux)

The `grep` command is used to search for a **specific pattern or keyword** inside a file.  
It prints the lines that match the search pattern.

`egrep` (Extended grep) is used for **advanced pattern searching** with multiple keywords.

---

## Syntax

```
grep [options] pattern file
```

---

# 1. Check grep Version

```
grep --version
```

Displays the installed version of the `grep` command.

---

# 2. Check Help for grep

```
grep --help
```

Shows all available options and usage for the `grep` command.

---

# 3. Search for a Keyword in a File

```
grep keyword file
```

Example

```
grep Rohan file1
```

This command searches for the word **Rohan** in `file1`.

---

# 4. Count Number of Matches

```
grep -c keyword file
```

Example

```
grep -c Rohan file1
```

This counts how many times the word **Rohan** appears in the file.

---

# 5. Ignore Case Sensitivity

```
grep -i keyword file
```

Example

```
grep -i rohan file1
```

This will match:

```
Rohan
rohan
ROHAN
```

---

# 6. Display Line Numbers

```
grep -n keyword file
```

Example

```
grep -n Rohan file1
```

Output will show the **line number where the match occurs**.

Example

```
9:Rohan Gupta
```

---

# 7. Display Lines Without Keyword

```
grep -v keyword file
```

Example

```
grep -v Rohan file1
```

This displays **all lines except those containing the word Rohan**.

---

# 8. Use grep with awk

```
grep keyword file | awk '{print $1}'
```

Example

```
grep Gupta file1 | awk '{print $1}'
```

This searches for **Gupta** and prints only the **first column**.

---

# 9. Search in Command Output

```
ls -l | grep file2
```

This searches for **file2** in the output of the `ls -l` command.

---

# 10. Search Multiple Keywords using egrep

```
egrep -i "keyword1|keyword2" file
```

Example

```
egrep -i "rohan|arjun" file1
```

This searches for **multiple keywords** in the file.

---

# Summary

`grep` and `egrep` are widely used in Linux for:

- Searching patterns in files
- Filtering command output
- Log file analysis
- Data extraction

These commands are commonly used with:

- `awk`
- `sed`
- `cut`
- `sort`

---

# RHCSA Note

`grep` is one of the most important commands for **text processing and log analysis in Linux system administration**.