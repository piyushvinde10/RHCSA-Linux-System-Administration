# Truncate File Size in Linux

The `truncate` command is used to **shrink or expand the size of a file** to a specified size.

It is commonly used to **reduce file size or clear file contents without deleting the file**.

---

## Syntax

```
truncate -s SIZE filename
```

| Option | Description |
|------|-------------|
| `-s` | Set or change the file size |

---

# Example File

First check the file content:

```
cat file1
```

Example output:

```
arav Sharma
Vivaan Patel
Aditya Singh
```

---

# 1. Truncate File to 10 Bytes

```
truncate -s 10 file1
```

This command reduces the size of `file1` to **10 bytes**.

Check the file again:

```
cat file1
```

Example output:

```
arav Sharm
```

Only the first **10 bytes** remain in the file.

---

# 2. Increase File Size

```
truncate -s 15 file1
```

This increases the file size to **15 bytes**.

If the file becomes larger, empty space is added.

---

# 3. Edit File Using vi

```
vi file1
```

You can open the file using `vi` editor to modify its contents after truncating the file.

---

# Summary

| Command | Purpose |
|------|------|
| `truncate -s SIZE file` | Change file size |
| `truncate -s 10 file` | Reduce file to 10 bytes |
| `truncate -s 15 file` | Increase file size |
| `vi file` | Edit file contents |

---

# RHCSA Note

The `truncate` command is useful for:

- Managing file sizes
- Clearing log files
- Preparing files for testing
- File manipulation in Linux administration