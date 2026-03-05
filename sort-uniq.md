# sort and uniq Command (Linux)

The `sort` command is used to sort lines of text files in alphabetical or numerical order.  
The `uniq` command is used to remove duplicate lines from a file.

Both commands are commonly used together in Linux text processing.

---

## Syntax

```
sort [options] file
uniq [options] file
```

---

# 1. Check sort Version

```
sort --version
```

Displays the installed version of the `sort` command.

---

# 2. Check sort Help

```
sort --help
```

Shows all available options and usage of the `sort` command.

---

# 3. Sort File Alphabetically

```
sort file1
```

This command sorts the contents of `file1` in alphabetical order.

Example output:

```
Aditya Singh
Ananya Gupta
Arjun Kumar
Ishaan Verma
Kabir Mehta
```

---

# 4. Sort in Reverse Order

```
sort -r file1
```

Sorts the file in reverse alphabetical order.

---

# 5. Sort by Field Number

```
sort -k2 file1
```

Sorts the file based on the second column (field).

---

# 6. Remove Duplicate Lines

```
uniq file1
```

Removes duplicate lines from a file.

Note: The file should be sorted before using `uniq`.

---

# 7. Sort and Remove Duplicates

```
sort file1 | uniq
```

This command sorts the file first and then removes duplicate lines.

---

# 8. Count Repeated Lines

```
sort file1 | uniq -c
```

Displays the number of times each line appears.

Example output:

```
1 Aditya Singh
2 Priya Patel
1 Rohan Gupta
```

---

# 9. Show Only Duplicate Lines

```
sort file1 | uniq -d
```

Displays only the repeated lines.

Example output:

```
Priya Patel
```

---

# Summary

The `sort` and `uniq` commands are useful for:

- Sorting text data
- Removing duplicate lines
- Counting repeated entries
- Data processing and log analysis

These commands are often used with:

- `grep`
- `awk`
- `sed`
- `cut`

---

# RHCSA Note

`sort` and `uniq` are important commands for text processing and data filtering in Linux system administration.