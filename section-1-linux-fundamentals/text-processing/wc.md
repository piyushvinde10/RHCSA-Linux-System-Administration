# wc Command (Linux)

The `wc` command is a text processing utility in Linux used to **count lines, words, and bytes** in a file.

`wc` stands for **word count**.

---

## Syntax

```
wc [options] file
```

---

# 1. Check wc Version

```
wc --version
```

Displays the installed version of the `wc` command.

---

# 2. Check Help

```
wc --help
```

Shows all available options and usage of the `wc` command.

---

# 3. Count Lines, Words, and Bytes

```
wc file1
```

This command displays:

- Number of lines
- Number of words
- Number of bytes
- File name

Example output:

```
11 22 136 file1
```

Explanation:

| Value | Meaning |
|-----|------|
| 11 | Number of lines |
| 22 | Number of words |
| 136 | Number of bytes |

---

# 4. Count Number of Lines

```
wc -l file1
```

Displays the **total number of lines** in a file.

Example:

```
11 file1
```

---

# 5. Count Number of Words

```
wc -w file1
```

Displays the **total number of words** in a file.

Example:

```
22 file1
```

---

# 6. Count Number of Bytes

```
wc -c file1
```

Displays the **total number of bytes** in a file.

Example:

```
136 file1
```

---

# 7. wc on Directory

```
wc dir1
```

This command will return an error because `wc` works on **files**, not directories.

Example output:

```
wc: dir1: Is a directory
```

---

# 8. Count Number of Files

```
ls -l | wc -l
```

Counts the **number of files and directories** listed in the current directory.

---

# 9. Count Matching Lines

```
grep keyword file1 | wc -l
```

Counts the **number of lines containing a specific keyword**.

Example:

```
grep Gupta file1 | wc -l
```

This will show how many lines contain the word **Gupta**.

---

# Summary

The `wc` command is useful for:

- Counting lines in files
- Counting words in text
- Measuring file size in bytes
- Analyzing log files
- Processing command output

It is often used with commands such as:

- `grep`
- `cat`
- `ls`
- `awk`

---

# RHCSA Note

The `wc` command is important for **text processing, file analysis, and log monitoring in Linux system administration**.