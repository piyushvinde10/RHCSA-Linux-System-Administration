# Compare Files in Linux (diff and cmp)

Linux provides commands to compare files and identify differences between them.  
Two commonly used commands are:

- `diff` – compares files line by line
- `cmp` – compares files byte by byte

---

## Verify Files

Before comparing, check the contents of both files.

### File1

```
cat file1
```

Example content:

```
arav Sharma
Vivaan Patel
Aditya Singh
Arjun Kumar
Rohan Gupta
Kabir Mehta
Ishaan Verma
Neha Sharma
Piyush Vinde
Priya Patel
Ananya Gupta
Priya Patel
```

### File2

```
cat file2
```

Example content:

```
arav Sharma
Vivaan Patel
Aditya Singh
Arjun Kumar
Rohan Gupta
Kabir Mehta
Ishaan Verma
Neha Sharma
Priya Patel
Ananya Gupta
Priya Patel
```

---

# diff Command

The `diff` command compares files **line by line** and shows the differences.

### Syntax

```
diff file1 file2
```

### Example

```
diff file1 file2
```

Example output:

```
9d8
< Piyush Vinde
```

Explanation:

- `9d8` → Line 9 in file1 is different compared to file2
- `<` indicates content present in file1 but not in file2

---

# cmp Command

The `cmp` command compares two files **byte by byte**.

### Syntax

```
cmp file1 file2
```

If the files are identical, no output is displayed.

If they differ, it shows the position of the first difference.

Example output:

```
file1 file2 differ: byte 120, line 9
```

---

# Summary

| Command | Comparison Type |
|--------|----------------|
| diff | Line by line comparison |
| cmp | Byte by byte comparison |

---

# RHCSA Note

The `diff` and `cmp` commands are useful for:

- Checking differences between configuration files
- Comparing text files
- Troubleshooting system changes
- Verifying file integrity