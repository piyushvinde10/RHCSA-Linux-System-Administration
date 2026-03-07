# Combining and Splitting Files in Linux

Linux provides commands to combine multiple files into one file and split large files into smaller parts.

These operations are useful for file management, data processing, and transferring large files.

---

# 1. Combining Files

The `cat` command can combine multiple files into a single file.

## Syntax

```
cat file1 file2 file3 > file4
```

## Example

```
cat file1 file2 file3 > file4
```

Explanation:

- `file1`, `file2`, `file3` → Source files
- `>` → Redirects output
- `file4` → Combined output file

Check the combined file:

```
cat file4
```

Example output:

```
arav Sharma
Rohan Patel
Rahul Verma
Aman Gupta
Vikram Singh
```

---

# 2. Splitting Files

The `split` command divides a large file into smaller files.

## Syntax

```
split -l 10 file4 file4
```

Explanation:

| Option | Meaning |
|------|------|
| `-l` | Number of lines per split file |
| `file4` | Original file |
| `file4` | Prefix for split files |

---

## Example

```
split -l 10 file4 file4
```

This splits the file into multiple files such as:

```
file4aa
file4ab
file4ac
file4ad
```

Each file will contain **10 lines**.

Check the files:

```
ls
```

---

# Summary

| Command | Purpose |
|------|------|
| `cat file1 file2 > file3` | Combine multiple files |
| `split -l N file prefix` | Split file into smaller parts |

---

# RHCSA Note

Combining and splitting files are useful for:

- Managing large log files
- Data processing
- File transfer
- Backup and archiving