# sort and uniq Command (Linux)

The `sort` command is used to **sort lines of text files** in alphabetical or numerical order.  
The `uniq` command is used to **remove duplicate lines** from a sorted file.

Both commands are commonly used together for **text processing in Linux**.

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

Displays the installed version of the `sort` command. :contentReference[oaicite:0]{index=0}

---

# 2. Check sort Help

```
sort --help
```

Shows available options and usage of the `sort` command. :contentReference[oaicite:1]{index=1}

---

# 3. Sort File Alphabetically

```
sort file1
```

This command sorts the contents of `file1` in **alphabetical order**. :contentReference[oaicite:2]{index=2}

Example output

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

Sorts the file in **reverse alphabetical order**. :contentReference[oaicite:3]{index=3}

---

# 5. Sort by Field Number

```
sort -k2 file1
```

Sorts the file based on the **second field (column)**. :contentReference[oaicite:4]{index=4}

---

# 6. Remove Duplicate Lines

```
uniq file1
```

Removes **duplicate lines** from a file.  
The file should be sorted before using `uniq`. :contentReference[oaicite:5]{index=5}

---

# 7. Sort and Remove Duplicates

```
sort file1 | uniq
```

This command first sorts the file and then removes duplicate lines. :contentReference[oaicite:6]{index=6}

---

# 8. Count Repeated Lines

```
sort file1 | uniq -c
```

Displays each line with the **number of times it appears**. :contentReference[oaicite:7]{index=7}

Example output

```
1 Aditya Singh
2 Priya Patel
1 Rohan Gupta
```

---

# 9. Display Only Repeated Lines

```
sort file1 | uniq -d
```

Shows only the **duplicate lines** in the file. :contentReference[oaicite:8]{index=8}

Example output

```
Priya Patel
```

---

# Summary

The `sort` and `uniq` commands are useful for:

- Sorting text data
- Removing duplicate lines
- Counting repeated values
- Data cleaning and analysis

These commands are often used with:

- `grep`
- `awk`
- `sed`
- `cut`

---

# RHCSA Note

`sort` and `uniq` are important commands for **text processing, log analysis, and data filtering in Linux system administration**.